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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="3d97a-104">OpenXR 故障排除</span><span class="sxs-lookup"><span data-stu-id="3d97a-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="3d97a-105">下面是使用 Windows Mixed Reality OpenXR 运行时开发 OpenXR 应用时的一些故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="3d97a-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="3d97a-106">如果你有关于<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a>或<a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。</span><span class="sxs-lookup"><span data-stu-id="3d97a-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="3d97a-107">当前 Windows Mixed Reality OpenXR 运行时中有一些已知问题。</span><span class="sxs-lookup"><span data-stu-id="3d97a-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="3d97a-108">此时，你应该为 x64 生成桌面 OpenXR 应用。</span><span class="sxs-lookup"><span data-stu-id="3d97a-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="3d97a-109">OpenXR 应用未启动 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3d97a-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="3d97a-110">如果 OpenXR 应用在运行时未启动 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。</span><span class="sxs-lookup"><span data-stu-id="3d97a-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="3d97a-111">请务必遵循上述说明，了解如何[开始 OpenXR For Windows Mixed Reality 耳机](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets)，使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="3d97a-111">Be sure to follow the instructions above for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="3d97a-112">你还可以运行[Windows Mixed Reality OpenXR 开发人员工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)以获取有关系统上 Windows Mixed Reality OpenXR 运行时状态的其他故障排除帮助。</span><span class="sxs-lookup"><span data-stu-id="3d97a-112">You can also run the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a><span data-ttu-id="3d97a-113">混合现实门户未显示 "设置 OpenXR" 菜单项</span><span class="sxs-lookup"><span data-stu-id="3d97a-113">Mixed Reality Portal not showing "Set up OpenXR" menu item</span></span>

<span data-ttu-id="3d97a-114">请确保至少运行 Windows 10 十月2018更新（1809）。</span><span class="sxs-lookup"><span data-stu-id="3d97a-114">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="3d97a-115">如果使用的是早期版本的 Windows 10，则可以使用[windows 10 更新助手](https://www.microsoft.com//software-download/windows10)升级到2019更新（1903）。</span><span class="sxs-lookup"><span data-stu-id="3d97a-115">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10).</span></span>

<span data-ttu-id="3d97a-116">如果你的混合现实门户应用的版本较旧，"设置 OpenXR" 菜单项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="3d97a-116">The "Set up OpenXR" menu item may not be available if you have an older version of the Mixed Reality Portal app.</span></span>  <span data-ttu-id="3d97a-117">检查[混合现实门户应用更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)以确保具有最新版本。</span><span class="sxs-lookup"><span data-stu-id="3d97a-117">Check for a [Mixed Reality Portal app update](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) to ensure you have the latest version.</span></span>

<span data-ttu-id="3d97a-118">请注意，如果已安装并激活 Windows Mixed Reality OpenXR 运行时，则不会显示 "设置 OpenXR" 菜单项。</span><span class="sxs-lookup"><span data-stu-id="3d97a-118">Note that the "Set up OpenXR" menu item will not show up if the Windows Mixed Reality OpenXR Runtime is already installed and active.</span></span>  <span data-ttu-id="3d97a-119">可以安装[Windows Mixed Reality OpenXR 开发人员工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)来确定系统上 OpenXR 运行时的当前状态。</span><span class="sxs-lookup"><span data-stu-id="3d97a-119">You can install the [Windows Mixed Reality OpenXR Developer Tools](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) to determine the current status of the OpenXR runtime on your system.</span></span>