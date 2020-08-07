---
title: Unity 开发概述
description: 在 Unity 中构建混合现实应用入门。
author: thetuvix
ms.author: kurtie
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档
ms.openlocfilehash: 4679e1a2b58a7e0d77e6b295803624a4de1fac19
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476709"
---
# <a name="unity-development-overview"></a><span data-ttu-id="ff4d5-104">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="ff4d5-104">Unity development overview</span></span>

<span data-ttu-id="ff4d5-105">构建[混合现实应用](app-views.md)的最快途径是使用 [Unity](https://unity.com)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](https://unity.com).</span></span> <span data-ttu-id="ff4d5-106">建议你花一些时间浏览 [Unity 教程](https://unity3d.com/learn/tutorials)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-106">We recommend that you take time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="ff4d5-107">如果你需要资产，Unity 有一个包罗万象的[资产商店](https://www.assetstore.unity3d.com/)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="ff4d5-108">有了对 Unity 的基本了解以后，即可访问[教程](tutorials.md)，了解使用 Unity 进行混合现实开发的具体细节。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-108">Once you have built up a basic understanding of Unity, you can visit the [tutorials](tutorials.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="ff4d5-109">若要与社区的其他人员交流在 Unity 中构建混合现实应用的心得，以及查找可能遇到的问题的解决方案，请务必访问 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-109">Be sure to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

<span data-ttu-id="ff4d5-110">若要开始使用 Unity 构建混合现实应用，请先[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-110">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span>

## <a name="new-unity-project-with-mixed-reality-toolkit"></a><span data-ttu-id="ff4d5-111">使用混合现实工具包新建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="ff4d5-111">New Unity Project with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="ff4d5-112">要在 Unity 中进行开发，最简单的方式是使用混合现实工具包，它将帮助你在项目中自动进行设置，并提供一组混合现实功能来助你加快开发速度。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-112">The easiest way to develop in Unity is with the Mixed Reality Toolkit, which will help you set up with the project automatically, and provide a set of mixed reality features to accelerate your development.</span></span> <span data-ttu-id="ff4d5-113">若要了解详细信息并开始操作，请查看[混合现实工具包 v2](mrtk-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-113">Check out [Mixed Reality Toolkit v2](mrtk-getting-started.md) to learn more and get started.</span></span> 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="ff4d5-114">将现有的 Unity 应用移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ff4d5-114">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="ff4d5-115">若要将现有的 Unity 项目移植到 Windows Mixed Reality，请按照 [Unity 移植指南](porting-guides.md)开始操作。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-115">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="ff4d5-116">配置用于 Windows Mixed Reality 的全新 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="ff4d5-116">Configuring new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="ff4d5-117">若要在不导入混合现实工具包的情况下创建新的 Unity 项目，需针对 Windows Mixed Reality 更改少量的 Unity 设置。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-117">If you're creating a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you need to change for Windows Mixed Reality.</span></span> <span data-ttu-id="ff4d5-118">这些设置分为两个类别：按项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-118">These settings are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="ff4d5-119">请查看此文档，获取[为 Windows Mixed Reality 配置全新 Unity 项目](Configure-Unity-Project.md)的分步指南</span><span class="sxs-lookup"><span data-stu-id="ff4d5-119">See here for a step-by-step guide to [Configure new Unity Project for Windows Mixed Reality](Configure-Unity-Project.md)</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="ff4d5-120">添加混合现实功能和输入</span><span class="sxs-lookup"><span data-stu-id="ff4d5-120">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="ff4d5-121">在项目中设置 MRTK V2 或按上述说明配置项目后，标准的 Unity 游戏对象（例如相机）会立即启动，为你带来坐定式体验。当用户在空间中移动头部时，相机的位置会自动更新。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-121">Once you've setup MRTK V2 with your project or configured your project as described above, standard Unity game objects like the camera will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="ff4d5-122">可借助直接内置到 Unity 中的 API，添加对 Windows Mixed Reality 功能（例如[空间舞台](coordinate-systems.md#spatial-coordinate-systems)、[手势、动作控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md)）的支持。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-122">Adding support for Windows Mixed Reality features, such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md), or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span> 

<span data-ttu-id="ff4d5-123">首先，请查看应用程序可能面对的[体验规模](coordinate-systems.md)：</span><span class="sxs-lookup"><span data-stu-id="ff4d5-123">First, review the [experience scales](coordinate-systems.md) that your application can target:</span></span>
* <span data-ttu-id="ff4d5-124">若要构建**仅限方向的体验**或**坐定式体验**，需将 Unity 的跟踪空间类型设置为 [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-124">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="ff4d5-125">若要构建**站姿体验**或**房间规模的体验**，需确保将 Unity 的跟踪空间类型成功设置为 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-125">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="ff4d5-126">若要在 HoloLens 上构建**世界规模**的体验，让用户在 5 米之外漫游，需使用 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 组件。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-126">If you're looking to build a **world-scale** experience on HoloLens that lets users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="ff4d5-127">混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-127">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="ff4d5-128">它们也可通过混合现实工具包获得。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-128">They are also available through the Mixed Reality Toolkit.</span></span>
* [<span data-ttu-id="ff4d5-129">摄像头</span><span class="sxs-lookup"><span data-stu-id="ff4d5-129">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="ff4d5-130">坐标系统</span><span class="sxs-lookup"><span data-stu-id="ff4d5-130">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="ff4d5-131">凝视</span><span class="sxs-lookup"><span data-stu-id="ff4d5-131">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="ff4d5-132">手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="ff4d5-132">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="ff4d5-133">语音输入</span><span class="sxs-lookup"><span data-stu-id="ff4d5-133">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="ff4d5-134">持久性</span><span class="sxs-lookup"><span data-stu-id="ff4d5-134">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="ff4d5-135">空间音效</span><span class="sxs-lookup"><span data-stu-id="ff4d5-135">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="ff4d5-136">空间映射</span><span class="sxs-lookup"><span data-stu-id="ff4d5-136">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="ff4d5-137">还有其他供许多混合现实应用程序使用的重要功能，这些功能也公开给 Unity 应用：</span><span class="sxs-lookup"><span data-stu-id="ff4d5-137">There are other key features that many mixed reality applications will want to use that are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="ff4d5-138">共享体验</span><span class="sxs-lookup"><span data-stu-id="ff4d5-138">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="ff4d5-139">可定位相机</span><span class="sxs-lookup"><span data-stu-id="ff4d5-139">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="ff4d5-140">焦点</span><span class="sxs-lookup"><span data-stu-id="ff4d5-140">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="ff4d5-141">失跟</span><span class="sxs-lookup"><span data-stu-id="ff4d5-141">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="ff4d5-142">键盘</span><span class="sxs-lookup"><span data-stu-id="ff4d5-142">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="ff4d5-143">在实际设备或模拟设备上运行 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="ff4d5-143">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="ff4d5-144">准备好对全息 Unity 项目进行测试以后，下一步是[导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-144">Once you've got your holographic Unity project ready for testing, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="ff4d5-145">有了该 VS 解决方案以后，即可使用真实的或模拟的设备通过下述三种方式之一运行应用程序：</span><span class="sxs-lookup"><span data-stu-id="ff4d5-145">With that VS solution in hand, you can then run your application in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="ff4d5-146">部署到真实的 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="ff4d5-146">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="ff4d5-147">部署到 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="ff4d5-147">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="ff4d5-148">部署到 Windows Mixed Reality 沉浸式头戴显示设备模拟器</span><span class="sxs-lookup"><span data-stu-id="ff4d5-148">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="ff4d5-149">Unity 文档</span><span class="sxs-lookup"><span data-stu-id="ff4d5-149">Unity documentation</span></span>

<span data-ttu-id="ff4d5-150">除了 docs.microsoft.com 上提供的此文档，Unity 还配置了适用于 Windows Mixed Reality 功能和 Unity 编辑器的文档。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-150">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="ff4d5-151">Unity 提供的文档包括两个单独的部分：</span><span class="sxs-lookup"><span data-stu-id="ff4d5-151">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="ff4d5-152">**Unity 脚本参考**</span><span class="sxs-lookup"><span data-stu-id="ff4d5-152">**Unity scripting reference**</span></span>
    * <span data-ttu-id="ff4d5-153">此部分文档包含 Unity 提供的脚本 API 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-153">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="ff4d5-154">可以在 Unity 编辑器中通过“帮助”>“脚本参考”进行访问</span><span class="sxs-lookup"><span data-stu-id="ff4d5-154">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="ff4d5-155">**Unity 手册**</span><span class="sxs-lookup"><span data-stu-id="ff4d5-155">**Unity manual**</span></span>
    * <span data-ttu-id="ff4d5-156">此手册旨在介绍如何使用 Unity，既有基本技术，又有高级技术。</span><span class="sxs-lookup"><span data-stu-id="ff4d5-156">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="ff4d5-157">可以在 Unity 编辑器中通过“帮助”>“手册”进行访问</span><span class="sxs-lookup"><span data-stu-id="ff4d5-157">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="ff4d5-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff4d5-158">See also</span></span>
* [<span data-ttu-id="ff4d5-159">混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="ff4d5-159">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="ff4d5-160">MR 基础知识 100：Unity 入门</span><span class="sxs-lookup"><span data-stu-id="ff4d5-160">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="ff4d5-161">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="ff4d5-161">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ff4d5-162">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="ff4d5-162">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="ff4d5-163">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="ff4d5-163">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="ff4d5-164">将 Windows 命名空间与 Unity 应用配合用于 HoloLens</span><span class="sxs-lookup"><span data-stu-id="ff4d5-164">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="ff4d5-165">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="ff4d5-165">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="ff4d5-166">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="ff4d5-166">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="ff4d5-167">移植指南</span><span class="sxs-lookup"><span data-stu-id="ff4d5-167">Porting guides</span></span>](porting-guides.md)
