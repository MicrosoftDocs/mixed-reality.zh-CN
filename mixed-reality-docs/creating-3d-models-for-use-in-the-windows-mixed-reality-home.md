---
title: 创建用于主页的3D 模型
description: 用于在 HoloLens 和沉浸式（VR）耳机上的 Windows Mixed Reality 主页中使用的三维模型的资产要求和创作指南。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D，建模，建模指南，资产要求，创作准则，启动器，3D 启动器，纹理，材料，复杂性，三角形，网格，多边形，polycount，限制
ms.openlocfilehash: 536fd9bc2002d679ee3bf73d5c906b84c51e5d46
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926581"
---
# <a name="create-3d-models-for-use-in-the-home"></a>创建用于主页的3D 模型

[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。 你可以为 Windows Mixed Reality 耳机设计应用程序，将[3d 模型用作应用启动器](implementing-3d-app-launchers.md)，并允许[将3d 深层链接放入应用内的 Windows Mixed Reality 主页](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)。 本文概述了用于创建与 Windows Mixed Reality 主页兼容的3D 模型的准则。

## <a name="asset-requirements-overview"></a>资产要求概述
为 Windows Mixed Reality 创建3D 模型时，所有资产都必须满足一些要求： 
1. [导出](#exporting-models)-必须以 glb 文件格式（二进制 glTF）传送资产
2. [建模](#modeling-guidelines)-资产必须小于10000个三角形，每个 LOD 不超过64个节点和 32 submeshes
3. [材料](#material-guidelines)-纹理不能大于 4096 x 4096，并且最小 mip 映射在任一维度上都不应大于4
4. [动画](#animation-guidelines)-动画的长度不能超过20分钟 30 FPS （36000关键帧），并且必须包含 < = 8192 变形目标顶点
5. [优化](#optimizations)-资产应使用[WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)进行优化。 这是**WINDOWS 操作系统版本 < = 1709 必需**的，建议在 windows 操作系统版本 > = 1803 上使用。

本文的其余部分详细介绍了这些要求，并提供了其他指导原则，以确保你的模型与 Windows Mixed Reality 主页良好合作。 

## <a name="detailed-guidance"></a>详细指南

### <a name="exporting-models"></a>导出模型

Windows Mixed Reality 主页需要使用带有嵌入图像和二进制数据的 glb 文件格式来传送3D 资产。 Glb 是 glTF 格式的二进制版本，它是 Khronos 组维护的用于3D 资产交付的版税免费开放标准。 由于 glTF 演变为可互操作的3D 内容的行业标准，因此 Microsoft 将跨 Windows 应用和体验提供格式支持。 如果尚未创建 glTF 资产，你可以在 glTF 工作组 github 页上找到[受支持的导出程序和转换器的列表](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)。  

### <a name="modeling-guidelines"></a>建模准则

Windows 应使用以下建模准则生成资产，以确保与混合现实主体验兼容。 当你选择的程序中的建模时，请牢记以下建议和限制：
1. 向上轴应设置为 "Y"。
2. 资产应正面朝正 Z 轴 "前进"。
3. 应在场景原点（0，0，0）的地面上构建所有资产
4. 应将工作单元设置为计量和资产，以便能够在全球范围内创作资产
5. 所有网格都不需要组合，但建议在目标为资源受限设备时使用
6. 所有网格应共享1个材料，并且仅将一个纹理集用于整个资产
7. 在0-1 空间中，Uv-11 的布局必须按正方形排列。 即使允许，也应避免使用平铺纹理。
8. 不支持多 Uv-11
9. 不支持双面材料

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形计数和详细级别（LODs）

Windows Mixed Reality home 不支持超过10000个三角形的模型。 建议在导出前三角化网格，以确保它们不超过此计数。 Windows MR 还支持可选几何级别的详细信息（LODs），以确保高性能和高质量的体验。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)将帮助你将模型的3个版本合并为 glb 模型。 Windows 根据模型占用的屏幕实际空间量来确定要显示的 LOD。 仅支持3个 LOD 级别，并提供以下建议的三角形计数：
<br>

|  LOD 级别  |  推荐的三角形计数  |  最大三角形计数 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5000  |  10,000 | 
|  LOD 2 |  2500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>节点计数和子网格限制
Windows Mixed Reality home 不支持每个 LOD 具有超过64个节点或 32 submeshes 的模型。 节点是[glTF 规范](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)中定义场景中对象的概念。 Submeshes 是在对象的网格上的[基元](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)数组中定义的。 

|  功能 |  描述  |  支持的最大值 | 文档 |
|------|------|------|------|
|  节点数 |  GlTF 场景中的对象 |  每 LOD 64 | [这儿](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  所有网格上的基元的总和 |  每 LOD 32 | [这儿](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>材料指导原则

应使用 .PBR 金属粗糙度工作流准备纹理。 首先创建一组完整的纹理，其中包括 Albedo、Normal、封闭、金属和粗糙度。 Windows Mixed Reality 支持的纹理分辨率最高可达4096x4096，但建议你在512x512 中创作。 此外，纹理应以4的倍数编写，因为这是在导出步骤中应用于纹理的压缩格式要求。 最后，在生成 mip maps 或纹理时，最小 mip 必须最大为4x4。
<br>

|  建议的纹理大小  |  最大纹理大小 | 最小 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大4x4|

### <a name="albedo-base-color-map"></a>Albedo （基本颜色）图

没有照明信息的原始颜色。 此地图还包含金属图的 reflectance 和漫射信息（金属地图中为白色）和 insulator （金属图中的黑色）。

### <a name="normal"></a>正常

相切空间正常映射

### <a name="roughness-map"></a>粗糙度图

描述对象的 microsurface。 白色1.0 的黑色0.0 为平滑。 此地图为资产提供了真正描述表面的最多字符，例如划痕、指纹、涂抹、grime 等。

### <a name="ambient-occlusion-map"></a>环境封闭映射

值缩放图，描述封闭像素光线的区域，这些区域会阻塞反射

### <a name="metallic-map"></a>金属图

指示着色器（如果有）。 Raw 金属 = 1.0 白色非金属色 = 0.0 黑色。 可能有一些过渡灰度值，这些值指示了诸如灰尘等原材料的内容，但通常情况下，此地图只应为黑色和白色。

## <a name="optimizations"></a>效果

Windows Mixed Reality 主页在使用自定义扩展定义的核心 glTF 规范之上提供一系列优化。 Windows 版本 < 为1709，并且建议在更高版本的 Windows 上执行这些优化。 可以使用[GitHub 上提供的 Windows Mixed Reality 资产转换器](https://github.com/Microsoft/glTF-Toolkit/releases)轻松优化任何 glTF 2.0 模型。 此工具将执行下面指定的正确纹理打包和优化。 对于常规用法，我们建议使用 WindowsMRAssetConverter，但如果您需要更好地控制体验并想要生成自己的优化管道，则可以参阅下面的详细规范。  

### <a name="materials"></a>资料

若要在混合现实环境中提高资产加载时间，Windows MR 支持根据此部分中定义的纹理打包方案来呈现打包的压缩 DDS 纹理。 使用[MSFT_texture_dds 扩展](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)来引用 DDS 纹理。 强烈建议使用压缩纹理。 

#### <a name="hololens"></a>HoloLens

基于 HoloLens 的混合现实体验预期纹理使用2纹理设置进行打包，使用的封装规范如下：
<br>

|  glTF 属性  |  褐色  |  打包方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Red （R）、绿（G）、蓝（B） | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  法线（RG），粗糙度（B），金属（A） | 


压缩 DDS 纹理时，每个映射上应有以下压缩：
<br>

|  褐色  |  预期压缩 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>沉浸式（VR）耳机

沉浸式（VR）耳机的基于 PC 的 Windows Mixed Reality 体验使用三纹理设置来封装纹理，使用以下封装规范：

##### <a name="windows-os--1803"></a>Windows OS > = 1803

<br>

|  glTF 属性  |  褐色  |  打包方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Red （R）、绿（G）、蓝（B） | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  封闭（R），粗糙度（G），金属（B） | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  正常（RG） | 

压缩 DDS 纹理时，每个映射上应有以下压缩：
<br>

|  褐色  |  预期压缩 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS < = 1709
<br>

|  glTF 属性  |  褐色  |  打包方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Red （R）、绿（G）、蓝（B） | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  粗糙度（R）、金属（G）、封闭（B） | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  正常（RG） | 

压缩 DDS 纹理时，每个映射上应有以下压缩：
<br>

|  褐色  |  预期压缩 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>添加网格 LODs

Windows MR 使用几何节点 LODs 根据屏幕覆盖情况在不同的详细级别中呈现3D 模型。 尽管此功能在技术上并不是必需的，但强烈建议将其用于所有资产。 目前，Windows 支持3个级别的详细信息。 默认 LOD 为0，表示最高质量。 其他 LODs 按顺序编号，例如1、2，并且质量逐渐降低。 [Windows Mixed Reality 资产转换器](https://github.com/Microsoft/glTF-Toolkit/releases)支持生成满足此 LOD 规范的资产，方法是接受多个 glTF 模型并将它们合并到具有有效 LOD 级别的单个资产中。 下表概述了预期的 LOD 排序和三角形目标：
<br>

|  LOD 级别  |  推荐的三角形计数  |  最大三角形计数 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5000  |  10,000 | 
|  LOD 2 |  2500  |  10,000 | 

当使用 LODs 时，始终指定3个 LOD 级别。 缺少 LODs 将导致模型不会意外呈现，因为 LOD 系统会切换到缺少的 LOD 级别。 glTF 2.0 当前不支持 LODs 作为核心规范的一部分，因此应使用[MSFT_LOD 扩展](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)来定义 LODs。

### <a name="screen-coverage"></a>屏幕覆盖范围

LODs 基于每个 LOD 上设置的屏幕覆盖值驱动的系统，在 Windows Mixed Reality 中显示。 当前耗用更大的屏幕空间部分的对象将显示在更高的 LOD 级别。 屏幕覆盖率不是 core glTF 2.0 规范的一部分，必须使用[MSFT_lod 扩展](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)的 "附加" 部分中 MSFT_ScreenCoverage 指定。
<br>

|  LOD 级别  |  建议范围  |  默认范围 | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  0\.5 | 
|  LOD 1 |  低于 50%-20%  |  .2 | 
|  LOD 2 |  低于 20%-1%  |  得出 | 
|  LOD 4  |  低于1%  |  - | 

## <a name="animation-guidelines"></a>动画指导原则

> [!NOTE]
> 此功能已作为[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分添加。 在较早版本的 Windows 上，这些动画将不会播放，但是，如果按照本文中的指南进行创作，它们仍会加载。  

混合现实主页支持在 HoloLens 和沉浸式（VR）耳机上进行动画处理的 glTF 对象。 如果要在模型上触发动画，则需要使用 glTF 格式的动画映射扩展。 此扩展使您可以基于用户在世界中的状态触发 glTF 模型中的动画，例如，当用户接近对象或正在查看动画时触发动画。 如果 glTF 对象具有动画，但没有定义触发器，动画将不会播放。 下面的部分介绍了一个用于将这些触发器添加到任何动画 glTF 对象的工作流。

### <a name="tools"></a>工具
首先，下载以下工具（如果尚未这样做）。 通过这些工具，可以轻松地打开任何 glTF 模型、预览它、进行更改并将其另存为 glTF 或 glb：
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [用于 Visual Studio Code 的 glTF 工具](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>打开和预览模型
首先，通过将 glTF 文件拖到编辑器窗口中，在 VSCode 中打开 glTF 模型。 请注意，如果你有 glb 而不是 glTF 文件，则可以使用已下载的 glTF 工具加载项将其导入 VSCode。 中转到 "视图 > 命令面板"，然后在命令面板中开始键入 "glTF"，并选择 "glTF：从 glb 导入"，这会弹出一个文件选取器，以便你使用将 glb 导入。 

打开 glTF 模型后，应会在编辑器窗口中看到 JSON。 请注意，您还可以使用右键单击文件名称，然后从右键单击菜单中选择 "glTF： Preview 3D 模型" 命令快捷方式，使用在实时三维查看器中预览模型。 

### <a name="adding-the-triggers"></a>添加触发器
动画触发器使用动画映射扩展添加到 glTF 模型 JSON。 此动画地图扩展[在此处在 GitHub 上](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)公开记录（注意：这是一个草稿扩展）。 若要将扩展添加到模型中，只需滚动到编辑器中的 glTF 文件的末尾，并将 "extensionsUsed" 和 "extension" 块添加到文件（如果它们尚不存在）。 在 "extensionsUsed" 部分中，你将添加对 "EXT_animation_map" 扩展的引用，在 "extension" 块中，你将向模型中的动画添加映射。

如[规范中](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)所述，使用 "动画" 列表中的 "语义" 字符串（动画索引数组）定义动画触发器。 在下面的示例中，我们指定了在用户 gazing 对象时要播放的动画：

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
Windows Mixed Reality 主页支持以下动画触发语义。  
* "始终"：不断循环播放动画
* "已保留"：在整个期间内循环对象将被抓取。
* "注视"：在查看对象时循环
* "邻近性"：在查看器接近对象时循环
* "指向"：当用户指向对象时循环

### <a name="saving-and-exporting"></a>保存和导出
对 glTF 模型进行更改后，可以直接将其保存为 glTF，也可以在编辑器中右键单击该文件的名称，并选择 "glTF： Export to GLB （二进制文件）"，以改为导出 GLB。 

### <a name="restrictions"></a>限制
动画的长度不能超过20分钟，并且不能包含超过36000个关键帧（20分钟，30 FPS）。 此外，当使用基于平滑目标的动画时，不能超过8192的变形目标顶点。 超过这些计数将导致动态资产在 Windows Mixed Reality 主页中不受支持。 

|功能|最多|
|-----|-----|
|Duration|20 minutes|
|关键帧|36000| 
|变形目标顶点|8192|

## <a name="gltf-implementation-notes"></a>glTF 实现注释
Windows MR 不支持使用负值刻度翻转几何。 具有负刻度的几何可能会导致视觉对象。

GlTF 资产必须指向使用 Windows MR 呈现的场景属性的默认场景。 此外，windows [10 2018 年4月更新](release-notes-april-2018.md)之前的 Windows MR glTF 加载程序**需要**访问器：
* 必须具有最小值和最大值。
* 类型标量必须是 componentType UNSIGNED_SHORT （5123）或 UNSIGNED_INT （5125）。
* 类型 VEC2 和 VEC3 必须为 componentType FLOAT （5126）。

以下材料属性用于核心 glTF 2.0 规范，但不是必需的：
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture：必须指向 dds 中存储的纹理。
* emissiveTexture：必须指向 dds 中存储的纹理。
* emissiveFactor
* alphaMode

以下材料属性将从核心规范中忽略：
* 所有多 Uv-11
* metalRoughnessTexture：必须改用下面定义的 Microsoft 优化纹理包
* normalTexture：必须改用下面定义的 Microsoft 优化纹理包
* normalScale
* occlusionTexture：必须改用下面定义的 Microsoft 优化纹理包
* occlusionStrength

Windows MR 不支持基元模式行和点。 

仅支持单个 UV 顶点属性。

## <a name="additional-resources"></a>其他资源
* [glTF 导出程序和转换器](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF 工具包](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 规范](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [电脑混合现实纹理封装扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 混合现实纹理封装扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 纹理 glTF 扩展规范](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>另请参阅

* [实现 3D 应用启动器（UWP 应用）](implementing-3d-app-launchers.md)
* [实现 3D 应用启动器（Win32 应用）](implementing-3d-app-launchers-win32.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
