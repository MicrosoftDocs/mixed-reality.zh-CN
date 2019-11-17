---
title: Azure 语音服务教程-3。 添加 Azure 认知服务语音翻译组件
description: 在本课程中，你将了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143234"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="33174-105">3. 添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="33174-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="33174-106">在本教程中，你将了解你的项目的 Azure 认知服务语音翻译组件以及如何转换为三种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="33174-106">In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="33174-107">说明</span><span class="sxs-lookup"><span data-stu-id="33174-107">Instructions</span></span>

1. <span data-ttu-id="33174-108">选择层次结构中的 "Lunarcom_Base" 对象，然后在 "检查器" 面板中单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="33174-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="33174-109">搜索并选择 Lunarcom 转换识别器。</span><span class="sxs-lookup"><span data-stu-id="33174-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="33174-111">禁用脱机模式模拟器。</span><span class="sxs-lookup"><span data-stu-id="33174-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="33174-113">在继续之前，请确保在测试 Speech SDK 转换器之前禁用了脱机模式模拟器（如上图所示）。</span><span class="sxs-lookup"><span data-stu-id="33174-113">Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator.</span></span> <span data-ttu-id="33174-114">若要进行转换，必须连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="33174-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="33174-115">单击 Lunarcom 转换识别器中的下拉箭头，然后选择要转换为的语言。</span><span class="sxs-lookup"><span data-stu-id="33174-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="33174-117">运行应用程序并通过单击 "附属项" 按钮来测试转换器，开始说话。</span><span class="sxs-lookup"><span data-stu-id="33174-117">Run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="33174-118">再次按卫星按钮以停止识别。</span><span class="sxs-lookup"><span data-stu-id="33174-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="33174-119">下面是场景外观的示例。</span><span class="sxs-lookup"><span data-stu-id="33174-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="33174-120">可以随时更改 "目标语言" 下拉列表下的语言（请参阅上图），以浏览其他语言的翻译。</span><span class="sxs-lookup"><span data-stu-id="33174-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="33174-121">以下是场景外观的示例：</span><span class="sxs-lookup"><span data-stu-id="33174-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="33174-123">祝贺</span><span class="sxs-lookup"><span data-stu-id="33174-123">Congratulations</span></span>

<span data-ttu-id="33174-124">你的项目现在可以成功地将你说的字词转换为多种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="33174-124">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="33174-125">可以自由地利用语言，并测试翻译的准确性。</span><span class="sxs-lookup"><span data-stu-id="33174-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="33174-126">下一教程： 4. 设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="33174-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
