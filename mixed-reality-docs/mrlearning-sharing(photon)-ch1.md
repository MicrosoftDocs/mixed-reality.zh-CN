---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523298"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="da90b-104">Photon Unity 网络设置</span><span class="sxs-lookup"><span data-stu-id="da90b-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="da90b-105">在本教程中，我们将了解如何为你的 Unity 项目导入 Photon Unity 网络 （双关语） 创建的共享的体验做好准备。</span><span class="sxs-lookup"><span data-stu-id="da90b-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="da90b-106">Photon 是多个网络选项可供 Mixed Reality 开发人员若要创建共享的体验之一。</span><span class="sxs-lookup"><span data-stu-id="da90b-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="da90b-107">我们我们将了解如何创建 Photon 帐户、 导入 Photon，并创建可选的本地服务器</span><span class="sxs-lookup"><span data-stu-id="da90b-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="da90b-108">目标：</span><span class="sxs-lookup"><span data-stu-id="da90b-108">Objectives:</span></span>

* <span data-ttu-id="da90b-109">了解如何创建 Photon 帐户</span><span class="sxs-lookup"><span data-stu-id="da90b-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="da90b-110">了解如何查找和导入 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="da90b-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="da90b-111">设置本地 Photon server</span><span class="sxs-lookup"><span data-stu-id="da90b-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="da90b-112">Photon 设置</span><span class="sxs-lookup"><span data-stu-id="da90b-112">Setting up Photon</span></span>

1. <span data-ttu-id="da90b-113">设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="da90b-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="da90b-114">通过单击导航到 Photon 注册页面[此链接](https://dashboard.photonengine.com/en-US/Account/SignUp)。</span><span class="sxs-lookup"><span data-stu-id="da90b-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="da90b-115">若要创建该帐户注册页面上按照的说明。</span><span class="sxs-lookup"><span data-stu-id="da90b-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="da90b-118">通过单击创建新的应用程序按钮创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="da90b-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="da90b-120">从 Photon 类型下的下拉列表菜单中选择 Photon 俏皮话。</span><span class="sxs-lookup"><span data-stu-id="da90b-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="da90b-121">然后为其提供一个名称。</span><span class="sxs-lookup"><span data-stu-id="da90b-121">Then give it a name.</span></span> <span data-ttu-id="da90b-122">在此示例中，我们命名为它 HoloLensPhotonProject。</span><span class="sxs-lookup"><span data-stu-id="da90b-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="da90b-123">完成后，单击创建按钮。</span><span class="sxs-lookup"><span data-stu-id="da90b-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="da90b-125">完成后，返回到应用程序页，并应看到类似于下面的图片。</span><span class="sxs-lookup"><span data-stu-id="da90b-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="da90b-126">单击应用程序 ID 并将其复制。</span><span class="sxs-lookup"><span data-stu-id="da90b-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="da90b-127">粘贴是可以轻松访问的某个位置。</span><span class="sxs-lookup"><span data-stu-id="da90b-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="da90b-129">创建一个新的 unity 项目并将其命名 HLSharingProject。</span><span class="sxs-lookup"><span data-stu-id="da90b-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="da90b-130">有关如何创建一个新的 Unity 项目的说明，请参阅[基本模块的"创建 Unity 项目"一节](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="da90b-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="da90b-131">项目加载后，单击资产应用商店选项卡，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="da90b-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="da90b-132">然后，在下图中突出显示搜索框中，键入双关语，然后选择如 FRE 的 Photon 双关语 2-"从搜索结果中的资产。</span><span class="sxs-lookup"><span data-stu-id="da90b-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="da90b-134">下载并导入此资产按下载并导入按钮。</span><span class="sxs-lookup"><span data-stu-id="da90b-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="da90b-136">Photon 完成导入进程，将显示双关语向导。</span><span class="sxs-lookup"><span data-stu-id="da90b-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="da90b-137">获取应用程序 ID （它应位于您的剪贴板上） 从步骤 4，并将其粘贴到 AppID 框中，并按安装项目按钮。</span><span class="sxs-lookup"><span data-stu-id="da90b-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="da90b-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="da90b-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="da90b-139">已成功添加后 AppID，导航到 Photon-> PhotonUnityNetworking-> 资源-> PhotonServerSettings 资产中的。</span><span class="sxs-lookup"><span data-stu-id="da90b-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="da90b-140">选择使用名称服务器选项，并设置对我们的固定的区域或 yourPphoton 服务区域。</span><span class="sxs-lookup"><span data-stu-id="da90b-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="da90b-142">祝贺</span><span class="sxs-lookup"><span data-stu-id="da90b-142">Congratulations</span></span>

<span data-ttu-id="da90b-143">已成功创建 Photon 帐户、 设置本地 Photon 服务器，并导入 Unity 俏皮话。</span><span class="sxs-lookup"><span data-stu-id="da90b-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="da90b-144">下一步是将设置项目，然后允许与其他用户的连接，以便多个用户可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="da90b-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="da90b-145">[下一教程：让 Unity 开发做好准备](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="da90b-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

