---
title: HoloLens 上的帐户
description: 如何设置和管理 HoloLens 上的用户帐户。
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 用户、 帐户、 aad、 adfs、 microsoft 帐户、 msa、 凭据
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591745"
---
# <a name="accounts-on-hololens"></a>HoloLens 上的帐户

安装过程中初始 HoloLens，要求用户使用他们想要在设备上使用的帐户登录。 此帐户可以是一个使用者 Microsoft 帐户或企业帐户已配置 Azure Active Directory (AAD) 或 Active Directory 联合身份验证服务 (ADFS) 中。

用户可以使用到的设备上登录到此帐户在安装过程中创建用户配置文件登录，并对其数据将存储的所有应用。 此相同帐户还为边缘或通过 Windows 帐户管理器 Api 的 Skype 等的应用提供单一登录。

此外，登录到企业或组织帐户在设备上的，它还可应用移动设备管理 (MDM) 策略，如果配置的 IT 管理员联系。

当在设备重新启动或从待机状态恢复时，使用此帐户的凭据以重新登录。 如果在设置中启用了强制实施显式单一登录选项，用户将需要再次键入其凭据。 在接收和应用 OS 更新后重启设备，只要显式单一登录需要。

## <a name="multi-user-support"></a>多用户支持

>[!NOTE]
>多用户支持需要商业套件，因为这是[Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)功能。

从开始[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)，HoloLens 支持从相同的 AAD 租户内的多个用户。 若要使用此选项必须设置最初具有属于你组织的帐户的设备。 随后，来自同一个租户的其他用户将能够登录到该设备从登录屏幕或通过点击开始面板中的用户磁贴可注销现有用户。 

在设备上安装的应用将可供所有其他用户，但各自有自己的应用程序数据和首选项。 删除应用程序还会删除它对于其他所有用户但。 

您可以删除设备以回收空间，通过转到设置中的设备用户 > 帐户 > 其他人。 这将还的所有其他用户的应用程序数据从设备中删除。 

## <a name="linked-accounts"></a>链接的帐户

在单个设备帐户中，用户可以链接在应用程序 （例如存储） 中更轻松地访问其他 web 帐户凭据或要合并个人和工作资源，类似于 Windows 的桌面版本的访问权限。 登录到这种方式中的其他帐户不会不单独的设备，如图像上创建的用户数据或下载。 后一个帐户具有已连接到设备时，可以进行应用程序使用它与你的权限来减少无需单独登录到每个应用。

## <a name="using-single-sign-on-within-an-app"></a>使用应用内的单一登录

作为应用开发人员，您可以利用已连接的标识对与 HoloLens [Windows 帐户管理器 Api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)，就像其他 Windows 设备上一样。 提供了这些 Api 一些代码示例[此处](http://go.microsoft.com/fwlink/p/?LinkId=620621)。

例如发出请求的用户可能会发生任何帐户中断许可的帐户信息，当应用程序请求的身份验证令牌时，必须处理双因素身份验证等。

如果您的应用程序要求之前尚未链接将特定的帐户类型，您的应用程序可以让系统提示用户添加一个。 这会触发帐户设置窗格为您的应用程序的子模式启动。 对于 2D 应用程序，此窗口会呈现直接通过中心的应用程序和 Unity 应用，这将简要需要从全息版应用中注销用户，以便可以呈现此子窗口。 描述命令和此窗格上的操作的自定义[此处](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)。

## <a name="enterprise-and-other-authentication"></a>企业和其他身份验证

如果你的应用程序使用的其他类型的身份验证，则可以使用 NTLM、 Basic 或 Kerberos，如[Windows 凭据 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx)收集、 处理和存储用户的凭据。 收集这些凭据的用户体验非常类似于其他云驱动帐户中断并将显示为 2D 应用顶部的子应用程序或暂时挂起的 Unity 应用要显示 UI。

## <a name="deprecated-apis"></a>已弃用的 Api

在从桌面 HoloLens 上进行开发的一个区别在于[OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API 不完全支持。 尽管它将返回一个令牌，主帐户处于良好支撑会中断如上文所述的那些不会显示任何 UI 对于用户，并且将无法正确进行身份验证帐户。

