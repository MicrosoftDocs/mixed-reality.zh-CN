---
title: 建立与全息远程处理的安全连接
description: 本页说明如何在使用全息远程处理时建立安全的加密连接。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: ac1170cb3e6d681fc164c3f4cee14da6ab6eb90b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092475"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>建立与全息远程处理的安全连接

>[!IMPORTANT]
>本指南特定于 HoloLens 2 上的全息远程处理。

本页说明如何在使用全息远程处理时建立安全的加密连接。

当通过不安全的网络（如开放 WiFi 或 internet）将内容流式传输到 HoloLens 2 时，强烈建议使用加密连接。

>[!IMPORTANT]
>即使使用受信任的本地 WiFi，也应考虑使用加密连接。

若要使用加密的连接，则需要同时实现[自定义播放器](holographic-remoting-create-player.md)和[自定义远程应用](holographic-remoting-create-host.md)。

加密是通过使用基础平台 TLS 实现实现的。

## <a name="basics-of-an-encrypted-connection"></a>加密连接的基本信息

需要实现以下对象才能允许证书交换。

>[!TIP]
>可以使用C++/WinRT. 轻松实现 WinRT 接口 [作者 api with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)一章对此进行了详细介绍。

>[!IMPORTANT]
>NuGet 包中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含有关与安全连接相关的 API 的详细文档。

1) 需要实现 ```ICertificate``` 接口的证书对象。

    * 通过 ```GetCertificatePfx``` 方法返回 pfx 证书的二进制内容。 与 .pfx 文件的二进制内容相同。
    * 通过 ```GetSubjectName```返回证书使用者名称。
    * 通过 ```GetPfxPassword```返回 pfx 密码。 为未受保护的 pfx 返回空字符串。

2) 一个证书提供程序，它实现 ```ICertificateProvider``` 接口，该接口在系统通过 ```GetCertificate``` 方法时提供证书。

3) 用于实现 ```ICertificateValidator``` 接口的证书验证程序。 它的任务是验证传入的证书。
    * 当基础平台应验证传入的证书链时，```PerformSystemValidation``` 方法应返回 ```true```，```false``` 否则返回。
    * ```ValidateCertificate``` 由客户端上下文调用以请求验证证书。 此方法接受证书链（第一个证书为 "使用者证书"）、与之建立连接的服务器的名称，以及是否应强制执行吊销检查。 如果已请求基础系统验证，则将提供系统验证结果。 若要继续处理 ```CertificateValidated``` 与相应的结果或 ```Cancel```，需要对传递的 ```ICertificateValidationCallback```调用取消验证。

而且，若要允许交换安全令牌，需要实现以下对象。

1) 实现 ```IAuthenticationProvider``` 接口的身份验证提供程序。 客户端上下文调用其 ```GetToken``` 方法，以请求用于客户端身份验证的令牌。 若要继续 ```TokenReceived``` 提供身份验证令牌并继续连接过程，或者 ```Cancel``` 取消需要在传递的 ```IAuthenticationProviderCallback```上调用的进程。
2) 实现 ```IAuthenticationReceiver``` 接口的身份验证接收器。 它的任务是验证传入令牌。
    * ```GetRealm``` 方法应返回身份验证领域的名称。
    * 服务器网络上下文调用 ```ValidateToken``` 方法来请求验证客户端身份验证令牌。 若要继续，请调用 ```ValidationCompleted``` 以指示验证完成，或 ```Cancel``` 以拒绝客户端连接。 根据传递给 ```ValidationCompleted```的验证结果，将会对客户端连接进行许可或拒绝。 

实现这些对象后 ```ListenSecure``` 需要调用，而不是 ```Listen``` 和 ```ConnectSecure```，而不是在远程上下文和播放机上下文上分别 ```Connect```。 ```ListenSecure``` 要求在 ```Listen```上使用其他证书提供程序和身份验证接收器。 ```ConnectSecure``` 要求对 ```Connect```使用额外的身份验证提供程序和证书验证程序。

## <a name="see-also"></a>另请参阅
* [编写全息远程处理远程应用](holographic-remoting-create-host.md)
* [编写自定义全息远程处理播放器应用程序](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
