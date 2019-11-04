---
title: Azure 空间锚点教程-3。 显示 Azure 空间锚点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438413"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="27981-105">3. 显示 Azure 空间锚点反馈</span><span class="sxs-lookup"><span data-stu-id="27981-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="27981-106">在本课程中，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点发现、事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="27981-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="27981-107">目标</span><span class="sxs-lookup"><span data-stu-id="27981-107">Objectives</span></span>

* <span data-ttu-id="27981-108">了解如何设置显示当前 ASA 会话重要信息的 UI 面板</span><span class="sxs-lookup"><span data-stu-id="27981-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="27981-109">了解并探索 ASA SDK 向用户提供的反馈元素</span><span class="sxs-lookup"><span data-stu-id="27981-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="27981-110">说明</span><span class="sxs-lookup"><span data-stu-id="27981-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="27981-111">设置 ASA 反馈 UI 面板</span><span class="sxs-lookup"><span data-stu-id="27981-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="27981-112">在本课中，我们未使用 "SaveAnchorToDisk" 和 "ShareAnchor" 按钮，因此，请选择两个按钮，并取消选中 "检查器" 面板中的复选框（如下所示）以隐藏这些按钮。</span><span class="sxs-lookup"><span data-stu-id="27981-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="27981-114">创建指令面板。</span><span class="sxs-lookup"><span data-stu-id="27981-114">Create the instruction panel.</span></span> <span data-ttu-id="27981-115">首先右键单击 "说明" 按钮，将鼠标悬停在 "3D 对象" 上，然后选择 "textmeshpro"。</span><span class="sxs-lookup"><span data-stu-id="27981-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="27981-117">调整文本的规模和位置，使其与场景中的说明相匹配。</span><span class="sxs-lookup"><span data-stu-id="27981-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="27981-118">此外，请确保所有文本的对齐方式都居中。</span><span class="sxs-lookup"><span data-stu-id="27981-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="27981-119">然后从文本编辑器中删除示例文本，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="27981-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="27981-121">将 TextMeshPro 对象的名称更改为 "FeedbackPanel"。</span><span class="sxs-lookup"><span data-stu-id="27981-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="27981-123">在 "项目" 面板中，选择 "资产" 并右键单击，然后选择 "在资源管理器中显示"。</span><span class="sxs-lookup"><span data-stu-id="27981-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="27981-125">单击[此处](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)下载接下来的几个步骤中所需的文件。</span><span class="sxs-lookup"><span data-stu-id="27981-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="27981-126">资源管理器打开后，选择 "资产" 文件夹，然后选择 "ASAmodulesAssets" 文件夹，并将定位点反馈脚本和定位点模块脚本文件复制到该文件夹中。</span><span class="sxs-lookup"><span data-stu-id="27981-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="27981-128">注意：如果您收到一条弹出消息，询问您是覆盖旧的还是保留旧的，请选择 "覆盖"。</span><span class="sxs-lookup"><span data-stu-id="27981-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="27981-129">返回到 "资产" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="27981-129">Return to the Assets folder.</span></span> <span data-ttu-id="27981-130">然后，进入 "AzureSpatialAnchorsPlugin" 文件夹，后跟示例文件夹和脚本文件夹。</span><span class="sxs-lookup"><span data-stu-id="27981-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="27981-131">然后将 Azure 空间锚定包装器复制到该文件夹中。</span><span class="sxs-lookup"><span data-stu-id="27981-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="27981-133">现在已上传文件，请确保在 ASA_feedback 层次结构中选择了 "feedbackpanel" 文本，单击 "添加组件"，并通过搜索和选择定位反馈脚本来添加它。</span><span class="sxs-lookup"><span data-stu-id="27981-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="27981-135">将 "feedbackPanel" 文本对象从 ASA_Feedback 层次结构拖动到脚本下的空槽中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="27981-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="27981-137">祝贺</span><span class="sxs-lookup"><span data-stu-id="27981-137">Congratulations</span></span>

<span data-ttu-id="27981-138">在本课程中，我们学习了如何创建 UI 面板来显示 Azure 空间锚体验的当前状态，以便为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="27981-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


