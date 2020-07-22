---
title: 入门教程 - 3. 配置 MRTK 配置文件
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2c413964a435814275a1b908770ca977412f92be
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304809"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="9b24c-105">3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="9b24c-106">概述</span><span class="sxs-lookup"><span data-stu-id="9b24c-106">Overview</span></span>

<span data-ttu-id="9b24c-107">在本教程中，你将学习如何自定义和配置 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9b24c-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="9b24c-108">此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。</span><span class="sxs-lookup"><span data-stu-id="9b24c-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="9b24c-109">但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。</span><span class="sxs-lookup"><span data-stu-id="9b24c-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="9b24c-110">目标</span><span class="sxs-lookup"><span data-stu-id="9b24c-110">Objectives</span></span>

* <span data-ttu-id="9b24c-111">了解如何自定义和配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="9b24c-112">隐藏空间感知网格</span><span class="sxs-lookup"><span data-stu-id="9b24c-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="9b24c-113">更改空间感知显示选项</span><span class="sxs-lookup"><span data-stu-id="9b24c-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="9b24c-114">隐藏空间感知网格所要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="9b24c-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="9b24c-115">克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="9b24c-116">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="9b24c-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="9b24c-117">克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="9b24c-118">克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="9b24c-119">更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="9b24c-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="9b24c-120">默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="9b24c-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="9b24c-121">这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="9b24c-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="9b24c-122">配置文件有多个嵌套层。</span><span class="sxs-lookup"><span data-stu-id="9b24c-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="9b24c-123">因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="9b24c-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="9b24c-124">1.克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="9b24c-125">配置配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="9b24c-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="9b24c-126">因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="9b24c-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="9b24c-127">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在检查器窗口中将“MixedRealityToolkit”配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”：</span><span class="sxs-lookup"><span data-stu-id="9b24c-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base  ](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="9b24c-129">在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="9b24c-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="9b24c-131">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_HoloLens2ConfigurationProfile），然后单击“克隆”按钮，创建“DefaultHololens2ConfigurationProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="9b24c-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="9b24c-133">新建的配置配置文件现已分配为场景中的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="9b24c-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="9b24c-135">在 Unity 菜单中，选择“文件” > “保存”以保存场景。 </span><span class="sxs-lookup"><span data-stu-id="9b24c-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="9b24c-136">在学习整篇教程的过程中，请记得保存自己的工作。</span><span class="sxs-lookup"><span data-stu-id="9b24c-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="9b24c-137">2.启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="9b24c-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="9b24c-138">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  </span><span class="sxs-lookup"><span data-stu-id="9b24c-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="9b24c-140">3.克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="9b24c-141">在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="9b24c-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="9b24c-143">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessSystemProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="9b24c-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="9b24c-145">新建的空间感知系统配置文件现已自动分配到你的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="9b24c-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="9b24c-147">4.克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="9b24c-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="9b24c-148">在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：  </span><span class="sxs-lookup"><span data-stu-id="9b24c-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="9b24c-150">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="9b24c-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="9b24c-152">新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="9b24c-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="9b24c-154">5.更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="9b24c-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="9b24c-155">在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  </span><span class="sxs-lookup"><span data-stu-id="9b24c-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9b24c-157">尽管空间映射网格不可见，但它依然存在且可正常运行。</span><span class="sxs-lookup"><span data-stu-id="9b24c-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="9b24c-158">例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="9b24c-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="9b24c-159">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="9b24c-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="9b24c-160">可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="9b24c-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="9b24c-161">由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。</span><span class="sxs-lookup"><span data-stu-id="9b24c-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="9b24c-162">若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [MRTK 配置文件配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="9b24c-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9b24c-163">祝贺</span><span class="sxs-lookup"><span data-stu-id="9b24c-163">Congratulations</span></span>

<span data-ttu-id="9b24c-164">在本教程中，你学习了如何克隆、自定义和配置 MRTK 配置文件和设置。</span><span class="sxs-lookup"><span data-stu-id="9b24c-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="9b24c-165">下一教程：4.定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="9b24c-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
