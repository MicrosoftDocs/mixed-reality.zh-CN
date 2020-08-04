---
title: Azure 空间定位点教程 - 4. 显示 Azure 空间定位点反馈
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376519"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="e0018-105">4.显示来自 Azure 空间定位点的反馈</span><span class="sxs-lookup"><span data-stu-id="e0018-105">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="e0018-106">在本教程中，你将学习如何使用 Azure 空间定位点 (ASA) 向用户提供有关定位点发现、事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="e0018-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="e0018-107">目标</span><span class="sxs-lookup"><span data-stu-id="e0018-107">Objectives</span></span>

* <span data-ttu-id="e0018-108">了解如何设置一个 UI 面板来显示当前 ASA 会话的相关重要信息</span><span class="sxs-lookup"><span data-stu-id="e0018-108">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="e0018-109">了解并探索 ASA SDK 提供给用户使用的反馈元素</span><span class="sxs-lookup"><span data-stu-id="e0018-109">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="e0018-110">设置 ASA 反馈面板</span><span class="sxs-lookup"><span data-stu-id="e0018-110">Setting up ASA feedback panel</span></span>

<span data-ttu-id="e0018-111">在“层次结构”窗口中，右键单击“说明” > “TextContent”对象 。</span><span class="sxs-lookup"><span data-stu-id="e0018-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="e0018-112">选择“3D 对象” > “Text - TextMeshPro”，创建作为“说明”>“TextContent 对象”的子级的 TextMeshPro 文本对象： </span><span class="sxs-lookup"><span data-stu-id="e0018-112">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="e0018-114">为了更轻松地在场景中操作，请单击“ParentAnchor”对象左侧的眼睛图标，将此对象的“场景可见性”设置为关闭。<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank"></a></span><span class="sxs-lookup"><span data-stu-id="e0018-114">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="e0018-115">这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性。</span><span class="sxs-lookup"><span data-stu-id="e0018-115">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="e0018-116">将新创建的文本 (TMP) 对象重命名为 Feedback，然后在检查器窗口中更改其位置和大小，使其整齐放置在说明文本的下方，例如：</span><span class="sxs-lookup"><span data-stu-id="e0018-116">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="e0018-117">将矩形变换组件的位置 Y 更改为 -0.24。</span><span class="sxs-lookup"><span data-stu-id="e0018-117">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="e0018-118">将矩形变换组件的宽度更改为 0.555。</span><span class="sxs-lookup"><span data-stu-id="e0018-118">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="e0018-119">将矩形变换组件的高度更改为 0.1。</span><span class="sxs-lookup"><span data-stu-id="e0018-119">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="e0018-120">然后，选择字体属性，使文本适当地显示在文本区域中，例如：</span><span class="sxs-lookup"><span data-stu-id="e0018-120">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="e0018-121">将 TextMeshPro - Text 组件的字体样式更改为粗体。</span><span class="sxs-lookup"><span data-stu-id="e0018-121">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="e0018-122">将 TextMeshPro - Text 组件的字体大小更改为 0.17。</span><span class="sxs-lookup"><span data-stu-id="e0018-122">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="e0018-123">将 TextMeshPro - Text 组件的对齐方式更改为“居中”。</span><span class="sxs-lookup"><span data-stu-id="e0018-123">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="e0018-125">还是在“层次结构”窗口中选择 Feedback 对象，然后在检查器窗口中，使用“添加组件”按钮添加“定位点反馈脚本(脚本)”组件，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="e0018-125">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="e0018-126">将 Feedback 对象本身分配到“定位点反馈脚本(脚本)”组件的“反馈文本”字段  。</span><span class="sxs-lookup"><span data-stu-id="e0018-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="e0018-128">祝贺</span><span class="sxs-lookup"><span data-stu-id="e0018-128">Congratulations</span></span>

<span data-ttu-id="e0018-129">在本教程中，你学习了如何创建 UI 面板。</span><span class="sxs-lookup"><span data-stu-id="e0018-129">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="e0018-130">它显示 Azure 空间定位点体验的当前状态，为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="e0018-130">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="e0018-131">下一教程：5.适用于 Android 和 iOS 的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="e0018-131">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
