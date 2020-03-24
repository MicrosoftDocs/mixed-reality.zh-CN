---
title: Azure 语音服务教程 - 2. 为本地语音到文本翻译添加脱机模式
description: 完成本课程可以了解如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031635"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="41a3f-105">2.使用语音识别执行命令</span><span class="sxs-lookup"><span data-stu-id="41a3f-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="41a3f-106">在本教程中，你将添加使用 Azure 语音识别执行命令的功能，以便可以根据定义的单词或短语执行一些操作。</span><span class="sxs-lookup"><span data-stu-id="41a3f-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="41a3f-107">目标</span><span class="sxs-lookup"><span data-stu-id="41a3f-107">Objectives</span></span>

* <span data-ttu-id="41a3f-108">了解如何使用 Azure 语音识别执行命令</span><span class="sxs-lookup"><span data-stu-id="41a3f-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="41a3f-109">说明</span><span class="sxs-lookup"><span data-stu-id="41a3f-109">Instructions</span></span>

<span data-ttu-id="41a3f-110">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 唤醒字词识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：   </span><span class="sxs-lookup"><span data-stu-id="41a3f-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="41a3f-111">在“唤醒字词”字段中输入适当的短语，例如“激活终端”。  </span><span class="sxs-lookup"><span data-stu-id="41a3f-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="41a3f-112">在“解除字词”字段中输入适当的短语，例如“解除终端”。  </span><span class="sxs-lookup"><span data-stu-id="41a3f-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="41a3f-114">MRTK 中未包含“Lunarcom 唤醒字词识别器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="41a3f-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="41a3f-115">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="41a3f-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="41a3f-116">如果现在进入“游戏”模式，与在上一篇教程中一样，默认已启用终端面板，但你现在可以通过讲出解除字词“解除终端”来禁用它： </span><span class="sxs-lookup"><span data-stu-id="41a3f-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="41a3f-118">讲出唤醒字词“激活终端”以再次启用终端面板： </span><span class="sxs-lookup"><span data-stu-id="41a3f-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="41a3f-120">应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="41a3f-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="41a3f-121">如果你预计经常无法连接到 Azure，还可以按照[启用语音命令](mrlearning-base-ch5.md#enabling-voice-commands)中的说明，使用 MRTK 实现语音命令。</span><span class="sxs-lookup"><span data-stu-id="41a3f-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="41a3f-122">祝贺</span><span class="sxs-lookup"><span data-stu-id="41a3f-122">Congratulations</span></span>

<span data-ttu-id="41a3f-123">现已实现了由 Azure 提供支持的语音命令。</span><span class="sxs-lookup"><span data-stu-id="41a3f-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="41a3f-124">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="41a3f-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="41a3f-125">下一篇教程将介绍如何使用 Azure 语音翻译来翻译语音。</span><span class="sxs-lookup"><span data-stu-id="41a3f-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="41a3f-126">下一教程：3.添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="41a3f-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
