---
title: 在 HoloLens 2 上学习 ASA 模块 Azure 空间锚的 MR
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
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="af464-104">Photon (如果错误, 请更正我)</span><span class="sxs-lookup"><span data-stu-id="af464-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="af464-105">在本课中,</span><span class="sxs-lookup"><span data-stu-id="af464-105">In this lesson,</span></span> 

<span data-ttu-id="af464-106">目标</span><span class="sxs-lookup"><span data-stu-id="af464-106">Objectives:</span></span>

* <span data-ttu-id="af464-107">了解如何 _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="af464-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="af464-108">了解如何 _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="af464-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="af464-109">说明</span><span class="sxs-lookup"><span data-stu-id="af464-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="af464-110">设置 Photon</span><span class="sxs-lookup"><span data-stu-id="af464-110">Setting Up Photon</span></span>

1. <span data-ttu-id="af464-111">设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。</span><span class="sxs-lookup"><span data-stu-id="af464-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="af464-112">执行此操作将会输入你的电子邮件并完成一些验证步骤。</span><span class="sxs-lookup"><span data-stu-id="af464-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="af464-114">注册后, 单击 "Sdk"。</span><span class="sxs-lookup"><span data-stu-id="af464-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="af464-115">一旦处于该页上, 请单击 "服务器", 并确保显示 "自承载"。</span><span class="sxs-lookup"><span data-stu-id="af464-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="af464-116">然后向下滚动并单击 "服务器", 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="af464-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="af464-119">这将导致文本框显示为 "阅读我"。</span><span class="sxs-lookup"><span data-stu-id="af464-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="af464-120">继续阅读。</span><span class="sxs-lookup"><span data-stu-id="af464-120">Go ahead and read it.</span></span> <span data-ttu-id="af464-121">完成后, 单击 "downloadSDK" 旁边的链接以下载它。</span><span class="sxs-lookup"><span data-stu-id="af464-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="af464-123">下载完成后, 双击该文件夹。</span><span class="sxs-lookup"><span data-stu-id="af464-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="af464-124">文件资源管理器打开并公开 SDK 文件夹后, 请复制 SDK 文件夹。</span><span class="sxs-lookup"><span data-stu-id="af464-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="af464-125">下一步是进入 windows C: 驱动器, 并创建名为 "server" 的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="af464-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="af464-127">现在打开文件夹, 然后粘贴前面复制的 SDK 文件夹。</span><span class="sxs-lookup"><span data-stu-id="af464-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="af464-129">完成后, 打开 SDK 文件夹, 然后前往 "部署", 然后单击 "bin_Win64", 然后双击 "photon 控件"。</span><span class="sxs-lookup"><span data-stu-id="af464-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="af464-131">注意:如果对 IP 地址或任何其他类似的问题有任何疑问, 则可以在工具栏中找到大多数信息 (如下图所示)。</span><span class="sxs-lookup"><span data-stu-id="af464-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="af464-133">设置并启动服务器后, 请返回到 Photon 网站, 然后单击 "配置文件" 图标 (下图中的 "装箱"), 并选择 "应用程序"。</span><span class="sxs-lookup"><span data-stu-id="af464-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="af464-135">单击 "创建新应用" 按钮, 创建一个应用程序 ID。</span><span class="sxs-lookup"><span data-stu-id="af464-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="af464-137">从 "Photon 类型" 下的下拉菜单中选择 "Photon 运行"。</span><span class="sxs-lookup"><span data-stu-id="af464-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="af464-138">然后为其指定一个名称 (你要记住的内容)。</span><span class="sxs-lookup"><span data-stu-id="af464-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="af464-139">在此示例中, 我们将其命名为 "HoloLensPhotonProject"。</span><span class="sxs-lookup"><span data-stu-id="af464-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="af464-140">完成后, 单击 "创建"。</span><span class="sxs-lookup"><span data-stu-id="af464-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="af464-142">完成后, 返回到应用程序页面, 你应该会看到类似于下图的内容。</span><span class="sxs-lookup"><span data-stu-id="af464-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="af464-143">单击 "应用 ID" 并复制它。</span><span class="sxs-lookup"><span data-stu-id="af464-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="af464-144">可以轻松地进行访问。</span><span class="sxs-lookup"><span data-stu-id="af464-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="af464-146">创建新的 unity 项目。</span><span class="sxs-lookup"><span data-stu-id="af464-146">Create a new unity project.</span></span> <span data-ttu-id="af464-147">打开 Unity 中心, 并单击 "新建"。</span><span class="sxs-lookup"><span data-stu-id="af464-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="af464-148">将其命名为 "HLSharingProject"。</span><span class="sxs-lookup"><span data-stu-id="af464-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="af464-149">然后单击 "创建"。</span><span class="sxs-lookup"><span data-stu-id="af464-149">Then click create.</span></span> 

   > <span data-ttu-id="af464-150">纪录根据计算机的速度, 最多可能需要2分钟的时间来加载。</span><span class="sxs-lookup"><span data-stu-id="af464-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="af464-152">注意: 通过更改 "location" 选项, 选择一个在计算机中保存项目的位置。</span><span class="sxs-lookup"><span data-stu-id="af464-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="af464-153">将其保存到你会记住并可轻松访问的位置。</span><span class="sxs-lookup"><span data-stu-id="af464-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="af464-154">加载项目后, 请单击 "资产存储"。</span><span class="sxs-lookup"><span data-stu-id="af464-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="af464-155">然后, 在下图所示的搜索框中键入 "双关语", 并选择 "Photon 双关语-2 FREE" 资产。</span><span class="sxs-lookup"><span data-stu-id="af464-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="af464-157">下载和导入!</span><span class="sxs-lookup"><span data-stu-id="af464-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="af464-159">**设置 Unity 项目**</span><span class="sxs-lookup"><span data-stu-id="af464-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="af464-160">单击此处, 下载在 Unity 中设置 Photon 所需的新资产[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="af464-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="af464-161">在 Unity 中, 单击 "资产" 菜单并选择 "导入资产", 然后单击 "自定义资产"。</span><span class="sxs-lookup"><span data-stu-id="af464-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="af464-163">选择刚刚从步骤1中提供的链接下载的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="af464-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="af464-164">"导入" 按钮出现在 Unity 中后, 单击该按钮。</span><span class="sxs-lookup"><span data-stu-id="af464-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="af464-166">注意: 无论将包下载到何处, 都可以找到它。</span><span class="sxs-lookup"><span data-stu-id="af464-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="af464-167">上面的图像不会描绘出包的位置。</span><span class="sxs-lookup"><span data-stu-id="af464-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="af464-168">创建新场景 (可以使用 control/command + N 或单击 "文件" 并选择 "新建场景" 来完成此操作。)</span><span class="sxs-lookup"><span data-stu-id="af464-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="af464-169">将场景保存为 "HLSharedProjectMain"。</span><span class="sxs-lookup"><span data-stu-id="af464-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="af464-170">注意: 你可能会收到类似于下面的图像的弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="af464-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="af464-171">现在, 只需单击 "否"。</span><span class="sxs-lookup"><span data-stu-id="af464-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="af464-173">在 "混合现实工具包" 下, 单击 "添加到场景并配置"。</span><span class="sxs-lookup"><span data-stu-id="af464-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="af464-175">完成后, 将出现一个新的配置文件, 允许你选择自定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="af464-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="af464-176">单击 "复制并自定义"。</span><span class="sxs-lookup"><span data-stu-id="af464-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="af464-178">向下滚动并取消选中 "启用诊断系统"。</span><span class="sxs-lookup"><span data-stu-id="af464-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="af464-179">这可以更轻松地设置此项目。</span><span class="sxs-lookup"><span data-stu-id="af464-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="af464-181">打开 "生成设置" (ctrl + shift + B)。</span><span class="sxs-lookup"><span data-stu-id="af464-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="af464-182">请注意, 该程序当前设置在 "PC、Mac 和 Linux 独立版" 平台下。</span><span class="sxs-lookup"><span data-stu-id="af464-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="af464-183">对于此项目, 请将平台设置为 "通用 windows 平台"。</span><span class="sxs-lookup"><span data-stu-id="af464-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="af464-184">选择它并单击 "切换平台"。</span><span class="sxs-lookup"><span data-stu-id="af464-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="af464-186">完成后, 单击显示 "添加打开的场景" 的框。</span><span class="sxs-lookup"><span data-stu-id="af464-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="af464-187">现在, 请前往检查器面板, 确保选中 "受支持的虚拟现实" (如下图所示) 右侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="af464-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="af464-189">纪录还要确保还检查了 "场景/HLSharedProjectMain" 旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="af464-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="af464-190">在 "检查器" 面板中的 "发布设置" 下, 向下滚动到 "功能" 并确保只标记以下复选框:</span><span class="sxs-lookup"><span data-stu-id="af464-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="af464-191">internet 客户端</span><span class="sxs-lookup"><span data-stu-id="af464-191">internet client</span></span>
