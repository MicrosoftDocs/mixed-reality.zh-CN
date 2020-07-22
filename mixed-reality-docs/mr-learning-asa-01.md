---
title: Azure 空间定位点教程 - 1. 简介
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6a015b4c9f6a5c1a92697ef9909443234a98ab09
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304185"
---
# <a name="1-introduction"></a><span data-ttu-id="03f1c-105">1.简介</span><span class="sxs-lookup"><span data-stu-id="03f1c-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="03f1c-106">概述</span><span class="sxs-lookup"><span data-stu-id="03f1c-106">Overview</span></span>

<span data-ttu-id="03f1c-107">欢迎学习 Azure 空间定位点教程！</span><span class="sxs-lookup"><span data-stu-id="03f1c-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="03f1c-108">通过本系列教程，你将了解 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure 空间定位点</a>的基础知识，学习如何在真实世界中创建定位空间的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="03f1c-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="03f1c-109">你还将了解如何将项目部署到 Android 和 iOS。</span><span class="sxs-lookup"><span data-stu-id="03f1c-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="03f1c-110">本系列教程：</span><span class="sxs-lookup"><span data-stu-id="03f1c-110">Tutorials in this series:</span></span>

1. [<span data-ttu-id="03f1c-111">简介</span><span class="sxs-lookup"><span data-stu-id="03f1c-111">Introduction</span></span>](mr-learning-asa-01.md)
2. [<span data-ttu-id="03f1c-112">Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="03f1c-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="03f1c-113">保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="03f1c-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="03f1c-114">显示 Azure 空间定位点反馈</span><span class="sxs-lookup"><span data-stu-id="03f1c-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="03f1c-115">适用于 Android 和 iOS 的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="03f1c-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="03f1c-116">目标</span><span class="sxs-lookup"><span data-stu-id="03f1c-116">Objectives</span></span>

* <span data-ttu-id="03f1c-117">了解如何创建空间定位点并从 Azure 中获取它们</span><span class="sxs-lookup"><span data-stu-id="03f1c-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="03f1c-118">了解如何在应用会话之间实现空间对齐</span><span class="sxs-lookup"><span data-stu-id="03f1c-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="03f1c-119">了解如何在多台设备之间实现空间对齐</span><span class="sxs-lookup"><span data-stu-id="03f1c-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="03f1c-120">了解如何准备、生成项目并将其部署到 Android 和 iOS 上</span><span class="sxs-lookup"><span data-stu-id="03f1c-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03f1c-121">先决条件</span><span class="sxs-lookup"><span data-stu-id="03f1c-121">Prerequisites</span></span>

* <span data-ttu-id="03f1c-122">一台 Windows 10 计算机，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="03f1c-122">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="03f1c-123">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="03f1c-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="03f1c-124">一台[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="03f1c-124">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="03f1c-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="03f1c-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="03f1c-126">已完成[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分（位于[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中）</span><span class="sxs-lookup"><span data-stu-id="03f1c-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="03f1c-127">已完成[入门教程](mr-learning-base-01.md)系列，或者之前有一些使用 Unity 和 MRTK 的基本经验</span><span class="sxs-lookup"><span data-stu-id="03f1c-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="03f1c-128">已完成 [Azure 空间定位点教程](mr-learning-asa-01.md)系列，或者之前有创建 Azure 空间定位点帐户的经验</span><span class="sxs-lookup"><span data-stu-id="03f1c-128">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or previous experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="03f1c-129">如果打算部署到 Android 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="03f1c-129">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="03f1c-130"><a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接</span><span class="sxs-lookup"><span data-stu-id="03f1c-130">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="03f1c-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 Android 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="03f1c-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="03f1c-132">如果打算部署到 iOS 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="03f1c-132">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="03f1c-133">一台已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机</span><span class="sxs-lookup"><span data-stu-id="03f1c-133">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="03f1c-134"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="03f1c-134">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="03f1c-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 iOS 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="03f1c-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="03f1c-136">建议对本系列教程使用混合现实工具包版本 MRTK 2.4.0。</span><span class="sxs-lookup"><span data-stu-id="03f1c-136">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="03f1c-137">建议对本系列教程使用 Unity 2019.3.15。</span><span class="sxs-lookup"><span data-stu-id="03f1c-137">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="03f1c-138">这将取代上述链接的先决条件中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="03f1c-138">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="03f1c-139">下一教程：2.开始使用 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="03f1c-139">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
