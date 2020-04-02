---
title: Azure 空间定位点教程 - 3. 显示 Azure 空间定位点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031254"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="5d9ec-105">3.显示 Azure 空间定位点反馈</span><span class="sxs-lookup"><span data-stu-id="5d9ec-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="5d9ec-106">本教程介绍如何在使用 Azure 空间定位点 (ASA) 时向用户提供有关定位点发现、事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="5d9ec-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="5d9ec-107">目标</span><span class="sxs-lookup"><span data-stu-id="5d9ec-107">Objectives</span></span>

* <span data-ttu-id="5d9ec-108">了解如何设置一个 UI 面板用于显示有关当前 ASA 会话的重要信息</span><span class="sxs-lookup"><span data-stu-id="5d9ec-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="5d9ec-109">了解并探索 ASA SDK 提供给用户使用的反馈元素</span><span class="sxs-lookup"><span data-stu-id="5d9ec-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="5d9ec-110">设置 ASA 反馈 UI 面板</span><span class="sxs-lookup"><span data-stu-id="5d9ec-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="5d9ec-111">在“层次结构”窗口中，右键单击“Instructions” > “TextContent”对象并选择“3D 对象” **“文本 - TextMeshPro”，以创建一个 TextMeshPro 文本对象作为“Instructions” > “TextContent”对象的子级，并为创建的对象指定适当的名称，例如 **Feedback**：**   </span><span class="sxs-lookup"><span data-stu-id="5d9ec-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="5d9ec-113">为了更轻松地在场景中操作，请单击“ParentAnchor”对象左侧的眼睛图标，将此对象的“场景可见性”设置为关闭。<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank"></a></span><span class="sxs-lookup"><span data-stu-id="5d9ec-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="5d9ec-114">这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性。</span><span class="sxs-lookup"><span data-stu-id="5d9ec-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="5d9ec-115">在仍选中了“Feedback”对象的情况下，在“检查器”窗口中更改其位置和大小，使其整齐地定位在说明文本下，例如： </span><span class="sxs-lookup"><span data-stu-id="5d9ec-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="5d9ec-116">将矩形变换的“位置 Y”更改为 -0.24 </span><span class="sxs-lookup"><span data-stu-id="5d9ec-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="5d9ec-117">将矩形变换的“宽度”更改为 0.555 </span><span class="sxs-lookup"><span data-stu-id="5d9ec-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="5d9ec-118">将矩形变换的“高度”更改为 0.1 </span><span class="sxs-lookup"><span data-stu-id="5d9ec-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="5d9ec-119">然后选择字体属性，使文本合体地显示在文本区域中，例如：</span><span class="sxs-lookup"><span data-stu-id="5d9ec-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="5d9ec-120">将 Text Mesh Pro (Script) 的“字体样式”更改为“粗体” </span><span class="sxs-lookup"><span data-stu-id="5d9ec-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="5d9ec-121">将 Text Mesh Pro (Script) 的“字体大小”更改为 0.17 </span><span class="sxs-lookup"><span data-stu-id="5d9ec-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="5d9ec-122">将 Text Mesh Pro (Script) 的“对齐方式”更改为“居中” </span><span class="sxs-lookup"><span data-stu-id="5d9ec-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="5d9ec-124">在仍选中了“Feedback”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“定位点反馈脚本(脚本)”组件添加到 Feedback 对象：   </span><span class="sxs-lookup"><span data-stu-id="5d9ec-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="5d9ec-126">将“Feedback”对象本身分配到“定位点反馈脚本(脚本)”组件的“反馈文本”字段：   </span><span class="sxs-lookup"><span data-stu-id="5d9ec-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="5d9ec-128">祝贺</span><span class="sxs-lookup"><span data-stu-id="5d9ec-128">Congratulations</span></span>

<span data-ttu-id="5d9ec-129">在本教程中，你已了解如何创建一个 UI 面板用于显示 Azure 空间定位点体验的当前状态，以便为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="5d9ec-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
