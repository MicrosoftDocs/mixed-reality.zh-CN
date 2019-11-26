---
title: Scene understanding SDK
description: Programming guide to the Scene Understanding SDK
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: f38145c4124a9f162e58188c6179dc29c22e864e
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491127"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="e99cf-104">Scene understanding SDK overview</span><span class="sxs-lookup"><span data-stu-id="e99cf-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="e99cf-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span><span class="sxs-lookup"><span data-stu-id="e99cf-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="e99cf-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span><span class="sxs-lookup"><span data-stu-id="e99cf-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="e99cf-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span><span class="sxs-lookup"><span data-stu-id="e99cf-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="e99cf-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span><span class="sxs-lookup"><span data-stu-id="e99cf-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="e99cf-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span><span class="sxs-lookup"><span data-stu-id="e99cf-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="e99cf-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span><span class="sxs-lookup"><span data-stu-id="e99cf-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="e99cf-111">Where do I get the SDK?</span><span class="sxs-lookup"><span data-stu-id="e99cf-111">Where do I get the SDK?</span></span>

<span data-ttu-id="e99cf-112">The SceneUnderstanding SDK is downloadable via NuGet.</span><span class="sxs-lookup"><span data-stu-id="e99cf-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="e99cf-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="e99cf-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="e99cf-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span><span class="sxs-lookup"><span data-stu-id="e99cf-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="e99cf-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span><span class="sxs-lookup"><span data-stu-id="e99cf-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="e99cf-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="e99cf-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="e99cf-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span><span class="sxs-lookup"><span data-stu-id="e99cf-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="e99cf-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span><span class="sxs-lookup"><span data-stu-id="e99cf-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="e99cf-119">Conceptual Overview</span><span class="sxs-lookup"><span data-stu-id="e99cf-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="e99cf-120">The Scene</span><span class="sxs-lookup"><span data-stu-id="e99cf-120">The Scene</span></span>

<span data-ttu-id="e99cf-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span><span class="sxs-lookup"><span data-stu-id="e99cf-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="e99cf-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span><span class="sxs-lookup"><span data-stu-id="e99cf-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="e99cf-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span><span class="sxs-lookup"><span data-stu-id="e99cf-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="e99cf-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span><span class="sxs-lookup"><span data-stu-id="e99cf-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="e99cf-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span><span class="sxs-lookup"><span data-stu-id="e99cf-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="e99cf-126">Instead, Scene generation is triggered by your application on demand.</span><span class="sxs-lookup"><span data-stu-id="e99cf-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="e99cf-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span><span class="sxs-lookup"><span data-stu-id="e99cf-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="e99cf-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span><span class="sxs-lookup"><span data-stu-id="e99cf-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="e99cf-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span><span class="sxs-lookup"><span data-stu-id="e99cf-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="e99cf-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span><span class="sxs-lookup"><span data-stu-id="e99cf-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Process Diagram](images/SU-ProcessFlow.png)

<span data-ttu-id="e99cf-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span><span class="sxs-lookup"><span data-stu-id="e99cf-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="e99cf-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span><span class="sxs-lookup"><span data-stu-id="e99cf-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="e99cf-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="e99cf-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="e99cf-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span><span class="sxs-lookup"><span data-stu-id="e99cf-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="e99cf-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span><span class="sxs-lookup"><span data-stu-id="e99cf-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="e99cf-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span><span class="sxs-lookup"><span data-stu-id="e99cf-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="e99cf-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span><span class="sxs-lookup"><span data-stu-id="e99cf-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="e99cf-139">布局</span><span class="sxs-lookup"><span data-stu-id="e99cf-139">Layout</span></span>

<span data-ttu-id="e99cf-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span><span class="sxs-lookup"><span data-stu-id="e99cf-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="e99cf-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span><span class="sxs-lookup"><span data-stu-id="e99cf-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="e99cf-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span><span class="sxs-lookup"><span data-stu-id="e99cf-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="e99cf-143">Below we present an example of a structure in both its flat and logical form.</span><span class="sxs-lookup"><span data-stu-id="e99cf-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="e99cf-144">Logical Layout</span><span class="sxs-lookup"><span data-stu-id="e99cf-144">Logical Layout</span></span></th><th><span data-ttu-id="e99cf-145">Physical Layout</span><span class="sxs-lookup"><span data-stu-id="e99cf-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="e99cf-146">Scene</span><span class="sxs-lookup"><span data-stu-id="e99cf-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="e99cf-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="e99cf-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="e99cf-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="e99cf-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="e99cf-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="e99cf-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="e99cf-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="e99cf-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="e99cf-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="e99cf-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="e99cf-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="e99cf-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="e99cf-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="e99cf-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="e99cf-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="e99cf-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="e99cf-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="e99cf-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="e99cf-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="e99cf-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="e99cf-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="e99cf-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="e99cf-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="e99cf-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="e99cf-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="e99cf-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="e99cf-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="e99cf-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="e99cf-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span><span class="sxs-lookup"><span data-stu-id="e99cf-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="e99cf-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span><span class="sxs-lookup"><span data-stu-id="e99cf-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="e99cf-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span><span class="sxs-lookup"><span data-stu-id="e99cf-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="e99cf-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span><span class="sxs-lookup"><span data-stu-id="e99cf-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="e99cf-168">API 概述</span><span class="sxs-lookup"><span data-stu-id="e99cf-168">API overview</span></span>

