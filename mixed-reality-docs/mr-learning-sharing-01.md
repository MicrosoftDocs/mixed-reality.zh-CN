---
title: 多用户功能教程 - 1. 简介
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376339"
---
# <a name="1-introduction"></a><span data-ttu-id="a8e91-105">1.简介</span><span class="sxs-lookup"><span data-stu-id="a8e91-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="a8e91-106">概述</span><span class="sxs-lookup"><span data-stu-id="a8e91-106">Overview</span></span>

<span data-ttu-id="a8e91-107">欢迎学习多用户功能教程！</span><span class="sxs-lookup"><span data-stu-id="a8e91-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="a8e91-108">通过本系列教程，你将学习有关使用 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN) 生成多用户体验的基础知识。</span><span class="sxs-lookup"><span data-stu-id="a8e91-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="a8e91-109">混合现实开发人员可使用多个网络选项来创建共享体验，PUN 就是其中的一个。</span><span class="sxs-lookup"><span data-stu-id="a8e91-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="a8e91-110">本系列教程：</span><span class="sxs-lookup"><span data-stu-id="a8e91-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="a8e91-111">设置 Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="a8e91-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="a8e91-112">连接多名用户</span><span class="sxs-lookup"><span data-stu-id="a8e91-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="a8e91-113">与多名用户共享对象移动情况</span><span class="sxs-lookup"><span data-stu-id="a8e91-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="a8e91-114">将 Azure 空间定位点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="a8e91-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="a8e91-115">目标</span><span class="sxs-lookup"><span data-stu-id="a8e91-115">Objectives</span></span>

* <span data-ttu-id="a8e91-116">了解如何创建 PUN 应用并将其连接到 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="a8e91-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="a8e91-117">了解如何在共享体验中连接多名用户</span><span class="sxs-lookup"><span data-stu-id="a8e91-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="a8e91-118">了解如何与其他用户共享对象移动情况</span><span class="sxs-lookup"><span data-stu-id="a8e91-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="a8e91-119">了解如何在多台设备之间实现空间对齐</span><span class="sxs-lookup"><span data-stu-id="a8e91-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8e91-120">必备条件</span><span class="sxs-lookup"><span data-stu-id="a8e91-120">Prerequisites</span></span>

* <span data-ttu-id="a8e91-121">一台 Windows 10 计算机，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="a8e91-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a8e91-122">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a8e91-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a8e91-123">一台[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="a8e91-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a8e91-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="a8e91-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="a8e91-125">已完成[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分（位于[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="a8e91-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="a8e91-126">已完成[入门教程](mr-learning-base-01.md)系列，或者之前有一些使用 Unity 和 MRTK 的基本经验</span><span class="sxs-lookup"><span data-stu-id="a8e91-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="a8e91-127">已完成 [Azure 空间定位点教程](mr-learning-asa-01.md)系列，或者之前创建 Azure 空间定位点帐户的经验</span><span class="sxs-lookup"><span data-stu-id="a8e91-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="a8e91-128">如果打算部署到 Android 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="a8e91-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="a8e91-129"><a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接</span><span class="sxs-lookup"><span data-stu-id="a8e91-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="a8e91-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 Android 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="a8e91-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="a8e91-131">如果打算部署到 iOS 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="a8e91-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="a8e91-132">一台已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机</span><span class="sxs-lookup"><span data-stu-id="a8e91-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="a8e91-133"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="a8e91-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="a8e91-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 iOS 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="a8e91-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="a8e91-135">建议对本系列教程使用混合现实工具包版本 MRTK 2.4.0。</span><span class="sxs-lookup"><span data-stu-id="a8e91-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="a8e91-136">建议对本系列教程使用 Unity 2019.3.15。</span><span class="sxs-lookup"><span data-stu-id="a8e91-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="a8e91-137">这将取代上述链接的先决条件中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="a8e91-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="a8e91-138">下一教程：2.设置 Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="a8e91-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
