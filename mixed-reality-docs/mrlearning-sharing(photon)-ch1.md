---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326721"
---
# <a name="setting-up-photon"></a><span data-ttu-id="87ae5-104">Photon 设置</span><span class="sxs-lookup"><span data-stu-id="87ae5-104">Setting Up Photon</span></span>

<span data-ttu-id="87ae5-105">在本课中，我们将了解如何为你的 Unity 项目导入 Photon Unity 网络 （双关语） 创建的共享的体验做好准备。</span><span class="sxs-lookup"><span data-stu-id="87ae5-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="87ae5-106">Photon 是多个网络选项可供 Mixed Reality 开发人员若要创建共享的体验之一。</span><span class="sxs-lookup"><span data-stu-id="87ae5-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="87ae5-107">我们我们将了解如何创建 Photon 帐户、 导入 Photon，并创建可选的本地服务器</span><span class="sxs-lookup"><span data-stu-id="87ae5-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="87ae5-108">目标：</span><span class="sxs-lookup"><span data-stu-id="87ae5-108">Objectives:</span></span>

* <span data-ttu-id="87ae5-109">了解如何创建 Photon 帐户</span><span class="sxs-lookup"><span data-stu-id="87ae5-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="87ae5-110">了解如何查找和导入 Photon Unity 网络</span><span class="sxs-lookup"><span data-stu-id="87ae5-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="87ae5-111">设置本地 Photon server</span><span class="sxs-lookup"><span data-stu-id="87ae5-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="87ae5-112">Photon 设置</span><span class="sxs-lookup"><span data-stu-id="87ae5-112">Setting Up Photon</span></span>

1. <span data-ttu-id="87ae5-113">设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="87ae5-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="87ae5-114">通过单击导航到 Photon 注册页面[此链接](https://dashboard.photonengine.com/en-US/Account/SignUp)。</span><span class="sxs-lookup"><span data-stu-id="87ae5-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="87ae5-115">若要创建该帐户注册页面上按照的说明。</span><span class="sxs-lookup"><span data-stu-id="87ae5-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="87ae5-117">一旦您注册了，单击 Sdk。</span><span class="sxs-lookup"><span data-stu-id="87ae5-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="87ae5-118">后该页面上，单击"服务器"，并确保它说，"自我托管。"</span><span class="sxs-lookup"><span data-stu-id="87ae5-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="87ae5-119">然后向下滚动并单击"服务器"中第二张插图所示。</span><span class="sxs-lookup"><span data-stu-id="87ae5-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="87ae5-122">这将导致文本框中，以便显示标记，"读取我。"</span><span class="sxs-lookup"><span data-stu-id="87ae5-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="87ae5-123">请继续并读取它。</span><span class="sxs-lookup"><span data-stu-id="87ae5-123">Go ahead and read it.</span></span> <span data-ttu-id="87ae5-124">完成后，单击"downloadSDK"若要下载它旁边的链接。</span><span class="sxs-lookup"><span data-stu-id="87ae5-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="87ae5-126">完成下载后，双击单击的文件夹。</span><span class="sxs-lookup"><span data-stu-id="87ae5-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="87ae5-127">在文件资源管理器打开后显示的 SDK 文件夹，将 SDK 文件夹复制。</span><span class="sxs-lookup"><span data-stu-id="87ae5-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="87ae5-128">下一步是转到 windows c： 驱动器并创建新的文件夹名为 server。</span><span class="sxs-lookup"><span data-stu-id="87ae5-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="87ae5-130">现在打开文件夹，并粘贴先前复制的 SDK 文件夹。</span><span class="sxs-lookup"><span data-stu-id="87ae5-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="87ae5-132">完成后，打开 SDK 文件夹并转到"部署"然后"bin_Win64，"，然后双击"photon 控制"。</span><span class="sxs-lookup"><span data-stu-id="87ae5-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="87ae5-134">注意：如果有任何疑问 IP 地址或任何其他类似问题，您可以在工具栏中发现你的信息的大部分，（如下图所示）。</span><span class="sxs-lookup"><span data-stu-id="87ae5-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="87ae5-136">现在，设置并启动服务器，请返回到 Photon 网站并确保仍登录 （或重新登录，如果您不。）单击配置文件图标 （在下图右上角中装箱），然后选择"在应用程序"。</span><span class="sxs-lookup"><span data-stu-id="87ae5-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="87ae5-138">通过单击"创建新的应用程序"按钮创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="87ae5-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="87ae5-140">从"photon 类型。"下的下拉列表菜单中选择"Photon 双关语"</span><span class="sxs-lookup"><span data-stu-id="87ae5-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="87ae5-141">然后为其提供一个名称，在此示例中，我们将其命名为"HoloLensPhotonProject。"</span><span class="sxs-lookup"><span data-stu-id="87ae5-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="87ae5-142">完成后，单击"创建"按钮。</span><span class="sxs-lookup"><span data-stu-id="87ae5-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="87ae5-144">完成后，返回到应用程序页，并应看到类似于下面的图片。</span><span class="sxs-lookup"><span data-stu-id="87ae5-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="87ae5-145">单击应用程序 id 并将其复制。</span><span class="sxs-lookup"><span data-stu-id="87ae5-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="87ae5-146">粘贴是可以轻松访问的某个位置。</span><span class="sxs-lookup"><span data-stu-id="87ae5-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="87ae5-148">创建一个新的 unity 项目并将其命名为"HLSharingProject。"</span><span class="sxs-lookup"><span data-stu-id="87ae5-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="87ae5-149">有关如何创建一个新的 Unity 项目的说明，请参阅[基本模块的"创建 Unity 项目"一节](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="87ae5-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="87ae5-150">项目加载后，单击"资产存储区"选项卡上，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="87ae5-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="87ae5-151">然后，在下图中突出显示搜索框中，键入"双关语"并从搜索结果中选择"Photon 双关语 2 免费"的资产。</span><span class="sxs-lookup"><span data-stu-id="87ae5-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="87ae5-153">下载并导入此资产按"下载"和"导入"按钮。</span><span class="sxs-lookup"><span data-stu-id="87ae5-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="87ae5-155">祝贺</span><span class="sxs-lookup"><span data-stu-id="87ae5-155">Congratulations</span></span>

<span data-ttu-id="87ae5-156">已成功创建 Photon 帐户、 设置本地 Photon 服务器，并导入 Unity 俏皮话。</span><span class="sxs-lookup"><span data-stu-id="87ae5-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="87ae5-157">下一步是将设置项目，然后允许与其他用户的连接，以便多个用户可以看到您的工作。</span><span class="sxs-lookup"><span data-stu-id="87ae5-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="87ae5-158">[下一课：第 2 课 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="87ae5-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