- <span data-ttu-id="af464-192">internet 客户端服务器</span><span class="sxs-lookup"><span data-stu-id="af464-192">internet client server</span></span>
- <span data-ttu-id="af464-193">专用网络客户端服务器</span><span class="sxs-lookup"><span data-stu-id="af464-193">private network client server</span></span>
- <span data-ttu-id="af464-194">照相机/网络摄像机</span><span class="sxs-lookup"><span data-stu-id="af464-194">camera/webcam</span></span>
- <span data-ttu-id="af464-195">麦克风</span><span class="sxs-lookup"><span data-stu-id="af464-195">microphone</span></span>

21. <span data-ttu-id="af464-196">与步骤12类似, 下一步是导入名为 "第2课" 的另一个自定义包, 可将其下载 [此处]。[第2课 link]导入该包。</span><span class="sxs-lookup"><span data-stu-id="af464-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="af464-198">现在, 在 "项目" 面板中, 请访问 "prototyping" 文件夹, 因为在接下来的几个步骤中, 将在场景中实施一些 prototyping。</span><span class="sxs-lookup"><span data-stu-id="af464-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="af464-199">在 "prototyping" 文件夹中, 单击 "prefab" 并将其拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="af464-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="af464-200">完成后, 保存该项目 (依次单击 "文件"、"保存" 或 "ctrl + S")</span><span class="sxs-lookup"><span data-stu-id="af464-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="af464-202">纪录你可能会注意到, 当你单击 prefab 时, 会显示一个弹出窗口, 询问你有关 TMP Essentials 的信息。</span><span class="sxs-lookup"><span data-stu-id="af464-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="af464-203">如果需要, 请单击 "导入 TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="af464-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="af464-205">**连接多个用户**</span><span class="sxs-lookup"><span data-stu-id="af464-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="af464-206">与步骤22一样, 在 "项目" 面板的 "prototyping" 文件夹中, 下一步是将 "NetworkLobby" prefab 拖放到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="af464-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="af464-208">打开父 prefab "NetworkLobby" 时, 应会看到子 prefab "NetworkRoom"。</span><span class="sxs-lookup"><span data-stu-id="af464-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="af464-209">选择该选项后, 进入检查器面板, 然后单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="af464-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="af464-210">搜索 "PhotonView" 并添加组件。</span><span class="sxs-lookup"><span data-stu-id="af464-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="af464-212">在层次结构中创建新的空游戏对象 (在层次结构中右键单击并选择 "空")。</span><span class="sxs-lookup"><span data-stu-id="af464-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="af464-213">确保将 "位置" 设置为 x = 0、y = 0、z = 0 并将对象命名为 "PhotonUser"。</span><span class="sxs-lookup"><span data-stu-id="af464-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="af464-215">祝贺</span><span class="sxs-lookup"><span data-stu-id="af464-215">Congratulations</span></span>



