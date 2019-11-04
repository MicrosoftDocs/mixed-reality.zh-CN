---
title: 多用户功能教程-1。 设置 Photon Unity 网络
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: c6a2bea3d50669000e81cad7c83ae6a69b8a847f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437746"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="40c9c-105">1. 设置 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="40c9c-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="40c9c-106">在本教程中，你将了解如何通过将 Photon Unity 网络（双关语）导入到 Unity 项目来准备创建共享体验。</span><span class="sxs-lookup"><span data-stu-id="40c9c-106">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="40c9c-107">Photon 是可供混合现实开发人员用来创建共享体验的多个网络选项之一。</span><span class="sxs-lookup"><span data-stu-id="40c9c-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="40c9c-108">你将了解如何创建 Photon 帐户、导入 Photon 以及创建可选的本地服务器</span><span class="sxs-lookup"><span data-stu-id="40c9c-108">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="40c9c-109">目标</span><span class="sxs-lookup"><span data-stu-id="40c9c-109">Objectives</span></span>

* <span data-ttu-id="40c9c-110">了解如何创建 Photon 帐户</span><span class="sxs-lookup"><span data-stu-id="40c9c-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="40c9c-111">了解如何查找和导入 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="40c9c-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="40c9c-112">设置本地 Photon 服务器</span><span class="sxs-lookup"><span data-stu-id="40c9c-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="40c9c-113">设置 Photon</span><span class="sxs-lookup"><span data-stu-id="40c9c-113">Setting up Photon</span></span>

1. <span data-ttu-id="40c9c-114">设置[Photon](https://dashboard.photonengine.com//Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="40c9c-114">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="40c9c-115">通过单击[此链接](https://dashboard.photonengine.com//Account/SignUp)导航到 "Photon 注册" 页。</span><span class="sxs-lookup"><span data-stu-id="40c9c-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="40c9c-116">按照注册页上的说明来创建帐户。</span><span class="sxs-lookup"><span data-stu-id="40c9c-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="40c9c-119">单击 "创建新应用程序" 按钮，创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="40c9c-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="40c9c-121">在 Photon Type 下的下拉菜单中选择 Photon 双关语。</span><span class="sxs-lookup"><span data-stu-id="40c9c-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="40c9c-122">然后为其指定名称。</span><span class="sxs-lookup"><span data-stu-id="40c9c-122">Then give it a name.</span></span> <span data-ttu-id="40c9c-123">在此示例中，我们将其命名为 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="40c9c-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="40c9c-124">完成后，单击 "创建" 按钮。</span><span class="sxs-lookup"><span data-stu-id="40c9c-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="40c9c-126">返回到应用程序页面，你应看到类似于下图的内容。</span><span class="sxs-lookup"><span data-stu-id="40c9c-126">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="40c9c-127">单击应用程序 ID 并复制它。</span><span class="sxs-lookup"><span data-stu-id="40c9c-127">Click the application ID and copy it.</span></span> <span data-ttu-id="40c9c-128">将其粘贴到可以轻松访问的位置。</span><span class="sxs-lookup"><span data-stu-id="40c9c-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="40c9c-130">创建新的 unity 项目，并将其命名为 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="40c9c-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="40c9c-131">有关如何创建新 Unity 项目的说明，请参阅[基本模块的 "创建 Unity 项目" 部分](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="40c9c-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="40c9c-132">加载项目后，单击 "资产存储" 选项卡，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="40c9c-132">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="40c9c-133">然后，在下图中突出显示的 "搜索" 框中，键入 "双关语"，然后从搜索结果中选择 "Photon 双关语 2-免费" 资产。</span><span class="sxs-lookup"><span data-stu-id="40c9c-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="40c9c-135">通过按 "下载" 和 "导入" 按钮来下载和导入此资产。</span><span class="sxs-lookup"><span data-stu-id="40c9c-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="40c9c-137">完成导入过程后，将显示双关语向导 Photon。</span><span class="sxs-lookup"><span data-stu-id="40c9c-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="40c9c-138">获取步骤4中的应用程序 ID （应在剪贴板中），将其粘贴到 "AppID" 框中，然后按 "设置项目" 按钮。</span><span class="sxs-lookup"><span data-stu-id="40c9c-138">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="40c9c-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="40c9c-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="40c9c-140">成功添加 AppID 后，导航到资产中的 Photon-> PhotonUnityNetworking > 资源-> PhotonServerSettings。</span><span class="sxs-lookup"><span data-stu-id="40c9c-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="40c9c-141">选择 "使用名称服务器" 选项，并将 "固定区域" 设置为 "US" 或 "photon" 服务区域。</span><span class="sxs-lookup"><span data-stu-id="40c9c-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="40c9c-143">祝贺</span><span class="sxs-lookup"><span data-stu-id="40c9c-143">Congratulations</span></span>

<span data-ttu-id="40c9c-144">已成功创建 Photon 帐户，设置本地 Photon 服务器，并将双关语导入到 Unity。</span><span class="sxs-lookup"><span data-stu-id="40c9c-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="40c9c-145">下一步是设置项目，并允许与其他用户进行连接，以便多个用户可以看到你的工作。</span><span class="sxs-lookup"><span data-stu-id="40c9c-145">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="40c9c-146">[下一教程： 2. 将 Unity 准备好进行开发](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="40c9c-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

