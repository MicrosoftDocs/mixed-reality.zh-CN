---
title: Unreal 中的空间音频
description: Unreal 引擎的空间音频插件概述。
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像, 游戏开发
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446788"
---
# <a name="spatial-audio-in-unreal"></a>Unreal 中的空间音频

## <a name="overview"></a>概述

与视觉不同，人类能听到 360 度环绕声。 空间音效模拟人类听觉的工作方式，从而提供识别世界空间中的声音位置所需的提示。 通过在你的混合现实应用程序中添加空间音效，可以提高用户所体验的沉浸感程度。  

高质量的空间音效处理比较复杂，因此，HoloLens 2 附带了用于处理这些声音对象的专用硬件。  在使用此硬件处理支持之前，需要在 Unreal 项目中安装 MicrosoftSpatialSound 插件。 本文将逐步指导你完成该插件的安装和配置，并且将提供在 Unreal 引擎中使用空间音效的更多相关深度资源。 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>安装 Microsoft 空间音效插件 

向项目添加空间音效的第一步是安装 Microsoft 空间音效插件，可通过以下方式找到该插件： 

1. 单击“编辑”>“插件”，然后在搜索框中搜索“MicrosoftSpatialSound” 。 
2. 在 MicrosoftSpatialSound 插件中选择“已启用”复选框 。 
3. 从插件页面选择“立即重启”来重启 Unreal 编辑器。 

> [!NOTE]
> 如果尚未安装 Microsoft Windows Mixed Reality 和 HoloLens 插件，需要按照我们 Unreal 教程系列[初始化你的项目](unreal-uxt-ch2.md)部分中的说明进行安装  。

![Unreal 空间音频插件](images/unreal-spatial-audio-img-01.png)

待编辑器重启后，你的项目就已就绪了！


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>设置 HoloLens 2 平台的空间化插件
配置空间化插件是以每个平台为基础进行的。  可以通过以下方式为 HoloLens 2 启用 Microsoft 空间音效插件：
1. 选择“编辑”>“项目设置”，滚动到“平台”，然后单击“HoloLens”  。
2. 展开“音频”属性，并将“空间化插件”字段设置为“Microsoft 空间音效”  。

![HoloLens 平台的空间化插件](images/unreal-spatial-audio-img-02.png)

如果要在台式电脑上的 Unreal 编辑器中预览应用程序，则需要针对 Windows 平台重复执行上述步骤：

![Windows 平台的空间化插件](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>在工作站上启用空间音频
空间音频在 Windows 桌面版上默认处于禁用状态。 可以通过以下方式启用它：
* 右键单击任务栏中的“音量”图标。 
    + 选择“空间音效”->“用于耳机的 Windows Sonic”以获得在 HoloLens 2 上所听到的声音的最佳呈现效果。

![空间化插件](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>仅当你计划在 Unreal 编辑器中测试项目时才需要此设置。

## <a name="creating-attenuation-objects"></a>创建衰减对象
安装并配置了必要插件后：
1. 在“放置参与者”窗口中搜索“环境声”参与者，并将它拖到“场景”窗口中  。

![添加“环境声”参与者](images/unreal-spatial-audio-img-07.png)

2. 将“环境声”参与者设置为场景中可视元素的子元素。 
    * 默认情况下，“环境声”参与者没有任何可视表示形式，因此你只能听到从它在场景中所处的位置传来的声音。 将它附加到可视元素后，就可以像对待任何其他资产一样查看和移动此参与者。

3.  右键单击“内容浏览器”，然后选择“创建高级资产”->“声音”->“声音衰减” ：

![创建声音衰减资产](images/unreal-spatial-audio-img-06.png)

4. 右键单击“内容浏览器”窗口中的“声音衰减”资产，然后选择“编辑”选项以打开属性窗口  。
    * 将“空间化方法”切换到“双声道” 。

![设置空间化方法](images/unreal-spatial-audio-img-03.png)

5. 选择“环境声”参与者，然后向下滚动到“详细信息”面板中的“衰减”部分  。 
    * 将“衰减设置”属性设置为你创建的声音衰减资产 。

![设置衰减设置](images/unreal-spatial-audio-img-08.png)

6. 通过以下方法设置要附加到“环境声”参与者的声音资产：更新环境声参与者的“声音”属性来指定要使用的 SoundAsset 文件 。

![设置声音资产](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> SoundAsset 文件需要为单声道，这样才能使用 Microsoft 空间音效插件对它进行空间化处理。 可以通过将鼠标悬停在“内容浏览器”窗口中的资产上来找到声音文件属性，如以下屏幕截图中所示。

![新的声音衰减资产](images/unreal-spatial-audio-img-10.png)

在完成以上所有配置后，即可使用 HoloLens 2 上的专用硬件卸载支持对环境声进行空间化处理。

## <a name="configuring-objects-for-spatialization"></a>配置空间化对象
使用空间音频意味着你需要管理声音在虚拟环境中的行为方式。 你的主要目标是创建声音对象，这些对象的特征是当用户靠近时声音会更大，而当用户远离时声音会更小。 这称为声音衰减，使声音听起来就像是被放在一个固定地点一样。

所有衰减对象都有针对以下各项的可修改设置：
* 距离
* 空间化
* 空气吸收
* 侦听器聚焦
* 混响发送
* 封闭

[Unreal 中的声音衰减](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)提供了有关这些主题的详细信息和实现细节。


## <a name="see-also"></a>另请参阅
* [空间音效](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [空间音效设计](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR 空间 220：空间音效](https://docs.microsoft.com/windows/mixed-reality/holograms-220)