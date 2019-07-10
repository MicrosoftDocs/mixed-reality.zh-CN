---
title: MR 和 Azure 307-机器学习
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 机器学习工作室。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 机器学习，机器学习，机器学习工作室，hololens，沉浸式、 vr
ms.openlocfilehash: 89d9758dedb6a2389644dda887bfadf5b28f6dd2
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694546"
---
>[!NOTE]
><span data-ttu-id="8a9f5-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8a9f5-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8a9f5-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8a9f5-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8a9f5-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8a9f5-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="8a9f5-110">MR 和 Azure 307:机器学习</span><span class="sxs-lookup"><span data-stu-id="8a9f5-110">MR and Azure 307: Machine learning</span></span>

![最终产品-启动](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="8a9f5-112">在本课程中，您将学习如何将机器学习 (ML) 功能添加到使用 Azure 机器学习工作室的混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="8a9f5-113">*Azure 机器学习工作室*是 Microsoft 服务，开发人员提供了大量的机器学习算法，它可以帮助数据输入、 输出、 准备和可视化效果。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="8a9f5-114">这些组件，就能开发预测分析试验、 循环访问它，并使用它来训练模型。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="8a9f5-115">以下培训，可以使您的模型操作在 Azure 云中，因此，然后新数据评分。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="8a9f5-116">有关详细信息，请访问[Azure 机器学习工作室页](https://azure.microsoft.com/en-au/services/machine-learning-studio/)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="8a9f5-117">已完成本课程，将具有混合的现实耳机沉浸式应用程序中，并将已了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="8a9f5-118">提供对销售数据的表*Azure 机器学习工作室*门户中，并设计一种算法来预测未来的销售额的热门项目。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="8a9f5-119">创建**Unity 项目**，其可接收和解释预测从机器学习服务的数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="8a9f5-120">中直观地显示断言而数据**Unity 项目**，通过架子上提供的最受欢迎的销售项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="8a9f5-121">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="8a9f5-122">本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="8a9f5-123">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="8a9f5-124">此过程是不直接涉及任何其他混合现实实验室的自包含的教程。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="8a9f5-125">设备支持</span><span class="sxs-lookup"><span data-stu-id="8a9f5-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8a9f5-126">课程</span><span class="sxs-lookup"><span data-stu-id="8a9f5-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8a9f5-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8a9f5-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8a9f5-128"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="8a9f5-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8a9f5-129">MR 和 Azure 307:机器学习</span><span class="sxs-lookup"><span data-stu-id="8a9f5-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="8a9f5-130">✔️</span><span class="sxs-lookup"><span data-stu-id="8a9f5-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8a9f5-131">✔️</span><span class="sxs-lookup"><span data-stu-id="8a9f5-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="8a9f5-132">尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="8a9f5-133">按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="8a9f5-134">使用 HoloLens，您可能注意到某些 echo 语音捕获过程。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a9f5-135">先决条件</span><span class="sxs-lookup"><span data-stu-id="8a9f5-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="8a9f5-136">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="8a9f5-137">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="8a9f5-138">你可以随意使用最新的软件，如中所列[安装工具一文](install-the-tools.md)，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="8a9f5-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="8a9f5-139">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="8a9f5-140">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="8a9f5-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="8a9f5-141">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="8a9f5-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8a9f5-142">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="8a9f5-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8a9f5-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="8a9f5-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8a9f5-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8a9f5-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="8a9f5-145">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="8a9f5-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="8a9f5-146">Internet 访问的 Azure 设置和机器学习数据检索</span><span class="sxs-lookup"><span data-stu-id="8a9f5-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8a9f5-147">开始之前</span><span class="sxs-lookup"><span data-stu-id="8a9f5-147">Before you start</span></span>

<span data-ttu-id="8a9f5-148">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="8a9f5-149">第 1 章-设置 Azure 存储帐户</span><span class="sxs-lookup"><span data-stu-id="8a9f5-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="8a9f5-150">若要使用 Azure 翻译 API，你需要配置要成为可用于应用程序的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="8a9f5-151">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8a9f5-152">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="8a9f5-153">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="8a9f5-154">你登录后，单击**存储帐户**在左侧菜单中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="8a9f5-156">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="8a9f5-157">上**存储帐户**选项卡上，单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="8a9f5-159">在中**创建存储帐户**面板：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="8a9f5-160">插入**名称**对于你的帐户，请注意此字段仅接受数字和小写字母。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="8a9f5-161">有关**部署模型**选择**资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="8a9f5-162">有关**帐户类型**，选择**存储 (常规用途 v1)** 。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="8a9f5-163">有关**性能**，选择**标准**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="8a9f5-164">有关**复制**选择**读取-访问-异地冗余存储 (RA-GRS)** 。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="8a9f5-165">将保留**需要安全传输**作为**禁用**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="8a9f5-166">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="8a9f5-167">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8a9f5-168">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8a9f5-169">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="8a9f5-170">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="8a9f5-171">确定**位置**为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="8a9f5-172">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="8a9f5-173">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="8a9f5-174">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="8a9f5-176">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="8a9f5-177">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="8a9f5-179">第 2 章-Azure 机器学习工作室</span><span class="sxs-lookup"><span data-stu-id="8a9f5-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="8a9f5-180">若要使用*Azure 机器学习*，将需要配置要成为可用于应用程序的机器学习服务的实例。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="8a9f5-181">在 Azure 门户中，单击**新建**在左上角，并搜索**机器学习工作室工作区**，按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="8a9f5-183">该新页面将提供的说明**机器学习工作室工作区**服务。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="8a9f5-184">在左下角此提示，请单击**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="8a9f5-185">一旦你单击**创建**，将显示一个面板，需要提供一些有关您的新详细信息**机器学习工作室服务**:</span><span class="sxs-lookup"><span data-stu-id="8a9f5-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="8a9f5-186">插入所需**工作区名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="8a9f5-187">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="8a9f5-188">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8a9f5-189">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8a9f5-190">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="8a9f5-191">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="8a9f5-192">确定**位置**为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="8a9f5-193">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="8a9f5-194">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="8a9f5-195">应使用在上一章中创建 Azure 存储使用的同一资源组。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="8a9f5-196">有关**存储帐户**部分中，单击**使用现有**，然后单击下拉列表菜单，并在此处，单击**存储帐户**在最后一章中创建。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="8a9f5-197">选择适当**工作区定价层**为你从下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="8a9f5-198">内**Web 服务计划**部分中，单击**创建** **新的、** 然后在文本字段中插入它的名称。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="8a9f5-199">从**Web 服务计划定价层**部分中，选择所选的价格层。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="8a9f5-200">开发测试层称为**开发测试标准**应可供无需任何费用。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="8a9f5-201">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="8a9f5-202">单击“创建”  。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-202">Click **Create**.</span></span>

        ![Azure 机器学习工作室](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="8a9f5-204">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="8a9f5-205">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="8a9f5-207">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="8a9f5-209">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="8a9f5-210">在页中显示，在**其他链接**部分中，单击**启动机器学习工作室**，这会将你的浏览器定向**机器学习工作室**门户。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="8a9f5-212">使用**Sign In**按钮，在右上角或中心，能够登录到你的机器学习工作室中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="8a9f5-214">第 3 章-机器学习工作室：数据集设置</span><span class="sxs-lookup"><span data-stu-id="8a9f5-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="8a9f5-215">一个机器学习算法工作的方式是通过分析现有数据，然后尝试预测未来结果基于现有数据集。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="8a9f5-216">这通常意味着，您有更好的算法预测未来的结果将是更现有数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="8a9f5-217">示例表为提供给您，本课程中，调用[ProductsTableCSV 并且可以在此处下载](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a9f5-218">上面的.zip 文件包含这两**ProductsTableCSV**并 **.unitypackage**，将会在需要[第 6 章](#chapter-6---importing-the-mlproducts-unity-package)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="8a9f5-219">尽管单独的 csv 文件中的相关章节，还提供此包。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="8a9f5-220">此示例数据集包含在一 2017 年中的每一天每隔一小时的最畅销的对象记录。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![机器学习工作室：数据集设置](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="8a9f5-222">例如，在 2017年的第 1 天，在下午 1 点 （13 小时），最畅销的项是佩珀中士。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="8a9f5-223">此示例表包含 9998 条目。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="8a9f5-224">回到**机器学习工作室**门户中，并添加此表作为**数据集**在机器学习。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="8a9f5-225">执行此操作通过单击 **+ 新建**中屏幕的左下角的按钮。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![机器学习工作室：数据集设置](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="8a9f5-227">部分将显示底部，并在左侧是导航面板中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="8a9f5-228">单击**数据集**，然后，右侧**从本地文件**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![机器学习工作室：数据集设置](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="8a9f5-230">上传新**数据集**通过执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="8a9f5-231">将显示上传窗口中，您可以在其中**浏览**硬盘空间用于新的数据集。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![机器学习工作室：数据集设置](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="8a9f5-233">一旦选择，并且在上传窗口后，将保持未选中的复选框。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="8a9f5-234">在下面的文本字段中，输入**ProductsTableCSV.csv**作为数据集的名称 （尽管应会自动添加）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="8a9f5-235">使用下拉列表菜单**类型**，选择**标头 (.csv) 的一般 CSV 文件**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="8a9f5-236">按上传窗口右下角中的刻度线和你**数据集**将上传。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="8a9f5-237">第 4 章-机器学习工作室：实验</span><span class="sxs-lookup"><span data-stu-id="8a9f5-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="8a9f5-238">您可以构建机器学习系统之前，需要构建试验，以验证在理论上有关你的数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="8a9f5-239">结果，您将知道是否需要更多数据，或如果没有数据和可能结果之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="8a9f5-240">若要开始创建试验：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="8a9f5-241">请再次单击 **+ 新建**按钮在左下角的页上，然后单击**实验** > **的空白实验**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="8a9f5-243">一个新页面将显示具有空白实验：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="8a9f5-244">在左侧面板中展开**保存的数据集** > **我的数据集**并将其拖**ProductsTableCSV**到**试验画布**.</span><span class="sxs-lookup"><span data-stu-id="8a9f5-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="8a9f5-246">在左侧面板中，展开**Data Transformation** > **样本和拆分**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="8a9f5-247">然后将拖**拆分数据**中的项到**试验画布**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="8a9f5-248">拆分数据项将拆分为两个部分的数据集。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="8a9f5-249">一个部分将使用用于定型的机器学习算法。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="8a9f5-250">第二部分将用于评估生成的算法的准确性。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="8a9f5-252">在右侧面板中 （在选择在画布上的项的拆分数据） 时，编辑**中第一个输出数据集的行部分**到**0.7**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="8a9f5-253">这会将数据拆分为两个部分，第一部分将为 70%的数据，并且第二个部分将在剩下的 30%。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="8a9f5-254">若要确保数据随机拆分，请确保**随机拆分**复选框保持选中状态。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="8a9f5-256">将连接从的基**ProductsTableCSV**拆分数据项顶部到画布上的项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="8a9f5-257">这将连接项并发送**ProductsTableCSV**拆分数据输入到数据集输出 （数据）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![机器学习工作室：实验](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="8a9f5-259">在中**试验**左侧和右侧面板中，展开**机器学习** > **训练**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="8a9f5-260">拖动**训练模型**到试验画布中签出项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="8a9f5-261">画布应为相同的外观如下。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-261">Your canvas should look the same as the below.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="8a9f5-263">从***靠下左对齐***的**拆分数据**项拖动到的连接**右上方**的**训练模型**项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="8a9f5-264">训练模型将使用从数据集中的第一个 70%拆分用于训练算法。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="8a9f5-266">选择**训练模型**项在画布上，并在**属性**面板中 （在浏览器窗口的右侧） 上单击**启动列选择器**按钮。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="8a9f5-267">在文本框中键入**产品**，然后按**Enter**，*产品*将设置为列定型预测。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="8a9f5-268">接着，单击**刻度线**右下角以关闭选择对话框中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="8a9f5-270">想要训练**多类逻辑回归**算法来预测最售出**产品**基于日期和日期的小时。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="8a9f5-271">它不在本文档介绍了 Azure 机器学习工作室，不过，所提供的不同算法的详细信息的范围内你可了解详细信息从[机器学习算法备忘单](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="8a9f5-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="8a9f5-272">从左侧的试验项目面板中，展开**机器学习** > **初始化模型** > **分类**，并将其拖**多类逻辑回归**到试验画布上的项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="8a9f5-273">连接输出中，从底部**多类逻辑回归**，到的顶部左侧输入**训练模型**项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="8a9f5-275">在左侧面板中的试验项目的列表中，展开**机器学习** > **分数**，并将其拖**评分模型**到画布上的项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="8a9f5-276">连接输出中，从底部**训练模型**，到的顶部左侧输入**评分模型**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="8a9f5-277">连接的底部右侧输出**拆分数据**，到右上角输入**评分模型**项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="8a9f5-279">在列表中**实验**在左侧面板中的项展开**机器学习** > **评估**，并将其拖**评估模型**项拖动到画布上的。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="8a9f5-280">连接的输出**评分模型**到的顶部左侧输入**评估模型**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="8a9f5-282">构建了第一个机器学习试验。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="8a9f5-283">你现在可以保存并运行此试验。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-283">You can now save and run the experiment.</span></span> <span data-ttu-id="8a9f5-284">在页面底部的菜单中，单击**保存**按钮以保存你的试验，然后单击**运行**开始试验。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="8a9f5-286">您可以看到**状态**的右上角画布中的实验。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="8a9f5-287">稍等片刻实验来完成。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="8a9f5-288">如果你有大 （实际） 数据集很可能试验可能需要小时才能运行。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="8a9f5-290">右键单击**评估模型**项画布中并从上下文菜单悬停通过鼠标**评估结果**，然后选择**可视化**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="8a9f5-292">将显示实际结果与这些预测的结果显示的评估结果。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="8a9f5-293">这将使用原始数据集，用于评估该模型更早版本，拆分的 30%。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="8a9f5-294">您可以看到的结果不太好了，理想情况下您最大的数字在每个行位于列中突出显示的项。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="8a9f5-296">关闭**结果**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-296">Close the **Results**.</span></span>

24. <span data-ttu-id="8a9f5-297">若要使用你需要将它作为新训练的机器学习模型**Web 服务**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="8a9f5-298">若要执行此操作，单击**设置 Web 服务**菜单项底部的页上，在菜单中，然后单击**预测 Web 服务**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="8a9f5-300">将创建一个新选项卡，并训练模型合并以创建新的 web 服务。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="8a9f5-301">在页面底部的菜单中单击**保存**，然后单击**运行**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="8a9f5-302">您将看到在实验画布的右上角中更新的状态。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="8a9f5-304">运行完成后**部署 Web 服务**按钮将出现在页面底部。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="8a9f5-305">已准备好部署 web 服务。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="8a9f5-306">单击**部署 Web 服务**（经典） 在页面底部的菜单中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="8a9f5-308">在浏览器可能会提示允许弹出窗口中，您应该**允许**中使用，但可能需要按**部署 Web 服务**同样，如果未显示部署页。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="8a9f5-309">创建试验后你将重定向到**仪表板**页面，其中有你**API 密钥**显示。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="8a9f5-310">暂时将其复制到记事本中，你将需要它在代码中非常快。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="8a9f5-311">一旦你已记下 API 密钥，则单击**请求/响应**按钮**默认终结点**键下面的部分。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="8a9f5-313">如果在此页中单击测试，你将能够输入的输入的数据，然后查看输出。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="8a9f5-314">输入**天**并**小时**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="8a9f5-315">将保留**产品**条目保留为空。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="8a9f5-316">然后单击**确认**按钮。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="8a9f5-317">在页面底部的输出将显示的 JSON 表示正在选择每个产品的可能性。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="8a9f5-318">新的 web 页面将打开，显示的说明和所需的机器学习工作室的请求结构有关的一些示例。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="8a9f5-319">复制**请求 URI**显示在此页上，到在记事本。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![机器学习工作室：实验](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="8a9f5-321">现在已构建的机器学习系统，它提供最有可能的产品销售根据历史购买数据、 相关的天和年的某一天的时间。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="8a9f5-322">若要调用 web 服务，将服务终结点和一个 API 密钥，该服务需要 URL。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="8a9f5-323">单击**使用**选项卡上，从顶部菜单中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="8a9f5-324">**消耗**信息页将显示你将需要从代码中调用 web 服务的信息。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="8a9f5-325">需要一份**主键**并**请求-响应**URL。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="8a9f5-326">你将需要这些在下一章。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="8a9f5-327">第 5 章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="8a9f5-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="8a9f5-328">设置和测试在混合现实沉浸式头戴式。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="8a9f5-329">你将**不**此课程需要运动控制器。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="8a9f5-330">如果你需要支持沉浸式头戴式设置，请单击[此处](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="8a9f5-331">打开**Unity**并创建一个名为的新的 Unity 项目**MR\_MachineLearning。**</span><span class="sxs-lookup"><span data-stu-id="8a9f5-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="8a9f5-332">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="8a9f5-333">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8a9f5-334">转到**编辑** > **首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8a9f5-335">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="8a9f5-336">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="8a9f5-337">接下来，请转到**文件** > **生成设置**，并切换到平台**通用 Windows 平台**，通过单击***切换平台***按钮。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="8a9f5-338">此外，请确保：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="8a9f5-339">**设备为目标**设置为**任一设备**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="8a9f5-340">对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="8a9f5-341">**生成的类型**设置为**D3D**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="8a9f5-342">**SDK**设置为**最新安装**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="8a9f5-343">**Visual Studio 版本**设置为**最新安装**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="8a9f5-344">**生成并运行**设置为**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="8a9f5-345">有关设置的信息，请不要担心**场景**稍后再试，因为这些提供更高版本。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="8a9f5-346">现在，应为默认值保留剩余的设置。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-346">The remaining settings should be left as default for now.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="8a9f5-348">在**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="8a9f5-349">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="8a9f5-350">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="8a9f5-351">**脚本编写** **运行时版本**应**实验**（.NET 4.6 等效）</span><span class="sxs-lookup"><span data-stu-id="8a9f5-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="8a9f5-352">**脚本编写后端**应为 ***.NET***</span><span class="sxs-lookup"><span data-stu-id="8a9f5-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="8a9f5-353">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="8a9f5-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="8a9f5-355">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="8a9f5-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="8a9f5-356">**InternetClient**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="8a9f5-358">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加</span><span class="sxs-lookup"><span data-stu-id="8a9f5-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="8a9f5-360">回到**生成设置** *Unity C#* 项目不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="8a9f5-361">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="8a9f5-362">保存项目 (**文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="8a9f5-363">第 6 章-导入 MLProducts Unity 程序包</span><span class="sxs-lookup"><span data-stu-id="8a9f5-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="8a9f5-364">本课程中，你将需要下载名为的 Unity 资产包[ **Azure MR 307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="8a9f5-365">此包提供完整的场景，与中的所有对象的预构建，因此您可以集中精力获取其所有工作。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="8a9f5-366">**ShelfKeeper**提供脚本，但只包含公共变量，用于场景安装程序结构。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="8a9f5-367">你将需要执行所有其他部分。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="8a9f5-368">若要导入此包：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-368">To import this package:</span></span>

1.  <span data-ttu-id="8a9f5-369">准备好 Unity 仪表板中，单击**资产**在屏幕顶部的菜单，然后单击**导入包、 自定义包**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="8a9f5-371">使用文件选取器选择**Azure MR 307.unitypackage**程序包，再单击**打开**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="8a9f5-372">将向你显示此资产的组件的列表。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="8a9f5-373">通过单击确认导入**导入**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-373">Confirm the import by clicking **Import**.</span></span>

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="8a9f5-375">完成导入后，你会注意到一些新文件夹刊登在您的 Unity**项目面板**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="8a9f5-376">这些都是三维模型和相应的材料的预制场景将处理的部分。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="8a9f5-377">在本课程中，你将编写的大部分代码。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-377">You will write the majority of the code in this course.</span></span>

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="8a9f5-379">内**项目面板**文件夹中，单击**场景**场景中单击文件夹并双击 (称为**MR_MachineLearningScene**)。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="8a9f5-380">场景会打开 （请参阅下图所示）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-380">The scene will open (see image below).</span></span> <span data-ttu-id="8a9f5-381">如果丢失了红色方块，只需单击**gizmos，请**顶部的按钮，角**游戏面板**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="8a9f5-383">第 7 章-检查在 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="8a9f5-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="8a9f5-384">若要利用 JSON 库 （用于序列化和反序列化） 的使用，Newtonsoft DLL 已实现与包中引入。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="8a9f5-385">库应具有正确的配置，但最好检查 （特别是在遇到问题的代码不起作用）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="8a9f5-386">为此，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-386">To do so:</span></span>

-  <span data-ttu-id="8a9f5-387">左键单击插件文件夹内对 Newtonsoft 文件，并查看**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="8a9f5-388">请确保**Any 平台**勾选了。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="8a9f5-389">转到**UWP 选项卡**并确保**不处理**勾选了。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![导入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="8a9f5-391">章 8-创建 ShelfKeeper 类</span><span class="sxs-lookup"><span data-stu-id="8a9f5-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="8a9f5-392">**ShelfKeeper**类承载方法，用于控制用户界面和生成在场景中的产品。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="8a9f5-393">作为导入的包的一部分，你将拥有对此类，但不完整。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="8a9f5-394">它现在是时候完成此类：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="8a9f5-395">双击**ShelfKeeper**编写脚本内**脚本**文件夹，将其与打开**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="8a9f5-396">替换现有的脚本使用以下代码，用于设置日期和时间，并有一个方法来显示产品中的所有代码。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="8a9f5-397">请务必保存中所做的更改**Visual Studio**才会回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="8a9f5-398">返回在 Unity 编辑器中，检查**ShelfKeeper**类看起来像如下：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="8a9f5-400">如果您的脚本不具有引用目标 (即 *（文本网格） 的日期*)，只需将中的相应对象拖**层次结构面板**，相应的目标字段中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="8a9f5-401">请参阅下面有关说明，如果需要：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="8a9f5-402">打开**衍生点**数组内**ShelfKeeper**组件脚本将按左键单击它。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="8a9f5-403">子部分将显示名为**大小**，指示数组的大小。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="8a9f5-404">类型**3**旁边的文本框**大小**然后按**Enter**，并将下创建三个插槽。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="8a9f5-405">内**层次结构**展开**时间显示**（通过单击鼠标左键其旁边的箭头） 的对象。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="8a9f5-406">接下来，单击***Main Camera***内**层次结构**，以便**Inspector**显示其信息。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="8a9f5-407">选择**主照相机**中**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="8a9f5-408">拖动**日期**并**时间**中的对象**层次结构面板**到**日期文本**并**时文本**在槽**Inspector**的**Main Camera**中**ShelfKeeper**组件。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="8a9f5-409">拖动**Spawn 点**从**层次结构面板**(下方*货架*对象) 到**3** **元素**引用下的目标**衍生点**数组，如图所示。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="8a9f5-411">章 9-创建 ProductPrediction 类</span><span class="sxs-lookup"><span data-stu-id="8a9f5-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="8a9f5-412">要创建的下一步类是**ProductPrediction**类。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="8a9f5-413">此类负责：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-413">This class is responsible for:</span></span>

-   <span data-ttu-id="8a9f5-414">查询**机器学习服务**提供当前日期和时间的实例。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="8a9f5-415">反 JSON 响应序列化使用的数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="8a9f5-416">解释的数据，检索的三个推荐的产品。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="8a9f5-417">调用**ShelfKeeper**类方法来显示场景中的数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="8a9f5-418">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-418">To create this class:</span></span>

1.  <span data-ttu-id="8a9f5-419">转到**脚本**文件夹，请在**项目面板**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="8a9f5-420">在文件夹中，右键单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="8a9f5-421">调用脚本**ProductPrediction**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="8a9f5-422">双击新**ProductPrediction**脚本以将其与打开**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="8a9f5-423">如果**检测到文件修改**对话框弹出，单击 \***重载解决方案**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="8a9f5-424">将以下命名空间添加到 ProductPrediction 类的顶部：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="8a9f5-425">内部**ProductPrediction**类插入组成了多个嵌套类的以下两个对象。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="8a9f5-426">这些类用于序列化和反序列化的机器学习服务的 JSON。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="8a9f5-427">（以便 JSON 相关的代码是在脚本中，下面的所有其他代码，并不碍事底部），然后添加以下变量前面的代码上方：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="8a9f5-428">确保插入**主键**并**请求响应终结点**，从机器学习门户，到这里的变量。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="8a9f5-429">下图显示其中您所需的键和从终结点。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![机器学习工作室：实验](images/AzureLabs-Lab7-53-1.png)
    >
    > ![机器学习工作室：实验](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="8a9f5-432">此代码中的插入**start （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="8a9f5-433">**Start （)** 类初始化时调用方法：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="8a9f5-434">下面是从 Windows 中收集的日期和时间，并将其转换为我们的机器学习实验可用于与表中存储的数据进行比较的格式的方法。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="8a9f5-435">你可以**删除** **update （)** 方法因为此类不会使用它。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="8a9f5-436">添加以下方法将当前日期和时间的机器学习终结点进行通信并接收 JSON 格式的响应。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="8a9f5-437">添加以下方法，它负责反序列化 JSON 响应，以及通信到反序列化的结果**ShelfKeeper**类。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="8a9f5-438">此结果将是预测销售在当前日期和时间最多的三个项的名称。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="8a9f5-439">将下面的代码插入**ProductPrediction**类，在上一方法的下方。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="8a9f5-440">保存**Visual Studio**和回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="8a9f5-441">拖动**ProductPrediction**类中的脚本**脚本**文件夹中，拖动到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="8a9f5-442">保存您的场景和项目**文件** > **保存场景/文件** > **保存项目**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="8a9f5-443">第 10 章 — 生成 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="8a9f5-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="8a9f5-444">就现在可以将项目生成为一个 UWP 的解决方案，以便它可以作为独立应用程序运行。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="8a9f5-445">若要生成：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-445">To Build:</span></span>

1.  <span data-ttu-id="8a9f5-446">通过单击保存当前场景**文件** > **保存场景**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="8a9f5-447">转到**文件** > **生成设置**</span><span class="sxs-lookup"><span data-stu-id="8a9f5-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="8a9f5-448">选中复选框调用**UnityC#项目**（这是重要因为这可以使您可以编辑类生成完成后）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="8a9f5-449">单击**添加打开场景**，</span><span class="sxs-lookup"><span data-stu-id="8a9f5-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="8a9f5-450">单击“生成”  。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-450">Click **Build**.</span></span>

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="8a9f5-452">系统将提示您选择你想要生成解决方案的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="8a9f5-453">创建**生成**文件夹并在该文件夹中创建另一个文件夹，与所选的适当的名称。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="8a9f5-454">单击新文件夹，然后单击**选择文件夹**，若要开始在该位置的生成。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-55.png)

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="8a9f5-457">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="8a9f5-458">章 11-部署应用程序</span><span class="sxs-lookup"><span data-stu-id="8a9f5-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="8a9f5-459">若要部署你的应用程序：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-459">To deploy your application:</span></span>

1.  <span data-ttu-id="8a9f5-460">导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="8a9f5-461">使用 Visual Studio 中打开，您需要还原 NuGet 包，这可以通过右键单击 MachineLearningLab_Build 解决方案，从解决方案资源管理器 （Visual Studio 的右侧找到），然后单击还原 NuGet 包：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![添加 NuGet 包](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="8a9f5-463">在解决方案配置中，选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="8a9f5-464">在解决方案平台中，选择**x86**，**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="8a9f5-465">对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="8a9f5-466">不过，需要还执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8a9f5-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="8a9f5-467">知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="8a9f5-468">请确保**开发人员模式**是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![添加 NuGet 包](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="8a9f5-470">转到**生成菜单**，然后单击**部署解决方案**旁加载到您的 PC 应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="8a9f5-471">你的应用现在应出现在已安装的应用，准备好启动列表中。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="8a9f5-472">运行混合现实应用程序时，你将看到您的 Unity 场景中设置工作台和从初始化时，设置在 Azure 中提取的数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="8a9f5-473">数据将反序列化应用程序中，并将作为工作台上的三个模型，以可视方式提供当前日期和时间前的三个结果。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="8a9f5-474">完成的机器学习应用程序</span><span class="sxs-lookup"><span data-stu-id="8a9f5-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="8a9f5-475">祝贺你，构建利用 Azure 机器学习来进行数据预测并将其显示在您的场景的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![添加 NuGet 包](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="8a9f5-477">练习</span><span class="sxs-lookup"><span data-stu-id="8a9f5-477">Exercise</span></span>

<span data-ttu-id="8a9f5-478">**练习 1**</span><span class="sxs-lookup"><span data-stu-id="8a9f5-478">**Exercise 1**</span></span>

<span data-ttu-id="8a9f5-479">试着你的应用程序的排序顺序并根据此数据可能会有用也已上架显示的三个底部预测。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="8a9f5-480">**练习 2**</span><span class="sxs-lookup"><span data-stu-id="8a9f5-480">**Exercise 2**</span></span>

<span data-ttu-id="8a9f5-481">使用**Azure 表**填充包含天气信息的新表并创建新的实验使用的数据。</span><span class="sxs-lookup"><span data-stu-id="8a9f5-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