<span data-ttu-id="e99cf-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="e99cf-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="e99cf-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span><span class="sxs-lookup"><span data-stu-id="e99cf-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="e99cf-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span><span class="sxs-lookup"><span data-stu-id="e99cf-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="e99cf-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span><span class="sxs-lookup"><span data-stu-id="e99cf-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="e99cf-173">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="e99cf-173">SceneComponents</span></span>

<span data-ttu-id="e99cf-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span><span class="sxs-lookup"><span data-stu-id="e99cf-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="e99cf-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span><span class="sxs-lookup"><span data-stu-id="e99cf-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="e99cf-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span><span class="sxs-lookup"><span data-stu-id="e99cf-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="e99cf-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span><span class="sxs-lookup"><span data-stu-id="e99cf-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="e99cf-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span><span class="sxs-lookup"><span data-stu-id="e99cf-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="e99cf-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span><span class="sxs-lookup"><span data-stu-id="e99cf-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="e99cf-180">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="e99cf-180">SceneObjects</span></span>

<span data-ttu-id="e99cf-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span><span class="sxs-lookup"><span data-stu-id="e99cf-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="e99cf-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span><span class="sxs-lookup"><span data-stu-id="e99cf-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="e99cf-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span><span class="sxs-lookup"><span data-stu-id="e99cf-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="e99cf-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span><span class="sxs-lookup"><span data-stu-id="e99cf-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="e99cf-185">SceneObjects can have any one of the following:</span><span class="sxs-lookup"><span data-stu-id="e99cf-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="e99cf-186">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="e99cf-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="e99cf-187">描述</span><span class="sxs-lookup"><span data-stu-id="e99cf-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="e99cf-188">后台</span><span class="sxs-lookup"><span data-stu-id="e99cf-188">Background</span></span></td><td><span data-ttu-id="e99cf-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span><span class="sxs-lookup"><span data-stu-id="e99cf-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="e99cf-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span><span class="sxs-lookup"><span data-stu-id="e99cf-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="e99cf-191">Wall</span><span class="sxs-lookup"><span data-stu-id="e99cf-191">Wall</span></span></td><td><span data-ttu-id="e99cf-192">A physical wall.</span><span class="sxs-lookup"><span data-stu-id="e99cf-192">A physical wall.</span></span> <span data-ttu-id="e99cf-193">Walls are assumed to be immovable environmental structures.</span><span class="sxs-lookup"><span data-stu-id="e99cf-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="e99cf-194">Floor</span><span class="sxs-lookup"><span data-stu-id="e99cf-194">Floor</span></span></td><td><span data-ttu-id="e99cf-195">Floors are any surfaces on which one can walk.</span><span class="sxs-lookup"><span data-stu-id="e99cf-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="e99cf-196">Note: stairs are not floors.</span><span class="sxs-lookup"><span data-stu-id="e99cf-196">Note: stairs are not floors.</span></span> <span data-ttu-id="e99cf-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span><span class="sxs-lookup"><span data-stu-id="e99cf-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="e99cf-198">Multi-level structures, ramps etc... should all classify as floor.</span><span class="sxs-lookup"><span data-stu-id="e99cf-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="e99cf-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="e99cf-199">Ceiling</span></span></td><td><span data-ttu-id="e99cf-200">The upper surface of a room.</span><span class="sxs-lookup"><span data-stu-id="e99cf-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="e99cf-201">平台</span><span class="sxs-lookup"><span data-stu-id="e99cf-201">Platform</span></span></td><td><span data-ttu-id="e99cf-202">A large flat surface on which you could place holograms.</span><span class="sxs-lookup"><span data-stu-id="e99cf-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="e99cf-203">These tend to represent tables, countertops and other large horizontal surfaces.</span><span class="sxs-lookup"><span data-stu-id="e99cf-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="e99cf-204">世界</span><span class="sxs-lookup"><span data-stu-id="e99cf-204">World</span></span></td><td><span data-ttu-id="e99cf-205">A reserved label for geometric data that is agnostic to labeling.</span><span class="sxs-lookup"><span data-stu-id="e99cf-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="e99cf-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span><span class="sxs-lookup"><span data-stu-id="e99cf-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="e99cf-207">Unknown</span><span class="sxs-lookup"><span data-stu-id="e99cf-207">Unknown</span></span></td><td><span data-ttu-id="e99cf-208">This scene object has yet to be classified and assigned a kind.</span><span class="sxs-lookup"><span data-stu-id="e99cf-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="e99cf-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span><span class="sxs-lookup"><span data-stu-id="e99cf-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="e99cf-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="e99cf-210">SceneMesh</span></span>

