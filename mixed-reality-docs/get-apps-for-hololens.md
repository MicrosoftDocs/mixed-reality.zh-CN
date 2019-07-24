---
title: 获取 HoloLens 应用
description: 介绍如何通过 Microsoft Store 和边载安装 HoloLens 的应用。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 旁加载, 端负载, 边负载, 存储, uwp, 应用, 安装
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522568"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="8aab4-104">获取 HoloLens 应用</span><span class="sxs-lookup"><span data-stu-id="8aab4-104">Get apps for HoloLens</span></span>

<span data-ttu-id="8aab4-105">作为 Windows 10 设备, HoloLens 支持应用商店中的许多现有 UWP 应用程序以及专为 HoloLens 构建的新应用程序。</span><span class="sxs-lookup"><span data-stu-id="8aab4-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="8aab4-106">基于这些应用程序, 您甚至可以[开发](development-overview.md)和安装自己的应用程序或您的朋友的应用程序!</span><span class="sxs-lookup"><span data-stu-id="8aab4-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="8aab4-107">正在安装应用</span><span class="sxs-lookup"><span data-stu-id="8aab4-107">Installing Apps</span></span>

<span data-ttu-id="8aab4-108">可以通过三种方式在 HoloLens 上安装新的应用。</span><span class="sxs-lookup"><span data-stu-id="8aab4-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="8aab4-109">主要方法是从 Windows 应用商店安装新的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8aab4-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="8aab4-110">不过, 也可以使用设备门户或从 Visual Studio 部署应用程序来安装自己的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8aab4-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="8aab4-111">从 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="8aab4-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="8aab4-112">执行[布隆](gestures.md#bloom)笔势以打开 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="8aab4-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="8aab4-113">选择应用商店应用, 然后点击将此磁贴置于世界中。</span><span class="sxs-lookup"><span data-stu-id="8aab4-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="8aab4-114">应用商店应用打开后, 使用搜索栏查找任何所需的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8aab4-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="8aab4-115">在应用程序页上选择 "**获取**" 或 "**安装**" (可能需要购买)。</span><span class="sxs-lookup"><span data-stu-id="8aab4-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="8aab4-116">使用设备门户安装应用程序包</span><span class="sxs-lookup"><span data-stu-id="8aab4-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="8aab4-117">建立从[设备门户](using-the-windows-device-portal.md)到目标 HoloLens 的连接。</span><span class="sxs-lookup"><span data-stu-id="8aab4-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="8aab4-118">导航到左侧导航栏中的 "**应用**" 页。</span><span class="sxs-lookup"><span data-stu-id="8aab4-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="8aab4-119">在 "**应用包**" 下, 浏览到与应用程序关联的 .appx 文件。</span><span class="sxs-lookup"><span data-stu-id="8aab4-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="8aab4-120">请确保引用任何关联的依赖项和证书文件。</span><span class="sxs-lookup"><span data-stu-id="8aab4-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="8aab4-121">单击 "**开始**"。</span><span class="sxs-lookup"><span data-stu-id="8aab4-121">Click **Go**.</span></span>

<span data-ttu-id="8aab4-122">![在 Microsoft HoloLens 上的 Windows 设备门户中安装应用表单](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="8aab4-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="8aab4-123">使用 Windows 设备门户在 HoloLens 上安装应用</span><span class="sxs-lookup"><span data-stu-id="8aab4-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="8aab4-124">从 Microsoft Visual Studio 2015 进行部署</span><span class="sxs-lookup"><span data-stu-id="8aab4-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="8aab4-125">打开应用的 Visual Studio 解决方案 (.sln 文件)。</span><span class="sxs-lookup"><span data-stu-id="8aab4-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="8aab4-126">打开项目的 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="8aab4-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="8aab4-127">选择以下生成配置:Master/x86/远程计算机。</span><span class="sxs-lookup"><span data-stu-id="8aab4-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="8aab4-128">选择 "远程计算机" 时:</span><span class="sxs-lookup"><span data-stu-id="8aab4-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="8aab4-129">请确保该地址指向 HoloLens 的 WiFi IP 地址。</span><span class="sxs-lookup"><span data-stu-id="8aab4-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="8aab4-130">将身份验证设置为通用 (未加密的协议)。</span><span class="sxs-lookup"><span data-stu-id="8aab4-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="8aab4-131">构建解决方案。</span><span class="sxs-lookup"><span data-stu-id="8aab4-131">Build your solution.</span></span>
6. <span data-ttu-id="8aab4-132">单击 "**远程计算机**" 按钮, 将开发 PC 中的应用部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="8aab4-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="8aab4-133">如果已有一个 HoloLens 现有版本, 请选择 "是" 以重新安装此更新版本。</span><span class="sxs-lookup"><span data-stu-id="8aab4-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="8aab4-134">![Visual Studio 中适用于应用的远程计算机部署到 Microsoft HoloLens](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="8aab4-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="8aab4-135">应用程序将在你的 HoloLens 上安装和自动启动。</span><span class="sxs-lookup"><span data-stu-id="8aab4-135">The application will install and auto launch on your HoloLens.</span></span>
