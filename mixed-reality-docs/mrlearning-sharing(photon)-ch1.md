---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416118"
---
# <a name="setting-up-photon"></a><span data-ttu-id="1b256-104">Photon 设置</span><span class="sxs-lookup"><span data-stu-id="1b256-104">Setting Up Photon</span></span>

<span data-ttu-id="1b256-105">在本课中，我们将了解如何为你的 Unity 项目导入 Photon Unity 网络 （双关语） 创建的共享的体验做好准备。</span><span class="sxs-lookup"><span data-stu-id="1b256-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="1b256-106">Photon 是多个网络选项可供 Mixed Reality 开发人员若要创建共享的体验之一。</span><span class="sxs-lookup"><span data-stu-id="1b256-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="1b256-107">我们我们将了解如何创建 Photon 帐户、 导入 Photon，并创建可选的本地服务器</span><span class="sxs-lookup"><span data-stu-id="1b256-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="1b256-108">目标：</span><span class="sxs-lookup"><span data-stu-id="1b256-108">Objectives:</span></span>

* <span data-ttu-id="1b256-109">了解如何创建 Photon 帐户</span><span class="sxs-lookup"><span data-stu-id="1b256-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="1b256-110">了解如何查找和导入 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="1b256-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="1b256-111">设置本地 Photon server</span><span class="sxs-lookup"><span data-stu-id="1b256-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="1b256-112">Photon 设置</span><span class="sxs-lookup"><span data-stu-id="1b256-112">Setting Up Photon</span></span>

1. <span data-ttu-id="1b256-113">设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="1b256-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="1b256-114">通过单击导航到 Photon 注册页面[此链接](https://dashboard.photonengine.com/en-US/Account/SignUp)。</span><span class="sxs-lookup"><span data-stu-id="1b256-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="1b256-115">若要创建该帐户注册页面上按照的说明。</span><span class="sxs-lookup"><span data-stu-id="1b256-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="1b256-118">通过单击"创建新的应用程序"按钮创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="1b256-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="1b256-120">从"photon 类型。"下的下拉列表菜单中选择"Photon 双关语"</span><span class="sxs-lookup"><span data-stu-id="1b256-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="1b256-121">然后为其提供一个名称，在此示例中，我们将其命名为"HoloLensPhotonProject。"</span><span class="sxs-lookup"><span data-stu-id="1b256-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="1b256-122">完成后，单击"创建"按钮。</span><span class="sxs-lookup"><span data-stu-id="1b256-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="1b256-124">完成后，返回到应用程序页，并应看到类似于下面的图片。</span><span class="sxs-lookup"><span data-stu-id="1b256-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="1b256-125">单击应用程序 id 并将其复制。</span><span class="sxs-lookup"><span data-stu-id="1b256-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="1b256-126">粘贴是可以轻松访问的某个位置。</span><span class="sxs-lookup"><span data-stu-id="1b256-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="1b256-128">创建一个新的 unity 项目并将其命名为"HLSharingProject。"</span><span class="sxs-lookup"><span data-stu-id="1b256-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="1b256-129">有关如何创建一个新的 Unity 项目的说明，请参阅[基本模块的"创建 Unity 项目"一节](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="1b256-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="1b256-130">项目加载后，单击"资产存储区"选项卡上，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="1b256-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="1b256-131">然后，在下图中突出显示搜索框中，键入"双关语"并从搜索结果中选择"Photon 双关语 2-免费"资产。</span><span class="sxs-lookup"><span data-stu-id="1b256-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="1b256-133">下载并导入此资产按"下载"和"导入"按钮。</span><span class="sxs-lookup"><span data-stu-id="1b256-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="1b256-135">Photon 完成导入进程，将出现双关语向导。</span><span class="sxs-lookup"><span data-stu-id="1b256-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="1b256-136">获取第 4 步中的应用程序 ID （它应位于您的剪贴板上） 并将其粘贴到 AppID 框中，并按"安装项目"按钮。</span><span class="sxs-lookup"><span data-stu-id="1b256-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="1b256-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1b256-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="1b256-138">已成功添加后 AppID，导航到"Photon"->"PhotonUnityNetworking"->"资源"->"PhotonServerSettings"中的资产。</span><span class="sxs-lookup"><span data-stu-id="1b256-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="1b256-139">选择"使用名称服务器"选项，将固定的区域设置为"我们"或你 photon 服务区域。</span><span class="sxs-lookup"><span data-stu-id="1b256-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1b256-141">祝贺</span><span class="sxs-lookup"><span data-stu-id="1b256-141">Congratulations</span></span>

<span data-ttu-id="1b256-142">已成功创建 Photon 帐户、 设置本地 Photon 服务器，并导入 Unity 俏皮话。</span><span class="sxs-lookup"><span data-stu-id="1b256-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="1b256-143">下一步是将设置项目，然后允许与其他用户的连接，以便多个用户可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="1b256-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="1b256-144">[下一课：第 2 课 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="1b256-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

