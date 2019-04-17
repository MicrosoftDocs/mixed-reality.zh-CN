---
title: 案例研究-构建 HoloSketch、 空间布局和 HoloLens 的素描应用的用户体验
description: HoloSketch 是一个设备上的空间布局和素描 HoloLens 以帮助您构建全息版体验的工具的用户体验。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch，HoloLens，Windows Mixed Reality，素描。 应用程序
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591866"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>案例研究-构建 HoloSketch、 空间布局和 HoloLens 的素描应用的用户体验

HoloSketch 是一个设备上的空间布局和素描 HoloLens 以帮助您构建全息版体验的工具的用户体验。 HoloSketch 配合配对的蓝牙键盘和鼠标，以及手势和语音命令。 HoloSketch 旨在提供简单的 UX 布局工具，用于快速可视化效果和迭代。

![HoloSketch:空间布局和 HoloLens 的素描应用的用户体验。](images/holosketch-image-01-640px.png)<br>
*HoloSketch： 空间布局和 HoloLens 的素描应用的用户体验*

![以进行快速可视化和迭代一个简单的 UX 布局工具。](images/holosketch-image-02.png)<br>
*一个简单的 UX 布局工具以进行快速可视化和迭代*

## <a name="features"></a>功能

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>用于快速研究和规模原型设计的基元

![使用基元形状](images/holosketch-primitives-giphy.gif)

对于快速 massing 研究和规模原型设计使用基元的形状。

### <a name="import-objects-through-onedrive"></a>通过 OneDrive 导入对象

![导入对象](images/holosketch-importobjects-giphy.gif)

PNG/JPG 图像或三维 FBX 对象导入 （需要在 Unity 中的打包） 到通过 OneDrive 的混合的现实空间。

### <a name="manipulate-objects"></a>操作对象

![操作对象](images/manipulate-objects-640px.jpg)

操作使用熟悉的三维对象接口的对象 （移动/旋转/缩放）。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>蓝牙、 鼠标/键盘、 手势和语音命令

![支持蓝牙](images/supports-bluetooth-640px.jpg)

HoloSketch 支持蓝牙鼠标/键盘、 手势和语音命令。

## <a name="background"></a>后台

### <a name="importance-of-experiencing-your-design-in-the-device"></a>遇到你的设备中的设计的重要性

在设计时的内容对于 HoloLens，务必体验你的设备中的设计。 混合的现实应用程序设计的最大挑战之一是很难获得的规模、 位置和深度，尤其是通过传统的 2D 草图。

### <a name="cost-of-2d-based-communication"></a>2D 的成本的通信

若要有效地传达 UX 流和向其他人的方案，设计器可能最终会花费大量时间来创建使用传统的 2D 工具，例如 Illustrator、 Photoshop 和 PowerPoint 的资产。 这些 2D 设计通常需要额外的工作量才能将其转换到 3D。 一些观点在会丢失这种转换从二维到三维物体。

### <a name="complex-deployment-process"></a>复杂的部署过程

由于混合的现实是为我们新的画布，它会按其性质涉及大量设计迭代和试用和错误。 对于不熟悉 Unity 和 Visual Studio 等工具的设计器，并不容易 HoloLens 一起添加某项。 通常，您需要经历以下过程以查看您的设备中的二维/三维作品。 这是快速循环访问的想法和方案的设计器的大障碍。

![复杂的部署过程](images/holosketch-image-03-1000px.png)<br>
*部署过程*

### <a name="simplified-process-with-holosketch"></a>使用 HoloSketch 简化的处理

使用 HoloSketch，我们想要简化此过程不涉及开发工具和设备门户配对。 使用 OneDrive，用户可以轻松地将二维/三维资产置于 HoloLens。

![使用 HoloSketch 简化的处理](images/holosketch-image-04-1000px.png)<br>
*使用 HoloSketch 简化的处理*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>鼓励三维设计思维和解决方案

我们认为此工具会使设计人员有机会了解真正三维空间中的解决方案并不会停滞在 2D。 它们无需考虑为它们的 UI 创建三维背景，由于背景是在 Hololens 的情况下现实世界。 HoloSketch 打开设计器，可轻松地在 Hololens 上浏览 3D 设计一种方法。

## <a name="get-started"></a>入门

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>如何导入 HoloSketch 2D 图像 (JPG/PNG)

* 将 JPG/PNG 图像上传到你的 OneDrive 文件夹文档/HoloSketch。
* 在中 HoloSketch OneDrive 菜单中，您将能够选择并将图像放在环境中。

![导入的 2D 图像](images/import-2d-images-1000px.jpg)<br>
*导入图像和三维对象通过 OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>如何导入 HoloSketch 三维对象

