---
title: 多用户功能教程-2。 正在准备好用于开发的 Unity
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 9d42811157db108baad51eab3f367a06a11b7f7b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701980"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="e2e22-105">2.正在准备好用于开发的 Unity</span><span class="sxs-lookup"><span data-stu-id="e2e22-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="e2e22-106">在本教程中, 我们将了解如何为应用程序开发准备和配置 Unity, 包括导入混合现实工具包、配置生成设置和准备场景。</span><span class="sxs-lookup"><span data-stu-id="e2e22-106">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="e2e22-107">目标</span><span class="sxs-lookup"><span data-stu-id="e2e22-107">Objectives</span></span>

- <span data-ttu-id="e2e22-108">为应用程序开发配置 Unity</span><span class="sxs-lookup"><span data-stu-id="e2e22-108">Configure Unity for application development</span></span>

- <span data-ttu-id="e2e22-109">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="e2e22-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="e2e22-110">准备项目场景</span><span class="sxs-lookup"><span data-stu-id="e2e22-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="e2e22-111">说明</span><span class="sxs-lookup"><span data-stu-id="e2e22-111">Instructions</span></span>

1. <span data-ttu-id="e2e22-112">单击此处下载并保存混合现实工具包 unity 包[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="e2e22-112">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="e2e22-113">在 Unity 中, 单击 "资产" 菜单并选择 "导入包", 然后单击 "自定义包"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-113">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="e2e22-115">选择刚刚从步骤1中提供的链接下载的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="e2e22-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="e2e22-116">导入弹出窗口出现在 Unity 中后, 单击 "导入" 按钮开始导入。</span><span class="sxs-lookup"><span data-stu-id="e2e22-116">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="e2e22-117">导入 MRTK 可能需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="e2e22-117">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="e2e22-119">注意:下载的包位于你保存该文件的本地文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e2e22-119">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="e2e22-120">上面的图像不会描绘出包的位置。</span><span class="sxs-lookup"><span data-stu-id="e2e22-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="e2e22-121">创建新场景。</span><span class="sxs-lookup"><span data-stu-id="e2e22-121">Create a new scene.</span></span> <span data-ttu-id="e2e22-122">可以通过单击 "文件", 然后选择 "新场景" 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="e2e22-122">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="e2e22-123">将场景保存为 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="e2e22-123">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="e2e22-124">注意: 你可能会收到类似于下面的图像的弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="e2e22-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="e2e22-125">现在, 单击 "否"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="e2e22-127">在 "混合现实工具包" 下, 单击 "添加到场景" 并配置。</span><span class="sxs-lookup"><span data-stu-id="e2e22-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="e2e22-129">完成后, 将显示一个新的配置文件, 让你选择自定义配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2e22-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="e2e22-130">单击 "复制和自定义"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-130">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="e2e22-134">如果要隐藏诊断窗口, 请向下滚动并取消选中 "启用诊断系统"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-134">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="e2e22-135">建议在应用程序开发期间保持诊断窗口处于启用状态, 以监视性能, 并在生产或应用程序演示过程中禁用它。</span><span class="sxs-lookup"><span data-stu-id="e2e22-135">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="e2e22-137">按 ctrl + shift + B 打开生成设置, 或转到 "文件 > 生成设置"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-137">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="e2e22-138">请注意, 该程序当前设置在 PC、Mac 和 Linux 独立平台下。</span><span class="sxs-lookup"><span data-stu-id="e2e22-138">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="e2e22-139">对于 HoloLens 2 开发, 请将平台设置为通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="e2e22-139">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="e2e22-140">选择它并单击 "切换平台"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-140">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="e2e22-142">完成后, 单击 "添加打开的场景" 框。</span><span class="sxs-lookup"><span data-stu-id="e2e22-142">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="e2e22-143">现在, 请前往检查器面板, 并确保已选中 "支持的虚拟现实 (如下图中所示)" 右侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="e2e22-143">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="e2e22-144">还应确保选中 "场景/HLSharedProjectMain" 旁边的复选框, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="e2e22-144">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="e2e22-146">在 "检查器" 面板中的 "发布设置" 部分下, 向下滚动到 "功能", 并确保已标记以下复选框:</span><span class="sxs-lookup"><span data-stu-id="e2e22-146">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="e2e22-148">导入名为 SharingAssetCollection 的自定义包, 可在[此处下载。](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="e2e22-148">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="e2e22-150">在 "项目" 面板中, 切换到 Prototyping 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e2e22-150">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="e2e22-151">在接下来的几个步骤中, 将几个 prototyping 实现到场景。</span><span class="sxs-lookup"><span data-stu-id="e2e22-151">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="e2e22-152">在 Prototyping 文件夹中, 单击 "prefab" 并将其拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="e2e22-152">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="e2e22-153">完成后, 单击 "文件", 然后单击 "保存" 或按 Ctrl + S 保存该项目。</span><span class="sxs-lookup"><span data-stu-id="e2e22-153">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="e2e22-155">注意:你可能会注意到, 当你单击 prefab 时, 会显示一个弹出窗口, 询问你有关 TMP Essentials 的信息。</span><span class="sxs-lookup"><span data-stu-id="e2e22-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="e2e22-156">单击 "需要时导入 TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="e2e22-156">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="e2e22-157">如果出现此弹出窗口, 可能需要从层次结构中删除 prefab, 并将其重新拖到层次结构中, 以避免出现与文本相关的潜在错误。</span><span class="sxs-lookup"><span data-stu-id="e2e22-157">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="e2e22-159">祝贺</span><span class="sxs-lookup"><span data-stu-id="e2e22-159">Congratulations</span></span>

<span data-ttu-id="e2e22-160">你的 Unity 项目现在已准备好 Photon。</span><span class="sxs-lookup"><span data-stu-id="e2e22-160">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="e2e22-161">在随后的教程中, 我们将在此场景和 Unity 项目的基础上构建全面的共享体验。</span><span class="sxs-lookup"><span data-stu-id="e2e22-161">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="e2e22-162">[下一教程:3.连接多个用户](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="e2e22-162">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

