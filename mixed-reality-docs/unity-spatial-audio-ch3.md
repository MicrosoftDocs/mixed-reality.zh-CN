---
title: 空间音频教程-3。 从视频 Spatializing 音频
description: 将视频资产导入到 Unity 项目，并 spatialize 视频中的音频。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合现实、unity、教程、hololens2、空间音频
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182744"
---
# <a name="spatializing-audio-from-a-video"></a>从视频 Spatializing 音频
在 HoloLens 2 Unity 教程的 "空间音频" 模块的第三章中，你将：
* 导入视频并添加视频播放器
* 播放视频到 quadrangle
* 将音频从视频路由到 quadrangle，并 spatialize 音频

## <a name="import-a-video-and-add-a-video-player"></a>导入视频并添加视频播放器

将视频文件拖到 Unity 项目的 "**项目**" 窗格中。 可以从空间音频示例项目使用[此视频](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true)。

![包含视频的资产文件夹](images/spatial-audio/assets-folder-with-video.png)

调整视频剪辑的质量设置可以确保在 HoloLens 2 上顺畅地播放。 单击 "**项目**" 窗格中的视频文件。 然后在视频文件的 "**检查器**" 窗格中，覆盖 Windows 应用商店应用的设置，并执行以下操作：
* 启用**转码**
* 将**编解码器**设置为 H264
* 将**比特率模式**设置为低
* 将**空间质量**设置为中等空间质量

完成这些调整后，视频文件的 "**检查器**" 窗格将如下所示：

![视频属性窗格](images/spatial-audio/video-property-pane.png)

接下来 **，通过右键单击 "** **层次结构**" 窗格并选择 "**视频 > 视频播放器**：

![层次结构中的视频播放器](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>播放视频到 quadrangle
**视频播放器**对象需要一个纹理游戏对象用于呈现视频。 首先 **，通过**右键单击 "**层次结构**" 窗格并选择 " **3d 对象-> 四个**：

![向层次结构添加四个](images/spatial-audio/add-quad-to-hierarchy.png)

若要确保在应用程序启动时**四**个显示在用户前面，请将**4**的 "**位置**" 属性设置为（0，0，2），并将 "**小数位数**" 属性设置为（1.28，0.72，1）。 进行这些更改后，**四**个 "**检查器**" 窗格中的 "**转换**" 组件将如下所示：

![四向转换](images/spatial-audio/quad-transform.png)

若要为**四**个视频着色，请创建新的**渲染纹理**。 在 "**项目**" 窗格中，右键单击并选择 "**创建-> 渲染纹理**"：

![创建着色纹理](images/spatial-audio/create-render-texture.png)

在**呈现纹理**的 "**检查器**" 窗格中，将 " **Size** " 属性设置为与视频的 "1280x720 的本机分辨率" 匹配。 然后，若要确保在 HoloLens 2 上呈现良好的性能，请将**深度缓冲区**属性设置为**至少16位深度**。 这些设置之后，**呈现纹理**的 "**检查器**" 窗格将如下所示：

![呈现纹理属性](images/spatial-audio/render-texture-properties.png)

接下来，使用新的**呈现纹理**作为**四**个的纹理：
1. 将**呈现纹理**从 "**项目**" 窗格拖到**层次结构**中的**四**个
2. 若要在 HoloLens 2 上确保良好的性能，请在 "**四**个**检查器**" 窗格中选择**混合现实工具包标准着色器**。

在这些设置中，**四**个 "**检查器**" 窗格中的**纹理**组件如下所示：

![四纹理属性](images/spatial-audio/quad-texture-properties.png)

若要设置新的**视频播放器**并**渲染纹理**以播放视频剪辑，请打开**视频播放器**的 "**检查器**" 窗格，并执行以下操作：
* 将**视频剪辑**属性设置为视频文件
* 选中 "**循环**" 复选框
* 将**目标纹理**设置为新的渲染纹理

**视频播放器**的 "**检查器**" 窗格现在将如下所示：

![视频播放器属性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialize 视频中的音频
在**四**个 "**检查器**" 窗格中，创建要将音频从视频路由到的**音频源**：
* 单击窗格底部的 "**添加组件**"
* 添加**音频源**

然后，在 "**音频源**：
* 将**输出**设置为混音器
* 选中 " **Spatialize** " 框
* 将**空间混合**滑块移动到1（3d）

进行这些更改后，**四**个 "**检查器**" 窗格中的 "**音频源**" 组件会如下所示：

![四核音频源检查器](images/spatial-audio/quad-audio-source-inspector.png)

若要将**视频播放器**设置为将音频源路由到**四**个视频**源**，请打开**视频播放器**的**检查器**窗格，并执行以下操作：
* 将**音频输出模式**设置为 "音频源"
* 将 "**音频源**" 属性设置为四

进行这些更改后，**视频播放器**的 "**检查器**" 窗格将如下所示：

![视频播放器设置音频源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>后续步骤
在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。 你将看到并听到视频，视频中的音频将为 spatialized。

继续第[4 章](unity-spatial-audio-ch4.md)，以便在运行时使用按钮来启用和禁用 spatialization。

