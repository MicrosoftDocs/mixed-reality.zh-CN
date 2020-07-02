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
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="0da28-104">Unreal 中的空间音频</span><span class="sxs-lookup"><span data-stu-id="0da28-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="0da28-105">概述</span><span class="sxs-lookup"><span data-stu-id="0da28-105">Overview</span></span>

<span data-ttu-id="0da28-106">与视觉不同，人类能听到 360 度环绕声。</span><span class="sxs-lookup"><span data-stu-id="0da28-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="0da28-107">空间音效模拟人类听觉的工作方式，从而提供识别世界空间中的声音位置所需的提示。</span><span class="sxs-lookup"><span data-stu-id="0da28-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="0da28-108">通过在你的混合现实应用程序中添加空间音效，可以提高用户所体验的沉浸感程度。</span><span class="sxs-lookup"><span data-stu-id="0da28-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="0da28-109">高质量的空间音效处理比较复杂，因此，HoloLens 2 附带了用于处理这些声音对象的专用硬件。</span><span class="sxs-lookup"><span data-stu-id="0da28-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="0da28-110">在使用此硬件处理支持之前，需要在 Unreal 项目中安装 MicrosoftSpatialSound 插件。</span><span class="sxs-lookup"><span data-stu-id="0da28-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="0da28-111">本文将逐步指导你完成该插件的安装和配置，并且将提供在 Unreal 引擎中使用空间音效的更多相关深度资源。</span><span class="sxs-lookup"><span data-stu-id="0da28-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span> 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="0da28-112">安装 Microsoft 空间音效插件</span><span class="sxs-lookup"><span data-stu-id="0da28-112">Installing the Microsoft Spatial Sound plugin</span></span> 

<span data-ttu-id="0da28-113">向项目添加空间音效的第一步是安装 Microsoft 空间音效插件，可通过以下方式找到该插件：</span><span class="sxs-lookup"><span data-stu-id="0da28-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span> 

1. <span data-ttu-id="0da28-114">单击“编辑”>“插件”，然后在搜索框中搜索“MicrosoftSpatialSound” 。</span><span class="sxs-lookup"><span data-stu-id="0da28-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span> 
2. <span data-ttu-id="0da28-115">在 MicrosoftSpatialSound 插件中选择“已启用”复选框 。</span><span class="sxs-lookup"><span data-stu-id="0da28-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span> 
3. <span data-ttu-id="0da28-116">从插件页面选择“立即重启”来重启 Unreal 编辑器。</span><span class="sxs-lookup"><span data-stu-id="0da28-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span> 

