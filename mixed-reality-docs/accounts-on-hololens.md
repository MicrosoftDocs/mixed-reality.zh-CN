---
title: HoloLens 帐户
description: 如何在 HoloLens 上设置和管理用户帐户。
author: tmlyon
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，用户，帐户，aad，adfs，microsoft 帐户，msa，凭据
ms.openlocfilehash: 5579cf53948b8bdbd4b41973dde7b8fc70a5aa31
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437082"
---
# <a name="accounts-on-hololens"></a>HoloLens 帐户

初次安装 HoloLens 期间，用户需要使用他们要在设备上使用的帐户登录。 此帐户可以是使用者 Microsoft 帐户或已在 Azure Active Directory （AAD）或 Active Directory 联合身份验证服务（ADFS）中配置的企业帐户。

在安装过程中登录此帐户将在设备上创建一个用户配置文件，用户可以使用该配置文件登录，并且所有应用程序都将在该设备上存储其数据。 此同一帐户还通过 Windows 帐户管理器 Api 为应用（如 Edge 或 Skype）提供单一登录。

此外，在设备上登录到企业或组织帐户时，它还可能应用移动设备管理（MDM）策略（如果你的 IT 管理员已配置）。

当设备重新启动或从待机状态恢复时，将使用此帐户的凭据重新登录。 如果在 "设置" 中启用了强制显式登录的选项，则该用户将需要再次键入其凭据。 如果设备在接收和应用 OS 更新后重新启动，则需要显式登录。

## <a name="multi-user-support"></a>多用户支持

>[!NOTE]
>多用户支持需要商用套件，因为这是一项[Windows 全息](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)版功能。

从[Windows 10 2018 年4月的更新](release-notes-april-2018.md)开始，HoloLens 支持同一 AAD 租户中的多个用户。 若要使用此设置，你必须首先使用属于你的组织的帐户设置设备。 随后，同一租户中的其他用户可以通过登录屏幕登录到该设备，或通过点击 "开始" 面板上的 "用户" 磁贴来注销现有用户。 

设备上安装的应用程序将可供所有其他用户使用，但每个应用程序都有自己的应用程序数据和首选项。 不过，删除应用程序时也会将其删除。 

可以通过转到 "设置" > 帐户 > 其他人 "，从设备中删除设备用户以回收空间。 这也会从设备中删除所有其他用户的应用数据。 

## <a name="linked-accounts"></a>链接的帐户

在单个设备帐户内，用户可以链接更多的 web 帐户凭据，以使应用中的访问更加轻松（例如应用商店）或合并对个人和工作资源的访问权限，这与 Windows 的桌面版本类似。 以这种方式登录到其他帐户不会分离在设备上创建的用户数据，如映像或下载。 一旦帐户已连接到设备，应用就可以将其与你的权限结合使用，以减少需要单独登录到每个应用的权限。

## <a name="using-single-sign-on-within-an-app"></a>在应用中使用单一登录

作为应用开发人员，你可以利用使用[Windows 帐户管理器 api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)在 HoloLens 上建立连接的标识，就像在其他 Windows 设备上一样。 [此处](https://go.microsoft.com/fwlink/p/?LinkId=620621)提供了这些 api 的一些代码示例。

当应用请求身份验证令牌时，必须处理任何可能发生的帐户中断，如请求用户同意帐户信息、双因素身份验证等。

如果你的应用程序需要以前未链接的特定帐户类型，你的应用程序可以要求系统提示用户添加一个。 这会触发 "帐户设置" 窗格作为应用的模式子级启动。 对于2D 应用程序，此窗口将直接呈现在应用的中心，而对于 Unity 应用，这会将用户从全息应用中弹出，以便能够呈现此子窗口。 [此处](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)描述了此窗格上的自定义命令和操作。

## <a name="enterprise-and-other-authentication"></a>企业和其他身份验证

如果你的应用程序使用其他类型的身份验证，例如 NTLM、Basic 或 Kerberos，则可以使用[Windows 凭据 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx)来收集、处理和存储用户凭据。 收集这些凭据的用户体验非常类似于其他云驱动的帐户中断，它将在2D 应用程序的基础上显示为子应用，或者只是暂时挂起 Unity 应用以显示 UI。

## <a name="deprecated-apis"></a>弃用的 Api

从桌面开发 HoloLens 的一个区别是不完全支持[OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API。 尽管主帐户在良好的情况下会返回令牌，但如下所述的中断将不会显示用户的任何 UI，并且无法正确地对帐户进行身份验证。

