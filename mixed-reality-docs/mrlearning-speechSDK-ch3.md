---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460315"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="58dc3-104">3.  添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="58dc3-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="58dc3-105">在本教程中, 我们将了解如何 aabout 项目中的 Azure 认知服务语音翻译组件, 并将其翻译为三种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="58dc3-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

1. <span data-ttu-id="58dc3-106">选择层次结构中的 Lunarcom_Base 对象, 并在 "检查器" 面板中单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="58dc3-106">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="58dc3-107">搜索并选择 "LunarcomTranslationRecognizer"。</span><span class="sxs-lookup"><span data-stu-id="58dc3-107">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="58dc3-109">注意:请确保在测试 Speech SDK 转换器之前禁用了脱机模式模拟器。</span><span class="sxs-lookup"><span data-stu-id="58dc3-109">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="58dc3-110">若要进行转换, 必须连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="58dc3-110">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="58dc3-111">请参阅下图中的查找此设置的位置。</span><span class="sxs-lookup"><span data-stu-id="58dc3-111">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="58dc3-113">单击 LunarcomTranslationRecognizer 中的下拉箭头, 然后选择要转换为的语言。</span><span class="sxs-lookup"><span data-stu-id="58dc3-113">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="58dc3-115">现在, 运行该应用程序并通过单击 "附属项" 按钮来测试转换器, 然后开始说话。</span><span class="sxs-lookup"><span data-stu-id="58dc3-115">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="58dc3-116">再次按卫星按钮以停止识别。</span><span class="sxs-lookup"><span data-stu-id="58dc3-116">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="58dc3-117">下面是场景外观的示例。</span><span class="sxs-lookup"><span data-stu-id="58dc3-117">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="58dc3-118">可以随时更改 "目标语言" 下拉列表下的语言 (请参阅上图), 以浏览其他语言的翻译。</span><span class="sxs-lookup"><span data-stu-id="58dc3-118">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="58dc3-119">注意:在测试之前, 请确保脱机模拟器已禁用, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="58dc3-119">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="58dc3-121">以下是场景外观的示例:</span><span class="sxs-lookup"><span data-stu-id="58dc3-121">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="58dc3-123">祝贺</span><span class="sxs-lookup"><span data-stu-id="58dc3-123">Congratulations</span></span>

<span data-ttu-id="58dc3-124">现在, 您的项目可以将您所说的字词转换为多种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="58dc3-124">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="58dc3-125">可以自由地利用语言, 并测试翻译的准确性。</span><span class="sxs-lookup"><span data-stu-id="58dc3-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="58dc3-126">下一教程:4.设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="58dc3-126">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

