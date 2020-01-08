---
title: 多用户功能教程-1。 设置 Photon Unity 网络
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334329"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="266a1-105">1. 设置 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="266a1-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="266a1-106">概述</span><span class="sxs-lookup"><span data-stu-id="266a1-106">Overview</span></span>

<span data-ttu-id="266a1-107">在本教程中，你将了解如何通过将 Photon Unity 网络（双关语）导入到 Unity 项目来准备创建共享体验。</span><span class="sxs-lookup"><span data-stu-id="266a1-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="266a1-108">Photon 是可供混合现实开发人员用来创建共享体验的多个网络选项之一。</span><span class="sxs-lookup"><span data-stu-id="266a1-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="266a1-109">你将了解如何创建 Photon 帐户、导入 Photon 以及创建可选的本地服务器</span><span class="sxs-lookup"><span data-stu-id="266a1-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="266a1-110">目标</span><span class="sxs-lookup"><span data-stu-id="266a1-110">Objectives</span></span>

* <span data-ttu-id="266a1-111">了解如何创建 Photon 帐户</span><span class="sxs-lookup"><span data-stu-id="266a1-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="266a1-112">了解如何查找和导入 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="266a1-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="266a1-113">设置本地 Photon 服务器</span><span class="sxs-lookup"><span data-stu-id="266a1-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="266a1-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="266a1-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="266a1-115">如果尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="266a1-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="266a1-116">使用安装了正确的[工具](install-the-tools.md)配置的 WINDOWS 10 电脑</span><span class="sxs-lookup"><span data-stu-id="266a1-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="266a1-117">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="266a1-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="266a1-118">一些基本C#编程功能</span><span class="sxs-lookup"><span data-stu-id="266a1-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="266a1-119">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="266a1-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="266a1-120">本系列教程需要<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> ，建议的版本是 unity 2019.1.14。</span><span class="sxs-lookup"><span data-stu-id="266a1-120">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="266a1-121">这将取代上述先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="266a1-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="266a1-122">设置 Photon</span><span class="sxs-lookup"><span data-stu-id="266a1-122">Setting up Photon</span></span>

1. <span data-ttu-id="266a1-123">设置[Photon](https://dashboard.photonengine.com//Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="266a1-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="266a1-124">通过单击[此链接](https://dashboard.photonengine.com//Account/SignUp)导航到 "Photon 注册" 页。</span><span class="sxs-lookup"><span data-stu-id="266a1-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="266a1-125">按照注册页上的说明来创建帐户。</span><span class="sxs-lookup"><span data-stu-id="266a1-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="266a1-128">单击 "创建新应用程序" 按钮，创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="266a1-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="266a1-130">在 Photon Type 下的下拉菜单中选择 Photon 双关语。</span><span class="sxs-lookup"><span data-stu-id="266a1-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="266a1-131">然后为其指定名称。</span><span class="sxs-lookup"><span data-stu-id="266a1-131">Then give it a name.</span></span> <span data-ttu-id="266a1-132">在此示例中，我们将其命名为 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="266a1-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="266a1-133">完成后，单击 "创建" 按钮。</span><span class="sxs-lookup"><span data-stu-id="266a1-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="266a1-135">返回到应用程序页面，你应看到类似于下图的内容。</span><span class="sxs-lookup"><span data-stu-id="266a1-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="266a1-136">单击应用程序 ID 并复制它。</span><span class="sxs-lookup"><span data-stu-id="266a1-136">Click the application ID and copy it.</span></span> <span data-ttu-id="266a1-137">将其粘贴到可以轻松访问的位置。</span><span class="sxs-lookup"><span data-stu-id="266a1-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="266a1-139">创建新的 unity 项目，并将其命名为 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="266a1-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="266a1-140">有关如何创建新 Unity 项目的说明，请参阅[基本模块的 "创建 Unity 项目" 部分](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="266a1-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="266a1-141">加载项目后，单击 "资产存储" 选项卡，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="266a1-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="266a1-142">然后，在下图中突出显示的 "搜索" 框中，键入 "双关语"，然后从搜索结果中选择 "Photon 双关语 2-免费" 资产。</span><span class="sxs-lookup"><span data-stu-id="266a1-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="266a1-144">通过按 "下载" 和 "导入" 按钮来下载和导入此资产。</span><span class="sxs-lookup"><span data-stu-id="266a1-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="266a1-146">完成导入过程后，将显示双关语向导 Photon。</span><span class="sxs-lookup"><span data-stu-id="266a1-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="266a1-147">获取步骤4中的应用程序 ID （应在剪贴板中），将其粘贴到 "AppID" 框中，然后按 "设置项目" 按钮。</span><span class="sxs-lookup"><span data-stu-id="266a1-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="266a1-149">成功添加 AppID 后，导航到资产中的 Photon-> PhotonUnityNetworking > 资源-> PhotonServerSettings。</span><span class="sxs-lookup"><span data-stu-id="266a1-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="266a1-150">选择 "使用名称服务器" 选项，并将 "固定区域" 设置为 "US" 或 "photon" 服务区域。</span><span class="sxs-lookup"><span data-stu-id="266a1-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="266a1-152">祝贺</span><span class="sxs-lookup"><span data-stu-id="266a1-152">Congratulations</span></span>

<span data-ttu-id="266a1-153">已成功创建 Photon 帐户，设置本地 Photon 服务器，并将双关语导入到 Unity。</span><span class="sxs-lookup"><span data-stu-id="266a1-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="266a1-154">下一步是设置项目，并允许与其他用户进行连接，以便多个用户可以看到你的工作。</span><span class="sxs-lookup"><span data-stu-id="266a1-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="266a1-155">[下一教程： 2. 将 Unity 准备好进行开发](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="266a1-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
