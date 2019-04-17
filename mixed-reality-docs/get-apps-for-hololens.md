---
title: 为 HoloLens 获取应用
description: 介绍 HoloLens，同时通过 Microsoft Store 和旁加载安装应用。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 旁加载、 旁加载、 加载、 存储、 uwp、 应用程序中，安装
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590105"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="d7482-104">为 HoloLens 获取应用</span><span class="sxs-lookup"><span data-stu-id="d7482-104">Get apps for HoloLens</span></span>

<span data-ttu-id="d7482-105">为 Windows 10 设备，HoloLens 支持许多的现有 UWP 应用程序从应用商店，以及新应用程序是专为 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d7482-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="d7482-106">基于这些数据，甚至可能需要向[开发](development-overview.md)并安装你自己的应用或与您的朋友 ！</span><span class="sxs-lookup"><span data-stu-id="d7482-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="d7482-107">安装应用</span><span class="sxs-lookup"><span data-stu-id="d7482-107">Installing Apps</span></span>

<span data-ttu-id="d7482-108">有三种方法在 HoloLens 上安装新的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d7482-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="d7482-109">主要方法是从 Windows 应用商店中安装新的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d7482-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="d7482-110">但是，还可以安装自己的应用程序使用设备门户或通过从 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="d7482-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="d7482-111">从 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="d7482-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="d7482-112">执行[布隆](gestures.md#bloom)手势以打开[开始菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="d7482-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="d7482-113">选择应用商店应用，然后点击要将此磁贴放入您的世界。</span><span class="sxs-lookup"><span data-stu-id="d7482-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="d7482-114">应用商店应用程序打开后，使用搜索栏查找任何所需的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d7482-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="d7482-115">选择**获取**或**安装**上的应用程序页 （购买可能会需要）。</span><span class="sxs-lookup"><span data-stu-id="d7482-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="d7482-116">使用设备门户安装应用程序包</span><span class="sxs-lookup"><span data-stu-id="d7482-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="d7482-117">从建立连接[设备门户](using-the-windows-device-portal.md)面向 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d7482-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="d7482-118">导航到**应用**页左侧导航窗格中的。</span><span class="sxs-lookup"><span data-stu-id="d7482-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="d7482-119">下**应用程序包**浏览到与你的应用程序相关联的.appx 文件。</span><span class="sxs-lookup"><span data-stu-id="d7482-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="d7482-120">请确保引用任何关联的依赖项和证书文件。</span><span class="sxs-lookup"><span data-stu-id="d7482-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="d7482-121">单击**转**。</span><span class="sxs-lookup"><span data-stu-id="d7482-121">Click **Go**.</span></span>

<span data-ttu-id="d7482-122">![在 Microsoft HoloLens 上 Windows Device Portal 中安装的应用窗体](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="d7482-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="d7482-123">使用 Windows Device Portal HoloLens 上安装应用</span><span class="sxs-lookup"><span data-stu-id="d7482-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="d7482-124">从 Microsoft Visual Studio 2015 进行部署</span><span class="sxs-lookup"><span data-stu-id="d7482-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="d7482-125">打开应用的 Visual Studio 解决方案 （.sln 文件）。</span><span class="sxs-lookup"><span data-stu-id="d7482-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="d7482-126">打开项目的**属性**。</span><span class="sxs-lookup"><span data-stu-id="d7482-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="d7482-127">选择以下的生成配置：母版/x86/远程计算机。</span><span class="sxs-lookup"><span data-stu-id="d7482-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="d7482-128">选择远程计算机时：</span><span class="sxs-lookup"><span data-stu-id="d7482-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="d7482-129">请确保地址点到 HoloLens 的 WiFi IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d7482-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="d7482-130">为通用 （未加密的协议） 设置身份验证。</span><span class="sxs-lookup"><span data-stu-id="d7482-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="d7482-131">生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="d7482-131">Build your solution.</span></span>
6. <span data-ttu-id="d7482-132">单击**远程计算机**按钮以部署到你 HoloLens 从进行开发的电脑应用。</span><span class="sxs-lookup"><span data-stu-id="d7482-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="d7482-133">如果你已有现有生成 HoloLens 上，选择是以重新安装此较新版本。</span><span class="sxs-lookup"><span data-stu-id="d7482-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="d7482-134">![应用到在 Visual Studio 中的 Microsoft HoloLens 的远程计算机部署](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="d7482-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="d7482-135">应用程序将安装和自动在 HoloLens 上的启动。</span><span class="sxs-lookup"><span data-stu-id="d7482-135">The application will install and auto launch on your HoloLens.</span></span>
