---
title: 在主页中创建用于 3D 模型
description: 资产要求和创作三维模型用于 Windows Mixed Reality HoloLens 和沉浸式 (VR) 耳机家庭中的指南。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D，建模，建模指南，资产要求，创作指南、 启动器、 3D 启动器、 纹理、 材料、 复杂性、 三角形、 网格、 多边形、 polycount，限制
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692282"
---
# <a name="create-3d-models-for-use-in-the-home"></a>在主页中创建用于 3D 模型

[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。 可以设计 Windows Mixed Reality 耳机，若要利用应用程序[三维模型应用启动器](implementing-3d-app-launchers.md)，并允许[3D 深层链接以放入 Windows Mixed Reality 家庭](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)从您的应用程序中。 本文概述了用于创建三维模型与 Windows Mixed Reality 家庭兼容的准则。

## <a name="asset-requirements-overview"></a>资产要求概述
在创建三维模型用于 Windows Mixed Reality 时有所有资产必须都满足一些要求： 
1. [导出](#exporting-models)的资产必须传递.glb 文件格式 (二进制 glTF)
2. [建模](#modeling-guidelines)的资产必须是少于 10 个 k 三角形，具有不超过 64 个节点和每个 LOD 32 submeshes
3. [材料](#material-guidelines)-纹理大小不得超过 4096 x 4096 和最小的 mip 映射应为不大于 4 上任一维度
4. [动画](#animation-guidelines)-不得超过 20 分钟的时间以每秒 30 帧的动画 （36000 关键帧），并且必须包含 < = 8192 morph 目标顶点
5. [优化](#optimizations)-应使用优化资产[WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)。 这是**在 Windows 操作系统版本上所需 < = 1709年**，建议在 Windows 操作系统版本上 > = 1803年

本文的其余部分包括这些要求，以及其他准则以确保您的模型很好地配合 Windows Mixed Reality 主页的详细的概述。 

## <a name="detailed-guidance"></a>详细的指南

### <a name="exporting-models"></a>导出模型

Windows Mixed Reality 家庭需要三维资产，以使用嵌入的图像和二进制数据使用.glb 文件格式来提供。 Glb 是缴纳版税的 glTF 格式的二进制版本由 Khronos 组维护的三维资产传送的免费开放标准。 在 Windows 应用和体验的行业标准的可互操作三维内容 glTF 随着因此将对格式的 Microsoft 的支持。 如果之前您可以找到尚未创建 glTF 资产[列表中的受支持的导出程序和转换器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)glTF 工作组 github 页上。  

### <a name="modeling-guidelines"></a>建模指南

Windows 需要的资产，以生成使用以下的建模准则以确保与混合现实家庭体验的兼容性。 在所选的应用程序建模时请记住以下建议和限制：
1. 最多轴应设置为"Y"。
2. 资产应"forward"正 Z 轴向人脸。
3. 应以场景原点 (0,0,0) 地面上生成的所有资产
4. 工作单元应设置为计量和资产，以便可以在世界上规模较大创作资产
5. 不需要的所有网格结合使用，但是建议如果在针对资源约束设备
6. 所有网格应只有一个纹理设置用于整个资产与都共享 1 材料
7. Uv 必须在 0-1 方形的排列方式布局空间。 避免平铺纹理，但允许这样做。
8. 不支持多 Uv
9. 不支持双精度单面的材料

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形计数和的详细信息 (Lod) 级别

主 Windows Mixed Reality 不支持具有超过 10,000 个三角形的模型。 建议在导出以确保它们不超过此计数之前三角化将网格。 Windows MR 还支持可选的几何图形级别的详细信息 (Lod) 以确保高性能且高品质体验。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)将帮助您将您的模型的 3 个版本合并成单个.glb 模型。 Windows 确定哪些 LOD 显示根据模型什么占用了屏幕空间量。 只需 3 LOD 级别支持使用以下建议三角形计数：
<br>

|  LOD 级别  |  建议的三角形计数  |  最大三角形计数 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>节点计数和显示的子网格限制
主 Windows Mixed Reality 不支持具有 64 个以上节点或每 LOD 32 submeshes 的模型。 节点是中的概念[glTF 规范](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)的场景中定义的对象。 中的数组定义 submeshes[基元](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)对象中网格上。 

|  功能 |  描述  |  最大支持 | 文档 |
|------|------|------|------|
|  节点数 |  GlTF 场景中的对象 |  每个 LOD 64 | [此处](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  上的所有网格基元的总和 |  每个 LOD 32 | [此处](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>材料的指导原则

纹理应准备好使用 PBR 裸机粗糙度工作流。 首先，创建一套完整的包括 Albedo、 Normal、 封闭、 金属外观和粗糙度的纹理。 Windows Mixed Reality 支持纹理分辨率高达 4096x4096 但建议在 512 x 512，在创作。 此外纹理应以 4 的倍数分辨率创作因为这是必需的压缩格式应用于如下所述的导出步骤中的纹理。 最后，当 gerating mip 映射或纹理最低 mip 必须是 4 × 4 的最大值。
<br>

|  建议的纹理大小  |  最大纹理大小 | 最小的 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大 4 × 4|

### <a name="albedo-base-color-map"></a>Albedo （基础颜色） 映射

没有照明信息的原始颜色。 此映射还分别包含的反射度和金属 （白色金属映射中） 和 （金属映射中为黑色） 绝缘体表面的漫射信息。

### <a name="normal"></a>正常

切空间正常映射

### <a name="roughness-map"></a>粗糙度映射

描述对象的 microsurface。 白色 1.0 是粗略黑色 0.0 非常顺利。 此映射提供最多字符它真正所述在图面例如讲述了的资产、 指纹、 这个、 污垢等。

### <a name="ambient-occlusion-map"></a>环境封闭映射

值扩展映射进行描述的封闭的像素 light 阻止的反射效果的区域

### <a name="metallic-map"></a>金属映射

通知是否某些内容是否为 metal 着色器。 原始金属 = 1.0 白色非金属 = 0.0 黑色。 可以过渡灰色值，用于指示内容覆盖原始金属如灰尘，但一般情况下，此映射应为黑色和白色。

## <a name="optimizations"></a>优化

Windows Mixed Reality 家庭提供了一系列的基础上使用自定义扩展插件定义核心 glTF 规范的优化。 这些优化，需要在 Windows 版本上 < = 1709年，建议使用较新版本的 Windows 上。 您可以轻松地优化任何 glTF 2.0 模型使用[Windows 混合现实资产转换器可在 GitHub 上](https://github.com/Microsoft/glTF-Toolkit/releases)。 此工具将执行的正确打包的纹理和按以下指定的优化。 对于常规使用我们建议使用 WindowsMRAssetConverter，但如果需要更好地控制体验，并且想要生成优化值管道然后您可以参考下面的详细规范。  

### <a name="materials"></a>材料

若要提高资产加载时间在混合现实环境中 Windows MR 支持呈现压缩的纹理打包在本部分中定义的方案根据打包的 DDS 纹理。 使用引用 DDS 纹理[MSFT_texture_dds 扩展](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)。 强烈建议压缩纹理。 

#### <a name="hololens"></a>HoloLens

基于 HoloLens 混合的现实体验预期纹理填满使用一个使用以下装箱规范的 2 纹理安装：
<br>

|  glTF 属性  |  纹理  |  封装方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  红色 (R)，绿色 (G)，蓝色 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  正常 (RG)，(B) 粗糙度金属外观 (A) | 


压缩 DDS 纹理时以下压缩会在每个映射：
<br>

|  纹理  |  预期的压缩 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>沉浸式 (VR) 耳机

基于 PC 的沉浸式 (VR) 耳机 Windows Mixed Reality 体验预期纹理填满使用一个使用以下装箱规范的 3 纹理安装：

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  glTF 属性  |  纹理  |  封装方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  红色 (R)，绿色 (G)，蓝色 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R)，粗糙度 (G) 金属外观 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  正常 (RG) | 

压缩 DDS 纹理时以下压缩会在每个映射：
<br>

|  纹理  |  预期的压缩 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  glTF 属性  |  纹理  |  封装方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  红色 (R)，绿色 (G)，蓝色 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R)，金属外观 (G)、 封闭 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  正常 (RG) | 

压缩 DDS 纹理时以下压缩会在每个映射：
<br>

|  纹理  |  预期的压缩 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>添加网格 Lod

Windows MR 使用 geometry 节点 Lod 呈现三维模型中不同级别的详细信息，具体取决于屏幕覆盖率。 尽管此功能从技术上讲不是必需，强烈建议对所有的资产。 目前 Windows 支持三种级别的详细信息。 默认值 LOD 为 0，它表示最高的质量。 其他 Lod 是按顺序编号，例如 1、 2 和渐进式中质量较低级别 get。 [Windows 混合现实资产转换器](https://github.com/Microsoft/glTF-Toolkit/releases)支持生成满足此 LOD 规范接受多个 glTF 模型并将它们合并到具有有效 LOD 级别的单个资产的资产。 下表概述了预期的 LOD 排序和三角形目标：
<br>

|  LOD 级别  |  建议的三角形计数  |  最大三角形计数 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

始终使用 Lod 时指定 3 个 LOD 级别。 缺少 Lod 将导致不呈现为 LOD 系统切换到缺失 LOD 级别的意外的模型。 glTF 2.0 当前不支持 Lod 核心规范的一部分。因此应使用定义 Lod [MSFT_LOD 扩展](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)。

### <a name="screen-coverage"></a>屏幕覆盖率

Lod 会显示在 Windows Mixed Reality 基于设置的每个 LOD 屏幕覆盖率值由驱动的系统上。 在更高版本的 LOD 级别显示当前正在使用较大屏幕空间的一部分的对象。 屏幕覆盖率不属于核心 glTF 2.0 规范，并且必须在"附加程序"部分中的使用 MSFT_ScreenCoverage 指定[MSFT_lod 扩展](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)。
<br>

|  LOD 级别  |  建议的范围  |  默认范围 | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  低于 50%-20%  |  .2 | 
|  LOD 2 |  低于 20%的 1%  |  .01 | 
|  LOD 4  |  低于 1%  |  - | 

## <a name="animation-guidelines"></a>动画指导原则

> [!NOTE]
> 此功能已添加的一部分[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)。 在较旧版本的 Windows 这些动画将无法播放，但是，它们将仍然加载如果编写，根据本文中的指导。  

混合的现实主页上 HoloLens 和沉浸式 (VR) 耳机支持动画的 glTF 对象。 如果你想要触发您在模型上的动画，您将需要 glTF 格式上使用动画映射扩展。 此扩展可以触发基于用户遍布全球的 glTF 模型中的动画，例如触发动画时，用户是接近对象或虽然它们正在查看它。 如果 glTF 对象具有动画，但未定义触发器将不返回播放动画。 以下部分介绍用于将这些触发器添加到任何动画的 glTF 对象的一个工作流。

### <a name="tools"></a>工具
如果你还没有它们，首先，下载以下工具。 这些工具可轻松打开任何 glTF 模型、 预览、 进行更改和保存回为 glTF 或.glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [针对 Visual Studio Code glTF 工具](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>打开和预览模型
首先，通过将.glTF 文件拖动到编辑器窗口中打开在 VSCode 中 glTF 模型。 请注意，如果您有而不是.glTF.glb 文件您可以将其导入 VSCode 使用所下载 glTF 工具外接程序。 请转到"视图-> 命令面板"，然后开始在命令面板中键入"glTF"并选择"glTF:导入从 glb"这将会弹出来将与.glb 导入的文件选取器。 

打开 glTF 模型后应会看到编辑器窗口中的 JSON。 请注意，您还可以预览中实时 3D 查看器使用的模型通过右键单击文件名称并选择"glTF:预览三维模型"右键单击菜单命令快捷方式。 

### <a name="adding-the-triggers"></a>添加触发器
动画触发器被添加到 glTF 模型使用动画映射扩展的 JSON。 动画映射扩展公开所述[此处 GitHub 上](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)(注意：这是一个草稿扩展。） 将扩展添加到你模型只是滚动到编辑器中 glTF 文件的末尾，并将"extensionsUsed"和"扩展"块添加到你的文件，如果它们尚不存在。 在"extensionsUsed"部分中，你将添加到"EXT_animation_map"扩展的引用，并在"扩展"块中，你将添加将映射到模型中的动画。

如所述[规范中](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)定义是什么触发动画的动画索引作为数组的"动画"列表上使用"语义"字符串。 在下面的示例中，我们已指定动画播放时用户观望对象：

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
下面的动画触发器语义受支持的主 Windows Mixed Reality。  
* "始终":不断循环播放动画
* "保持":循环期间的整个持续时间被获取一个对象。
* "看":循环时要查看对象
* "邻近":闭合靠近对象查看器时
* "指向":闭合用户指向一个对象时

### <a name="saving-and-exporting"></a>保存和导出
一次到 glTF 模型可以将其保存为 glTF 直接进行了更改，也可以右键单击在编辑器中，选择文件的名称"glTF:将导出到 GLB （二进制文件）"改为导出.glb。 

### <a name="restrictions"></a>限制
动画不能超过 20 分钟，并且不能包含多个 36000 关键帧 （每秒 30 帧在 20 分钟）。 此外时使用基于 morph 目标动画不超过 8192 morph 目标顶点或更少。 超过这些计数将能经过动画处理的资产不支持在 Windows Mixed Reality 主页中。 

|功能|最多|
|-----|-----|
|Duration|20 分钟|
|关键帧|36,000| 
|Morph 目标顶点|8192|

## <a name="gltf-implementation-notes"></a>glTF 实现说明
Windows MR 不支持使用负刻度的翻转几何图形。 具有负的刻度将可能会导致视觉效果的几何图形。

GlTF 资产必须指向使用场景属性来呈现由 Windows MR 的默认场景。 早于 Windows MR glTF 加载程序的另外[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)**需要**访问器：
* 必须具有最小值和最大值。
* 标量类型必须为 componentType UNSIGNED_SHORT (5123) 或 UNSIGNED_INT (5125)。
* 类型 VEC2 和 VEC3 必须 componentType FLOAT (5126)。

以下的 material 属性是核心 glTF 2.0 规范中使用，但不是必需的：
* baseColorFactor，metallicFactor roughnessFactor
* baseColorTexture:必须指向存储在 dds 纹理。
* emissiveTexture:必须指向存储在 dds 纹理。
* emissiveFactor
* alphaMode

以下材料属性会忽略从核心规范：
* 所有多 Uv
* metalRoughnessTexture:必须改用下面定义的 Microsoft 优化纹理装箱
* normalTexture:必须改用下面定义的 Microsoft 优化纹理装箱
* normalScale
* occlusionTexture:必须改用下面定义的 Microsoft 优化纹理装箱
* occlusionStrength

Windows MR 不支持基元模式线条和点。 

仅单个 UV 顶点属性是受支持。

## <a name="additional-resources"></a>其他资源
* [glTF 导出程序和转换器](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 规范](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [混合现实纹理打包扩展规范的 PC](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 混合现实纹理打包扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 纹理 glTF 扩展规范](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>请参阅

* [实现 3D 应用启动器（UWP 应用）](implementing-3d-app-launchers.md)
* [实现 3D 应用启动器（Win32 应用）](implementing-3d-app-launchers-win32.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
