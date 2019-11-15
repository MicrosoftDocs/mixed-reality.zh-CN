---
title: 多用户功能教程-2。 正在准备好用于开发的 Unity
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 750161ff4c52a7ab71869b3cb0f97197d4ad09f2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106049"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="806e6-105">2. 获取 Unity 以便开发</span><span class="sxs-lookup"><span data-stu-id="806e6-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="806e6-106">在本教程中，你将了解如何为应用程序开发准备和配置 Unity，包括导入混合现实工具包、配置生成设置和准备场景。</span><span class="sxs-lookup"><span data-stu-id="806e6-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="806e6-107">目标</span><span class="sxs-lookup"><span data-stu-id="806e6-107">Objectives</span></span>

- <span data-ttu-id="806e6-108">为应用程序开发配置 Unity</span><span class="sxs-lookup"><span data-stu-id="806e6-108">Configure Unity for application development</span></span>

- <span data-ttu-id="806e6-109">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="806e6-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="806e6-110">准备项目场景</span><span class="sxs-lookup"><span data-stu-id="806e6-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="806e6-111">说明</span><span class="sxs-lookup"><span data-stu-id="806e6-111">Instructions</span></span>

1. <span data-ttu-id="806e6-112">单击此处下载并保存混合现实工具包 Foundation unity 包[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="806e6-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="806e6-113">在 Unity 中，单击 "资产" 菜单并选择 "导入包"，然后单击 "自定义包"。</span><span class="sxs-lookup"><span data-stu-id="806e6-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="806e6-115">选择刚刚从步骤1中提供的链接下载的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="806e6-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="806e6-116">导入弹出窗口出现在 Unity 中后，单击 "导入" 按钮以开始导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="806e6-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="806e6-117">这可能需要几分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="806e6-117">This may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="806e6-119">注意：下载的包位于你的本地文件夹中，你在该文件夹中保存了该文件。</span><span class="sxs-lookup"><span data-stu-id="806e6-119">Note: The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="806e6-120">上面的图像不会描绘出包的位置。</span><span class="sxs-lookup"><span data-stu-id="806e6-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="806e6-121">创建新场景。</span><span class="sxs-lookup"><span data-stu-id="806e6-121">Create a new scene.</span></span> <span data-ttu-id="806e6-122">可以通过单击 "文件" 并选择 "新建场景" 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="806e6-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="806e6-123">将其保存为 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="806e6-123">Save it as HLSharedProjectMain.</span></span>

> <span data-ttu-id="806e6-124">注意：你可能会收到类似于下面的图像的弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="806e6-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="806e6-125">现在，单击 "否"。</span><span class="sxs-lookup"><span data-stu-id="806e6-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="806e6-127">在 "混合现实工具包" 下，单击 "添加到场景" 并配置。</span><span class="sxs-lookup"><span data-stu-id="806e6-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="806e6-129">完成后，将显示一个新的配置文件，让你选择自定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="806e6-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> 

![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="806e6-131">从层次结构中选择混合现实工具包（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="806e6-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="806e6-132">在 "检查器" 面板中，查找混合现实工具包脚本并按下图所示的 "复制 & 自定义" 按钮。</span><span class="sxs-lookup"><span data-stu-id="806e6-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="806e6-133">此时将显示一个 pop，并在弹出菜单中选择 "克隆" 选项。</span><span class="sxs-lookup"><span data-stu-id="806e6-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

7. <span data-ttu-id="806e6-136">如果要隐藏诊断窗口，请向下滚动并取消选中 "启用诊断系统"。</span><span class="sxs-lookup"><span data-stu-id="806e6-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="806e6-137">建议在应用程序开发过程中保持诊断窗口处于启用状态，以监视性能，然后在生产或应用程序演示过程中禁用它。</span><span class="sxs-lookup"><span data-stu-id="806e6-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="806e6-139">按 ctrl + shift + B 打开生成设置，或转到 "文件 > 生成设置"。</span><span class="sxs-lookup"><span data-stu-id="806e6-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="806e6-140">请注意，该程序当前设置在 PC、Mac 和 Linux 独立平台下。</span><span class="sxs-lookup"><span data-stu-id="806e6-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="806e6-141">对于 HoloLens 2 开发，请将平台设置为通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="806e6-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="806e6-142">选择它并单击 "切换平台"。</span><span class="sxs-lookup"><span data-stu-id="806e6-142">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="806e6-144">完成后，单击名为 "添加打开场景" 的框。</span><span class="sxs-lookup"><span data-stu-id="806e6-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="806e6-145">现在，请前往检查器面板，确保选中 "支持的虚拟现实（如下图中所示）" 右侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="806e6-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="806e6-146">还要确保还检查了 "场景/HLSharedProjectMain" 旁边的复选框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="806e6-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="806e6-148">在 "检查器" 面板中的 "发布设置" 部分下，向下滚动到 "功能" 并确保以下复选框已标记：</span><span class="sxs-lookup"><span data-stu-id="806e6-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="806e6-150">导入列出的自定义包：</span><span class="sxs-lookup"><span data-stu-id="806e6-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="806e6-151">a.</span><span class="sxs-lookup"><span data-stu-id="806e6-151">a.</span></span> [<span data-ttu-id="806e6-152">HoloLens2. GettingStarted. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="806e6-152">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    <span data-ttu-id="806e6-153">b.</span><span class="sxs-lookup"><span data-stu-id="806e6-153">b.</span></span> [<span data-ttu-id="806e6-154">HoloLens2. MultiUserCapabilities. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="806e6-154">Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    ><span data-ttu-id="806e6-155">如果你已完成[入门教程](mrlearning-base-ch1.md)，则你的计算机上可能会存储名为 HoloLens2 的 unity 包。 _2.1.0.0. unitypackage_ 。</span><span class="sxs-lookup"><span data-stu-id="806e6-155">If you have completed the [Getting started tutorials](mrlearning-base-ch1.md), you might still have the Unity package named _Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage_ stored on your computer.</span></span> <span data-ttu-id="806e6-156">如果是这样，则可以跳过下载上一步中列出的资产。</span><span class="sxs-lookup"><span data-stu-id="806e6-156">If so, you can skip downloading the asset listed in step a above.</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="806e6-158">在 "项目" 面板中，切换到 Prototyping 文件夹。</span><span class="sxs-lookup"><span data-stu-id="806e6-158">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="806e6-159">在下面的步骤中，你将在场景中实施几个 prototyping。</span><span class="sxs-lookup"><span data-stu-id="806e6-159">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="806e6-160">在 Prototyping 文件夹中，单击 "prefab" 并将其拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="806e6-160">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="806e6-161">完成后，单击 "文件"，然后单击 "保存" 或按 Ctrl + S 保存该项目。</span><span class="sxs-lookup"><span data-stu-id="806e6-161">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="806e6-163">注意：你可能会注意到，单击 prefab 时，会显示一个弹出窗口，询问你有关 TMP Essentials 的信息。</span><span class="sxs-lookup"><span data-stu-id="806e6-163">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="806e6-164">单击 "需要时导入 TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="806e6-164">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="806e6-165">如果出现此弹出窗口，可能需要从层次结构中删除 prefab，并将其重新拖到层次结构中，以避免出现与文本相关的潜在错误。</span><span class="sxs-lookup"><span data-stu-id="806e6-165">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="806e6-167">祝贺</span><span class="sxs-lookup"><span data-stu-id="806e6-167">Congratulations</span></span>

<span data-ttu-id="806e6-168">你的 Unity 项目现在已准备好 Photon。</span><span class="sxs-lookup"><span data-stu-id="806e6-168">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="806e6-169">在随后的教程中，我们将在此场景和 Unity 项目的基础上构建全面的共享体验。</span><span class="sxs-lookup"><span data-stu-id="806e6-169">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="806e6-170">[下一教程： 3. 连接多个用户](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="806e6-170">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

