---
title: MR 和 Azure 313-IoT 中心服务
description: 完成本课程，了解如何在运行 Ubuntu 16.4 的虚拟机上实现 Azure IoT 中心服务，然后使用 Microsoft HoloLens 或沉浸式（VR）耳机直观显示邮件数据。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure，混合现实，学院，边缘，iot edge，教程，api，通知，函数，表，hololens，沉浸，vr，iot，虚拟机，ubuntu，python
ms.openlocfilehash: bfb1518869892ed4899019d7b9c504a960e7db3f
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926838"
---
>[!NOTE]
><span data-ttu-id="24c2a-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="24c2a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="24c2a-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="24c2a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="24c2a-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="24c2a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="24c2a-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="24c2a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="24c2a-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="24c2a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="24c2a-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="24c2a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="24c2a-110">MR 和 Azure 313： IoT 中心服务</span><span class="sxs-lookup"><span data-stu-id="24c2a-110">MR and Azure 313: IoT Hub Service</span></span>

![课程结果](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="24c2a-112">在本课程中，你将了解如何在运行 Ubuntu 16.4 操作系统的虚拟机上实现**Azure IoT 中心服务**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="24c2a-113">然后， **azure Function App**将用于从 Ubuntu VM 接收消息，并将结果存储在**Azure 表服务**中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="24c2a-114">然后，你将能够使用 Microsoft HoloLens 或沉浸式（VR）耳机上的**Power BI**查看此数据。</span><span class="sxs-lookup"><span data-stu-id="24c2a-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="24c2a-115">本课程的内容*适用*于 IoT Edge 设备，不过，在本课程中，重点将位于虚拟机环境中，因此不需要访问物理边缘设备。</span><span class="sxs-lookup"><span data-stu-id="24c2a-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="24c2a-116">完成本课程后，你将学习：</span><span class="sxs-lookup"><span data-stu-id="24c2a-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="24c2a-117">将**IoT Edge 模块**部署到表示 IoT 设备的虚拟机（UBUNTU 16 OS）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="24c2a-118">将**Azure 自定义视觉 Tensorflow 模型**添加到 Edge 模块，其中包含用于分析容器中存储的图像的代码。</span><span class="sxs-lookup"><span data-stu-id="24c2a-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="24c2a-119">设置模块以将分析结果消息发送回**IoT 中心服务**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="24c2a-120">使用**azure Function App**将消息存储在**azure 表**中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="24c2a-121">设置**Power BI**以收集存储的消息并创建报表。</span><span class="sxs-lookup"><span data-stu-id="24c2a-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="24c2a-122">在**Power BI**中直观显示 IoT 消息数据。</span><span class="sxs-lookup"><span data-stu-id="24c2a-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="24c2a-123">将使用的服务包括：</span><span class="sxs-lookup"><span data-stu-id="24c2a-123">The Services you will use include:</span></span>

- <span data-ttu-id="24c2a-124">**Azure IoT 中心**是一种 Microsoft Azure 服务，它允许开发人员连接、监视和管理 IoT 资产。</span><span class="sxs-lookup"><span data-stu-id="24c2a-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="24c2a-125">有关详细信息，请访问[ **Azure IoT 中心服务**页](https://azure.microsoft.com/services/iot-hub/)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/services/iot-hub/).</span></span>

- <span data-ttu-id="24c2a-126">**Azure 容器注册表**是一种 Microsoft Azure 服务，它允许开发人员为各种类型的容器存储容器映像。</span><span class="sxs-lookup"><span data-stu-id="24c2a-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="24c2a-127">有关详细信息，请访问[ **Azure 容器注册表服务**页](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/services/container-registry/).</span></span>

- <span data-ttu-id="24c2a-128">**Azure Function App**是一种 Microsoft Azure 服务，它允许开发人员在 Azure 中运行小部分代码 "函数"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="24c2a-129">这提供了一种方法，可将工作委托给云，而不是本地应用程序，这可能有很多好处。</span><span class="sxs-lookup"><span data-stu-id="24c2a-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="24c2a-130">**Azure Functions**支持多种开发语言，包括 C\#、F\#、Node.js、JAVA 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="24c2a-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="24c2a-131">有关详细信息，请访问[ **Azure Functions**页](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="24c2a-132">**Azure 存储：表**是一项 Microsoft Azure 服务，它允许开发人员在云中存储结构化非 SQL 数据，使其在任何位置轻松访问。</span><span class="sxs-lookup"><span data-stu-id="24c2a-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="24c2a-133">此服务的设计良好，可根据需要进行表的发展，因此非常灵活。</span><span class="sxs-lookup"><span data-stu-id="24c2a-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="24c2a-134">有关详细信息，请访问[ **Azure 表**页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="24c2a-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="24c2a-135">本课程将介绍如何设置和使用 IoT 中心服务，然后将设备提供的响应可视化。</span><span class="sxs-lookup"><span data-stu-id="24c2a-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="24c2a-136">您可以将这些概念应用到您可能会构建的自定义 IoT 中心服务设置。</span><span class="sxs-lookup"><span data-stu-id="24c2a-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="24c2a-137">设备支持</span><span class="sxs-lookup"><span data-stu-id="24c2a-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="24c2a-138">摘要</span><span class="sxs-lookup"><span data-stu-id="24c2a-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="24c2a-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="24c2a-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="24c2a-140"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="24c2a-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="24c2a-141">MR 和 Azure 313： IoT 中心服务</span><span class="sxs-lookup"><span data-stu-id="24c2a-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="24c2a-142">✔️</span><span class="sxs-lookup"><span data-stu-id="24c2a-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="24c2a-143">✔️</span><span class="sxs-lookup"><span data-stu-id="24c2a-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="24c2a-144">必备条件</span><span class="sxs-lookup"><span data-stu-id="24c2a-144">Prerequisites</span></span>

<span data-ttu-id="24c2a-145">有关利用混合现实进行开发的最新先决条件，包括 Microsoft HoloLens，请访问[安装工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文。</span><span class="sxs-lookup"><span data-stu-id="24c2a-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="24c2a-146">本教程适用于具有 Python 的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="24c2a-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="24c2a-147">另外，请注意，本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容（2018年7月）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="24c2a-148">您可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的软件内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="24c2a-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="24c2a-149">需要以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="24c2a-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="24c2a-150">Windows 10 秋季创意者更新（或更高版本），**开发人员模式已启用**</span><span class="sxs-lookup"><span data-stu-id="24c2a-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="24c2a-151">你无法在 Windows 10 Home Edition 上使用 Hyper-v 运行虚拟机。</span><span class="sxs-lookup"><span data-stu-id="24c2a-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="24c2a-152">Windows 10 SDK （最新版本）</span><span class="sxs-lookup"><span data-stu-id="24c2a-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="24c2a-153">**已启用 HoloLens、开发人员模式**</span><span class="sxs-lookup"><span data-stu-id="24c2a-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="24c2a-154">Visual Studio 2017.15.4 （仅用于访问 Azure Cloud Explorer）</span><span class="sxs-lookup"><span data-stu-id="24c2a-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="24c2a-155">Azure 和 IoT 中心服务的 Internet 访问。</span><span class="sxs-lookup"><span data-stu-id="24c2a-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="24c2a-156">有关详细信息，请访问[IoT 中心服务页面链接](https://azure.microsoft.com/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="24c2a-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/services/iot-hub/)</span></span>
- <span data-ttu-id="24c2a-157">机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="24c2a-157">A machine learning model.</span></span> <span data-ttu-id="24c2a-158">如果没有现成的可用模型，[可以使用本课程提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="24c2a-159">在 Windows 10 开发计算机上启用**hyper-v**软件。</span><span class="sxs-lookup"><span data-stu-id="24c2a-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="24c2a-160">运行 Ubuntu （16.4 或18.4）的虚拟机，可在开发计算机上运行，也可以使用运行 Linux 的单独计算机（Ubuntu 16.4 或18.4）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="24c2a-161">可以在["开始之前" 一章](#before-you-start)中找到有关如何使用 Hyper-v 在 Windows 上创建虚拟机的详细信息。（ https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine) 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="24c2a-162">开始之前</span><span class="sxs-lookup"><span data-stu-id="24c2a-162">Before you start</span></span>

1. <span data-ttu-id="24c2a-163">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="24c2a-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="24c2a-164">如果需要支持设置 HoloLens，请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="24c2a-165">在开始开发新的 HoloLens 应用程序时，最好执行**校准**和**传感器调整**（有时它可以帮助为每个用户执行这些任务）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="24c2a-166">有关校准的帮助信息，请单击此链接，了解[到 HoloLens 校准文章](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="24c2a-167">有关传感器优化的帮助，请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="24c2a-168">使用**hyper-v**设置**Ubuntu 虚拟机**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="24c2a-169">以下资源将帮助你执行此过程。</span><span class="sxs-lookup"><span data-stu-id="24c2a-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="24c2a-170">首先，请单击以下链接[下载 Ubuntu 16.04.4 LTS （Xenial Xerus） ISO](https://au.releases.ubuntu.com/16.04/)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="24c2a-171">选择**64-BIT PC （AMD64）桌面映像**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="24c2a-172">请确保已在 Windows 10 计算机上启用**hyper-v** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="24c2a-173">你可以访问此链接以获取有关在[Windows 10 上安装和启用 hyper-v](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)的指南。</span><span class="sxs-lookup"><span data-stu-id="24c2a-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="24c2a-174">启动 Hyper-v 并创建新的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="24c2a-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="24c2a-175">可以访问此链接，了解有关[如何使用 hyper-v 创建 VM](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)的分步指导。</span><span class="sxs-lookup"><span data-stu-id="24c2a-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="24c2a-176">当请求 **"从可启动的映像文件安装操作系统"** 时，选择之前下载的**Ubuntu ISO** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24c2a-177">不建议使用**Hyper-v 快速创建**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="24c2a-178">第1章-检索自定义视觉模型</span><span class="sxs-lookup"><span data-stu-id="24c2a-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="24c2a-179">在本课程中，您将有权访问[预建的自定义视觉模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)，用于检测图像中的键盘和鼠标。</span><span class="sxs-lookup"><span data-stu-id="24c2a-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="24c2a-180">如果使用此操作，请转到[第2章](#chapter-2---the-container-registry-service)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="24c2a-181">但是，如果想要使用自己的自定义视觉模型，则可以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="24c2a-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="24c2a-182">在**自定义视觉项目**中转到 "**性能**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="24c2a-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="24c2a-183">您的模型必须使用*精简*域来导出模型。</span><span class="sxs-lookup"><span data-stu-id="24c2a-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="24c2a-184">你可以在项目的设置中更改模型域。</span><span class="sxs-lookup"><span data-stu-id="24c2a-184">You can change your models domain in the settings for your project.</span></span>

    ![性能选项卡](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="24c2a-186">选择要导出的**迭代**，并单击 "**导出**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="24c2a-187">随即出现一个边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="24c2a-187">A blade will appear.</span></span>

    ![导出边栏选项卡](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="24c2a-189">在边栏选项卡中，单击 " **Docker 文件**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-189">In the blade click **Docker File**.</span></span>

    ![选择 docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="24c2a-191">在下拉菜单中单击 " **Linux** "，然后单击 "**下载**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![单击 "下载"](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="24c2a-193">解压缩内容。</span><span class="sxs-lookup"><span data-stu-id="24c2a-193">Unzip the content.</span></span> <span data-ttu-id="24c2a-194">稍后将在本课程中使用它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="24c2a-195">第2章-容器注册表服务</span><span class="sxs-lookup"><span data-stu-id="24c2a-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="24c2a-196">**容器注册表服务**是用于托管容器的存储库。</span><span class="sxs-lookup"><span data-stu-id="24c2a-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="24c2a-197">你将在本课程中构建和使用的**IoT 中心服务**是指**容器注册表服务**，用于获取要在边缘设备中部署的容器。</span><span class="sxs-lookup"><span data-stu-id="24c2a-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="24c2a-198">首先，请[在 Azure 门户](https://portal.azure.com/)中单击此链接，然后用你的凭据登录。</span><span class="sxs-lookup"><span data-stu-id="24c2a-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="24c2a-199">请参阅**创建资源**并查找**容器注册表**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![容器注册表](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="24c2a-201">单击 "**创建**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="24c2a-202">设置服务安装参数：</span><span class="sxs-lookup"><span data-stu-id="24c2a-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="24c2a-203">插入项目的名称，在本示例中，它称为**IoTCRegistry**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="24c2a-204">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="24c2a-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="24c2a-205">资源组提供一种方式来监视、控制访问、预配和管理 Azure 资产集合的计费。</span><span class="sxs-lookup"><span data-stu-id="24c2a-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="24c2a-206">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="24c2a-207">设置服务的位置。</span><span class="sxs-lookup"><span data-stu-id="24c2a-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="24c2a-208">将 "**管理员用户**" 设置为**启用**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="24c2a-209">将**SKU**设置为**基本**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="24c2a-210">单击 "**创建**" 并等待要创建的服务。</span><span class="sxs-lookup"><span data-stu-id="24c2a-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="24c2a-211">通知进入成功创建*容器注册表*后，请单击 "**转到资源**"，将其重定向到 "服务" 页。</span><span class="sxs-lookup"><span data-stu-id="24c2a-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="24c2a-212">在 "*容器注册表*服务" 页上，单击 "**访问密钥**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="24c2a-213">请注意（可以使用记事本）以下参数：</span><span class="sxs-lookup"><span data-stu-id="24c2a-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="24c2a-214">**登录服务器**</span><span class="sxs-lookup"><span data-stu-id="24c2a-214">**Login Server**</span></span>
    2. <span data-ttu-id="24c2a-215">**Username**</span><span class="sxs-lookup"><span data-stu-id="24c2a-215">**Username**</span></span>
    3. <span data-ttu-id="24c2a-216">**密码**</span><span class="sxs-lookup"><span data-stu-id="24c2a-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="24c2a-217">第3章-IoT 中心服务</span><span class="sxs-lookup"><span data-stu-id="24c2a-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="24c2a-218">现在，你将开始创建和设置**IoT 中心服务**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="24c2a-219">如果尚未登录，请登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="24c2a-220">登录后，单击左上角的 "**创建资源**"，搜索 " **IoT 中心**"，然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![搜索存储帐户](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="24c2a-222">新页将提供**存储帐户**服务的说明。</span><span class="sxs-lookup"><span data-stu-id="24c2a-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="24c2a-223">在此提示符的左下方，单击 "**创建**" 按钮以创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="24c2a-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="24c2a-225">单击 "**创建**" 后，将显示一个面板：</span><span class="sxs-lookup"><span data-stu-id="24c2a-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="24c2a-226">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="24c2a-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="24c2a-227">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="24c2a-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="24c2a-228">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="24c2a-229">如果希望了解有关 Azure 资源组的详细信息，请参阅此[链接，了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="24c2a-230">选择适当的**位置**（在本课程中创建的所有服务之间使用同一位置）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="24c2a-231">为此服务实例插入所需的**名称**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="24c2a-232">在页面底部，单击 "**下一步：大小和缩放**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="24c2a-234">在此页中，选择**定价和缩放层**（如果这是你的第一个 IoT 中心服务实例，你应该可以使用免费层）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="24c2a-235">单击 "**查看" + "创建**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-235">Click on **Review + Create**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="24c2a-237">查看设置，然后单击 "**创建**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-237">Review your settings and click on **Create**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="24c2a-239">通知进入成功创建*IoT 中心*服务的通知后，请单击 "**转到资源**"，将其重定向到 "服务" 页。</span><span class="sxs-lookup"><span data-stu-id="24c2a-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="24c2a-241">滚动到左侧的侧面板，直到看到 "*自动设备管理*"，然后单击 " **IoT Edge**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="24c2a-243">在出现在右侧的窗口中，单击 "**添加 IoT Edge 设备**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="24c2a-244">边栏选项卡将显示在右侧。</span><span class="sxs-lookup"><span data-stu-id="24c2a-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="24c2a-245">在边栏选项卡中，为新设备提供**设备 ID** （所选的名称）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="24c2a-246">然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-246">Then, click **Save**.</span></span> <span data-ttu-id="24c2a-247">如果已**自动生成**勾选，则*主密钥*和*辅助密钥*将自动生成。</span><span class="sxs-lookup"><span data-stu-id="24c2a-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="24c2a-249">你将导航回*IoT Edge 设备*"部分，将在其中列出新设备。</span><span class="sxs-lookup"><span data-stu-id="24c2a-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="24c2a-250">单击新设备（下图中以红色突出显示）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![创建存储实例](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="24c2a-252">在出现的 "*设备详细信息*" 页上，获取**连接字符串**（主键）的副本。</span><span class="sxs-lookup"><span data-stu-id="24c2a-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="24c2a-254">返回到左侧的面板，单击 "*共享访问策略*" 将其打开。</span><span class="sxs-lookup"><span data-stu-id="24c2a-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="24c2a-255">在显示的页面上，单击 " **iothubowner**"，屏幕右侧会显示一个边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="24c2a-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="24c2a-256">请注意**连接字符串的连接字符串**（主密钥），以便以后在将*连接字符串*设置到设备时使用。</span><span class="sxs-lookup"><span data-stu-id="24c2a-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="24c2a-258">第4章-设置开发环境</span><span class="sxs-lookup"><span data-stu-id="24c2a-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="24c2a-259">若要为*IoT 中心边缘*创建和部署模块，需要在运行 Windows 10 的开发计算机上安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="24c2a-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="24c2a-260">[用于 Windows 的 Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，它将要求你创建一个可供下载的帐户。</span><span class="sxs-lookup"><span data-stu-id="24c2a-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="24c2a-261">[![下载适用于 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="24c2a-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="24c2a-262">Docker 需要*windows 10 专业* *版、企业版 14393*或*windows Server 2016 RTM*才能运行。</span><span class="sxs-lookup"><span data-stu-id="24c2a-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="24c2a-263">如果你运行的是其他版本的 Windows 10，则可以尝试使用[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)安装 docker。</span><span class="sxs-lookup"><span data-stu-id="24c2a-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="24c2a-264">[Python 3.6](https://www.python.org/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="24c2a-265">[![下载 python 3。6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="24c2a-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="24c2a-266">[Visual Studio Code （也称为 VS Code）](https://code.visualstudio.com/download)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="24c2a-267">[![下载 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="24c2a-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="24c2a-268">安装上述软件之后，需要重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="24c2a-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="24c2a-269">第5章-设置 Ubuntu 环境</span><span class="sxs-lookup"><span data-stu-id="24c2a-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="24c2a-270">现在，可以转到设置**运行 UBUNTU 操作系统**的设备。</span><span class="sxs-lookup"><span data-stu-id="24c2a-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="24c2a-271">按照以下步骤安装所需的软件，以便在你的面板上部署容器：</span><span class="sxs-lookup"><span data-stu-id="24c2a-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24c2a-272">应始终在带有**sudo**的终端命令之前，以管理员用户身份运行。</span><span class="sxs-lookup"><span data-stu-id="24c2a-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="24c2a-273">亦</span><span class="sxs-lookup"><span data-stu-id="24c2a-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="24c2a-274">打开**Ubuntu 终端**，并使用以下命令安装**pip**：</span><span class="sxs-lookup"><span data-stu-id="24c2a-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [!提示]<span data-ttu-id="24c2a-275"> 可以使用键盘快捷方式轻松地打开*终端*： **Ctrl + Alt + T**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="24c2a-276">在本章中，系统可能会提示你：*终端*，允许使用设备存储，并输入**y/n** （是或否），键入 **"y"** ，然后按**enter**键接受。</span><span class="sxs-lookup"><span data-stu-id="24c2a-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="24c2a-277">完成该命令后，请使用以下命令安装**卷**：</span><span class="sxs-lookup"><span data-stu-id="24c2a-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="24c2a-278">安装**pip**和**卷曲**后，使用以下命令安装**IoT Edge 运行时**，这是部署和控制板上的模块所必需的：</span><span class="sxs-lookup"><span data-stu-id="24c2a-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="24c2a-279">此时，系统将提示你打开*运行时配置文件*，以便在创建**IoT 中心服务**（在第[3 章的步骤 14](#chapter-3---the-iot-hub-service)中）时，插入你记下的**设备连接字符串**（在记事本中）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="24c2a-280">在终端上运行以下行，以打开该文件：</span><span class="sxs-lookup"><span data-stu-id="24c2a-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="24c2a-281">此时将显示**yaml**文件，供你编辑：</span><span class="sxs-lookup"><span data-stu-id="24c2a-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="24c2a-282">打开此文件时，可能会有些混乱。</span><span class="sxs-lookup"><span data-stu-id="24c2a-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="24c2a-283">你将在*终端*本身中编辑此文件的文本。</span><span class="sxs-lookup"><span data-stu-id="24c2a-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="24c2a-284">使用键盘上的箭头键向下滚动（您将需要向下滚动一点），以便到达包含 "：</span><span class="sxs-lookup"><span data-stu-id="24c2a-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="24c2a-285">" **\<在此处添加设备连接字符串 >** "。</span><span class="sxs-lookup"><span data-stu-id="24c2a-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="24c2a-286">用前面记下的**设备连接字符串**替换线条（**包括方括号**）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="24c2a-287">建立连接字符串后，请在键盘上按**Ctrl + X**键保存该文件。</span><span class="sxs-lookup"><span data-stu-id="24c2a-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="24c2a-288">它将要求通过键入**Y**进行确认。然后，按**enter**键以确认。</span><span class="sxs-lookup"><span data-stu-id="24c2a-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="24c2a-289">你将返回到常规*终端*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="24c2a-290">成功运行这些命令后，你将安装**IoT Edge 运行时**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="24c2a-291">初始化后，每次打开设备时，运行时就会自行启动，并将在后台等待从**IoT 中心服务**部署模块。</span><span class="sxs-lookup"><span data-stu-id="24c2a-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="24c2a-292">运行以下命令行，初始化*IoT Edge 运行时*：</span><span class="sxs-lookup"><span data-stu-id="24c2a-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="24c2a-293">如果更改了 yaml 文件或上述设置，则需要在*终端*内再次运行上面的重新启动行。</span><span class="sxs-lookup"><span data-stu-id="24c2a-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="24c2a-294">通过运行以下命令行检查*IoT Edge 运行时*状态。</span><span class="sxs-lookup"><span data-stu-id="24c2a-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="24c2a-295">运行时应以绿色文本显示状态 "**活动（正在运行）** "。</span><span class="sxs-lookup"><span data-stu-id="24c2a-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="24c2a-296">按下**Ctrl + C**键，退出 "状态" 页。</span><span class="sxs-lookup"><span data-stu-id="24c2a-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="24c2a-297">可以通过键入以下命令来验证*IoT Edge 运行时*是否正确拉取容器：</span><span class="sxs-lookup"><span data-stu-id="24c2a-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="24c2a-298">应该会出现一个包含两个（2）容器的列表。</span><span class="sxs-lookup"><span data-stu-id="24c2a-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="24c2a-299">这些是 IoT 中心服务（edgeAgent 和 edgeHub）自动创建的默认模块。</span><span class="sxs-lookup"><span data-stu-id="24c2a-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="24c2a-300">一旦您创建和部署自己的模块，它们将显示在此列表中的默认值之下。</span><span class="sxs-lookup"><span data-stu-id="24c2a-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="24c2a-301">第6章-安装扩展</span><span class="sxs-lookup"><span data-stu-id="24c2a-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24c2a-302">接下来的几章（6-9）将在你的 Windows 10 计算机上执行。</span><span class="sxs-lookup"><span data-stu-id="24c2a-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="24c2a-303">打开**VS Code**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="24c2a-304">单击 VS Code 左侧栏上的 "**扩展**" （方形）按钮，打开 "**扩展" 面板**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="24c2a-305">搜索并安装以下扩展（如下图所示）：</span><span class="sxs-lookup"><span data-stu-id="24c2a-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="24c2a-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="24c2a-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="24c2a-307">Azure IoT 工具包</span><span class="sxs-lookup"><span data-stu-id="24c2a-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="24c2a-308">Docker</span><span class="sxs-lookup"><span data-stu-id="24c2a-308">Docker</span></span>   

    ![创建容器](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="24c2a-310">安装扩展后，请关闭并重新打开 VS Code。</span><span class="sxs-lookup"><span data-stu-id="24c2a-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="24c2a-311">再次打开 VS Code，导航到 "**查看** > **集成终端**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="24c2a-312">现在，你将安装**Cookiecutter**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="24c2a-313">在终端中运行以下 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="24c2a-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示]<span data-ttu-id="24c2a-314"> 如果你在使用此命令时遇到问题：</span><span class="sxs-lookup"><span data-stu-id="24c2a-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="24c2a-315">重新启动 VS Code 和/或您的计算机。</span><span class="sxs-lookup"><span data-stu-id="24c2a-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="24c2a-316">可能有必要将**VS Code 终端**切换到你用来安装 Python 的计算机（即**Powershell** ）（尤其是在计算机上已安装 python 环境时）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="24c2a-317">打开终端后，会在终端的右侧找到下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="24c2a-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="24c2a-318">![创建容器](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="24c2a-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="24c2a-319">请确保将**Python**安装路径添加为计算机上的**环境变量**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="24c2a-320">Cookiecutter 应属于同一位置路径。</span><span class="sxs-lookup"><span data-stu-id="24c2a-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="24c2a-321">[有关环境变量的详细信息](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)，请访问此链接</span><span class="sxs-lookup"><span data-stu-id="24c2a-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="24c2a-322">**Cookiecutter**安装完成后，应重新启动计算机，以便在系统环境中将**Cookiecutter**识别为命令。</span><span class="sxs-lookup"><span data-stu-id="24c2a-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="24c2a-323">第7章-创建容器解决方案</span><span class="sxs-lookup"><span data-stu-id="24c2a-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="24c2a-324">此时，需要创建包含模块的容器，将其推送到*容器注册表*中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="24c2a-325">推送容器后，将使用*IoT 中心边缘*服务将其部署到运行*IoT Edge 运行时*的设备。</span><span class="sxs-lookup"><span data-stu-id="24c2a-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="24c2a-326">在 VS Code 中，单击 "**查看** > **命令面板**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="24c2a-327">在调色板中，搜索并运行**Azure IoT Edge：新的 IoT Edge 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="24c2a-328">浏览到要在其中创建解决方案的位置。</span><span class="sxs-lookup"><span data-stu-id="24c2a-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="24c2a-329">按**enter**键接受该位置。</span><span class="sxs-lookup"><span data-stu-id="24c2a-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="24c2a-330">为解决方案指定一个名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-330">Give a name to your solution.</span></span> <span data-ttu-id="24c2a-331">按**enter**键以确认所提供的名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="24c2a-332">现在，系统将提示您选择解决方案的模板框架。</span><span class="sxs-lookup"><span data-stu-id="24c2a-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="24c2a-333">单击 " **Python 模块**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-333">Click **Python Module**.</span></span> <span data-ttu-id="24c2a-334">按**enter**键确认此选择。</span><span class="sxs-lookup"><span data-stu-id="24c2a-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="24c2a-335">为模块指定名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-335">Give a name to your module.</span></span> <span data-ttu-id="24c2a-336">按**enter**键以确认模块的名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="24c2a-337">请确保记下模块名称的注释（使用记事本），因为稍后将用到它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="24c2a-338">你会注意到，组件面板上将显示预先生成的*Docker 映像存储库*地址。</span><span class="sxs-lookup"><span data-stu-id="24c2a-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="24c2a-339">它将如下所示：</span><span class="sxs-lookup"><span data-stu-id="24c2a-339">It will look like:</span></span>

    <span data-ttu-id="24c2a-340">**localhost： 5000/-模块的名称-** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="24c2a-341">删除**localhost： 5000**，并在其位置插入\*容器注册表\***登录服务器**地址，在创建**容器注册表服务**时记下该地址（[在第2章的步骤8中](#chapter-2---the-container-registry-service)）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="24c2a-342">按**enter**键以确认地址。</span><span class="sxs-lookup"><span data-stu-id="24c2a-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="24c2a-343">此时，将创建包含 Python 模块模板的解决方案，并将其结构显示在 "浏览" 选项卡的 "**浏览器" 选项卡**中，在 "浏览器" 选项卡中，在 "浏览器" 选项卡中，在 "VS Code</span><span class="sxs-lookup"><span data-stu-id="24c2a-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="24c2a-344">如果 "**资源管理器" 选项卡**未打开，则可以通过单击左侧栏中的最上面的按钮打开它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![创建容器](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="24c2a-346">本章的最后一个步骤是，从 "**浏览" 选项卡**中单击并打开 " **env" 文件**，然后添加\*容器注册表\***用户名**和**密码**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="24c2a-347">Git 忽略此文件，但在构建容器时，将设置用于访问**容器注册表服务**的凭据。</span><span class="sxs-lookup"><span data-stu-id="24c2a-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![创建容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="24c2a-349">第8章-编辑容器解决方案</span><span class="sxs-lookup"><span data-stu-id="24c2a-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="24c2a-350">现在，你将通过更新下列文件来完成容器解决方案：</span><span class="sxs-lookup"><span data-stu-id="24c2a-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="24c2a-351">py python 脚本。 *<span></span>*</span><span class="sxs-lookup"><span data-stu-id="24c2a-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="24c2a-352">*要求 .txt*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-352">*requirements.txt*.</span></span>
- <span data-ttu-id="24c2a-353">*deployment*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="24c2a-354">*Dockerfile amd64*</span><span class="sxs-lookup"><span data-stu-id="24c2a-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="24c2a-355">然后，将创建用于 python*脚本的 images 文件夹，* 以检查图像是否与*自定义视觉模型*匹配。</span><span class="sxs-lookup"><span data-stu-id="24c2a-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="24c2a-356">最后，您将添加*标签 .txt*文件，以帮助读取您的模型，以及*模型文件。*</span><span class="sxs-lookup"><span data-stu-id="24c2a-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="24c2a-357">打开 VS Code，导航到模块文件夹，然后查找名 **<span></span>为 py**的脚本。</span><span class="sxs-lookup"><span data-stu-id="24c2a-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="24c2a-358">双击以打开它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-358">Double-click to open it.</span></span>

2. <span data-ttu-id="24c2a-359">删除文件的内容并插入以下代码：</span><span class="sxs-lookup"><span data-stu-id="24c2a-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="24c2a-360">打开名为 "**要求 .txt**" 的文件，并将其内容替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="24c2a-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="24c2a-361">打开名为 " **deployment**" 的文件，并根据以下准则替换其内容：</span><span class="sxs-lookup"><span data-stu-id="24c2a-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="24c2a-362">由于你将拥有自己的唯一 JSON 结构，因此需要手动编辑（而不是复制示例）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="24c2a-363">为此，请使用以下图像作为指导。</span><span class="sxs-lookup"><span data-stu-id="24c2a-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="24c2a-364">外观与你的区域不同，但你**不应更改为黄色**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="24c2a-365">**您需要删除的部分将突出显示为红色。**</span><span class="sxs-lookup"><span data-stu-id="24c2a-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="24c2a-366">请注意删除正确的方括号，同时删除逗号。</span><span class="sxs-lookup"><span data-stu-id="24c2a-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![创建容器](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="24c2a-368">已完成的 JSON 应该如下图所示（但唯一的区别在于：*用户名/密码/模块名称/模块引用*）：</span><span class="sxs-lookup"><span data-stu-id="24c2a-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![创建容器](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="24c2a-370">打开名为**Dockerfile**的文件，并将其内容替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="24c2a-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="24c2a-371">右键单击 "**模块**" 下的文件夹（它将具有你先前提供的名称; 在示例中，该名称为 " *pythonmodule*"），然后单击 "**新建文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="24c2a-372">将文件夹命名为**images**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="24c2a-373">在该文件夹中，添加包含鼠标或键盘的一些图像。</span><span class="sxs-lookup"><span data-stu-id="24c2a-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="24c2a-374">这些将是 Tensorflow 模型将分析的映像。</span><span class="sxs-lookup"><span data-stu-id="24c2a-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="24c2a-375">如果你使用自己的模型，则需要更改此以反映你自己的模型数据。</span><span class="sxs-lookup"><span data-stu-id="24c2a-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="24c2a-376">你现在需要在[第1章](#chapter-1---retrieve-the-custom-vision-model)中从你先前下载的（或从你自己的**自定义影像服务**创建的）模型文件夹中检索**标签 .txt**和**model。**</span><span class="sxs-lookup"><span data-stu-id="24c2a-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="24c2a-377">获得这些文件后，请将它们放在解决方案中，并将它们放在其他文件中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="24c2a-378">最终结果应该如下图所示：</span><span class="sxs-lookup"><span data-stu-id="24c2a-378">The final result should look like the image below:</span></span>

    ![创建容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="24c2a-380">第9章-将解决方案打包为容器</span><span class="sxs-lookup"><span data-stu-id="24c2a-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="24c2a-381">现在，你可以将文件 "打包" 为容器并将其推送到**Azure 容器注册表**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="24c2a-382">在 VS Code 中，打开*集成终端*（**查看** > **集成终端**或按**Ctrl**+ **\`** ），并使用以下行登录到**Docker** （将命令的值替换为**Azure 容器注册表（ACR）** 的凭据：</span><span class="sxs-lookup"><span data-stu-id="24c2a-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="24c2a-383">右键单击文件 " **deployment**"，然后单击 "**生成 IoT Edge 解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="24c2a-384">此生成过程需要很长时间（具体取决于你的设备），因此请准备好等待。</span><span class="sxs-lookup"><span data-stu-id="24c2a-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="24c2a-385">在生成过程完成后，将在名为**config**的新文件夹内创建一个**deployment. json**文件。</span><span class="sxs-lookup"><span data-stu-id="24c2a-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![创建部署](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="24c2a-387">再次打开**命令面板**，然后搜索 " **Azure：登录**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="24c2a-388">按照使用 Azure 帐户凭据的提示进行操作;VS Code 将向你提供一个选项，用于*复制和打开*，这将会复制你即将需要的设备代码，并打开默认 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="24c2a-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="24c2a-389">当系统询问时，粘贴设备代码以对计算机进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="24c2a-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![复制并打开](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="24c2a-391">登录后，将在 "*浏览*" 面板的底部看到一个名为 " **Azure IoT 中心设备**" 的新部分。</span><span class="sxs-lookup"><span data-stu-id="24c2a-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="24c2a-392">单击此部分以将其展开。</span><span class="sxs-lookup"><span data-stu-id="24c2a-392">Click this section to expand it.</span></span>

    ![边缘设备](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="24c2a-394">如果你的设备不在此处，你需要右键单击 " *Azure IoT 中心设备*"，然后单击 "**设置 IoT 中心连接字符串**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="24c2a-395">然后，你将看到**命令面板**（位于 VS Code 顶部）将提示你输入*连接字符串*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="24c2a-396">这是你在[第3章](#chapter-3---the-iot-hub-service)末尾记下的*连接字符串*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="24c2a-397">在中复制字符串后，按**enter**键。</span><span class="sxs-lookup"><span data-stu-id="24c2a-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="24c2a-398">设备应加载并显示。</span><span class="sxs-lookup"><span data-stu-id="24c2a-398">Your device should load, and appear.</span></span> <span data-ttu-id="24c2a-399">右键单击设备名称，然后单击 "**创建单个设备的部署**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![创建部署](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="24c2a-401">你将看到一个*文件资源管理器*提示，你可以在其中导航到**config**文件夹，然后选择 " **deployment** " 文件。</span><span class="sxs-lookup"><span data-stu-id="24c2a-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="24c2a-402">选择该文件后，单击 "**选择边缘部署清单**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="24c2a-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![创建部署](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="24c2a-404">此时，你已为**IoT 中心服务**提供了一个清单，用于从**Azure 容器注册表**将容器（作为模块）部署到你的设备，并有效地将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="24c2a-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="24c2a-405">若要查看从设备发送到 IoT 中心的消息，请再次右键单击 " **Azure IoT 中心设备**" 部分中的设备名称，然后在 "**资源管理器**" 面板中单击 "**开始监视 D2C 消息**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="24c2a-406">设备发送的消息应显示在 VS 终端中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="24c2a-407">请耐心等待，因为这可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="24c2a-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="24c2a-408">请参阅下一章进行调试，并检查部署是否成功。</span><span class="sxs-lookup"><span data-stu-id="24c2a-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="24c2a-409">此模块现在将在**images**文件夹中的图像之间进行循环访问，并在每次迭代时进行分析。</span><span class="sxs-lookup"><span data-stu-id="24c2a-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="24c2a-410">这显然只是演示如何获取基本机器学习模型，以便在 IoT Edge 设备环境中工作。</span><span class="sxs-lookup"><span data-stu-id="24c2a-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="24c2a-411">若要扩展此示例的功能，可以通过多种方式继续操作。</span><span class="sxs-lookup"><span data-stu-id="24c2a-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="24c2a-412">其中一种方法可能是在容器中包含某些代码，这些代码从连接到设备的网络摄像机捕获照片，并将图像保存到 images 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="24c2a-413">另一种方法是将映像从 IoT 设备复制到容器中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="24c2a-414">实现此目的的一种可行方法是在 IoT 设备终端中运行以下命令（如果想要自动执行此过程，可能只有小型应用才能执行此操作）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="24c2a-415">可以通过从存储文件的文件夹位置手动运行此命令来对其进行测试：</span><span class="sxs-lookup"><span data-stu-id="24c2a-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="24c2a-416">第10章-调试 IoT Edge 运行时</span><span class="sxs-lookup"><span data-stu-id="24c2a-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="24c2a-417">下面是命令行和提示的列表，可帮助你从**Ubuntu 设备**监视和调试*IoT Edge 运行时*的消息传递活动。</span><span class="sxs-lookup"><span data-stu-id="24c2a-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="24c2a-418">通过运行以下命令行检查*IoT Edge 运行时*状态：</span><span class="sxs-lookup"><span data-stu-id="24c2a-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="24c2a-419">请记得按**Ctrl + C**来完成状态的查看。</span><span class="sxs-lookup"><span data-stu-id="24c2a-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="24c2a-420">列出当前部署的容器。</span><span class="sxs-lookup"><span data-stu-id="24c2a-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="24c2a-421">如果*IoT 中心服务*成功部署了容器，则会通过运行以下命令行来显示它们：</span><span class="sxs-lookup"><span data-stu-id="24c2a-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="24c2a-422">或</span><span class="sxs-lookup"><span data-stu-id="24c2a-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="24c2a-423">以上是检查模块是否已成功部署的好方法，因为它将出现在列表中;否则，你将**只**看到*edgeHub*和*edgeAgent*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="24c2a-424">若要显示容器的代码日志，请运行以下命令行：</span><span class="sxs-lookup"><span data-stu-id="24c2a-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="24c2a-425">**用于管理 IoT Edge 运行时的有用命令：**</span><span class="sxs-lookup"><span data-stu-id="24c2a-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="24c2a-426">删除主机中的所有容器：</span><span class="sxs-lookup"><span data-stu-id="24c2a-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="24c2a-427">若要停止*IoT Edge 运行时*：</span><span class="sxs-lookup"><span data-stu-id="24c2a-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="24c2a-428">第11章-创建表服务</span><span class="sxs-lookup"><span data-stu-id="24c2a-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="24c2a-429">导航回到 Azure 门户，在该门户中创建存储资源。</span><span class="sxs-lookup"><span data-stu-id="24c2a-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="24c2a-430">如果尚未登录，请登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="24c2a-431">登录后，单击左上角的 "**创建资源**"，搜索 "**存储帐户**"，然后按**enter**键开始搜索。</span><span class="sxs-lookup"><span data-stu-id="24c2a-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="24c2a-432">出现后，单击列表中的 "**存储帐户-blob、文件、表、队列**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜索存储帐户](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="24c2a-434">新页将提供**存储帐户**服务的说明。</span><span class="sxs-lookup"><span data-stu-id="24c2a-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="24c2a-435">在此提示符的左下方，单击 "**创建**" 按钮以创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="24c2a-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="24c2a-437">单击 "**创建**" 后，将显示一个面板：</span><span class="sxs-lookup"><span data-stu-id="24c2a-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="24c2a-438">为此服务实例插入所需的**名称**（*必须全部小写*）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="24c2a-439">对于**部署模型**，单击 "**资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="24c2a-440">对于 "**帐户类型**"，请使用下拉菜单，单击 "**存储（常规用途 v1）** "。</span><span class="sxs-lookup"><span data-stu-id="24c2a-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="24c2a-441">单击适当的**位置**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="24c2a-442">对于 "**复制**" 下拉菜单，单击 "**读取-访问-异地冗余存储（GRS）** "。</span><span class="sxs-lookup"><span data-stu-id="24c2a-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="24c2a-443">对于 "**性能**"，请单击 "**标准**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="24c2a-444">在 "**需要安全传输**" 部分中，单击 "**禁用**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="24c2a-445">从 "**订阅**" 下拉菜单中，单击相应的订阅。</span><span class="sxs-lookup"><span data-stu-id="24c2a-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="24c2a-446">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="24c2a-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="24c2a-447">资源组提供一种方式来监视、控制访问、预配和管理 Azure 资产集合的计费。</span><span class="sxs-lookup"><span data-stu-id="24c2a-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="24c2a-448">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="24c2a-449">如果希望了解有关 Azure 资源组的详细信息，请参阅此[链接，了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="24c2a-450">如果这是一个选项，请将**虚拟网络**保留为**禁用状态**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="24c2a-451">单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-451">Click **Create**.</span></span>

        ![填写存储详细信息](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="24c2a-453">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="24c2a-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="24c2a-454">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="24c2a-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="24c2a-455">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="24c2a-455">Click on the notifications to explore your new Service instance.</span></span>

    ![新存储通知](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="24c2a-457">单击通知中的 "**转到资源**" 按钮，会转到 "新建存储服务实例概述" 页。</span><span class="sxs-lookup"><span data-stu-id="24c2a-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![中转到资源](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="24c2a-459">在 "概述" 页中，单击右侧的 "**表**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![张](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="24c2a-461">右侧面板将更改为显示**表服务**信息，你需要添加一个新表。</span><span class="sxs-lookup"><span data-stu-id="24c2a-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="24c2a-462">单击左上角的 " **+ 表**" 按钮即可执行此操作。</span><span class="sxs-lookup"><span data-stu-id="24c2a-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![打开表](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="24c2a-464">将显示一个新页，需要在其中输入**表名称**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="24c2a-465">这是将用于在后面的章节中引用应用程序中的数据的名称（创建 Function App 和 Power BI）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="24c2a-466">插入 " **IoTMessages** " 作为名称（可以自行选择，只需记住它，稍后在本文档中使用），然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="24c2a-467">创建新表后，可以在 "**表服务**" 页（底部）中查看它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![已创建新表](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="24c2a-469">现在，单击 "**访问密钥**"，然后复制**存储帐户名称**和**密钥**（使用记事本），稍后在创建**Azure Function App**时，将使用这些值。</span><span class="sxs-lookup"><span data-stu-id="24c2a-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![已创建新表](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="24c2a-471">再次使用左侧的面板，滚动到 "*表服务*" 部分，单击 "**表**" （或 "在新门户中**浏览表**"），并获取**表 URL** （使用记事本）的副本。</span><span class="sxs-lookup"><span data-stu-id="24c2a-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="24c2a-472">在本课程中，将表链接到**Power BI**应用程序时，将使用此值。</span><span class="sxs-lookup"><span data-stu-id="24c2a-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![已创建新表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="24c2a-474">第12章-完成 Azure 表</span><span class="sxs-lookup"><span data-stu-id="24c2a-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="24c2a-475">由于已设置了**表服务**存储帐户，因此可以向其添加数据，这将用于存储和检索信息。</span><span class="sxs-lookup"><span data-stu-id="24c2a-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="24c2a-476">可以通过**Visual Studio**来编辑表。</span><span class="sxs-lookup"><span data-stu-id="24c2a-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="24c2a-477">打开**Visual Studio** （**不**Visual Studio Code）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="24c2a-478">从菜单中，单击 "**查看** > **Cloud Explorer**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![打开 cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="24c2a-480">**Cloud Explorer**将作为停靠项打开（患者，因为加载可能需要一些时间）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="24c2a-481">如果用于创建*存储帐户*的订阅不可见，请确保：</span><span class="sxs-lookup"><span data-stu-id="24c2a-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="24c2a-482">已登录到与 Azure 门户一起使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="24c2a-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="24c2a-483">从 "帐户管理" 页中选择了你的订阅（你可能需要从帐户设置应用筛选器）：</span><span class="sxs-lookup"><span data-stu-id="24c2a-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![查找订阅](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="24c2a-485">将显示你的 Azure 云服务。</span><span class="sxs-lookup"><span data-stu-id="24c2a-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="24c2a-486">查找**存储帐户**，并单击其左侧的箭头以展开你的帐户。</span><span class="sxs-lookup"><span data-stu-id="24c2a-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![打开存储帐户](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="24c2a-488">展开后，新创建的**存储帐户**应该可用。</span><span class="sxs-lookup"><span data-stu-id="24c2a-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="24c2a-489">单击存储左侧的箭头，然后在展开后，查找 "**表**" 并单击该按钮旁边的箭头，以显示在上一章中创建的**表**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="24c2a-490">双击**表**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="24c2a-491">您的表将在您的 Visual Studio 窗口的中心打开。</span><span class="sxs-lookup"><span data-stu-id="24c2a-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="24c2a-492">单击表图标，其中包含 **+** （加号）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![添加新表](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="24c2a-494">将显示一个窗口，提示你*添加实体*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="24c2a-495">您将只创建一个实体，但它将具有三个属性。</span><span class="sxs-lookup"><span data-stu-id="24c2a-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="24c2a-496">你会注意到已提供了*PartitionKey*和*RowKey* ，因为表使用这些方法来查找数据。</span><span class="sxs-lookup"><span data-stu-id="24c2a-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![分区和行键](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="24c2a-498">更新以下值：</span><span class="sxs-lookup"><span data-stu-id="24c2a-498">Update the following values:</span></span>

    - <span data-ttu-id="24c2a-499">名称： **PartitionKey**，值： **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="24c2a-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="24c2a-500">名称： **RowKey**，值： **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="24c2a-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="24c2a-501">然后，在 "*添加实体*" 窗口的左下角单击 "**添加属性**"，并添加以下属性：</span><span class="sxs-lookup"><span data-stu-id="24c2a-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="24c2a-502">**MessageContent** *，将值*保留为空。</span><span class="sxs-lookup"><span data-stu-id="24c2a-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="24c2a-503">表应与下图中的表匹配：</span><span class="sxs-lookup"><span data-stu-id="24c2a-503">Your table should match the one in the image below:</span></span>

    ![添加正确的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="24c2a-505">在行键中，实体的编号为1的原因是，您可能需要添加更多的消息，而您希望在本课程中进行进一步试验。</span><span class="sxs-lookup"><span data-stu-id="24c2a-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="24c2a-506">完成后，单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="24c2a-507">现在可以使用表了。</span><span class="sxs-lookup"><span data-stu-id="24c2a-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="24c2a-508">第13章-创建 Azure Function App</span><span class="sxs-lookup"><span data-stu-id="24c2a-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="24c2a-509">现在可以创建一个*Azure Function App*， *IoT 中心服务*将调用该将*IoT Edge*设备消息存储在之前章节中创建的**表**服务中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="24c2a-510">首先，需要创建一个文件，该文件允许 Azure 函数加载所需的库。</span><span class="sxs-lookup"><span data-stu-id="24c2a-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="24c2a-511">打开**记事本**（按*Windows 键*，然后键入*Notepad*）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![打开记事本](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="24c2a-513">打开记事本后，将下面的 JSON 结构插入其中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="24c2a-514">完成此操作后，将其以**项目 json**的形式保存在桌面上。</span><span class="sxs-lookup"><span data-stu-id="24c2a-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="24c2a-515">此文件定义函数将使用的库。</span><span class="sxs-lookup"><span data-stu-id="24c2a-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="24c2a-516">如果使用了 NuGet，则会很熟悉。</span><span class="sxs-lookup"><span data-stu-id="24c2a-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="24c2a-517">命名正确，这一点很重要。确保它没有 **.txt**文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="24c2a-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="24c2a-518">请参阅下面的参考：</span><span class="sxs-lookup"><span data-stu-id="24c2a-518">See below for reference:</span></span>
    >
    > ![JSON 保存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="24c2a-520">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="24c2a-521">登录后，单击左上角的 "**创建资源**"，搜索**Function App**，然后按**enter**键进行搜索。</span><span class="sxs-lookup"><span data-stu-id="24c2a-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="24c2a-522">在结果中单击 " *Function App* " 以打开新面板。</span><span class="sxs-lookup"><span data-stu-id="24c2a-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![搜索函数应用](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="24c2a-524">新面板将提供**Function App**服务的说明。</span><span class="sxs-lookup"><span data-stu-id="24c2a-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="24c2a-525">在此面板的左下方，单击 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="24c2a-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![function app 实例](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="24c2a-527">单击 "**创建**" 后，请填写以下内容：</span><span class="sxs-lookup"><span data-stu-id="24c2a-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="24c2a-528">对于 "**应用名称**"，请为此服务实例插入所需的名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="24c2a-529">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="24c2a-530">选择适合你的定价层，如果这是第一次创建**Function App 服务**，则应提供免费层。</span><span class="sxs-lookup"><span data-stu-id="24c2a-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="24c2a-531">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="24c2a-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="24c2a-532">资源组提供一种方式来监视、控制访问、预配和管理 Azure 资产集合的计费。</span><span class="sxs-lookup"><span data-stu-id="24c2a-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="24c2a-533">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="24c2a-534">如果希望了解有关 Azure 资源组的详细信息，请参阅此[链接，了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="24c2a-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="24c2a-535">对于**操作系统**，请单击 "Windows"，因为这是预期的平台。</span><span class="sxs-lookup"><span data-stu-id="24c2a-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="24c2a-536">选择**托管计划**（本教程使用**消耗计划**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="24c2a-537">选择**位置**（选择与在上一步骤中生成的存储相同的位置）</span><span class="sxs-lookup"><span data-stu-id="24c2a-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="24c2a-538">对于 "**存储**" 部分，**你必须选择在上一步中创建的存储服务**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="24c2a-539">在此应用中不需要*Application Insights* ，因此可随意将其**关闭**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="24c2a-540">单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-540">Click **Create**.</span></span>

        ![创建新实例](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="24c2a-542">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="24c2a-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="24c2a-543">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="24c2a-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![新建通知](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="24c2a-545">完成部署后，单击 "通知"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="24c2a-546">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="24c2a-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![中转到资源](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="24c2a-548">在新面板的左侧，单击 "*函数*" 旁边的 **+** （加号）图标以创建新函数。</span><span class="sxs-lookup"><span data-stu-id="24c2a-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![添加新函数](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="24c2a-550">在中央面板中，将显示 "**函数**创建" 窗口。</span><span class="sxs-lookup"><span data-stu-id="24c2a-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="24c2a-551">进一步向下滚动，然后单击 "**自定义函数**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-551">Scroll down further, and click on **Custom function**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="24c2a-553">在下一页上向下滚动，直到找到**IoT 中心（事件中心）** ，然后单击它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="24c2a-555">在 " **IoT 中心（事件中心）** " 边栏选项卡中， **C#** 将 "语言" 设置为，然后单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="24c2a-557">在将显示的窗口中，确保已选中 " **Iot 中心**"，并且 " *iot 中心*" 字段的名称与你之前创建的*iot 中心服务*的名称（[在第3章的步骤8中](#chapter-3---the-iot-hub-service)）相对应。</span><span class="sxs-lookup"><span data-stu-id="24c2a-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="24c2a-558">然后单击 "**选择**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="24c2a-558">Then click the **Select** button.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="24c2a-560">返回到**IoT 中心（事件中心）** 边栏选项卡，并单击 "**创建**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="24c2a-562">你将被重定向到函数编辑器。</span><span class="sxs-lookup"><span data-stu-id="24c2a-562">You will be redirected to the function editor.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="24c2a-564">删除其中的所有代码，并将其替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="24c2a-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="24c2a-565">更改以下变量，使其对应于你将在**存储帐户**中找到的相应值（**表**和**存储**值，[分别为第11章和第11章的步骤11和 13](#chapter-11---create-table-service)）：</span><span class="sxs-lookup"><span data-stu-id="24c2a-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="24c2a-566">**tableName**，其中包含你的**存储帐户**中的**表**的名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="24c2a-567">**tableURL**，其中包含你的**存储帐户**中的**表**的 URL。</span><span class="sxs-lookup"><span data-stu-id="24c2a-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="24c2a-568">**storageAccountName**，其中包含与你的**存储帐户**名称的名称相对应的值的名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="24c2a-569">**storageAccountKey**，其中包含你之前在创建的存储服务中获得的密钥。</span><span class="sxs-lookup"><span data-stu-id="24c2a-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="24c2a-571">在代码准备就绪后，单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="24c2a-572">接下来，单击页面右侧的 **\<** （箭头）图标。</span><span class="sxs-lookup"><span data-stu-id="24c2a-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="24c2a-574">面板会从右侧滑入。</span><span class="sxs-lookup"><span data-stu-id="24c2a-574">A panel will slide in from the right.</span></span> <span data-ttu-id="24c2a-575">在该面板中，单击 "**上载**"，将显示*文件浏览器*。</span><span class="sxs-lookup"><span data-stu-id="24c2a-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="24c2a-576">导航到，然后单击 "您之前在**记事本**中创建的**项目 json**文件"，然后单击 "**打开**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="24c2a-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="24c2a-577">此文件定义函数将使用的库。</span><span class="sxs-lookup"><span data-stu-id="24c2a-577">This file defines the libraries that your function will use.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="24c2a-579">文件上传后，它将显示在右侧的面板中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="24c2a-580">单击它会在**函数**编辑器中打开它。</span><span class="sxs-lookup"><span data-stu-id="24c2a-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="24c2a-581">它必须与下一个图像**完全**相同。</span><span class="sxs-lookup"><span data-stu-id="24c2a-581">It must look **exactly** the same as the next image.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="24c2a-583">此时，最好测试函数将消息存储在*表*中的功能。</span><span class="sxs-lookup"><span data-stu-id="24c2a-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="24c2a-584">在窗口的右上角，单击 "**测试**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-584">On the top right side of the window, click on **Test**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="24c2a-586">在**请求正文**中插入一条消息（如上图所示），然后单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="24c2a-587">该函数将运行，并显示结果状态（你将注意到 "*输出*" 窗口上方的 "已**接受绿色状态 202**"，这表示它是成功的调用）：</span><span class="sxs-lookup"><span data-stu-id="24c2a-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![输出结果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="24c2a-589">第14章-查看活动消息</span><span class="sxs-lookup"><span data-stu-id="24c2a-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="24c2a-590">如果现在打开 Visual Studio （**而不**是 Visual Studio Code），可以可视化测试消息结果，因为它将存储在*MessageContent*字符串区域中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![自定义函数](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="24c2a-592">在表服务和 Function App 就绪后，Ubuntu 设备消息将显示在*IoTMessages*表中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="24c2a-593">如果尚未运行，则重新启动设备，你将能够通过使用 Visual Studio *Cloud Explorer*在表中看到来自你的设备和模块的结果消息。</span><span class="sxs-lookup"><span data-stu-id="24c2a-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![可视化数据](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="24c2a-595">第15章-Power BI 安装</span><span class="sxs-lookup"><span data-stu-id="24c2a-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="24c2a-596">若要将数据从 IOT 设备中可视化，你需要设置**Power BI** （桌面版本），以从你刚创建的*表*服务中收集数据。</span><span class="sxs-lookup"><span data-stu-id="24c2a-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="24c2a-597">Power BI 的*HoloLens*版本随后将使用该数据来可视化结果。</span><span class="sxs-lookup"><span data-stu-id="24c2a-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="24c2a-598">在 Windows 10 上打开 Microsoft Store，并搜索**Power BI Desktop**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="24c2a-600">下载应用程序。</span><span class="sxs-lookup"><span data-stu-id="24c2a-600">Download the application.</span></span> <span data-ttu-id="24c2a-601">完成下载后，请将其打开。</span><span class="sxs-lookup"><span data-stu-id="24c2a-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="24c2a-602">用**Microsoft 365 帐户**登录*Power BI* 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="24c2a-603">你可能会被重定向到浏览器进行注册。</span><span class="sxs-lookup"><span data-stu-id="24c2a-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="24c2a-604">注册后，返回到 Power BI 应用，然后再次登录。</span><span class="sxs-lookup"><span data-stu-id="24c2a-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="24c2a-605">单击 "**获取数据**"，然后单击 "**更多 ...** "。</span><span class="sxs-lookup"><span data-stu-id="24c2a-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="24c2a-607">单击 " **azure**"、" **azure 表存储**"，然后单击 "**连接**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="24c2a-609">系统将提示您插入先前收集的**表 URL** （[第11章第11章的第13步](#chapter-11---create-table-service)），同时创建表服务。</span><span class="sxs-lookup"><span data-stu-id="24c2a-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="24c2a-610">插入 URL 后，删除引用表 "子文件夹" （在本课程中为 IoTMessages）的路径部分。</span><span class="sxs-lookup"><span data-stu-id="24c2a-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="24c2a-611">最终结果应如下图所示。</span><span class="sxs-lookup"><span data-stu-id="24c2a-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="24c2a-612">然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="24c2a-614">系统将提示你在创建表存储时，先插入你记下的**存储密钥**（[在第11章的第11章中](#chapter-11---create-table-service)）。</span><span class="sxs-lookup"><span data-stu-id="24c2a-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="24c2a-615">然后单击 "**连接**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="24c2a-617">将显示 **"导航器" 面板**，勾选表旁边的框，然后单击 "**加载**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="24c2a-619">你的表现在已在 Power BI 上加载，但它需要一个查询以显示其中的值。</span><span class="sxs-lookup"><span data-stu-id="24c2a-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="24c2a-620">为此，请右键单击位于屏幕右侧的 "**字段" 面板**中的表名称。</span><span class="sxs-lookup"><span data-stu-id="24c2a-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="24c2a-621">然后单击 "**编辑查询**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="24c2a-623">**Power Query 编辑器**将作为新窗口打开，并显示您的表。</span><span class="sxs-lookup"><span data-stu-id="24c2a-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="24c2a-624">单击表的 "*内容*" 列中的字词**记录**，以可视化存储的内容。</span><span class="sxs-lookup"><span data-stu-id="24c2a-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="24c2a-626">单击窗口左上角的 "**到表**"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="24c2a-628">单击 "**关闭" & 应用**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="24c2a-630">完成加载查询后，在屏幕右侧的 "**字段" 面板**中，勾选与参数**名称**和**值**相对应的框，以可视化**MessageContent**列内容。</span><span class="sxs-lookup"><span data-stu-id="24c2a-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="24c2a-632">单击窗口左上角的**蓝色磁盘图标**，将工作保存到所选的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="24c2a-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="24c2a-634">你现在可以单击 "发布" 按钮将表上传到工作区。</span><span class="sxs-lookup"><span data-stu-id="24c2a-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="24c2a-635">出现提示时，单击 **"我的工作区**" 并单击 "*选择*"。</span><span class="sxs-lookup"><span data-stu-id="24c2a-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="24c2a-636">等待它显示成功提交的提交结果。</span><span class="sxs-lookup"><span data-stu-id="24c2a-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="24c2a-639">下面是特定于 HoloLens 的章节。</span><span class="sxs-lookup"><span data-stu-id="24c2a-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="24c2a-640">Power BI 当前不适用于沉浸式应用程序，但你可以通过桌面应用在 Windows Mixed Reality 门户（也称为 Cliff 房子）中运行桌面版本。</span><span class="sxs-lookup"><span data-stu-id="24c2a-640">Power BI is not currently available as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="24c2a-641">第16章-显示 Power BI HoloLens 上的数据</span><span class="sxs-lookup"><span data-stu-id="24c2a-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="24c2a-642">在 HoloLens 上，通过在应用程序列表中点击其图标来登录到**Microsoft Store**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="24c2a-644">搜索并下载**Power BI**应用程序。</span><span class="sxs-lookup"><span data-stu-id="24c2a-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="24c2a-646">从应用程序列表中启动**Power BI** 。</span><span class="sxs-lookup"><span data-stu-id="24c2a-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="24c2a-647">**Power BI**可能会要求你登录到**Microsoft 365 帐户**。</span><span class="sxs-lookup"><span data-stu-id="24c2a-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="24c2a-648">在应用程序中，默认情况下，工作区应显示，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="24c2a-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="24c2a-649">如果未执行此操作，只需单击窗口左侧的工作区图标。</span><span class="sxs-lookup"><span data-stu-id="24c2a-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="24c2a-651">已完成 IoT 中心应用程序</span><span class="sxs-lookup"><span data-stu-id="24c2a-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="24c2a-652">恭喜，你已成功创建了一个包含模拟虚拟机边缘设备的 IoT 中心服务。</span><span class="sxs-lookup"><span data-stu-id="24c2a-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="24c2a-653">你的设备可以将机器学习模型的结果传达给 Azure 表服务，该服务由 Azure Function App （读入 Power BI 并在 Microsoft HoloLens 中进行可视化）促进。</span><span class="sxs-lookup"><span data-stu-id="24c2a-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="24c2a-655">额外练习</span><span class="sxs-lookup"><span data-stu-id="24c2a-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="24c2a-656">练习1</span><span class="sxs-lookup"><span data-stu-id="24c2a-656">Exercise 1</span></span>

<span data-ttu-id="24c2a-657">展开表中存储的消息结构，并将其显示为图形。</span><span class="sxs-lookup"><span data-stu-id="24c2a-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="24c2a-658">您可能想要收集更多的数据，并将其存储在同一个表中，以便以后显示。</span><span class="sxs-lookup"><span data-stu-id="24c2a-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="24c2a-659">练习2</span><span class="sxs-lookup"><span data-stu-id="24c2a-659">Exercise 2</span></span>

<span data-ttu-id="24c2a-660">创建要部署在 IoT 板上的其他 "相机捕获" 模块，使其可以通过要分析的相机捕获映像。</span><span class="sxs-lookup"><span data-stu-id="24c2a-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
