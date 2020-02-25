---
title: 多用户功能教程-2。 正在准备好用于开发的 Unity
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 2bcec7e70949186c6e711120c36ee8649c006ec7
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553827"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="dd609-105">2. 获取 Unity 以便开发</span><span class="sxs-lookup"><span data-stu-id="dd609-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="dd609-106">在本教程中，你将了解如何为应用程序开发准备和配置 Unity，包括导入混合现实工具包、配置生成设置和准备场景。</span><span class="sxs-lookup"><span data-stu-id="dd609-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="dd609-107">目标</span><span class="sxs-lookup"><span data-stu-id="dd609-107">Objectives</span></span>

* <span data-ttu-id="dd609-108">为应用程序开发配置 Unity</span><span class="sxs-lookup"><span data-stu-id="dd609-108">Configure Unity for application development</span></span>
* <span data-ttu-id="dd609-109">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="dd609-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="dd609-110">准备项目场景</span><span class="sxs-lookup"><span data-stu-id="dd609-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="dd609-111">说明</span><span class="sxs-lookup"><span data-stu-id="dd609-111">Instructions</span></span>

1. <span data-ttu-id="dd609-112">单击此处下载并保存混合现实工具包 Foundation unity 包[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="dd609-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="dd609-113">在 Unity 中，单击 "资产" 菜单并选择 "导入包"，然后单击 "自定义包"。</span><span class="sxs-lookup"><span data-stu-id="dd609-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="dd609-115">选择刚刚从步骤1中提供的链接下载的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="dd609-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="dd609-116">导入弹出窗口出现在 Unity 中后，单击 "导入" 按钮以开始导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="dd609-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="dd609-117">这可能需要几分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="dd609-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="dd609-119">下载的包位于你的本地文件夹中，你在该文件夹中保存了该文件。</span><span class="sxs-lookup"><span data-stu-id="dd609-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="dd609-120">上面的图像不会描绘出包的位置。</span><span class="sxs-lookup"><span data-stu-id="dd609-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="dd609-121">在导入包后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="dd609-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="dd609-122">如果未打开，请在 Unity 菜单中选择 "混合现实工具包" > 实用程序 > 配置 Unity 项目 "。</span><span class="sxs-lookup"><span data-stu-id="dd609-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="dd609-123">在 "MRTK 项目配置器" 窗口中，展开 "修改配置" 部分，取消选中 "启用 MSBuild for Unity" 复选框，确保选中所有其他选项，然后单击 "应用" 按钮以应用设置。</span><span class="sxs-lookup"><span data-stu-id="dd609-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="dd609-125">MSBuild for Unity 可能不支持你将使用的所有 SDK，在启用它后再禁用它可能比较困难。</span><span class="sxs-lookup"><span data-stu-id="dd609-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="dd609-126">因此，强烈建议不要启用 MSBuild for Unity。</span><span class="sxs-lookup"><span data-stu-id="dd609-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="dd609-127">创建新场景。</span><span class="sxs-lookup"><span data-stu-id="dd609-127">Create a new scene.</span></span> <span data-ttu-id="dd609-128">可以通过单击 "文件" 并选择 "新建场景" 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="dd609-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="dd609-129">将其保存为 HLSharedProjectMain。</span><span class="sxs-lookup"><span data-stu-id="dd609-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="dd609-130">在 "混合现实工具包" 下，单击 "添加到场景" 并配置。</span><span class="sxs-lookup"><span data-stu-id="dd609-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="dd609-132">完成后，从层次结构中选择混合现实工具包（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="dd609-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="dd609-133">在 "检查器" 面板中，将 MRTK 配置文件更改为 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="dd609-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="dd609-135">从层次结构中选择混合现实工具包（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="dd609-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="dd609-136">在 "检查器" 面板中，查找混合现实工具包脚本并按下图所示的 "复制 & 自定义" 按钮。</span><span class="sxs-lookup"><span data-stu-id="dd609-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="dd609-137">此时将显示一个 pop，并在弹出菜单中选择 "克隆" 选项。</span><span class="sxs-lookup"><span data-stu-id="dd609-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="dd609-140">如果要隐藏诊断窗口，请向下滚动并取消选中 "启用诊断系统"。</span><span class="sxs-lookup"><span data-stu-id="dd609-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="dd609-141">建议在应用程序开发过程中保持诊断窗口处于启用状态，以监视性能，然后在生产或应用程序演示过程中禁用它。</span><span class="sxs-lookup"><span data-stu-id="dd609-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="dd609-143">按 ctrl + shift + B 打开生成设置，或转到 "文件 > 生成设置"。</span><span class="sxs-lookup"><span data-stu-id="dd609-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="dd609-144">请注意，该程序当前设置在 PC、Mac 和 Linux 独立平台下。</span><span class="sxs-lookup"><span data-stu-id="dd609-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="dd609-145">对于 HoloLens 2 开发，请将平台设置为通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="dd609-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="dd609-146">选择它并单击 "切换平台"。</span><span class="sxs-lookup"><span data-stu-id="dd609-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="dd609-148">完成后，单击名为 "添加打开场景" 的框。</span><span class="sxs-lookup"><span data-stu-id="dd609-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="dd609-149">现在，请前往检查器面板，确保选中 "支持的虚拟现实（如下图中所示）" 右侧的复选框。</span><span class="sxs-lookup"><span data-stu-id="dd609-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="dd609-150">还要确保还检查了 "场景/HLSharedProjectMain" 旁边的复选框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dd609-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="dd609-152">在 "检查器" 面板中的 "发布设置" 部分下，向下滚动到 "功能" 并确保以下复选框已标记：</span><span class="sxs-lookup"><span data-stu-id="dd609-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="dd609-154">导入列出的自定义包：</span><span class="sxs-lookup"><span data-stu-id="dd609-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="dd609-155">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) （版本2.1.1）</span><span class="sxs-lookup"><span data-stu-id="dd609-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="dd609-156">MRTK.HoloLens2. GettingStarted. 2.3.0.2. unitypackage</span><span class="sxs-lookup"><span data-stu-id="dd609-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="dd609-157">MRTK.HoloLens2. AzureSpatialAnchors. 2.3.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="dd609-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="dd609-158">MRTK.HoloLens2. MultiUserCapabilities. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="dd609-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="dd609-159">有关如何为 Azure 空间锚定配置 Unity 项目的提醒，请参阅 azure 空间[锚定入门教程，](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)其中包含[Azure 空间锚定](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)系列教程系列。</span><span class="sxs-lookup"><span data-stu-id="dd609-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="dd609-160">在 "项目" 面板中，切换到 Prototyping 文件夹。</span><span class="sxs-lookup"><span data-stu-id="dd609-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="dd609-161">在下面的步骤中，你将在场景中实施几个 prototyping。</span><span class="sxs-lookup"><span data-stu-id="dd609-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="dd609-162">在 Prototyping 文件夹中，单击 "prefab" 并将其拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="dd609-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="dd609-163">完成后，单击 "文件"，然后单击 "保存" 或按 Ctrl + S 保存该项目。</span><span class="sxs-lookup"><span data-stu-id="dd609-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="dd609-165">你可能会注意到，当你单击 prefab 时，会显示一个弹出窗口，询问你有关 TMP Essentials 的信息。</span><span class="sxs-lookup"><span data-stu-id="dd609-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="dd609-166">单击 "需要时导入 TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="dd609-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="dd609-167">如果出现此弹出窗口，可能需要从层次结构中删除 prefab，并将其重新拖到层次结构中，以避免出现与文本相关的潜在错误。</span><span class="sxs-lookup"><span data-stu-id="dd609-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="dd609-169">祝贺你</span><span class="sxs-lookup"><span data-stu-id="dd609-169">Congratulations</span></span>

<span data-ttu-id="dd609-170">你的 Unity 项目现在已准备好 Photon。</span><span class="sxs-lookup"><span data-stu-id="dd609-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="dd609-171">在随后的教程中，我们将在此场景和 Unity 项目的基础上构建全面的共享体验。</span><span class="sxs-lookup"><span data-stu-id="dd609-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="dd609-172">[下一教程： 3. 连接多个用户](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="dd609-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
