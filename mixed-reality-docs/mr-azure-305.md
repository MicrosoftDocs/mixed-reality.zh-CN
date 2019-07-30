---
title: MR 和 Azure 305-功能和存储
description: 完成本课程以了解如何在混合现实应用程序中实现 Azure 存储和功能。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, 函数, 存储, hololens, 沉浸, vr
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694559"
---
>[!NOTE]
><span data-ttu-id="80405-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="80405-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="80405-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="80405-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="80405-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="80405-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="80405-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="80405-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="80405-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="80405-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="80405-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="80405-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="80405-110">MR 和 Azure 305:函数和存储</span><span class="sxs-lookup"><span data-stu-id="80405-110">MR and Azure 305: Functions and storage</span></span>

![最终产品-启动](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="80405-112">在本课程中, 你将了解如何在混合现实应用程序中创建和使用 Azure 存储资源 Azure Functions 和存储数据。</span><span class="sxs-lookup"><span data-stu-id="80405-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="80405-113">*Azure Functions*是一项 Microsoft 服务, 它允许开发人员在 Azure 中运行少量的代码 "函数"。</span><span class="sxs-lookup"><span data-stu-id="80405-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="80405-114">这提供了一种方法, 可将工作委托给云, 而不是本地应用程序, 这可能有很多好处。</span><span class="sxs-lookup"><span data-stu-id="80405-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="80405-115">*Azure Functions*支持多种开发语言, 包括 C\#、F\#、node.js、Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="80405-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="80405-116">有关详细信息, 请访问[Azure Functions 文章](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="80405-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="80405-117">*Azure 存储*是一种 Microsoft 云服务, 可让开发人员存储数据, 保证其高度可用、安全、持久、可缩放和冗余。</span><span class="sxs-lookup"><span data-stu-id="80405-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="80405-118">这意味着, Microsoft 将处理所有维护和关键问题。</span><span class="sxs-lookup"><span data-stu-id="80405-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="80405-119">有关详细信息, 请访问[Azure 存储一文](https://docs.microsoft.com/azure/storage/common/storage-introduction)。</span><span class="sxs-lookup"><span data-stu-id="80405-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="80405-120">完成本课程后, 你将拥有一个混合现实沉浸式耳机应用程序, 该应用程序将能够执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="80405-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="80405-121">允许用户浏览场景。</span><span class="sxs-lookup"><span data-stu-id="80405-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="80405-122">当用户 gazes 三维 "button" 时触发对象的生成。</span><span class="sxs-lookup"><span data-stu-id="80405-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="80405-123">生成的对象将由 Azure 函数选择。</span><span class="sxs-lookup"><span data-stu-id="80405-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="80405-124">生成每个对象时, 应用程序会将对象类型存储在 azure*存储*中的*azure 文件*中。</span><span class="sxs-lookup"><span data-stu-id="80405-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="80405-125">第二次加载时, 将检索*Azure 文件*数据, 并使用它来重播应用程序的上一个实例中的生成操作。</span><span class="sxs-lookup"><span data-stu-id="80405-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="80405-126">在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="80405-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="80405-127">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="80405-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="80405-128">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="80405-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="80405-129">设备支持</span><span class="sxs-lookup"><span data-stu-id="80405-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="80405-130">摘要</span><span class="sxs-lookup"><span data-stu-id="80405-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="80405-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="80405-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="80405-132"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="80405-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="80405-133">MR 和 Azure 305:函数和存储</span><span class="sxs-lookup"><span data-stu-id="80405-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="80405-134">✔️</span><span class="sxs-lookup"><span data-stu-id="80405-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="80405-135">✔️</span><span class="sxs-lookup"><span data-stu-id="80405-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="80405-136">尽管本课程主要侧重于 Windows Mixed Reality 沉浸 (VR) 耳机, 但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="80405-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="80405-137">在本课程中, 你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="80405-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80405-138">先决条件</span><span class="sxs-lookup"><span data-stu-id="80405-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="80405-139">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="80405-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="80405-140">另外请注意, 本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="80405-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="80405-141">您可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="80405-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="80405-142">本课程建议采用以下硬件和软件:</span><span class="sxs-lookup"><span data-stu-id="80405-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="80405-143">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC, 用于沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="80405-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="80405-144">Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="80405-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="80405-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="80405-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="80405-146">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="80405-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="80405-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="80405-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="80405-148">启用了开发人员模式的[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="80405-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="80405-149">Azure 帐户的订阅, 用于创建 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="80405-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="80405-150">Azure 安装和数据检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="80405-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="80405-151">开始之前</span><span class="sxs-lookup"><span data-stu-id="80405-151">Before you start</span></span>

<span data-ttu-id="80405-152">为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。</span><span class="sxs-lookup"><span data-stu-id="80405-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="80405-153">第1章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="80405-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="80405-154">若要使用**Azure 存储服务**, 你将需要在 Azure 门户中创建并配置一个**存储帐户**。</span><span class="sxs-lookup"><span data-stu-id="80405-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="80405-155">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="80405-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="80405-156">如果还没有 Azure 帐户, 则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="80405-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="80405-157">如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="80405-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="80405-158">登录后, 单击左上角的 "**新建**", 搜索 "*存储帐户*", 然后单击 "**输入**"。</span><span class="sxs-lookup"><span data-stu-id="80405-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure 存储搜索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="80405-160">在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="80405-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="80405-161">新页面将提供*Azure 存储帐户*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="80405-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="80405-162">在此提示符下, 选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="80405-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![创建服务](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="80405-164">单击 "**创建**" 后:</span><span class="sxs-lookup"><span data-stu-id="80405-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="80405-165">插入帐户的*名称*, 请注意, 此字段仅接受数字和小写字母。</span><span class="sxs-lookup"><span data-stu-id="80405-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="80405-166">对于*部署模型*, 选择 "**资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="80405-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="80405-167">对于 "*帐户类型*", 请选择 "**存储 (常规用途 v1)** "。</span><span class="sxs-lookup"><span data-stu-id="80405-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="80405-168">确定资源组的*位置*(如果要创建新的资源组)。</span><span class="sxs-lookup"><span data-stu-id="80405-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="80405-169">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="80405-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="80405-170">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="80405-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="80405-171">对于*复制*, 请选择 "**读取-访问-异地冗余存储 (GRS)** "。</span><span class="sxs-lookup"><span data-stu-id="80405-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="80405-172">对于 "*性能*", 请选择 "**标准**"。</span><span class="sxs-lookup"><span data-stu-id="80405-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="80405-173">使*安全传输*保持**禁用状态**。</span><span class="sxs-lookup"><span data-stu-id="80405-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="80405-174">选择*订阅*。</span><span class="sxs-lookup"><span data-stu-id="80405-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="80405-175">选择一个*资源组*, 或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="80405-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="80405-176">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="80405-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="80405-177">建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="80405-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="80405-178">若要了解有关 Azure 资源组的详细信息, 请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="80405-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="80405-179">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="80405-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="80405-180">选择“创建”  。</span><span class="sxs-lookup"><span data-stu-id="80405-180">Select **Create**.</span></span>

        ![输入服务信息](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="80405-182">单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="80405-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="80405-183">创建服务实例后, 门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="80405-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![azure 门户中的新通知](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="80405-185">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="80405-185">Click on the notifications to explore your new Service instance.</span></span>

    ![中转到资源](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="80405-187">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="80405-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="80405-188">你将转到新的*存储帐户*服务实例。</span><span class="sxs-lookup"><span data-stu-id="80405-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![访问密钥](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="80405-190">单击 "*访问密钥*", 以显示此云服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="80405-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="80405-191">使用*记事本*或类似的, 复制其中一个密钥供以后使用。</span><span class="sxs-lookup"><span data-stu-id="80405-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="80405-192">另外, 请记下*连接字符串*值, 因为它将用于稍后将创建的*azure 服务*类中。</span><span class="sxs-lookup"><span data-stu-id="80405-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![复制连接字符串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="80405-194">第2章-设置 Azure 函数</span><span class="sxs-lookup"><span data-stu-id="80405-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="80405-195">现在, 你将在 Azure 服务中编写**azure** **函数**。</span><span class="sxs-lookup"><span data-stu-id="80405-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="80405-196">你可以使用**Azure 函数**对你在代码中使用经典函数执行的任何操作, 区别在于, 具有访问 Azure 帐户的凭据的任何应用程序都可以访问此函数。</span><span class="sxs-lookup"><span data-stu-id="80405-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="80405-197">若要创建 Azure 函数:</span><span class="sxs-lookup"><span data-stu-id="80405-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="80405-198">在*Azure 门户*中, 单击左上角的 "**新建**", 搜索 " *Function App*", 然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="80405-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![创建函数应用](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="80405-200">在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="80405-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="80405-201">新页面将提供*Azure Function App*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="80405-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="80405-202">在此提示符下, 选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="80405-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![函数应用信息](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="80405-204">单击 "**创建**" 后:</span><span class="sxs-lookup"><span data-stu-id="80405-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="80405-205">提供*应用名称*。</span><span class="sxs-lookup"><span data-stu-id="80405-205">Provide an *App name*.</span></span> <span data-ttu-id="80405-206">此处只能使用字母和数字 (允许大写或小写)。</span><span class="sxs-lookup"><span data-stu-id="80405-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="80405-207">选择首选*订阅*。</span><span class="sxs-lookup"><span data-stu-id="80405-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="80405-208">选择一个*资源组*, 或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="80405-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="80405-209">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="80405-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="80405-210">建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="80405-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="80405-211">若要了解有关 Azure 资源组的详细信息, 请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="80405-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="80405-212">对于本练习, 请选择 " *Windows* " 作为所选**操作系统**。</span><span class="sxs-lookup"><span data-stu-id="80405-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="80405-213">为**托管计划**选择*消耗计划*。</span><span class="sxs-lookup"><span data-stu-id="80405-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="80405-214">确定资源组的*位置*(如果要创建新的资源组)。</span><span class="sxs-lookup"><span data-stu-id="80405-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="80405-215">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="80405-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="80405-216">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="80405-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="80405-217">为了获得最佳性能, 请选择与存储帐户相同的区域。</span><span class="sxs-lookup"><span data-stu-id="80405-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="80405-218">对于 "*存储*", 请选择 "**使用现有**", 然后使用下拉菜单查找先前创建的存储。</span><span class="sxs-lookup"><span data-stu-id="80405-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="80405-219">对于本练习, 请退出*Application Insights* 。</span><span class="sxs-lookup"><span data-stu-id="80405-219">Leave *Application Insights* off for this exercise.</span></span>

        ![输入函数应用详细信息](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="80405-221">单击“创建”  按钮。</span><span class="sxs-lookup"><span data-stu-id="80405-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="80405-222">单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="80405-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="80405-223">创建服务实例后, 门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="80405-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新的 azure 门户通知](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="80405-225">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="80405-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![中转到资源函数应用](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="80405-227">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="80405-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="80405-228">你将转到新的*Function App*服务实例。</span><span class="sxs-lookup"><span data-stu-id="80405-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="80405-229">在 " *Function App* " 仪表板上, 将鼠标悬停在左侧面板中的 "*函数*" 上方, 然后单击 " **+" (加号)** 符号。</span><span class="sxs-lookup"><span data-stu-id="80405-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![创建新函数](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="80405-231">在下一页上, 确保已选择 " **Webhook + API** ", 对于 *"选择语言",* 请选择 " **CSharp**", 因为这将是本教程中使用的语言。</span><span class="sxs-lookup"><span data-stu-id="80405-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="80405-232">最后, 单击 "**创建此函数**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="80405-232">Lastly, click the **Create this function** button.</span></span>

    ![选择 web 挂钩 csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="80405-234">您应该转到代码页 (run.csx), 如果不是, 请在左侧面板的 "函数" 列表中, 单击新创建的函数。</span><span class="sxs-lookup"><span data-stu-id="80405-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![打开新函数](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="80405-236">将以下代码复制到函数中。</span><span class="sxs-lookup"><span data-stu-id="80405-236">Copy the following code into your function.</span></span> <span data-ttu-id="80405-237">调用时, 此函数将只返回0到2之间的随机整数。</span><span class="sxs-lookup"><span data-stu-id="80405-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="80405-238">不要担心现有代码, 可以随意将其粘贴到其顶部。</span><span class="sxs-lookup"><span data-stu-id="80405-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="80405-239">选择“保存”。 </span><span class="sxs-lookup"><span data-stu-id="80405-239">Select **Save**.</span></span>

14. <span data-ttu-id="80405-240">结果应类似于下图。</span><span class="sxs-lookup"><span data-stu-id="80405-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="80405-241">单击 "**获取函数 URL** " 并记下显示的*终结点*。</span><span class="sxs-lookup"><span data-stu-id="80405-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="80405-242">你将需要将其插入到你稍后将在本课程中创建的*azure 服务*类中。</span><span class="sxs-lookup"><span data-stu-id="80405-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![获取函数终结点](images/AzureLabs-Lab5-16.png)

    ![获取函数终结点](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="80405-245">第3章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="80405-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="80405-246">下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="80405-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="80405-247">设置并测试混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="80405-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="80405-248">本课程**不**需要移动控制器。</span><span class="sxs-lookup"><span data-stu-id="80405-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="80405-249">如果需要支持设置沉浸式耳机, 请[访问混合现实设置一文](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="80405-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="80405-250">打开 Unity, 并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="80405-250">Open Unity and click **New**.</span></span>

    ![创建新的 unity 项目](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="80405-252">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="80405-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="80405-253">插入**MR_Azure_Functions**。</span><span class="sxs-lookup"><span data-stu-id="80405-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="80405-254">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="80405-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="80405-255">将位置设置为合适的*位置*(请记住, 更接近根目录更好)。</span><span class="sxs-lookup"><span data-stu-id="80405-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="80405-256">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="80405-256">Then, click **Create project**.</span></span>

    ![为新的 unity 项目命名](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="80405-258">当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="80405-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="80405-259">转到 "**编辑** > **首选项**", 然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="80405-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="80405-260">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="80405-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="80405-261">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="80405-261">Close the **Preferences** window.</span></span>

    ![将 visual studio 设置为脚本编辑器](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="80405-263">接下来, 转到 "**文件** > **生成设置**", 并通过单击 "**切换平台**" 按钮将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="80405-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![将平台切换到 uwp](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="80405-265">中转到 "**文件** > " "**生成设置**", 并确保:</span><span class="sxs-lookup"><span data-stu-id="80405-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="80405-266">"**目标设备**" 设置为 "**任何设备**"。</span><span class="sxs-lookup"><span data-stu-id="80405-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="80405-267">对于 Microsoft HoloLens, 将 "**目标设备**" 设置为 " *hololens*"。</span><span class="sxs-lookup"><span data-stu-id="80405-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="80405-268">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="80405-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="80405-269">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="80405-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="80405-270">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="80405-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="80405-271">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="80405-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="80405-272">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="80405-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="80405-273">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="80405-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="80405-274">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="80405-274">A save window will appear.</span></span>

            ![添加打开的场景](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="80405-276">为此创建新文件夹, 并为将来的任何场景创建一个新文件夹, 然后选择 "**新建文件夹**" 按钮以创建新文件夹, 将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="80405-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![创建场景文件夹](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="80405-278">打开新创建的**场景**文件夹, 然后在 "文件名 **:** 文本" 字段中, 键入**FunctionsScene**, 然后按 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="80405-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![保存函数场景](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="80405-280">现在, "**生成设置**" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="80405-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![保存函数场景](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="80405-282">在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="80405-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![检查器中的播放机设置](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="80405-284">在此面板中, 需要验证几项设置:</span><span class="sxs-lookup"><span data-stu-id="80405-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="80405-285">在 "**其他设置**" 选项卡中:</span><span class="sxs-lookup"><span data-stu-id="80405-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="80405-286">**脚本运行时版本**应为**试验**性的 (.net 4.6 等效项), 这会触发重新启动编辑器的需要。</span><span class="sxs-lookup"><span data-stu-id="80405-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="80405-287">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="80405-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="80405-288">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="80405-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="80405-289">在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:</span><span class="sxs-lookup"><span data-stu-id="80405-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="80405-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="80405-290">**InternetClient**</span></span>

            ![设置功能](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="80405-292">在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="80405-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 XR 设置](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="80405-294">"返回*生成设置* *" C# Unity 项目*不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="80405-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![计时周期 c # 项目](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="80405-296">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="80405-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="80405-297">保存场景和项目 (**文件** > **保存场景/文件** > **保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="80405-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="80405-298">第4章-设置主摄像机</span><span class="sxs-lookup"><span data-stu-id="80405-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80405-299">如果要跳过*Unity 设置*本课程的组件, 并继续直接进入代码, 可以[下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), 并将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入到项目中。</span><span class="sxs-lookup"><span data-stu-id="80405-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="80405-300">这还将包含下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="80405-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="80405-301">导入后, 从[第7章](#chapter-7---create-the-azureservices-class)继续。</span><span class="sxs-lookup"><span data-stu-id="80405-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="80405-302">在 "*层次结构" 面板*中, 你会看到一个名为 "**主相机**" 的对象, 此对象表示你在应用程序中 "内部" 后的 "头" 点。</span><span class="sxs-lookup"><span data-stu-id="80405-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="80405-303">在您前面的 Unity 仪表板中, 选择 " **GameObject" 主摄像机**。</span><span class="sxs-lookup"><span data-stu-id="80405-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="80405-304">你会注意到, "*检查器" 面板*(通常位于仪表板中) 将显示该*GameObject*的各种组件, 其中的 "*转换*" 位于顶部, 后面跟有*相机*和一些其他组件。</span><span class="sxs-lookup"><span data-stu-id="80405-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="80405-305">需要重置主摄像机的转换, 以便正确定位。</span><span class="sxs-lookup"><span data-stu-id="80405-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="80405-306">为此, 请选择相机*转换*组件旁边的**齿轮**图标, 然后选择 "**重置**"。</span><span class="sxs-lookup"><span data-stu-id="80405-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![重置转换](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="80405-308">然后, 将**转换**组件更新为如下所示:</span><span class="sxs-lookup"><span data-stu-id="80405-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="80405-309">转换位置</span><span class="sxs-lookup"><span data-stu-id="80405-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="80405-310">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-310">**X**</span></span>   | <span data-ttu-id="80405-311">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-311">**Y**</span></span>                     | <span data-ttu-id="80405-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-312">**Z**</span></span> |
    | <span data-ttu-id="80405-313">0</span><span class="sxs-lookup"><span data-stu-id="80405-313">0</span></span>       | <span data-ttu-id="80405-314">1</span><span class="sxs-lookup"><span data-stu-id="80405-314">1</span></span>                         | <span data-ttu-id="80405-315">0</span><span class="sxs-lookup"><span data-stu-id="80405-315">0</span></span>     |    

    |       | <span data-ttu-id="80405-316">转换-旋转</span><span class="sxs-lookup"><span data-stu-id="80405-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="80405-317">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-317">**X**</span></span> | <span data-ttu-id="80405-318">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-318">**Y**</span></span>                | <span data-ttu-id="80405-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-319">**Z**</span></span> |
    | <span data-ttu-id="80405-320">0</span><span class="sxs-lookup"><span data-stu-id="80405-320">0</span></span>     | <span data-ttu-id="80405-321">0</span><span class="sxs-lookup"><span data-stu-id="80405-321">0</span></span>                    | <span data-ttu-id="80405-322">0</span><span class="sxs-lookup"><span data-stu-id="80405-322">0</span></span>     |

    |       | <span data-ttu-id="80405-323">转换-缩放</span><span class="sxs-lookup"><span data-stu-id="80405-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="80405-324">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-324">**X**</span></span> | <span data-ttu-id="80405-325">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-325">**Y**</span></span>             | <span data-ttu-id="80405-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-326">**Z**</span></span> |
    | <span data-ttu-id="80405-327">1</span><span class="sxs-lookup"><span data-stu-id="80405-327">1</span></span>     | <span data-ttu-id="80405-328">1</span><span class="sxs-lookup"><span data-stu-id="80405-328">1</span></span>                 | <span data-ttu-id="80405-329">1</span><span class="sxs-lookup"><span data-stu-id="80405-329">1</span></span>     |

    ![设置相机转换](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="80405-331">第5章-设置 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="80405-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="80405-332">右键单击 "*层次结构" 面板*的空白区域中的 " **3d 对象**" 下的 "添加**平面**"。</span><span class="sxs-lookup"><span data-stu-id="80405-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![创建新平面](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="80405-334">选择 "**平面**" 对象后, 在 "*检查器" 面板*中更改以下参数:</span><span class="sxs-lookup"><span data-stu-id="80405-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="80405-335">转换位置</span><span class="sxs-lookup"><span data-stu-id="80405-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="80405-336">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-336">**X**</span></span> | <span data-ttu-id="80405-337">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-337">**Y**</span></span>                | <span data-ttu-id="80405-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-338">**Z**</span></span> |
    | <span data-ttu-id="80405-339">0</span><span class="sxs-lookup"><span data-stu-id="80405-339">0</span></span>     | <span data-ttu-id="80405-340">0</span><span class="sxs-lookup"><span data-stu-id="80405-340">0</span></span>                    | <span data-ttu-id="80405-341">4</span><span class="sxs-lookup"><span data-stu-id="80405-341">4</span></span>     |

    |       | <span data-ttu-id="80405-342">转换-缩放</span><span class="sxs-lookup"><span data-stu-id="80405-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="80405-343">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-343">**X**</span></span> | <span data-ttu-id="80405-344">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-344">**Y**</span></span>             | <span data-ttu-id="80405-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-345">**Z**</span></span> |
    | <span data-ttu-id="80405-346">10</span><span class="sxs-lookup"><span data-stu-id="80405-346">10</span></span>    | <span data-ttu-id="80405-347">1</span><span class="sxs-lookup"><span data-stu-id="80405-347">1</span></span>                 | <span data-ttu-id="80405-348">10</span><span class="sxs-lookup"><span data-stu-id="80405-348">10</span></span>    |

    ![设置平面位置和刻度](images/AzureLabs-Lab5-32.png)

    ![平面的场景视图](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="80405-351">右键单击 "*层次结构" 面板*的空白区域中的 "**三维对象**" 下的 "添加**多维数据集**"。</span><span class="sxs-lookup"><span data-stu-id="80405-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="80405-352">将多维数据集重命名为**GazeButton** (选择了多维数据集, 按 "F2")。</span><span class="sxs-lookup"><span data-stu-id="80405-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="80405-353">在 "*检查器" 面板*中更改以下参数:</span><span class="sxs-lookup"><span data-stu-id="80405-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="80405-354">转换位置</span><span class="sxs-lookup"><span data-stu-id="80405-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="80405-355">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-355">**X**</span></span> | <span data-ttu-id="80405-356">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-356">**Y**</span></span>                | <span data-ttu-id="80405-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-357">**Z**</span></span> |
        | <span data-ttu-id="80405-358">0</span><span class="sxs-lookup"><span data-stu-id="80405-358">0</span></span>     | <span data-ttu-id="80405-359">3</span><span class="sxs-lookup"><span data-stu-id="80405-359">3</span></span>                    | <span data-ttu-id="80405-360">5</span><span class="sxs-lookup"><span data-stu-id="80405-360">5</span></span>     |


        ![设置注视按钮转换](images/AzureLabs-Lab5-34.png)

        ![注视按钮场景视图](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="80405-363">单击 "**标记**" 下拉按钮, 然后单击 "**添加标记**" 以打开 "*标记 & 层" 窗格*。</span><span class="sxs-lookup"><span data-stu-id="80405-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![添加新标记](images/AzureLabs-Lab5-36.png)

        ![选择加号](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="80405-366">选择 " **+ (加)** " 按钮, 在 "*新标记名称*" 字段中, 输入**GazeButton**, 然后按 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="80405-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![命名新标记](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="80405-368">单击 "*层次结构" 面板*中的**GazeButton**对象, 然后在 "*检查器" 面板*中, 分配新创建的**GazeButton**标记。</span><span class="sxs-lookup"><span data-stu-id="80405-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![为新标记分配 "注视" 按钮](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="80405-370">右键单击 "*层次结构" 面板*中的**GazeButton**对象, 然后添加一个**空的 GameObject** (将作为*子*对象添加)。</span><span class="sxs-lookup"><span data-stu-id="80405-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="80405-371">选择新的对象, 并将其重命名为**ShapeSpawnPoint**。</span><span class="sxs-lookup"><span data-stu-id="80405-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="80405-372">在 "*检查器" 面板*中更改以下参数:</span><span class="sxs-lookup"><span data-stu-id="80405-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="80405-373">转换位置</span><span class="sxs-lookup"><span data-stu-id="80405-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="80405-374">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-374">**X**</span></span> |<span data-ttu-id="80405-375">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-375">**Y**</span></span>                 | <span data-ttu-id="80405-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-376">**Z**</span></span> |
        | <span data-ttu-id="80405-377">0</span><span class="sxs-lookup"><span data-stu-id="80405-377">0</span></span>     | <span data-ttu-id="80405-378">-1</span><span class="sxs-lookup"><span data-stu-id="80405-378">-1</span></span>                   | <span data-ttu-id="80405-379">0</span><span class="sxs-lookup"><span data-stu-id="80405-379">0</span></span>     |

        ![更新形状衍生点转换](images/AzureLabs-Lab5-40.png)

        ![形状生成点场景视图](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="80405-382">接下来, 你将创建一个**3D 文本**对象, 以提供有关 Azure 服务状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="80405-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="80405-383">再次右键单击 "层次结构" 面板中的**GazeButton** , 并添加一个**3d 对象** > **3d 文本**对象作为*子*对象。</span><span class="sxs-lookup"><span data-stu-id="80405-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![创建新的3D 文本对象](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="80405-385">将**3D 文本**对象重命名为**AzureStatusText**。</span><span class="sxs-lookup"><span data-stu-id="80405-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="80405-386">按如下所示更改**AzureStatusText**对象转换:</span><span class="sxs-lookup"><span data-stu-id="80405-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="80405-387">转换位置</span><span class="sxs-lookup"><span data-stu-id="80405-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="80405-388">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-388">**X**</span></span> | <span data-ttu-id="80405-389">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-389">**Y**</span></span>                | <span data-ttu-id="80405-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-390">**Z**</span></span> |
    | <span data-ttu-id="80405-391">0</span><span class="sxs-lookup"><span data-stu-id="80405-391">0</span></span>     | <span data-ttu-id="80405-392">0</span><span class="sxs-lookup"><span data-stu-id="80405-392">0</span></span>                    | <span data-ttu-id="80405-393">-0。6</span><span class="sxs-lookup"><span data-stu-id="80405-393">-0.6</span></span>  |

    |       | <span data-ttu-id="80405-394">转换-缩放</span><span class="sxs-lookup"><span data-stu-id="80405-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="80405-395">**X**</span><span class="sxs-lookup"><span data-stu-id="80405-395">**X**</span></span> | <span data-ttu-id="80405-396">**误差**</span><span class="sxs-lookup"><span data-stu-id="80405-396">**Y**</span></span>             | <span data-ttu-id="80405-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="80405-397">**Z**</span></span> |
    | <span data-ttu-id="80405-398">0.1</span><span class="sxs-lookup"><span data-stu-id="80405-398">0.1</span></span>   | <span data-ttu-id="80405-399">0.1</span><span class="sxs-lookup"><span data-stu-id="80405-399">0.1</span></span>               | <span data-ttu-id="80405-400">0.1</span><span class="sxs-lookup"><span data-stu-id="80405-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="80405-401">请不要担心它看起来是离线的, 因为在更新以下文本网格组件时, 将修复这种情况。</span><span class="sxs-lookup"><span data-stu-id="80405-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="80405-402">更改**文本网格**组件以匹配以下内容:</span><span class="sxs-lookup"><span data-stu-id="80405-402">Change the **Text Mesh** component to match the below:</span></span>

    ![设置文本网格组件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="80405-404">此处选择的颜色是十六进制颜色:尽管可以随意选择自己的**000000FF**, 只需确保它是可读的。</span><span class="sxs-lookup"><span data-stu-id="80405-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="80405-405">层次结构面板结构现在应如下所示:</span><span class="sxs-lookup"><span data-stu-id="80405-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![场景视图中的文本网格](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="80405-407">您的场景现在应如下所示:</span><span class="sxs-lookup"><span data-stu-id="80405-407">Your scene should now look like this:</span></span>

    ![场景视图中的文本网格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="80405-409">第6章-导入适用于 Unity 的 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="80405-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="80405-410">你将使用适用于 Unity 的 Azure 存储 (它本身利用 .Net SDK for Azure)。</span><span class="sxs-lookup"><span data-stu-id="80405-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="80405-411">有关详细信息, 请参阅适用于[Unity 的 Azure 存储一文](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="80405-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="80405-412">当前 Unity 中存在一个已知问题, 需要在导入后重新配置插件。</span><span class="sxs-lookup"><span data-stu-id="80405-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="80405-413">解决 bug 后, 将不再需要这些步骤 (本部分中的 4-7)。</span><span class="sxs-lookup"><span data-stu-id="80405-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="80405-414">若要将 SDK 导入到自己的项目中, 请确保已从 GitHub 下载最新的["unitypackage"](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="80405-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="80405-415">然后, 执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="80405-415">Then, do the following:</span></span>

1.  <span data-ttu-id="80405-416">使用 "**资产** > **导入包** > **自定义包**" 菜单选项将**unitypackage**文件添加到 Unity。</span><span class="sxs-lookup"><span data-stu-id="80405-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="80405-417">在弹出的 "**导入 Unity 包**" 框中, 可以选择 "**插件** > " "**存储**" 下的所有内容。</span><span class="sxs-lookup"><span data-stu-id="80405-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="80405-418">取消选中所有其他内容, 因为本课程不需要这样做。</span><span class="sxs-lookup"><span data-stu-id="80405-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![导入到包](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="80405-420">单击 "**导入**" 按钮, 将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="80405-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="80405-421">在 "项目" 视图中, 在 "*插件*" 下, 选择 "*存储*" 文件夹, 并*仅*选择以下插件:</span><span class="sxs-lookup"><span data-stu-id="80405-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="80405-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="80405-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="80405-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="80405-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="80405-424">Windowsazure.storage</span><span class="sxs-lookup"><span data-stu-id="80405-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="80405-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="80405-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="80405-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="80405-426">System.Spatial</span></span>

        ![取消选中任何平台](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="80405-428">选择*这些特定插件*后,**取消选中\*\**任何平台*并**取消选中**" *WSAPlayer* ", 然后单击 "**应用\*\*"。</span><span class="sxs-lookup"><span data-stu-id="80405-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![应用平台 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="80405-430">我们正在将这些特定插件标记为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="80405-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="80405-431">这是因为在从 Unity 导出项目后, 将使用 WSA 文件夹中的相同插件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="80405-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="80405-432">在*存储*插件文件夹中, 只选择:</span><span class="sxs-lookup"><span data-stu-id="80405-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="80405-433">Microsoft。</span><span class="sxs-lookup"><span data-stu-id="80405-433">Microsoft.Data.Services.Client</span></span>

        ![为 dll 设置不处理](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="80405-435">选中 "*平台设置*" 下的 "**不处理**" 框, 并单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="80405-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![不应用处理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="80405-437">我们正在将此插件标记为 "不处理", 因为 Unity 程序集 patcher 在处理此插件时遇到困难。</span><span class="sxs-lookup"><span data-stu-id="80405-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="80405-438">即使未处理插件, 该插件仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="80405-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="80405-439">第7章-创建 Azure 服务类</span><span class="sxs-lookup"><span data-stu-id="80405-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="80405-440">要创建的第一个类是*azure 服务*类。</span><span class="sxs-lookup"><span data-stu-id="80405-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="80405-441">*Azure 服务*类将负责:</span><span class="sxs-lookup"><span data-stu-id="80405-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="80405-442">存储 Azure 帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="80405-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="80405-443">调用 Azure 应用函数。</span><span class="sxs-lookup"><span data-stu-id="80405-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="80405-444">在 Azure 云存储中上传和下载数据文件。</span><span class="sxs-lookup"><span data-stu-id="80405-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="80405-445">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="80405-445">To create this Class:</span></span>

1.  <span data-ttu-id="80405-446">右键单击 "*资产*" 文件夹, 该文件夹位于 "项目" 面板中的 "**创建** > **文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="80405-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="80405-447">命名文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="80405-447">Name the folder **Scripts**.</span></span>

    ![创建新文件夹](images/AzureLabs-Lab5-50.png)

    ![调用文件夹-脚本](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="80405-450">双击刚创建的文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="80405-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="80405-451">右键单击文件夹内的 "**创建** >   **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="80405-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="80405-452">调用脚本*azure 服务*。</span><span class="sxs-lookup"><span data-stu-id="80405-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="80405-453">双击新的*azure 服务*类以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="80405-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="80405-454">将以下命名空间添加到*azure 服务*的顶部:</span><span class="sxs-lookup"><span data-stu-id="80405-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="80405-455">在*azure 服务*类中添加以下检查器字段:</span><span class="sxs-lookup"><span data-stu-id="80405-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="80405-456">然后在*azure 服务*类中添加以下成员变量:</span><span class="sxs-lookup"><span data-stu-id="80405-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="80405-457">请确保将*终结点*和*连接字符串*值替换为 Azure 门户中的 azure 存储值</span><span class="sxs-lookup"><span data-stu-id="80405-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="80405-458">现在需要添加*唤醒 ()* 和*Start ()* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="80405-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="80405-459">类初始化时, 将调用这些方法:</span><span class="sxs-lookup"><span data-stu-id="80405-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="80405-460">我们将在[以后的章节](#chapter-10---completing-the-azureservices-class)中填写*CallAzureFunctionForNextShape ()* 的代码。</span><span class="sxs-lookup"><span data-stu-id="80405-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="80405-461">删除*Update ()* 方法, 因为此类将不会使用它。</span><span class="sxs-lookup"><span data-stu-id="80405-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="80405-462">在 Visual Studio 中保存更改, 然后返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="80405-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="80405-463">单击 "脚本" 文件夹中的*azure 服务*类, 并将其拖到 "*层次结构" 面板*中的主相机对象。</span><span class="sxs-lookup"><span data-stu-id="80405-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="80405-464">选择主摄像机, 并从**GazeButton**对象下获取**AzureStatusText**子对象, 并将其放置在*检查器*的**AzureStatusText**引用目标字段中, 以提供对*Azure 服务*脚本。</span><span class="sxs-lookup"><span data-stu-id="80405-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![分配 azure 状态文本引用目标](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="80405-466">第8章-创建 ShapeFactory 类</span><span class="sxs-lookup"><span data-stu-id="80405-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="80405-467">要创建的下一个脚本是*ShapeFactory*类。</span><span class="sxs-lookup"><span data-stu-id="80405-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="80405-468">此类的作用是在请求时创建一个新的形状, 并保存在*形状历史记录列表*中创建的形状的历史记录。</span><span class="sxs-lookup"><span data-stu-id="80405-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="80405-469">每次创建形状时, 都将在*new-azureservice*类中更新*形状历史记录列表*, 然后将其存储在*Azure 存储*中。</span><span class="sxs-lookup"><span data-stu-id="80405-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="80405-470">当应用程序启动时, 如果在*Azure 存储*中找到存储的文件, 则将检索和重播*形状历史记录列表*, 其中包含的**3d 文本**对象用于提供生成的形状是来自存储还是新的。</span><span class="sxs-lookup"><span data-stu-id="80405-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="80405-471">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="80405-471">To create this class:</span></span>

1.  <span data-ttu-id="80405-472">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="80405-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="80405-473">右键单击文件夹内的 "**创建** >   **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="80405-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="80405-474">调用脚本*ShapeFactory*。</span><span class="sxs-lookup"><span data-stu-id="80405-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="80405-475">双击新的*ShapeFactory*脚本以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="80405-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="80405-476">确保*ShapeFactory*类包含以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="80405-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="80405-477">将下面显示的变量添加到*ShapeFactory*类, 并将*Start ()* 和*唤醒 ()* 函数替换为以下内容:</span><span class="sxs-lookup"><span data-stu-id="80405-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="80405-478">*CreateShape ()* 方法基于提供的*整数*参数生成基元形状。</span><span class="sxs-lookup"><span data-stu-id="80405-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="80405-479">布尔参数用于指定当前创建的形状是来自存储还是新的。</span><span class="sxs-lookup"><span data-stu-id="80405-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="80405-480">在*ShapeFactory*类中, 将以下代码放在前面的方法之前:</span><span class="sxs-lookup"><span data-stu-id="80405-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="80405-481">在返回到 Unity 之前, 请务必保存 Visual Studio 中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="80405-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="80405-482">返回 Unity 编辑器, 单击 "**脚本**" 文件夹中的*ShapeFactory*类并将其拖到 "*层次结构" 面板*中的**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="80405-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="80405-483">选择主相机后, 你会注意到*ShapeFactory*脚本组件缺少*生成点*引用。</span><span class="sxs-lookup"><span data-stu-id="80405-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="80405-484">若要修复此问题, 请将**ShapeSpawnPoint**对象从 "*层次结构" 面板*拖动到 "**生成点**引用目标"。</span><span class="sxs-lookup"><span data-stu-id="80405-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![设置形状工厂引用目标](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="80405-486">第9章-创建注视类</span><span class="sxs-lookup"><span data-stu-id="80405-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="80405-487">你需要创建的最后一个脚本是看不到*的类。*</span><span class="sxs-lookup"><span data-stu-id="80405-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="80405-488">此类负责创建将从主相机向前投影的**Raycast** , 以检测用户正在查看的对象。</span><span class="sxs-lookup"><span data-stu-id="80405-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="80405-489">在这种情况下, Raycast 需要确定用户是否正在查看场景中的**GazeButton**对象并触发行为。</span><span class="sxs-lookup"><span data-stu-id="80405-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="80405-490">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="80405-490">To create this Class:</span></span>

1.  <span data-ttu-id="80405-491">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="80405-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="80405-492">右键单击 "项目" 面板中的 "**创建** >   **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="80405-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="80405-493">调用脚本*注视*。</span><span class="sxs-lookup"><span data-stu-id="80405-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="80405-494">双击新的 "*注视*" 脚本以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="80405-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="80405-495">确保脚本顶部包含以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="80405-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="80405-496">然后在*注视*类中添加以下变量:</span><span class="sxs-lookup"><span data-stu-id="80405-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="80405-497">其中一些变量将能够在*编辑器*中进行编辑。</span><span class="sxs-lookup"><span data-stu-id="80405-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="80405-498">现在需要添加*唤醒 ()* 和*Start ()* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="80405-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="80405-499">添加下面的代码, 它将在开始时创建一个 cursor 对象, 以及*Update ()* 方法, 该方法将运行 Raycast 方法, 并在 GazeEnabled 布尔值的切换位置:</span><span class="sxs-lookup"><span data-stu-id="80405-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="80405-500">接下来, 添加*UpdateRaycast ()* 方法, 该方法将投影 Raycast 并检测命中目标。</span><span class="sxs-lookup"><span data-stu-id="80405-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="80405-501">最后, 添加*ResetFocusedObject ()* 方法, 该方法会将 GazeButton 对象的当前颜色切换为当前颜色, 指示是否正在创建新的形状。</span><span class="sxs-lookup"><span data-stu-id="80405-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="80405-502">在返回到 Unity 之前, 在 Visual Studio 中保存更改。</span><span class="sxs-lookup"><span data-stu-id="80405-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="80405-503">单击 "脚本" 文件夹中的 "*注视*" 类并将其拖到 "*层次结构" 面板*中的**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="80405-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="80405-504">第10章-完成 Azure 服务类</span><span class="sxs-lookup"><span data-stu-id="80405-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="80405-505">当其他脚本准备就绪后, 现在可以*完成* *azure 服务*类。</span><span class="sxs-lookup"><span data-stu-id="80405-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="80405-506">这将通过以下步骤实现:</span><span class="sxs-lookup"><span data-stu-id="80405-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="80405-507">添加一个名为*CreateCloudIdentityAsync ()* 的新方法来设置与 Azure 进行通信所需的身份验证变量。</span><span class="sxs-lookup"><span data-stu-id="80405-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="80405-508">此方法还会检查是否存在包含形状列表的以前存储的文件。</span><span class="sxs-lookup"><span data-stu-id="80405-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="80405-509">**如果找到该文件**, 它将禁用用户*注视*, 并根据形状模式 (存储在**Azure 存储文件**中) 触发形状创建。</span><span class="sxs-lookup"><span data-stu-id="80405-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="80405-510">用户可以查看此内容, 因为**文本网格**会根据形状原点提供显示 "存储" 或 "新建"。</span><span class="sxs-lookup"><span data-stu-id="80405-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="80405-511">**如果找不到文件**, 它将启用*注视*, 使用户能够在查看场景中的**GazeButton**对象时创建形状。</span><span class="sxs-lookup"><span data-stu-id="80405-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="80405-512">下一个代码段来自*Start ()* 方法,调用*CreateCloudIdentityAsync ()* 方法的情况。</span><span class="sxs-lookup"><span data-stu-id="80405-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="80405-513">可随意复制当前的*Start ()* 方法, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="80405-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="80405-514">填写方法*CallAzureFunctionForNextShape ()* 的代码。</span><span class="sxs-lookup"><span data-stu-id="80405-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="80405-515">你将使用之前创建的*Azure Function App*来请求形状索引。</span><span class="sxs-lookup"><span data-stu-id="80405-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="80405-516">接收到新形状后, 此方法会将形状发送到*ShapeFactory*类, 以在场景中创建新的形状。</span><span class="sxs-lookup"><span data-stu-id="80405-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="80405-517">使用下面的代码完成*CallAzureFunctionForNextShape ()* 的正文。</span><span class="sxs-lookup"><span data-stu-id="80405-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="80405-518">添加一个方法来创建字符串, 方法是连接形状历史记录列表中存储的整数, 并将其保存在*Azure 存储文件*中。</span><span class="sxs-lookup"><span data-stu-id="80405-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="80405-519">添加一个方法, 用于检索存储在位于*Azure 存储文件文件*中的文件中的文本, 并将其*反序列化为*列表。</span><span class="sxs-lookup"><span data-stu-id="80405-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="80405-520">完成此过程后, 该方法将重新启用注视, 使用户可以将更多形状添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="80405-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="80405-521">在返回到 Unity 之前, 在 Visual Studio 中保存更改。</span><span class="sxs-lookup"><span data-stu-id="80405-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="80405-522">第11章-构建 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="80405-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="80405-523">开始生成过程:</span><span class="sxs-lookup"><span data-stu-id="80405-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="80405-524">中转到 "**文件** > **生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="80405-524">Go to **File** > **Build Settings**.</span></span>

    ![构建应用程序](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="80405-526">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="80405-526">Click **Build**.</span></span> <span data-ttu-id="80405-527">Unity 将启动*文件资源管理器*窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="80405-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="80405-528">立即创建该文件夹并将其命名为*应用*。</span><span class="sxs-lookup"><span data-stu-id="80405-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="80405-529">选择*应用*文件夹后, 按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="80405-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="80405-530">Unity 将开始向*应用*文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="80405-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="80405-531">Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "*文件资源管理器*" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。</span><span class="sxs-lookup"><span data-stu-id="80405-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="80405-532">第12章-部署应用程序</span><span class="sxs-lookup"><span data-stu-id="80405-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="80405-533">若要部署应用程序:</span><span class="sxs-lookup"><span data-stu-id="80405-533">To deploy your application:</span></span>

1.  <span data-ttu-id="80405-534">导航到在[上一章](#chapter-11---build-the-uwp-solution)中创建的*应用*文件夹。</span><span class="sxs-lookup"><span data-stu-id="80405-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="80405-535">你将看到一个文件, 其中包含你的应用程序名称, 其中包含 ".sln" 扩展名, 你应该双击该文件, 以便在*Visual Studio*中将其打开。</span><span class="sxs-lookup"><span data-stu-id="80405-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="80405-536">在**解决方案平台**中, 选择 " **X86, 本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="80405-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="80405-537">在**解决方案配置**中, 选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="80405-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="80405-538">对于 Microsoft HoloLens, 你可能会发现将其设置为*远程计算机*会更容易, 因此你不会受限到计算机上。</span><span class="sxs-lookup"><span data-stu-id="80405-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="80405-539">不过, 还需要执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="80405-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="80405-540">了解你的 HoloLens 的**IP 地址**, 该地址可在 "**设置** > "**网络 & Internet** > **wi-fi** > **高级选项**"中找到; IPv4 是你应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="80405-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="80405-541">确保**开发人员模式**已**打开**;在 "**设置** > 更新" 中找到**开发人员** **& 安全性** > 。</span><span class="sxs-lookup"><span data-stu-id="80405-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![部署解决方案](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="80405-543">请在 "**生成**" 菜单中, 单击 "**部署解决方案**", 将应用程序旁加载到计算机上。</span><span class="sxs-lookup"><span data-stu-id="80405-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="80405-544">应用现在应显示在已安装的应用列表中, 可以启动和测试!</span><span class="sxs-lookup"><span data-stu-id="80405-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="80405-545">已完成的 Azure Functions 和存储应用程序</span><span class="sxs-lookup"><span data-stu-id="80405-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="80405-546">恭喜, 你构建了一个同时利用 Azure Functions 和 Azure 存储服务的混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="80405-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="80405-547">你的应用程序将能够在存储的数据上进行绘制, 并提供基于该数据的操作。</span><span class="sxs-lookup"><span data-stu-id="80405-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![最终产品-结束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="80405-549">额外练习</span><span class="sxs-lookup"><span data-stu-id="80405-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="80405-550">练习1</span><span class="sxs-lookup"><span data-stu-id="80405-550">Exercise 1</span></span>

<span data-ttu-id="80405-551">创建第二个生成点, 并记录创建对象的生成点。</span><span class="sxs-lookup"><span data-stu-id="80405-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="80405-552">加载数据文件时, 请重播从其最初创建的位置生成的形状。</span><span class="sxs-lookup"><span data-stu-id="80405-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="80405-553">练习2</span><span class="sxs-lookup"><span data-stu-id="80405-553">Exercise 2</span></span>

<span data-ttu-id="80405-554">创建一种方法来重新启动应用程序, 而不必每次都重新打开它。</span><span class="sxs-lookup"><span data-stu-id="80405-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="80405-555">**加载场景**是一种很好的起点。</span><span class="sxs-lookup"><span data-stu-id="80405-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="80405-556">完成此操作后, 创建一种方法来清除*Azure 存储*中存储的列表, 以便可以轻松地从应用重置。</span><span class="sxs-lookup"><span data-stu-id="80405-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
