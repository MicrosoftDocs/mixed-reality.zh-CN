---
title: MR 和 Azure 313-IoT 中心服务
description: 完成此课程以了解如何在运行 Ubuntu 16.4 的虚拟机上实现 Azure IoT 中心服务，然后使用 Microsoft HoloLens 或沉浸式的 (VR) 耳机将消息数据可视化。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 edge、 iot edge、 教程、 api、 通知、 函数中，表、 沉浸式 hololens、 vr、 iot、 虚拟机、 ubuntu、 python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590108"
---
>[!NOTE]
><span data-ttu-id="21a2c-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="21a2c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="21a2c-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="21a2c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="21a2c-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="21a2c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="21a2c-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="21a2c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="21a2c-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="21a2c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="21a2c-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="21a2c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="21a2c-110">MR 和 Azure 313:IoT 中心服务</span><span class="sxs-lookup"><span data-stu-id="21a2c-110">MR and Azure 313: IoT Hub Service</span></span>

![课程结果](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="21a2c-112">在本课程中，您将学习如何实现**Azure IoT 中心服务**虚拟机上运行 Ubuntu 16.4 操作系统。</span><span class="sxs-lookup"><span data-stu-id="21a2c-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="21a2c-113">**Azure Function App**然后将使用 Ubuntu VM，从接收消息并在将结果存储**Azure 表服务**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="21a2c-114">然后将能够查看此数据使用**Power BI** Microsoft HoloLens 或沉浸式 (VR) 耳机上。</span><span class="sxs-lookup"><span data-stu-id="21a2c-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="21a2c-115">本课程的内容*适用于*到 IoT Edge 设备，但在本课程中，他们将着重介绍在虚拟机环境中，因此就不需要访问物理边缘设备。</span><span class="sxs-lookup"><span data-stu-id="21a2c-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="21a2c-116">通过完成本课程，您将了解到：</span><span class="sxs-lookup"><span data-stu-id="21a2c-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="21a2c-117">部署**IoT Edge 模块**到虚拟机 (Ubuntu 16 OS)，它将表示你的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="21a2c-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="21a2c-118">添加**Azure 自定义影像 Tensorflow 模型**到 Edge 模块，将分析图像存储在容器中的代码。</span><span class="sxs-lookup"><span data-stu-id="21a2c-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="21a2c-119">设置该模块将分析结果消息发送回您**IoT 中心服务**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="21a2c-120">使用**Azure Function App**存储中的消息**Azure 表**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="21a2c-121">设置**Power BI**收集存储的消息和创建报表。</span><span class="sxs-lookup"><span data-stu-id="21a2c-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="21a2c-122">实现 IoT 消息中的数据可视化效果**Power BI**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="21a2c-123">将使用的服务包括：</span><span class="sxs-lookup"><span data-stu-id="21a2c-123">The Services you will use include:</span></span>

- <span data-ttu-id="21a2c-124">**Azure IoT 中心**是一种 Microsoft Azure 服务，使开发人员可以连接、 监视和管理 IoT 资产。</span><span class="sxs-lookup"><span data-stu-id="21a2c-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="21a2c-125">有关详细信息，请访问[ **Azure IoT 中心服务**页面](https://azure.microsoft.com/en-au/services/iot-hub/)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="21a2c-126">**Azure 容器注册表**是一种 Microsoft Azure 服务，使开发人员可以将容器映像，为各种类型的容器。</span><span class="sxs-lookup"><span data-stu-id="21a2c-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="21a2c-127">有关详细信息，请访问[ **Azure 容器注册表服务**页面](https://azure.microsoft.com/en-au/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="21a2c-128">**Azure Function App**是一个 Microsoft Azure 服务，它允许开发人员运行小段代码，函数，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="21a2c-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="21a2c-129">这使您能够将工作委托给云，而不是本地应用程序，它可以有许多好处。</span><span class="sxs-lookup"><span data-stu-id="21a2c-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="21a2c-130">**Azure Functions**支持多种开发语言，包括 C\#，F\#，Node.js、 Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="21a2c-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="21a2c-131">有关详细信息，请访问[ **Azure Functions**页面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="21a2c-132">**Azure 存储：表**是一个 Microsoft Azure 服务，它使开发人员可以存储结构化，非 SQL、 数据在云中，使其在任意位置时可以轻松进行访问。</span><span class="sxs-lookup"><span data-stu-id="21a2c-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="21a2c-133">该服务实现了一种无架构设计，根据需要允许为表的演变，因此非常灵活。</span><span class="sxs-lookup"><span data-stu-id="21a2c-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="21a2c-134">有关详细信息，请访问[ **Azure 表**页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="21a2c-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="21a2c-135">本课程将介绍如何设置并使用 IoT 中心服务，然后直观显示由设备提供的响应。</span><span class="sxs-lookup"><span data-stu-id="21a2c-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="21a2c-136">它将取决于您要应用于自定义的 IoT 中心服务安装，您可能要构建的这些概念。</span><span class="sxs-lookup"><span data-stu-id="21a2c-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="21a2c-137">设备支持</span><span class="sxs-lookup"><span data-stu-id="21a2c-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="21a2c-138">课程</span><span class="sxs-lookup"><span data-stu-id="21a2c-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="21a2c-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="21a2c-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="21a2c-140"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="21a2c-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="21a2c-141">MR 和 Azure 313:IoT 中心服务</span><span class="sxs-lookup"><span data-stu-id="21a2c-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="21a2c-142">✔️</span><span class="sxs-lookup"><span data-stu-id="21a2c-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="21a2c-143">✔️</span><span class="sxs-lookup"><span data-stu-id="21a2c-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="21a2c-144">先决条件</span><span class="sxs-lookup"><span data-stu-id="21a2c-144">Prerequisites</span></span>

<span data-ttu-id="21a2c-145">有关使用混合现实，包括与 Microsoft HoloLens，进行开发的最新的必备组件，请访问[安装的工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文。</span><span class="sxs-lookup"><span data-stu-id="21a2c-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="21a2c-146">本教程专为开发人员没有使用 Python 的基本经验。</span><span class="sxs-lookup"><span data-stu-id="21a2c-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="21a2c-147">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="21a2c-148">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配将比下面列出的较新的软件中找到的内容。</span><span class="sxs-lookup"><span data-stu-id="21a2c-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="21a2c-149">以下硬件和软件是必需的：</span><span class="sxs-lookup"><span data-stu-id="21a2c-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="21a2c-150">Windows 10 Fall Creators Update （或更高版本），**启用开发人员模式**</span><span class="sxs-lookup"><span data-stu-id="21a2c-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="21a2c-151">不能运行在 Windows 10 家庭版上使用 HYPER-V 的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="21a2c-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="21a2c-152">Windows 10 SDK （最新版本）</span><span class="sxs-lookup"><span data-stu-id="21a2c-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="21a2c-153">一个 HoloLens，**启用开发人员模式**</span><span class="sxs-lookup"><span data-stu-id="21a2c-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="21a2c-154">Visual Studio 2017.15.4 （仅用于访问 Azure 云资源管理器）</span><span class="sxs-lookup"><span data-stu-id="21a2c-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="21a2c-155">Internet 访问 Azure，以及 IoT 中心服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="21a2c-156">有关详细信息，请遵循此[链接到 IoT 中心服务页](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="21a2c-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="21a2c-157">机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="21a2c-157">A machine learning model.</span></span> <span data-ttu-id="21a2c-158">如果不具有自己的已准备好使用模型中，[可以使用与此课程中提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="21a2c-159">**Hyper V** Windows 10 的开发计算机上启用软件。</span><span class="sxs-lookup"><span data-stu-id="21a2c-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="21a2c-160">在开发计算机或者运行运行 Ubuntu （16.4 或 18.4） 的虚拟机可以使用运行 Linux (Ubuntu 16.4 或 18.4) 的单独计算机。</span><span class="sxs-lookup"><span data-stu-id="21a2c-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="21a2c-161">可以找到有关如何在 Windows 上创建的 VM 详细信息使用中的 HYPER-V ["开始之前"一章](#before-you-start)。 (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="21a2c-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="21a2c-162">开始之前</span><span class="sxs-lookup"><span data-stu-id="21a2c-162">Before you start</span></span>

1. <span data-ttu-id="21a2c-163">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="21a2c-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="21a2c-164">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="21a2c-165">它是执行一个好办法**校准**并**传感器优化**开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时。</span><span class="sxs-lookup"><span data-stu-id="21a2c-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="21a2c-166">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="21a2c-167">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="21a2c-168">设置你**Ubuntu 虚拟机**使用**HYPER-V**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="21a2c-169">以下资源将帮助你与该进程。</span><span class="sxs-lookup"><span data-stu-id="21a2c-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="21a2c-170">首先，按照此链接[下载 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="21a2c-171">选择**64 位电脑 (AMD64) 桌面映像**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="21a2c-172">请确保**HYPER-V**在 Windows 10 计算机上启用。</span><span class="sxs-lookup"><span data-stu-id="21a2c-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="21a2c-173">您可以在跟踪指导此链接[安装和启用 Windows 10 上的 HYPER-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="21a2c-174">启动 HYPER-V 并创建一个新的 Ubuntu 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="21a2c-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="21a2c-175">可以按照此链接[有关如何使用 HYPER-V 创建虚拟机的分步指南](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="21a2c-176">请求时 **"从可启动映像文件安装操作系统"**，选择**Ubuntu ISO**先前已下载。</span><span class="sxs-lookup"><span data-stu-id="21a2c-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="21a2c-177">使用**HYPER-V 快速创建**不建议使用。</span><span class="sxs-lookup"><span data-stu-id="21a2c-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="21a2c-178">第 1 章-检索自定义影像模型</span><span class="sxs-lookup"><span data-stu-id="21a2c-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="21a2c-179">本课程将有权[预建的自定义影像模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)，用于检测键盘和鼠标从映像。</span><span class="sxs-lookup"><span data-stu-id="21a2c-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="21a2c-180">如果使用此操作，请转到[第 2 章](#chapter-2---the-container-registry-service)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="21a2c-181">但是，如果你想要使用你自己的自定义影像模型可以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="21a2c-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="21a2c-182">在你**自定义视觉项目**转到**性能**选项卡。</span><span class="sxs-lookup"><span data-stu-id="21a2c-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="21a2c-183">您的模型必须使用*compact*域，以导出该模型。</span><span class="sxs-lookup"><span data-stu-id="21a2c-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="21a2c-184">你可以为你的项目中设置模型的域。</span><span class="sxs-lookup"><span data-stu-id="21a2c-184">You can change your models domain in the settings for your project.</span></span>

    ![性能选项卡](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="21a2c-186">选择**迭代**你想要导出，然后单击**导出**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="21a2c-187">将显示一个边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="21a2c-187">A blade will appear.</span></span>

    ![导出边栏选项卡](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="21a2c-189">在边栏选项卡中单击**Docker 文件**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-189">In the blade click **Docker File**.</span></span>

    ![选择 docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="21a2c-191">单击**Linux**在下拉列表菜单，然后单击**下载**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![单击下载](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="21a2c-193">将其中内容解压缩。</span><span class="sxs-lookup"><span data-stu-id="21a2c-193">Unzip the content.</span></span> <span data-ttu-id="21a2c-194">稍后在本课程中，将使用它。</span><span class="sxs-lookup"><span data-stu-id="21a2c-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="21a2c-195">第 2 章-容器注册表服务</span><span class="sxs-lookup"><span data-stu-id="21a2c-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="21a2c-196">**容器注册表服务**是用来承载你的容器的存储库。</span><span class="sxs-lookup"><span data-stu-id="21a2c-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="21a2c-197">**IoT 中心服务**你将构建和使用在本课程中，指**容器注册表服务**以获取要部署在边缘设备中的容器。</span><span class="sxs-lookup"><span data-stu-id="21a2c-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="21a2c-198">首先，按照这[到 Azure 门户的链接](https://portal.azure.com/)，并使用你的凭据登录。</span><span class="sxs-lookup"><span data-stu-id="21a2c-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="21a2c-199">转到**创建资源**并查找**容器注册表**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![容器注册表](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="21a2c-201">单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="21a2c-202">设置服务安装程序参数：</span><span class="sxs-lookup"><span data-stu-id="21a2c-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="21a2c-203">在此示例中插入一个名称为你的项目，它称**IoTCRegistry**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="21a2c-204">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="21a2c-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="21a2c-205">资源组提供了一种方法来监视、 控制访问，预配，以及管理 Azure 资产的集合计费。</span><span class="sxs-lookup"><span data-stu-id="21a2c-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="21a2c-206">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="21a2c-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="21a2c-207">设置服务的位置。</span><span class="sxs-lookup"><span data-stu-id="21a2c-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="21a2c-208">设置**管理员用户**到**启用**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="21a2c-209">设置**SKU**到**基本**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="21a2c-210">单击**创建**并等待要创建的服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="21a2c-211">后通知您成功创建弹出通知*容器注册表*，单击**转到资源**重定向到你的服务页面。</span><span class="sxs-lookup"><span data-stu-id="21a2c-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="21a2c-212">在中*容器注册表*服务页上，单击**访问密钥**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="21a2c-213">请注意 （可以使用在记事本） 的以下参数：</span><span class="sxs-lookup"><span data-stu-id="21a2c-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="21a2c-214">**Login Server**</span><span class="sxs-lookup"><span data-stu-id="21a2c-214">**Login Server**</span></span>
    2. <span data-ttu-id="21a2c-215">**Username**</span><span class="sxs-lookup"><span data-stu-id="21a2c-215">**Username**</span></span>
    3. <span data-ttu-id="21a2c-216">**密码**</span><span class="sxs-lookup"><span data-stu-id="21a2c-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="21a2c-217">第 3 章-IoT 中心服务</span><span class="sxs-lookup"><span data-stu-id="21a2c-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="21a2c-218">现在，你将开始创建和安装你**IoT 中心服务**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="21a2c-219">如果尚未登录，登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="21a2c-220">登录后，单击**创建资源**在左上角，并搜索**IoT 中心**，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![搜索存储帐户](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="21a2c-222">该新页面将提供的说明**存储帐户**服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="21a2c-223">在左下角此提示，请单击**创建**按钮，以创建服务的此实例。</span><span class="sxs-lookup"><span data-stu-id="21a2c-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="21a2c-225">一旦你单击**创建**，将显示一个面板：</span><span class="sxs-lookup"><span data-stu-id="21a2c-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="21a2c-226">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="21a2c-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="21a2c-227">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="21a2c-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="21a2c-228">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="21a2c-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="21a2c-229">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="21a2c-230">选择相应**位置**（在本课程中创建的所有服务之间使用相同的位置）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="21a2c-231">插入所需**名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="21a2c-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="21a2c-232">在页面底部单击**下一步：大小和小数位数**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="21a2c-234">在此页上，选择你**定价和缩放层**（如果这是你第一个 IoT 中心服务实例，免费级别应为可供你）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="21a2c-235">单击**查看 + 创建**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-235">Click on **Review + Create**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="21a2c-237">查看你的设置并单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-237">Review your settings and click on **Create**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="21a2c-239">后通知您成功创建弹出通知*IoT 中心*服务，单击**转到资源**重定向到你的服务页面。</span><span class="sxs-lookup"><span data-stu-id="21a2c-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="21a2c-241">滚动左侧侧面板，直到看到*自动设备管理*，单击**IoT Edge**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="21a2c-243">在右侧显示窗口中，单击**添加 IoT Edge 设备**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="21a2c-244">右侧将显示一个边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="21a2c-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="21a2c-245">在边栏选项卡，提供新设备**设备 ID** （所选的名称）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="21a2c-246">然后，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-246">Then, click **Save**.</span></span> <span data-ttu-id="21a2c-247">*主*并*辅助密钥*将自动生成，如果你有**自动生成**勾选了。</span><span class="sxs-lookup"><span data-stu-id="21a2c-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="21a2c-249">将导航回*IoT Edge 设备*部分中，其中显示在新设备。</span><span class="sxs-lookup"><span data-stu-id="21a2c-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="21a2c-250">单击新设备上 (在红色框下图)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![创建存储实例](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="21a2c-252">上*设备详细信息*页上显示，需要一份**连接字符串**（主键）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="21a2c-254">返回到面板在左侧，并单击*共享访问策略*，若要打开它。</span><span class="sxs-lookup"><span data-stu-id="21a2c-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="21a2c-255">在显示的页面，单击**iothubowner**，和一个边栏选项卡将显示在屏幕的右侧。</span><span class="sxs-lookup"><span data-stu-id="21a2c-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="21a2c-256">请注意 （在你记事本) 上的**连接字符串**（主键），以供以后使用时设置*连接字符串*向你的设备。</span><span class="sxs-lookup"><span data-stu-id="21a2c-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="21a2c-258">第 4 章-设置开发环境</span><span class="sxs-lookup"><span data-stu-id="21a2c-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="21a2c-259">若要创建和部署用于模块*IoT 中心 Edge*，将需要在运行 Windows 10 的开发计算机上安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="21a2c-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="21a2c-260">[适用于 Windows 的 docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，它会要求您创建的帐户，以便能够下载。</span><span class="sxs-lookup"><span data-stu-id="21a2c-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="21a2c-261">[![下载适用于 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="21a2c-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="21a2c-262">Docker 需要*Windows 10 PRO*，*企业 14393*，或*Windows Server 2016 RTM*来运行。</span><span class="sxs-lookup"><span data-stu-id="21a2c-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="21a2c-263">如果正在运行其他版本的 Windows 10，则可以尝试使用 Docker 安装[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="21a2c-264">[Python 3.6](https://www.python.org/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="21a2c-265">[![下载 python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="21a2c-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="21a2c-266">[Visual Studio Code (也称为 VS Code)](https://code.visualstudio.com/download)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="21a2c-267">[![下载 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="21a2c-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="21a2c-268">在安装前面所述的软件之后, 将需要重新启动你的计算机。</span><span class="sxs-lookup"><span data-stu-id="21a2c-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="21a2c-269">第 5 章-设置 Ubuntu 环境</span><span class="sxs-lookup"><span data-stu-id="21a2c-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="21a2c-270">现在，可以设置你的设备转**运行 Ubuntu OS**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="21a2c-271">请按照下面，安装必要的软件，将在板上的将容器部署的步骤操作：</span><span class="sxs-lookup"><span data-stu-id="21a2c-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21a2c-272">应总是置于前面使用的终端命令**sudo**以管理用户身份运行。</span><span class="sxs-lookup"><span data-stu-id="21a2c-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="21a2c-273">即：</span><span class="sxs-lookup"><span data-stu-id="21a2c-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="21a2c-274">打开**Ubuntu 终端**，然后使用以下命令安装**pip**:</span><span class="sxs-lookup"><span data-stu-id="21a2c-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [!提示]<span data-ttu-id="21a2c-275"> 可打开\*终端\*非常轻松地通过使用键盘快捷方式：*\*Ctrl + Alt + T*\*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-275"> You can open \*Terminal* very easily through using the keyboard shortcut: *\*Ctrl + Alt + T*\*.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="21a2c-276">在本章中，您可能会提示您，由*终端*、 权限以使用你的设备存储，以及为你输入**y/n** （是或否）、 类型**y**，然后按**Enter**键，接受。</span><span class="sxs-lookup"><span data-stu-id="21a2c-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="21a2c-277">完成该命令后，使用以下命令安装**curl**:</span><span class="sxs-lookup"><span data-stu-id="21a2c-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="21a2c-278">一次**pip**并**curl**是安装，请使用以下命令安装**IoT Edge 运行时**，这是需要部署并控制在板上的模块：</span><span class="sxs-lookup"><span data-stu-id="21a2c-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="21a2c-279">此时系统会提示打开*运行时配置文件*，以插入**设备连接字符串**，（你在记事本中），记下创建时**IoT 中心服务** ([处的章节 3 步骤 14，](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="21a2c-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="21a2c-280">在终端来打开该文件上运行以下行：</span><span class="sxs-lookup"><span data-stu-id="21a2c-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="21a2c-281">**Config.yaml**文件将显示，以便您进行编辑：</span><span class="sxs-lookup"><span data-stu-id="21a2c-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="21a2c-282">打开此文件后，它可能有些不易理解。</span><span class="sxs-lookup"><span data-stu-id="21a2c-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="21a2c-283">可以编辑此文件中的文本*终端*本身。</span><span class="sxs-lookup"><span data-stu-id="21a2c-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="21a2c-284">使用键盘上的箭头键可滚动的列表中 （您将需要向下一个小的方式滚动），到达行包含":</span><span class="sxs-lookup"><span data-stu-id="21a2c-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="21a2c-285">"**\<添加设备连接字符串 &GT;**"。</span><span class="sxs-lookup"><span data-stu-id="21a2c-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="21a2c-286">替换为行中，**包括括号**，使用**设备连接字符串**，如上文所述。</span><span class="sxs-lookup"><span data-stu-id="21a2c-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="21a2c-287">连接字符串后，在键盘上按**CTRL-X**键保存该文件。</span><span class="sxs-lookup"><span data-stu-id="21a2c-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="21a2c-288">它将请求您确认通过键入**Y**。然后，按**Enter**密钥进行确认。</span><span class="sxs-lookup"><span data-stu-id="21a2c-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="21a2c-289">将返回到常规*终端*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="21a2c-290">这些命令具有所有运行成功后，便会安装**IoT Edge 运行时**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="21a2c-291">初始化后，运行时将从其自身，打开设备的每次，并将一直等待模块从部署在后台**IoT 中心服务**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="21a2c-292">运行以下命令行来初始化*IoT Edge 运行时*:</span><span class="sxs-lookup"><span data-stu-id="21a2c-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="21a2c-293">如果你的.yaml 文件或更高版本的安装程序进行更改，将需要再次运行上述的重新启动行内*终端*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="21a2c-294">检查*IoT Edge 运行时*通过运行以下命令行的状态。</span><span class="sxs-lookup"><span data-stu-id="21a2c-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="21a2c-295">在运行时应显示为状态**处于活动状态 （正在运行）** 绿色文本中。</span><span class="sxs-lookup"><span data-stu-id="21a2c-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="21a2c-296">按**Ctrl + C**键，若要退出该状态页。</span><span class="sxs-lookup"><span data-stu-id="21a2c-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="21a2c-297">你可以验证*IoT Edge 运行时*拉取容器正确通过键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="21a2c-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="21a2c-298">应显示两个 （2） 容器的列表。</span><span class="sxs-lookup"><span data-stu-id="21a2c-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="21a2c-299">这些是由 IoT 中心服务 （edgeAgent 和 edgeHub） 自动创建的默认模块。</span><span class="sxs-lookup"><span data-stu-id="21a2c-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="21a2c-300">一旦您创建和部署你自己的模块，它们将显示在此列表中，默认的下方。</span><span class="sxs-lookup"><span data-stu-id="21a2c-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="21a2c-301">第 6-章安装扩展</span><span class="sxs-lookup"><span data-stu-id="21a2c-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21a2c-302">下一步的几个章节 (6-9) 是要在 Windows 10 计算机上执行。</span><span class="sxs-lookup"><span data-stu-id="21a2c-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="21a2c-303">打开**VS 代码**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="21a2c-304">单击**扩展**（方形） 按钮在左侧栏的 VS Code 中，以打开**扩展面板**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="21a2c-305">搜索并安装，以下扩展 （如下图所示）：</span><span class="sxs-lookup"><span data-stu-id="21a2c-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="21a2c-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="21a2c-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="21a2c-307">Azure IoT 工具包</span><span class="sxs-lookup"><span data-stu-id="21a2c-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="21a2c-308">Docker</span><span class="sxs-lookup"><span data-stu-id="21a2c-308">Docker</span></span>   

    ![创建容器](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="21a2c-310">一旦安装了扩展，关闭并重新打开 VS Code。</span><span class="sxs-lookup"><span data-stu-id="21a2c-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="21a2c-311">使用 VS Code 一次打开，导航到**视图 > 集成的终端**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-311">With VS Code open once more, navigate to **View > Integrated terminal**.</span></span>

6. <span data-ttu-id="21a2c-312">现在，您将安装**Cookiecutter**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="21a2c-313">在终端运行以下 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="21a2c-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示]<span data-ttu-id="21a2c-314"> 如果你遇到问题，使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="21a2c-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="21a2c-315">重新启动 VS Code 中，和/或您的计算机。</span><span class="sxs-lookup"><span data-stu-id="21a2c-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="21a2c-316">它可能需要切换**VS Code 终端**到你已在用于安装 Python，即**Powershell** （尤其是如果您的计算机上已安装的 Python 环境）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="21a2c-317">终端打开后，您会发现终端右侧的下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="21a2c-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="21a2c-318">![创建容器](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="21a2c-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="21a2c-319">请确保**Python**安装路径添加为**环境变量**在计算机上。</span><span class="sxs-lookup"><span data-stu-id="21a2c-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="21a2c-320">Cookiecutter 应该是相同的位置路径的一部分。</span><span class="sxs-lookup"><span data-stu-id="21a2c-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="21a2c-321">请遵循此[环境变量的详细信息的链接](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)，</span><span class="sxs-lookup"><span data-stu-id="21a2c-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="21a2c-322">一次**Cookiecutter**已完成安装，应重新启动你的计算机，以便**Cookiecutter**被识别为您的系统的环境中的命令。</span><span class="sxs-lookup"><span data-stu-id="21a2c-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="21a2c-323">章 7-创建容器解决方案</span><span class="sxs-lookup"><span data-stu-id="21a2c-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="21a2c-324">此时，您需要创建具有该模块，若要推送到容器中，*容器注册表*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="21a2c-325">已推送到容器，将使用*IoT 中心 Edge*服务，以将其部署到你的设备，这运行*IoT Edge 运行时*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="21a2c-326">从 VS Code 中，单击**视图 > 命令面板**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-326">From VS Code, click **View > Command palette**.</span></span>

2. <span data-ttu-id="21a2c-327">在面板中，搜索并运行**Azure IoT Edge:新的 Iot Edge 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="21a2c-328">浏览到想要创建你的解决方案的位置。</span><span class="sxs-lookup"><span data-stu-id="21a2c-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="21a2c-329">按**Enter**键，若要接受的位置。</span><span class="sxs-lookup"><span data-stu-id="21a2c-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="21a2c-330">为你的解决方案名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-330">Give a name to your solution.</span></span> <span data-ttu-id="21a2c-331">按**Enter**密钥，以确认你提供的名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="21a2c-332">现在系统将提示选择你的解决方案模板 framework。</span><span class="sxs-lookup"><span data-stu-id="21a2c-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="21a2c-333">单击**Python 模块**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-333">Click **Python Module**.</span></span> <span data-ttu-id="21a2c-334">按**Enter**密钥，以确认选择此选项。</span><span class="sxs-lookup"><span data-stu-id="21a2c-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="21a2c-335">为你的模块名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-335">Give a name to your module.</span></span> <span data-ttu-id="21a2c-336">按**Enter**密钥，以确认你的模块名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="21a2c-337">请务必记下 （与在记事本) 的模块名称，因为更高版本使用它。</span><span class="sxs-lookup"><span data-stu-id="21a2c-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="21a2c-338">你会注意到预建*Docker 映像存储库*地址将显示在面板上。</span><span class="sxs-lookup"><span data-stu-id="21a2c-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="21a2c-339">它将如下所示：</span><span class="sxs-lookup"><span data-stu-id="21a2c-339">It will look like:</span></span>

    <span data-ttu-id="21a2c-340">**localhost:5000 /-NAME 的模块-**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="21a2c-341">删除**localhost:5000**，并在其位置插入\*容器注册表\***登录服务器**地址，创建时记下**容器注册表服务**([在步骤 8 的第 2 章](#chapter-2---the-container-registry-service))。</span><span class="sxs-lookup"><span data-stu-id="21a2c-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="21a2c-342">按**Enter**密钥，以确认该地址。</span><span class="sxs-lookup"><span data-stu-id="21a2c-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="21a2c-343">此时，将创建包含 Python 模块的模板的解决方案，其结构将显示在**浏览选项卡**，VS Code 中，在屏幕左侧。</span><span class="sxs-lookup"><span data-stu-id="21a2c-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="21a2c-344">如果**浏览选项卡**是未打开，您可以打开它通过单击最顶部的按钮，在左侧栏中。</span><span class="sxs-lookup"><span data-stu-id="21a2c-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![创建容器](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="21a2c-346">本章节中，最后一步是单击，然后打开 **.env 文件**，从**浏览选项卡**，并添加你\*容器注册表\***用户名**并**密码**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="21a2c-347">通过 git，忽略此文件，但有关生成容器，将设置用于访问的凭据**容器注册表服务**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![创建容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="21a2c-349">第 8 章-编辑容器解决方案</span><span class="sxs-lookup"><span data-stu-id="21a2c-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="21a2c-350">现在，您将完成的容器解决方案，通过更新以下文件：</span><span class="sxs-lookup"><span data-stu-id="21a2c-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="21a2c-351">*主要<span></span>.py* python 脚本。</span><span class="sxs-lookup"><span data-stu-id="21a2c-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="21a2c-352">*requirements.txt*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-352">*requirements.txt*.</span></span>
- <span data-ttu-id="21a2c-353">*deployment.template.json*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="21a2c-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="21a2c-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="21a2c-355">然后您将创建*映像*文件夹中，python 脚本用于检查的映像以匹配你*自定义影像模型*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="21a2c-356">最后，您将添加*labels.txt*文件中，以帮助读取您的模型，并*model.pb*文件，它是您的模型。</span><span class="sxs-lookup"><span data-stu-id="21a2c-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="21a2c-357">使用 VS Code 打开，导航到模块文件夹，然后查找名为脚本**主要<span></span>.py**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="21a2c-358">双击将其打开。</span><span class="sxs-lookup"><span data-stu-id="21a2c-358">Double-click to open it.</span></span>

2. <span data-ttu-id="21a2c-359">删除文件的内容并插入以下代码：</span><span class="sxs-lookup"><span data-stu-id="21a2c-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="21a2c-360">打开的文件称为**requirements.txt**，并将其与以下内容：</span><span class="sxs-lookup"><span data-stu-id="21a2c-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="21a2c-361">打开的文件称为**deployment.template.json**，并将其替换其内容的以下准则如下：</span><span class="sxs-lookup"><span data-stu-id="21a2c-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="21a2c-362">由于你将有自己唯一的 JSON 结构，您需要对其进行手动编辑 （而不是复制示例）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="21a2c-363">若要让轻松，请使用下图作为指南。</span><span class="sxs-lookup"><span data-stu-id="21a2c-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="21a2c-364">看起来会对由你掌控，不同的区域，但在**不应更改会突出显示的黄色**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="21a2c-365">**需删除，请使用此部分介绍了突出显示为红色。**</span><span class="sxs-lookup"><span data-stu-id="21a2c-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="21a2c-366">请注意，若要删除正确方括号，并且还可以删除逗号。</span><span class="sxs-lookup"><span data-stu-id="21a2c-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![创建容器](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="21a2c-368">已完成的 JSON 应如图所示 (不过，与你唯一的区别：*用户名/密码/模块名称/模块引用*):</span><span class="sxs-lookup"><span data-stu-id="21a2c-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![创建容器](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="21a2c-370">打开的文件称为**Dockerfile.amd64**，并将其与以下内容：</span><span class="sxs-lookup"><span data-stu-id="21a2c-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="21a2c-371">右键单击下方的文件夹**模块**(它将具有以前; 提供的名称在示例中进一步向下，它调用*pythonmodule*)，并单击**新文件夹**.</span><span class="sxs-lookup"><span data-stu-id="21a2c-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="21a2c-372">将文件夹命名为**映像**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="21a2c-373">在文件夹中，添加包含鼠标或键盘的一些图像。</span><span class="sxs-lookup"><span data-stu-id="21a2c-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="21a2c-374">这些将 Tensorflow 模型要分析的映像。</span><span class="sxs-lookup"><span data-stu-id="21a2c-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="21a2c-375">如果使用自己的模型，您需要更改此设置以反映你自己的模型数据。</span><span class="sxs-lookup"><span data-stu-id="21a2c-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="21a2c-376">您现在需要检索**labels.txt**并**model.pb**模型文件夹，你以前下载的文件 (或从你自己创建**自定义影像服务**)，在[第 1 章](#chapter-1---retrieve-the-custom-vision-model)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="21a2c-377">这些文件后，将它们放在你的解决方案，以及其他文件。</span><span class="sxs-lookup"><span data-stu-id="21a2c-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="21a2c-378">最终结果应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="21a2c-378">The final result should look like the image below:</span></span>

    ![创建容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="21a2c-380">第 9 章 — 包的容器解决方案</span><span class="sxs-lookup"><span data-stu-id="21a2c-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="21a2c-381">你现已准备好你的文件"包"作为容器并将其推送到您**Azure 容器注册表**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="21a2c-382">在 VS Code 中打开*集成终端*(**视图 > 集成终端 / CTRL + '**)，并使用登录到下面的代码行**Docker** (替换以下值命令的凭据与你**Azure 容器注册表 (ACR)**):</span><span class="sxs-lookup"><span data-stu-id="21a2c-382">Within VS Code, open the *Integrated Terminal* (**View > Integrated Terminal / CTRL + \`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="21a2c-383">右键单击该文件**deployment.template.json**，然后单击**生成 IoT Edge 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="21a2c-384">此生成过程需要花费很长时间 （具体取决于你的设备），因此请准备好等待。</span><span class="sxs-lookup"><span data-stu-id="21a2c-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="21a2c-385">生成过程完成后， **deployment.json**文件将创建一个名为的新文件夹内**config**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![创建部署](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="21a2c-387">打开**命令面板**同样，并搜索**Azure:登录**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="21a2c-388">按照提示使用 Azure 帐户凭据;VS Code 将为您提供的选项*复制并打开*，这会将复制你很快将需要并打开默认 web 浏览器的设备代码。</span><span class="sxs-lookup"><span data-stu-id="21a2c-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="21a2c-389">当要求时，将粘贴的设备代码进行身份验证你的计算机。</span><span class="sxs-lookup"><span data-stu-id="21a2c-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![复制并打开](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="21a2c-391">一旦登录后，在您将注意到，在底部的一端*浏览*面板中，一个名为的新部分**Azure IoT 中心设备**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="21a2c-392">单击此部分，以将其展开。</span><span class="sxs-lookup"><span data-stu-id="21a2c-392">Click this section to expand it.</span></span>

    ![边缘设备](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="21a2c-394">如果你的设备不是此处，您将需要右键单击*Azure IoT 中心设备*，然后单击**Set IoT Hub Connection String**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="21a2c-395">然后会看到**命令面板**（在 VS Code 的顶部），将提示你输入你*连接字符串*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="21a2c-396">这是*连接字符串*结束时记下[第 3 章](#chapter-3---the-iot-hub-service)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="21a2c-397">按**Enter**键，一旦复制中的字符串。</span><span class="sxs-lookup"><span data-stu-id="21a2c-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="21a2c-398">你的设备应加载和显示。</span><span class="sxs-lookup"><span data-stu-id="21a2c-398">Your device should load, and appear.</span></span> <span data-ttu-id="21a2c-399">右键单击设备名称，然后依次，**的单个设备创建部署**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![创建部署](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="21a2c-401">你将获得*文件资源管理器*提示符下，您可以导航到**config**文件夹，，然后选择**deployment.json**文件。</span><span class="sxs-lookup"><span data-stu-id="21a2c-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="21a2c-402">该文件处于选定状态，单击**选择边缘部署清单**按钮。</span><span class="sxs-lookup"><span data-stu-id="21a2c-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![创建部署](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="21a2c-404">此时您已提供你**IoT 中心服务**与清单即可部署你的容器，为模块，从你**Azure 容器注册表**，从而有效地将其部署到你的设备。</span><span class="sxs-lookup"><span data-stu-id="21a2c-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="21a2c-405">若要查看从你的设备发送到 IoT 中心的消息，再次右键单击设备名称在**Azure IoT 中心设备**部分中，在**资源管理器**面板，并单击**启动监视D2C 消息**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="21a2c-406">从你的设备发送的消息应显示在 VS 终端。</span><span class="sxs-lookup"><span data-stu-id="21a2c-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="21a2c-407">耐心等待，因为这可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="21a2c-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="21a2c-408">请参阅下一章中的进行调试和检查部署是否成功。</span><span class="sxs-lookup"><span data-stu-id="21a2c-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="21a2c-409">现在，此模块将循环访问中的映像之间**映像**文件夹和分析，每次迭代。</span><span class="sxs-lookup"><span data-stu-id="21a2c-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="21a2c-410">这是很明显只是演示如何获取要在 IoT Edge 设备环境中工作的基本机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="21a2c-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="21a2c-411">若要扩展此示例中的功能，可以继续以下几种方式。</span><span class="sxs-lookup"><span data-stu-id="21a2c-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="21a2c-412">一种方法可能包括一些代码中的容器，用于捕获从网络摄像头，连接到设备，然后将映像保存在 images 文件夹中的照片。</span><span class="sxs-lookup"><span data-stu-id="21a2c-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="21a2c-413">另一种方法可以将复制映像 IoT 设备到容器。</span><span class="sxs-lookup"><span data-stu-id="21a2c-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="21a2c-414">一个实用方法可执行此操作是在 IoT 设备 （可能是一个小型应用无法执行该作业，如果想要自动执行此过程） 的终端中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="21a2c-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="21a2c-415">可以通过从存储文件的文件夹位置手动运行它来测试此命令：</span><span class="sxs-lookup"><span data-stu-id="21a2c-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="21a2c-416">第 10 章 — 调试 IoT Edge 运行时</span><span class="sxs-lookup"><span data-stu-id="21a2c-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="21a2c-417">以下是命令行和技巧，以帮助您监视和调试的消息传递活动的列表*IoT Edge 运行时*，从你**Ubuntu 设备**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="21a2c-418">检查*IoT Edge 运行时*通过运行以下命令行的状态：</span><span class="sxs-lookup"><span data-stu-id="21a2c-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="21a2c-419">请记住，按**Ctrl + C**以完成查看状态。</span><span class="sxs-lookup"><span data-stu-id="21a2c-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="21a2c-420">列出当前已部署的容器。</span><span class="sxs-lookup"><span data-stu-id="21a2c-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="21a2c-421">如果*IoT 中心服务*是否容器成功部署，它们将显示通过运行以下命令行：</span><span class="sxs-lookup"><span data-stu-id="21a2c-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="21a2c-422">或</span><span class="sxs-lookup"><span data-stu-id="21a2c-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="21a2c-423">以上是一种检查是否在模块是否已成功部署，因为它将出现在列表中; 很好方法否则将**仅**请参阅*edgeHub*并*edgeAgent*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="21a2c-424">若要显示容器的代码日志，请运行以下命令行：</span><span class="sxs-lookup"><span data-stu-id="21a2c-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="21a2c-425">**用于管理 IoT Edge 运行时的有用命令：**</span><span class="sxs-lookup"><span data-stu-id="21a2c-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="21a2c-426">若要删除所有容器主机中：</span><span class="sxs-lookup"><span data-stu-id="21a2c-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="21a2c-427">若要停止*IoT Edge 运行时*:</span><span class="sxs-lookup"><span data-stu-id="21a2c-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="21a2c-428">章 11-创建表服务</span><span class="sxs-lookup"><span data-stu-id="21a2c-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="21a2c-429">导航回到你的 Azure 门户，其中将创建 Azure 表服务，通过创建存储资源。</span><span class="sxs-lookup"><span data-stu-id="21a2c-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="21a2c-430">如果尚未登录，登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="21a2c-431">登录后，单击**创建资源**，在左上角，并搜索**存储帐户**，然后按**Enter**键，若要开始搜索。</span><span class="sxs-lookup"><span data-stu-id="21a2c-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="21a2c-432">一旦它已出现，请单击**存储帐户-blob、 文件、 表、 队列**从列表中。</span><span class="sxs-lookup"><span data-stu-id="21a2c-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜索存储帐户](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="21a2c-434">该新页面将提供的说明**存储帐户**服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="21a2c-435">在左下角此提示，请单击**创建**按钮，以创建服务的此实例。</span><span class="sxs-lookup"><span data-stu-id="21a2c-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![创建存储实例](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="21a2c-437">一旦你单击**创建**，将显示一个面板：</span><span class="sxs-lookup"><span data-stu-id="21a2c-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="21a2c-438">插入所需**名称**此服务实例 (*必须全部小写*)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="21a2c-439">有关**部署模型**，单击**资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="21a2c-440">有关**帐户类型**，使用下拉列表菜单，单击**存储 (常规用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="21a2c-441">单击相应**位置**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="21a2c-442">有关**复制**下拉菜单中，单击**读取-访问-异地冗余存储 (RA-GRS)**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="21a2c-443">有关**性能**，单击**标准**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="21a2c-444">内**需要安全传输**部分中，单击**禁用**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="21a2c-445">从**订阅**下拉菜单中，单击相应的订阅。</span><span class="sxs-lookup"><span data-stu-id="21a2c-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="21a2c-446">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="21a2c-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="21a2c-447">资源组提供了一种方法来监视、 控制访问，预配，以及管理 Azure 资产的集合计费。</span><span class="sxs-lookup"><span data-stu-id="21a2c-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="21a2c-448">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="21a2c-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="21a2c-449">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="21a2c-450">将保留**虚拟网络**作为**禁用**，如果这是为你的选项。</span><span class="sxs-lookup"><span data-stu-id="21a2c-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="21a2c-451">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="21a2c-451">Click **Create**.</span></span>

        ![填写存储详细信息](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="21a2c-453">一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="21a2c-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="21a2c-454">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="21a2c-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="21a2c-455">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="21a2c-455">Click on the notifications to explore your new Service instance.</span></span>

    ![新的存储通知](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="21a2c-457">单击**转到资源**按钮中的通知，和你将转到新的存储服务实例概述页。</span><span class="sxs-lookup"><span data-stu-id="21a2c-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![转到资源](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="21a2c-459">从概述页上，到右侧，单击**表**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![表](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="21a2c-461">在右侧面板将更改为显示**表服务**其中所需添加一个新表的信息。</span><span class="sxs-lookup"><span data-stu-id="21a2c-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="21a2c-462">执行此操作通过单击 **+ 表**左上角的按钮。</span><span class="sxs-lookup"><span data-stu-id="21a2c-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![打开表](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="21a2c-464">将显示一个新页面，其中你需要输入**表名称**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="21a2c-465">这是将用于引用应用程序中后面的章节 （创建函数应用和 Power BI） 的数据的名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="21a2c-466">插入**IoTMessages**作为名称 （可以选择你自己，只需记住它稍后在本文档中使用时），单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="21a2c-467">一旦创建新表后，你将能够看到它在**表服务**页 （底部）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![创建新表](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="21a2c-469">现在，单击**访问密钥**，并采取一份**存储帐户名称**并**密钥**（使用在记事本），您将使用这些值更高版本中此课程中，创建时**Azure 函数应用**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![创建新表](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="21a2c-471">同样，在左侧使用面板滚动到*表服务*部分，然后单击**表**(或**浏览表**，较新的门户网站中)，并采取一份**表 URL** （使用在记事本）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="21a2c-472">链接到您的表时，将稍后在本课程中，使用此值您**Power BI**应用程序。</span><span class="sxs-lookup"><span data-stu-id="21a2c-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![创建新表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="21a2c-474">第 12 章-完成 Azure 表</span><span class="sxs-lookup"><span data-stu-id="21a2c-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="21a2c-475">现在，你**表服务**存储帐户已被安装程序，即可将数据添加到它，将用于存储和检索信息。</span><span class="sxs-lookup"><span data-stu-id="21a2c-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="21a2c-476">编辑你的表，可通过完成**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="21a2c-477">打开**Visual Studio** (**不**Visual Studio Code)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="21a2c-478">从菜单中，单击**视图 > 云资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-478">From the menu, click **View > Cloud Explorer**.</span></span>

    ![打开 cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="21a2c-480">**云资源管理器**以停靠项 （如加载可能需要时间，则请耐心等待，） 将打开。</span><span class="sxs-lookup"><span data-stu-id="21a2c-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="21a2c-481">如果用于创建订阅你*存储帐户*不可见，请确保您具有：</span><span class="sxs-lookup"><span data-stu-id="21a2c-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="21a2c-482">登录到 Azure 门户使用的同一个帐户。</span><span class="sxs-lookup"><span data-stu-id="21a2c-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="21a2c-483">（您可能需要从你的帐户设置应用筛选器） 在帐户管理页上选择你的订阅：</span><span class="sxs-lookup"><span data-stu-id="21a2c-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![查找订阅](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="21a2c-485">将显示在 Azure 云服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="21a2c-486">查找**存储帐户**，然后单击箭头以展开你的帐户的左侧。</span><span class="sxs-lookup"><span data-stu-id="21a2c-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![打开存储帐户](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="21a2c-488">展开后，新创建**存储帐户**应可用。</span><span class="sxs-lookup"><span data-stu-id="21a2c-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="21a2c-489">单击你的存储，左侧的箭头，然后后，已展开，找到**表**，然后单击箭头旁边的以显示**表**在最后一章中创建。</span><span class="sxs-lookup"><span data-stu-id="21a2c-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="21a2c-490">双击您**表**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="21a2c-491">将在 Visual Studio 窗口的中心中打开您的表。</span><span class="sxs-lookup"><span data-stu-id="21a2c-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="21a2c-492">单击与表图标 **+** （加上） 在其上。</span><span class="sxs-lookup"><span data-stu-id="21a2c-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![添加新表](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="21a2c-494">你能够将出现一个窗口提示*添加实体*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="21a2c-495">您将创建一个实体，它将具有三个属性也是如此。</span><span class="sxs-lookup"><span data-stu-id="21a2c-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="21a2c-496">您会注意*PartitionKey*并*RowKey*已提供了，因为需要使用这些表以查找你的数据。</span><span class="sxs-lookup"><span data-stu-id="21a2c-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![分区键和行键](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="21a2c-498">更新以下值：</span><span class="sxs-lookup"><span data-stu-id="21a2c-498">Update the following values:</span></span>

    - <span data-ttu-id="21a2c-499">名称：**PartitionKey**，值：**PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="21a2c-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="21a2c-500">名称：**RowKey**，值：**RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="21a2c-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="21a2c-501">然后，单击**将属性添加**(到左下角*添加实体*窗口)，并添加以下属性：</span><span class="sxs-lookup"><span data-stu-id="21a2c-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="21a2c-502">**MessageContent**，作为*字符串*，将值保留为空。</span><span class="sxs-lookup"><span data-stu-id="21a2c-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="21a2c-503">您的表应与下图中的一个匹配：</span><span class="sxs-lookup"><span data-stu-id="21a2c-503">Your table should match the one in the image below:</span></span>

    ![添加正确的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="21a2c-505">实体具有行键中的数字 1 的原因是因为你可能想要添加更多消息，你希望试验进一步与此课程。</span><span class="sxs-lookup"><span data-stu-id="21a2c-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="21a2c-506">单击**确定**完成之后。</span><span class="sxs-lookup"><span data-stu-id="21a2c-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="21a2c-507">您的表现可供使用。</span><span class="sxs-lookup"><span data-stu-id="21a2c-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="21a2c-508">章 13-创建 Azure Function App</span><span class="sxs-lookup"><span data-stu-id="21a2c-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="21a2c-509">现在即可创建*Azure Function App*，这将调用*IoT 中心服务*存储*IoT Edge*设备中的消息**表**服务，在上一章中创建。</span><span class="sxs-lookup"><span data-stu-id="21a2c-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="21a2c-510">首先，需要创建一个文件，将允许您的 Azure 函数以加载所需的库。</span><span class="sxs-lookup"><span data-stu-id="21a2c-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="21a2c-511">打开**记事本**(按*Windows 键*，然后键入*记事本*)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![打开记事本](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="21a2c-513">使用记事本打开，将插入到其中的以下 JSON 结构。</span><span class="sxs-lookup"><span data-stu-id="21a2c-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="21a2c-514">完成后，将其保存为您的桌面上**project.json**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="21a2c-515">此文件定义函数将使用的库。</span><span class="sxs-lookup"><span data-stu-id="21a2c-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="21a2c-516">如果已使用 NuGet，它会很熟悉。</span><span class="sxs-lookup"><span data-stu-id="21a2c-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="21a2c-517">很重要的命名正确。请确保它**不具有.txt**文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="21a2c-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="21a2c-518">有关参考，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="21a2c-518">See below for reference:</span></span>
    >
    > ![保存的 JSON](images/AzureLabs-Lab313-52.png)

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

3.  <span data-ttu-id="21a2c-520">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="21a2c-521">后记录，单击**创建资源**在左上角，并搜索**Function App**，然后按**Enter**键，搜索。</span><span class="sxs-lookup"><span data-stu-id="21a2c-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="21a2c-522">单击*Function App*从结果中，打开一个新的面板。</span><span class="sxs-lookup"><span data-stu-id="21a2c-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![搜索函数应用](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="21a2c-524">新的面板将提供的说明**Function App**服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="21a2c-525">在左下角此面板中，单击**创建**按钮，以创建与此关联服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![function app 实例](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="21a2c-527">一旦你单击**创建**，填写以下：</span><span class="sxs-lookup"><span data-stu-id="21a2c-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="21a2c-528">有关**应用名称**，插入此服务实例所需的名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="21a2c-529">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="21a2c-530">选择定价层适合你，如果这是首次创建**Function App 服务**，应可供你免费层。</span><span class="sxs-lookup"><span data-stu-id="21a2c-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="21a2c-531">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="21a2c-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="21a2c-532">资源组提供了一种方法来监视、 控制访问，预配，以及管理 Azure 资产的集合计费。</span><span class="sxs-lookup"><span data-stu-id="21a2c-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="21a2c-533">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="21a2c-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="21a2c-534">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="21a2c-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="21a2c-535">有关**OS**，单击 Windows，因为这是预期的平台。</span><span class="sxs-lookup"><span data-stu-id="21a2c-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="21a2c-536">选择**托管计划**(使用本教程**消耗计划**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="21a2c-537">选择**位置**（上一步中选择与已生成的存储相同的位置）</span><span class="sxs-lookup"><span data-stu-id="21a2c-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="21a2c-538">有关**存储**部分中，**必须选择在上一步中创建的存储服务**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="21a2c-539">您不需要*Application Insights*在此应用中，所以请随意将其留**关闭**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="21a2c-540">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="21a2c-540">Click **Create**.</span></span>

        ![创建新的实例](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="21a2c-542">一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="21a2c-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="21a2c-543">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="21a2c-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![新的通知](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="21a2c-545">部署成功后单击该通知 （已完成）。</span><span class="sxs-lookup"><span data-stu-id="21a2c-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="21a2c-546">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="21a2c-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![转到资源](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="21a2c-548">在左侧和右侧的新面板，单击 **+** （加号） 旁边的图标*函数*，以创建新的函数。</span><span class="sxs-lookup"><span data-stu-id="21a2c-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![添加新函数](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="21a2c-550">在中间面板**函数**创建窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="21a2c-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="21a2c-551">此外，向下滚动并单击**自定义函数**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-551">Scroll down further, and click on **Custom function**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="21a2c-553">下一个页面，直到找到中向下的滚动**IoT 中心 （事件中心）**，然后单击它。</span><span class="sxs-lookup"><span data-stu-id="21a2c-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="21a2c-555">在中**IoT 中心 （事件中心）** 边栏选项卡，将**语言**到**C#** ，然后单击**新**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="21a2c-557">在窗口中将出现，请确保**IoT 中心**处于选中状态和名称*IoT 中心*字段对应的名称与你*IoT 中心服务*必须以前创建 ([在步骤 8 的第 3 章](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="21a2c-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="21a2c-558">然后单击**选择**按钮。</span><span class="sxs-lookup"><span data-stu-id="21a2c-558">Then click the **Select** button.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="21a2c-560">重新**IoT 中心 （事件中心）** 边栏选项卡上，单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="21a2c-562">你将重定向到在函数编辑器。</span><span class="sxs-lookup"><span data-stu-id="21a2c-562">You will be redirected to the function editor.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="21a2c-564">删除在其中的所有代码并使用以下代码替换它：</span><span class="sxs-lookup"><span data-stu-id="21a2c-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="21a2c-565">更改以下变量，以便它们对应于相应的值 (**表**并**存储**值，从[步骤 11 到 13，分别，第 11 章](#chapter-11---create-table-service))，将在中找到你**存储帐户**:</span><span class="sxs-lookup"><span data-stu-id="21a2c-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="21a2c-566">**tableName**，名称为你**表**位于你**存储帐户**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="21a2c-567">**tableURL**，url 为你**表**位于你**存储帐户**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="21a2c-568">**storageAccountName**，具有的名称相对应的值的名称与你**存储帐户**名称。</span><span class="sxs-lookup"><span data-stu-id="21a2c-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="21a2c-569">**storageAccountKey**，已在具有以前创建的存储服务中获取的密钥。</span><span class="sxs-lookup"><span data-stu-id="21a2c-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="21a2c-571">使用的代码中的位置，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="21a2c-572">接下来，单击 **\<** （箭头） 图标，在页面的右侧。</span><span class="sxs-lookup"><span data-stu-id="21a2c-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="21a2c-574">一个面板，将从右侧滑中。</span><span class="sxs-lookup"><span data-stu-id="21a2c-574">A panel will slide in from the right.</span></span> <span data-ttu-id="21a2c-575">在该面板中，单击**上传**，和一个*文件浏览器*将出现。</span><span class="sxs-lookup"><span data-stu-id="21a2c-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="21a2c-576">导航到，然后单击， **project.json**中创建的文件**记事本**以前，然后单击**打开**按钮。</span><span class="sxs-lookup"><span data-stu-id="21a2c-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="21a2c-577">此文件定义函数将使用的库。</span><span class="sxs-lookup"><span data-stu-id="21a2c-577">This file defines the libraries that your function will use.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="21a2c-579">当完成上传文件时，它会在右侧面板中显示。</span><span class="sxs-lookup"><span data-stu-id="21a2c-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="21a2c-580">单击它即可打开它内**函数**编辑器。</span><span class="sxs-lookup"><span data-stu-id="21a2c-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="21a2c-581">它必须看起来**完全**的下一步的映像相同。</span><span class="sxs-lookup"><span data-stu-id="21a2c-581">It must look **exactly** the same as the next image.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="21a2c-583">现在那会很不错，若要测试你的函数的功能，若要将该消息存储在你*表*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="21a2c-584">在窗口右上角，单击**测试**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-584">On the top right side of the window, click on **Test**.</span></span>

    ![自定义函数](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="21a2c-586">插入一条消息上**请求正文**，在上图中的，然后单击中所示**运行**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="21a2c-587">该函数将运行，并显示结果状态 (您将注意到绿色**状态 202 已接受**上面*输出*窗口中，这意味着它已成功调用):</span><span class="sxs-lookup"><span data-stu-id="21a2c-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![输出结果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="21a2c-589">第 14 章 — 查看活动消息</span><span class="sxs-lookup"><span data-stu-id="21a2c-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="21a2c-590">如果现在打开 Visual Studio (**不**Visual Studio Code)，可以可视化您测试的消息结果，因为它将存储在*MessageContent*区域的字符串。</span><span class="sxs-lookup"><span data-stu-id="21a2c-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![自定义函数](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="21a2c-592">使用表服务和 Function App 中的位置，在 Ubuntu 设备的消息将出现在你*IoTMessages*表。</span><span class="sxs-lookup"><span data-stu-id="21a2c-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="21a2c-593">如果尚未运行，再次启动你的设备，您将能够看到的结果消息从设备和模块，在表中，使用 Visual Studio*云资源管理器*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![实现数据可视化效果](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="21a2c-595">第 15 章-Power BI 安装程序</span><span class="sxs-lookup"><span data-stu-id="21a2c-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="21a2c-596">若要从 IOT 设备将在安装程序将数据可视化**Power BI** （桌面版），以收集数据的*表*刚创建的服务。</span><span class="sxs-lookup"><span data-stu-id="21a2c-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="21a2c-597">*HoloLens*版本的 Power BI 然后会使用该数据的结果可视化。</span><span class="sxs-lookup"><span data-stu-id="21a2c-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="21a2c-598">打开 Windows 10 上的 Microsoft Store 并搜索**Power BI Desktop**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="21a2c-600">下载应用程序。</span><span class="sxs-lookup"><span data-stu-id="21a2c-600">Download the application.</span></span> <span data-ttu-id="21a2c-601">完成下载后，请将其打开。</span><span class="sxs-lookup"><span data-stu-id="21a2c-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="21a2c-602">登录到*Power BI*与你**Microsoft 365 帐户**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="21a2c-603">你可能会重定向到浏览器中，若要注册。</span><span class="sxs-lookup"><span data-stu-id="21a2c-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="21a2c-604">一旦您注册了，请返回到 Power BI 应用，并再次登录。</span><span class="sxs-lookup"><span data-stu-id="21a2c-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="21a2c-605">单击**获取数据**，然后单击**更多...**.</span><span class="sxs-lookup"><span data-stu-id="21a2c-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="21a2c-607">单击**Azure**， **Azure 表存储**，然后单击**Connect**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="21a2c-609">系统会提示要插入**表 URL**先前收集的 ([在步骤 13 第 11 章](#chapter-11---create-table-service))，创建表服务时。</span><span class="sxs-lookup"><span data-stu-id="21a2c-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="21a2c-610">插入 URL 后, 删除引用表"子文件夹"（这是 IoTMessages，本课程中） 的路径的一部分。</span><span class="sxs-lookup"><span data-stu-id="21a2c-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="21a2c-611">最终结果应如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="21a2c-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="21a2c-612">然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="21a2c-614">系统会提示要插入**存储密钥**记下 ([在第 11 章第 11 步](#chapter-11---create-table-service)) 早期创建在表存储时。</span><span class="sxs-lookup"><span data-stu-id="21a2c-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="21a2c-615">然后单击**Connect**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="21a2c-617">一个**导航器面板**将显示，选中你的表旁边的框，然后单击**负载**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="21a2c-619">现在在 Power BI 上加载您的表，但它需要一个查询来显示中它的值。</span><span class="sxs-lookup"><span data-stu-id="21a2c-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="21a2c-620">为此，请右键单击表名称中位于**字段面板**在屏幕的右侧。</span><span class="sxs-lookup"><span data-stu-id="21a2c-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="21a2c-621">然后单击**编辑查询**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="21a2c-623">一个**Power Query 编辑器**以显示您的表的新窗口将打开。</span><span class="sxs-lookup"><span data-stu-id="21a2c-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="21a2c-624">单击单词**记录**内*内容*表，可视化存储的内容的列。</span><span class="sxs-lookup"><span data-stu-id="21a2c-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="21a2c-626">单击**Into 表**，在窗口的左上方。</span><span class="sxs-lookup"><span data-stu-id="21a2c-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="21a2c-628">单击**关闭并应用**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="21a2c-630">在加载查询，完成**字段面板**，在屏幕的右侧，勾选对应参数的框**名称**并**值**到可视化**MessageContent**列的内容。</span><span class="sxs-lookup"><span data-stu-id="21a2c-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="21a2c-632">单击**蓝色磁盘图标**在左上角的窗口在所选的文件夹中保存工作。</span><span class="sxs-lookup"><span data-stu-id="21a2c-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="21a2c-634">现在可以单击发布按钮以将您的表上传到你的工作区。</span><span class="sxs-lookup"><span data-stu-id="21a2c-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="21a2c-635">出现提示时，单击**我的工作区**然后单击*选择*。</span><span class="sxs-lookup"><span data-stu-id="21a2c-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="21a2c-636">等待显示成功提交的结果。</span><span class="sxs-lookup"><span data-stu-id="21a2c-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="21a2c-639">以下章节都是特定的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="21a2c-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="21a2c-640">Power BI 当前不提供为沉浸式应用程序，但可以在 Windows 混合现实门户 （也称为 Cliff 房屋） 中运行的桌面版本通过桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="21a2c-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="21a2c-641">第 16 章 — 在 HoloLens 上显示 Power BI 数据</span><span class="sxs-lookup"><span data-stu-id="21a2c-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="21a2c-642">在你 HoloLens 登录**Microsoft Store**，通过点击应用程序列表中对应的图标。</span><span class="sxs-lookup"><span data-stu-id="21a2c-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="21a2c-644">搜索，然后下载**Power BI**应用程序。</span><span class="sxs-lookup"><span data-stu-id="21a2c-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="21a2c-646">启动**Power BI**从您的应用程序的列表。</span><span class="sxs-lookup"><span data-stu-id="21a2c-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="21a2c-647">**Power BI**可能会要求你登录到你**Microsoft 365 帐户**。</span><span class="sxs-lookup"><span data-stu-id="21a2c-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="21a2c-648">一次在应用程序，在工作区应显示默认情况下下, 图中所示。</span><span class="sxs-lookup"><span data-stu-id="21a2c-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="21a2c-649">如果不会发生，只需单击窗口左侧的工作区图标。</span><span class="sxs-lookup"><span data-stu-id="21a2c-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="21a2c-651">在完成 IoT 中心应用程序</span><span class="sxs-lookup"><span data-stu-id="21a2c-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="21a2c-652">祝贺您，您已成功创建 IoT 中心服务，使用模拟的虚拟机 Edge 设备。</span><span class="sxs-lookup"><span data-stu-id="21a2c-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="21a2c-653">你的设备可以进行通信机器学习模型到 Azure 表服务，利用 Azure Function App，这是读取到 Power BI，Microsoft HoloLens 中可视化的结果。</span><span class="sxs-lookup"><span data-stu-id="21a2c-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="21a2c-655">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="21a2c-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="21a2c-656">练习 1</span><span class="sxs-lookup"><span data-stu-id="21a2c-656">Exercise 1</span></span>

<span data-ttu-id="21a2c-657">展开表中存储的消息传递结构并将其显示为图形。</span><span class="sxs-lookup"><span data-stu-id="21a2c-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="21a2c-658">你可能想要收集更多数据并将其存储在同一个表，以更高版本显示。</span><span class="sxs-lookup"><span data-stu-id="21a2c-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="21a2c-659">练习 2</span><span class="sxs-lookup"><span data-stu-id="21a2c-659">Exercise 2</span></span>

<span data-ttu-id="21a2c-660">创建一个附加"相机捕捉"模块来部署 IoT 板上，以便它可以捕获映像通过摄像机来对其进行分析。</span><span class="sxs-lookup"><span data-stu-id="21a2c-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
