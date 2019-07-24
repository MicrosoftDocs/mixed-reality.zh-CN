---
title: 案例研究-为 HoloLens 构建 HoloSketch、空间布局和 UX 草绘应用
description: HoloSketch 是一种设备上的空间布局和适用于 HoloLens 的 UX 草图工具, 用于帮助构建全息体验。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, 草绘, 应用
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524547"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>案例研究-为 HoloLens 构建 HoloSketch、空间布局和 UX 草绘应用

HoloSketch 是一种设备上的空间布局和适用于 HoloLens 的 UX 草图工具, 用于帮助构建全息体验。 HoloSketch 适用于配对的蓝牙键盘和鼠标以及笔势和语音命令。 HoloSketch 的目的是提供一个简单的 UX 布局工具, 用于快速可视化和迭代。

![HoloSketch:用于 HoloLens 的空间布局和 UX 草绘应用。](images/holosketch-image-01-640px.png)<br>
*HoloSketch: 用于 HoloLens 的空间布局和 UX 草绘应用*

![用于快速可视化和迭代的简单 UX 布局工具。](images/holosketch-image-02.png)<br>
*简单的 UX 布局工具, 用于快速可视化和迭代*

## <a name="features"></a>功能

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>用于快速研究和规模原型构建的基元

![使用基元形状](images/holosketch-primitives-giphy.gif)

将基元形状用于快速 massing 研究和规模原型设计。

### <a name="import-objects-through-onedrive"></a>通过 OneDrive 导入对象

![导入对象](images/holosketch-importobjects-giphy.gif)

通过 OneDrive 将 PNG/JPG 图像或 3D FBX 对象 (需要在 Unity 中打包) 导入到混合现实空间。

### <a name="manipulate-objects"></a>操作对象

![操作对象](images/manipulate-objects-640px.jpg)

使用熟悉的3D 对象接口操作对象 (移动/旋转/缩放)。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>蓝牙、鼠标/键盘、笔势和语音命令

![支持蓝牙](images/supports-bluetooth-640px.jpg)

HoloSketch 支持蓝牙鼠标/键盘、笔势和语音命令。

## <a name="background"></a>后台

### <a name="importance-of-experiencing-your-design-in-the-device"></a>在设备中体验设计的重要性

为 HoloLens 设计内容时, 在设备中体验设计很重要。 混合现实应用程序设计面临的最大挑战之一是很难理解规模、位置和深度, 尤其是通过传统的2D 草图。

### <a name="cost-of-2d-based-communication"></a>基于2D 的通信的成本

为了有效地向他人传达 UX 流和方案, 设计人员可能会花费大量时间, 使用传统的2D 工具 (例如 Illustrator、Photoshop 和 PowerPoint) 来创建资产。 这些2D 设计通常需要额外的精力才能将其转换为三维。 从2D 到3D 的转换中, 一些想法会丢失。

### <a name="complex-deployment-process"></a>复杂的部署过程

由于混合现实是我们的新画布, 因此它的本质涉及到许多设计迭代和试用和错误。 对于不熟悉 Unity 和 Visual Studio 等工具的设计人员, 在 HoloLens 中将某些内容组合在一起并不容易。 通常, 您必须完成以下过程才能在设备中查看您的 2D/3D 插图。 这是一种非常大的障碍, 设计人员能够快速循环访问创意和方案。

![复杂的部署过程](images/holosketch-image-03-1000px.png)<br>
*部署过程*

### <a name="simplified-process-with-holosketch"></a>简化了 HoloSketch 的过程

通过 HoloSketch, 我们想要简化此过程, 而不涉及开发工具和设备门户配对。 使用 OneDrive, 用户可以轻松地将 2D/3D 资产置于 HoloLens 中。

![简化了 HoloSketch 的过程](images/holosketch-image-04-1000px.png)<br>
*简化了 HoloSketch 的过程*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>鼓励三维设计思想和解决方案

我们认为, 此工具可让设计人员在真正的三维空间中探索解决方案, 而不是在2D 中。 他们无需考虑为 UI 创建三维背景, 因为在这种情况下, 在 Hololens 情况下, 背景是真实世界。 HoloSketch 打开了一种方法, 使设计人员能够轻松地在 Hololens 上浏览3D 设计。

## <a name="get-started"></a>入门

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>如何将二维图像 (JPG/PNG) 导入 HoloSketch

* 将 JPG/PNG 图像上传到 OneDrive 文件夹的文档/HoloSketch。
* 在 HoloSketch 的 OneDrive 菜单中, 可以选择映像并将其放置在环境中。

![导入2D 图像](images/import-2d-images-1000px.jpg)<br>
*通过 OneDrive 导入图像和3D 对象*

### <a name="how-to-import-3d-objects-into-holosketch"></a>如何将3D 对象导入 HoloSketch

