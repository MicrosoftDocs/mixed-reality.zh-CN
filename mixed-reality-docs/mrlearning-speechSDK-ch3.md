---
title: Azure 语音服务教程 - 3. 添加 Azure 认知服务语音翻译组件
description: 本课程介绍如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028320"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="14bc1-105">3.添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="14bc1-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="14bc1-106">在本教程中，你将在项目中添加语音翻译，以便可以将语音翻译和听录成三种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="14bc1-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="14bc1-107">目标</span><span class="sxs-lookup"><span data-stu-id="14bc1-107">Objectives</span></span>

* <span data-ttu-id="14bc1-108">了解如何集成 Azure 语音翻译</span><span class="sxs-lookup"><span data-stu-id="14bc1-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="14bc1-109">说明</span><span class="sxs-lookup"><span data-stu-id="14bc1-109">Instructions</span></span>

<span data-ttu-id="14bc1-110">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 翻译识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：   </span><span class="sxs-lookup"><span data-stu-id="14bc1-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="14bc1-111">将“目标语言”更改为所选语言，例如“德语”  </span><span class="sxs-lookup"><span data-stu-id="14bc1-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="14bc1-113">MRTK 中未包含“Lunarcom 翻译识别器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="14bc1-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="14bc1-114">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="14bc1-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="14bc1-115">如果现在进入“游戏”模式，可以先按卫星按钮来测试语音翻译。</span><span class="sxs-lookup"><span data-stu-id="14bc1-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="14bc1-116">假设计算机上配备了麦克风，当你讲话时，你的语音将翻译成所选语言，并在终端面板上听录：</span><span class="sxs-lookup"><span data-stu-id="14bc1-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="14bc1-118">应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="14bc1-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="14bc1-119">祝贺</span><span class="sxs-lookup"><span data-stu-id="14bc1-119">Congratulations</span></span>

<span data-ttu-id="14bc1-120">项目现在可以成功地将你讲出的词语翻译成多种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="14bc1-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="14bc1-121">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="14bc1-121">Run the application on your device to ensure the feature is working properly.</span></span>

[<span data-ttu-id="14bc1-122">下一教程：4.设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="14bc1-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
