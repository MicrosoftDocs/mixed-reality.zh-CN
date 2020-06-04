---
title: 语音输入
description: 在 HoloLens 2 和 Unreal 引擎中设置和使用语音输入的教程
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，Unreal，Unreal 引擎4，UE4，HoloLens 2，语音，语音输入，语音识别，混合现实，开发，功能，文档，指南，全息影像，游戏开发
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330629"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="48173-104">Unreal 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="48173-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="48173-105">概述</span><span class="sxs-lookup"><span data-stu-id="48173-105">Overview</span></span>
<span data-ttu-id="48173-106">语音输入使你可以与全息图交互，而无需使用手型，并支持在 HoloLens （第一代）和 HoloLens 2 上。</span><span class="sxs-lookup"><span data-stu-id="48173-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="48173-107">它通过支持所有其他通用 Windows 应用程序中的语音的同一个引擎提供支持，并可以为在混合现实中交互的方式添加自然感觉。</span><span class="sxs-lookup"><span data-stu-id="48173-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="48173-108">支持的语音功能包括：</span><span class="sxs-lookup"><span data-stu-id="48173-108">Supported voice features include:</span></span>
- <span data-ttu-id="48173-109">[选择命令](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="48173-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="48173-110">你好，Cortana</span><span class="sxs-lookup"><span data-stu-id="48173-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="48173-111">"查看" 按钮和标签交互</span><span class="sxs-lookup"><span data-stu-id="48173-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="48173-112">听写</span><span class="sxs-lookup"><span data-stu-id="48173-112">Dictation</span></span>

<span data-ttu-id="48173-113">有关详细信息，请参阅主要的[语音输入](voice-input.md)文档。</span><span class="sxs-lookup"><span data-stu-id="48173-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="48173-114">启用语音识别</span><span class="sxs-lookup"><span data-stu-id="48173-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="48173-115">在 HoloLens 上启用语音识别：</span><span class="sxs-lookup"><span data-stu-id="48173-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="48173-116">选择 "**项目设置" > 平台 > HoloLens > 功能**并启用**麦克风**。</span><span class="sxs-lookup"><span data-stu-id="48173-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="48173-117">在设置中启用了语音 recogniztion **> 隐私 > 语音**和选择**英语**。</span><span class="sxs-lookup"><span data-stu-id="48173-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="48173-118">语音识别始终在 "**设置**" 应用程序中配置的 Windows 显示语言中工作。</span><span class="sxs-lookup"><span data-stu-id="48173-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="48173-119">建议你同时启用**在线语音识别**，以获得最佳的服务质量。</span><span class="sxs-lookup"><span data-stu-id="48173-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Windows 语音识别设置](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="48173-121">当应用程序首次启动时，将显示一个对话框，询问你是否要启用麦克风。</span><span class="sxs-lookup"><span data-stu-id="48173-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="48173-122">选择 **"是"** 将在应用中启动语音输入。</span><span class="sxs-lookup"><span data-stu-id="48173-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="48173-123">语音输入不需要任何特殊的 Windows Mixed Reality Api;它基于现有的 Unreal Engine 4[输入](https://docs.unrealengine.com/Gameplay/Input/index.html)映射 API 构建。</span><span class="sxs-lookup"><span data-stu-id="48173-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="48173-124">添加语音映射</span><span class="sxs-lookup"><span data-stu-id="48173-124">Adding Speech Mappings</span></span>
<span data-ttu-id="48173-125">使用语音输入时，将语音连接到操作非常重要。</span><span class="sxs-lookup"><span data-stu-id="48173-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="48173-126">这些映射会监视用户可能会说出的语音关键字应用，然后发出链接的操作。</span><span class="sxs-lookup"><span data-stu-id="48173-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="48173-127">可以通过以下方式找到语音映射：</span><span class="sxs-lookup"><span data-stu-id="48173-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="48173-128">选择 "**编辑 > 项目设置**"，滚动到 "**引擎**" 部分，然后单击 "**输入**"。</span><span class="sxs-lookup"><span data-stu-id="48173-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="48173-129">添加跳转命令的新语音映射：</span><span class="sxs-lookup"><span data-stu-id="48173-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="48173-130">单击 " **+** **数组元素**" 旁边的图标，然后填写以下值：</span><span class="sxs-lookup"><span data-stu-id="48173-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="48173-131">**操作名称**的**jumpWord**</span><span class="sxs-lookup"><span data-stu-id="48173-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="48173-132">**跳转\*\*\*\*语音关键字**</span><span class="sxs-lookup"><span data-stu-id="48173-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="48173-133">任何英语单词或短句子都可以用作关键字。</span><span class="sxs-lookup"><span data-stu-id="48173-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![UE4 引擎输入的输入](images/unreal/engine-input.png)

<span data-ttu-id="48173-135">语音映射可用作操作或轴映射等输入组件或事件图中的蓝图节点。</span><span class="sxs-lookup"><span data-stu-id="48173-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="48173-136">例如，可以链接 "跳转" 命令，根据字词的讲述时间打印出两个不同的日志：</span><span class="sxs-lookup"><span data-stu-id="48173-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="48173-137">双击蓝图以在**事件图**中打开它。</span><span class="sxs-lookup"><span data-stu-id="48173-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="48173-138">**右键单击**并搜索语音映射的**操作名称**（在本例中为**JumpWord**），然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="48173-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="48173-139">这会将 "**输入操作**" 节点添加到关系图中。</span><span class="sxs-lookup"><span data-stu-id="48173-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="48173-140">将**按下**的 pin 拖放到 "**打印字符串**" 节点，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="48173-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="48173-141">你可以保留已**释放**的 pin，而不会对语音映射执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="48173-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![简单的语音操作](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="48173-143">播放应用，口述 "**跳转**" 并观看控制台打印日志！</span><span class="sxs-lookup"><span data-stu-id="48173-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="48173-144">这就是在 Unreal 中开始向 HoloLens 应用添加语音输入所需的全部设置。</span><span class="sxs-lookup"><span data-stu-id="48173-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="48173-145">可以在下面的链接中找到有关语音和交互性的详细信息，并确保考虑要为用户创建的体验。</span><span class="sxs-lookup"><span data-stu-id="48173-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="48173-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48173-146">See also</span></span>
* [<span data-ttu-id="48173-147">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="48173-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="48173-148">本能交互</span><span class="sxs-lookup"><span data-stu-id="48173-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="48173-149">MR 输入 212：语音</span><span class="sxs-lookup"><span data-stu-id="48173-149">MR Input 212: Voice</span></span>](holograms-212.md)