> [!NOTE]
> <span data-ttu-id="0da28-117">如果尚未安装 Microsoft Windows Mixed Reality 和 HoloLens 插件，需要按照我们 Unreal 教程系列[初始化你的项目](unreal-uxt-ch2.md)部分中的说明进行安装  。</span><span class="sxs-lookup"><span data-stu-id="0da28-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Unreal 空间音频插件](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="0da28-119">待编辑器重启后，你的项目就已就绪了！</span><span class="sxs-lookup"><span data-stu-id="0da28-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="0da28-120">设置 HoloLens 2 平台的空间化插件</span><span class="sxs-lookup"><span data-stu-id="0da28-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="0da28-121">配置空间化插件是以每个平台为基础进行的。</span><span class="sxs-lookup"><span data-stu-id="0da28-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="0da28-122">可以通过以下方式为 HoloLens 2 启用 Microsoft 空间音效插件：</span><span class="sxs-lookup"><span data-stu-id="0da28-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="0da28-123">选择“编辑”>“项目设置”，滚动到“平台”，然后单击“HoloLens”  。</span><span class="sxs-lookup"><span data-stu-id="0da28-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="0da28-124">展开“音频”属性，并将“空间化插件”字段设置为“Microsoft 空间音效”  。</span><span class="sxs-lookup"><span data-stu-id="0da28-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![HoloLens 平台的空间化插件](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="0da28-126">如果要在台式电脑上的 Unreal 编辑器中预览应用程序，则需要针对 Windows 平台重复执行上述步骤：</span><span class="sxs-lookup"><span data-stu-id="0da28-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Windows 平台的空间化插件](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="0da28-128">在工作站上启用空间音频</span><span class="sxs-lookup"><span data-stu-id="0da28-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="0da28-129">空间音频在 Windows 桌面版上默认处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="0da28-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="0da28-130">可以通过以下方式启用它：</span><span class="sxs-lookup"><span data-stu-id="0da28-130">You can enable it by:</span></span>
* <span data-ttu-id="0da28-131">右键单击任务栏中的“音量”图标。</span><span class="sxs-lookup"><span data-stu-id="0da28-131">Right-clicking on the **volume** icon in the task bar.</span></span> 
    + <span data-ttu-id="0da28-132">选择“空间音效”->“用于耳机的 Windows Sonic”以获得在 HoloLens 2 上所听到的声音的最佳呈现效果。</span><span class="sxs-lookup"><span data-stu-id="0da28-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![空间化插件](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="0da28-134">仅当你计划在 Unreal 编辑器中测试项目时才需要此设置。</span><span class="sxs-lookup"><span data-stu-id="0da28-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="0da28-135">创建衰减对象</span><span class="sxs-lookup"><span data-stu-id="0da28-135">Creating Attenuation objects</span></span>
<span data-ttu-id="0da28-136">安装并配置了必要插件后：</span><span class="sxs-lookup"><span data-stu-id="0da28-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="0da28-137">在“放置参与者”窗口中搜索“环境声”参与者，并将它拖到“场景”窗口中  。</span><span class="sxs-lookup"><span data-stu-id="0da28-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![添加“环境声”参与者](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="0da28-139">将“环境声”参与者设置为场景中可视元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="0da28-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span> 
    * <span data-ttu-id="0da28-140">默认情况下，“环境声”参与者没有任何可视表示形式，因此你只能听到从它在场景中所处的位置传来的声音。</span><span class="sxs-lookup"><span data-stu-id="0da28-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="0da28-141">将它附加到可视元素后，就可以像对待任何其他资产一样查看和移动此参与者。</span><span class="sxs-lookup"><span data-stu-id="0da28-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="0da28-142">右键单击“内容浏览器”，然后选择“创建高级资产”->“声音”->“声音衰减” ：</span><span class="sxs-lookup"><span data-stu-id="0da28-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![创建声音衰减资产](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="0da28-144">右键单击“内容浏览器”窗口中的“声音衰减”资产，然后选择“编辑”选项以打开属性窗口  。</span><span class="sxs-lookup"><span data-stu-id="0da28-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="0da28-145">将“空间化方法”切换到“双声道” 。</span><span class="sxs-lookup"><span data-stu-id="0da28-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![设置空间化方法](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="0da28-147">选择“环境声”参与者，然后向下滚动到“详细信息”面板中的“衰减”部分  。</span><span class="sxs-lookup"><span data-stu-id="0da28-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span> 
    * <span data-ttu-id="0da28-148">将“衰减设置”属性设置为你创建的声音衰减资产 。</span><span class="sxs-lookup"><span data-stu-id="0da28-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![设置衰减设置](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="0da28-150">通过以下方法设置要附加到“环境声”参与者的声音资产：更新环境声参与者的“声音”属性来指定要使用的 SoundAsset 文件 。</span><span class="sxs-lookup"><span data-stu-id="0da28-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![设置声音资产](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> <span data-ttu-id="0da28-152">SoundAsset 文件需要为单声道，这样才能使用 Microsoft 空间音效插件对它进行空间化处理。</span><span class="sxs-lookup"><span data-stu-id="0da28-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="0da28-153">可以通过将鼠标悬停在“内容浏览器”窗口中的资产上来找到声音文件属性，如以下屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="0da28-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![新的声音衰减资产](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="0da28-155">在完成以上所有配置后，即可使用 HoloLens 2 上的专用硬件卸载支持对环境声进行空间化处理。</span><span class="sxs-lookup"><span data-stu-id="0da28-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="0da28-156">配置空间化对象</span><span class="sxs-lookup"><span data-stu-id="0da28-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="0da28-157">使用空间音频意味着你需要管理声音在虚拟环境中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="0da28-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="0da28-158">你的主要目标是创建声音对象，这些对象的特征是当用户靠近时声音会更大，而当用户远离时声音会更小。</span><span class="sxs-lookup"><span data-stu-id="0da28-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="0da28-159">这称为声音衰减，使声音听起来就像是被放在一个固定地点一样。</span><span class="sxs-lookup"><span data-stu-id="0da28-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="0da28-160">所有衰减对象都有针对以下各项的可修改设置：</span><span class="sxs-lookup"><span data-stu-id="0da28-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="0da28-161">距离</span><span class="sxs-lookup"><span data-stu-id="0da28-161">Distance</span></span>
* <span data-ttu-id="0da28-162">空间化</span><span class="sxs-lookup"><span data-stu-id="0da28-162">Spatialization</span></span>
* <span data-ttu-id="0da28-163">空气吸收</span><span class="sxs-lookup"><span data-stu-id="0da28-163">Air Absorption</span></span>
* <span data-ttu-id="0da28-164">侦听器聚焦</span><span class="sxs-lookup"><span data-stu-id="0da28-164">Listener Focus</span></span>
* <span data-ttu-id="0da28-165">混响发送</span><span class="sxs-lookup"><span data-stu-id="0da28-165">Reverb Send</span></span>
* <span data-ttu-id="0da28-166">封闭</span><span class="sxs-lookup"><span data-stu-id="0da28-166">Occlusion</span></span>

<span data-ttu-id="0da28-167">[Unreal 中的声音衰减](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)提供了有关这些主题的详细信息和实现细节。</span><span class="sxs-lookup"><span data-stu-id="0da28-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>


## <a name="see-also"></a><span data-ttu-id="0da28-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0da28-168">See also</span></span>
* [<span data-ttu-id="0da28-169">空间音效</span><span class="sxs-lookup"><span data-stu-id="0da28-169">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="0da28-170">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="0da28-170">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="0da28-171">MR 空间 220：空间音效</span><span class="sxs-lookup"><span data-stu-id="0da28-171">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)