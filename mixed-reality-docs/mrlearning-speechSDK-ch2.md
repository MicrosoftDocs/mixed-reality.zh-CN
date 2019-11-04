---
title: Azure Speech Services 教程-2。 添加本地语音到文本转换的脱机模式
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 5382a1cce38e8607042c21b8dd3157d1da2fa72e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437553"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="a5564-105">2. 为本地语音到文本转换添加脱机模式</span><span class="sxs-lookup"><span data-stu-id="a5564-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="a5564-106">在本教程中，我们将添加一个脱机模式，使你能够在无法连接到 Azure 服务时执行本地语音到文本转换。</span><span class="sxs-lookup"><span data-stu-id="a5564-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="a5564-107">我们还将*模拟*断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="a5564-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="a5564-108">说明</span><span class="sxs-lookup"><span data-stu-id="a5564-108">Instructions</span></span>

1. <span data-ttu-id="a5564-109">选择层次结构中的 Lunarcom_Base 对象。</span><span class="sxs-lookup"><span data-stu-id="a5564-109">Select the Lunarcom_Base object in the hierarchy.</span></span>
2. <span data-ttu-id="a5564-110">单击 "检查器" 面板中的 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="a5564-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="a5564-111">搜索并选择 "Lunarcom 脱机识别"。</span><span class="sxs-lookup"><span data-stu-id="a5564-111">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="a5564-113">单击 LunarcomOfflineRecognizer 中的下拉箭头，然后选择 "已启用"。</span><span class="sxs-lookup"><span data-stu-id="a5564-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="a5564-114">这会使项目的行为类似于用户没有连接。</span><span class="sxs-lookup"><span data-stu-id="a5564-114">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="a5564-116">按下 "在 Unity 编辑器中播放"，并对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="a5564-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="a5564-117">在屏幕左下角按下麦克风，开始说话。</span><span class="sxs-lookup"><span data-stu-id="a5564-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="a5564-118">由于我们处于脱机状态，因此唤醒 word 功能已禁用。</span><span class="sxs-lookup"><span data-stu-id="a5564-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="a5564-119">每次希望在脱机时识别语音时，您都需要通过物理方式单击麦克风。</span><span class="sxs-lookup"><span data-stu-id="a5564-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="a5564-120">下面是场景外观的示例。</span><span class="sxs-lookup"><span data-stu-id="a5564-120">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="a5564-122">祝贺</span><span class="sxs-lookup"><span data-stu-id="a5564-122">Congratulations</span></span>

<span data-ttu-id="a5564-123">脱机模式已启用。</span><span class="sxs-lookup"><span data-stu-id="a5564-123">The offline mode has been enabled.</span></span> <span data-ttu-id="a5564-124">现在，脱机时，仍可以使用 speech SDK 来处理项目！</span><span class="sxs-lookup"><span data-stu-id="a5564-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="a5564-125">下一教程： 3. 添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="a5564-125">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