在上传到 OneDrive 文件夹之前, 请按照下面的步骤将3D 对象打包到 Unity 资产包。 使用此过程可以从3D 软件 (如 Maya、电影院4D 和 Microsoft 画图 3D) 导入 FBX/OBJ 文件。

>[!IMPORTANT]
>目前, Unity 版本第5.4.5 节 f1 支持创建资产包。

1. 下载并打开 Unity 项目["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。 此 Unity 项目包含捆绑资产生成的脚本。
2. 创建新的 GameObject。
3. 基于内容命名 GameObject。
4. 在检查器面板中, 单击 "添加组件" 并添加 "Box 碰撞器"。 

   ![在检查器面板中, 单击 "添加组件" 并添加 "Box 碰撞器"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在检查器面板中, 单击 "添加组件" 并添加 "Box 碰撞器" #2](images/holosketch-10b-assetbundles-1000px.png)

5. 通过将 3D FBX 文件拖到 "项目" 面板中, 将其导入。
6. 将对象拖到**新 GameObject 下**的 "层次结构" 面板中。

   ![将对象拖到新 GameObject 下的 "层次结构" 面板中。](images/holosketch-12-assetbundles-1000px.png)

7. 如果碰撞器维度与对象不匹配, 则调整它。 将对象旋转为面朝**Z 轴**。

   ![如果它与对象不匹配, 则调整碰撞器维度。](images/holosketch-13-assetbundles-1000px.png)

8. 将对象从 "层次结构" 面板拖到 "项目" 面板,**使其 prefab**。
9. 在检查器面板的底部, 单击下拉列表, 创建并分配一个新的唯一名称。 下面的示例演示如何添加 "brownchair" 并将其分配给 AssetBundle 名称。 

   ![在检查器面板的底部, 单击下拉列表并分配一个新的唯一名称。](images/holosketch-14-assetbundles-1000px.png)

10. 为模型对象准备缩略图。 
   ![将一个图像拖到 "项目" 面板中, 并分配用于该对象的名称。](images/holosketch-15-assetbundles-1000px.png)

11. 在 Unity 项目的 "资产" 文件夹下创建一个名为 "Assetbundles" 的文件夹。

12. 从 "资产" 菜单中选择 "生成 AssetBundles" 以生成文件。 
   ![从 "资产" 菜单中选择 "生成 AssetBundles" 以生成文件。](images/holosketch-15a-assetbundles.png)


13. **将生成的文件上传到 OneDrive 上的/Files/Documents/HoloSketch 文件夹。** 仅上传 asset_unique_name 文件。 不需要上传清单文件或 AssetBundles 文件。 <br>
![将文件添加到文件/文档/HoloSketch/](images/holosketch-onedriveupload-1000px.png)
文件夹![在 HoloSketch 的 OneDrive 菜单中可以看到添加的3d 对象](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>如何操作对象

HoloSketch 支持3D 软件广泛使用的传统接口。 您可以使用 "移动"、"旋转"、"用手势和鼠标缩放对象"。 您可以通过语音或键盘在不同模式之间快速切换。

### <a name="object-manipulation-modes"></a>对象操作模式

![如何操作对象](images/holosketch-image-06-1000px.png)<br>
*如何操作对象*

### <a name="contextual-and-tool-belt-menus"></a>上下文和工具皮带菜单

**使用上下文菜单**

双击以打开上下文菜单。 

菜单项:
* **布局图面:** 这是一个三维网格系统, 你可以在其中布局多个对象并将其作为一个组进行管理。 双击布局面以向其中添加对象。
* **上述**使用多维数据集、球体、圆柱和圆锥进行 massing 研究。
* **Business**打开 OneDrive 菜单以导入对象。
* **帮助：** 显示帮助屏幕。

![上下文菜单](images/holosketch-image-07.png)<br>
*上下文菜单*

**使用工具皮带菜单**

可从 "工具" 菜单使用 "移动"、"旋转"、"缩放"、"保存" 和 "加载" 场景。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>使用键盘、笔势和语音命令

![键盘、手势和语音命令](images/holosketch-image-08-1000px.png)<br>
*键盘、笔势和语音命令*

## <a name="download-the-app"></a>下载应用

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">从 Microsoft Store 免费下载并安装 HoloSketch 应用</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>已知问题
* **Unity 版本第5.4.5 节 f1**支持当前创建的资产包。
* 根据 OneDrive 中的数据量, 应用可能看起来就像在加载 OneDrive 内容时已停止
* 目前, 保存和加载功能仅支持基元对象
* 在上下文菜单上禁用文本、声音、视频和照片菜单
* 工具皮带菜单上的 "播放" 按钮将清除操作 gizmos

## <a name="sharing-your-sketches"></a>共享草图

可以通过说 "你好 Cortana, 开始/停止记录" 来使用 HoloLens 中的视频录制功能。 同时按向上键和向下键, 拍摄草图的图片。

## <a name="about-the-authors"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 停车场</b><br>UX 设计器@Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Sebring</b><br>开发@Microsoft</td>
</tr>
</table> 
