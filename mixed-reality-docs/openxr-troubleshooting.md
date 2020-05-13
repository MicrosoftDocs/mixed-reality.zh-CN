---
title: OpenXR 故障排除
description: 解决 OpenXR 应用程序中的问题。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，故障排除
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228002"
---
# <a name="openxr-troubleshooting"></a>OpenXR 故障排除

下面是使用 Windows Mixed Reality OpenXR 运行时开发 OpenXR 应用时的一些故障排除提示。  如果你有关于<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a>或<a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。

>[!NOTE]
>当前 Windows Mixed Reality OpenXR 运行时中有一些已知问题。  此时，你应该为 x64 生成桌面 OpenXR 应用。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 应用未启动 Windows Mixed Reality

如果 OpenXR 应用在运行时未启动 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。  请务必遵循上述说明，了解如何[开始 OpenXR For Windows Mixed Reality 耳机](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets)，使运行时处于活动状态。

你还可以运行[Windows Mixed Reality OpenXR 开发人员工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)以获取有关系统上 Windows Mixed Reality OpenXR 运行时状态的其他故障排除帮助。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>混合现实门户未显示 "设置 OpenXR" 菜单项

请确保至少运行 Windows 10 十月2018更新（1809）。  如果使用的是早期版本的 Windows 10，则可以使用[windows 10 更新助手](https://www.microsoft.com//software-download/windows10)升级到2019更新（1903）。

如果你的混合现实门户应用的版本较旧，"设置 OpenXR" 菜单项可能不可用。  检查[混合现实门户应用更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)以确保具有最新版本。

请注意，如果已安装并激活 Windows Mixed Reality OpenXR 运行时，则不会显示 "设置 OpenXR" 菜单项。  可以安装[Windows Mixed Reality OpenXR 开发人员工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)来确定系统上 OpenXR 运行时的当前状态。