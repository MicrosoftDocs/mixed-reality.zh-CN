---
title: MR 和 Azure 303 的自然语言理解 (LUIS)
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 语言理解智能服务 (LUIS)。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 语言理解智能服务，luis，沉浸式、 hololens、 vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592605"
---
>[!NOTE]
><span data-ttu-id="653a4-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="653a4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="653a4-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="653a4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="653a4-106">这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="653a4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="653a4-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="653a4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="653a4-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="653a4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="653a4-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="653a4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="653a4-110">MR 和 Azure 303:自然语言理解 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="653a4-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="653a4-111">在本课程中，您将学习如何将语言理解集成到 Azure 认知服务，与语言理解 API 结合使用的混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="653a4-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![实验结果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="653a4-113">*语言理解 (LUIS)* 是应用程序提供的功能以便利用用户输入，如通过提取一个人可能想什么，用他们自己的话说是 Microsoft Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="653a4-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="653a4-114">这被通过机器学习，它能够理解和学习的输入的信息，并将其可以反馈详细的相关信息。</span><span class="sxs-lookup"><span data-stu-id="653a4-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="653a4-115">有关详细信息，请访问[Azure 语言理解 (LUIS) 页](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。</span><span class="sxs-lookup"><span data-stu-id="653a4-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="653a4-116">已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="653a4-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="653a4-117">捕获用户输入的语音，使用附加到沉浸式耳机式麦克风。</span><span class="sxs-lookup"><span data-stu-id="653a4-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="653a4-118">发送捕获的听写*Azure 语言理解智能服务*(*LUIS*)。</span><span class="sxs-lookup"><span data-stu-id="653a4-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="653a4-119">具有 LUIS 提取这意味着从发送信息，它将进行分析，并尝试确定将所做的用户的请求。</span><span class="sxs-lookup"><span data-stu-id="653a4-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="653a4-120">开发将包括用户将能够使用语音和/或注视若要更改的大小和场景中对象的颜色的应用的创建。</span><span class="sxs-lookup"><span data-stu-id="653a4-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="653a4-121">将不再重复介绍 motion 控制器使用。</span><span class="sxs-lookup"><span data-stu-id="653a4-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="653a4-122">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="653a4-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="653a4-123">本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="653a4-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="653a4-124">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="653a4-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="653a4-125">请做好准备定型 LUIS 到几次，此内容中进行介绍[第 12 章](#chapter-12--improving-your-luis-service)。</span><span class="sxs-lookup"><span data-stu-id="653a4-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="653a4-126">你将获得更佳结果定型 LUIS 的更多时间。</span><span class="sxs-lookup"><span data-stu-id="653a4-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="653a4-127">设备支持</span><span class="sxs-lookup"><span data-stu-id="653a4-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="653a4-128">课程</span><span class="sxs-lookup"><span data-stu-id="653a4-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="653a4-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="653a4-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="653a4-130"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="653a4-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="653a4-131">MR 和 Azure 303:自然语言理解 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="653a4-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="653a4-132">✔️</span><span class="sxs-lookup"><span data-stu-id="653a4-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="653a4-133">✔️</span><span class="sxs-lookup"><span data-stu-id="653a4-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="653a4-134">尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="653a4-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="653a4-135">按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。</span><span class="sxs-lookup"><span data-stu-id="653a4-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="653a4-136">使用 HoloLens，您可能注意到某些 echo 语音捕获过程。</span><span class="sxs-lookup"><span data-stu-id="653a4-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="653a4-137">先决条件</span><span class="sxs-lookup"><span data-stu-id="653a4-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="653a4-138">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="653a4-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="653a4-139">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="653a4-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="653a4-140">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="653a4-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="653a4-141">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="653a4-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="653a4-142">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="653a4-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="653a4-143">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="653a4-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="653a4-144">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="653a4-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="653a4-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="653a4-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="653a4-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="653a4-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="653a4-147">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="653a4-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="653a4-148">一组的耳机使用内置的麦克风 （如果耳机没有内置的麦克风和扬声器）</span><span class="sxs-lookup"><span data-stu-id="653a4-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="653a4-149">Internet 访问的 Azure 设置和 LUIS 检索</span><span class="sxs-lookup"><span data-stu-id="653a4-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="653a4-150">开始之前</span><span class="sxs-lookup"><span data-stu-id="653a4-150">Before you start</span></span>

