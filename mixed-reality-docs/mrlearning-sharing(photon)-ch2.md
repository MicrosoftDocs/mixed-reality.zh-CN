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
# <a name="2-getting-unity-ready-for-development"></a>2.让 Unity 为开发做好准备

本教程介绍如何为应用程序开发准备和配置 Unity，包括导入混合现实工具包、配置生成设置和准备场景。

## <a name="objectives"></a>目标

* 为应用程序开发配置 Unity
* 导入混合现实工具包
* 准备项目场景

## <a name="instructions"></a>说明

1. 单击[此处](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)下载 Mixed Reality Toolkit Foundation Unity 包并将其保存。

2. 在 Unity 中，单击“资产”菜单并选择“导入包”，然后单击“自定义包”。

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 选择刚刚从步骤 1 中提供的链接下载的 Unity 包。 Unity 中出现“导入”弹出窗口后，单击“导入”按钮开始导入 MRTK。 此过程可能需要几分钟时间。

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >下载的包位于文件所保存到的本地文件夹中。 上图未展示该包的保存位置。

    在导入包后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请在 Unity 菜单中选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”将其打开。

    在“MRTK 项目配置器”窗口中，展开“修改配置”部分，取消选中“启用 MSBuild for Unity”复选框，确保勾选所有其他选项，然后单击“应用”按钮以应用设置。

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > MSBuild for Unity 可能不支持你将使用的所有 SDK，在启用它后再禁用它可能比较困难。 因此，强烈建议不要启用 MSBuild for Unity。
    
4. 创建新场景。 可以单击“文件”并选择“新建场景”来完成此操作。 将场景保存为 HLSharedProjectMain。

5. 在“混合现实工具包”下，单击“添加到场景并进行配置”。

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成该操作后，在层次结构中选择“混合现实工具包(MRTK)”。 在检查器面板中，将 MRTK 配置配置文件更改为 DefaultHoloLens2ConfigurationProfile。

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. 在层次结构中选择“混合现实工具包(MRTK)”。 在检查器面板中，找到“混合现实工具包脚本”并按“复制和自定义”按钮，如下图所示。  随后会显示一个弹出窗口。请在弹出菜单中选择克隆选项。

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. 若要隐藏诊断窗口，请向下滚动并取消选中“启用诊断系统”。 我们建议在应用程序开发期间保持启用诊断窗口以监视性能，并在生产或应用程序演示期间将其禁用。 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. 按 Ctrl+Shift+B 或转到“文件”>“生成设置”打开生成设置。 请注意，该程序当前已在 PC、Mac 和 Linux 独立平台下设置。 对于 HoloLens 2 开发，请将平台设置为“通用 Windows 平台”。 选择此选项并单击“切换平台”。

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. 完成后，单击名为“添加开放场景”的框。 现在请转到“检查器”面板，确保已选中“支持的虚拟现实”右侧的复选框（如下图所示）。 另请确保选中了“scenes/HLSharedProjectMain”旁边的复选框，如下图所示。

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. 在“检查器”面板中的“发布设置”部分下，向下滚动到“功能”并确保已选中以下复选框：

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. 导入列出的自定义包：

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)（版本 2.1.1）
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >有关如何为 Azure 空间定位点配置 Unity 项目的提示，可参阅 [Azure 空间定位点](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)教程系列中的 [Azure 空间定位点入门](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)教程。


13. 在“项目”面板中，转到“预制件”文件夹。 以下步骤将在场景中实现几个预制件。 在“预制件”文件夹中，单击“调试窗口”预制件并将其拖放到层次结构中。 完成后，单击“文件”并选择“保存”，或者按 Ctrl+S 以保存项目。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    单击该预制件时，你可能会发现显示了一个弹出窗口，其中询问是否要导入 TMP 基本信息。 请单击“导入 TMP 基本信息”，因为需要这些信息。 如果出现此弹出窗口，你可能需要从层次结构中删除该预制件，并将其重新拖放到层次结构中，以免出现文本相关的潜在错误。

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>祝贺

Unity 项目现已准备好用于 Photon 开发。 在后面的教程中，我们将基于此场景生成应用程序，而我们的 Unity 项目也会逐渐形成一个完整的共享体验。

[下一教程：3.连接多个用户](mrlearning-sharing(photon)-ch3.md)
