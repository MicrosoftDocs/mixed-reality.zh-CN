---
title: 多用户功能教程-2。 正在准备好用于开发的 Unity
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 6840bcc583fe3e42dcaa6f42e71098f4dbe76f4c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334315"
---
# <a name="2-getting-unity-ready-for-development"></a>2. 获取 Unity 以便开发

在本教程中，你将了解如何为应用程序开发准备和配置 Unity，包括导入混合现实工具包、配置生成设置和准备场景。

## <a name="objectives"></a>目标

* 为应用程序开发配置 Unity
* 导入混合现实工具包
* 准备项目场景

## <a name="instructions"></a>说明

1. 单击此处下载并保存混合现实工具包 Foundation unity 包[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. 在 Unity 中，单击 "资产" 菜单并选择 "导入包"，然后单击 "自定义包"。

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 选择刚刚从步骤1中提供的链接下载的 Unity 包。 导入弹出窗口出现在 Unity 中后，单击 "导入" 按钮以开始导入 MRTK。 这可能需要几分钟。

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >下载的包位于你的本地文件夹中，你在该文件夹中保存了该文件。 上面的图像不会描绘出包的位置。

4. 创建新场景。 可以通过单击 "文件" 并选择 "新建场景" 来完成此操作。 将其保存为 HLSharedProjectMain。

    你可能会收到类似于下面的图像的弹出窗口。 现在，单击 "否"。
    ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 在 "混合现实工具包" 下，单击 "添加到场景" 并配置。

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成后，将显示一个新的配置文件，让你选择自定义配置文件。

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. 从层次结构中选择混合现实工具包（MRTK）。 在 "检查器" 面板中，查找混合现实工具包脚本并按下图所示的 "复制 & 自定义" 按钮。  此时将显示一个 pop，并在弹出菜单中选择 "克隆" 选项。

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. 如果要隐藏诊断窗口，请向下滚动并取消选中 "启用诊断系统"。 建议在应用程序开发过程中保持诊断窗口处于启用状态，以监视性能，然后在生产或应用程序演示过程中禁用它。 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. 按 ctrl + shift + B 打开生成设置，或转到 "文件 > 生成设置"。 请注意，该程序当前设置在 PC、Mac 和 Linux 独立平台下。 对于 HoloLens 2 开发，请将平台设置为通用 Windows 平台。 选择它并单击 "切换平台"。

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. 完成后，单击名为 "添加打开场景" 的框。 现在，请前往检查器面板，确保选中 "支持的虚拟现实（如下图中所示）" 右侧的复选框。 还要确保还检查了 "场景/HLSharedProjectMain" 旁边的复选框，如下图所示。

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. 在 "检查器" 面板中的 "发布设置" 部分下，向下滚动到 "功能" 并确保以下复选框已标记：

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. 导入列出的自定义包：

    a. [HoloLens2. GettingStarted. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    b. [HoloLens2. MultiUserCapabilities. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    >如果你已完成[入门教程](mrlearning-base-ch1.md)，则你的计算机上可能会存储名为 HoloLens2 的 unity 包。 _2.1.0.0. unitypackage_ 。 如果是这样，则可以跳过下载上一步中列出的资产。

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. 在 "项目" 面板中，切换到 Prototyping 文件夹。 在下面的步骤中，你将在场景中实施几个 prototyping。 在 Prototyping 文件夹中，单击 "prefab" 并将其拖到层次结构中。 完成后，单击 "文件"，然后单击 "保存" 或按 Ctrl + S 保存该项目。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    你可能会注意到，当你单击 prefab 时，会显示一个弹出窗口，询问你有关 TMP Essentials 的信息。 单击 "需要时导入 TMP Essentials"。 如果出现此弹出窗口，可能需要从层次结构中删除 prefab，并将其重新拖到层次结构中，以避免出现与文本相关的潜在错误。

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>祝贺

你的 Unity 项目现在已准备好 Photon。 在随后的教程中，我们将在此场景和 Unity 项目的基础上构建全面的共享体验。

[下一教程： 3. 连接多个用户](mrlearning-sharing(photon)-ch3.md)