1.  <span data-ttu-id="653a4-151">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="653a4-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="653a4-152">若要允许您的计算机以启用听写，请转到**Windows 设置 > 隐私 > 语音，墨迹书写和键入**按按钮**启用语音服务和键入建议**。</span><span class="sxs-lookup"><span data-stu-id="653a4-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="653a4-153">在本教程中的代码将允许从录制**默认麦克风设备**在计算机上设置。</span><span class="sxs-lookup"><span data-stu-id="653a4-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="653a4-154">请确保默认麦克风设备设置为想要用于捕获您的声音。</span><span class="sxs-lookup"><span data-stu-id="653a4-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="653a4-155">如果您的头戴式有内置麦克风，确保将选项 *"当我 wear 我耳机时，切换到耳机式麦克风"* 中开启*混合现实门户*设置。</span><span class="sxs-lookup"><span data-stu-id="653a4-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![设置沉浸式头戴式](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="653a4-157">第 1 章 – 设置 Azure 门户</span><span class="sxs-lookup"><span data-stu-id="653a4-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="653a4-158">若要使用*语言理解*服务在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="653a4-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="653a4-159">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="653a4-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="653a4-160">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="653a4-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="653a4-161">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="653a4-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="653a4-162">你登录后，单击**新建**在左上角，并搜索*语言理解*，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="653a4-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![创建 LUIS 资源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="653a4-164">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="653a4-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="653a4-165">右侧的新页将提供语言理解服务的说明。</span><span class="sxs-lookup"><span data-stu-id="653a4-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="653a4-166">在左下角此页上，选择**创建**按钮，创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="653a4-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS 服务创建-法律声明](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="653a4-168">一次单击在创建：</span><span class="sxs-lookup"><span data-stu-id="653a4-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="653a4-169">插入所需**名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="653a4-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="653a4-170">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="653a4-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="653a4-171">选择**定价层**适合您，如果这是第一个时间来创建*LUIS 服务*，应可供你免费层 （名为 F0）。</span><span class="sxs-lookup"><span data-stu-id="653a4-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="653a4-172">免费分配应足以应付此课程。</span><span class="sxs-lookup"><span data-stu-id="653a4-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="653a4-173">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="653a4-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="653a4-174">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="653a4-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="653a4-175">建议尽量与常见的资源组下的单个项目 （例如如这些课程） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="653a4-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="653a4-176">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="653a4-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="653a4-177">确定**位置**为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="653a4-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="653a4-178">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="653a4-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="653a4-179">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="653a4-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="653a4-180">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="653a4-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="653a4-181">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="653a4-181">Select **Create**.</span></span>

        ![创建 LUIS 服务-用户输入](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="653a4-183">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="653a4-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="653a4-184">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="653a4-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新的 Azure 通知图像](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="653a4-186">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="653a4-186">Click on the notification to explore your new Service instance.</span></span>

    ![成功的资源创建通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="653a4-188">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="653a4-189">你将转到新的 LUIS 服务实例。</span><span class="sxs-lookup"><span data-stu-id="653a4-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![访问 LUIS 密钥](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="653a4-191">在本教程中，你的应用程序将需要对你的服务，通过使用服务的订阅密钥来完成进行调用。</span><span class="sxs-lookup"><span data-stu-id="653a4-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="653a4-192">从*快速入门*页上的你*LUIS API*服务，，请导航到的第一步*捕捉密钥*，然后单击**密钥**（也可以实现此目的通过单击蓝色超链接密钥，位于服务导航菜单中，由密钥图标表示）。</span><span class="sxs-lookup"><span data-stu-id="653a4-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="653a4-193">此时会显示你的服务*密钥*。</span><span class="sxs-lookup"><span data-stu-id="653a4-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="653a4-194">需要一份某个显示的密钥，因为你将需要此更高版本中您的项目。</span><span class="sxs-lookup"><span data-stu-id="653a4-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="653a4-195">在中*服务*页上，单击*语言理解门户*重定向到的网页将用来创建新服务，LUIS 应用程序中的。</span><span class="sxs-lookup"><span data-stu-id="653a4-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="653a4-196">第 2 章-语言理解门户</span><span class="sxs-lookup"><span data-stu-id="653a4-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="653a4-197">在本部分中将了解如何在 LUIS 门户上进行 LUIS 应用。</span><span class="sxs-lookup"><span data-stu-id="653a4-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="653a4-198">请特别注意，该设置*实体*，*意向*，并*语音样本*这一章中只是第一步构建 LUIS 服务： 你还将需要重新训练服务，几次，因此若要使其更准确。</span><span class="sxs-lookup"><span data-stu-id="653a4-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="653a4-199">中介绍了你的服务重新训练[最后一章](#chapter-12--improving-your-luis-service)的本课程中，因此请确保完成它。</span><span class="sxs-lookup"><span data-stu-id="653a4-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="653a4-200">一旦达到*语言理解门户*，您可能需要登录，如果您尚不，使用 Azure 门户相同的凭据。</span><span class="sxs-lookup"><span data-stu-id="653a4-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 登录页](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="653a4-202">如果这是你首次使用 LUIS，您将需要向下滚动到要查找，然后单击欢迎页的底部**创建 LUIS 应用**按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![创建 LUIS 应用程序页](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="653a4-204">登录后，单击**我的应用**（如果您当前不是那一节中）。</span><span class="sxs-lookup"><span data-stu-id="653a4-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="653a4-205">您可以单击**创建新应用**。</span><span class="sxs-lookup"><span data-stu-id="653a4-205">You can then click on **Create new app**.</span></span>

    ![LUIS-我的应用的映像](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="653a4-207">为提供您的应用程序*名称*。</span><span class="sxs-lookup"><span data-stu-id="653a4-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="653a4-208">如果您的应用程序应以了解不同于英语语言，应更改*区域性*为合适的语言。</span><span class="sxs-lookup"><span data-stu-id="653a4-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="653a4-209">此处您还可以添加*说明*新 LUIS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="653a4-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-创建新的应用](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="653a4-211">按下后**完成**，将进入*构建*将新的页*LUIS*应用程序。</span><span class="sxs-lookup"><span data-stu-id="653a4-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="653a4-212">有几个需要了解此处的重要概念：</span><span class="sxs-lookup"><span data-stu-id="653a4-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="653a4-213">*意向*，表示将从用户以下查询调用的方法。</span><span class="sxs-lookup"><span data-stu-id="653a4-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="653a4-214">*意向*可能具有一个或多个*实体*。</span><span class="sxs-lookup"><span data-stu-id="653a4-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="653a4-215">*实体*，是说明与相关的信息的查询的组件*意向*。</span><span class="sxs-lookup"><span data-stu-id="653a4-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="653a4-216">*语音样本*，提供由开发人员，该 LUIS 将用于定型本身是查询的示例。</span><span class="sxs-lookup"><span data-stu-id="653a4-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="653a4-217">如果这些概念并不完全清除，请不要担心，因为此课程将进行它们做进一步说明这一章中。</span><span class="sxs-lookup"><span data-stu-id="653a4-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="653a4-218">将首先创建*实体*需生成此课程。</span><span class="sxs-lookup"><span data-stu-id="653a4-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="653a4-219">在左侧和右侧的页上，单击*实体*，然后单击**创建新实体**。</span><span class="sxs-lookup"><span data-stu-id="653a4-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![创建新实体](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="653a4-221">调用新的实体*颜色*，将其类型设置为*简单*，然后按**完成**。</span><span class="sxs-lookup"><span data-stu-id="653a4-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![创建简单的实体的颜色](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="653a4-223">重复此过程以创建三 （3） 更多简单实体名为：</span><span class="sxs-lookup"><span data-stu-id="653a4-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="653a4-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="653a4-224">*upsize*</span></span>
    -   <span data-ttu-id="653a4-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="653a4-225">*downsize*</span></span>
    -   <span data-ttu-id="653a4-226">*target*</span><span class="sxs-lookup"><span data-stu-id="653a4-226">*target*</span></span>

<span data-ttu-id="653a4-227">结果应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-227">The result should look like the image below:</span></span>

![创建实体时的结果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="653a4-229">现在可以开始创建*意向*。</span><span class="sxs-lookup"><span data-stu-id="653a4-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="653a4-230">不要删除**None**意向。</span><span class="sxs-lookup"><span data-stu-id="653a4-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="653a4-231">在左侧和右侧的页上，单击**意向**，然后单击**创建新的意向**。</span><span class="sxs-lookup"><span data-stu-id="653a4-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![创建新的 intents](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="653a4-233">调用新*意向* **ChangeObjectColor**。</span><span class="sxs-lookup"><span data-stu-id="653a4-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="653a4-234">这*意向*使用名称中的代码更高版本中此课程，因此对于获得最佳结果，使用此名称完全按原样。</span><span class="sxs-lookup"><span data-stu-id="653a4-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="653a4-235">一旦确认系统会定向到意向页的名称。</span><span class="sxs-lookup"><span data-stu-id="653a4-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS 的意向页](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="653a4-237">您会注意到没有要求你为 5 或更多个不同类型的 textbox*语音样本*。</span><span class="sxs-lookup"><span data-stu-id="653a4-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="653a4-238">LUIS 将所有查询文本转换为小写。</span><span class="sxs-lookup"><span data-stu-id="653a4-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="653a4-239">插入以下*语音样本*顶部的文本框中 (当前具有文本*键入大约 5 示例...*</span><span class="sxs-lookup"><span data-stu-id="653a4-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="653a4-240">)，然后按**Enter**:</span><span class="sxs-lookup"><span data-stu-id="653a4-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="653a4-241">您将注意到，新*语音样本*会在下方列表中。</span><span class="sxs-lookup"><span data-stu-id="653a4-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="653a4-242">按照相同的过程中，插入以下六 （6） 言辞：</span><span class="sxs-lookup"><span data-stu-id="653a4-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="653a4-243">对于已创建的每个查询文本，必须标识哪些字词应用作 luis 实体。</span><span class="sxs-lookup"><span data-stu-id="653a4-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="653a4-244">在此示例中您需要为所有颜色*颜色*实体，并且对作为目标的所有可能引用*目标*实体。</span><span class="sxs-lookup"><span data-stu-id="653a4-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="653a4-245">若要执行此操作，请尝试单击的词*柱状体*第一个查询文本，然后选择*目标*。</span><span class="sxs-lookup"><span data-stu-id="653a4-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![识别语音样本目标](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="653a4-247">现在，单击单词*红色*第一个查询文本，然后选择*颜色*。</span><span class="sxs-lookup"><span data-stu-id="653a4-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![确定查询文本实体](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="653a4-249">此外，标记的下一行其中*多维数据集*应*目标*，并*黑色*应为*颜色*。</span><span class="sxs-lookup"><span data-stu-id="653a4-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="653a4-250">另请注意使用的某些词 *'this'*， *it*，并 *'此对象*，我们提供，因此还具有可用的非特定于目标类型。</span><span class="sxs-lookup"><span data-stu-id="653a4-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="653a4-251">重复上述过程，直到所有语音样本已标记为的实体。</span><span class="sxs-lookup"><span data-stu-id="653a4-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="653a4-252">请参阅下图，如果需要帮助。</span><span class="sxs-lookup"><span data-stu-id="653a4-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="653a4-253">当选择单词以作为实体标记它们：</span><span class="sxs-lookup"><span data-stu-id="653a4-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="653a4-254">为单个词只需单击它们。</span><span class="sxs-lookup"><span data-stu-id="653a4-254">For single words just click them.</span></span>
    > - <span data-ttu-id="653a4-255">两个或多个单词的一组，请单击开头和，然后在集的末尾。</span><span class="sxs-lookup"><span data-stu-id="653a4-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="653a4-256">可以使用*令牌视图*切换按钮来切换**实体 / 令牌视图**！</span><span class="sxs-lookup"><span data-stu-id="653a4-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="653a4-257">结果应如中所示下, 图中显示**实体 / 令牌视图**:</span><span class="sxs-lookup"><span data-stu-id="653a4-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![令牌和实体视图](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="653a4-259">此时按**训练**页面的右上按钮并等待的小型倒圆角的指示符，它才会变为绿色。</span><span class="sxs-lookup"><span data-stu-id="653a4-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="653a4-260">这表示，LUIS 成功定型识别此意向。</span><span class="sxs-lookup"><span data-stu-id="653a4-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![定型 LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="653a4-262">为你的练习，创建名为新意向**ChangeObjectSize**，使用实体*目标*，*升迁*，以及*缩小*。</span><span class="sxs-lookup"><span data-stu-id="653a4-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="653a4-263">遵循与前一意图，相同的进程插入以下 8 个语音样本添加有关*大小*更改：</span><span class="sxs-lookup"><span data-stu-id="653a4-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="653a4-264">结果应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-264">The result should be like the one in the image below:</span></span>

    ![设置 ChangeObjectSize 令牌 / 实体](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="653a4-266">一次这两种意图**ChangeObjectColor**并**ChangeObjectSize**，已创建并定型，单击**发布**页面顶部的按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![发布 LUIS 服务](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="653a4-268">上*发布*将完成并发布 LUIS 应用，以便其可以访问你的代码页。</span><span class="sxs-lookup"><span data-stu-id="653a4-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="653a4-269">向下设置下拉*发布到*作为**生产**。</span><span class="sxs-lookup"><span data-stu-id="653a4-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="653a4-270">设置*时区*到您所在的时区。</span><span class="sxs-lookup"><span data-stu-id="653a4-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="653a4-271">选中复选框**包括所有预测意向分数**。</span><span class="sxs-lookup"><span data-stu-id="653a4-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="653a4-272">单击**发布到生产槽**。</span><span class="sxs-lookup"><span data-stu-id="653a4-272">Click on **Publish to Production Slot**.</span></span>

        ![发布设置](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="653a4-274">在部分*资源和密钥*:</span><span class="sxs-lookup"><span data-stu-id="653a4-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="653a4-275">选择在 Azure 门户中的服务实例设置的区域。</span><span class="sxs-lookup"><span data-stu-id="653a4-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="653a4-276">你会注意到**Starter_Key**元素下面，将其忽略。</span><span class="sxs-lookup"><span data-stu-id="653a4-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="653a4-277">单击**添加密钥**，并插入*密钥*创建您的服务实例时获得在 Azure 门户中。</span><span class="sxs-lookup"><span data-stu-id="653a4-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="653a4-278">如果你的 Azure 和 LUIS 门户登录到同一用户中，将提供的下拉列表菜单*租户名称*，*订阅名称*，并*密钥*你想要使用 （将具有相同的名称，如前面在 Azure 门户中提供。</span><span class="sxs-lookup"><span data-stu-id="653a4-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="653a4-279">其下方*终结点*，复制的键对应的终结点已插入，很快将在代码中使用它。</span><span class="sxs-lookup"><span data-stu-id="653a4-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="653a4-280">第 3 章 – 设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="653a4-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="653a4-281">以下是一组典型使用混合现实中，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="653a4-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="653a4-282">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="653a4-282">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="653a4-284">现在将需要提供 Unity 项目的名称，插入**MR_LUIS**。</span><span class="sxs-lookup"><span data-stu-id="653a4-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="653a4-285">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="653a4-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="653a4-286">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="653a4-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="653a4-287">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="653a4-287">Then, click **Create project**.</span></span>

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="653a4-289">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="653a4-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="653a4-290">转到编辑 > 首选项，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="653a4-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="653a4-291">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="653a4-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="653a4-292">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="653a4-292">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="653a4-294">接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="653a4-296">转到**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="653a4-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="653a4-297">**设备为目标**设置为**任一设备**</span><span class="sxs-lookup"><span data-stu-id="653a4-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="653a4-298">对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="653a4-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="653a4-299">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="653a4-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="653a4-300">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="653a4-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="653a4-301">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="653a4-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="653a4-302">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="653a4-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="653a4-303">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="653a4-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="653a4-304">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="653a4-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="653a4-305">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="653a4-305">A save window will appear.</span></span>
        
            ![单击添加打开场景按钮](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="653a4-307">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="653a4-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="653a4-309">打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_LuisScene**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="653a4-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![为新的场景提供一个名称。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="653a4-311">中的剩余设置，*生成设置*，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="653a4-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="653a4-312">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="653a4-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放器设置。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="653a4-314">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="653a4-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="653a4-315">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="653a4-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="653a4-316">**脚本运行时版本**应**稳定**（.NET 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="653a4-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="653a4-317">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="653a4-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="653a4-318">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="653a4-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="653a4-320">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="653a4-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="653a4-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="653a4-321">**InternetClient**</span></span>
        2. <span data-ttu-id="653a4-322">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="653a4-322">**Microphone**</span></span>

            ![正在更新的发布设置。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="653a4-324">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="653a4-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新的 X R 设置。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="653a4-326">回到*生成设置* _Unity C#_ 项目不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="653a4-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="653a4-327">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="653a4-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="653a4-328">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="653a4-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="653a4-329">第 4 章-创建场景</span><span class="sxs-lookup"><span data-stu-id="653a4-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="653a4-330">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5--create-the-microphonemanager-class)。</span><span class="sxs-lookup"><span data-stu-id="653a4-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="653a4-331">在空白区域中单击右键*层次结构面板*下**三维对象**，将添加**平面**。</span><span class="sxs-lookup"><span data-stu-id="653a4-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![创建一个平面。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="653a4-333">请注意，当在中右键单击*层次结构*再次以创建更多的对象，如果您仍然可以选择的最后一个对象，所选的对象将新对象的父对象。</span><span class="sxs-lookup"><span data-stu-id="653a4-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="653a4-334">在层次结构中的空白空间中单击鼠标左键，然后右键单击可以避免此问题。</span><span class="sxs-lookup"><span data-stu-id="653a4-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="653a4-335">重复上述过程添加以下对象：</span><span class="sxs-lookup"><span data-stu-id="653a4-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="653a4-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="653a4-336">*Sphere*</span></span>
    2. <span data-ttu-id="653a4-337">*Cylinder*</span><span class="sxs-lookup"><span data-stu-id="653a4-337">*Cylinder*</span></span>
    3. <span data-ttu-id="653a4-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="653a4-338">*Cube*</span></span>
    4. <span data-ttu-id="653a4-339">*三维文字*</span><span class="sxs-lookup"><span data-stu-id="653a4-339">*3D Text*</span></span>

4.  <span data-ttu-id="653a4-340">生成场景*层次结构*应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![场景层次结构的设置。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="653a4-342">在单击鼠标左键**Main Camera**若要选择它，请查看*检查器面板*您将看到所有相机对象及其组件。</span><span class="sxs-lookup"><span data-stu-id="653a4-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="653a4-343">单击**添加组件**按钮位于最底部*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="653a4-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![添加音频源](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="653a4-345">搜索调用的组件*音频源*，如上所示。</span><span class="sxs-lookup"><span data-stu-id="653a4-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="653a4-346">此外，请确保*转换*Main Camera 组件设置为 (0,0,0)，这可以通过按**齿轮**照相机的旁边的图标*转换*组件并选择**重置**。</span><span class="sxs-lookup"><span data-stu-id="653a4-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="653a4-347">*转换*组件应如下所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="653a4-348">*位置*设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="653a4-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="653a4-349">*旋转*设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="653a4-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="653a4-350">对于 Microsoft HoloLens，您将需要还可以更改以下内容，属于**照相机**组件，它位于您**Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="653a4-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="653a4-351">**清除标志：** 纯色。</span><span class="sxs-lookup"><span data-stu-id="653a4-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="653a4-352">**背景**黑色、 Alpha 0 – 十六进制颜色: #00000000。</span><span class="sxs-lookup"><span data-stu-id="653a4-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="653a4-353">在单击鼠标左键**平面**以将其选中。</span><span class="sxs-lookup"><span data-stu-id="653a4-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="653a4-354">在中*检查器面板*设置*转换*组件使用以下值：</span><span class="sxs-lookup"><span data-stu-id="653a4-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="653a4-355">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="653a4-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="653a4-356">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-356">**X**</span></span> | <span data-ttu-id="653a4-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-357">**Y**</span></span>                  | <span data-ttu-id="653a4-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-358">**Z**</span></span> |
    | <span data-ttu-id="653a4-359">0</span><span class="sxs-lookup"><span data-stu-id="653a4-359">0</span></span>     | <span data-ttu-id="653a4-360">-1</span><span class="sxs-lookup"><span data-stu-id="653a4-360">-1</span></span>                     | <span data-ttu-id="653a4-361">0</span><span class="sxs-lookup"><span data-stu-id="653a4-361">0</span></span>     |


10. <span data-ttu-id="653a4-362">在单击鼠标左键**球体**以将其选中。</span><span class="sxs-lookup"><span data-stu-id="653a4-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="653a4-363">在中*检查器面板*设置*转换*组件使用以下值：</span><span class="sxs-lookup"><span data-stu-id="653a4-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="653a4-364">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="653a4-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="653a4-365">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-365">**X**</span></span> | <span data-ttu-id="653a4-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-366">**Y**</span></span>                  | <span data-ttu-id="653a4-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-367">**Z**</span></span> |
    | <span data-ttu-id="653a4-368">2</span><span class="sxs-lookup"><span data-stu-id="653a4-368">2</span></span>     | <span data-ttu-id="653a4-369">1</span><span class="sxs-lookup"><span data-stu-id="653a4-369">1</span></span>                      | <span data-ttu-id="653a4-370">2</span><span class="sxs-lookup"><span data-stu-id="653a4-370">2</span></span>     |

11. <span data-ttu-id="653a4-371">在单击鼠标左键**柱状体**以将其选中。</span><span class="sxs-lookup"><span data-stu-id="653a4-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="653a4-372">在中*检查器面板*设置*转换*组件使用以下值：</span><span class="sxs-lookup"><span data-stu-id="653a4-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="653a4-373">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="653a4-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="653a4-374">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-374">**X**</span></span> | <span data-ttu-id="653a4-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-375">**Y**</span></span>                  | <span data-ttu-id="653a4-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-376">**Z**</span></span> |
    | <span data-ttu-id="653a4-377">-2</span><span class="sxs-lookup"><span data-stu-id="653a4-377">-2</span></span>    | <span data-ttu-id="653a4-378">1</span><span class="sxs-lookup"><span data-stu-id="653a4-378">1</span></span>                      | <span data-ttu-id="653a4-379">2</span><span class="sxs-lookup"><span data-stu-id="653a4-379">2</span></span>     |

12. <span data-ttu-id="653a4-380">在单击鼠标左键**多维数据集**以将其选中。</span><span class="sxs-lookup"><span data-stu-id="653a4-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="653a4-381">在中*检查器面板*设置*转换*组件使用以下值：</span><span class="sxs-lookup"><span data-stu-id="653a4-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="653a4-382">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="653a4-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="653a4-383">转换的*旋转*</span><span class="sxs-lookup"><span data-stu-id="653a4-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="653a4-384">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-384">**X**</span></span> | <span data-ttu-id="653a4-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-385">**Y**</span></span>                   | <span data-ttu-id="653a4-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-386">**Z**</span></span> |  \| | <span data-ttu-id="653a4-387">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-387">**X**</span></span> | <span data-ttu-id="653a4-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-388">**Y**</span></span>                  | <span data-ttu-id="653a4-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-389">**Z**</span></span> |
    | <span data-ttu-id="653a4-390">0</span><span class="sxs-lookup"><span data-stu-id="653a4-390">0</span></span>     | <span data-ttu-id="653a4-391">1</span><span class="sxs-lookup"><span data-stu-id="653a4-391">1</span></span>                       | <span data-ttu-id="653a4-392">4</span><span class="sxs-lookup"><span data-stu-id="653a4-392">4</span></span>     |  \| | <span data-ttu-id="653a4-393">45</span><span class="sxs-lookup"><span data-stu-id="653a4-393">45</span></span>    | <span data-ttu-id="653a4-394">45</span><span class="sxs-lookup"><span data-stu-id="653a4-394">45</span></span>                     | <span data-ttu-id="653a4-395">0</span><span class="sxs-lookup"><span data-stu-id="653a4-395">0</span></span>     | 

13. <span data-ttu-id="653a4-396">在单击鼠标左键**新文本**对象以将其选中。</span><span class="sxs-lookup"><span data-stu-id="653a4-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="653a4-397">在中*检查器面板*设置*转换*组件使用以下值：</span><span class="sxs-lookup"><span data-stu-id="653a4-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="653a4-398">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="653a4-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="653a4-399">转换的*规模*</span><span class="sxs-lookup"><span data-stu-id="653a4-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="653a4-400">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-400">**X**</span></span> | <span data-ttu-id="653a4-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-401">**Y**</span></span>                  | <span data-ttu-id="653a4-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-402">**Z**</span></span> |  \| | <span data-ttu-id="653a4-403">**X**</span><span class="sxs-lookup"><span data-stu-id="653a4-403">**X**</span></span> | <span data-ttu-id="653a4-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="653a4-404">**Y**</span></span>               | <span data-ttu-id="653a4-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="653a4-405">**Z**</span></span> |
    | <span data-ttu-id="653a4-406">-2</span><span class="sxs-lookup"><span data-stu-id="653a4-406">-2</span></span>    | <span data-ttu-id="653a4-407">6</span><span class="sxs-lookup"><span data-stu-id="653a4-407">6</span></span>                      | <span data-ttu-id="653a4-408">9</span><span class="sxs-lookup"><span data-stu-id="653a4-408">9</span></span>     |  \| | <span data-ttu-id="653a4-409">0.1</span><span class="sxs-lookup"><span data-stu-id="653a4-409">0.1</span></span>   | <span data-ttu-id="653a4-410">0.1</span><span class="sxs-lookup"><span data-stu-id="653a4-410">0.1</span></span>                 | <span data-ttu-id="653a4-411">0.1</span><span class="sxs-lookup"><span data-stu-id="653a4-411">0.1</span></span>   | 

14. <span data-ttu-id="653a4-412">更改**字号**中**文本 Mesh**组件**50**。</span><span class="sxs-lookup"><span data-stu-id="653a4-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="653a4-413">更改*名称*的**文本 Mesh**对象传递给**听写文本**。</span><span class="sxs-lookup"><span data-stu-id="653a4-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![创建三维文本对象](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="653a4-415">层次结构面板结构现在应如下所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![文本在场景视图中的网格](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="653a4-417">最后一个场景应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-417">The final scene should look like the image below:</span></span>

    ![场景视图中。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="653a4-419">第 5 章-创建 MicrophoneManager 类</span><span class="sxs-lookup"><span data-stu-id="653a4-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="653a4-420">要创建的第一个脚本是*MicrophoneManager*类。</span><span class="sxs-lookup"><span data-stu-id="653a4-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="653a4-421">接着，您将创建*LuisManager*，则*行为*类，并最后*注视*类 （可随时创建所有这些目前为止，但将为您介绍访问每一章）。</span><span class="sxs-lookup"><span data-stu-id="653a4-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="653a4-422">*MicrophoneManager*类负责：</span><span class="sxs-lookup"><span data-stu-id="653a4-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="653a4-423">检测到耳机或 （二者是为默认值） 的计算机随附的录制设备。</span><span class="sxs-lookup"><span data-stu-id="653a4-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="653a4-424">捕获音频 （语音），并使用听写将其存储为字符串。</span><span class="sxs-lookup"><span data-stu-id="653a4-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="653a4-425">一旦语音已暂停，提交到听写*LuisManager*类。</span><span class="sxs-lookup"><span data-stu-id="653a4-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="653a4-426">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="653a4-426">To create this class:</span></span> 

1.  <span data-ttu-id="653a4-427">在中右击*项目面板*，**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="653a4-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="653a4-428">将该文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="653a4-428">Call the folder **Scripts**.</span></span> 

    ![创建脚本的文件夹。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="653a4-430">与**脚本**创建文件夹，双击它，以打开。</span><span class="sxs-lookup"><span data-stu-id="653a4-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="653a4-431">然后，在该文件夹中，右键单击，**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="653a4-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="653a4-432">脚本命名为*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="653a4-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="653a4-433">双击*MicrophoneManager*以打开其与*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="653a4-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="653a4-434">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="653a4-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="653a4-435">然后添加以下变量内的*MicrophoneManager*类：</span><span class="sxs-lookup"><span data-stu-id="653a4-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="653a4-436">为代码*Awake()* 并*start （)* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="653a4-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="653a4-437">类初始化时将会调用：</span><span class="sxs-lookup"><span data-stu-id="653a4-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="653a4-438">现在，您需要应用用于启动和停止语音捕获，并将其传递给方法*LuisManager*类，您很快就会生成。</span><span class="sxs-lookup"><span data-stu-id="653a4-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="653a4-439">添加*听写处理程序*语音暂停时，将调用的。</span><span class="sxs-lookup"><span data-stu-id="653a4-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="653a4-440">此方法将传递到的听写文本*LuisManager*类。</span><span class="sxs-lookup"><span data-stu-id="653a4-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="653a4-441">删除*update （)* 方法因为此类不会使用它。</span><span class="sxs-lookup"><span data-stu-id="653a4-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="653a4-442">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="653a4-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="653a4-443">此时你会注意到出现在错误*Unity 编辑器控制台面板*。</span><span class="sxs-lookup"><span data-stu-id="653a4-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="653a4-444">这是因为该代码引用*LuisManager*将在下一章中创建的类。</span><span class="sxs-lookup"><span data-stu-id="653a4-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="653a4-445">第 6 章-创建 LUISManager 类</span><span class="sxs-lookup"><span data-stu-id="653a4-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="653a4-446">是为您创建的时候*LuisManager*类，该类将对 Azure LUIS 服务的调用。</span><span class="sxs-lookup"><span data-stu-id="653a4-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="653a4-447">此类的目的是接收从听写文本*MicrophoneManager*类，并将其发送到*Azure 语言理解 API*若要对其进行分析。</span><span class="sxs-lookup"><span data-stu-id="653a4-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="653a4-448">此类将反序列化*JSON*响应并调用相应的方法的*行为*类，以触发操作。</span><span class="sxs-lookup"><span data-stu-id="653a4-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="653a4-449">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="653a4-449">To create this class:</span></span> 

1.  <span data-ttu-id="653a4-450">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="653a4-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="653a4-451">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="653a4-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="653a4-452">脚本命名为*LuisManager*。</span><span class="sxs-lookup"><span data-stu-id="653a4-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="653a4-453">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="653a4-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="653a4-454">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="653a4-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="653a4-455">将首先创建三个类**内** *LuisManager*类 (在相同的脚本文件中，上面*start （)* 方法)，将表示的反序列化从 Azure 的 JSON 响应。</span><span class="sxs-lookup"><span data-stu-id="653a4-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="653a4-456">接下来，添加以下变量内的*LuisManager*类：</span><span class="sxs-lookup"><span data-stu-id="653a4-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="653a4-457">请确保现在将放置在你 LUIS 的终结点 （它必须从 LUIS 门户）。</span><span class="sxs-lookup"><span data-stu-id="653a4-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="653a4-458">为代码*Awake()* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="653a4-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="653a4-459">类初始化时，将会调用此方法：</span><span class="sxs-lookup"><span data-stu-id="653a4-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="653a4-460">现在，你需要此应用程序用来发送来自听写的方法*MicrophoneManager*类来*LUIS*，然后接收和反序列化响应。</span><span class="sxs-lookup"><span data-stu-id="653a4-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="653a4-461">一旦已确定的值的意向和关联的实体，它们传递到的实例*行为*类，以触发所需的操作。</span><span class="sxs-lookup"><span data-stu-id="653a4-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="653a4-462">创建一个名为的新方法*AnalyseResponseElements()* ，它将读取生成*AnalysedQuery*并确定实体。</span><span class="sxs-lookup"><span data-stu-id="653a4-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="653a4-463">这些实体确定后，它们将被传递到的实例*行为*类，以在操作中使用。</span><span class="sxs-lookup"><span data-stu-id="653a4-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="653a4-464">删除*start （)* 并*update （)* 方法，因为此类不会使用它们。</span><span class="sxs-lookup"><span data-stu-id="653a4-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="653a4-465">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="653a4-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="653a4-466">此时你会注意到出现在多个错误*Unity 编辑器控制台面板*。</span><span class="sxs-lookup"><span data-stu-id="653a4-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="653a4-467">这是因为该代码引用*行为*将在下一章中创建的类。</span><span class="sxs-lookup"><span data-stu-id="653a4-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="653a4-468">第 7 章 – 创建行为类</span><span class="sxs-lookup"><span data-stu-id="653a4-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="653a4-469">*行为*类将触发的操作，使用提供的实体*LuisManager*类。</span><span class="sxs-lookup"><span data-stu-id="653a4-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="653a4-470">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="653a4-470">To create this class:</span></span> 

1.  <span data-ttu-id="653a4-471">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="653a4-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="653a4-472">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="653a4-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="653a4-473">脚本命名为*行为*。</span><span class="sxs-lookup"><span data-stu-id="653a4-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="653a4-474">双击要将其与打开的脚本*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="653a4-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="653a4-475">然后添加以下变量内的*行为*类：</span><span class="sxs-lookup"><span data-stu-id="653a4-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="653a4-476">添加*Awake()* 方法代码。</span><span class="sxs-lookup"><span data-stu-id="653a4-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="653a4-477">类初始化时，将会调用此方法：</span><span class="sxs-lookup"><span data-stu-id="653a4-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="653a4-478">调用以下方法*LuisManager*类 （先前已创建） 来确定哪些对象是查询的目标，然后触发相应的措施。</span><span class="sxs-lookup"><span data-stu-id="653a4-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="653a4-479">添加*FindTarget()* 方法来确定哪些*GameObjects*是当前的意向的目标。</span><span class="sxs-lookup"><span data-stu-id="653a4-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="653a4-480">此方法将默认为目标*GameObject*正在"gazed"如果未明确指定目标定义实体中。</span><span class="sxs-lookup"><span data-stu-id="653a4-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="653a4-481">删除*start （)* 并*update （)* 方法，因为此类不会使用它们。</span><span class="sxs-lookup"><span data-stu-id="653a4-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="653a4-482">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="653a4-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="653a4-483">章 8 – 创建的视线移动类</span><span class="sxs-lookup"><span data-stu-id="653a4-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="653a4-484">将需要完成此应用的最后一个类是*注视*类。</span><span class="sxs-lookup"><span data-stu-id="653a4-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="653a4-485">此类将更新对引用*GameObject*当前在用户的可视焦点。</span><span class="sxs-lookup"><span data-stu-id="653a4-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="653a4-486">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="653a4-486">To create this Class:</span></span> 

1.  <span data-ttu-id="653a4-487">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="653a4-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="653a4-488">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="653a4-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="653a4-489">脚本命名为*注视*。</span><span class="sxs-lookup"><span data-stu-id="653a4-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="653a4-490">双击要将其与打开的脚本*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="653a4-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="653a4-491">插入此类的以下代码：</span><span class="sxs-lookup"><span data-stu-id="653a4-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="653a4-492">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="653a4-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="653a4-493">第 9 章 – 完成场景设置</span><span class="sxs-lookup"><span data-stu-id="653a4-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="653a4-494">若要完成场景的安装程序，将脚本文件夹中创建每个脚本**Main Camera**对象中*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="653a4-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="653a4-495">选择**Main Camera**并查看*检查器面板*，您应该能够看到已附加，每个脚本，会注意到有尚设置每个脚本参数。</span><span class="sxs-lookup"><span data-stu-id="653a4-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![设置照相机引用目标。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="653a4-497">若要正确设置这些参数，请按照这些说明操作：</span><span class="sxs-lookup"><span data-stu-id="653a4-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="653a4-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="653a4-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="653a4-499">从*层次结构面板*，拖动**听写文本**对象插入**听写文本**参数值。</span><span class="sxs-lookup"><span data-stu-id="653a4-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="653a4-500">*行为*，从*层次结构面板*:</span><span class="sxs-lookup"><span data-stu-id="653a4-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="653a4-501">拖动**球体**对象插入*球体*引用目标。</span><span class="sxs-lookup"><span data-stu-id="653a4-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="653a4-502">拖动**柱状体**成*柱状体*引用目标。</span><span class="sxs-lookup"><span data-stu-id="653a4-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="653a4-503">拖动**多维数据集**成*多维数据集*引用目标。</span><span class="sxs-lookup"><span data-stu-id="653a4-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="653a4-504">*注视*:</span><span class="sxs-lookup"><span data-stu-id="653a4-504">*Gaze*:</span></span>

        - <span data-ttu-id="653a4-505">设置*注视最大距离*到**300** （如果还没有的话）。</span><span class="sxs-lookup"><span data-stu-id="653a4-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="653a4-506">结果应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="653a4-506">The result should look like the image below:</span></span>

    ![显示相机引用目标，现在设置。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="653a4-508">第 10 章-测试在 Unity 编辑器</span><span class="sxs-lookup"><span data-stu-id="653a4-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="653a4-509">测试场景设置正确地实现。</span><span class="sxs-lookup"><span data-stu-id="653a4-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="653a4-510">请确保：</span><span class="sxs-lookup"><span data-stu-id="653a4-510">Ensure that:</span></span>

-   <span data-ttu-id="653a4-511">所有脚本都附加到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="653a4-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="653a4-512">中的所有字段*主相机检查器面板*正确分配。</span><span class="sxs-lookup"><span data-stu-id="653a4-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="653a4-513">按**播放**按钮*Unity 编辑器*。</span><span class="sxs-lookup"><span data-stu-id="653a4-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="653a4-514">应用程序应在附加的沉浸式头戴式内运行。</span><span class="sxs-lookup"><span data-stu-id="653a4-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="653a4-515">尝试一些查询文本，例如：</span><span class="sxs-lookup"><span data-stu-id="653a4-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="653a4-516">如果看到有关更改默认音频设备 Unity 控制台中的错误，场景可能无法按预期方式。</span><span class="sxs-lookup"><span data-stu-id="653a4-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="653a4-517">这是由于混合的现实门户内置麦克风耳机具有它们的处理的方式。</span><span class="sxs-lookup"><span data-stu-id="653a4-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="653a4-518">如果看到此错误，只需停止场景并重新启动它，并且应该可以正常为预期。</span><span class="sxs-lookup"><span data-stu-id="653a4-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="653a4-519">第 11 章 – 生成和旁加载 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="653a4-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="653a4-520">一旦你可确保应用程序使用在 Unity 编辑器中，已准备好生成和部署。</span><span class="sxs-lookup"><span data-stu-id="653a4-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="653a4-521">若要生成：</span><span class="sxs-lookup"><span data-stu-id="653a4-521">To Build:</span></span>

1.  <span data-ttu-id="653a4-522">通过单击保存当前场景**文件 > 保存**。</span><span class="sxs-lookup"><span data-stu-id="653a4-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="653a4-523">转到**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="653a4-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="653a4-524">选中名为框**UnityC#项目**（用于查看和创建 UWP 项目后调试代码。</span><span class="sxs-lookup"><span data-stu-id="653a4-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="653a4-525">单击**添加打开场景**，然后单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="653a4-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![生成设置窗口](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="653a4-527">系统将提示您选择你想要生成解决方案的文件夹。</span><span class="sxs-lookup"><span data-stu-id="653a4-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="653a4-528">创建*生成*文件夹并在该文件夹中创建另一个文件夹，与所选的适当的名称。</span><span class="sxs-lookup"><span data-stu-id="653a4-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="653a4-529">单击**选择文件夹**若要开始在该位置的生成。</span><span class="sxs-lookup"><span data-stu-id="653a4-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="653a4-530">![创建内部版本文件夹](images/AzureLabs-Lab3-44.png)
    ![选择生成文件夹](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="653a4-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="653a4-531">一次 Unity 已完成的生成 （它可能需要一些时间），它应打开**文件资源管理器**窗口在生成的位置。</span><span class="sxs-lookup"><span data-stu-id="653a4-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="653a4-532">若要在本地计算机上部署：</span><span class="sxs-lookup"><span data-stu-id="653a4-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="653a4-533">在中*Visual Studio*，打开已在中创建的解决方案文件[上一章](#chapter-10--test-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="653a4-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="653a4-534">在中**解决方案平台**，选择**x86**，**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="653a4-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="653a4-535">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="653a4-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="653a4-536">对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="653a4-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="653a4-537">不过，需要还执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="653a4-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="653a4-538">知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="653a4-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="653a4-539">请确保**开发人员模式**是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。</span><span class="sxs-lookup"><span data-stu-id="653a4-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![将应用部署](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="653a4-541">转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。</span><span class="sxs-lookup"><span data-stu-id="653a4-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="653a4-542">你的应用现在应出现在列表中的已安装的应用，准备好启动 ！</span><span class="sxs-lookup"><span data-stu-id="653a4-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="653a4-543">启动后，应用将提示你授予访问权限_麦克风_。</span><span class="sxs-lookup"><span data-stu-id="653a4-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="653a4-544">使用*运动控制器*，或*语音输入*，或*键盘*按**是**按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="653a4-545">第 12 章-提高 LUIS 服务</span><span class="sxs-lookup"><span data-stu-id="653a4-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="653a4-546">这一章非常重要，可能需要为 interated 后几次，这会有助于提高准确性 LUIS 服务： 请确保完成此操作。</span><span class="sxs-lookup"><span data-stu-id="653a4-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="653a4-547">若要改进的级别提供的 LUIS 理解需要捕获新查询文本并使用它们来重新训练 LUIS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="653a4-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="653a4-548">例如，你可能具有经过培训 LUIS 了解"Increase"和"降级"，但不希望您的应用程序，以便了解"放大"等单词？</span><span class="sxs-lookup"><span data-stu-id="653a4-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="653a4-549">在使用你的应用程序几次，所有内容你说将收集的 LUIS，LUIS 门户中提供。</span><span class="sxs-lookup"><span data-stu-id="653a4-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="653a4-550">转到门户应用以下这[链接](https://www.luis.ai/home)，和日志中。</span><span class="sxs-lookup"><span data-stu-id="653a4-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="653a4-551">一旦使用 MS 凭据登录，单击你*应用名称*。</span><span class="sxs-lookup"><span data-stu-id="653a4-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="653a4-552">单击**查看终结点语音样本**页面左侧的按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![查看查询文本](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="653a4-554">将显示一系列在混合现实应用程序发送到 LUIS 语音样本。</span><span class="sxs-lookup"><span data-stu-id="653a4-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![查询文本的列表](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="653a4-556">你会注意到一些突出显示*实体*。</span><span class="sxs-lookup"><span data-stu-id="653a4-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="653a4-557">悬停在每个突出显示单词时，可以查看每个语音样本，并确定哪些实体具有已正确识别，这是错误的实体，哪些实体会丢失。</span><span class="sxs-lookup"><span data-stu-id="653a4-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="653a4-558">在上面的示例中，它已找到，"鱼叉式"一词有已突出显示为目标，因此它可以纠正该错误，可以悬停在该单词设置为鼠标，然后单击所需**删除标签**。</span><span class="sxs-lookup"><span data-stu-id="653a4-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="653a4-559">![检查语音样本](images/AzureLabs-Lab3-49.png)
![删除标签图像](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="653a4-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="653a4-560">如果发现有完全错误时的语音样本，则可以删除它们使用**删除**屏幕右侧的按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![删除错误的查询文本](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="653a4-562">或如果您认为 LUIS 已正确解释语音样本，您可以通过使用验证其对理解**添加到对齐意向**按钮。</span><span class="sxs-lookup"><span data-stu-id="653a4-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![将添加到对齐意向](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="653a4-564">已排序的显示语音样本后, 重试并重新加载页后，可以查看的详细信息是否可用。</span><span class="sxs-lookup"><span data-stu-id="653a4-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="653a4-565">它是重复多次以尽可能提高应用程序了解此过程非常重要。</span><span class="sxs-lookup"><span data-stu-id="653a4-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="653a4-566">**玩得愉快！**</span><span class="sxs-lookup"><span data-stu-id="653a4-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="653a4-567">完成的 LUIS 集成应用程序</span><span class="sxs-lookup"><span data-stu-id="653a4-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="653a4-568">祝贺你，构建利用 Azure 语言理解智能服务，以了解用户显示和处理该信息的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="653a4-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![实验结果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="653a4-570">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="653a4-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="653a4-571">练习 1</span><span class="sxs-lookup"><span data-stu-id="653a4-571">Exercise 1</span></span>

<span data-ttu-id="653a4-572">使用此应用程序时可能会注意到，是否您注视 Floor 对象，并要求更改其颜色，它都会这样。</span><span class="sxs-lookup"><span data-stu-id="653a4-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="653a4-573">您可以推断出如何停止您的应用程序更改基底的颜色？</span><span class="sxs-lookup"><span data-stu-id="653a4-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="653a4-574">练习 2</span><span class="sxs-lookup"><span data-stu-id="653a4-574">Exercise 2</span></span>

<span data-ttu-id="653a4-575">请尝试将 LUIS 和应用程序功能，在场景; 中添加对象的附加功能扩展例如，在提供注视命中的点，具体取决于哪些用户显示，并便能够使用这些对象，以及当前场景对象，使用现有的命令创建新对象。</span><span class="sxs-lookup"><span data-stu-id="653a4-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
