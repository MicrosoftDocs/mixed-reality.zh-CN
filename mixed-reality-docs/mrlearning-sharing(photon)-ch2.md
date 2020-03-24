---
title: 多用户功能教程 - 2. 让 Unity 为开发做好准备
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031241"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="3b8d5-105">2.让 Unity 为开发做好准备</span><span class="sxs-lookup"><span data-stu-id="3b8d5-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="3b8d5-106">本教程介绍如何为应用程序开发准备和配置 Unity，包括导入混合现实工具包、配置生成设置和准备场景。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="3b8d5-107">目标</span><span class="sxs-lookup"><span data-stu-id="3b8d5-107">Objectives</span></span>

* <span data-ttu-id="3b8d5-108">为应用程序开发配置 Unity</span><span class="sxs-lookup"><span data-stu-id="3b8d5-108">Configure Unity for application development</span></span>
* <span data-ttu-id="3b8d5-109">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="3b8d5-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="3b8d5-110">准备项目场景</span><span class="sxs-lookup"><span data-stu-id="3b8d5-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="3b8d5-111">说明</span><span class="sxs-lookup"><span data-stu-id="3b8d5-111">Instructions</span></span>

1. <span data-ttu-id="3b8d5-112">单击[此处](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)下载 Mixed Reality Toolkit Foundation Unity 包并将其保存。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="3b8d5-113">在 Unity 中，单击“资产”菜单并选择“导入包”，然后单击“自定义包”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="3b8d5-115">选择刚刚从步骤 1 中提供的链接下载的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="3b8d5-116">Unity 中出现“导入”弹出窗口后，单击“导入”按钮开始导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="3b8d5-117">此过程可能需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="3b8d5-119">下载的包位于文件所保存到的本地文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="3b8d5-120">上图未展示该包的保存位置。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="3b8d5-121">在导入包后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="3b8d5-122">如果未显示该窗口，请在 Unity 菜单中选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”将其打开。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="3b8d5-123">在“MRTK 项目配置器”窗口中，展开“修改配置”部分，取消选中“启用 MSBuild for Unity”复选框，确保勾选所有其他选项，然后单击“应用”按钮以应用设置。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="3b8d5-125">MSBuild for Unity 可能不支持你将使用的所有 SDK，在启用它后再禁用它可能比较困难。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="3b8d5-126">因此，强烈建议不要启用 MSBuild for Unity。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="3b8d5-127">创建新场景。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-127">Create a new scene.</span></span> <span data-ttu-id="3b8d5-128">可以单击“文件”并选择“新建场景”来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="3b8d5-129">将场景保存为 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="3b8d5-130">在“混合现实工具包”下，单击“添加到场景并进行配置”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="3b8d5-132">完成该操作后，在层次结构中选择“混合现实工具包(MRTK)”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="3b8d5-133">在检查器面板中，将 MRTK 配置配置文件更改为 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="3b8d5-135">在层次结构中选择“混合现实工具包(MRTK)”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="3b8d5-136">在检查器面板中，找到“混合现实工具包脚本”并按“复制和自定义”按钮，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="3b8d5-137">随后会显示一个弹出窗口。请在弹出菜单中选择克隆选项。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="3b8d5-140">若要隐藏诊断窗口，请向下滚动并取消选中“启用诊断系统”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="3b8d5-141">我们建议在应用程序开发期间保持启用诊断窗口以监视性能，并在生产或应用程序演示期间将其禁用。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="3b8d5-143">按 Ctrl+Shift+B 或转到“文件”>“生成设置”打开生成设置。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="3b8d5-144">请注意，该程序当前已在 PC、Mac 和 Linux 独立平台下设置。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="3b8d5-145">对于 HoloLens 2 开发，请将平台设置为“通用 Windows 平台”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="3b8d5-146">选择此选项并单击“切换平台”。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="3b8d5-148">完成后，单击名为“添加开放场景”的框。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="3b8d5-149">现在请转到“检查器”面板，确保已选中“支持的虚拟现实”右侧的复选框（如下图所示）。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="3b8d5-150">另请确保选中了“scenes/HLSharedProjectMain”旁边的复选框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="3b8d5-152">在“检查器”面板中的“发布设置”部分下，向下滚动到“功能”并确保已选中以下复选框：</span><span class="sxs-lookup"><span data-stu-id="3b8d5-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="3b8d5-154">导入列出的自定义包：</span><span class="sxs-lookup"><span data-stu-id="3b8d5-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="3b8d5-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)（版本 2.1.1）</span><span class="sxs-lookup"><span data-stu-id="3b8d5-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="3b8d5-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="3b8d5-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="3b8d5-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="3b8d5-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="3b8d5-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="3b8d5-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="3b8d5-159">有关如何为 Azure 空间定位点配置 Unity 项目的提示，可参阅 [Azure 空间定位点](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)教程系列中的 [Azure 空间定位点入门](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)教程。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="3b8d5-160">在“项目”面板中，转到“预制件”文件夹。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="3b8d5-161">以下步骤将在场景中实现几个预制件。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="3b8d5-162">在“预制件”文件夹中，单击“调试窗口”预制件并将其拖放到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="3b8d5-163">完成后，单击“文件”并选择“保存”，或者按 Ctrl+S 以保存项目。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="3b8d5-165">单击该预制件时，你可能会发现显示了一个弹出窗口，其中询问是否要导入 TMP 基本信息。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="3b8d5-166">请单击“导入 TMP 基本信息”，因为需要这些信息。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="3b8d5-167">如果出现此弹出窗口，你可能需要从层次结构中删除该预制件，并将其重新拖放到层次结构中，以免出现文本相关的潜在错误。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="3b8d5-169">祝贺</span><span class="sxs-lookup"><span data-stu-id="3b8d5-169">Congratulations</span></span>

<span data-ttu-id="3b8d5-170">Unity 项目现已准备好用于 Photon 开发。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="3b8d5-171">在后面的教程中，我们将基于此场景生成应用程序，而我们的 Unity 项目也会逐渐形成一个完整的共享体验。</span><span class="sxs-lookup"><span data-stu-id="3b8d5-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="3b8d5-172">[下一教程：3.连接多个用户](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="3b8d5-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
