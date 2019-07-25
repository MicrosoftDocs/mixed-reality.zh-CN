---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460339"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="e0948-104">Speech SDK 学习模块-使用语音命令的火箭启动器控件</span><span class="sxs-lookup"><span data-stu-id="e0948-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="e0948-105">在本课程中, 我们将使用 Azure 语音服务的意向功能来了解语音的意图。</span><span class="sxs-lookup"><span data-stu-id="e0948-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="e0948-106">我们将使用检测到的语音的意图来控制火箭启动器。</span><span class="sxs-lookup"><span data-stu-id="e0948-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="e0948-107">在本课程中, 我们将导入火箭启动器资产, 并将检测到的意向语音命令接口到预定义的控制按钮以控制火箭。</span><span class="sxs-lookup"><span data-stu-id="e0948-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="e0948-108">目标</span><span class="sxs-lookup"><span data-stu-id="e0948-108">Objectives</span></span>

- <span data-ttu-id="e0948-109">了解如何将语音意向连接为语音命令。</span><span class="sxs-lookup"><span data-stu-id="e0948-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="e0948-110">了解如何使用语音意向语音命令作为火箭控制输入命令。</span><span class="sxs-lookup"><span data-stu-id="e0948-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="e0948-111">说明</span><span class="sxs-lookup"><span data-stu-id="e0948-111">Instructions</span></span>
1. <span data-ttu-id="e0948-112">在本教程中, 我们将使用 "BaseModule" 资源将火箭启动器与语音命令集成。</span><span class="sxs-lookup"><span data-stu-id="e0948-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="e0948-113">为此, 我们需要将资产导入到项目中。</span><span class="sxs-lookup"><span data-stu-id="e0948-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="e0948-114">你可以使用此链接 (附加链接) 下载 "火箭启动器" 资产。</span><span class="sxs-lookup"><span data-stu-id="e0948-114">You can download the "Rocket Launcher" asset using this link (Attach the link).</span></span> 

2. <span data-ttu-id="e0948-115">若要导入资产, 请转到 "资产-> 导入包-> 自定义包" > 导航到下载的文件, 然后单击 "导入"。</span><span class="sxs-lookup"><span data-stu-id="e0948-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="e0948-117">导入 "火箭启动器" 资产后, 在 "火箭启动器" 文件夹内导航 > Prototyping-> 选择 "火箭 Launcher_Complete", 然后将其拖放到现有场景层次结构。</span><span class="sxs-lookup"><span data-stu-id="e0948-117">After importing the "Rocket Launcher" asset, navigate inside the "Rocket Launcher" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="e0948-119">现在, 我们需要将 "火箭启动器" 与我们在上一课中处理的 LUIS 项目集成 (lesson4 的链接)。</span><span class="sxs-lookup"><span data-stu-id="e0948-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson (link for lesson4).</span></span> <span data-ttu-id="e0948-120">为此, 请在层次结构中展开 "火箭 Launcher_Complete" prefab, 并找到 "LaunchRoundButton"、"ResetRoundButton" 和 "位置提示" 按钮。</span><span class="sxs-lookup"><span data-stu-id="e0948-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="e0948-122">选择 "LaunchRoundButton", 然后在 "检查器" 面板中, 依次单击 "种不可交互" 和 "事件" OnClick () ", 拖放" LunarModule "prefab。</span><span class="sxs-lookup"><span data-stu-id="e0948-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="e0948-123">然后, 选择 "函数" 下拉箭头并选择 "LunarModule", 并导航到 "StartThruster ()" 函数并将其选中。</span><span class="sxs-lookup"><span data-stu-id="e0948-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3。0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="e0948-126">选择 "ResetRoundButton", 然后在 "检查器" 面板中, 依次单击 "种不可交互" 和 "事件" OnClick () ", 拖放" LunarModule "prefab。</span><span class="sxs-lookup"><span data-stu-id="e0948-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="e0948-127">然后, 选择 "函数" 下拉箭头并选择 "LunarModule", 并导航到 "resetModule ()" 函数并将其选中。</span><span class="sxs-lookup"><span data-stu-id="e0948-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="e0948-129">选择 "放置提示", 然后在 "检查器" 面板中, 选择 "种不可交互", 并在事件 "OnClick ()" 下, 拖放 "LunarModule" prefab。</span><span class="sxs-lookup"><span data-stu-id="e0948-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="e0948-130">然后, 选择 "函数" 下拉箭头并选择 "LunarModule", 并导航到 "TogglePlacementHints" 函数, 然后选择 "ToggleGameOBjects ()"。</span><span class="sxs-lookup"><span data-stu-id="e0948-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="e0948-132">接下来, 选择 "Lunarcom_Completed prefab in 层次结构" 并导航到 "检查器" 中的 "Lunarcom 意向识别器" 脚本, 然后将 "LaunchRoundButton"、"ResetRoundButton" 和 "位置提示" 按钮拖放到各自的位置。</span><span class="sxs-lookup"><span data-stu-id="e0948-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="e0948-134">按下 Unity 编辑器中的 "播放" 按钮, 然后单击 "火箭" 按钮, 然后 utter "推送火箭启动" 按钮、"向我显示放置提示"、"按 rest" 按钮, 或与启动、重置或提示的火箭启动器请求相关的任何其他短语。</span><span class="sxs-lookup"><span data-stu-id="e0948-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="e0948-138">祝贺</span><span class="sxs-lookup"><span data-stu-id="e0948-138">Congratulations</span></span>

<span data-ttu-id="e0948-139">在本课中, 我们学习了如何将 AI 功能的语音命令连接到语音命令, 以将其用作输入方法。</span><span class="sxs-lookup"><span data-stu-id="e0948-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="e0948-140">现在, 我们的程序可以使用扬声器意向作为语音命令, 为火箭启动器提供输入。</span><span class="sxs-lookup"><span data-stu-id="e0948-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>

