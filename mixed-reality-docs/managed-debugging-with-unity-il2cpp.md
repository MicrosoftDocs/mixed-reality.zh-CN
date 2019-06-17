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
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="de769-104">托管调试与 Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="de769-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="de769-105">请按照下列步骤以将托管的调试器附加到 Unity IL2CPP UWP 生成。</span><span class="sxs-lookup"><span data-stu-id="de769-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="de769-106">本指南最初是为 HoloLens 和 HoloLens 2 开发的。</span><span class="sxs-lookup"><span data-stu-id="de769-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="de769-107">絋粄**InternetClientServer**并**PrivateNetworkClientServer** UWP 的发布设置功能在 Unity 中检查。</span><span class="sxs-lookup"><span data-stu-id="de769-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 发布设置功能](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="de769-109">配置 Unity UWP 生成设置：</span><span class="sxs-lookup"><span data-stu-id="de769-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="de769-110">开发内部版本</span><span class="sxs-lookup"><span data-stu-id="de769-110">Development Build</span></span>
    - <span data-ttu-id="de769-111">脚本调试</span><span class="sxs-lookup"><span data-stu-id="de769-111">Script Debugging</span></span>
    - <span data-ttu-id="de769-112">等待托管调试器 （可选）</span><span class="sxs-lookup"><span data-stu-id="de769-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP 生成设置](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="de769-114">在 Unity 中生成。</span><span class="sxs-lookup"><span data-stu-id="de769-114">Build in Unity.</span></span>
1. <span data-ttu-id="de769-115">生成并从 Visual Studio 解决方案部署到你的设备。</span><span class="sxs-lookup"><span data-stu-id="de769-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="de769-116">您应使用生成**调试**或**发行**配置。</span><span class="sxs-lookup"><span data-stu-id="de769-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="de769-117">**Master**配置禁用 Unity 探查器，并能防止最佳调试。</span><span class="sxs-lookup"><span data-stu-id="de769-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="de769-118">（可选） 验证**Internet （客户端和服务器）** 并**专用网络 （客户端和服务器）** 在 Package.appxmanifest 中解决方案的功能列表中。</span><span class="sxs-lookup"><span data-stu-id="de769-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="de769-119">在设备上启动该应用程序。</span><span class="sxs-lookup"><span data-stu-id="de769-119">Start the app on your device.</span></span> <span data-ttu-id="de769-120">请确保你的设备连接到您的电脑与相同的网络。</span><span class="sxs-lookup"><span data-stu-id="de769-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="de769-121">请确保该设备**不是**到您的 PC 通过 USB 连接。</span><span class="sxs-lookup"><span data-stu-id="de769-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="de769-122">转到 Visual Studio 解决方案时，双击在 Unity 中，您可以在其中查看并编辑脚本创建在C#脚本。</span><span class="sxs-lookup"><span data-stu-id="de769-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="de769-123">调试-> 附加 Unity 调试器。</span><span class="sxs-lookup"><span data-stu-id="de769-123">Debug -> Attach Unity Debugger.</span></span>

    ![附加 Unity 调试器](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="de769-125">在列表中选择你的设备，然后单击"确定"以将附加。</span><span class="sxs-lookup"><span data-stu-id="de769-125">Select your device in the list and click "OK" to attach.</span></span>

    ![设备列表](images/il2cpp-debugging-machines.png)