<span data-ttu-id="e99cf-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span><span class="sxs-lookup"><span data-stu-id="e99cf-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="e99cf-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span><span class="sxs-lookup"><span data-stu-id="e99cf-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="e99cf-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span><span class="sxs-lookup"><span data-stu-id="e99cf-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="e99cf-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span><span class="sxs-lookup"><span data-stu-id="e99cf-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="e99cf-215">Winding Order and Coordinate Systems</span><span class="sxs-lookup"><span data-stu-id="e99cf-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="e99cf-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span><span class="sxs-lookup"><span data-stu-id="e99cf-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="e99cf-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span><span class="sxs-lookup"><span data-stu-id="e99cf-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="e99cf-218">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="e99cf-218">SceneQuad</span></span>

<span data-ttu-id="e99cf-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span><span class="sxs-lookup"><span data-stu-id="e99cf-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="e99cf-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span><span class="sxs-lookup"><span data-stu-id="e99cf-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="e99cf-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span><span class="sxs-lookup"><span data-stu-id="e99cf-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="e99cf-222">SceneQuad shape</span><span class="sxs-lookup"><span data-stu-id="e99cf-222">SceneQuad shape</span></span>

<span data-ttu-id="e99cf-223">SceneQuads define a bounded rectangular surface in 2d.</span><span class="sxs-lookup"><span data-stu-id="e99cf-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="e99cf-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span><span class="sxs-lookup"><span data-stu-id="e99cf-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="e99cf-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span><span class="sxs-lookup"><span data-stu-id="e99cf-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="e99cf-226">Scene understanding SDK details and reference</span><span class="sxs-lookup"><span data-stu-id="e99cf-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="e99cf-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="e99cf-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="e99cf-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span><span class="sxs-lookup"><span data-stu-id="e99cf-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="e99cf-229">初始化</span><span class="sxs-lookup"><span data-stu-id="e99cf-229">Initialization</span></span>

<span data-ttu-id="e99cf-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span><span class="sxs-lookup"><span data-stu-id="e99cf-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="e99cf-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span><span class="sxs-lookup"><span data-stu-id="e99cf-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="e99cf-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span><span class="sxs-lookup"><span data-stu-id="e99cf-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="e99cf-233">Scenes are computed using a SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="e99cf-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="e99cf-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span><span class="sxs-lookup"><span data-stu-id="e99cf-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="e99cf-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span><span class="sxs-lookup"><span data-stu-id="e99cf-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="e99cf-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span><span class="sxs-lookup"><span data-stu-id="e99cf-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

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

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="e99cf-237">Initialization from Data (aka.</span><span class="sxs-lookup"><span data-stu-id="e99cf-237">Initialization from Data (aka.</span></span> <span data-ttu-id="e99cf-238">the PC Path)</span><span class="sxs-lookup"><span data-stu-id="e99cf-238">the PC Path)</span></span>

<span data-ttu-id="e99cf-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span><span class="sxs-lookup"><span data-stu-id="e99cf-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="e99cf-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span><span class="sxs-lookup"><span data-stu-id="e99cf-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="e99cf-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span><span class="sxs-lookup"><span data-stu-id="e99cf-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="e99cf-242">You may then deserialize it yourself or save it for future use.</span><span class="sxs-lookup"><span data-stu-id="e99cf-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="e99cf-243">SceneObject Enumeration</span><span class="sxs-lookup"><span data-stu-id="e99cf-243">SceneObject Enumeration</span></span>

<span data-ttu-id="e99cf-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="e99cf-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="e99cf-245">This is done by accessing the **SceneObjects** property:</span><span class="sxs-lookup"><span data-stu-id="e99cf-245">This is done by accessing the **SceneObjects** property:</span></span>

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

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="e99cf-246">Component update and re-finding components</span><span class="sxs-lookup"><span data-stu-id="e99cf-246">Component update and re-finding components</span></span>