上传到 OneDrive 文件夹，请按照以下步骤来打包到 Unity 资产捆绑三维对象。 使用此过程可以从 Maya、 影院 4d 和 Microsoft 画图 3D 等的 3D 软件导 FBX/OBJ 文件。

>[!IMPORTANT]
>目前，使用 Unity 版本 5.4.5f1 支持资产捆绑包创建。

1. 下载并打开 Unity 项目[AssetBunlder_Unity](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。 此 Unity 项目包括用于捆绑包资产生成的脚本。
2. 创建新的 GameObject。
3. 名称基于内容的 GameObject。
4. 在检查器窗格中，单击添加组件并添加盒状碰撞体。 

   ![在检查器窗格中，单击添加组件，并添加盒状碰撞体](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在检查器窗格中，单击添加组件，并添加盒状碰撞体 #2](images/holosketch-10b-assetbundles-1000px.png)

5. 通过将其拖到项目面板中，导入三维 FBX 文件。
6. 将对象拖到层次结构面板**在新的 GameObject**。

   ![将对象拖到层次结构面板下新的 GameObject](images/holosketch-12-assetbundles-1000px.png)

7. 调整碰撞体维度，如果与该对象不匹配。 旋转对象面临着**z 轴**。

   ![调整碰撞体维度，如果与该对象不匹配。](images/holosketch-13-assetbundles-1000px.png)

8. 将对象从层次结构面板拖到项目面板**使其预设**。
9. 在检查器面板的底部，单击下拉列表、 创建和分配新的唯一名称。 以下示例演示如何添加并分配 brownchair AssetBundle 名称。 

   ![在检查器面板的底部，单击下拉列表中并分配新的唯一名称。](images/holosketch-14-assetbundles-1000px.png)

10. 为模型对象准备缩略图。 
   ![将图像拖到项目面板并将分配的对象使用的名称。](images/holosketch-15-assetbundles-1000px.png)

11. 在 Unity 项目的资产文件夹下创建名为 Assetbundles 的文件夹。

12. 从资产菜单上，选择生成 AssetBundles 生成文件。 
   ![从资产菜单上，选择生成 AssetBundles 生成文件。](images/holosketch-15a-assetbundles.png)


13. **将生成的文件上传到 OneDrive 上的 /Files/Documents/HoloSketch 文件夹。** 上传仅 asset_unique_name 文件。 不需要上传清单文件或 AssetBundles 文件。 <br>
![将文件添加到文件/文档/HoloSketch/文件夹](images/holosketch-onedriveupload-1000px.png)
![您将看到 HoloSketch 的 OneDrive 菜单中添加了三维对象](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>如何操作的对象

HoloSketch 支持 3D 软件中广泛使用的传统接口。 可以使用移动、 旋转、 缩放手势和鼠标的对象。 您可以快速使用语音或键盘的不同模式之间切换。

### <a name="object-manipulation-modes"></a>对象操作模式

![如何操作的对象](images/holosketch-image-06-1000px.png)<br>
*如何操作的对象*

### <a name="contextual-and-tool-belt-menus"></a>上下文和工具腰带菜单

**使用上下文菜单**

双精度敲击打开上下文菜单。 

菜单项：
* **布局图面：** 这是一个三维网格系统布局的可能多个对象，并管理它们作为一个组。 以无线方式-双击布局图面，将对象添加到它。
* **基元层：** 用于多维数据集、 球体、 圆柱体和圆锥 massing 研究。
* **OneDrive:** 打开 OneDrive 菜单导入的对象。
* **帮助：** 显示帮助屏幕。

![上下文菜单](images/holosketch-image-07.png)<br>
*上下文菜单*

**使用工具腰带菜单**

移动、 旋转、 缩放，保存和加载场景可从工具腰带菜单。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>使用键盘、 手势和语音命令

![键盘、 手势和语音命令](images/holosketch-image-08-1000px.png)<br>
*键盘、 笔势和语音命令*

## <a name="download-the-app"></a>下载应用

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">下载并安装 HoloSketch 应用免费从 Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>已知问题
* 目前资产捆绑包创建支持**Unity 版本 5.4.5f1。**
* 具体取决于你的 OneDrive 中的数据量，该应用程序可能会出现像它已停止加载 OneDrive 内容时
* 目前，保存并加载功能仅支持基元对象
* 文本、 声音、 视频和照片菜单处于禁用状态的上下文菜单上
* 工具腰带菜单上的 Play 按钮清除操作 gizmos 请

## <a name="sharing-your-sketches"></a>共享你草图

您可以使用视频录制中的功能 HoloLens 通过说你好，小娜启动/停止录制。 按向上/向下键在一起以拍摄照片你草图的卷。

## <a name="about-the-authors"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon Park</b><br>UX 设计人员 @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>开发人员 @Microsoft</td>
</tr>
</table> 
