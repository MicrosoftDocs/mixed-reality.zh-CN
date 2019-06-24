---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327160"
---
# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="b5beb-104">**让 Unity 开发做好准备**</span><span class="sxs-lookup"><span data-stu-id="b5beb-104">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="b5beb-105">在本课程中，我们将学习如何准备和配置 Unity 应用程序开发，包括导入混合现实工具包、 配置生成设置和准备场景。</span><span class="sxs-lookup"><span data-stu-id="b5beb-105">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="b5beb-106">目标：</span><span class="sxs-lookup"><span data-stu-id="b5beb-106">Objectives:</span></span>

- <span data-ttu-id="b5beb-107">配置 Unity 应用程序开发</span><span class="sxs-lookup"><span data-stu-id="b5beb-107">Configure Unity for app development</span></span>

- <span data-ttu-id="b5beb-108">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="b5beb-108">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="b5beb-109">准备项目场景</span><span class="sxs-lookup"><span data-stu-id="b5beb-109">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="b5beb-110">说明</span><span class="sxs-lookup"><span data-stu-id="b5beb-110">Instructions</span></span>

1. <span data-ttu-id="b5beb-111">下载并保存混合现实工具包 unity 包，通过单击[此处。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="b5beb-111">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span></span>
2. <span data-ttu-id="b5beb-112">在 Unity 中，单击资产菜单选择"导入包"，然后单击"自定义包"。</span><span class="sxs-lookup"><span data-stu-id="b5beb-112">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="b5beb-114">选择您刚从在步骤 1 中提供的链接下载 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="b5beb-114">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="b5beb-115">导入弹出窗口出现后在 Unity 中，单击导入按钮以开始导入。</span><span class="sxs-lookup"><span data-stu-id="b5beb-115">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="b5beb-116">导入 MRTK 可能需要几分钟。</span><span class="sxs-lookup"><span data-stu-id="b5beb-116">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="b5beb-118">注意：下载的包将文件保存在本地文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b5beb-118">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="b5beb-119">上图没有描绘出将在何处找到程序包。</span><span class="sxs-lookup"><span data-stu-id="b5beb-119">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="b5beb-120">创建新的场景 （这可以通过单击"文件"并选择"新的场景"）。</span><span class="sxs-lookup"><span data-stu-id="b5beb-120">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="b5beb-121">将场景另存为"HLSharedProjectMain。"</span><span class="sxs-lookup"><span data-stu-id="b5beb-121">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="b5beb-122">注意： 可能会收到一个弹出窗口，它看起来类似于下图所示。</span><span class="sxs-lookup"><span data-stu-id="b5beb-122">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="b5beb-123">现在，只需单击"否"。</span><span class="sxs-lookup"><span data-stu-id="b5beb-123">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="b5beb-125">在"混合现实 Toolkit"单击"将添加到场景和配置"。</span><span class="sxs-lookup"><span data-stu-id="b5beb-125">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="b5beb-127">完成后完成后，新的配置文件将出现，让您选择自定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="b5beb-127">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="b5beb-128">单击"复制和自定义"。</span><span class="sxs-lookup"><span data-stu-id="b5beb-128">Click "copy and customize."</span></span>

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. <span data-ttu-id="b5beb-130">向下滚动并取消选中"启用诊断系统"是否你想要隐藏诊断窗口。</span><span class="sxs-lookup"><span data-stu-id="b5beb-130">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="b5beb-131">我们建议保持诊断窗口启用应用程序开发过程来监视性能，并在生产环境或应用程序演示期间禁用它。</span><span class="sxs-lookup"><span data-stu-id="b5beb-131">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span>

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. <span data-ttu-id="b5beb-133">通过按 control + shift + B 或转到文件中打开生成设置 > 生成设置。</span><span class="sxs-lookup"><span data-stu-id="b5beb-133">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="b5beb-134">请注意，该程序当前在"电脑、 Mac 和 Linux 独立"平台设置。</span><span class="sxs-lookup"><span data-stu-id="b5beb-134">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="b5beb-135">HoloLens 2 开发，将平台设置为"通用 Windows 平台。"</span><span class="sxs-lookup"><span data-stu-id="b5beb-135">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="b5beb-136">选择它，然后单击"切换平台"。</span><span class="sxs-lookup"><span data-stu-id="b5beb-136">Select it and click "switch platform."</span></span>

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. <span data-ttu-id="b5beb-138">完成后，单击框，其中显示"添加打开的场景。</span><span class="sxs-lookup"><span data-stu-id="b5beb-138">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="b5beb-139">现在请转到检查器面板，并确保右侧的"支持的虚拟现实"复选框 （如在下图中所示） 已选中。</span><span class="sxs-lookup"><span data-stu-id="b5beb-139">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="b5beb-140">此外确保也选中"场景/HLSharedProjectMain"旁边的复选框，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="b5beb-140">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. <span data-ttu-id="b5beb-142">在"发布设置"部分中检查器面板中向下滚动到"功能"，并确保标记下面的复选框：</span><span class="sxs-lookup"><span data-stu-id="b5beb-142">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>
    - <span data-ttu-id="b5beb-143">internet 客户端</span><span class="sxs-lookup"><span data-stu-id="b5beb-143">internet client</span></span>
       
       - <span data-ttu-id="b5beb-144">internet 客户端服务器</span><span class="sxs-lookup"><span data-stu-id="b5beb-144">internet client server</span></span>
       
       - <span data-ttu-id="b5beb-145">专用网络客户端服务器</span><span class="sxs-lookup"><span data-stu-id="b5beb-145">private network client server</span></span>
   
       - <span data-ttu-id="b5beb-146">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="b5beb-146">camera/webcam</span></span>

       - <span data-ttu-id="b5beb-147">麦克风</span><span class="sxs-lookup"><span data-stu-id="b5beb-147">microphone</span></span>
   
   11. <span data-ttu-id="b5beb-148">导入名为"第 2 课"可以在下载此处自定义包。</span><span class="sxs-lookup"><span data-stu-id="b5beb-148">Import the custom package called "Lesson2" which can be downloaded here.</span></span> <span data-ttu-id="b5beb-149">TODO:提供指向资产包。</span><span class="sxs-lookup"><span data-stu-id="b5beb-149">TODO: Provide link to asset pack.</span></span>
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. <span data-ttu-id="b5beb-151">现在，在项目面板中，转到"预设"文件夹，因为下一步的几个步骤中您将执行向场景的几个预设。</span><span class="sxs-lookup"><span data-stu-id="b5beb-151">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="b5beb-152">在"预设"文件夹中，单击并拖动预设可在层次结构"DebugWindow"。</span><span class="sxs-lookup"><span data-stu-id="b5beb-152">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="b5beb-153">完成后，保存项目 （单击文件，然后保存，或按 control + S）</span><span class="sxs-lookup"><span data-stu-id="b5beb-153">Once finished, save the project (click file, then save, or press control+S)</span></span>
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > <span data-ttu-id="b5beb-155">注意：您可能注意到一个弹出窗口，显示当您单击预设可，询问您 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="b5beb-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="b5beb-156">单击"导入 TMP Essentials"，因为将需要它们。</span><span class="sxs-lookup"><span data-stu-id="b5beb-156">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="b5beb-157">如果此弹出窗口，您可能需要删除预设可从你的层次结构并重新将其拖到层次结构，以避免潜在与文本相关的错误。</span><span class="sxs-lookup"><span data-stu-id="b5beb-157">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="b5beb-159">祝贺</span><span class="sxs-lookup"><span data-stu-id="b5beb-159">Congratulations</span></span>

<span data-ttu-id="b5beb-160">你的 Unity 项目现已准备好 Photon ！</span><span class="sxs-lookup"><span data-stu-id="b5beb-160">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="b5beb-161">在接下来的课程中，我们将在此场景和我们的 Unity 项目针对完整的共享体验为基础进行构建。</span><span class="sxs-lookup"><span data-stu-id="b5beb-161">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="b5beb-162">[下一课：第 3 课 Sharing(Photon)](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="b5beb-162">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