<span data-ttu-id="e99cf-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span><span class="sxs-lookup"><span data-stu-id="e99cf-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="e99cf-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span><span class="sxs-lookup"><span data-stu-id="e99cf-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="e99cf-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span><span class="sxs-lookup"><span data-stu-id="e99cf-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="e99cf-250">Accessing Meshes and Quads from Scene Objects</span><span class="sxs-lookup"><span data-stu-id="e99cf-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="e99cf-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span><span class="sxs-lookup"><span data-stu-id="e99cf-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="e99cf-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span><span class="sxs-lookup"><span data-stu-id="e99cf-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="e99cf-253">The following code will enumerate all quads and meshes of our floor object.</span><span class="sxs-lookup"><span data-stu-id="e99cf-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

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

<span data-ttu-id="e99cf-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span><span class="sxs-lookup"><span data-stu-id="e99cf-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="e99cf-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span><span class="sxs-lookup"><span data-stu-id="e99cf-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="e99cf-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="e99cf-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="e99cf-257">Dealing with Transforms</span><span class="sxs-lookup"><span data-stu-id="e99cf-257">Dealing with Transforms</span></span>

<span data-ttu-id="e99cf-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span><span class="sxs-lookup"><span data-stu-id="e99cf-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="e99cf-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span><span class="sxs-lookup"><span data-stu-id="e99cf-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="e99cf-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span><span class="sxs-lookup"><span data-stu-id="e99cf-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="e99cf-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="e99cf-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="e99cf-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span><span class="sxs-lookup"><span data-stu-id="e99cf-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="e99cf-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span><span class="sxs-lookup"><span data-stu-id="e99cf-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

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

<span data-ttu-id="e99cf-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span><span class="sxs-lookup"><span data-stu-id="e99cf-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="e99cf-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span><span class="sxs-lookup"><span data-stu-id="e99cf-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="e99cf-266">Quad</span><span class="sxs-lookup"><span data-stu-id="e99cf-266">Quad</span></span>

<span data-ttu-id="e99cf-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span><span class="sxs-lookup"><span data-stu-id="e99cf-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="e99cf-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span><span class="sxs-lookup"><span data-stu-id="e99cf-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="e99cf-269">They offer information such as extent, shape, and provide APIs for placement.</span><span class="sxs-lookup"><span data-stu-id="e99cf-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="e99cf-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span><span class="sxs-lookup"><span data-stu-id="e99cf-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="e99cf-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span><span class="sxs-lookup"><span data-stu-id="e99cf-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="e99cf-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span><span class="sxs-lookup"><span data-stu-id="e99cf-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="e99cf-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span><span class="sxs-lookup"><span data-stu-id="e99cf-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="e99cf-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span><span class="sxs-lookup"><span data-stu-id="e99cf-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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

<span data-ttu-id="e99cf-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span><span class="sxs-lookup"><span data-stu-id="e99cf-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="e99cf-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span><span class="sxs-lookup"><span data-stu-id="e99cf-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="e99cf-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span><span class="sxs-lookup"><span data-stu-id="e99cf-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> <span data-ttu-id="e99cf-278">For more detailed information please see our samples on quads which show specific implementations.</span><span class="sxs-lookup"><span data-stu-id="e99cf-278">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="e99cf-279">Mesh</span><span class="sxs-lookup"><span data-stu-id="e99cf-279">Mesh</span></span>

<span data-ttu-id="e99cf-280">Meshes represent geometric representations of objects or environments.</span><span class="sxs-lookup"><span data-stu-id="e99cf-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="e99cf-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span><span class="sxs-lookup"><span data-stu-id="e99cf-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="e99cf-282">Vertex positions are provided in the coordinate system of the `Scene`.</span><span class="sxs-lookup"><span data-stu-id="e99cf-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="e99cf-283">The specific APIs used to reference this data are as follows:</span><span class="sxs-lookup"><span data-stu-id="e99cf-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="e99cf-284">The following code provides an example of generating a triangle list from the mesh structure:</span><span class="sxs-lookup"><span data-stu-id="e99cf-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="e99cf-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span><span class="sxs-lookup"><span data-stu-id="e99cf-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="e99cf-286">Developing with scene understandings</span><span class="sxs-lookup"><span data-stu-id="e99cf-286">Developing with scene understandings</span></span>

<span data-ttu-id="e99cf-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span><span class="sxs-lookup"><span data-stu-id="e99cf-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="e99cf-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span><span class="sxs-lookup"><span data-stu-id="e99cf-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="e99cf-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span><span class="sxs-lookup"><span data-stu-id="e99cf-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="e99cf-290">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e99cf-290">See also</span></span>

* [<span data-ttu-id="e99cf-291">空间映射</span><span class="sxs-lookup"><span data-stu-id="e99cf-291">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="e99cf-292">场景理解</span><span class="sxs-lookup"><span data-stu-id="e99cf-292">Scene understanding</span></span>](scene-understanding.md)
