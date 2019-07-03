# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="f83bf-101">让 Unity 开发做好准备</span><span class="sxs-lookup"><span data-stu-id="f83bf-101">Getting Unity ready for development</span></span> 

<span data-ttu-id="f83bf-102">在本教程中，我们将了解如何准备和配置 Unity 应用程序开发，包括导入混合现实工具包、 配置生成设置和准备场景。</span><span class="sxs-lookup"><span data-stu-id="f83bf-102">In this tutorial, we learn how to prepare and configure Unity for applicaiton development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="f83bf-103">目标：</span><span class="sxs-lookup"><span data-stu-id="f83bf-103">Objectives:</span></span>

- <span data-ttu-id="f83bf-104">配置 Unity 应用程序开发</span><span class="sxs-lookup"><span data-stu-id="f83bf-104">Configure Unity for applicaiton development</span></span>

- <span data-ttu-id="f83bf-105">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="f83bf-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="f83bf-106">准备项目场景</span><span class="sxs-lookup"><span data-stu-id="f83bf-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="f83bf-107">说明</span><span class="sxs-lookup"><span data-stu-id="f83bf-107">Instructions</span></span>

1. <span data-ttu-id="f83bf-108">下载并保存混合现实工具包 unity 包，通过单击[此处。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="f83bf-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="f83bf-109">在 Unity 中，单击资产菜单，选择导入包，然后单击自定义包。</span><span class="sxs-lookup"><span data-stu-id="f83bf-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="f83bf-111">选择您刚从在步骤 1 中提供的链接下载 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="f83bf-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="f83bf-112">导入弹出窗口出现后在 Unity 中，单击导入按钮以开始导入。</span><span class="sxs-lookup"><span data-stu-id="f83bf-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="f83bf-113">导入 MRTK 可能需要几分钟。</span><span class="sxs-lookup"><span data-stu-id="f83bf-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="f83bf-115">注意：下载的包是在你保存文件的本地文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f83bf-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="f83bf-116">上图没有描绘出将在何处找到程序包。</span><span class="sxs-lookup"><span data-stu-id="f83bf-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="f83bf-117">创建新的场景。</span><span class="sxs-lookup"><span data-stu-id="f83bf-117">Create a new scene.</span></span> <span data-ttu-id="f83bf-118">此可通过单击文件，并选择新的场景"）。</span><span class="sxs-lookup"><span data-stu-id="f83bf-118">Tthis can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="f83bf-119">将场景另存为 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="f83bf-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="f83bf-120">注意： 可能会收到一个弹出窗口，它看起来类似于下图所示。</span><span class="sxs-lookup"><span data-stu-id="f83bf-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="f83bf-121">现在，请单击不可以。</span><span class="sxs-lookup"><span data-stu-id="f83bf-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="f83bf-123">在混合现实工具包，单击添加到场景和配置。</span><span class="sxs-lookup"><span data-stu-id="f83bf-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="f83bf-125">完成后完成后，新的配置文件会出现，让您自定义配置文件的选择。</span><span class="sxs-lookup"><span data-stu-id="f83bf-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="f83bf-126">单击复制和自定义。</span><span class="sxs-lookup"><span data-stu-id="f83bf-126">Click Copy and Customize.</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="f83bf-130">向下滚动并取消选中启用 Siagnostics 系统，如果你想要隐藏诊断窗口。</span><span class="sxs-lookup"><span data-stu-id="f83bf-130">Scroll down and uncheck Enable Siagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="f83bf-131">我们建议保持诊断窗口启用应用程序开发期间来监视性能，并在生产环境或应用程序演示期间禁用它。</span><span class="sxs-lookup"><span data-stu-id="f83bf-131">We recommend keeping the diagnostics window enabled during applicaiton development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="f83bf-133">打开通过按 control + shift + B 或转到文件的生成设置-> 生成设置。</span><span class="sxs-lookup"><span data-stu-id="f83bf-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="f83bf-134">请注意，该程序当前设置在 PC、 Mac 和 Linux 独立平台。</span><span class="sxs-lookup"><span data-stu-id="f83bf-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="f83bf-135">对于 HoloLens 2 开发，设置要为通用 Windows 平台的平台。</span><span class="sxs-lookup"><span data-stu-id="f83bf-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="f83bf-136">选择它，然后单击切换平台。</span><span class="sxs-lookup"><span data-stu-id="f83bf-136">Select it and click Switch Platform.</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="f83bf-138">完成后，单击添加打开场景框。</span><span class="sxs-lookup"><span data-stu-id="f83bf-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="f83bf-139">现在转到检查器面板中，并确保选中该复选框右侧的虚拟现实支持 （如下图所示）。</span><span class="sxs-lookup"><span data-stu-id="f83bf-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="f83bf-140">此外确保场景/HLSharedProjectMain 旁边的复选框还选中下图中所示。</span><span class="sxs-lookup"><span data-stu-id="f83bf-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="f83bf-142">在检查器面板中的发布设置部分中，向下滚动到功能，并确保标记下面的复选框：</span><span class="sxs-lookup"><span data-stu-id="f83bf-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="f83bf-144">导入自定义包调用可以在下载 SharingAssetCollection[此处。](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f83bf-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="f83bf-145">在项目面板中，转到置入 Prefabs 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f83bf-145">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="f83bf-146">在下一步的几个步骤中，您将实现向场景的几个预设。</span><span class="sxs-lookup"><span data-stu-id="f83bf-146">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="f83bf-147">中置入 Prefabs 文件夹中，单击并拖动预设可 DebugWindow 到层次结构。</span><span class="sxs-lookup"><span data-stu-id="f83bf-147">In the Prefabs folder, click and drag the prefab, DebugWindow into the hierarchy.</span></span> <span data-ttu-id="f83bf-148">完成后，将项目保存由 clckin 文件，然后保存或按控件 + S。</span><span class="sxs-lookup"><span data-stu-id="f83bf-148">Once finished, save the project by clckin File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="f83bf-150">注意：您可能注意到一个弹出窗口，显示当您单击预设可，询问您 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="f83bf-150">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="f83bf-151">单击导入 TMP Essentials，因为需要它们。</span><span class="sxs-lookup"><span data-stu-id="f83bf-151">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="f83bf-152">如果此弹出窗口，您可能需要删除预设可从你的层次结构并重新将其拖到层次结构，以避免潜在与文本相关的错误。</span><span class="sxs-lookup"><span data-stu-id="f83bf-152">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="f83bf-154">祝贺</span><span class="sxs-lookup"><span data-stu-id="f83bf-154">Congratulations</span></span>

<span data-ttu-id="f83bf-155">你的 Unity 项目现已准备好 Photon。</span><span class="sxs-lookup"><span data-stu-id="f83bf-155">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="f83bf-156">在接下来的教程中，我们将在此场景和我们的 Unity 项目针对完整的共享体验为基础进行构建。</span><span class="sxs-lookup"><span data-stu-id="f83bf-156">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="f83bf-157">[下一教程：将多个用户连接](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="f83bf-157">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

