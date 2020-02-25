---
title: Azure 空间锚点教程-3。 显示 Azure 空间锚点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553919"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="09a60-105">3. 显示 Azure 空间锚点反馈</span><span class="sxs-lookup"><span data-stu-id="09a60-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="09a60-106">在本教程中，你将了解如何在使用 Azure 空间锚（ASA）时向用户提供有关定位点发现、事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="09a60-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="09a60-107">目标</span><span class="sxs-lookup"><span data-stu-id="09a60-107">Objectives</span></span>

* <span data-ttu-id="09a60-108">了解如何设置显示当前 ASA 会话重要信息的 UI 面板</span><span class="sxs-lookup"><span data-stu-id="09a60-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="09a60-109">了解并探索 ASA SDK 向用户提供的反馈元素</span><span class="sxs-lookup"><span data-stu-id="09a60-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="09a60-110">设置 ASA 反馈 UI 面板</span><span class="sxs-lookup"><span data-stu-id="09a60-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="09a60-111">在 "层次结构" 窗口中，右键单击 > **TextContent** "对象的**说明**，然后选择" **3d 对象** > " **TextMeshPro** " 以将 TextMeshPro 文本对象创建为说明 > TextContent 对象的子项，并为其提供一个合适的名称，例如 "**反馈**"：</span><span class="sxs-lookup"><span data-stu-id="09a60-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="09a60-113">若要更轻松地使用场景，请通过单击对象左侧的眼睛图标，将 ParentAnchor 对象的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>设置为 "关"。</span><span class="sxs-lookup"><span data-stu-id="09a60-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="09a60-114">这将隐藏场景窗口中的对象，而无需更改其游戏中的可见性。</span><span class="sxs-lookup"><span data-stu-id="09a60-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="09a60-115">当**反馈**对象仍处于选中状态时，在 "检查器" 窗口中更改其位置和大小，以便将它整齐地放置在说明文本下，例如：</span><span class="sxs-lookup"><span data-stu-id="09a60-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="09a60-116">将矩形转换位置**Y**改为-0.24</span><span class="sxs-lookup"><span data-stu-id="09a60-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="09a60-117">将矩形转换**宽度**更改为0.555</span><span class="sxs-lookup"><span data-stu-id="09a60-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="09a60-118">将矩形转换**高度**更改为0。1</span><span class="sxs-lookup"><span data-stu-id="09a60-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="09a60-119">然后选择字体属性，使文本在文本区域内非常合适，例如：</span><span class="sxs-lookup"><span data-stu-id="09a60-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="09a60-120">将文本网格 Pro （脚本）**字体样式**更改为粗体</span><span class="sxs-lookup"><span data-stu-id="09a60-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="09a60-121">将文本网格 Pro （脚本）**字号**更改为0.17</span><span class="sxs-lookup"><span data-stu-id="09a60-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="09a60-122">将文本网格 Pro （脚本）**对齐方式**更改为居中和居中</span><span class="sxs-lookup"><span data-stu-id="09a60-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="09a60-124">如果仍选中 "**反馈**" 对象，则在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**定位点反馈脚本（脚本）** 组件添加到反馈对象：</span><span class="sxs-lookup"><span data-stu-id="09a60-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="09a60-126">将**反馈**对象本身分配给**定位点反馈脚本（脚本）** 组件的**反馈文本**字段：</span><span class="sxs-lookup"><span data-stu-id="09a60-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="09a60-128">祝贺你</span><span class="sxs-lookup"><span data-stu-id="09a60-128">Congratulations</span></span>

<span data-ttu-id="09a60-129">在本教程中，已学习如何创建 UI 面板来显示 Azure 空间锚体验的当前状态，以便为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="09a60-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
