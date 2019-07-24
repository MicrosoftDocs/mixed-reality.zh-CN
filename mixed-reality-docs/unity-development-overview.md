---
title: Unity 开发概述
description: 在 Unity 中构建混合现实应用入门。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 照相机, 模拟, 仿真, 文档
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414524"
---
# <a name="unity-development-overview"></a><span data-ttu-id="bf034-104">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="bf034-104">Unity development overview</span></span>

<span data-ttu-id="bf034-105">构建[混合现实应用](app-views.md)的最快途径是使用[Unity](http://aka.ms/HoloLensUnity)。</span><span class="sxs-lookup"><span data-stu-id="bf034-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="bf034-106">建议你花时间浏览[Unity 教程](https://unity3d.com/learn/tutorials)。</span><span class="sxs-lookup"><span data-stu-id="bf034-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="bf034-107">如果需要资产, Unity 有一个全面的[资产存储区](https://www.assetstore.unity3d.com/)。</span><span class="sxs-lookup"><span data-stu-id="bf034-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="bf034-108">构建基本的 Unity 理解后, 可以访问这些[教程](tutorials.md), 了解使用 unity 进行混合现实开发的细节。</span><span class="sxs-lookup"><span data-stu-id="bf034-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="bf034-109">请务必访问[Unity 混合现实论坛](http://forum.unity3d.com/forums/hololens.102/), 与在 Unity 中构建混合现实应用的其他社区合作, 查找可能遇到的问题的解决方案。</span><span class="sxs-lookup"><span data-stu-id="bf034-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>


<span data-ttu-id="bf034-110">若要开始通过 Unity 构建混合现实应用, 请先[安装这些工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="bf034-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="bf034-111">带有混合现实工具包的新 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="bf034-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="bf034-112">若要在 Unity 中进行开发, 最简单的方法是利用混合现实工具包的帮助。</span><span class="sxs-lookup"><span data-stu-id="bf034-112">The easiest way to develop in Unity is with the help of Mixed Reality Toolkit.</span></span> <span data-ttu-id="bf034-113">它将帮助你自动设置项目, 并提供一组混合现实功能以加速开发。</span><span class="sxs-lookup"><span data-stu-id="bf034-113">It will help you setup with project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="bf034-114">请查看[混合现实工具包 v2](mrtk-getting-started.md)以了解详细信息并开始。</span><span class="sxs-lookup"><span data-stu-id="bf034-114">Please check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="bf034-115">将现有 Unity 应用移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bf034-115">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="bf034-116">如果你有要移植到 Windows Mixed Reality 的现有 Unity 项目, 请按照[Unity 迁移指南](porting-guides.md)中的步骤开始操作。</span><span class="sxs-lookup"><span data-stu-id="bf034-116">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="bf034-117">为 Windows Mixed Reality 配置新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="bf034-117">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="bf034-118">如果要在不导入混合现实工具包的情况下创建新的 Unity 项目, 则需要为 Windows Mixed Reality 手动更改的一小组 Unity 设置。</span><span class="sxs-lookup"><span data-stu-id="bf034-118">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="bf034-119">这些分类分为两类: 每个项目和每场景。</span><span class="sxs-lookup"><span data-stu-id="bf034-119">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="bf034-120">有关为[Windows Mixed Reality 配置新 Unity 项目](Configure-Unity-Project.md)的分步指南, 请参阅此处。</span><span class="sxs-lookup"><span data-stu-id="bf034-120">See here for step by step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="bf034-121">添加混合现实功能和输入</span><span class="sxs-lookup"><span data-stu-id="bf034-121">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="bf034-122">在您的项目中设置 MRTK V2 并按上述方式配置项目后, 标准 Unity 游戏对象 (如相机) 会立即为**固定规模的体验**亮起, 照相机的位置会自动更新为用户将其头部移到世界各地。</span><span class="sxs-lookup"><span data-stu-id="bf034-122">Once you've setup MRTK V2 with your project, or configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="bf034-123">添加对 Windows Mixed Reality 功能的支持, 例如[空间阶段](coordinate-systems.md#spatial-coordinate-systems)、[手势、动作控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md), 使用直接内置于 Unity 的 api 实现。</span><span class="sxs-lookup"><span data-stu-id="bf034-123">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="bf034-124">首先, 请查看 applicatioin 可面向的[体验规模](coordinate-systems.md):</span><span class="sxs-lookup"><span data-stu-id="bf034-124">First, review the [experience scales](coordinate-systems.md) that your applicatioin can target:</span></span>
* <span data-ttu-id="bf034-125">如果希望构建**仅限方向**或**固定规模的体验**, 则需要将 Unity 的跟踪空间类型设置为 "[静态](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)"。</span><span class="sxs-lookup"><span data-stu-id="bf034-125">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="bf034-126">如果希望构建**大规模**或**房间规模的体验**, 则需要确保 Unity 的跟踪空间类型已成功设置为[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="bf034-126">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="bf034-127">如果你希望在 HoloLens 上构建可让用户漫游超过5米的**全球规模**体验, 则需要使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)组件。</span><span class="sxs-lookup"><span data-stu-id="bf034-127">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="bf034-128">混合现实应用程序的所有核心构建基块的公开方式与其他 Unity Api 一致。</span><span class="sxs-lookup"><span data-stu-id="bf034-128">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="bf034-129">它们还可通过混合现实工具包获得。</span><span class="sxs-lookup"><span data-stu-id="bf034-129">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="bf034-130">摄像头</span><span class="sxs-lookup"><span data-stu-id="bf034-130">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="bf034-131">坐标系统</span><span class="sxs-lookup"><span data-stu-id="bf034-131">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="bf034-132">凝视</span><span class="sxs-lookup"><span data-stu-id="bf034-132">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="bf034-133">手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="bf034-133">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="bf034-134">语音输入</span><span class="sxs-lookup"><span data-stu-id="bf034-134">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="bf034-135">保持</span><span class="sxs-lookup"><span data-stu-id="bf034-135">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="bf034-136">空间音效</span><span class="sxs-lookup"><span data-stu-id="bf034-136">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="bf034-137">空间映射</span><span class="sxs-lookup"><span data-stu-id="bf034-137">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="bf034-138">许多混合现实应用程序还需要使用其他重要功能, 这些功能也会公开给 Unity 应用:</span><span class="sxs-lookup"><span data-stu-id="bf034-138">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="bf034-139">共享体验</span><span class="sxs-lookup"><span data-stu-id="bf034-139">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="bf034-140">可定位相机</span><span class="sxs-lookup"><span data-stu-id="bf034-140">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="bf034-141">焦点</span><span class="sxs-lookup"><span data-stu-id="bf034-141">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="bf034-142">跟踪丢失</span><span class="sxs-lookup"><span data-stu-id="bf034-142">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="bf034-143">键盘</span><span class="sxs-lookup"><span data-stu-id="bf034-143">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="bf034-144">在实际或模拟设备上运行 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="bf034-144">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="bf034-145">完成全息 Unity 项目以进行测试后, 下一步就是[导出并构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="bf034-145">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="bf034-146">使用该 VS 解决方案, 可以通过以下三种方式之一运行应用程序: 使用实设备或模拟设备:</span><span class="sxs-lookup"><span data-stu-id="bf034-146">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="bf034-147">部署到真实的 HoloLens 或 Windows Mixed Reality 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="bf034-147">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="bf034-148">部署到 HoloLens 模拟器</span><span class="sxs-lookup"><span data-stu-id="bf034-148">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="bf034-149">部署到 Windows Mixed Reality 沉浸式耳机模拟器</span><span class="sxs-lookup"><span data-stu-id="bf034-149">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="bf034-150">Unity 文档</span><span class="sxs-lookup"><span data-stu-id="bf034-150">Unity documentation</span></span>

<span data-ttu-id="bf034-151">除了 Windows 开发人员中心提供的此文档外, Unity 还随 Unity 编辑器一起安装 Windows Mixed Reality 功能的文档。</span><span class="sxs-lookup"><span data-stu-id="bf034-151">In addition to this documentation available on the Windows Dev Center, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="bf034-152">Unity 提供的文档包括两个单独的部分:</span><span class="sxs-lookup"><span data-stu-id="bf034-152">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="bf034-153">**Unity 脚本参考**</span><span class="sxs-lookup"><span data-stu-id="bf034-153">**Unity scripting reference**</span></span>
    * <span data-ttu-id="bf034-154">文档的本节包含 Unity 提供的脚本编写 API 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bf034-154">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="bf034-155">可以通过 "**帮助" > 脚本参考来**访问 Unity 编辑器</span><span class="sxs-lookup"><span data-stu-id="bf034-155">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="bf034-156">**Unity 手册**</span><span class="sxs-lookup"><span data-stu-id="bf034-156">**Unity manual**</span></span>
    * <span data-ttu-id="bf034-157">本手册旨在帮助你了解如何使用 Unity, 从基本到高级的技术。</span><span class="sxs-lookup"><span data-stu-id="bf034-157">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="bf034-158">可从 Unity 编辑器通过**Help > 手动**访问</span><span class="sxs-lookup"><span data-stu-id="bf034-158">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="bf034-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf034-159">See also</span></span>
* [<span data-ttu-id="bf034-160">混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="bf034-160">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="bf034-161">MR 基础知识 100：Unity 入门</span><span class="sxs-lookup"><span data-stu-id="bf034-161">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="bf034-162">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="bf034-162">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="bf034-163">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="bf034-163">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="bf034-164">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="bf034-164">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="bf034-165">将 Windows 命名空间与 Unity 应用配合用于 HoloLens</span><span class="sxs-lookup"><span data-stu-id="bf034-165">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="bf034-166">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="bf034-166">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="bf034-167">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="bf034-167">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="bf034-168">移植指南</span><span class="sxs-lookup"><span data-stu-id="bf034-168">Porting guides</span></span>](porting-guides.md)
