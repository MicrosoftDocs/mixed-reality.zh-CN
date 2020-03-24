---
title: 多用户功能教程 - 1. 设置 Photon Unity Networking
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031333"
---
# <a name="1-setting-up-photon-unity-networking"></a>1.设置 Photon Unity Networking

## <a name="overview"></a>概述

本教程介绍如何通过将 Photon Unity Networking (PUN) 导入到 Unity 项目来准备创建共享体验。 Photon 是可供混合现实开发人员用来创建共享体验的多个网络选项之一。 本教程将介绍如何创建 Photon 帐户、导入 Photon，以及创建可选的本地服务器

## <a name="objectives"></a>目标

* 了解如何创建 Photon 帐户
* 了解如何查找和导入 Photon Unity Networking
* 设置本地 Photon 服务器

## <a name="prerequisites"></a>必备条件

>[!TIP]
>如果你尚未完成[入门教程](mrlearning-base.md)和 [Azure 空间定位点入门](mrlearning-asa-ch1.md)教程系列，我们建议先完成这些教程。

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* 一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备

>[!IMPORTANT]
> 建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="setting-up-photon"></a>设置 Photon

1. 设置一个 [Photon](https://dashboard.photonengine.com//Account/SignUp) 帐户。 单击[此链接](https://dashboard.photonengine.com//Account/SignUp)导航到“Photon 注册”页。 按照注册页上的说明创建帐户。

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 单击“创建新应用”按钮创建应用程序 ID。

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 在“Photon 类型”下的下拉菜单中选择“Photon PUN”。 然后为 PUN 指定名称。 本示例已将其命名为 HoloLensPhotonProject。 完成后，单击“创建”按钮。

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 返回到应用程序页面，此时应会看到下图所示的内容。 单击应用程序 ID 并复制此 ID。 将其粘贴到可以轻松访问的位置。  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 创建新的 Unity 项目，并将其命名为 HLSharingProject。 有关如何创建新 Unity 项目的说明，请参阅[基础模块的“创建 Unity 项目”部分](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 

6. 加载项目后，单击“资产存储”选项卡，如下图所示。 然后，在下图中突出显示的搜索框中键入 PUN，并从搜索结果中选择“Photon PUN 2 - 免费”资产。

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 按“下载”和“导入”按钮下载并导入此资产。

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon 完成导入过程后，将显示“PUN 向导”。 将步骤 4 中获取的应用程序 ID（应已复制到剪贴板）粘贴到“应用 ID”框中，然后按“设置项目”按钮。

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. 成功添加应用 ID 后，导航到“资产”中的“Photon”->“PhotonUnityNetworking”>“资源”->“PhotonServerSettings”。 选择“使用名称服务器”选项，并将固定区域设置为“美国”或你所在的 Photon 服务区域。

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>祝贺

现已成功创建了 Photon 帐户，设置了本地 Photon 服务器，并将 PUN 导入到了 Unity。 下一步是设置项目并允许与其他用户建立连接，使多个用户可以看到你的工作。

[下一教程：2.让 Unity 为开发做好准备](mrlearning-sharing(photon)-ch2.md)
