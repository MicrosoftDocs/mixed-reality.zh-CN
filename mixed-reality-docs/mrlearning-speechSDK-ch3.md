---
title: Azure 语音服务教程-3。 添加 Azure 认知服务语音翻译组件
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913199"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="a8ef6-105">3. 添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="a8ef6-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="a8ef6-106">在本教程中，我们将了解项目中的 Azure 认知服务语音翻译组件，并将其翻译为三种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="a8ef6-107">说明</span><span class="sxs-lookup"><span data-stu-id="a8ef6-107">Instructions</span></span>

1. <span data-ttu-id="a8ef6-108">选择层次结构中的 "Lunarcom_Base" 对象，然后在 "检查器" 面板中单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="a8ef6-109">搜索并选择 Lunarcom 转换识别器。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="a8ef6-111">禁用脱机模式模拟器。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="a8ef6-113">在继续之前，请确保在测试 Speech SDK 转换器之前，禁用了脱机模式模拟器（如上图所示）。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="a8ef6-114">若要进行转换，必须连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="a8ef6-115">单击 Lunarcom 转换识别器中的下拉箭头，然后选择要转换为的语言。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="a8ef6-117">现在，运行该应用程序并通过单击 "附属项" 按钮来测试转换器，然后开始说话。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="a8ef6-118">再次按卫星按钮以停止识别。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="a8ef6-119">下面是场景外观的示例。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="a8ef6-120">可以随时更改 "目标语言" 下拉列表下的语言（请参阅上图），以浏览其他语言的翻译。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="a8ef6-121">以下是场景外观的示例：</span><span class="sxs-lookup"><span data-stu-id="a8ef6-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="a8ef6-123">祝贺</span><span class="sxs-lookup"><span data-stu-id="a8ef6-123">Congratulations</span></span>

<span data-ttu-id="a8ef6-124">现在，您的项目可以将您所说的字词转换为多种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="a8ef6-125">可以自由地利用语言，并测试翻译的准确性。</span><span class="sxs-lookup"><span data-stu-id="a8ef6-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="a8ef6-126">下一教程： 4. 设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="a8ef6-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
