---
title: MR 学习 ASA 模块上 HoloLens 2 Azure 空间的定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327402"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="ce2e5-104">Photon （更正我如果我是错误）</span><span class="sxs-lookup"><span data-stu-id="ce2e5-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="ce2e5-105">在本课中，</span><span class="sxs-lookup"><span data-stu-id="ce2e5-105">In this lesson,</span></span> 

<span data-ttu-id="ce2e5-106">目标：</span><span class="sxs-lookup"><span data-stu-id="ce2e5-106">Objectives:</span></span>

* <span data-ttu-id="ce2e5-107">了解如何 ___</span><span class="sxs-lookup"><span data-stu-id="ce2e5-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="ce2e5-108">了解如何 ___</span><span class="sxs-lookup"><span data-stu-id="ce2e5-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="ce2e5-109">说明</span><span class="sxs-lookup"><span data-stu-id="ce2e5-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="ce2e5-110">Photon 设置</span><span class="sxs-lookup"><span data-stu-id="ce2e5-110">Setting Up Photon</span></span>

1. <span data-ttu-id="ce2e5-111">设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="ce2e5-112">执行此操作将包含输入你的电子邮件和经过一些验证步骤。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="ce2e5-114">一旦您注册了，单击 Sdk。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="ce2e5-115">后该页面上，单击"服务器"，并确保它说，"自我托管。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="ce2e5-116">然后向下滚动并单击"服务器"中第二张插图所示。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="ce2e5-119">这将导致文本框中，以便显示标记，"读取我。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="ce2e5-120">请继续并读取它。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-120">Go ahead and read it.</span></span> <span data-ttu-id="ce2e5-121">完成后，单击"downloadSDK"若要下载它旁边的链接。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="ce2e5-123">完成下载后，双击单击的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="ce2e5-124">在文件资源管理器打开后显示的 SDK 文件夹，将 SDK 文件夹复制。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="ce2e5-125">下一步是转到 windows c： 驱动器并创建新的文件夹名为 server。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="ce2e5-127">现在打开文件夹，并粘贴先前复制的 SDK 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="ce2e5-129">完成后，打开 SDK 文件夹并转到"部署"然后"bin_Win64，"，然后双击"photon 控制"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="ce2e5-131">注意：如果有任何疑问 IP 地址或任何其他类似问题，您可以在工具栏中发现你的信息的大部分，（如下图所示）。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="ce2e5-133">现在，设置并启动服务器，回到 Photon 网站并单击配置文件图标 （如下图中装箱） 并选择"在应用程序"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="ce2e5-135">通过单击"创建新的应用程序"按钮创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="ce2e5-137">从"photon 类型。"下的下拉列表菜单中选择"Photon 运行"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="ce2e5-138">然后为其提供一个名称，（这会记住）。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="ce2e5-139">在此示例中，我们其命名为"HoloLensPhotonProject。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="ce2e5-140">完成后，单击"创建"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="ce2e5-142">完成后，返回到应用程序页，并应看到类似于下面的图片。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="ce2e5-143">单击应用程序 id 并将其复制。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="ce2e5-144">粘贴是可以轻松访问的某个位置。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="ce2e5-146">创建新的 unity 项目。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-146">Create a new unity project.</span></span> <span data-ttu-id="ce2e5-147">打开 Unity 中心，然后单击"new。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="ce2e5-148">其命名为"HLSharingProject。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="ce2e5-149">然后单击创建。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-149">Then click create.</span></span> 

   > <span data-ttu-id="ce2e5-150">注意：这可能需要 2 分钟的时间来加载，请根据您的计算机的速度。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="ce2e5-152">注意： 选择一个位置来保存在计算机中的项目，通过更改"位置"选项。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="ce2e5-153">将其保存到您能记住并轻松访问的位置。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="ce2e5-154">项目加载后，单击"资产 store"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="ce2e5-155">然后，在搜索框中显示下图中，键入"双关语"并选择"Photon 双关语 2 免费"资产。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="ce2e5-157">下载并导入 ！</span><span class="sxs-lookup"><span data-stu-id="ce2e5-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="ce2e5-159">**设置 Unity 项目**</span><span class="sxs-lookup"><span data-stu-id="ce2e5-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="ce2e5-160">下载新的资产所需设置 Photon Unity 中通过单击[此处。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="ce2e5-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="ce2e5-161">在 Unity 中，单击资产菜单并选择"导入资产，"，然后单击"自定义的资产。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="ce2e5-163">选择您刚从在步骤 1 中提供的链接下载 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="ce2e5-164">后的导入按钮出现在 Unity 中，单击它。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="ce2e5-166">注意： 下载到包的任何位置将在哪里找到它。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="ce2e5-167">上图没有描绘出将在何处找到程序包。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="ce2e5-168">创建新的场景 (这可以是已通过使用控件 / 命令 + N 或通过单击"文件"并选择"新的场景。")。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="ce2e5-169">将场景另存为"HLSharedProjectMain。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="ce2e5-170">注意： 可能会收到一个弹出窗口，它看起来类似于下图所示。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="ce2e5-171">现在，只需单击"否"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="ce2e5-173">在"混合现实 Toolkit"单击"将添加到场景和配置"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="ce2e5-175">完成后完成后，新的配置文件将出现，让您选择自定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="ce2e5-176">单击"复制和自定义"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="ce2e5-178">向下滚动并取消选中"启用诊断系统。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="ce2e5-179">这将使更方便地设置此项目。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="ce2e5-181">打开生成设置 （控制 + shift + B）。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="ce2e5-182">请注意，该程序当前在"电脑、 Mac 和 Linux 独立"平台设置。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="ce2e5-183">对于此项目，将设置为"通用 windows 平台。"的平台</span><span class="sxs-lookup"><span data-stu-id="ce2e5-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="ce2e5-184">选择它，然后单击"切换平台"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="ce2e5-186">完成后，单击框，其中显示"添加打开的场景。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="ce2e5-187">现在请转到检查器面板，并确保右侧的"支持的虚拟现实"复选框 （如在下图中所示） 已选中。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="ce2e5-189">注意：此外请确保也选中"场景/HLSharedProjectMain"旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="ce2e5-190">在检查器面板中的"发布设置"向下滚动到"功能"，并确保标记仅以下复选框：</span><span class="sxs-lookup"><span data-stu-id="ce2e5-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="ce2e5-191">internet 客户端</span><span class="sxs-lookup"><span data-stu-id="ce2e5-191">internet client</span></span>
- <span data-ttu-id="ce2e5-192">internet 客户端服务器</span><span class="sxs-lookup"><span data-stu-id="ce2e5-192">internet client server</span></span>
- <span data-ttu-id="ce2e5-193">专用网络客户端服务器</span><span class="sxs-lookup"><span data-stu-id="ce2e5-193">private network client server</span></span>
- <span data-ttu-id="ce2e5-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="ce2e5-194">camera/webcam</span></span>
- <span data-ttu-id="ce2e5-195">麦克风</span><span class="sxs-lookup"><span data-stu-id="ce2e5-195">microphone</span></span>

21. <span data-ttu-id="ce2e5-196">就像步骤 12 中下, 一步是导入另一个名为"第 2 课"可以在 [此处]。 下载的自定义包[此处显示 lesson2.unitypackage 链接]导入该包。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="ce2e5-198">现在，在项目面板中，转到"预设"文件夹，因为下一步的几个步骤中您将执行向场景的几个预设。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="ce2e5-199">在"预设"文件夹中，单击并拖动预设可在层次结构"DebugWindow"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="ce2e5-200">完成后，保存项目 (单击文件，然后保存，或控制 + S)</span><span class="sxs-lookup"><span data-stu-id="ce2e5-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="ce2e5-202">注意：您可能注意到一个弹出窗口，显示当您单击预设可，询问您 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="ce2e5-203">单击"导入 TMP Essentials"，因为将需要它们。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="ce2e5-205">**将多个用户连接**</span><span class="sxs-lookup"><span data-stu-id="ce2e5-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="ce2e5-206">步骤 22 的"预设"文件夹中的项目面板中，正如下一步是拖放到层次结构删除"NetworkLobby"预设。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="ce2e5-208">当您打开父预设，"NetworkLobby，"应该会看到子预设，"NetworkRoom。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="ce2e5-209">使用它选择，请转到检查器面板并单击"添加组件"。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="ce2e5-210">搜索"PhotonView"并添加该组件。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="ce2e5-212">在层次结构 （右键单击在层次结构中，选择"空"） 中创建一个新的空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="ce2e5-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="ce2e5-213">确保将位置设置为 x = 0，y = 0，z = 0，命名该对象，"PhotonUser。"</span><span class="sxs-lookup"><span data-stu-id="ce2e5-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="ce2e5-215">祝贺</span><span class="sxs-lookup"><span data-stu-id="ce2e5-215">Congratulations</span></span>



