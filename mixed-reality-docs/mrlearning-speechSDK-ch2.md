---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460307"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="3eb8e-104">2.  添加本地语音到文本转换的脱机模式</span><span class="sxs-lookup"><span data-stu-id="3eb8e-104">2.    Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="3eb8e-105">在本教程中, 我们将添加一个脱机模式, 使你能够在无法连接到 Azure 服务时执行本地语音到文本转换。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-105">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="3eb8e-106">我们还将*模拟*断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-106">We will also *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="3eb8e-107">选择层次结构中的 Lunarcom_Base 对象, 并在 "检查器" 面板中单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="3eb8e-108">搜索并选择 "Lunarcom 脱机识别"。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-108">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="3eb8e-110">单击 LunarcomOfflineRecognizer 中的下拉箭头, 然后选择 "已启用"。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-110">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="3eb8e-111">这会使项目的行为类似于用户没有连接。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-111">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="3eb8e-113">现在, 按下 "在 Unity 编辑器中播放" 并对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-113">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="3eb8e-114">在屏幕左下角按下麦克风, 开始说话。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-114">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="3eb8e-115">由于我们处于脱机状态, 因此唤醒 word 功能已禁用。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-115">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="3eb8e-116">每次希望在离线时识别语音时, 您都必须每次都单击麦克风。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-116">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="3eb8e-117">下面是场景外观的示例。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-117">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="3eb8e-119">祝贺</span><span class="sxs-lookup"><span data-stu-id="3eb8e-119">Congratulations</span></span>

<span data-ttu-id="3eb8e-120">脱机模式已启用。</span><span class="sxs-lookup"><span data-stu-id="3eb8e-120">The offline mode has been enabled.</span></span> <span data-ttu-id="3eb8e-121">现在, 脱机时, 仍可以使用 speech SDK 来处理项目!</span><span class="sxs-lookup"><span data-stu-id="3eb8e-121">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="3eb8e-122">下一教程:3.添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="3eb8e-122">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

