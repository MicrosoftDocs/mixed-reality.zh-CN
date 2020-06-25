---
title: 场景理解 SDK
description: 场景理解 SDK 的编程指南
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 场景了解，空间映射，Windows Mixed Reality，Unity
ms.openlocfilehash: eb2c6d88ce5a5ba637976a7d67abfdc2763c1674
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345677"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="94f6c-104">场景理解 SDK 概述</span><span class="sxs-lookup"><span data-stu-id="94f6c-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="94f6c-105">场景理解的目标是转换混合现实设备捕获的非结构化环境传感器数据，并将其转换为直观且易于开发的功能强大但更抽象的表示形式。</span><span class="sxs-lookup"><span data-stu-id="94f6c-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="94f6c-106">SDK 充当应用程序和场景了解运行时之间的通信层。</span><span class="sxs-lookup"><span data-stu-id="94f6c-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="94f6c-107">它旨在模拟现有的标准构造，如3D 表示的三维场景图形、2d 矩形和用于2D 应用程序的面板。</span><span class="sxs-lookup"><span data-stu-id="94f6c-107">It's aimed to mimic existing standard constructs such as 3D scene graphs for 3D representations and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="94f6c-108">尽管构造场景了解模拟将映射到你可以使用的具体框架，但在一般情况下，SceneUnderstanding 是框架不可知的，允许在与它交互的可变框架之间进行互操作。</span><span class="sxs-lookup"><span data-stu-id="94f6c-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="94f6c-109">随着场景理解演变，SDK 的作用是确保新的表示形式和功能继续在统一框架内公开。</span><span class="sxs-lookup"><span data-stu-id="94f6c-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="94f6c-110">在本文档中，我们将首先介绍高级概念，这些概念将帮助你熟悉开发环境/用法，并为特定的类和构造提供更详细的文档。</span><span class="sxs-lookup"><span data-stu-id="94f6c-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="94f6c-111">在何处获取 SDK？</span><span class="sxs-lookup"><span data-stu-id="94f6c-111">Where do I get the SDK?</span></span>

<span data-ttu-id="94f6c-112">SceneUnderstanding SDK 可通过 NuGet 下载。</span><span class="sxs-lookup"><span data-stu-id="94f6c-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="94f6c-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="94f6c-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="94f6c-114">**注意：** 最新版本依赖于预览包，你将需要启用预发布包才能查看。</span><span class="sxs-lookup"><span data-stu-id="94f6c-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="94f6c-115">从版本 0.5.2022-rc，场景理解支持 c # 和 c + + 的语言投影，使应用程序可以开发适用于 Win32 或 UWP 平台的应用程序。</span><span class="sxs-lookup"><span data-stu-id="94f6c-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="94f6c-116">在此版本中，SceneUnderstanding 支持 unity 内编辑器支持，禁止使用专用于与 HoloLens2 通信的 SceneObserver。</span><span class="sxs-lookup"><span data-stu-id="94f6c-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="94f6c-117">SceneUnderstanding 需要 Windows SDK 版本18362或更高版本。</span><span class="sxs-lookup"><span data-stu-id="94f6c-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="94f6c-118">如果你使用的是 Unity 项目中的 SDK，请使用[NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity)将包安装到你的项目中。</span><span class="sxs-lookup"><span data-stu-id="94f6c-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="94f6c-119">概念概述</span><span class="sxs-lookup"><span data-stu-id="94f6c-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="94f6c-120">场景</span><span class="sxs-lookup"><span data-stu-id="94f6c-120">The Scene</span></span>

