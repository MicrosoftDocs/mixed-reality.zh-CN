---
title: MR 和 Azure 305-函数和存储
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 存储和函数。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 函数、 存储、 hololens，令人着迷，vr
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590254"
---
>[!NOTE]
><span data-ttu-id="32de1-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="32de1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="32de1-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="32de1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="32de1-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="32de1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="32de1-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="32de1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="32de1-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="32de1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="32de1-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="32de1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="32de1-110">MR 和 Azure 305:函数和存储</span><span class="sxs-lookup"><span data-stu-id="32de1-110">MR and Azure 305: Functions and storage</span></span>

![最终产品-启动](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="32de1-112">在本课程中，您将学习如何创建和使用 Azure Functions 以及如何使用 Azure 存储资源，在混合的现实应用程序中存储数据。</span><span class="sxs-lookup"><span data-stu-id="32de1-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="32de1-113">*Azure Functions*是一个 Microsoft 服务，它允许开发人员运行小段代码，函数，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="32de1-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="32de1-114">这使您能够将工作委托给云，而不是本地应用程序，它可以有许多好处。</span><span class="sxs-lookup"><span data-stu-id="32de1-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="32de1-115">*Azure Functions*支持多种开发语言，包括 C\#，F\#，Node.js、 Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="32de1-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="32de1-116">有关详细信息，请访问[Azure Functions 项目](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="32de1-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="32de1-117">*Azure 存储*是 Microsoft 云服务，使开发人员可以使用存储数据，它将是高度可用、 安全、 持久、 可缩放和冗余的保险。</span><span class="sxs-lookup"><span data-stu-id="32de1-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="32de1-118">这意味着，Microsoft 将为您处理所有维护和关键问题。</span><span class="sxs-lookup"><span data-stu-id="32de1-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="32de1-119">有关详细信息，请访问[Azure 存储文章](https://docs.microsoft.com/azure/storage/common/storage-introduction)。</span><span class="sxs-lookup"><span data-stu-id="32de1-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="32de1-120">已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="32de1-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="32de1-121">允许用户看围绕一个场景。</span><span class="sxs-lookup"><span data-stu-id="32de1-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="32de1-122">触发生成的对象，当用户在一个三维 'button' gazes。</span><span class="sxs-lookup"><span data-stu-id="32de1-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="32de1-123">生成的对象将选择的 Azure 函数。</span><span class="sxs-lookup"><span data-stu-id="32de1-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="32de1-124">在生成的每个对象，该应用程序会将存储在中的对象类型*Azure 文件*，它位于*Azure 存储*。</span><span class="sxs-lookup"><span data-stu-id="32de1-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="32de1-125">在加载第二次*Azure 文件*将检索数据，并将其用它来重播从应用程序的前一个实例的生成操作。</span><span class="sxs-lookup"><span data-stu-id="32de1-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="32de1-126">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="32de1-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="32de1-127">本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="32de1-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="32de1-128">它是作业以使用此课程以增强你的混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="32de1-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="32de1-129">设备支持</span><span class="sxs-lookup"><span data-stu-id="32de1-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="32de1-130">课程</span><span class="sxs-lookup"><span data-stu-id="32de1-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="32de1-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="32de1-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="32de1-132"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="32de1-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="32de1-133">MR 和 Azure 305:函数和存储</span><span class="sxs-lookup"><span data-stu-id="32de1-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="32de1-134">✔️</span><span class="sxs-lookup"><span data-stu-id="32de1-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="32de1-135">✔️</span><span class="sxs-lookup"><span data-stu-id="32de1-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="32de1-136">尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="32de1-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="32de1-137">按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。</span><span class="sxs-lookup"><span data-stu-id="32de1-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32de1-138">系统必备</span><span class="sxs-lookup"><span data-stu-id="32de1-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="32de1-139">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="32de1-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="32de1-140">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="32de1-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="32de1-141">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="32de1-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="32de1-142">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="32de1-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="32de1-143">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="32de1-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="32de1-144">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="32de1-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="32de1-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="32de1-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="32de1-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="32de1-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="32de1-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="32de1-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="32de1-148">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="32de1-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="32de1-149">对用于创建 Azure 资源的 Azure 帐户的订阅</span><span class="sxs-lookup"><span data-stu-id="32de1-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="32de1-150">用于 Azure 的安装程序和数据检索的 Internet 访问权限</span><span class="sxs-lookup"><span data-stu-id="32de1-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="32de1-151">开始之前</span><span class="sxs-lookup"><span data-stu-id="32de1-151">Before you start</span></span>

<span data-ttu-id="32de1-152">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="32de1-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="32de1-153">第 1 章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="32de1-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="32de1-154">若要使用**Azure 存储服务**，将需要创建和配置**存储帐户**在 Azure 门户中。</span><span class="sxs-lookup"><span data-stu-id="32de1-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="32de1-155">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="32de1-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="32de1-156">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="32de1-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="32de1-157">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="32de1-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="32de1-158">你登录后，单击**新建**在左上角，并搜索*存储帐户*，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="32de1-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure 存储空间搜索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="32de1-160">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="32de1-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="32de1-161">该新页面将提供的说明*Azure 存储帐户*服务。</span><span class="sxs-lookup"><span data-stu-id="32de1-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="32de1-162">在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="32de1-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![创建服务](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="32de1-164">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="32de1-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="32de1-165">插入*名称*对于你的帐户，请注意此字段仅接受数字和小写字母。</span><span class="sxs-lookup"><span data-stu-id="32de1-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="32de1-166">有关*部署模型*，选择**资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="32de1-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="32de1-167">有关*帐户类型*，选择**存储 (常规用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="32de1-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="32de1-168">确定*位置*为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="32de1-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="32de1-169">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="32de1-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="32de1-170">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="32de1-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="32de1-171">有关*复制*选择**读取-访问-异地冗余存储 (RA-GRS)**。</span><span class="sxs-lookup"><span data-stu-id="32de1-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="32de1-172">有关*性能*，选择**标准**。</span><span class="sxs-lookup"><span data-stu-id="32de1-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="32de1-173">将保留*需要安全传输*作为**禁用**。</span><span class="sxs-lookup"><span data-stu-id="32de1-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="32de1-174">选择*订阅*。</span><span class="sxs-lookup"><span data-stu-id="32de1-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="32de1-175">选择*资源组*或新建一个。</span><span class="sxs-lookup"><span data-stu-id="32de1-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="32de1-176">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="32de1-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="32de1-177">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="32de1-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="32de1-178">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="32de1-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="32de1-179">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="32de1-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="32de1-180">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="32de1-180">Select **Create**.</span></span>

        ![输入的服务信息](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="32de1-182">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="32de1-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="32de1-183">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="32de1-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![在 azure 门户中的新通知](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="32de1-185">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="32de1-185">Click on the notifications to explore your new Service instance.</span></span>

    ![转到资源](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="32de1-187">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="32de1-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="32de1-188">你将会转到新*存储帐户*服务实例。</span><span class="sxs-lookup"><span data-stu-id="32de1-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![访问密钥](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="32de1-190">单击*访问密钥*，以显示此云服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="32de1-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="32de1-191">使用*记事本*或类似，供以后使用其中一个密钥复制到。</span><span class="sxs-lookup"><span data-stu-id="32de1-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="32de1-192">另请注意*连接字符串*值，因为它将在中使用*azure 服务*类，该类将更高版本创建。</span><span class="sxs-lookup"><span data-stu-id="32de1-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![复制连接字符串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="32de1-194">第 2 章-设置 Azure 函数</span><span class="sxs-lookup"><span data-stu-id="32de1-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="32de1-195">现在，您将编写**Azure** **函数**Azure 服务中。</span><span class="sxs-lookup"><span data-stu-id="32de1-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="32de1-196">可以使用**Azure Function**来执行几乎所有操作，你将处理经典函数在代码中，不同之处在于，此函数可由任何应用程序有访问你的 Azure 帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="32de1-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="32de1-197">若要创建 Azure 函数：</span><span class="sxs-lookup"><span data-stu-id="32de1-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="32de1-198">从你*Azure 门户*，单击**新建**在左上角，并搜索*Function App*，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="32de1-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![创建 function app](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="32de1-200">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="32de1-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="32de1-201">该新页面将提供的说明*Azure Function App*服务。</span><span class="sxs-lookup"><span data-stu-id="32de1-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="32de1-202">在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="32de1-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![函数应用信息](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="32de1-204">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="32de1-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="32de1-205">提供*应用名称*。</span><span class="sxs-lookup"><span data-stu-id="32de1-205">Provide an *App name*.</span></span> <span data-ttu-id="32de1-206">可以在此处使用字母和数字 （允许使用大写或小写）。</span><span class="sxs-lookup"><span data-stu-id="32de1-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="32de1-207">选择首选*订阅*。</span><span class="sxs-lookup"><span data-stu-id="32de1-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="32de1-208">选择*资源组*或新建一个。</span><span class="sxs-lookup"><span data-stu-id="32de1-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="32de1-209">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="32de1-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="32de1-210">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="32de1-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="32de1-211">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="32de1-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="32de1-212">对于此练习中，选择*Windows*作为所选**OS**。</span><span class="sxs-lookup"><span data-stu-id="32de1-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="32de1-213">选择*消耗计划*有关**托管计划**。</span><span class="sxs-lookup"><span data-stu-id="32de1-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="32de1-214">确定*位置*为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="32de1-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="32de1-215">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="32de1-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="32de1-216">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="32de1-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="32de1-217">为了获得最佳性能的存储帐户中选择的同一区域。</span><span class="sxs-lookup"><span data-stu-id="32de1-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="32de1-218">有关*存储*，选择**使用现有**，然后使用下拉列表菜单中，找到你之前创建的存储。</span><span class="sxs-lookup"><span data-stu-id="32de1-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="32de1-219">将保留*Application Insights*关闭对于此练习。</span><span class="sxs-lookup"><span data-stu-id="32de1-219">Leave *Application Insights* off for this exercise.</span></span>

        ![输入的函数应用的详细信息](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="32de1-221">单击“创建”按钮。</span><span class="sxs-lookup"><span data-stu-id="32de1-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="32de1-222">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="32de1-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="32de1-223">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="32de1-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新 azure 门户通知](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="32de1-225">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="32de1-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![转到资源函数应用](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="32de1-227">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="32de1-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="32de1-228">你将会转到新*Function App*服务实例。</span><span class="sxs-lookup"><span data-stu-id="32de1-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="32de1-229">上*Function App*仪表板中，将鼠标悬停*函数*，在左侧面板中找到，然后单击 **+ （加）** 符号。</span><span class="sxs-lookup"><span data-stu-id="32de1-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![创建新的函数](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="32de1-231">在下一页上，确保**Webhook + API**已选中，并为*选择一种语言，* 选择**CSharp**，因为它是本教程中使用的语言。</span><span class="sxs-lookup"><span data-stu-id="32de1-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="32de1-232">最后，单击**创建此函数**按钮。</span><span class="sxs-lookup"><span data-stu-id="32de1-232">Lastly, click the **Create this function** button.</span></span>

    ![选择 web 挂钩 csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="32de1-234">应会转到代码页 (run.csx)，否则，单击左侧面板内的函数列表中新创建的函数。</span><span class="sxs-lookup"><span data-stu-id="32de1-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![打开新的函数](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="32de1-236">将以下代码复制到你的函数。</span><span class="sxs-lookup"><span data-stu-id="32de1-236">Copy the following code into your function.</span></span> <span data-ttu-id="32de1-237">此函数只需将返回介于 0 和 2 调用时之间的随机整数。</span><span class="sxs-lookup"><span data-stu-id="32de1-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="32de1-238">不要担心现有代码，可随意将粘贴到顶部。</span><span class="sxs-lookup"><span data-stu-id="32de1-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="32de1-239">选择“保存”。</span><span class="sxs-lookup"><span data-stu-id="32de1-239">Select **Save**.</span></span>

14. <span data-ttu-id="32de1-240">结果应如下图所示。</span><span class="sxs-lookup"><span data-stu-id="32de1-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="32de1-241">单击**获取函数 URL**并记下*终结点*显示。</span><span class="sxs-lookup"><span data-stu-id="32de1-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="32de1-242">将需要将其插入到*azure 服务*将稍后在本课程中创建的类。</span><span class="sxs-lookup"><span data-stu-id="32de1-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![获取函数终结点](images/AzureLabs-Lab5-16.png)

    ![获取函数终结点](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="32de1-245">第 3 章 — 设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="32de1-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="32de1-246">以下是一组典型使用 Mixed Reality 开发并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="32de1-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="32de1-247">设置和测试您的混合的现实沉浸式头戴式。</span><span class="sxs-lookup"><span data-stu-id="32de1-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="32de1-248">你将**不**此课程需要运动控制器。</span><span class="sxs-lookup"><span data-stu-id="32de1-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="32de1-249">如果需要支持沉浸式头戴式设置，请[访问混合的现实设置文章](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="32de1-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="32de1-250">打开 Unity，然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="32de1-250">Open Unity and click **New**.</span></span>

    ![创建新的 unity 项目](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="32de1-252">现在，需要提供 Unity 项目的名称。</span><span class="sxs-lookup"><span data-stu-id="32de1-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="32de1-253">插入**MR_Azure_Functions**。</span><span class="sxs-lookup"><span data-stu-id="32de1-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="32de1-254">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="32de1-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="32de1-255">设置*位置*到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="32de1-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="32de1-256">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="32de1-256">Then, click **Create project**.</span></span>

    ![为新的 unity 项目提供一个名称](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="32de1-258">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="32de1-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="32de1-259">转到 **编辑* > *首选项** ，然后在新窗口中，导航到 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="32de1-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="32de1-260">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="32de1-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="32de1-261">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="32de1-261">Close the **Preferences** window.</span></span>

    ![设置 visual studio 为脚本编辑器](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="32de1-263">接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="32de1-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![切换到 uwp 的平台](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="32de1-265">转到**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="32de1-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="32de1-266">**设备为目标**设置为**任一设备**。</span><span class="sxs-lookup"><span data-stu-id="32de1-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="32de1-267">对于 Microsoft HoloLens**目标设备**到*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="32de1-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="32de1-268">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="32de1-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="32de1-269">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="32de1-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="32de1-270">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="32de1-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="32de1-271">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="32de1-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="32de1-272">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="32de1-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="32de1-273">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="32de1-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="32de1-274">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="32de1-274">A save window will appear.</span></span>

            ![添加打开场景](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="32de1-276">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="32de1-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![创建场景文件夹](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="32de1-278">打开新建**场景**文件夹，然后在**文件名：** 文本字段中，键入**FunctionsScene**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="32de1-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![保存函数场景](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="32de1-280">中的剩余设置，**生成设置**，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="32de1-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![保存函数场景](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="32de1-282">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="32de1-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![检查器中的播放机设置](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="32de1-284">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="32de1-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="32de1-285">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="32de1-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="32de1-286">**脚本运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="32de1-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="32de1-287">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="32de1-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="32de1-288">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="32de1-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="32de1-289">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="32de1-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="32de1-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="32de1-290">**InternetClient**</span></span>

            ![组功能](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="32de1-292">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows Mixed RealitySDK**添加。</span><span class="sxs-lookup"><span data-stu-id="32de1-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 XR 设置](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="32de1-294">回到*生成设置* *UnityC#项目*不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="32de1-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![刻度线的 c# 项目](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="32de1-296">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="32de1-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="32de1-297">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="32de1-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="32de1-298">第 4 章-安装程序主照相机</span><span class="sxs-lookup"><span data-stu-id="32de1-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32de1-299">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)，并将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="32de1-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="32de1-300">这还将包含下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="32de1-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="32de1-301">导入后，继续从[第 7 章](#chapter-7---create-the-azureservices-class)。</span><span class="sxs-lookup"><span data-stu-id="32de1-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="32de1-302">在中*层次结构面板*，您会发现一个名为对象**Main Camera**，"内部"应用程序后，此对象表示"head"的观点。</span><span class="sxs-lookup"><span data-stu-id="32de1-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="32de1-303">准备好 Unity 仪表板中，选择**主相机 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="32de1-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="32de1-304">您会注意*检查器面板*（通常右侧，在仪表板中找到） 将显示的各种组件*GameObject*，与*转换*在顶部后, 接*照相机*，而另一些其他组件。</span><span class="sxs-lookup"><span data-stu-id="32de1-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="32de1-305">你将需要重置的转换的 Main Camera，使其正确定位。</span><span class="sxs-lookup"><span data-stu-id="32de1-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="32de1-306">若要执行此操作，请选择**齿轮**旁的摄像机*转换*组件，然后选择**重置**。</span><span class="sxs-lookup"><span data-stu-id="32de1-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![重置转换](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="32de1-308">然后更新**转换**组件如下所示：</span><span class="sxs-lookup"><span data-stu-id="32de1-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="32de1-309">转换的位置</span><span class="sxs-lookup"><span data-stu-id="32de1-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="32de1-310">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-310">**X**</span></span>   | <span data-ttu-id="32de1-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-311">**Y**</span></span>                     | <span data-ttu-id="32de1-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-312">**Z**</span></span> |
    | <span data-ttu-id="32de1-313">0</span><span class="sxs-lookup"><span data-stu-id="32de1-313">0</span></span>       | <span data-ttu-id="32de1-314">1</span><span class="sxs-lookup"><span data-stu-id="32de1-314">1</span></span>                         | <span data-ttu-id="32de1-315">0</span><span class="sxs-lookup"><span data-stu-id="32de1-315">0</span></span>     |    

    |       | <span data-ttu-id="32de1-316">转换的旋转</span><span class="sxs-lookup"><span data-stu-id="32de1-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="32de1-317">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-317">**X**</span></span> | <span data-ttu-id="32de1-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-318">**Y**</span></span>                | <span data-ttu-id="32de1-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-319">**Z**</span></span> |
    | <span data-ttu-id="32de1-320">0</span><span class="sxs-lookup"><span data-stu-id="32de1-320">0</span></span>     | <span data-ttu-id="32de1-321">0</span><span class="sxs-lookup"><span data-stu-id="32de1-321">0</span></span>                    | <span data-ttu-id="32de1-322">0</span><span class="sxs-lookup"><span data-stu-id="32de1-322">0</span></span>     |

    |       | <span data-ttu-id="32de1-323">转换-横向</span><span class="sxs-lookup"><span data-stu-id="32de1-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="32de1-324">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-324">**X**</span></span> | <span data-ttu-id="32de1-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-325">**Y**</span></span>             | <span data-ttu-id="32de1-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-326">**Z**</span></span> |
    | <span data-ttu-id="32de1-327">1</span><span class="sxs-lookup"><span data-stu-id="32de1-327">1</span></span>     | <span data-ttu-id="32de1-328">1</span><span class="sxs-lookup"><span data-stu-id="32de1-328">1</span></span>                 | <span data-ttu-id="32de1-329">1</span><span class="sxs-lookup"><span data-stu-id="32de1-329">1</span></span>     |

    ![集相机转换](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="32de1-331">第 5 章-设置在 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="32de1-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="32de1-332">在空白区域中单击右键*层次结构面板*下**三维对象**，将添加**平面**。</span><span class="sxs-lookup"><span data-stu-id="32de1-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![创建新计划](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="32de1-334">与**平面**对象选择，更改中的以下参数*检查器面板*:</span><span class="sxs-lookup"><span data-stu-id="32de1-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="32de1-335">转换的位置</span><span class="sxs-lookup"><span data-stu-id="32de1-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="32de1-336">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-336">**X**</span></span> | <span data-ttu-id="32de1-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-337">**Y**</span></span>                | <span data-ttu-id="32de1-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-338">**Z**</span></span> |
    | <span data-ttu-id="32de1-339">0</span><span class="sxs-lookup"><span data-stu-id="32de1-339">0</span></span>     | <span data-ttu-id="32de1-340">0</span><span class="sxs-lookup"><span data-stu-id="32de1-340">0</span></span>                    | <span data-ttu-id="32de1-341">4</span><span class="sxs-lookup"><span data-stu-id="32de1-341">4</span></span>     |

    |       | <span data-ttu-id="32de1-342">转换-横向</span><span class="sxs-lookup"><span data-stu-id="32de1-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="32de1-343">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-343">**X**</span></span> | <span data-ttu-id="32de1-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-344">**Y**</span></span>             | <span data-ttu-id="32de1-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-345">**Z**</span></span> |
    | <span data-ttu-id="32de1-346">10</span><span class="sxs-lookup"><span data-stu-id="32de1-346">10</span></span>    | <span data-ttu-id="32de1-347">1</span><span class="sxs-lookup"><span data-stu-id="32de1-347">1</span></span>                 | <span data-ttu-id="32de1-348">10</span><span class="sxs-lookup"><span data-stu-id="32de1-348">10</span></span>    |

    ![设置平面位置和缩放](images/AzureLabs-Lab5-32.png)

    ![平面的场景视图](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="32de1-351">在的空白区域中单击右键*层次结构面板*下**三维对象**，将添加**多维数据集**。</span><span class="sxs-lookup"><span data-stu-id="32de1-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="32de1-352">重命名为多维数据集**GazeButton** （选定的多维数据集，按 F2）。</span><span class="sxs-lookup"><span data-stu-id="32de1-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="32de1-353">更改中的以下参数*检查器面板*:</span><span class="sxs-lookup"><span data-stu-id="32de1-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="32de1-354">转换的位置</span><span class="sxs-lookup"><span data-stu-id="32de1-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="32de1-355">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-355">**X**</span></span> | <span data-ttu-id="32de1-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-356">**Y**</span></span>                | <span data-ttu-id="32de1-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-357">**Z**</span></span> |
        | <span data-ttu-id="32de1-358">0</span><span class="sxs-lookup"><span data-stu-id="32de1-358">0</span></span>     | <span data-ttu-id="32de1-359">3</span><span class="sxs-lookup"><span data-stu-id="32de1-359">3</span></span>                    | <span data-ttu-id="32de1-360">5</span><span class="sxs-lookup"><span data-stu-id="32de1-360">5</span></span>     |


        ![集的视线移动按钮转换](images/AzureLabs-Lab5-34.png)

        ![对此按钮场景视图](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="32de1-363">单击**标记**下拉列表按钮，然后单击**添加标记**以打开*标记和图层窗格*。</span><span class="sxs-lookup"><span data-stu-id="32de1-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![添加新标记](images/AzureLabs-Lab5-36.png)

        ![选择加号](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="32de1-366">选择 **+ （加）** 按钮，然后在*新标记名称*字段中，输入**GazeButton**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="32de1-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![新的用户名标记](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="32de1-368">单击**GazeButton**对象中*层次结构面板*，然后在*检查器面板*，将分配新创建**GazeButton**标记。</span><span class="sxs-lookup"><span data-stu-id="32de1-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![分配新标记的视线移动按钮](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="32de1-370">右键单击**GazeButton**对象，在*层次结构面板*，并添加**空的 GameObject** (这将添加为*子*对象的名称。</span><span class="sxs-lookup"><span data-stu-id="32de1-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="32de1-371">选择新的对象，并将其重命名**ShapeSpawnPoint**。</span><span class="sxs-lookup"><span data-stu-id="32de1-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="32de1-372">更改中的以下参数*检查器面板*:</span><span class="sxs-lookup"><span data-stu-id="32de1-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="32de1-373">转换的位置</span><span class="sxs-lookup"><span data-stu-id="32de1-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="32de1-374">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-374">**X**</span></span> |<span data-ttu-id="32de1-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-375">**Y**</span></span>                 | <span data-ttu-id="32de1-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-376">**Z**</span></span> |
        | <span data-ttu-id="32de1-377">0</span><span class="sxs-lookup"><span data-stu-id="32de1-377">0</span></span>     | <span data-ttu-id="32de1-378">-1</span><span class="sxs-lookup"><span data-stu-id="32de1-378">-1</span></span>                   | <span data-ttu-id="32de1-379">0</span><span class="sxs-lookup"><span data-stu-id="32de1-379">0</span></span>     |

        ![更新形状生成点转换](images/AzureLabs-Lab5-40.png)

        ![形状生成点场景视图](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="32de1-382">接下来将创建**三维文字**对象以提供有关 Azure 服务的状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="32de1-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="32de1-383">右键单击**GazeButton**层次结构中面板再次并添加**三维对象 > 三维文字**对象作为*子*。</span><span class="sxs-lookup"><span data-stu-id="32de1-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![创建新的三维文字对象](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="32de1-385">重命名**三维文字**对象传递给**AzureStatusText**。</span><span class="sxs-lookup"><span data-stu-id="32de1-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="32de1-386">更改**AzureStatusText**对象转换为如下所示：</span><span class="sxs-lookup"><span data-stu-id="32de1-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="32de1-387">转换的位置</span><span class="sxs-lookup"><span data-stu-id="32de1-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="32de1-388">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-388">**X**</span></span> | <span data-ttu-id="32de1-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-389">**Y**</span></span>                | <span data-ttu-id="32de1-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-390">**Z**</span></span> |
    | <span data-ttu-id="32de1-391">0</span><span class="sxs-lookup"><span data-stu-id="32de1-391">0</span></span>     | <span data-ttu-id="32de1-392">0</span><span class="sxs-lookup"><span data-stu-id="32de1-392">0</span></span>                    | <span data-ttu-id="32de1-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="32de1-393">-0.6</span></span>  |

    |       | <span data-ttu-id="32de1-394">转换-横向</span><span class="sxs-lookup"><span data-stu-id="32de1-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="32de1-395">**X**</span><span class="sxs-lookup"><span data-stu-id="32de1-395">**X**</span></span> | <span data-ttu-id="32de1-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="32de1-396">**Y**</span></span>             | <span data-ttu-id="32de1-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="32de1-397">**Z**</span></span> |
    | <span data-ttu-id="32de1-398">0.1</span><span class="sxs-lookup"><span data-stu-id="32de1-398">0.1</span></span>   | <span data-ttu-id="32de1-399">0.1</span><span class="sxs-lookup"><span data-stu-id="32de1-399">0.1</span></span>               | <span data-ttu-id="32de1-400">0.1</span><span class="sxs-lookup"><span data-stu-id="32de1-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="32de1-401">如果它似乎是关闭中心，因为这将在修复时不用再担心文本网格下方组件已更新。</span><span class="sxs-lookup"><span data-stu-id="32de1-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="32de1-402">更改**文本 Mesh**组件以匹配下面：</span><span class="sxs-lookup"><span data-stu-id="32de1-402">Change the **Text Mesh** component to match the below:</span></span>

    ![设置文本网格组件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="32de1-404">所选的颜色是十六进制颜色：**000000FF**，但可随意选择你自己，只需确保它是可读。</span><span class="sxs-lookup"><span data-stu-id="32de1-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="32de1-405">层次结构面板结构现在应如下所示：</span><span class="sxs-lookup"><span data-stu-id="32de1-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![文本在场景视图中的网格](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="32de1-407">您的场景现在应如下所示：</span><span class="sxs-lookup"><span data-stu-id="32de1-407">Your scene should now look like this:</span></span>

    ![文本在场景视图中的网格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="32de1-409">第 6 章-为 Unity 中导入 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="32de1-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="32de1-410">您将使用 Azure 存储于 Unity （其本身使用.Net 的 Azure SDK）。</span><span class="sxs-lookup"><span data-stu-id="32de1-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="32de1-411">你可以阅读更多有关此[Unity 项目的 Azure 存储](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="32de1-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="32de1-412">这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。</span><span class="sxs-lookup"><span data-stu-id="32de1-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="32de1-413">这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。</span><span class="sxs-lookup"><span data-stu-id="32de1-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="32de1-414">若要导入您自己的项目的 SDK，请确保已下载最新[从 GitHub.unitypackage](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="32de1-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="32de1-415">然后，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="32de1-415">Then, do the following:</span></span>

1.  <span data-ttu-id="32de1-416">添加 **.unitypackage**通过使用到 Unity 文件**资产 > 导入包 > 自定义包**菜单选项。</span><span class="sxs-lookup"><span data-stu-id="32de1-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="32de1-417">在中 **导入 Unity 程序包** 框，弹出，你可以选择下的所有内容 \**插件* > \*存储\*\*。</span><span class="sxs-lookup"><span data-stu-id="32de1-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="32de1-418">取消选中其他任何内容，因为它不需要此课程。</span><span class="sxs-lookup"><span data-stu-id="32de1-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![导入包](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="32de1-420">单击**导入**按钮将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="32de1-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="32de1-421">转到*存储*下的文件夹*插件*，在项目视图中，选择以下插件*仅*:</span><span class="sxs-lookup"><span data-stu-id="32de1-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="32de1-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="32de1-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="32de1-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="32de1-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="32de1-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="32de1-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="32de1-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="32de1-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="32de1-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="32de1-426">System.Spatial</span></span>

        ![取消选中任何平台](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="32de1-428">与*这些特定插件*选择，**取消选中** *Any 平台*并**取消选中** *WSAPlayer*然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="32de1-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![应用平台 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="32de1-430">我们将会使这些特定的插件，只使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="32de1-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="32de1-431">这是因为存在不同版本的项目会导出从 Unity 后，将使用 WSA 文件夹中的同一个插件。</span><span class="sxs-lookup"><span data-stu-id="32de1-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="32de1-432">在中*存储*插件文件夹中，只选择：</span><span class="sxs-lookup"><span data-stu-id="32de1-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="32de1-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="32de1-433">Microsoft.Data.Services.Client</span></span>

        ![组不处理的 dll](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="32de1-435">检查**不进程**框下*平台设置*然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="32de1-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![应用不会进行处理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="32de1-437">我们会将标记此插件"不处理"因为 Unity 程序集 patcher 有处理此插件的难度。</span><span class="sxs-lookup"><span data-stu-id="32de1-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="32de1-438">即使未处理，该插件仍将起作用。</span><span class="sxs-lookup"><span data-stu-id="32de1-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="32de1-439">章 7-创建 azure 服务类</span><span class="sxs-lookup"><span data-stu-id="32de1-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="32de1-440">要创建的第一个类是*azure 服务*类。</span><span class="sxs-lookup"><span data-stu-id="32de1-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="32de1-441">*Azure 服务*类将负责：</span><span class="sxs-lookup"><span data-stu-id="32de1-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="32de1-442">将 Azure 帐户凭据的存储。</span><span class="sxs-lookup"><span data-stu-id="32de1-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="32de1-443">调用 Azure 函数应用。</span><span class="sxs-lookup"><span data-stu-id="32de1-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="32de1-444">上传和下载数据文件在 Azure 云存储中。</span><span class="sxs-lookup"><span data-stu-id="32de1-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="32de1-445">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="32de1-445">To create this Class:</span></span>

1.  <span data-ttu-id="32de1-446">在中右击*资产*文件夹中，在项目面板中，位于**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="32de1-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="32de1-447">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="32de1-447">Name the folder **Scripts**.</span></span>

    ![创建新文件夹](images/AzureLabs-Lab5-50.png)

    ![将文件夹的脚本](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="32de1-450">双击刚创建的文件夹，以将其打开。</span><span class="sxs-lookup"><span data-stu-id="32de1-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="32de1-451">在文件夹中，右键单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="32de1-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="32de1-452">调用脚本*azure 服务*。</span><span class="sxs-lookup"><span data-stu-id="32de1-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="32de1-453">双击新*azure 服务*类以打开其与*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="32de1-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="32de1-454">将以下命名空间添加到顶部*azure 服务*:</span><span class="sxs-lookup"><span data-stu-id="32de1-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="32de1-455">添加以下检查器字段内*azure 服务*类：</span><span class="sxs-lookup"><span data-stu-id="32de1-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="32de1-456">然后添加以下成员变量内的*azure 服务*类：</span><span class="sxs-lookup"><span data-stu-id="32de1-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="32de1-457">请确保您替换*终结点*并*连接字符串*在 Azure 门户中找到的值与 Azure 存储的值</span><span class="sxs-lookup"><span data-stu-id="32de1-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="32de1-458">为代码*Awake()* 并*start （)* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="32de1-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="32de1-459">类初始化时，将会调用这些方法：</span><span class="sxs-lookup"><span data-stu-id="32de1-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="32de1-460">我们的代码中将填充*CallAzureFunctionForNextShape()* 中[未来一章](#chapter-10---completing-the-AzureServices-class)。</span><span class="sxs-lookup"><span data-stu-id="32de1-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="32de1-461">删除*update （)* 方法因为此类不会使用它。</span><span class="sxs-lookup"><span data-stu-id="32de1-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="32de1-462">在 Visual Studio 中，保存所做的更改，然后返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="32de1-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="32de1-463">单击并拖动*azure 服务*从脚本文件夹中的 Main Camera 对象的类*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="32de1-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="32de1-464">选择主相机，然后抓取**AzureStatusText**从下方的子对象**GazeButton**对象，并将其内放置**AzureStatusText**引用目标字段中*Inspector*，以提供对引用*azure 服务*脚本。</span><span class="sxs-lookup"><span data-stu-id="32de1-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![分配 azure 状态文本引用目标](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="32de1-466">章 8-创建 ShapeFactory 类</span><span class="sxs-lookup"><span data-stu-id="32de1-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="32de1-467">若要创建，下一个脚本是*ShapeFactory*类。</span><span class="sxs-lookup"><span data-stu-id="32de1-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="32de1-468">此类角色是请求时，创建新形状，并保留历史记录中创建形状*形状历史记录列表*。</span><span class="sxs-lookup"><span data-stu-id="32de1-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="32de1-469">每次创建形状时，*形状历史记录列表*中更新*AzureService*类，并随后将存储在你*Azure 存储*。</span><span class="sxs-lookup"><span data-stu-id="32de1-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="32de1-470">在应用程序启动时，如果存储的文件中找到你*Azure 存储*，则*形状历史记录列表*检索并将其重播，具有**三维文字**对象提供生成的形状是否从存储，或新。</span><span class="sxs-lookup"><span data-stu-id="32de1-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="32de1-471">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="32de1-471">To create this class:</span></span>

1.  <span data-ttu-id="32de1-472">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="32de1-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="32de1-473">在文件夹中，右键单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="32de1-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="32de1-474">调用脚本*ShapeFactory*。</span><span class="sxs-lookup"><span data-stu-id="32de1-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="32de1-475">双击新*ShapeFactory*脚本以将其与打开*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="32de1-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="32de1-476">请确保*ShapeFactory*类包括以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="32de1-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="32de1-477">添加到如下所示的变量*ShapeFactory*类，并替换*start （)* 并*Awake()* 与下面的函数：</span><span class="sxs-lookup"><span data-stu-id="32de1-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="32de1-478">*CreateShape()* 方法将生成基于所提供的基元形状*整数*参数。</span><span class="sxs-lookup"><span data-stu-id="32de1-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="32de1-479">用于指定当前创建的形状是从存储，或新的布尔参数。</span><span class="sxs-lookup"><span data-stu-id="32de1-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="32de1-480">将以下代码中的您*ShapeFactory*类，以前的方法如下：</span><span class="sxs-lookup"><span data-stu-id="32de1-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="32de1-481">请确保在返回到 Unity 之前的 Visual Studio 中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="32de1-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="32de1-482">返回在 Unity 编辑器中，单击并拖动*ShapeFactory*类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*.</span><span class="sxs-lookup"><span data-stu-id="32de1-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="32de1-483">您会发现与所选 Main Camera *ShapeFactory*脚本组件缺少*衍生点*引用。</span><span class="sxs-lookup"><span data-stu-id="32de1-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="32de1-484">若要修复它，请拖动**ShapeSpawnPoint**对象从*层次结构面板*到**衍生点**引用目标。</span><span class="sxs-lookup"><span data-stu-id="32de1-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![组形状工厂引用目标](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="32de1-486">章 9-创建的视线移动类</span><span class="sxs-lookup"><span data-stu-id="32de1-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="32de1-487">若要创建所需的最后一个脚本是*注视*类。</span><span class="sxs-lookup"><span data-stu-id="32de1-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="32de1-488">此类负责创建**Raycast**将从 Main Camera，以检测用户正在通过哪个对象向前投影的。</span><span class="sxs-lookup"><span data-stu-id="32de1-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="32de1-489">在这种情况下，Raycast 将需要确定如果用户寻求**GazeButton**对象在场景中，并触发一个行为。</span><span class="sxs-lookup"><span data-stu-id="32de1-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="32de1-490">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="32de1-490">To create this Class:</span></span>

1.  <span data-ttu-id="32de1-491">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="32de1-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="32de1-492">在项目面板中，右键单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="32de1-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="32de1-493">调用脚本*注视*。</span><span class="sxs-lookup"><span data-stu-id="32de1-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="32de1-494">双击新*注视*脚本以将其与打开*Visual Studio。*</span><span class="sxs-lookup"><span data-stu-id="32de1-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="32de1-495">请确保以下命名空间是包括在脚本顶部：</span><span class="sxs-lookup"><span data-stu-id="32de1-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="32de1-496">然后添加以下变量内的*注视*类：</span><span class="sxs-lookup"><span data-stu-id="32de1-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="32de1-497">其中一些变量将能够在中进行编辑*编辑器*。</span><span class="sxs-lookup"><span data-stu-id="32de1-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="32de1-498">为代码*Awake()* 并*start （)* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="32de1-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="32de1-499">添加以下代码，将创建游标对象处开始，连同*update （)* 方法，将运行 Raycast 方法，以及在其中切换 GazeEnabled 布尔值：</span><span class="sxs-lookup"><span data-stu-id="32de1-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="32de1-500">接下来，添加*UpdateRaycast()* 方法，它将项目 Raycast 并检测命中的目标。</span><span class="sxs-lookup"><span data-stu-id="32de1-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="32de1-501">最后，将添加*ResetFocusedObject()* 方法，它将切换 GazeButton 对象当前颜色，指示它是否创建一个新的形状。</span><span class="sxs-lookup"><span data-stu-id="32de1-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="32de1-502">返回到 Unity 之前，Visual Studio 中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="32de1-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="32de1-503">单击并拖动*注视*到脚本文件夹中的类**Main Camera**对象中*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="32de1-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="32de1-504">第 10 章-完成 azure 服务类</span><span class="sxs-lookup"><span data-stu-id="32de1-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="32de1-505">与其他脚本中的位置，现在就可以*完整* *azure 服务*类。</span><span class="sxs-lookup"><span data-stu-id="32de1-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="32de1-506">将通过实现此目的：</span><span class="sxs-lookup"><span data-stu-id="32de1-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="32de1-507">添加名为的新方法*CreateCloudIdentityAsync()*，若要设置用于与 Azure 进行通信所需的身份验证变量。</span><span class="sxs-lookup"><span data-stu-id="32de1-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="32de1-508">此方法还将检查存在包含形状列表的以前存储文件。</span><span class="sxs-lookup"><span data-stu-id="32de1-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="32de1-509">**如果找到该文件**，它将禁用的用户*注视*，并触发形状创建过程中，根据形状的模式，如存储在**Azure 存储文件**。</span><span class="sxs-lookup"><span data-stu-id="32de1-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="32de1-510">用户可以看到这一点，作为**文本 Mesh**将提供显示存储或 New，具体取决于形状原点。</span><span class="sxs-lookup"><span data-stu-id="32de1-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="32de1-511">**如果未找到文件**，它可实现*注视*，使用户可以在查看时创建的形状**GazeButton**场景中的对象。</span><span class="sxs-lookup"><span data-stu-id="32de1-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="32de1-512">下一步的代码片段是从*start （)* 方法; 其中一个调用将对*CreateCloudIdentityAsync()* 方法。</span><span class="sxs-lookup"><span data-stu-id="32de1-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="32de1-513">可随意复制您的当前*start （)* 方法中，使用如下：</span><span class="sxs-lookup"><span data-stu-id="32de1-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="32de1-514">方法的代码中填写*CallAzureFunctionForNextShape()*。</span><span class="sxs-lookup"><span data-stu-id="32de1-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="32de1-515">您将使用之前创建*Azure Function App*来请求一个形状的索引。</span><span class="sxs-lookup"><span data-stu-id="32de1-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="32de1-516">此方法后收到新形状时，会将发送到形状*ShapeFactory*类，以在场景中创建新的形状。</span><span class="sxs-lookup"><span data-stu-id="32de1-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="32de1-517">使用下面的代码来完成的正文*CallAzureFunctionForNextShape()*。</span><span class="sxs-lookup"><span data-stu-id="32de1-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="32de1-518">添加一个方法来创建字符串，通过串联整数存储在形状历史记录列表中，并保存在你*Azure 存储文件*。</span><span class="sxs-lookup"><span data-stu-id="32de1-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="32de1-519">添加一个方法以便检索存储在文件中的文本你*Azure 存储文件*并*反序列化*到列表。</span><span class="sxs-lookup"><span data-stu-id="32de1-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="32de1-520">完成此过程后，该方法将重新启用的视线移动，以便用户可以向场景添加更多的形状。</span><span class="sxs-lookup"><span data-stu-id="32de1-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="32de1-521">返回到 Unity 之前，Visual Studio 中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="32de1-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="32de1-522">第 11 章 — 生成 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="32de1-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="32de1-523">若要开始生成过程：</span><span class="sxs-lookup"><span data-stu-id="32de1-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="32de1-524">转到**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="32de1-524">Go to **File > Build Settings**.</span></span>

    ![生成应用](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="32de1-526">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="32de1-526">Click **Build**.</span></span> <span data-ttu-id="32de1-527">将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="32de1-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="32de1-528">现在，创建该文件夹并将其命名*应用*。</span><span class="sxs-lookup"><span data-stu-id="32de1-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="32de1-529">然后使用*应用程序*文件夹选择，按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="32de1-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="32de1-530">Unity 将开始构建您的项目*应用*文件夹。</span><span class="sxs-lookup"><span data-stu-id="32de1-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="32de1-531">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开*文件资源管理器*窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="32de1-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="32de1-532">第 12 章 — 部署应用程序</span><span class="sxs-lookup"><span data-stu-id="32de1-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="32de1-533">若要部署你的应用程序：</span><span class="sxs-lookup"><span data-stu-id="32de1-533">To deploy your application:</span></span>

1.  <span data-ttu-id="32de1-534">导航到*应用程序*文件夹中创建[最后一章](#chapter-11---build-the-uwp-solution)。</span><span class="sxs-lookup"><span data-stu-id="32de1-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="32de1-535">您将查看你的应用名称，使用.sln 扩展，则您应该双击了文件，因此，若要中打开它*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="32de1-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="32de1-536">在中**解决方案平台**，选择**x86，本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="32de1-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="32de1-537">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="32de1-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="32de1-538">对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="32de1-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="32de1-539">不过，需要还执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="32de1-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="32de1-540">知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="32de1-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="32de1-541">请确保**开发人员模式**是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。</span><span class="sxs-lookup"><span data-stu-id="32de1-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![部署解决方案](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="32de1-543">转到**构建**菜单，并单击**部署解决方案**旁加载到计算机中，应用程序。</span><span class="sxs-lookup"><span data-stu-id="32de1-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="32de1-544">你的应用现在应已安装的应用，准备好进行启动和测试的列表中显示 ！</span><span class="sxs-lookup"><span data-stu-id="32de1-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="32de1-545">你已完成的 Azure 函数和存储应用程序</span><span class="sxs-lookup"><span data-stu-id="32de1-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="32de1-546">祝贺你，构建利用 Azure Functions 和 Azure 存储服务的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="32de1-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="32de1-547">您的应用程序将能够利用存储的数据，并提供一个操作基于该数据。</span><span class="sxs-lookup"><span data-stu-id="32de1-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![最终产品的最终](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="32de1-549">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="32de1-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="32de1-550">练习 1</span><span class="sxs-lookup"><span data-stu-id="32de1-550">Exercise 1</span></span>

<span data-ttu-id="32de1-551">创建第二个生成点和记录的生成的点从创建了一个对象。</span><span class="sxs-lookup"><span data-stu-id="32de1-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="32de1-552">当数据文件加载时，重播正在从最初创建它们的位置生成的形状。</span><span class="sxs-lookup"><span data-stu-id="32de1-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="32de1-553">练习 2</span><span class="sxs-lookup"><span data-stu-id="32de1-553">Exercise 2</span></span>

<span data-ttu-id="32de1-554">创建应用程序中，而不是无需重新打开它每次重新启动的方法。</span><span class="sxs-lookup"><span data-stu-id="32de1-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="32de1-555">**正在加载场景**是启动操作的好地方。</span><span class="sxs-lookup"><span data-stu-id="32de1-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="32de1-556">执行这些操作之后, 创建一种方法来清除中的存储的列表*Azure 存储*，以便它可以轻松地重置从您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="32de1-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
