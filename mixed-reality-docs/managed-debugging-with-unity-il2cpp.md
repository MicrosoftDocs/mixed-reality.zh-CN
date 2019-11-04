---
title: 通过 Unity IL2CPP 进行托管调试
description: 本文介绍如何在 Unity IL2CPP UWP 项目上运行托管调试器。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity，visual studio，调试，il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439628"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="ce32f-104">通过 Unity IL2CPP 进行托管调试</span><span class="sxs-lookup"><span data-stu-id="ce32f-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="ce32f-105">按照以下步骤将托管调试器附加到 Unity IL2CPP UWP 生成。</span><span class="sxs-lookup"><span data-stu-id="ce32f-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="ce32f-106">本指南最初为 HoloLens 和 HoloLens 2 开发。</span><span class="sxs-lookup"><span data-stu-id="ce32f-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="ce32f-107">需要在支持[多播](https://en.wikipedia.org/wiki/Multicast)的网络上使用。</span><span class="sxs-lookup"><span data-stu-id="ce32f-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="ce32f-108">确保**InternetClientServer**和**PRIVATENETWORKCLIENTSERVER**已在 UWP 发布设置功能下的 Unity 中签入。</span><span class="sxs-lookup"><span data-stu-id="ce32f-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 发布设置功能](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="ce32f-110">配置 Unity UWP 生成设置：</span><span class="sxs-lookup"><span data-stu-id="ce32f-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="ce32f-111">开发版本</span><span class="sxs-lookup"><span data-stu-id="ce32f-111">Development Build</span></span>
    - <span data-ttu-id="ce32f-112">脚本调试</span><span class="sxs-lookup"><span data-stu-id="ce32f-112">Script Debugging</span></span>
    - <span data-ttu-id="ce32f-113">等待托管调试器（可选）</span><span class="sxs-lookup"><span data-stu-id="ce32f-113">Wait for Managed Debugger (optional)</span></span>

    ![UWP 生成设置](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="ce32f-115">在 Unity 中构建。</span><span class="sxs-lookup"><span data-stu-id="ce32f-115">Build in Unity.</span></span>
1. <span data-ttu-id="ce32f-116">生成 Visual Studio 解决方案并将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="ce32f-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="ce32f-117">你应以 "**调试**" 或 "**发布**" 配置进行构建。</span><span class="sxs-lookup"><span data-stu-id="ce32f-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="ce32f-118">**主**配置将禁用 Unity 探查器，并可防止优化调试。</span><span class="sxs-lookup"><span data-stu-id="ce32f-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="ce32f-119">（可选）在解决方案的 appxmanifest.xml 中的功能列表中验证**Internet （客户端 & 服务器）** 和**专用网络（客户端 & 服务器）** 。</span><span class="sxs-lookup"><span data-stu-id="ce32f-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="ce32f-120">在设备上启动应用。</span><span class="sxs-lookup"><span data-stu-id="ce32f-120">Start the app on your device.</span></span> <span data-ttu-id="ce32f-121">确保你的设备已连接到与你的电脑相同的网络。</span><span class="sxs-lookup"><span data-stu-id="ce32f-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="ce32f-122">请确保设备**未**通过 USB 连接到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="ce32f-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="ce32f-123">在您双击 Unity 中的脚本时，请跳到创建的 Visual Studio 解决方案，您可以在其中查看和编辑C#脚本。</span><span class="sxs-lookup"><span data-stu-id="ce32f-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="ce32f-124">调试-> 附加 Unity 调试器。</span><span class="sxs-lookup"><span data-stu-id="ce32f-124">Debug -> Attach Unity Debugger.</span></span>

    ![附加 Unity 调试器](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="ce32f-126">在列表中选择你的设备，然后单击 "确定" 以附加。</span><span class="sxs-lookup"><span data-stu-id="ce32f-126">Select your device in the list and click "OK" to attach.</span></span>

    ![设备列表](images/il2cpp-debugging-machines.png)