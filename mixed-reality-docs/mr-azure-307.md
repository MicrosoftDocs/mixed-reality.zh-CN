---
title: MR 和 Azure 307-机器学习
description: 完成本课程以了解如何在混合现实应用程序内实现 Azure 机器学习 Studio。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，机器学习，ml，机器学习工作室，hololens，沉浸，vr
ms.openlocfilehash: e302e287049cd746a436904c2af2bcc2b0835796
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926619"
---
>[!NOTE]
><span data-ttu-id="ce3fb-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ce3fb-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ce3fb-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ce3fb-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ce3fb-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ce3fb-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="ce3fb-110">MR 和 Azure 307：机器学习</span><span class="sxs-lookup"><span data-stu-id="ce3fb-110">MR and Azure 307: Machine learning</span></span>

![最终产品-启动](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="ce3fb-112">在本课程中，您将学习如何使用 Azure 机器学习 Studio 向混合现实应用程序添加机器学习（ML）功能。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="ce3fb-113">*Azure 机器学习 Studio*是一项 Microsoft 服务，它为开发人员提供了大量机器学习算法，可帮助进行数据输入、输出、准备和可视化。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="ce3fb-114">然后，可以通过这些组件开发预测分析试验，对其进行循环访问，并使用它来训练模型。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="ce3fb-115">完成培训后，可以在 Azure 云中操作模型，使其可以对新数据进行评分。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="ce3fb-116">有关详细信息，请访问[Azure 机器学习 Studio 页](https://azure.microsoft.com/services/machine-learning-studio/)。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="ce3fb-117">完成本课程后，你将拥有一个混合现实沉浸式耳机式应用程序，并将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="ce3fb-118">向*Azure 机器学习 Studio*门户提供销售数据表，并设计一个算法以预测未来的热门项目的销售情况。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="ce3fb-119">创建可从 ML 服务接收和解释预测数据的**Unity 项目**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="ce3fb-120">通过在货位上提供最常用的销售项，直观显示**Unity 项目**中的断言而数据。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="ce3fb-121">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ce3fb-122">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ce3fb-123">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="ce3fb-124">本课程是一个自包含教程，并不直接涉及任何其他混合现实实验室。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="ce3fb-125">设备支持</span><span class="sxs-lookup"><span data-stu-id="ce3fb-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ce3fb-126">摘要</span><span class="sxs-lookup"><span data-stu-id="ce3fb-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ce3fb-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ce3fb-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ce3fb-128"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="ce3fb-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ce3fb-129">MR 和 Azure 307：机器学习</span><span class="sxs-lookup"><span data-stu-id="ce3fb-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="ce3fb-130">✔️</span><span class="sxs-lookup"><span data-stu-id="ce3fb-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ce3fb-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ce3fb-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ce3fb-132">尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ce3fb-133">在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ce3fb-134">使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce3fb-135">必备条件</span><span class="sxs-lookup"><span data-stu-id="ce3fb-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ce3fb-136">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ce3fb-137">另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ce3fb-138">您可以随意使用最新的软件（如[安装工具一文](install-the-tools.md)中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ce3fb-139">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ce3fb-140">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="ce3fb-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ce3fb-141">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="ce3fb-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ce3fb-142">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ce3fb-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ce3fb-143">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="ce3fb-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ce3fb-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ce3fb-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ce3fb-145">启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ce3fb-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ce3fb-146">Azure 安装和 ML 数据检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="ce3fb-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ce3fb-147">开始之前</span><span class="sxs-lookup"><span data-stu-id="ce3fb-147">Before you start</span></span>

<span data-ttu-id="ce3fb-148">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="ce3fb-149">第1章-Azure 存储帐户设置</span><span class="sxs-lookup"><span data-stu-id="ce3fb-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="ce3fb-150">若要使用 Azure Translator API，你将需要配置服务的实例，使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="ce3fb-151">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce3fb-152">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ce3fb-153">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ce3fb-154">登录后，单击左侧菜单中的 "**存储帐户**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="ce3fb-156">在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="ce3fb-157">在 "**存储帐户**" 选项卡上，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="ce3fb-159">在 "**创建存储帐户**" 面板中：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="ce3fb-160">插入帐户的**名称**，请注意，此字段仅接受数字和小写字母。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="ce3fb-161">对于**部署模型，选择 "** **资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="ce3fb-162">对于 "**帐户类型**"，请选择 "**存储（常规用途 v1）** "。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="ce3fb-163">对于 "**性能**"，请选择 "**标准**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="ce3fb-164">对于**复制**，请选择 "**读取-访问-异地冗余存储（GRS）** "。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="ce3fb-165">使**安全传输**保持**禁用状态**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="ce3fb-166">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="ce3fb-167">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ce3fb-168">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ce3fb-169">建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ce3fb-170">若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="ce3fb-171">确定资源组的**位置**（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ce3fb-172">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ce3fb-173">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="ce3fb-174">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="ce3fb-176">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="ce3fb-177">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="ce3fb-179">第2章-Azure 机器学习工作室</span><span class="sxs-lookup"><span data-stu-id="ce3fb-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="ce3fb-180">若要使用*Azure 机器学习*，需要配置机器学习服务的实例，使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="ce3fb-181">在 Azure 门户中，单击左上角的 "**新建**"，然后搜索**机器学习 Studio 工作区**，按**enter**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure 机器学习 Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="ce3fb-183">新页将提供**机器学习 Studio 工作区**服务的说明。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="ce3fb-184">在此提示符的左下方，单击 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="ce3fb-185">单击 "**创建**" 后，将显示一个面板，需要在其中提供有关新**机器学习 Studio 服务**的一些详细信息：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="ce3fb-186">为此服务实例插入所需的**工作区名称**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="ce3fb-187">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="ce3fb-188">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ce3fb-189">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ce3fb-190">建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="ce3fb-191">若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="ce3fb-192">确定资源组的**位置**（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ce3fb-193">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ce3fb-194">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="ce3fb-195">应使用在上一章中用于创建 Azure 存储的同一资源组。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="ce3fb-196">对于 "**存储帐户**" 部分，单击 "**使用现有**项"，然后单击下拉菜单，然后从那里单击你在上一章中创建的**存储帐户**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="ce3fb-197">从下拉菜单中选择合适的**工作区定价层**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="ce3fb-198">在 " **Web 服务计划**" 部分中 **，单击 "** **新建"，** 然后在 "文本" 字段中插入它的名称。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="ce3fb-199">从 " **Web 服务计划定价层**" 部分，选择所选的价格层。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="ce3fb-200">名为**开发测试 Standard**的开发测试层应免费提供给您。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="ce3fb-201">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="ce3fb-202">单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-202">Click **Create**.</span></span>

        ![Azure 机器学习 Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="ce3fb-204">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="ce3fb-205">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 机器学习 Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="ce3fb-207">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 机器学习 Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="ce3fb-209">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="ce3fb-210">在显示的页面的 "**其他链接**" 部分下，单击 "**启动机器学习 Studio**"，这会将浏览器定向到**机器学习 studio**门户。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure 机器学习 Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="ce3fb-212">使用右上角的 "**登录**" 按钮登录到机器学习 Studio。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure 机器学习 Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="ce3fb-214">第3章-机器学习 Studio：数据集设置</span><span class="sxs-lookup"><span data-stu-id="ce3fb-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="ce3fb-215">机器学习算法的一种方法是分析现有数据，然后根据现有数据集尝试预测未来结果。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="ce3fb-216">这通常意味着您拥有的现有数据越多，算法的预测未来结果就越好。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="ce3fb-217">本课程提供了一个示例表，此课程称为 ProductsTableCSV，[可在此处下载](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce3fb-218">上述 .zip 文件包含**ProductsTableCSV**和**unitypackage**，这将在[第6章](#chapter-6---importing-the-mlproducts-unity-package)中需要。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="ce3fb-219">这一章中也提供了此包，但它与 csv 文件分离。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="ce3fb-220">此示例数据集包含2017年每一天的每个小时的最佳销售对象的记录。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![机器学习 Studio：数据集设置](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="ce3fb-222">例如，在2017的第1天（每小时13点），最佳销售物品是 salt 和辣椒。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="ce3fb-223">此示例表包含9998个条目。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="ce3fb-224">返回到**机器学习 Studio**门户，并将此表添加为 ML 的**数据集**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="ce3fb-225">单击屏幕左下角的 " **+ 新建**" 按钮即可执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![机器学习 Studio：数据集设置](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="ce3fb-227">部分将从底部开始，并在左侧有导航面板。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="ce3fb-228">单击 "数据集"，然后依次单击 "**数据集**"、"**本地文件**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![机器学习 Studio：数据集设置](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="ce3fb-230">按照以下步骤上传新的**数据集**：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="ce3fb-231">此时将显示 "上传" 窗口，您可以在其中**浏览**硬盘驱动器以查找新的数据集。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![机器学习 Studio：数据集设置](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="ce3fb-233">选择后，返回到 "上传" 窗口，将复选框保留为 "未选中"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="ce3fb-234">在下面的文本字段中，输入**ProductsTableCSV**作为数据集的名称（但应自动添加）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="ce3fb-235">使用**类型**的下拉菜单，选择**带有标头的通用 CSV 文件（.csv）** 。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="ce3fb-236">按上传窗口右下角的勾选标记，将上传**数据集**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="ce3fb-237">第4章-机器学习工作室：试验</span><span class="sxs-lookup"><span data-stu-id="ce3fb-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="ce3fb-238">在构建机器学习系统之前，你需要构建一个试验来验证你的数据的理论。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="ce3fb-239">在结果中，你将知道是否需要更多数据，或者数据与可能的结果之间是否没有关联。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="ce3fb-240">开始创建试验：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="ce3fb-241">再次单击页面左下角的 " **+ 新建**" 按钮，然后单击**试验** > **空白实验**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="ce3fb-243">将显示一个新页面，其中包含一个空白实验：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="ce3fb-244">在左侧面板中，展开 "**保存的数据集**" >  **"我的数据集**"，并将**ProductsTableCSV**拖到**试验画布**上。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="ce3fb-246">在左侧面板中，展开 "**数据转换**" > "**示例" 和 "拆分**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="ce3fb-247">然后将**拆分**数据项拖到**试验画布**中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="ce3fb-248">拆分数据项会将数据集拆分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="ce3fb-249">用于训练机器学习算法的部分。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="ce3fb-250">第二部分将用于计算生成的算法的准确性。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="ce3fb-252">在右侧面板中（选择了画布上的 Split 数据项时），将**第一个输出数据集中的行的小数部分**编辑为**0.7**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="ce3fb-253">这会将数据拆分为两个部分，第一部分将为70% 的数据，第二个部分将是剩余的30%。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="ce3fb-254">若要确保数据随机拆分，请确保**随机拆分**复选框保持选中状态。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="ce3fb-256">将连接从画布上**ProductsTableCSV**项的基拖到拆分数据项的顶部。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="ce3fb-257">这会将这些项连接起来，并将**ProductsTableCSV**数据集输出（数据）发送到拆分数据输入。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="ce3fb-259">在左侧的**试验**面板中，展开 "**机器学习** > **训练**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="ce3fb-260">将**训练模型**项拖出到试验画布。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="ce3fb-261">画布应与下面的外观相同。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-261">Your canvas should look the same as the below.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="ce3fb-263">从 "**拆分数据项**" 的左下***方***将连接拖到 "**定型模型**" 项的**右上方**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="ce3fb-264">定型模型将使用数据集中的第一个70% 拆分来训练该算法。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="ce3fb-266">在画布上选择 "**训练模型**" 项，然后在 "**属性**" 面板（位于浏览器窗口的右侧）中，单击 "**启动列选择器**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="ce3fb-267">在文本框中键入**product** ，然后按**enter**，*产品*将设置为用于定型预测的列。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="ce3fb-268">在此之后，单击右下角的**勾选标记**以关闭选择对话框。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="ce3fb-270">你将定型**多类逻辑回归**算法，根据一天中的小时和日期预测最销售的**产品**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="ce3fb-271">此文档超出了本文档的讨论范围，可以说明 Azure 机器学习 studio 提供的不同算法的详细信息，但你可以从[机器学习算法](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)备忘单中了解详细信息</span><span class="sxs-lookup"><span data-stu-id="ce3fb-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="ce3fb-272">在左侧的 "试验项" 面板中，展开 "**机器学习** > **初始化模型** > **分类**，然后将"**多类逻辑回归**"项拖到试验画布上。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="ce3fb-273">将**多类逻辑回归**的底部的输出连接到**定型模型**项的左上方输入。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="ce3fb-275">在左侧面板中的实验项列表中，展开 "**机器学习** > **评分**"，然后将 "**评分模型**" 项拖到画布上。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="ce3fb-276">将来自**定型模型**底部的输出连接到**评分模型**的左上方输入。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="ce3fb-277">将从**拆分数据**向右下的输出连接到**评分模型**项的右上方输入。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="ce3fb-279">在左侧面板中的**实验**项列表中，展开 "**机器学习** > "**评估**"，然后将"**评估模型**"项拖到画布上。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="ce3fb-280">将**评分模型**的输出连接到**评估模型**的左上方输入。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="ce3fb-282">您已经生成了第一个机器学习试验。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="ce3fb-283">你现在可以保存并运行试验。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-283">You can now save and run the experiment.</span></span> <span data-ttu-id="ce3fb-284">在页面底部的菜单中，单击 "**保存**" 按钮以保存实验，并单击 "**运行**" 开始试验。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="ce3fb-286">可以在画布的右上方查看试验**状态**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="ce3fb-287">请稍等片刻，等待试验结束。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="ce3fb-288">如果有大型（现实）数据集，可能会有可能需要数小时才能运行试验。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="ce3fb-290">右键单击画布中的 "**评估模型**" 项，然后从上下文菜单中将鼠标悬停在 "**评估结果**" 上，然后选择 "**可视化**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="ce3fb-292">将显示计算结果，显示预测结果与实际结果。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="ce3fb-293">这将使用之前拆分的原始数据集的30% 来计算模型。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="ce3fb-294">您可以看到，结果并不是很好，理想情况下，每行中的最大数目是列中突出显示的项。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="ce3fb-296">关闭**结果**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-296">Close the **Results**.</span></span>

24. <span data-ttu-id="ce3fb-297">若要使用新训练的机器学习模型，你需要将其公开为**Web 服务**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="ce3fb-298">为此，请单击页面底部菜单中的 "**设置 Web 服务**" 菜单项，然后单击 "**预测 Web 服务**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="ce3fb-300">将创建一个新选项卡，并合并定型模型以创建新的 web 服务。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="ce3fb-301">在页面底部的菜单中，单击 "**保存**"，然后单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="ce3fb-302">你将在实验画布的右上角显示状态 "已更新"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="ce3fb-304">运行完毕后，将在页面底部显示 "**部署 Web 服务**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="ce3fb-305">你已准备好部署 web 服务。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="ce3fb-306">单击页面底部菜单中的 "**部署 Web 服务**（经典）"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="ce3fb-308">你的浏览器可能会提示你允许弹出窗口（你应该**允许**这样做），尽管你可能需要再次按 "**部署 Web 服务**" （如果未显示 "部署" 页）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="ce3fb-309">一旦创建了实验，你会被重定向到 "**仪表板**" 页面，你将在其中显示**API 密钥**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="ce3fb-310">将其复制到记事本中，你将很快在代码中需要它。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="ce3fb-311">记下 API 密钥后，请单击密钥下面的 "**默认终结点**" 部分中的 "**请求/响应**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="ce3fb-313">如果单击此页中的 "测试"，将能够输入输入数据并查看输出。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="ce3fb-314">输入**日期** **和时间**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="ce3fb-315">将**产品**条目留空。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="ce3fb-316">然后单击 "**确认**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="ce3fb-317">页面底部的输出将显示 JSON，表示每个产品选择的可能性。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="ce3fb-318">随即打开一个新网页，其中显示了有关机器学习 Studio 所需的请求结构的说明和示例。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="ce3fb-319">将此页中显示的**请求 URI**复制到记事本中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![机器学习 Studio：试验](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="ce3fb-321">现在，你已构建了一个机器学习系统，它提供了最有可能使用的产品，这些产品是基于历史购买数据销售的，并与一天中的时间和日期相关联。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="ce3fb-322">若要调用 web 服务，你将需要服务终结点的 URL 和服务的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="ce3fb-323">单击顶部菜单中的 "**使用**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="ce3fb-324">"**消耗**信息" 页将显示从代码中调用 web 服务所需的信息。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="ce3fb-325">获取**主密钥**和**请求-响应**URL 的副本。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="ce3fb-326">下一章将需要这些项。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="ce3fb-327">第5章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="ce3fb-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="ce3fb-328">设置并测试混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="ce3fb-329">本课程**不**需要移动控制器。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="ce3fb-330">如果需要支持设置沉浸式耳机，请单击[此处](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="ce3fb-331">打开**unity**并创建名为**MR\_Default-machinelearning-southcentralus**的新 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="ce3fb-332">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="ce3fb-333">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ce3fb-334">转到 "**编辑** > **首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ce3fb-335">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ce3fb-336">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="ce3fb-337">接下来，通过单击 "***切换平台***" 按钮转到 "**文件** > **生成设置**"，并将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="ce3fb-338">另外，请确保：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="ce3fb-339">"**目标设备**" 设置为 "**任何设备**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="ce3fb-340">对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ce3fb-341">**生成类型**设置为**D3D**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="ce3fb-342">**SDK**设置为 "**最新安装**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="ce3fb-343">**Visual Studio 版本**设置为 "**最新安装**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="ce3fb-344">"**生成并运行**" 设置为 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="ce3fb-345">请不要担心现在设置**场景**，因为稍后会提供这些信息。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="ce3fb-346">其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-346">The remaining settings should be left as default for now.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="ce3fb-348">在 "**生成设置**" 窗口中，单击 "**播放机设置**" 按钮，这会在**检查器**所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="ce3fb-349">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ce3fb-350">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ce3fb-351">**脚本** **运行时版本**应为**试验**性的（.net 4.6 等效项）</span><span class="sxs-lookup"><span data-stu-id="ce3fb-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="ce3fb-352">**脚本编写后端**应为 ***.net***</span><span class="sxs-lookup"><span data-stu-id="ce3fb-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="ce3fb-353">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="ce3fb-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="ce3fb-355">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ce3fb-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ce3fb-356">**InternetClient**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="ce3fb-358">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK**</span><span class="sxs-lookup"><span data-stu-id="ce3fb-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="ce3fb-360">"返回**生成设置** *" C# Unity*项目不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="ce3fb-361">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="ce3fb-362">保存项目（**文件 > 保存项目**）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="ce3fb-363">第6章-导入 MLProducts Unity 包</span><span class="sxs-lookup"><span data-stu-id="ce3fb-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="ce3fb-364">在本课程中，你将需要下载名为[**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)的 Unity 资产包。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="ce3fb-365">此包随场景一起提供，其中的所有对象都是预先构建的，因此你可以专注于使其正常工作。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="ce3fb-366">尽管仅出于场景设置结构的目的保留公共变量，但提供了**ShelfKeeper**脚本。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="ce3fb-367">您将需要执行所有其他部分。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="ce3fb-368">导入此包：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-368">To import this package:</span></span>

1.  <span data-ttu-id="ce3fb-369">在您前面的 "Unity" 面板中，单击屏幕顶部菜单中的 "**资产**"，然后单击 "**导入包、自定义包**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="ce3fb-371">使用文件选取器选择**unitypackage**包，并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="ce3fb-372">此时将显示此资产的组件列表。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="ce3fb-373">单击 "**导入**" 确认导入。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-373">Confirm the import by clicking **Import**.</span></span>

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="ce3fb-375">导入完成后，你会注意到某些新文件夹已显示在 Unity**项目面板**中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="ce3fb-376">这些是三维模型和各自的材料，它们是您将处理的预先准备的场景的组成部分。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="ce3fb-377">在本课程中，您将编写大部分代码。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-377">You will write the majority of the code in this course.</span></span>

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="ce3fb-379">在 "**项目面板**" 文件夹中，单击 "**场景**" 文件夹，然后双击（称为**MR_MachineLearningScene**）中的场景。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="ce3fb-380">屏幕将打开（请参阅下图）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-380">The scene will open (see image below).</span></span> <span data-ttu-id="ce3fb-381">如果缺少红色菱形，只需单击**游戏面板**右上角的 " **Gizmos** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="ce3fb-383">第7章-检查 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="ce3fb-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="ce3fb-384">若要利用 JSON 库（用于序列化和反序列化），已使用中的包实现了 Newtonsoft.json DLL。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="ce3fb-385">库应具有正确的配置，尽管需要检查它（特别是在代码不工作时遇到的问题）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="ce3fb-386">执行此操作的步骤：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-386">To do so:</span></span>

-  <span data-ttu-id="ce3fb-387">左键单击 "插件" 文件夹中的 Newtonsoft.json 文件，并查看 "**检查器" 面板**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="ce3fb-388">请确保勾选**任何平台**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="ce3fb-389">请在 " **UWP" 选项卡上**，确保**不勾选进程**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![导入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="ce3fb-391">第8章-创建 ShelfKeeper 类</span><span class="sxs-lookup"><span data-stu-id="ce3fb-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="ce3fb-392">**ShelfKeeper**类承载控制在场景中生成的 UI 和产品的方法。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="ce3fb-393">作为导入包的一部分，你将获得此类，但它是不完整的。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="ce3fb-394">现在可以完成该类：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="ce3fb-395">双击**Scripts**文件夹中的**ShelfKeeper**脚本，通过**Visual Studio 2017**将其打开。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="ce3fb-396">将脚本中的所有现有代码替换为以下代码，这会设置时间和日期，并具有显示产品的方法。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="ce3fb-397">在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="ce3fb-398">返回 Unity 编辑器，检查**ShelfKeeper**类是否如下所示：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ce3fb-400">如果脚本没有引用目标（即*日期（文本网格）* ），只需将相应的对象从 "**层次结构" 面板**拖动到目标字段。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="ce3fb-401">如有必要，请参阅下面的说明：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="ce3fb-402">在**ShelfKeeper**组件脚本中，通过左键单击**生成点**数组，将其打开。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="ce3fb-403">子节将出现 "**大小**"，指示数组的大小。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="ce3fb-404">在 "**大小**" 旁边的文本框中键入**3** ，按**enter**，然后将创建三个槽。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="ce3fb-405">在**层次结构**中，展开 "**时间显示**" 对象（通过左键单击其旁边的箭头）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="ce3fb-406">接下来，单击**层次结构**中的***主摄像机***，使**检查器**显示其信息。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="ce3fb-407">选择 "**层次结构" 面板**中的**主相机**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="ce3fb-408">将 "**日期**和**时间**" 对象从 **"层次结构" 面板**拖动到 " **ShelfKeeper** " 组件中的**主摄像机** **检查器**内的**日期文本**和**时间文本**槽。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="ce3fb-409">将 "**层次结构" 面板**（位于*货位*对象下）中的**生成点**拖到**生成点**数组下的**3**个**元素**引用目标，如图中所示。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="ce3fb-411">第9章-创建 ProductPrediction 类</span><span class="sxs-lookup"><span data-stu-id="ce3fb-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="ce3fb-412">要创建的下一个类是**ProductPrediction**类。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="ce3fb-413">此类负责：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-413">This class is responsible for:</span></span>

-   <span data-ttu-id="ce3fb-414">查询**机器学习服务**实例，同时提供当前日期和时间。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="ce3fb-415">将 JSON 响应反序列化为可用的数据。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="ce3fb-416">解释数据，检索3个推荐的产品。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="ce3fb-417">调用**ShelfKeeper**类方法以在场景中显示数据。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="ce3fb-418">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-418">To create this class:</span></span>

1.  <span data-ttu-id="ce3fb-419">在 "**项目" 面板**中，打开 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="ce3fb-420">右键单击文件夹内部，**创建** >  **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="ce3fb-421">调用脚本**ProductPrediction**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="ce3fb-422">双击新的**ProductPrediction**脚本以通过**Visual Studio 2017**将其打开。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="ce3fb-423">如果弹出了**文件修改**对话框，请单击 "**重新加载解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="ce3fb-424">将以下命名空间添加到 ProductPrediction 类的顶部：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="ce3fb-425">在**ProductPrediction**类中，插入以下两个由若干嵌套类组成的对象。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="ce3fb-426">这些类用于序列化和反序列化机器学习服务的 JSON。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="ce3fb-427">然后，将以下变量添加到前面的代码上（以便 JSON 相关的代码位于脚本底部，在所有其他代码的下面，并在所有其他代码之外）：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="ce3fb-428">请确保将机器学习门户中的**主密钥**和**请求-响应终结点**插入到此处的变量中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="ce3fb-429">以下图像显示了从何处获取密钥和终结点的位置。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![机器学习 Studio：试验](images/AzureLabs-Lab7-53-1.png)
    >
    > ![机器学习 Studio：试验](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="ce3fb-432">将此代码插入**Start （）** 方法内。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="ce3fb-433">当类初始化时，将调用**Start （）** 方法：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="ce3fb-434">下面是收集 Windows 中的日期和时间，并将其转换为机器学习试验可用于与表中存储的数据进行比较的格式的方法。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="ce3fb-435">您可以**删除** **Update （）** 方法，因为此类将不会使用它。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="ce3fb-436">添加以下方法，该方法将当前日期和时间传递到机器学习终结点，并接收 JSON 格式的响应。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

            // Serialize the request
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

12. <span data-ttu-id="ce3fb-437">添加以下方法，该方法负责反序列化 JSON 响应，并将反序列化的结果传递给**ShelfKeeper**类。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="ce3fb-438">此结果将是预测在当前日期和时间销售的三个项目的名称。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="ce3fb-439">将下面的代码插入到前面方法下面的**ProductPrediction**类中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="ce3fb-440">保存**Visual Studio**并返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="ce3fb-441">将**ProductPrediction**类脚本从**脚本**文件夹拖到**主相机**对象上。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="ce3fb-442">保存场景和项目**文件**， > **保存场景/文件** > **保存项目**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="ce3fb-443">第10章-构建 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="ce3fb-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="ce3fb-444">现在可以将项目构建为 UWP 解决方案，使其可以作为独立的应用程序运行。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="ce3fb-445">若要生成：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-445">To Build:</span></span>

1.  <span data-ttu-id="ce3fb-446">单击 "**文件**" > **保存场景**，保存当前场景。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="ce3fb-447">中转到**File** > **生成设置**</span><span class="sxs-lookup"><span data-stu-id="ce3fb-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="ce3fb-448">选中 "名为**Unity C#项目**的" 框（这一点很重要，因为它将允许您在生成完成后编辑类）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="ce3fb-449">单击 "**添加打开的场景**"，</span><span class="sxs-lookup"><span data-stu-id="ce3fb-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="ce3fb-450">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-450">Click **Build**.</span></span>

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="ce3fb-452">系统将提示您选择要在其中生成解决方案的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="ce3fb-453">创建一个**生成**文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="ce3fb-454">单击新文件夹，然后单击 "**选择文件夹**"，在该位置开始生成。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-55.png)

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="ce3fb-457">Unity 完成生成（可能需要一些时间）后，它会在生成的位置打开 "**文件资源管理器**" 窗口（检查任务栏，因为它可能不会始终出现在窗口之上，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="ce3fb-458">第11章-部署应用程序</span><span class="sxs-lookup"><span data-stu-id="ce3fb-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="ce3fb-459">若要部署应用程序：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-459">To deploy your application:</span></span>

1.  <span data-ttu-id="ce3fb-460">导航到新的 Unity 生成（**应用**文件夹），并在**Visual Studio**中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="ce3fb-461">在 Visual Studio 打开的情况下，你需要还原 NuGet 包，可以通过右键单击 MachineLearningLab_Build 解决方案来完成此操作，方法是在解决方案资源管理器（位于 Visual Studio 的右侧），然后单击 "还原 NuGet 包"：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![添加 NuGet 包](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="ce3fb-463">在解决方案配置中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="ce3fb-464">在解决方案平台中，选择 " **x86**，**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="ce3fb-465">对于 Microsoft HoloLens，你可能会发现将其设置为*远程计算机*会更容易，因此你不会受限到计算机上。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="ce3fb-466">不过，还需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ce3fb-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="ce3fb-467">知道您的 HoloLens 的**IP 地址**，可在 "*设置" > 网络 & Internet > > "高级选项*" 中找到;IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="ce3fb-468">确保**开发人员模式**已**打开**;在 "设置" 中找到 *> 更新开发人员 & 安全 >* 。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![添加 NuGet 包](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="ce3fb-470">中转到 "**生成" 菜单**，然后单击 "**部署解决方案**"，将应用程序旁加载到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="ce3fb-471">应用现在应显示在已安装的应用列表中，可以启动。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="ce3fb-472">运行混合现实应用程序时，你将看到在 Unity 场景中设置的工作台，并从初始化中获取在 Azure 中设置的数据。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="ce3fb-473">数据将在应用程序中进行反序列化，当前日期和时间的三个最顶部结果将以直观的形式提供，作为工作台上的三个模型。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="ce3fb-474">已完成的机器学习应用程序</span><span class="sxs-lookup"><span data-stu-id="ce3fb-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="ce3fb-475">恭喜，你构建了一个混合现实应用，它利用 Azure 机器学习来进行数据预测，并将其显示在你的场景中。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![添加 NuGet 包](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="ce3fb-477">小心谨慎</span><span class="sxs-lookup"><span data-stu-id="ce3fb-477">Exercise</span></span>

<span data-ttu-id="ce3fb-478">**练习1**</span><span class="sxs-lookup"><span data-stu-id="ce3fb-478">**Exercise 1**</span></span>

<span data-ttu-id="ce3fb-479">试验您的应用程序的排序顺序并使这三个最低预测出现在货位上，因为此数据可能也很有用。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="ce3fb-480">**练习2**</span><span class="sxs-lookup"><span data-stu-id="ce3fb-480">**Exercise 2**</span></span>

<span data-ttu-id="ce3fb-481">使用**Azure 表**时，将使用天气信息填充新表，并使用数据创建新试验。</span><span class="sxs-lookup"><span data-stu-id="ce3fb-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
