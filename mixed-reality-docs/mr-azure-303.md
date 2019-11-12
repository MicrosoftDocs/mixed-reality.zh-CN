---
title: MR 和 Azure 303-自然语言理解（LUIS）
description: 完成本课程以了解如何在混合现实应用程序中实现 Azure 语言理解智能服务（LUIS）。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，语言理解智能服务，luis，hololens，沉浸，vr
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926808"
---
>[!NOTE]
><span data-ttu-id="2eb93-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="2eb93-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2eb93-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="2eb93-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2eb93-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="2eb93-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2eb93-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="2eb93-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2eb93-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="2eb93-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2eb93-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="2eb93-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="2eb93-110">MR 和 Azure 303：自然语言理解（LUIS）</span><span class="sxs-lookup"><span data-stu-id="2eb93-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="2eb93-111">在本课程中，你将了解如何使用 Azure 认知服务将语言理解集成到混合现实应用程序中，语言理解 API。</span><span class="sxs-lookup"><span data-stu-id="2eb93-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![实验室结果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="2eb93-113">*语言理解（LUIS）* 是一种 Microsoft Azure 服务，它使应用程序能够从用户输入中代替用户输入，例如通过提取用户可能需要的内容。</span><span class="sxs-lookup"><span data-stu-id="2eb93-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="2eb93-114">这是通过机器学习来实现的，它可以理解和学习输入信息，然后可以使用详细的相关信息进行回复。</span><span class="sxs-lookup"><span data-stu-id="2eb93-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="2eb93-115">有关详细信息，请访问[Azure 语言理解（LUIS）页](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。</span><span class="sxs-lookup"><span data-stu-id="2eb93-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="2eb93-116">完成本课程后，你将拥有一个混合现实沉浸式耳机应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2eb93-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="2eb93-117">使用连接到沉浸式耳机的麦克风捕获用户输入语音。</span><span class="sxs-lookup"><span data-stu-id="2eb93-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="2eb93-118">将捕获的听写发送到*Azure 语言理解智能服务*（*LUIS*）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="2eb93-119">让 LUIS 从发送信息中提取含义，将对其进行分析，并尝试确定用户请求的意图。</span><span class="sxs-lookup"><span data-stu-id="2eb93-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="2eb93-120">开发过程包括创建一个应用程序，用户可以使用该应用程序来更改场景中对象的大小和颜色。</span><span class="sxs-lookup"><span data-stu-id="2eb93-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="2eb93-121">不会覆盖运动控制器的使用。</span><span class="sxs-lookup"><span data-stu-id="2eb93-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="2eb93-122">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="2eb93-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="2eb93-123">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="2eb93-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="2eb93-124">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="2eb93-125">准备多次训练 LUIS，这将在第[12 章](#chapter-12--improving-your-luis-service)中介绍。</span><span class="sxs-lookup"><span data-stu-id="2eb93-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="2eb93-126">更好的结果是训练 LUIS 的次数越多。</span><span class="sxs-lookup"><span data-stu-id="2eb93-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="2eb93-127">设备支持</span><span class="sxs-lookup"><span data-stu-id="2eb93-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2eb93-128">摘要</span><span class="sxs-lookup"><span data-stu-id="2eb93-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2eb93-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2eb93-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2eb93-130"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="2eb93-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="2eb93-131">MR 和 Azure 303：自然语言理解（LUIS）</span><span class="sxs-lookup"><span data-stu-id="2eb93-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="2eb93-132">✔️</span><span class="sxs-lookup"><span data-stu-id="2eb93-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2eb93-133">✔️</span><span class="sxs-lookup"><span data-stu-id="2eb93-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2eb93-134">尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2eb93-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="2eb93-135">在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="2eb93-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="2eb93-136">使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。</span><span class="sxs-lookup"><span data-stu-id="2eb93-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2eb93-137">必备条件</span><span class="sxs-lookup"><span data-stu-id="2eb93-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2eb93-138">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="2eb93-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2eb93-139">另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="2eb93-140">您可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="2eb93-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="2eb93-141">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="2eb93-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2eb93-142">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="2eb93-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2eb93-143">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="2eb93-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="2eb93-144">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="2eb93-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="2eb93-145">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="2eb93-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="2eb93-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2eb93-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="2eb93-147">启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="2eb93-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="2eb93-148">带有内置麦克风的一组耳机（如果耳机没有内置麦克风和扬声器）</span><span class="sxs-lookup"><span data-stu-id="2eb93-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="2eb93-149">Azure 安装和 LUIS 检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="2eb93-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2eb93-150">开始之前</span><span class="sxs-lookup"><span data-stu-id="2eb93-150">Before you start</span></span>

1.  <span data-ttu-id="2eb93-151">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="2eb93-152">若要允许计算机启用听写，请转到 " **Windows 设置" > 隐私 > 语音 "、" 墨迹书写 & 键入**"和"**打开语音服务并键入建议**"按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="2eb93-153">本教程中的代码将允许你从计算机上的**默认麦克风设备**设置进行录制。</span><span class="sxs-lookup"><span data-stu-id="2eb93-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="2eb93-154">请确保将默认麦克风设备设置为要用于捕获语音的设备。</span><span class="sxs-lookup"><span data-stu-id="2eb93-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="2eb93-155">如果耳机有内置麦克风，请确保在*混合现实门户*设置中启用 *"我戴上耳机，切换到耳机麦克风"* 选项。</span><span class="sxs-lookup"><span data-stu-id="2eb93-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![设置沉浸式耳机](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="2eb93-157">第1章–设置 Azure 门户</span><span class="sxs-lookup"><span data-stu-id="2eb93-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="2eb93-158">若要在 Azure 中使用*语言理解*服务，你将需要配置服务的实例，使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2eb93-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="2eb93-159">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="2eb93-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2eb93-160">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="2eb93-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2eb93-161">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="2eb93-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2eb93-162">登录后，单击左上角的 "**新建**"，搜索 "*语言理解*"，然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![创建 LUIS 资源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="2eb93-164">在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="2eb93-165">向右的新页将提供语言理解服务的说明。</span><span class="sxs-lookup"><span data-stu-id="2eb93-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="2eb93-166">在此页的左下角，选择 "**创建**" 按钮以创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="2eb93-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![创建 LUIS 服务-法律声明](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="2eb93-168">单击 "创建" 后：</span><span class="sxs-lookup"><span data-stu-id="2eb93-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="2eb93-169">为此服务实例插入所需的**名称**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="2eb93-170">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="2eb93-171">选择适合你的**定价层**，如果这是第一次创建*LUIS 服务*，则你应该可以使用免费层（名为 F0）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="2eb93-172">对于本课程，免费分配应该已经足够。</span><span class="sxs-lookup"><span data-stu-id="2eb93-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="2eb93-173">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="2eb93-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="2eb93-174">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="2eb93-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2eb93-175">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="2eb93-176">若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="2eb93-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="2eb93-177">确定资源组的**位置**（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2eb93-178">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2eb93-179">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="2eb93-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="2eb93-180">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="2eb93-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="2eb93-181">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="2eb93-181">Select **Create**.</span></span>

        ![创建 LUIS 服务-用户输入](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="2eb93-183">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="2eb93-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="2eb93-184">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="2eb93-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新的 Azure 通知映像](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="2eb93-186">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="2eb93-186">Click on the notification to explore your new Service instance.</span></span>

    ![成功创建资源通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="2eb93-188">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="2eb93-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="2eb93-189">你将转到新的 LUIS 服务实例。</span><span class="sxs-lookup"><span data-stu-id="2eb93-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![访问 LUIS 项](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="2eb93-191">在本教程中，你的应用程序将需要调用你的服务，这是通过使用你的服务的订阅密钥来完成的。</span><span class="sxs-lookup"><span data-stu-id="2eb93-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="2eb93-192">在*LUIS API*服务的 "*快速启动*" 页上，导航到第一步，*获取你的密钥*，然后单击 "**密钥**" （也可以通过单击位于 "服务" 导航菜单中的蓝色超链接项（由键图标表示）来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="2eb93-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="2eb93-193">这会显示你的服务*密钥*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="2eb93-194">复制其中一个所显示的密钥，因为稍后会在项目中使用此密钥。</span><span class="sxs-lookup"><span data-stu-id="2eb93-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="2eb93-195">在 "*服务*" 页上，单击 "*语言理解门户*" 以重定向到在 LUIS 应用中用于创建新服务的网页。</span><span class="sxs-lookup"><span data-stu-id="2eb93-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="2eb93-196">第2章–语言理解门户</span><span class="sxs-lookup"><span data-stu-id="2eb93-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="2eb93-197">在本部分中，你将了解如何在 LUIS 门户中创建 LUIS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="2eb93-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="2eb93-198">请注意，在本章中设置*实体*、*意向*和*最谈话*只是构建 LUIS 服务的第一步：你还需要多次重新训练服务，以便使其更准确。</span><span class="sxs-lookup"><span data-stu-id="2eb93-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="2eb93-199">本课程的[最后一章](#chapter-12--improving-your-luis-service)介绍了重新训练你的服务，因此请确保完成此操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="2eb93-200">进入*语言理解门户*后，你可能需要登录（如果尚未登录），其凭据与 Azure 门户相同。</span><span class="sxs-lookup"><span data-stu-id="2eb93-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 登录页](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="2eb93-202">如果这是你第一次使用 LUIS，则需要向下滚动到 "欢迎" 页的底部，查找并单击 "**创建 LUIS 应用**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    !["创建 LUIS 应用" 页](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="2eb93-204">登录后，单击 **"我的应用**" （如果当前不在该部分中）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="2eb93-205">然后，可以单击 "**创建新应用**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-205">You can then click on **Create new app**.</span></span>

    ![LUIS-我的应用图像](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="2eb93-207">为应用程序*命名*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="2eb93-208">如果你的应用程序应了解不同于英语的语言，则应将*区域性*更改为适当的语言。</span><span class="sxs-lookup"><span data-stu-id="2eb93-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="2eb93-209">你还可以在此处添加新的 LUIS 应用的*描述*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-创建新应用](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="2eb93-211">按下 "**完成**" 后，将进入新*LUIS*应用程序的 "*生成*" 页。</span><span class="sxs-lookup"><span data-stu-id="2eb93-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="2eb93-212">此处有几个重要概念需要了解：</span><span class="sxs-lookup"><span data-stu-id="2eb93-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="2eb93-213">*意向*，表示将从用户查询后调用的方法。</span><span class="sxs-lookup"><span data-stu-id="2eb93-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="2eb93-214">*意向*可以有一个或多个*实体*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="2eb93-215">*实体*，是描述与*意向*相关的信息的查询组件。</span><span class="sxs-lookup"><span data-stu-id="2eb93-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="2eb93-216">*最谈话*是由开发人员提供的查询的示例，LUIS 将使用该查询来训练自身。</span><span class="sxs-lookup"><span data-stu-id="2eb93-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="2eb93-217">如果这些概念并不完全清晰，请不要担心，因为本课程将在本章中进一步阐明它们。</span><span class="sxs-lookup"><span data-stu-id="2eb93-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="2eb93-218">首先创建生成此课程所需的*实体*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="2eb93-219">在页面左侧，单击 "*实体*"，并单击 "**创建新实体**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![创建新实体](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="2eb93-221">调用新的实体*颜色*，将其类型设置为 "*简单*"，并按 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![创建简单实体-颜色](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="2eb93-223">重复此过程以创建三个（3）个名更简单的实体：</span><span class="sxs-lookup"><span data-stu-id="2eb93-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="2eb93-224">*降级*</span><span class="sxs-lookup"><span data-stu-id="2eb93-224">*upsize*</span></span>
    -   <span data-ttu-id="2eb93-225">*缩小*</span><span class="sxs-lookup"><span data-stu-id="2eb93-225">*downsize*</span></span>
    -   <span data-ttu-id="2eb93-226">*靶*</span><span class="sxs-lookup"><span data-stu-id="2eb93-226">*target*</span></span>

<span data-ttu-id="2eb93-227">结果应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-227">The result should look like the image below:</span></span>

![实体创建的结果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="2eb93-229">此时，你可以开始创建*意向*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="2eb93-230">请勿删除 "**无**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="2eb93-231">在页面左侧，单击 "选择 **"，然后**单击 "**创建新意向**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![创建新意向](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="2eb93-233">调用新*意向* **ChangeObjectColor**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="2eb93-234">本课程后面的代码中使用此*意向*名称，因此为了获得最佳结果，请完全按所提供的名称使用此名称。</span><span class="sxs-lookup"><span data-stu-id="2eb93-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="2eb93-235">确认名称后，将定向到 "意向" 页。</span><span class="sxs-lookup"><span data-stu-id="2eb93-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS 页](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="2eb93-237">你会注意到有一个文本框要求你键入5个或更多不同的*最谈话*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="2eb93-238">LUIS 将所有最谈话都转换为小写。</span><span class="sxs-lookup"><span data-stu-id="2eb93-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="2eb93-239">在顶部文本框中插入以下*查询文本*（当前文本*类型约为5个示例 ...*</span><span class="sxs-lookup"><span data-stu-id="2eb93-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="2eb93-240">），然后按**enter**：</span><span class="sxs-lookup"><span data-stu-id="2eb93-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="2eb93-241">你会注意到，新的*查询文本*将显示在下面的列表中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="2eb93-242">按照相同的过程，插入以下六个（6）最谈话：</span><span class="sxs-lookup"><span data-stu-id="2eb93-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="2eb93-243">对于创建的每个查询文本，必须确定 LUIS 将哪些字词作为实体使用。</span><span class="sxs-lookup"><span data-stu-id="2eb93-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="2eb93-244">在此示例中，需要将所有颜色标记为一个*颜色*实体，并将所有可能的引用标记为*目标实体。*</span><span class="sxs-lookup"><span data-stu-id="2eb93-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="2eb93-245">为此，请在第一个查询文本中单击 "*圆柱*"，然后选择 "*目标*"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![标识查询文本目标](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="2eb93-247">现在，在第一个查询文本中单击 "*红色*"，然后选择 "*颜色*"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![标识查询文本实体](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="2eb93-249">标记下一行，其中， *cube*应为*目标*，*黑色*应为一种*颜色*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="2eb93-250">另请注意，我们提供了单词 *"this"* 、 *"it"* 和 *"this object"* ，因此还提供了非特定目标类型。</span><span class="sxs-lookup"><span data-stu-id="2eb93-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="2eb93-251">重复上述过程，直到所有最谈话都具有标记的实体。</span><span class="sxs-lookup"><span data-stu-id="2eb93-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="2eb93-252">如果需要帮助，请参阅下图。</span><span class="sxs-lookup"><span data-stu-id="2eb93-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="2eb93-253">选择字词以将其标记为实体时：</span><span class="sxs-lookup"><span data-stu-id="2eb93-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="2eb93-254">只需单击一下即可。</span><span class="sxs-lookup"><span data-stu-id="2eb93-254">For single words just click them.</span></span>
    > - <span data-ttu-id="2eb93-255">对于两个或多个单词的集合，请单击 "开始"，然后在集末尾单击。</span><span class="sxs-lookup"><span data-stu-id="2eb93-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2eb93-256">您可以使用 "*标记视图*" 切换按钮在**实体/标记视图**之间切换！</span><span class="sxs-lookup"><span data-stu-id="2eb93-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="2eb93-257">结果应如下图所示，其中显示了 "**实体/标记" 视图**：</span><span class="sxs-lookup"><span data-stu-id="2eb93-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![标记 & 实体视图](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="2eb93-259">此时，按页面右上角的 "**训练**" 按钮，并等待其上的小圆形指示器变为绿色。</span><span class="sxs-lookup"><span data-stu-id="2eb93-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="2eb93-260">这表示已成功训练 LUIS 以识别此目的。</span><span class="sxs-lookup"><span data-stu-id="2eb93-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![训练 LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="2eb93-262">作为练习，使用实体*target*、*升迁*和*缩小*创建名为**ChangeObjectSize**的新意向。</span><span class="sxs-lookup"><span data-stu-id="2eb93-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="2eb93-263">遵循与上一意向相同的过程，插入以下八个（8）最谈话*大小*更改：</span><span class="sxs-lookup"><span data-stu-id="2eb93-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="2eb93-264">结果应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-264">The result should be like the one in the image below:</span></span>

    ![设置 ChangeObjectSize 令牌/实体](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="2eb93-266">一旦创建并训练了**ChangeObjectColor**和**ChangeObjectSize**，单击页面顶部的 "**发布**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![发布 LUIS 服务](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="2eb93-268">在 "*发布*" 页上，您将完成并发布 LUIS 应用程序，以便您的代码可以访问它。</span><span class="sxs-lookup"><span data-stu-id="2eb93-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="2eb93-269">将下拉 "*发布到*" 设置为 "**生产**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="2eb93-270">将*时区*设置为时区。</span><span class="sxs-lookup"><span data-stu-id="2eb93-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="2eb93-271">选中 "**包括所有预测意向分数**" 框。</span><span class="sxs-lookup"><span data-stu-id="2eb93-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="2eb93-272">单击 "**发布到生产槽**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-272">Click on **Publish to Production Slot**.</span></span>

        ![发布设置](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="2eb93-274">在 "*资源和密钥*" 部分中：</span><span class="sxs-lookup"><span data-stu-id="2eb93-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="2eb93-275">在 Azure 门户中选择为服务实例设置的区域。</span><span class="sxs-lookup"><span data-stu-id="2eb93-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="2eb93-276">你将注意到下面的一个**Starter_Key**元素，请将其忽略。</span><span class="sxs-lookup"><span data-stu-id="2eb93-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="2eb93-277">单击 "**添加密钥**"，并在创建服务实例时插入在 Azure 门户中获取的*密钥*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="2eb93-278">如果你的 Azure 和 LUIS 门户登录到同一用户，你将向你提供 "*租户名称*"、"*订阅名称*" 和你想要使用的*密钥*的下拉菜单（与你之前在 Azure 门户中提供的名称相同）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="2eb93-279">在 "*终结点*" 下，获取与所插入的密钥对应的终结点副本，然后在代码中立即使用该副本。</span><span class="sxs-lookup"><span data-stu-id="2eb93-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="2eb93-280">第3章–设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="2eb93-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="2eb93-281">下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="2eb93-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="2eb93-282">打开*Unity* ，并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-282">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="2eb93-284">你现在需要提供 Unity 项目名称，插入**MR_LUIS**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="2eb93-285">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="2eb93-286">将位置设置为合适的**位置**（请记住，更接近根目录更好）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2eb93-287">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-287">Then, click **Create project**.</span></span>

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="2eb93-289">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="2eb93-290">转到 "编辑 > 首选项"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2eb93-291">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2eb93-292">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="2eb93-292">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="2eb93-294">接下来，通过单击 "**切换平台**" 按钮转到 "**文件 > 生成设置**"，并将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="2eb93-296">请参阅**文件 > 生成设置**，并确保：</span><span class="sxs-lookup"><span data-stu-id="2eb93-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="2eb93-297">**目标设备**设置为**任何设备**</span><span class="sxs-lookup"><span data-stu-id="2eb93-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="2eb93-298">对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="2eb93-299">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="2eb93-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="2eb93-300">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="2eb93-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="2eb93-301">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="2eb93-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="2eb93-302">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="2eb93-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="2eb93-303">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="2eb93-304">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="2eb93-305">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="2eb93-305">A save window will appear.</span></span>
        
            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="2eb93-307">为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 "**新建文件夹**" 按钮以创建新文件夹，将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            !["创建新脚本" 文件夹](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="2eb93-309">打开新创建的**场景**文件夹，然后*在 "文件名：文本" 字段*中，键入**MR_LuisScene**，然后按 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![为新场景指定名称。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="2eb93-311">现在，"*生成设置*" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="2eb93-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="2eb93-312">在 "*生成设置*" 窗口中，单击 "**播放机设置**" 按钮，这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="2eb93-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放机设置。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="2eb93-314">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="2eb93-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="2eb93-315">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="2eb93-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="2eb93-316">**脚本运行时版本**应**稳定**（与 .net 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="2eb93-317">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="2eb93-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="2eb93-318">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="2eb93-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="2eb93-320">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="2eb93-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="2eb93-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="2eb93-321">**InternetClient**</span></span>
        2. <span data-ttu-id="2eb93-322">**十分**</span><span class="sxs-lookup"><span data-stu-id="2eb93-322">**Microphone**</span></span>

            ![正在更新发布设置。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="2eb93-324">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="2eb93-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 设置。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="2eb93-326">"返回*生成设置* _" C# Unity_项目不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="2eb93-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="2eb93-327">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="2eb93-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="2eb93-328">保存场景和项目（**file > SAVE 场景/file > SAVE Project**）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="2eb93-329">第4章-创建场景</span><span class="sxs-lookup"><span data-stu-id="2eb93-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2eb93-330">如果希望跳过本课程的*Unity 设置*组件，并继续直接进入代码，可以下载[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从[第5章](#chapter-5--create-the-microphonemanager-class)继续。</span><span class="sxs-lookup"><span data-stu-id="2eb93-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="2eb93-331">右键单击 "*层次结构" 面板*的空白区域中的 " **3d 对象**" 下的 "添加**平面**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![创建平面。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="2eb93-333">请注意，在*层次结构*中再次右键单击以创建多个对象时，如果仍选择最后一个对象，则所选对象将是新对象的父对象。</span><span class="sxs-lookup"><span data-stu-id="2eb93-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="2eb93-334">避免在层次结构内的空白区域中左键单击，然后右键单击。</span><span class="sxs-lookup"><span data-stu-id="2eb93-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="2eb93-335">重复上述过程以添加以下对象：</span><span class="sxs-lookup"><span data-stu-id="2eb93-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="2eb93-336">*球面*</span><span class="sxs-lookup"><span data-stu-id="2eb93-336">*Sphere*</span></span>
    2. <span data-ttu-id="2eb93-337">*圆柱体*</span><span class="sxs-lookup"><span data-stu-id="2eb93-337">*Cylinder*</span></span>
    3. <span data-ttu-id="2eb93-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="2eb93-338">*Cube*</span></span>
    4. <span data-ttu-id="2eb93-339">*3D 文本*</span><span class="sxs-lookup"><span data-stu-id="2eb93-339">*3D Text*</span></span>

4.  <span data-ttu-id="2eb93-340">生成的场景*层次结构*应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![场景层次结构设置。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="2eb93-342">在**摄像机**上左键单击以选择它，查看 "*检查器" 面板*，其中包含其所有组件。</span><span class="sxs-lookup"><span data-stu-id="2eb93-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="2eb93-343">单击位于 "*检查器" 面板*底部的 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![添加音频源](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="2eb93-345">搜索名为 "*音频源*" 的组件，如上所示。</span><span class="sxs-lookup"><span data-stu-id="2eb93-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="2eb93-346">此外，请确保将摄像机的*转换*组件设置为（0，0，0），可以通过按下相机的*转换*组件旁边的**齿轮**图标，然后选择 "**重置**" 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="2eb93-347">*转换*组件如下所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="2eb93-348">*位置*设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="2eb93-349">*旋转*设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="2eb93-350">对于 Microsoft HoloLens，你还需要更改以下内容，这是**相机**组件（位于你的**主摄像机**上）的一部分：</span><span class="sxs-lookup"><span data-stu-id="2eb93-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="2eb93-351">**清除标志：** 纯色。</span><span class="sxs-lookup"><span data-stu-id="2eb93-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="2eb93-352">**背景**"黑色，Alpha 0" –十六进制颜色： #00000000。</span><span class="sxs-lookup"><span data-stu-id="2eb93-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="2eb93-353">在**平面**上单击以将其选中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="2eb93-354">在 "*检查器" 面板*中，用以下值设置*转换*组件：</span><span class="sxs-lookup"><span data-stu-id="2eb93-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="2eb93-355">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="2eb93-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="2eb93-356">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-356">**X**</span></span> | <span data-ttu-id="2eb93-357">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-357">**Y**</span></span>                  | <span data-ttu-id="2eb93-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-358">**Z**</span></span> |
    | <span data-ttu-id="2eb93-359">0</span><span class="sxs-lookup"><span data-stu-id="2eb93-359">0</span></span>     | <span data-ttu-id="2eb93-360">-1</span><span class="sxs-lookup"><span data-stu-id="2eb93-360">-1</span></span>                     | <span data-ttu-id="2eb93-361">0</span><span class="sxs-lookup"><span data-stu-id="2eb93-361">0</span></span>     |


10. <span data-ttu-id="2eb93-362">左键单击**球体**将其选中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="2eb93-363">在 "*检查器" 面板*中，用以下值设置*转换*组件：</span><span class="sxs-lookup"><span data-stu-id="2eb93-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="2eb93-364">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="2eb93-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="2eb93-365">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-365">**X**</span></span> | <span data-ttu-id="2eb93-366">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-366">**Y**</span></span>                  | <span data-ttu-id="2eb93-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-367">**Z**</span></span> |
    | <span data-ttu-id="2eb93-368">2</span><span class="sxs-lookup"><span data-stu-id="2eb93-368">2</span></span>     | <span data-ttu-id="2eb93-369">1</span><span class="sxs-lookup"><span data-stu-id="2eb93-369">1</span></span>                      | <span data-ttu-id="2eb93-370">2</span><span class="sxs-lookup"><span data-stu-id="2eb93-370">2</span></span>     |

11. <span data-ttu-id="2eb93-371">左键单击**圆柱体**以将其选中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="2eb93-372">在 "*检查器" 面板*中，用以下值设置*转换*组件：</span><span class="sxs-lookup"><span data-stu-id="2eb93-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="2eb93-373">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="2eb93-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="2eb93-374">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-374">**X**</span></span> | <span data-ttu-id="2eb93-375">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-375">**Y**</span></span>                  | <span data-ttu-id="2eb93-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-376">**Z**</span></span> |
    | <span data-ttu-id="2eb93-377">-2</span><span class="sxs-lookup"><span data-stu-id="2eb93-377">-2</span></span>    | <span data-ttu-id="2eb93-378">1</span><span class="sxs-lookup"><span data-stu-id="2eb93-378">1</span></span>                      | <span data-ttu-id="2eb93-379">2</span><span class="sxs-lookup"><span data-stu-id="2eb93-379">2</span></span>     |

12. <span data-ttu-id="2eb93-380">左键单击**多维数据集**以将其选中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="2eb93-381">在 "*检查器" 面板*中，用以下值设置*转换*组件：</span><span class="sxs-lookup"><span data-stu-id="2eb93-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="2eb93-382">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="2eb93-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="2eb93-383">转换-*旋转*</span><span class="sxs-lookup"><span data-stu-id="2eb93-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="2eb93-384">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-384">**X**</span></span> | <span data-ttu-id="2eb93-385">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-385">**Y**</span></span>                   | <span data-ttu-id="2eb93-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-386">**Z**</span></span> |  \| | <span data-ttu-id="2eb93-387">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-387">**X**</span></span> | <span data-ttu-id="2eb93-388">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-388">**Y**</span></span>                  | <span data-ttu-id="2eb93-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-389">**Z**</span></span> |
    | <span data-ttu-id="2eb93-390">0</span><span class="sxs-lookup"><span data-stu-id="2eb93-390">0</span></span>     | <span data-ttu-id="2eb93-391">1</span><span class="sxs-lookup"><span data-stu-id="2eb93-391">1</span></span>                       | <span data-ttu-id="2eb93-392">4</span><span class="sxs-lookup"><span data-stu-id="2eb93-392">4</span></span>     |  \| | <span data-ttu-id="2eb93-393">45</span><span class="sxs-lookup"><span data-stu-id="2eb93-393">45</span></span>    | <span data-ttu-id="2eb93-394">45</span><span class="sxs-lookup"><span data-stu-id="2eb93-394">45</span></span>                     | <span data-ttu-id="2eb93-395">0</span><span class="sxs-lookup"><span data-stu-id="2eb93-395">0</span></span>     | 

13. <span data-ttu-id="2eb93-396">左键单击新的**文本**对象以将其选中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="2eb93-397">在 "*检查器" 面板*中，用以下值设置*转换*组件：</span><span class="sxs-lookup"><span data-stu-id="2eb93-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="2eb93-398">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="2eb93-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="2eb93-399">转换-*缩放*</span><span class="sxs-lookup"><span data-stu-id="2eb93-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="2eb93-400">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-400">**X**</span></span> | <span data-ttu-id="2eb93-401">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-401">**Y**</span></span>                  | <span data-ttu-id="2eb93-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-402">**Z**</span></span> |  \| | <span data-ttu-id="2eb93-403">**X-blade**</span><span class="sxs-lookup"><span data-stu-id="2eb93-403">**X**</span></span> | <span data-ttu-id="2eb93-404">**误差**</span><span class="sxs-lookup"><span data-stu-id="2eb93-404">**Y**</span></span>               | <span data-ttu-id="2eb93-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="2eb93-405">**Z**</span></span> |
    | <span data-ttu-id="2eb93-406">-2</span><span class="sxs-lookup"><span data-stu-id="2eb93-406">-2</span></span>    | <span data-ttu-id="2eb93-407">6</span><span class="sxs-lookup"><span data-stu-id="2eb93-407">6</span></span>                      | <span data-ttu-id="2eb93-408">9</span><span class="sxs-lookup"><span data-stu-id="2eb93-408">9</span></span>     |  \| | <span data-ttu-id="2eb93-409">0.1</span><span class="sxs-lookup"><span data-stu-id="2eb93-409">0.1</span></span>   | <span data-ttu-id="2eb93-410">0.1</span><span class="sxs-lookup"><span data-stu-id="2eb93-410">0.1</span></span>                 | <span data-ttu-id="2eb93-411">0.1</span><span class="sxs-lookup"><span data-stu-id="2eb93-411">0.1</span></span>   | 

14. <span data-ttu-id="2eb93-412">在**文本网格**组件中将**字体大小**更改为**50**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="2eb93-413">将**文本网格**对象的*名称*更改为 "**听写文本**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![创建3D 文本对象](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="2eb93-415">层次结构面板结构现在应如下所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![场景视图中的文本网格](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="2eb93-417">最终场景应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-417">The final scene should look like the image below:</span></span>

    ![场景视图。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="2eb93-419">第5章–创建 MicrophoneManager 类</span><span class="sxs-lookup"><span data-stu-id="2eb93-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="2eb93-420">要创建的第一个脚本是*MicrophoneManager*类。</span><span class="sxs-lookup"><span data-stu-id="2eb93-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="2eb93-421">接下来，你将创建*LuisManager*和*行为*类，最后是一个*注视*类（现在可以自由地创建所有这些类，但在每个章节中将会介绍）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="2eb93-422">*MicrophoneManager*类负责：</span><span class="sxs-lookup"><span data-stu-id="2eb93-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="2eb93-423">检测连接到耳机或计算机的记录设备（以默认值为准）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="2eb93-424">捕获音频（语音）并使用听写将其存储为字符串。</span><span class="sxs-lookup"><span data-stu-id="2eb93-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="2eb93-425">暂停语音后，将听写提交到*LuisManager*类。</span><span class="sxs-lookup"><span data-stu-id="2eb93-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="2eb93-426">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2eb93-426">To create this class:</span></span> 

1.  <span data-ttu-id="2eb93-427">右键单击 "*项目" 面板*，**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="2eb93-428">调用文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-428">Call the folder **Scripts**.</span></span> 

    ![创建脚本文件夹。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="2eb93-430">创建**脚本**文件夹后，双击它以打开。</span><span class="sxs-lookup"><span data-stu-id="2eb93-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="2eb93-431">然后，在该文件夹中，右键单击，**创建 > C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="2eb93-432">将脚本命名为*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="2eb93-433">双击 " *MicrophoneManager* " 以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="2eb93-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="2eb93-434">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="2eb93-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="2eb93-435">然后在*MicrophoneManager*类中添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="2eb93-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="2eb93-436">现在需要添加*唤醒（）* 和*Start （）* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="2eb93-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="2eb93-437">当类初始化时，将调用以下内容：</span><span class="sxs-lookup"><span data-stu-id="2eb93-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="2eb93-438">现在，你需要应用程序用来启动和停止语音捕获，并将其传递给*LuisManager*类的方法。</span><span class="sxs-lookup"><span data-stu-id="2eb93-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="2eb93-439">添加语音暂停时要调用的*听写处理程序*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="2eb93-440">此方法会将听写文本传递给*LuisManager*类。</span><span class="sxs-lookup"><span data-stu-id="2eb93-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="2eb93-441">删除*Update （）* 方法，因为此类将不会使用它。</span><span class="sxs-lookup"><span data-stu-id="2eb93-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="2eb93-442">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2eb93-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2eb93-443">此时，你会注意到在*Unity 编辑器控制台面板*中出现错误。</span><span class="sxs-lookup"><span data-stu-id="2eb93-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="2eb93-444">这是因为代码引用了将在下一章中创建的*LuisManager*类。</span><span class="sxs-lookup"><span data-stu-id="2eb93-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="2eb93-445">第6章–创建 LUISManager 类</span><span class="sxs-lookup"><span data-stu-id="2eb93-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="2eb93-446">你可以创建*LuisManager*类，它将调用 Azure LUIS 服务。</span><span class="sxs-lookup"><span data-stu-id="2eb93-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="2eb93-447">此类的目的是接收来自*MicrophoneManager*类的听写文本，并将其发送到要分析的*Azure 语言理解 API* 。</span><span class="sxs-lookup"><span data-stu-id="2eb93-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="2eb93-448">此类将反序列化*JSON*响应并调用*行为*类的适当方法来触发操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="2eb93-449">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2eb93-449">To create this class:</span></span> 

1.  <span data-ttu-id="2eb93-450">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="2eb93-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2eb93-451">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2eb93-452">将脚本命名为*LuisManager*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="2eb93-453">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="2eb93-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="2eb93-454">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="2eb93-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="2eb93-455">首先，在*LuisManager* **类中创建三个类（** 在与*Start （）* 方法相同的脚本文件中），该文件将表示来自 Azure 的反序列化 JSON 响应。</span><span class="sxs-lookup"><span data-stu-id="2eb93-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="2eb93-456">接下来，在*LuisManager*类中添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="2eb93-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="2eb93-457">请确保现在将 LUIS 终结点置于（将从 LUIS 门户中获得）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="2eb93-458">现在需要添加*唤醒（）* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="2eb93-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="2eb93-459">当类初始化时，将调用此方法：</span><span class="sxs-lookup"><span data-stu-id="2eb93-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="2eb93-460">现在，你需要此应用程序用来将*MicrophoneManager*类收到的听写发送到*LUIS*的方法，然后接收并反序列化响应。</span><span class="sxs-lookup"><span data-stu-id="2eb93-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="2eb93-461">一旦确定了意向值和关联实体后，就会将这些值传递给*行为*类的实例，以触发预期的操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="2eb93-462">创建一个名为*AnalyseResponseElements （）* 的新方法，该方法将读取生成的*AnalysedQuery*并确定实体。</span><span class="sxs-lookup"><span data-stu-id="2eb93-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="2eb93-463">确定这些实体后，它们将被传递到要在操作中使用的*行为*类的实例。</span><span class="sxs-lookup"><span data-stu-id="2eb93-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognized intent, read the entities name
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
    > <span data-ttu-id="2eb93-464">删除*Start （）* 和*Update （）* 方法，因为此类将不会使用它们。</span><span class="sxs-lookup"><span data-stu-id="2eb93-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="2eb93-465">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2eb93-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="2eb93-466">此时，你会注意到在*Unity 编辑器控制台面板*中出现了几个错误。</span><span class="sxs-lookup"><span data-stu-id="2eb93-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="2eb93-467">这是因为代码引用了将在下一章中创建的*行为*类。</span><span class="sxs-lookup"><span data-stu-id="2eb93-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="2eb93-468">第7章–创建行为类</span><span class="sxs-lookup"><span data-stu-id="2eb93-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="2eb93-469">*行为*类将使用*LuisManager*类提供的实体触发操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="2eb93-470">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2eb93-470">To create this class:</span></span> 

1.  <span data-ttu-id="2eb93-471">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="2eb93-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2eb93-472">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2eb93-473">将脚本命名为*行为*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="2eb93-474">双击脚本以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="2eb93-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="2eb93-475">然后在*行为*类中添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="2eb93-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="2eb93-476">添加*唤醒（）* 方法代码。</span><span class="sxs-lookup"><span data-stu-id="2eb93-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="2eb93-477">当类初始化时，将调用此方法：</span><span class="sxs-lookup"><span data-stu-id="2eb93-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="2eb93-478">下面的方法由*LuisManager*类（先前创建）调用，以确定哪个对象是查询的目标，然后触发相应的操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="2eb93-479">添加*FindTarget （）* 方法，以确定哪一个*Gameobject*是当前意向的目标。</span><span class="sxs-lookup"><span data-stu-id="2eb93-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="2eb93-480">如果实体中未定义显式目标，则此方法默认为 "gazed" 的*GameObject* 。</span><span class="sxs-lookup"><span data-stu-id="2eb93-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
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
    > <span data-ttu-id="2eb93-481">删除*Start （）* 和*Update （）* 方法，因为此类将不会使用它们。</span><span class="sxs-lookup"><span data-stu-id="2eb93-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="2eb93-482">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2eb93-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="2eb93-483">第8章–创建注视类</span><span class="sxs-lookup"><span data-stu-id="2eb93-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="2eb93-484">完成此应用需要完成的最后一个类是 "*注视*类"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="2eb93-485">此类将对当前用户视觉对象集中的*GameObject*的引用进行更新。</span><span class="sxs-lookup"><span data-stu-id="2eb93-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="2eb93-486">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2eb93-486">To create this Class:</span></span> 

1.  <span data-ttu-id="2eb93-487">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="2eb93-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2eb93-488">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2eb93-489">将脚本命名为 "*注视*"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="2eb93-490">双击脚本以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="2eb93-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="2eb93-491">为此类插入以下代码：</span><span class="sxs-lookup"><span data-stu-id="2eb93-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="2eb93-492">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2eb93-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="2eb93-493">第9章-完成场景设置</span><span class="sxs-lookup"><span data-stu-id="2eb93-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="2eb93-494">若要完成场景的设置，请将已创建的每个脚本从 "脚本" 文件夹拖到 "*层次结构" 面板*中的 "**照相机**" 对象。</span><span class="sxs-lookup"><span data-stu-id="2eb93-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="2eb93-495">选择**主摄像机**，查看*检查器面板*，您应该能够看到已附加的每个脚本，您会注意到每个脚本上都有一些参数还需要设置。</span><span class="sxs-lookup"><span data-stu-id="2eb93-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![设置照相机引用目标。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="2eb93-497">若要正确设置这些参数，请遵循以下说明：</span><span class="sxs-lookup"><span data-stu-id="2eb93-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="2eb93-498">*MicrophoneManager*：</span><span class="sxs-lookup"><span data-stu-id="2eb93-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="2eb93-499">从 "*层次结构" 面板*中，将 "**听写文本**" 对象拖到 "**听写文本**参数值" 框中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="2eb93-500">*行为*，从 "*层次结构" 面板*：</span><span class="sxs-lookup"><span data-stu-id="2eb93-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="2eb93-501">将**球体**对象拖到 "*球*引用目标" 框中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="2eb93-502">将**圆柱体**拖到 "*圆柱形*引用目标" 框中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="2eb93-503">将**多维数据集**拖到 "*多维数据集*引用目标" 框中。</span><span class="sxs-lookup"><span data-stu-id="2eb93-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="2eb93-504">*注视*：</span><span class="sxs-lookup"><span data-stu-id="2eb93-504">*Gaze*:</span></span>

        - <span data-ttu-id="2eb93-505">将 "*注视最大距离*" 设置为**300** （如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="2eb93-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="2eb93-506">结果应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="2eb93-506">The result should look like the image below:</span></span>

    ![当前设置了照相机引用目标。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="2eb93-508">第10章–在 Unity 编辑器中测试</span><span class="sxs-lookup"><span data-stu-id="2eb93-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="2eb93-509">测试场景设置是否已正确实现。</span><span class="sxs-lookup"><span data-stu-id="2eb93-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="2eb93-510">请确保：</span><span class="sxs-lookup"><span data-stu-id="2eb93-510">Ensure that:</span></span>

-   <span data-ttu-id="2eb93-511">所有脚本都附加到**相机**对象上。</span><span class="sxs-lookup"><span data-stu-id="2eb93-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="2eb93-512">*主相机检查器面板*中的所有字段均已正确分配。</span><span class="sxs-lookup"><span data-stu-id="2eb93-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="2eb93-513">按下*Unity 编辑器*中的 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="2eb93-514">应用应在附加的沉浸式耳机中运行。</span><span class="sxs-lookup"><span data-stu-id="2eb93-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="2eb93-515">尝试一些最谈话，例如：</span><span class="sxs-lookup"><span data-stu-id="2eb93-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="2eb93-516">如果在 Unity 控制台中看到有关默认音频设备变化的错误，场景可能无法按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="2eb93-517">这是因为混合现实门户使用内置麦克风处理随附的耳机的方式。</span><span class="sxs-lookup"><span data-stu-id="2eb93-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="2eb93-518">如果看到此错误，只需停止场景并再次启动，应按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="2eb93-519">第11章–构建和旁加载 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="2eb93-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="2eb93-520">确保应用程序在 Unity 编辑器中运行后，便可以生成并部署了。</span><span class="sxs-lookup"><span data-stu-id="2eb93-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="2eb93-521">若要生成：</span><span class="sxs-lookup"><span data-stu-id="2eb93-521">To Build:</span></span>

1.  <span data-ttu-id="2eb93-522">单击 "**文件" > "保存**"，保存当前场景。</span><span class="sxs-lookup"><span data-stu-id="2eb93-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="2eb93-523">请参阅**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="2eb93-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="2eb93-524">勾选称为 " **Unity C#项目**" 的框（在创建 UWP 项目后，可用于查看和调试代码。</span><span class="sxs-lookup"><span data-stu-id="2eb93-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="2eb93-525">单击 "**添加打开的场景**"，然后单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    !["生成设置" 窗口](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="2eb93-527">系统将提示您选择要在其中生成解决方案的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2eb93-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="2eb93-528">创建一个*生成*文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。</span><span class="sxs-lookup"><span data-stu-id="2eb93-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="2eb93-529">单击 "**选择文件夹**"，在该位置开始生成。</span><span class="sxs-lookup"><span data-stu-id="2eb93-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="2eb93-530">![创建生成文件夹](images/AzureLabs-Lab3-44.png)
    ![选择生成文件夹](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="2eb93-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="2eb93-531">Unity 完成生成后（可能需要一些时间），应在生成的位置打开**文件资源管理器**窗口。</span><span class="sxs-lookup"><span data-stu-id="2eb93-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="2eb93-532">在本地计算机上部署：</span><span class="sxs-lookup"><span data-stu-id="2eb93-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="2eb93-533">在*Visual Studio*中，打开已在[上一章](#chapter-10--test-in-the-unity-editor)中创建的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="2eb93-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="2eb93-534">在**解决方案平台**中，选择 " **X86**，**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="2eb93-535">在**解决方案配置**中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="2eb93-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="2eb93-536">对于 Microsoft HoloLens，你可能会发现将其设置为*远程计算机*会更容易，因此你不会受限到计算机上。</span><span class="sxs-lookup"><span data-stu-id="2eb93-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="2eb93-537">不过，还需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2eb93-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="2eb93-538">知道您的 HoloLens 的**IP 地址**，可在 "*设置" > 网络 & Internet > > "高级选项*" 中找到;IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="2eb93-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="2eb93-539">确保**开发人员模式**已**打开**;在 "设置" 中找到 *> 更新开发人员 & 安全 >* 。</span><span class="sxs-lookup"><span data-stu-id="2eb93-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![部署应用](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="2eb93-541">请在 "**生成" 菜单**中，单击 "**部署解决方案**"，将应用程序旁加载到计算机上。</span><span class="sxs-lookup"><span data-stu-id="2eb93-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="2eb93-542">应用现在应显示在已安装的应用列表中，可以启动了！</span><span class="sxs-lookup"><span data-stu-id="2eb93-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="2eb93-543">启动后，应用会提示你授权访问_麦克风_。</span><span class="sxs-lookup"><span data-stu-id="2eb93-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="2eb93-544">使用*运动控制器*、*语音输入*或*键盘*按 **"是"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="2eb93-545">第12章-改进 LUIS 服务</span><span class="sxs-lookup"><span data-stu-id="2eb93-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="2eb93-546">本章非常重要，可能需要多次迭代，因为这将有助于提高 LUIS 服务的准确性：请确保完成此操作。</span><span class="sxs-lookup"><span data-stu-id="2eb93-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="2eb93-547">若要改进 LUIS 提供的理解级别，需要捕获新的最谈话，并使用它们重新训练 LUIS 应用。</span><span class="sxs-lookup"><span data-stu-id="2eb93-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="2eb93-548">例如，你可能已经训练了 LUIS 来理解 "增加" 和 "升迁"，但又不希望你的应用程序也知道 "放大" 等词呢？</span><span class="sxs-lookup"><span data-stu-id="2eb93-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="2eb93-549">一旦你使用了应用程序几次，你所说的一切将被 LUIS 收集，并在 LUIS 门户中可用。</span><span class="sxs-lookup"><span data-stu-id="2eb93-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="2eb93-550">请按照以下[链接](https://www.luis.ai/home)打开门户应用程序，并登录。</span><span class="sxs-lookup"><span data-stu-id="2eb93-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="2eb93-551">用 MS 凭据登录后，单击你的*应用名称*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="2eb93-552">单击页面左侧的 "**查看终结点最谈话**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2eb93-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![查看最谈话](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="2eb93-554">将显示一个列表，其中包含已由混合现实应用程序发送到 LUIS 的最谈话。</span><span class="sxs-lookup"><span data-stu-id="2eb93-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![最谈话列表](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="2eb93-556">你会注意到一些突出显示的*实体*。</span><span class="sxs-lookup"><span data-stu-id="2eb93-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="2eb93-557">通过将鼠标悬停在每个突出显示的单词上，你可以查看每个查询文本并确定哪些实体已正确识别，哪些实体出现错误以及哪些实体丢失。</span><span class="sxs-lookup"><span data-stu-id="2eb93-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="2eb93-558">在上面的示例中，发现 "鱼叉式" 一词已突出显示为目标，因此需要更正此错误，这是通过将鼠标悬停在单词上并单击 "**删除标签**" 来完成的。</span><span class="sxs-lookup"><span data-stu-id="2eb93-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="2eb93-559">![检查最谈话](images/AzureLabs-Lab3-49.png)
![删除标签图像](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="2eb93-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="2eb93-560">如果找到完全错误的最谈话，可以使用屏幕右侧的 "**删除**" 按钮删除它们。</span><span class="sxs-lookup"><span data-stu-id="2eb93-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![删除错误的最谈话](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="2eb93-562">或者，如果您认为 LUIS 已正确解释查询文本，则可以使用 "**添加到对齐意向**" 按钮来验证其理解。</span><span class="sxs-lookup"><span data-stu-id="2eb93-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![添加到对齐意向](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="2eb93-564">对所有显示的最谈话进行排序后，请尝试重新加载页面，查看是否有更多的可用功能。</span><span class="sxs-lookup"><span data-stu-id="2eb93-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="2eb93-565">尽可能多地重复此过程以提高应用程序理解。</span><span class="sxs-lookup"><span data-stu-id="2eb93-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="2eb93-566">**玩得愉快！**</span><span class="sxs-lookup"><span data-stu-id="2eb93-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="2eb93-567">已完成的 LUIS 集成应用程序</span><span class="sxs-lookup"><span data-stu-id="2eb93-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="2eb93-568">恭喜，你构建了一个使用 Azure 语言理解智能服务的混合现实应用，以了解用户所说的内容，并对该信息采取措施。</span><span class="sxs-lookup"><span data-stu-id="2eb93-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![实验室结果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2eb93-570">额外练习</span><span class="sxs-lookup"><span data-stu-id="2eb93-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="2eb93-571">练习1</span><span class="sxs-lookup"><span data-stu-id="2eb93-571">Exercise 1</span></span>

<span data-ttu-id="2eb93-572">使用此应用程序时，您可能会注意到，如果注视地面对象并要求更改其颜色，则会这样做。</span><span class="sxs-lookup"><span data-stu-id="2eb93-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="2eb93-573">您可以如何阻止您的应用程序更改地面颜色？</span><span class="sxs-lookup"><span data-stu-id="2eb93-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="2eb93-574">练习2</span><span class="sxs-lookup"><span data-stu-id="2eb93-574">Exercise 2</span></span>

<span data-ttu-id="2eb93-575">尝试扩展 LUIS 和应用功能，为场景中的对象添加其他功能;例如，在注视点处创建新的对象，具体取决于用户所显示的内容，然后可以将这些对象和当前场景对象与现有的命令一起使用。</span><span class="sxs-lookup"><span data-stu-id="2eb93-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
