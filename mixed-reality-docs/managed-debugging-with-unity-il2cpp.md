---
title: 托管调试与 Unity IL2CPP
description: 这篇文章介绍如何在 Unity IL2CPP UWP 项目上运行托管的调试器。
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: unity 中，visual studio 中，调试 il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148852"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>托管调试与 Unity IL2CPP

请按照下列步骤以将托管的调试器附加到 Unity IL2CPP UWP 生成。 本指南最初是为 HoloLens 和 HoloLens 2 开发的。

1. 絋粄**InternetClientServer**并**PrivateNetworkClientServer** UWP 的发布设置功能在 Unity 中检查。

    ![UWP 发布设置功能](images/il2cpp-debugging-capabilities.png)

1. 配置 Unity UWP 生成设置：
    - 开发内部版本
    - 脚本调试
    - 等待托管调试器 （可选）

    ![UWP 生成设置](images/il2cpp-debugging-build.png)

1. 在 Unity 中生成。
1. 生成并从 Visual Studio 解决方案部署到你的设备。 您应使用生成**调试**或**发行**配置。 **Master**配置禁用 Unity 探查器，并能防止最佳调试。 （可选） 验证**Internet （客户端和服务器）** 并**专用网络 （客户端和服务器）** 在 Package.appxmanifest 中解决方案的功能列表中。
1. 在设备上启动该应用程序。 请确保你的设备连接到您的电脑与相同的网络。
1. 请确保该设备**不是**到您的 PC 通过 USB 连接。
1. 转到 Visual Studio 解决方案时，双击在 Unity 中，您可以在其中查看并编辑脚本创建在C#脚本。
1. 调试-> 附加 Unity 调试器。

    ![附加 Unity 调试器](images/il2cpp-debugging-attach.png)

1. 在列表中选择你的设备，然后单击"确定"以将附加。

    ![设备列表](images/il2cpp-debugging-machines.png)