<span data-ttu-id="94f6c-121">混合现实设备会不断集成有关它在你的环境中看到的内容的信息。</span><span class="sxs-lookup"><span data-stu-id="94f6c-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="94f6c-122">场景了解漏斗图所有这些数据源，并生成一个统一的抽象抽象。</span><span class="sxs-lookup"><span data-stu-id="94f6c-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="94f6c-123">场景理解会生成场景，这些场景是[SceneObjects](scene-understanding-SDK.md#sceneobjects)的组成部分，表示单个事物的实例（例如墙壁/天花板/楼层。）场景对象本身是[SceneComponents](scene-understanding-SDK.md#scenecomponents)的组成部分，表示构成此 SceneObject 的更精细的部分。</span><span class="sxs-lookup"><span data-stu-id="94f6c-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="94f6c-124">组件的示例包括四边形和网格，但将来可能表示边界框、冲突网格、元数据等。</span><span class="sxs-lookup"><span data-stu-id="94f6c-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="94f6c-125">将原始传感器数据转换为场景的过程是一项潜在的代价高昂的操作，可能需要几秒钟的时间（约10x10m）到几分钟的时间才能获得非常大的空间（~ 50x50m），因此，不是由没有应用程序请求的设备计算。</span><span class="sxs-lookup"><span data-stu-id="94f6c-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="94f6c-126">相反，应用程序会按需触发场景生成。</span><span class="sxs-lookup"><span data-stu-id="94f6c-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="94f6c-127">SceneObserver 类具有可计算或反序列化场景的静态方法，然后可以使用该场景进行枚举/交互。</span><span class="sxs-lookup"><span data-stu-id="94f6c-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="94f6c-128">"计算" 操作按需执行，在 CPU 上执行，但在单独的进程中执行（混合现实驱动程序）。</span><span class="sxs-lookup"><span data-stu-id="94f6c-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="94f6c-129">但是，虽然我们在另一个进程中进行计算，但生成的场景数据会存储在应用程序的场景对象中并进行维护。</span><span class="sxs-lookup"><span data-stu-id="94f6c-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="94f6c-130">下面的关系图演示了此流程，并显示了两个应用程序与场景理解运行时交互的示例。</span><span class="sxs-lookup"><span data-stu-id="94f6c-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![流程图](images/SU-ProcessFlow.png)

<span data-ttu-id="94f6c-132">左侧是混合现实运行时的关系图，它在自己的进程中始终处于打开和运行状态。</span><span class="sxs-lookup"><span data-stu-id="94f6c-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="94f6c-133">此运行时负责执行设备跟踪、空间映射和其他操作，场景了解使用它来理解和解决世界的相关原因。</span><span class="sxs-lookup"><span data-stu-id="94f6c-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="94f6c-134">在关系图的右侧，我们将显示两个使用场景理解的理论应用程序。</span><span class="sxs-lookup"><span data-stu-id="94f6c-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="94f6c-135">使用 MRTK 的第一个应用程序接口在内部使用场景理解 SDK，第二个应用计算并使用两个单独的场景实例。</span><span class="sxs-lookup"><span data-stu-id="94f6c-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="94f6c-136">此关系图中的所有3个场景都生成了不同场景的不同实例，驱动程序不跟踪在一个场景中的应用程序和场景对象之间共享的全局状态。</span><span class="sxs-lookup"><span data-stu-id="94f6c-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="94f6c-137">场景理解提供一种机制来跟踪时间，但这是使用 SDK 完成的，执行此跟踪的代码将在应用程序的进程中的 SDK 中运行。</span><span class="sxs-lookup"><span data-stu-id="94f6c-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="94f6c-138">由于每个场景会将其数据存储在应用程序的内存空间中，因此，你可以假定场景对象的所有功能或它的内部数据始终在应用程序的进程中执行。</span><span class="sxs-lookup"><span data-stu-id="94f6c-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="94f6c-139">Layout</span><span class="sxs-lookup"><span data-stu-id="94f6c-139">Layout</span></span>

<span data-ttu-id="94f6c-140">若要使用场景理解，了解并了解运行时如何以逻辑方式和物理方式表示组件可能会很有价值。</span><span class="sxs-lookup"><span data-stu-id="94f6c-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="94f6c-141">场景表示具有特定布局的数据，其中选择了简单的布局，同时保持基础结构 pliable，而无需进行重大修改。</span><span class="sxs-lookup"><span data-stu-id="94f6c-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="94f6c-142">场景通过将所有组件（所有场景对象的构建基块）存储在简单列表中，并通过引用（其中特定组件引用其他组件）来定义层次结构和组合来实现此功能。</span><span class="sxs-lookup"><span data-stu-id="94f6c-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="94f6c-143">下面的示例展示了结构的平面和逻辑形式。</span><span class="sxs-lookup"><span data-stu-id="94f6c-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="94f6c-144">逻辑布局</span><span class="sxs-lookup"><span data-stu-id="94f6c-144">Logical Layout</span></span></th><th><span data-ttu-id="94f6c-145">物理布局</span><span class="sxs-lookup"><span data-stu-id="94f6c-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="94f6c-146">场景</span><span class="sxs-lookup"><span data-stu-id="94f6c-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="94f6c-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="94f6c-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="94f6c-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="94f6c-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="94f6c-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="94f6c-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="94f6c-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="94f6c-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="94f6c-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="94f6c-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="94f6c-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="94f6c-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="94f6c-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="94f6c-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="94f6c-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="94f6c-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="94f6c-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="94f6c-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="94f6c-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="94f6c-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="94f6c-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="94f6c-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="94f6c-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="94f6c-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="94f6c-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="94f6c-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="94f6c-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="94f6c-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="94f6c-164">此图重点介绍场景的物理布局和逻辑布局之间的差异。</span><span class="sxs-lookup"><span data-stu-id="94f6c-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="94f6c-165">在左侧，我们将看到你的应用程序在枚举场景时看到的数据的分层布局。</span><span class="sxs-lookup"><span data-stu-id="94f6c-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="94f6c-166">在右侧，我们看到场景实际包含12个不同的组件，这些组件可在必要时单独访问。</span><span class="sxs-lookup"><span data-stu-id="94f6c-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="94f6c-167">处理新场景时，我们希望应用程序以逻辑方式对此层次结构进行遍历，但当在场景更新之间进行跟踪时，某些应用程序可能只对在两个场景之间共享的特定组件感兴趣。</span><span class="sxs-lookup"><span data-stu-id="94f6c-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="94f6c-168">API 概述</span><span class="sxs-lookup"><span data-stu-id="94f6c-168">API overview</span></span>

<span data-ttu-id="94f6c-169">以下部分提供对场景理解中的构造的高级概述。</span><span class="sxs-lookup"><span data-stu-id="94f6c-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="94f6c-170">阅读本部分后，你将了解如何表达场景以及各种组件的用途/用途。</span><span class="sxs-lookup"><span data-stu-id="94f6c-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="94f6c-171">下一节将提供具体的代码示例以及在本概述中 glossed 的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="94f6c-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="94f6c-172">下面所述的所有类型都驻留在 `Microsoft.MixedReality.SceneUnderstanding` 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="94f6c-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="94f6c-173">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="94f6c-173">SceneComponents</span></span>

<span data-ttu-id="94f6c-174">现在，您已经了解了幕后的逻辑布局，接下来可以展示 SceneComponents 的概念，以及如何使用它们来组合层次结构。</span><span class="sxs-lookup"><span data-stu-id="94f6c-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="94f6c-175">SceneComponents 是 SceneUnderstanding 中最精细的分解，表示单个核心事物，例如网格或四个边界框。</span><span class="sxs-lookup"><span data-stu-id="94f6c-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="94f6c-176">SceneComponents 是可以独立更新并可由其他 SceneComponents 引用的项，因此，它们具有一个唯一 Id 的单一全局属性，该属性允许此类跟踪/引用机制。</span><span class="sxs-lookup"><span data-stu-id="94f6c-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="94f6c-177">Id 用于场景层次结构的逻辑组合以及对象持久性（相对于另一场景更新一个场景的操作）。</span><span class="sxs-lookup"><span data-stu-id="94f6c-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="94f6c-178">如果要将每个新计算的场景视为不同的场景，只需枚举其中的所有数据，Id 就会对您很有透明度。</span><span class="sxs-lookup"><span data-stu-id="94f6c-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="94f6c-179">但是，如果打算跟踪多个更新上的组件，则将使用 Id 在场景对象之间建立索引和查找 SceneComponents。</span><span class="sxs-lookup"><span data-stu-id="94f6c-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="94f6c-180">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="94f6c-180">SceneObjects</span></span>

<span data-ttu-id="94f6c-181">SceneObject 是一个 SceneComponent，表示一个 "事物" 的实例，例如墙壁、地面、天花板等 .。。用其 Kind 属性表示。</span><span class="sxs-lookup"><span data-stu-id="94f6c-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="94f6c-182">SceneObjects 是几何，因此具有在空间中表示其位置的函数和属性，但不包含任何几何或逻辑结构。</span><span class="sxs-lookup"><span data-stu-id="94f6c-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="94f6c-183">相反，SceneObjects 引用其他 SceneComponents，特别是 SceneQuads 和 SceneMeshes，它们提供系统支持的各种表示形式。</span><span class="sxs-lookup"><span data-stu-id="94f6c-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="94f6c-184">计算新场景时，应用程序很可能会枚举场景的 SceneObjects，以处理其感兴趣的内容。</span><span class="sxs-lookup"><span data-stu-id="94f6c-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="94f6c-185">SceneObjects 可以包含以下任一项：</span><span class="sxs-lookup"><span data-stu-id="94f6c-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="94f6c-186">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="94f6c-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="94f6c-187">说明</span><span class="sxs-lookup"><span data-stu-id="94f6c-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="94f6c-188">背景</span><span class="sxs-lookup"><span data-stu-id="94f6c-188">Background</span></span></td><td><span data-ttu-id="94f6c-189">已知 SceneObject<b>不</b>是其他已识别的场景对象类型之一。</span><span class="sxs-lookup"><span data-stu-id="94f6c-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="94f6c-190">此类不应与 Unknown 混淆，其中背景已知不是墙壁/楼层/天花板，等等 .。。虽然未知还未分类。</span><span class="sxs-lookup"><span data-stu-id="94f6c-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="94f6c-191">壁</span><span class="sxs-lookup"><span data-stu-id="94f6c-191">Wall</span></span></td><td><span data-ttu-id="94f6c-192">物理墙。</span><span class="sxs-lookup"><span data-stu-id="94f6c-192">A physical wall.</span></span> <span data-ttu-id="94f6c-193">墙壁被认为是可移动的环境结构。</span><span class="sxs-lookup"><span data-stu-id="94f6c-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="94f6c-194">层</span><span class="sxs-lookup"><span data-stu-id="94f6c-194">Floor</span></span></td><td><span data-ttu-id="94f6c-195">楼层是可以进行审核的任何表面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="94f6c-196">注意：楼梯不是楼层。</span><span class="sxs-lookup"><span data-stu-id="94f6c-196">Note: stairs are not floors.</span></span> <span data-ttu-id="94f6c-197">另请注意，该楼层假设有任何不可的表面，因此没有显式假设。</span><span class="sxs-lookup"><span data-stu-id="94f6c-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="94f6c-198">多层结构，斜坡等 .。。应将所有分类为楼层。</span><span class="sxs-lookup"><span data-stu-id="94f6c-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="94f6c-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="94f6c-199">Ceiling</span></span></td><td><span data-ttu-id="94f6c-200">房间的上部面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="94f6c-201">Platform</span><span class="sxs-lookup"><span data-stu-id="94f6c-201">Platform</span></span></td><td><span data-ttu-id="94f6c-202">一个大平面，可以在其上放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="94f6c-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="94f6c-203">它们倾向于表示表、countertops 和其他大型水平曲面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="94f6c-204">World</span><span class="sxs-lookup"><span data-stu-id="94f6c-204">World</span></span></td><td><span data-ttu-id="94f6c-205">标记不可知的几何数据的保留标签。</span><span class="sxs-lookup"><span data-stu-id="94f6c-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="94f6c-206">通过设置 EnableWorldMesh 更新标志生成的网格将归为 "世界"。</span><span class="sxs-lookup"><span data-stu-id="94f6c-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="94f6c-207">未知</span><span class="sxs-lookup"><span data-stu-id="94f6c-207">Unknown</span></span></td><td><span data-ttu-id="94f6c-208">尚未对此场景对象进行分类并为其分配一种类型。</span><span class="sxs-lookup"><span data-stu-id="94f6c-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="94f6c-209">这不应与背景混淆，因为此对象可能是任何内容，而系统刚刚没有提供足够强大的分类。</span><span class="sxs-lookup"><span data-stu-id="94f6c-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="94f6c-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="94f6c-210">SceneMesh</span></span>

<span data-ttu-id="94f6c-211">SceneMesh 是一种 SceneComponent，它使用三角形列表来模拟任意几何对象的几何。</span><span class="sxs-lookup"><span data-stu-id="94f6c-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="94f6c-212">SceneMeshes 用于多个不同的上下文中，它们可以表示 watertight 单元结构的组件，或表示与场景关联的未绑定空间映射网格的 WorldMesh。</span><span class="sxs-lookup"><span data-stu-id="94f6c-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="94f6c-213">每个网格提供的索引和顶点数据使用与用于在所有新式渲染 Api 中呈现三角形网格的[顶点和索引缓冲区](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx)相同的熟悉布局。</span><span class="sxs-lookup"><span data-stu-id="94f6c-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="94f6c-214">请注意，在场景理解中，网格使用32位索引，可能需要分解为某些呈现引擎的块。</span><span class="sxs-lookup"><span data-stu-id="94f6c-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="94f6c-215">缠绕顺序和坐标系统</span><span class="sxs-lookup"><span data-stu-id="94f6c-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="94f6c-216">场景理解生成的所有网格都应该使用顺时针缠绕顺序在右手坐标系内返回网格。</span><span class="sxs-lookup"><span data-stu-id="94f6c-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="94f6c-217">注意：版本之前的操作系统版本。191105可能有一个已知 bug，其中 "World" 网格以逆时针缠绕顺序返回，后者随后已修复。</span><span class="sxs-lookup"><span data-stu-id="94f6c-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="94f6c-218">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="94f6c-218">SceneQuad</span></span>

<span data-ttu-id="94f6c-219">SceneQuad 是一个 SceneComponent，它表示占据三维世界的2d 面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="94f6c-220">SceneQuads 可以与 ARKit ARPlaneAnchor 或 ARCore 平面相似，但它们提供了更高级别的功能，如要由平面应用程序使用的2d 画布，或更高的 UX。</span><span class="sxs-lookup"><span data-stu-id="94f6c-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="94f6c-221">为四边形提供了2D 特定的 Api，使放置和布局简单易用，并使用四边形进行开发（但着色除外）时，其感觉比使用3d 网格的2d 画布更加类似。</span><span class="sxs-lookup"><span data-stu-id="94f6c-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="94f6c-222">SceneQuad 形状</span><span class="sxs-lookup"><span data-stu-id="94f6c-222">SceneQuad shape</span></span>

<span data-ttu-id="94f6c-223">SceneQuads 在2d 中定义边界矩形图面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="94f6c-224">但是，SceneQuads 表示具有任意和可能复杂的形状的图面（如环形形状的表）。若要表示四部分的复杂形状，可以使用 GetSurfaceMask API 将图面上的形状呈现到提供的图像缓冲区。</span><span class="sxs-lookup"><span data-stu-id="94f6c-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="94f6c-225">如果具有四部分的 SceneObject 还具有网格，则网格三角形应等效于此呈现的图像，它们都表示图面的实坐标，只是在2d 或3d 坐标中。</span><span class="sxs-lookup"><span data-stu-id="94f6c-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="94f6c-226">场景理解 SDK 详细信息和参考</span><span class="sxs-lookup"><span data-stu-id="94f6c-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="94f6c-227">以下部分将帮助你熟悉 SceneUnderstanding 的基础知识。</span><span class="sxs-lookup"><span data-stu-id="94f6c-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="94f6c-228">本部分应为你提供基础知识，此时你应该具有足够的上下文来浏览示例应用程序，以了解如何整体使用 SceneUnderstanding。</span><span class="sxs-lookup"><span data-stu-id="94f6c-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="94f6c-229">初始化</span><span class="sxs-lookup"><span data-stu-id="94f6c-229">Initialization</span></span>

<span data-ttu-id="94f6c-230">使用 SceneUnderstanding 的第一步是让应用程序获取对场景对象的引用。</span><span class="sxs-lookup"><span data-stu-id="94f6c-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="94f6c-231">可以通过以下两种方式之一完成此操作：可以通过驱动程序计算场景，也可以反序列化过去计算的现有场景。</span><span class="sxs-lookup"><span data-stu-id="94f6c-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="94f6c-232">后者对于在开发过程中使用 SceneUnderstanding 特别有用，在这种情况下，应用程序和体验可以在没有混合现实设备的情况下快速建立原型。</span><span class="sxs-lookup"><span data-stu-id="94f6c-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="94f6c-233">使用 SceneObserver 计算场景。</span><span class="sxs-lookup"><span data-stu-id="94f6c-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="94f6c-234">在创建场景之前，应用程序应查询你的设备以确保它支持 SceneUnderstanding，并请求用户访问以获取 SceneUnderstanding 所需的信息。</span><span class="sxs-lookup"><span data-stu-id="94f6c-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="94f6c-235">如果未调用 RequestAccessAsync （），计算新场景将会失败。</span><span class="sxs-lookup"><span data-stu-id="94f6c-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="94f6c-236">接下来，我们将计算一个围绕混合现实耳机的新场景，具有10米半径。</span><span class="sxs-lookup"><span data-stu-id="94f6c-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="94f6c-237">从数据初始化（亦即</span><span class="sxs-lookup"><span data-stu-id="94f6c-237">Initialization from Data (aka.</span></span> <span data-ttu-id="94f6c-238">PC 路径）</span><span class="sxs-lookup"><span data-stu-id="94f6c-238">the PC Path)</span></span>

<span data-ttu-id="94f6c-239">尽管可以计算用于直接使用的场景，但也可以使用序列化形式计算，以便以后使用。</span><span class="sxs-lookup"><span data-stu-id="94f6c-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="94f6c-240">证明这对于开发非常有用，因为它允许开发人员在无需设备的情况下使用和测试场景理解。</span><span class="sxs-lookup"><span data-stu-id="94f6c-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="94f6c-241">序列化场景的操作与计算场景几乎完全相同，数据将返回到应用程序，而不是由 SDK 在本地反序列化。</span><span class="sxs-lookup"><span data-stu-id="94f6c-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="94f6c-242">然后，你可以自行反序列化它或将其保存以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="94f6c-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="94f6c-243">SceneObject 枚举</span><span class="sxs-lookup"><span data-stu-id="94f6c-243">SceneObject Enumeration</span></span>

<span data-ttu-id="94f6c-244">现在，你的应用程序有场景，你的应用程序将查看和与 SceneObjects 交互。</span><span class="sxs-lookup"><span data-stu-id="94f6c-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="94f6c-245">这可以通过访问**SceneObjects**属性来完成：</span><span class="sxs-lookup"><span data-stu-id="94f6c-245">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="94f6c-246">组件更新和重新查找组件</span><span class="sxs-lookup"><span data-stu-id="94f6c-246">Component update and re-finding components</span></span>

<span data-ttu-id="94f6c-247">还有另一个函数，可检索场景（称为***FindComponent***）中的组件。</span><span class="sxs-lookup"><span data-stu-id="94f6c-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="94f6c-248">当更新跟踪对象并在后续场景中查找它们时，此函数很有用。</span><span class="sxs-lookup"><span data-stu-id="94f6c-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="94f6c-249">下面的代码将计算一个相对于以前场景的新场景，然后在新场景中查找楼层。</span><span class="sxs-lookup"><span data-stu-id="94f6c-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="94f6c-250">从场景对象访问网格和四边形</span><span class="sxs-lookup"><span data-stu-id="94f6c-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="94f6c-251">找到 SceneObjects 后，你的应用程序很可能想要访问包含在其中的四边形/网格中的数据。</span><span class="sxs-lookup"><span data-stu-id="94f6c-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="94f6c-252">可以通过***四边形***和***网格***属性访问此数据。</span><span class="sxs-lookup"><span data-stu-id="94f6c-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="94f6c-253">下面的代码将枚举地面对象的所有四边形和网格。</span><span class="sxs-lookup"><span data-stu-id="94f6c-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="94f6c-254">请注意，它是相对于场景原点的转换的 SceneObject。</span><span class="sxs-lookup"><span data-stu-id="94f6c-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="94f6c-255">这是因为 SceneObject 表示 "事物" 的实例，在空间中可定位，四边形和网格表示相对于其父级转换的几何图形。</span><span class="sxs-lookup"><span data-stu-id="94f6c-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="94f6c-256">单独的 SceneObjects 可以引用相同的 SceneMesh/SceneQuad SceneComponents，也可能是 SceneObject 有多个 SceneMesh/SceneQuad。</span><span class="sxs-lookup"><span data-stu-id="94f6c-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="94f6c-257">处理转换</span><span class="sxs-lookup"><span data-stu-id="94f6c-257">Dealing with Transforms</span></span>

<span data-ttu-id="94f6c-258">在处理转换时，场景理解已精心尝试与传统的三维场景表示。</span><span class="sxs-lookup"><span data-stu-id="94f6c-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="94f6c-259">因此，每个场景都局限于一个坐标系统，这与大多数常见的3D 环境表示形式非常类似。</span><span class="sxs-lookup"><span data-stu-id="94f6c-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="94f6c-260">每个 SceneObjects 都提供它们在该坐标系中的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="94f6c-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="94f6c-261">如果你的应用程序正在处理的场景会延伸到单个源所提供的限制，则可以将 SceneObjects 定位到 SpatialAnchors，或生成多个场景并将它们合并在一起，但为了简单起见，我们假定 watertight 场景位于其自身的源中，而该已由由场景 OriginSpatialGraphNodeId 定义的一个本地化。</span><span class="sxs-lookup"><span data-stu-id="94f6c-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="94f6c-262">例如，以下 Unity 代码演示了如何使用 Windows 感知和 Unity Api 来协调坐标系。</span><span class="sxs-lookup"><span data-stu-id="94f6c-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="94f6c-263">若要[详细了解如何](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced)获取与 unity 世界原点对应的 SpatialCoordinateSystem，以及用于在和之间进行转换的扩展方法的详细信息，请参阅[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)和[SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) 。 `.ToUnity()` `System.Numerics.Matrix4x4` `UnityEngine.Matrix4x4`</span><span class="sxs-lookup"><span data-stu-id="94f6c-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

<span data-ttu-id="94f6c-264">每个 `SceneObject` 都有一个 `Position` 和 `Orientation` 属性，该属性可用于相对于包含的源定位相应的内容 `Scene` 。</span><span class="sxs-lookup"><span data-stu-id="94f6c-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="94f6c-265">例如，下面的示例假定游戏是场景根的子元素，并分配其本地位置和旋转，使其与给定的对齐 `SceneObject` ：</span><span class="sxs-lookup"><span data-stu-id="94f6c-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="94f6c-266">十字</span><span class="sxs-lookup"><span data-stu-id="94f6c-266">Quad</span></span>

<span data-ttu-id="94f6c-267">四边形旨在简化2D 布局方案，并应被视为2D 画布 UX 元素的扩展。</span><span class="sxs-lookup"><span data-stu-id="94f6c-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="94f6c-268">尽管四边形是 SceneObjects 的组件并且可以在3D 中呈现，但四个 Api 本身假设四边形是2D 结构。</span><span class="sxs-lookup"><span data-stu-id="94f6c-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="94f6c-269">它们提供了信息（如区、形状），并提供了用于放置的 Api。</span><span class="sxs-lookup"><span data-stu-id="94f6c-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="94f6c-270">四边形具有矩形区，但它们表示任意形状的2D 图面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="94f6c-271">若要在与3D 环境四边形的图面上实现放置，使此交互成为可能。</span><span class="sxs-lookup"><span data-stu-id="94f6c-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="94f6c-272">当前场景理解提供了两个此类函数： **FindCentermostPlacement**和**GetOcclusionMask**。</span><span class="sxs-lookup"><span data-stu-id="94f6c-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="94f6c-273">FindCentermostPlacement 是一种高级的 API，用于定位四个位置上的一个对象，并尝试查找您的对象的最佳位置，以确保您提供的边界框位于底层图面上。</span><span class="sxs-lookup"><span data-stu-id="94f6c-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="94f6c-274">下面的示例演示如何查找 centermost 可放置位置并将全息图定位到四个部分。</span><span class="sxs-lookup"><span data-stu-id="94f6c-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="94f6c-275">步骤1-4 依赖于特定的框架/实现，但主题应类似。</span><span class="sxs-lookup"><span data-stu-id="94f6c-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="94f6c-276">请注意，四个部分只表示在空间中进行了本地化的界限2D 平面。</span><span class="sxs-lookup"><span data-stu-id="94f6c-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="94f6c-277">通过让引擎/框架知道四个部分，并相对于四个部分定位对象，您的全息影像会正确地定位到现实世界。</span><span class="sxs-lookup"><span data-stu-id="94f6c-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> <span data-ttu-id="94f6c-278">有关更多详细信息，请参阅四边形上的示例，这些示例显示特定实现。</span><span class="sxs-lookup"><span data-stu-id="94f6c-278">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="94f6c-279">网格</span><span class="sxs-lookup"><span data-stu-id="94f6c-279">Mesh</span></span>

<span data-ttu-id="94f6c-280">网格表示对象或环境的几何表示形式。</span><span class="sxs-lookup"><span data-stu-id="94f6c-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="94f6c-281">与每个空间 surface 网格一起提供的[空间映射](spatial-mapping.md)、网格索引和顶点数据非常类似于在所有新式渲染 api 中用于呈现三角形网格的顶点和索引缓冲区。</span><span class="sxs-lookup"><span data-stu-id="94f6c-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="94f6c-282">顶点位置在的坐标系统中提供 `Scene` 。</span><span class="sxs-lookup"><span data-stu-id="94f6c-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="94f6c-283">用于引用此数据的特定 Api 如下所示：</span><span class="sxs-lookup"><span data-stu-id="94f6c-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="94f6c-284">下面的代码提供了一个示例，说明如何从网格结构生成三角形列表：</span><span class="sxs-lookup"><span data-stu-id="94f6c-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="94f6c-285">索引/顶点缓冲区必须是 >= 索引/顶点计数，但也可以任意调整大小以允许有效的内存重复使用。</span><span class="sxs-lookup"><span data-stu-id="94f6c-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="94f6c-286">用场景理解进行开发</span><span class="sxs-lookup"><span data-stu-id="94f6c-286">Developing with scene understandings</span></span>

<span data-ttu-id="94f6c-287">此时，你应该了解场景的核心构建基块了解运行时和 SDK。</span><span class="sxs-lookup"><span data-stu-id="94f6c-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="94f6c-288">大容量和复杂性在于访问模式、与3D 框架的交互，以及可以在这些 Api 之上编写的工具，以执行更高级的任务，例如空间规划、房间分析、导航、物理学等。我们想要在示例中捕获这些示例，这些示例应指导您正确地指导您的场景。</span><span class="sxs-lookup"><span data-stu-id="94f6c-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="94f6c-289">如果有我们未解决的示例/方案，请告知我们，我们将尝试记录/原型所需的内容。</span><span class="sxs-lookup"><span data-stu-id="94f6c-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="94f6c-290">在哪里可以获取示例代码？</span><span class="sxs-lookup"><span data-stu-id="94f6c-290">Where can I get sample code?</span></span>

<span data-ttu-id="94f6c-291">可在[Unity 示例页](https://github.com/sceneunderstanding-microsoft/unitysample)页面上了解 unity 的示例代码。</span><span class="sxs-lookup"><span data-stu-id="94f6c-291">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="94f6c-292">此应用程序将允许你与设备进行通信并呈现各种场景对象，或者，它允许你将序列化场景加载到电脑上，并允许你在不使用设备的情况下体验场景。</span><span class="sxs-lookup"><span data-stu-id="94f6c-292">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="94f6c-293">在哪里可以获取示例场景？</span><span class="sxs-lookup"><span data-stu-id="94f6c-293">Where can I get sample scenes?</span></span>

<span data-ttu-id="94f6c-294">如果你有 HoloLens2，则可以通过将 ComputeSerializedAsync 的输出保存到文件，并在方便时反序列化，来保存已捕获的任何场景。</span><span class="sxs-lookup"><span data-stu-id="94f6c-294">If you have a HoloLens2 you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="94f6c-295">如果你没有 HoloLens2 设备，但想要在场景理解的情况上播放，则需要下载预捕获的场景。</span><span class="sxs-lookup"><span data-stu-id="94f6c-295">If you do not have a HoloLens2 device but want to play with Scene Understanding you will need to download a pre-captured scene.</span></span> <span data-ttu-id="94f6c-296">场景理解示例当前附带了序列化场景，可以在方便的时候下载和使用。</span><span class="sxs-lookup"><span data-stu-id="94f6c-296">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="94f6c-297">可在此处找到它们：</span><span class="sxs-lookup"><span data-stu-id="94f6c-297">You can find them here:</span></span>

[<span data-ttu-id="94f6c-298">场景了解示例场景</span><span class="sxs-lookup"><span data-stu-id="94f6c-298">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="94f6c-299">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94f6c-299">See also</span></span>

* [<span data-ttu-id="94f6c-300">空间映射</span><span class="sxs-lookup"><span data-stu-id="94f6c-300">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="94f6c-301">场景理解</span><span class="sxs-lookup"><span data-stu-id="94f6c-301">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="94f6c-302">Unity 示例</span><span class="sxs-lookup"><span data-stu-id="94f6c-302">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
