---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326522"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="1bc4e-104">显示 Azure 空间的定位点反馈</span><span class="sxs-lookup"><span data-stu-id="1bc4e-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="1bc4e-105">在本课中，您将了解如何使用 Azure 空间的定位点时为用户提供有关定位点发现、 事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="1bc4e-106">目标：</span><span class="sxs-lookup"><span data-stu-id="1bc4e-106">Objectives:</span></span>

* <span data-ttu-id="1bc4e-107">了解如何设置用户界面面板，用于显示当前的 ASA 会话有关的重要信息</span><span class="sxs-lookup"><span data-stu-id="1bc4e-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="1bc4e-108">了解和探索 ASA SDK 向用户提供的反馈元素</span><span class="sxs-lookup"><span data-stu-id="1bc4e-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="1bc4e-109">说明</span><span class="sxs-lookup"><span data-stu-id="1bc4e-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="1bc4e-110">设置 ASA 反馈 UI 面板</span><span class="sxs-lookup"><span data-stu-id="1bc4e-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="1bc4e-111">在本课中，我们不使用"SaveAnchorToDisk"和"ShareAnchor"按钮，因此选择这两个按钮和取消选中检查器面板中的复选框 （如下所示） 来隐藏这些按钮。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="1bc4e-113">接下来，创建指令面板。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-113">Next, create the instruction panel.</span></span> <span data-ttu-id="1bc4e-114">通过右键单击"说明"按钮启动、 悬停"3D 对象"，然后选择"textmeshpro-text。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="1bc4e-116">调整规模和定位文本，以便它与您的场景中的说明进行操作相匹配。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="1bc4e-117">此外，确保居中的所有文本的对齐方式。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="1bc4e-118">然后从文本编辑器中，删除示例文本，如在下图中所示。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="1bc4e-120">将 TextMeshPro 对象的名称更改为"FeedbackPanel。"</span><span class="sxs-lookup"><span data-stu-id="1bc4e-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="1bc4e-122">在项目面板中，选择"资产"并右键单击，然后选择"显示在资源管理器"。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="1bc4e-124">现在，单击[此处](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)下载文件所需在接下来的几个步骤。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="1bc4e-125">资源管理器打开后，选择资产文件夹，然后"ASAmodulesAssets"文件夹，并将定位点反馈脚本和定位点模块脚本文件复制到文件夹。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="1bc4e-127">注意： 如果你收到一个弹出窗口，询问您是否要覆盖旧或保留旧请确保选择覆盖。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="1bc4e-128">现在返回到资产文件夹。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-128">Now return to the Assets folder.</span></span> <span data-ttu-id="1bc4e-129">然后，转到"AzureSpatialAnchorsPlugin"文件夹，然后示例文件夹，并最后 scripts 文件夹中，并将 Azure 空间的定位点演示包装器复制到该文件夹。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="1bc4e-131">现在，将文件上传时，确保选中"feedbackpanel"文本，ASA_feedback 层次结构中并单击"添加组件"并通过为其搜索，然后选择它后它会显示添加定位点反馈脚本。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="1bc4e-133">从 ASA_Feedback 层次结构拖动到空槽脚本下的"feedbackPanel"文本对象，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="1bc4e-135">祝贺</span><span class="sxs-lookup"><span data-stu-id="1bc4e-135">Congratulations</span></span>

<span data-ttu-id="1bc4e-136">在本课程中，我们学习了如何创建一个用户界面面板，以显示向用户提供实时反馈的 Azure 空间定位体验的当前状态。</span><span class="sxs-lookup"><span data-stu-id="1bc4e-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


