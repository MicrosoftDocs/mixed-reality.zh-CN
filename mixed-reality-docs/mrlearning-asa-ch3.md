---
title: Azure 空间锚点教程-3。 显示 Azure 空间锚点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 19529cbfebd74938395545c329097d42b5af9ff9
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334401"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="46f87-105">3. 显示 Azure 空间锚点反馈</span><span class="sxs-lookup"><span data-stu-id="46f87-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="46f87-106">在本课程中，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点发现、事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="46f87-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="46f87-107">目标</span><span class="sxs-lookup"><span data-stu-id="46f87-107">Objectives</span></span>

* <span data-ttu-id="46f87-108">了解如何设置显示当前 ASA 会话重要信息的 UI 面板</span><span class="sxs-lookup"><span data-stu-id="46f87-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="46f87-109">了解并探索 ASA SDK 向用户提供的反馈元素</span><span class="sxs-lookup"><span data-stu-id="46f87-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="46f87-110">设置 ASA 反馈 UI 面板</span><span class="sxs-lookup"><span data-stu-id="46f87-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="46f87-111">在本课中，我们未使用 "SaveAnchorToDisk" 和 "ShareAnchor" 按钮，因此，请选择两个按钮，并取消选中 "检查器" 面板中的复选框（如下所示）以隐藏这些按钮。</span><span class="sxs-lookup"><span data-stu-id="46f87-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="46f87-113">创建指令面板。</span><span class="sxs-lookup"><span data-stu-id="46f87-113">Create the instruction panel.</span></span> <span data-ttu-id="46f87-114">首先右键单击 "说明" 按钮，将鼠标悬停在 "3D 对象" 上，然后选择 "textmeshpro"。</span><span class="sxs-lookup"><span data-stu-id="46f87-114">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="46f87-116">调整文本的规模和位置，使其与场景中的说明相匹配。</span><span class="sxs-lookup"><span data-stu-id="46f87-116">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="46f87-117">此外，请确保所有文本的对齐方式都居中。</span><span class="sxs-lookup"><span data-stu-id="46f87-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="46f87-118">然后从文本编辑器中删除示例文本，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="46f87-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="46f87-120">将 TextMeshPro 对象的名称更改为 "FeedbackPanel"。</span><span class="sxs-lookup"><span data-stu-id="46f87-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="46f87-122">确保在 ASA_feedback 层次结构中选择 "feedbackpanel" 文本，单击 "添加组件"，并通过搜索和选择定位反馈脚本来添加它。</span><span class="sxs-lookup"><span data-stu-id="46f87-122">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span>

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="46f87-124">将 "feedbackPanel" 文本对象从 ASA_Feedback 层次结构拖到脚本下的空槽中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="46f87-124">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span>

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="46f87-126">祝贺</span><span class="sxs-lookup"><span data-stu-id="46f87-126">Congratulations</span></span>

<span data-ttu-id="46f87-127">在本课程中，我们学习了如何创建 UI 面板来显示 Azure 空间锚体验的当前状态，以便为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="46f87-127">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
