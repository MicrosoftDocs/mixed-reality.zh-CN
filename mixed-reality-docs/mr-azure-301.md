---
title: MR 和 Azure 301-语言翻译
description: 完成此课程以了解如何实现 Azure 文本翻译 API 混合的现实应用程序中。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 文本翻译，沉浸式、 hololens、 vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592739"
---
>[!NOTE]
><span data-ttu-id="2dbe7-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2dbe7-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2dbe7-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2dbe7-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2dbe7-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2dbe7-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="2dbe7-110">MR 和 Azure 301:语言翻译</span><span class="sxs-lookup"><span data-stu-id="2dbe7-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="2dbe7-111">在本课程中，您将学习如何将翻译功能添加到文本翻译 api 使用 Azure 认知服务的混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![最终产品](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="2dbe7-113">文本翻译 API 是翻译服务最后一种接近实时的速度。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="2dbe7-114">该服务是基于云的并使用 REST API 调用，可以使应用程序使用的神经网络机器翻译技术翻译为其他语言的文本。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="2dbe7-115">有关详细信息，请访问[Azure 文本翻译 API 页](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="2dbe7-116">完成本课程时，之后您将拥有一个混合的现实应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="2dbe7-117">用户将连接到沉浸式的 (VR) 耳机式麦克风 （或 HoloLens 内置麦克风） 进行朗读。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="2dbe7-118">应用程序将捕获听写，并将其发送到 Azure 文本翻译 API。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="2dbe7-119">翻译结果将显示在 Unity 场景中的简单用户界面组。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="2dbe7-120">本课程将介绍如何将结果从 Translator 服务到基于 Unity 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="2dbe7-121">它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="2dbe7-122">设备支持</span><span class="sxs-lookup"><span data-stu-id="2dbe7-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2dbe7-123">课程</span><span class="sxs-lookup"><span data-stu-id="2dbe7-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2dbe7-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2dbe7-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2dbe7-125"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="2dbe7-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2dbe7-126">MR 和 Azure 301:语言翻译</span><span class="sxs-lookup"><span data-stu-id="2dbe7-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="2dbe7-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2dbe7-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2dbe7-128">✔️</span><span class="sxs-lookup"><span data-stu-id="2dbe7-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2dbe7-129">尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="2dbe7-130">按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="2dbe7-131">使用 HoloLens，您可能注意到某些 echo 语音捕获过程。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2dbe7-132">系统必备</span><span class="sxs-lookup"><span data-stu-id="2dbe7-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2dbe7-133">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2dbe7-134">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="2dbe7-135">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="2dbe7-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="2dbe7-136">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2dbe7-137">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="2dbe7-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2dbe7-138">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="2dbe7-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2dbe7-139">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="2dbe7-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2dbe7-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="2dbe7-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2dbe7-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2dbe7-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="2dbe7-142">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="2dbe7-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="2dbe7-143">一组的耳机使用内置的麦克风 （如果耳机没有内置的麦克风和扬声器）</span><span class="sxs-lookup"><span data-stu-id="2dbe7-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="2dbe7-144">用于 Azure 的安装程序和转换检索 Internet 访问权限</span><span class="sxs-lookup"><span data-stu-id="2dbe7-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2dbe7-145">开始之前</span><span class="sxs-lookup"><span data-stu-id="2dbe7-145">Before you start</span></span>

- <span data-ttu-id="2dbe7-146">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="2dbe7-147">在本教程中的代码将允许您记录从默认麦克风设备连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="2dbe7-148">请确保默认麦克风设备设置为你打算使用捕获您的声音的设备。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="2dbe7-149">若要允许您的 PC 以启用听写，请转到**设置 > 隐私 > 语音，墨迹书写和键入**，然后选择按钮**启用语音服务和键入建议**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="2dbe7-150">如果您使用的麦克风和耳机连接到 （或内置于） 将耳机，请确保选择"当我 wear 我耳机时，切换到耳机式麦克风"中打开**设置 > 混合现实 > 音频和语音**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![混合的现实设置](images/AzureLabs-Lab1-00-5.png)

   ![麦克风设置](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="2dbe7-153">请注意，如果你正在开发为此实验室的沉浸式头戴式耳机，可能会遇到音频输出设备问题。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="2dbe7-154">这是 unity 的因为 Unity，在更高版本 (Unity 2018.2) 中已修复的问题。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="2dbe7-155">此问题可防止 Unity 在运行时更改默认音频输出设备。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="2dbe7-156">来解决，确保您已完成上述步骤，和关闭并重新打开编辑器中，当此问题提供本身。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="2dbe7-157">第 1 章 – Azure 门户</span><span class="sxs-lookup"><span data-stu-id="2dbe7-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="2dbe7-158">若要使用 Azure 翻译 API，你需要配置要成为可用于应用程序的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="2dbe7-159">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2dbe7-160">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2dbe7-161">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2dbe7-162">你登录后，单击**新建**右上左角并搜索"文本翻译 API。"</span><span class="sxs-lookup"><span data-stu-id="2dbe7-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="2dbe7-163">选择**输入**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-163">Select **Enter**.</span></span>

    ![新的资源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="2dbe7-165">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="2dbe7-166">该新页面将提供的说明*文本翻译 API*服务。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="2dbe7-167">在左下角此页上，选择**创建**按钮，以创建与此关联服务。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Translator 文本 API 服务创建](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="2dbe7-169">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="2dbe7-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="2dbe7-170">插入所需**名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="2dbe7-171">选择相应**订阅**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="2dbe7-172">选择**定价层**适合您，如果这是第一个时间来创建*Translator 文本服务*，应可供你免费层 （名为 F0）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="2dbe7-173">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="2dbe7-174">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2dbe7-175">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些实验室））。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="2dbe7-176">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="2dbe7-177">确定**位置**为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2dbe7-178">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2dbe7-179">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="2dbe7-180">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="2dbe7-181">选择“创建”  。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-181">Select **Create**.</span></span>

        ![选择创建按钮。](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="2dbe7-183">一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="2dbe7-184">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure 服务创建通知](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="2dbe7-186">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-186">Click on the notification to explore your new Service instance.</span></span> 

    ![请转到资源弹出窗口。](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="2dbe7-188">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="2dbe7-189">你将转到新的翻译文本 API 服务实例。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator 文本 API 服务页](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="2dbe7-191">在本教程中，你的应用程序将需要对你的服务，通过使用服务的订阅密钥来完成进行调用。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="2dbe7-192">从*快速入门*页你*文本翻译*服务中，导航到的第一步*捕捉密钥*，然后单击**密钥**（也可以此外实现此目的通过单击蓝色超链接密钥，位于服务导航菜单中，由密钥图标表示）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="2dbe7-193">此时会显示你的服务*密钥*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="2dbe7-194">需要一份某个显示的密钥，因为你将需要此更高版本中您的项目。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="2dbe7-195">第 2 章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="2dbe7-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="2dbe7-196">设置和测试您的混合的现实沉浸式头戴式。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="2dbe7-197">不需要此课程运动控制器。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="2dbe7-198">如果需要支持沉浸式头戴式设置，请[请按照下列步骤](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="2dbe7-199">以下是一组典型使用混合现实进行开发，在这种情况下，是很好的其他项目模板：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="2dbe7-200">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-200">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="2dbe7-202">现在，需要提供 Unity 项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="2dbe7-203">插入**MR_Translation**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="2dbe7-204">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="2dbe7-205">设置*位置*到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2dbe7-206">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-206">Then, click **Create project**.</span></span>

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="2dbe7-208">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="2dbe7-209">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2dbe7-210">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2dbe7-211">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-211">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="2dbe7-213">接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="2dbe7-215">转到**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="2dbe7-216">**设备为目标**设置为**任一设备**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="2dbe7-217">对于 Microsoft HoloLens**目标设备**到*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="2dbe7-218">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="2dbe7-219">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="2dbe7-220">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="2dbe7-221">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="2dbe7-222">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="2dbe7-223">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="2dbe7-224">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-224">A save window will appear.</span></span>

            ![单击添加打开场景按钮](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="2dbe7-226">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="2dbe7-228">打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_TranslationScene**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![为新的场景提供一个名称。](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="2dbe7-230">请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="2dbe7-231">创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="2dbe7-232">中的剩余设置，*生成设置*，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="2dbe7-233">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放器设置。](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="2dbe7-235">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="2dbe7-236">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="2dbe7-237">**脚本运行时版本**应**稳定**（.NET 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="2dbe7-238">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="2dbe7-239">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="2dbe7-241">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="2dbe7-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-242">**InternetClient**</span></span>
        2. <span data-ttu-id="2dbe7-243">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-243">**Microphone**</span></span>

            ![正在更新的发布设置。](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="2dbe7-245">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新的 X R 设置。](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="2dbe7-247">回到**生成设置**， *UnityC#项目*不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="2dbe7-248">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="2dbe7-249">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="2dbe7-250">第 3 章 – 主照相机设置</span><span class="sxs-lookup"><span data-stu-id="2dbe7-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2dbe7-251">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，将其导入项目中，作为[ *自定义包*](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5--create-the-results-class)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="2dbe7-252">仍需要创建一个 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="2dbe7-253">在中*层次结构面板*，您会发现一个名为对象**Main Camera**，"内部"应用程序后，此对象表示"head"的观点。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="2dbe7-254">准备好 Unity 仪表板中，选择**主相机 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="2dbe7-255">您会注意*检查器面板*（通常右侧，在仪表板中找到） 将显示的各种组件*GameObject*，与*转换*在顶部后, 接*照相机*，而另一些其他组件。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="2dbe7-256">你将需要重置的转换的 Main Camera，使其正确定位。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="2dbe7-257">若要执行此操作，请选择**齿轮**旁的摄像机*转换*组件，并选择**重置**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![重置 Main Camera 转换。](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="2dbe7-259">*转换*组件应如下所示：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="2dbe7-260">*位置*设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="2dbe7-261">*旋转*设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="2dbe7-262">并*规模*设置为**1，1，1**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![转换用于相机的信息](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="2dbe7-264">接下来，使用**Main Camera**对象选择，请参阅**添加组件**按钮位于最底部*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="2dbe7-265">选择该按钮，然后搜索 (通过键入*音频源*到搜索字段或导航部分) 调用组件**音频源**，如下所示，然后选择它 (按 enter 在其上也可）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="2dbe7-266">*音频源*组件将添加到**Main Camera**如下所示。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![添加将音频源组件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="2dbe7-268">对于 Microsoft HoloLens，您将需要还可以更改以下内容，这属于**照相机**组件上你**Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="2dbe7-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="2dbe7-269">**清除标志：** 纯色。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="2dbe7-270">**背景**黑色、 Alpha 0 – 十六进制颜色: #00000000。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="2dbe7-271">第 4 章-安装程序调试画布</span><span class="sxs-lookup"><span data-stu-id="2dbe7-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="2dbe7-272">若要显示的输入和输出的转换，需要创建一个基本 UI。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="2dbe7-273">对于本课程中，将使用多个文本对象，若要显示的数据创建画布 UI 对象。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="2dbe7-274">在空白区域中单击右键*层次结构面板*下**UI**，将添加**画布**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![添加新的画布 UI 对象。](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="2dbe7-276">与画布对象后，在*检查器面板*（在画布组件），更改**呈现模式**到**世界空间**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="2dbe7-277">接下来，更改中的以下参数*检查器面板的 Rect 转换*:</span><span class="sxs-lookup"><span data-stu-id="2dbe7-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="2dbe7-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="2dbe7-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="2dbe7-279">*Width* -    500</span><span class="sxs-lookup"><span data-stu-id="2dbe7-279">*Width* -    500</span></span>
    3. <span data-ttu-id="2dbe7-280">*Height* -   300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-280">*Height* -   300</span></span>
    4. <span data-ttu-id="2dbe7-281">*规模* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="2dbe7-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![更新画布的 rect 转换。](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="2dbe7-283">右键单击**画布**中*层次结构面板*下**UI**，并添加**面板**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="2dbe7-284">这**面板**将提供到您将在场景中显示的文本的背景。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="2dbe7-285">右键单击**面板**中*层次结构面板*下**UI**，并添加**文本对象**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="2dbe7-286">重复相同的过程，直到总共创建了四个 UI 文本对象 (提示： 如果具有所选的第一个文本对象，可以只需按**Ctrl + 有**、 对其进行复制，将有四个总之前)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="2dbe7-287">每个**文本对象**，选择它，使用下表设置参数*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="2dbe7-288">有关*Rect 转换*组件：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="2dbe7-289">名称</span><span class="sxs-lookup"><span data-stu-id="2dbe7-289">Name</span></span>                   | <span data-ttu-id="2dbe7-290">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="2dbe7-290">Transform - *Position*</span></span>             | <span data-ttu-id="2dbe7-291">宽度</span><span class="sxs-lookup"><span data-stu-id="2dbe7-291">Width</span></span>      | <span data-ttu-id="2dbe7-292">Height</span><span class="sxs-lookup"><span data-stu-id="2dbe7-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="2dbe7-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="2dbe7-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="2dbe7-295">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-295">300</span></span>        | <span data-ttu-id="2dbe7-296">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-296">30</span></span>        |
        | <span data-ttu-id="2dbe7-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-297">AzureResponseLabel</span></span>     | <span data-ttu-id="2dbe7-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="2dbe7-299">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-299">300</span></span>        | <span data-ttu-id="2dbe7-300">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-300">30</span></span>        |
        | <span data-ttu-id="2dbe7-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-301">DictationLabel</span></span>         | <span data-ttu-id="2dbe7-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="2dbe7-303">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-303">300</span></span>        | <span data-ttu-id="2dbe7-304">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-304">30</span></span>        |
        | <span data-ttu-id="2dbe7-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-305">TranslationResultLabel</span></span> | <span data-ttu-id="2dbe7-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="2dbe7-307">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-307">300</span></span>        | <span data-ttu-id="2dbe7-308">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-308">30</span></span>        |


    2. <span data-ttu-id="2dbe7-309">有关**文本 （脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="2dbe7-310">名称</span><span class="sxs-lookup"><span data-stu-id="2dbe7-310">Name</span></span>                   | <span data-ttu-id="2dbe7-311">Text</span><span class="sxs-lookup"><span data-stu-id="2dbe7-311">Text</span></span>               | <span data-ttu-id="2dbe7-312">字号</span><span class="sxs-lookup"><span data-stu-id="2dbe7-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="2dbe7-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="2dbe7-314">麦克风状态：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-314">Microphone Status:</span></span> | <span data-ttu-id="2dbe7-315">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-315">20</span></span>           |
        | <span data-ttu-id="2dbe7-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-316">AzureResponseLabel</span></span>     | <span data-ttu-id="2dbe7-317">Azure Web 响应</span><span class="sxs-lookup"><span data-stu-id="2dbe7-317">Azure Web Response</span></span> | <span data-ttu-id="2dbe7-318">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-318">20</span></span>           |
        | <span data-ttu-id="2dbe7-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-319">DictationLabel</span></span>         |   <span data-ttu-id="2dbe7-320">您刚才在说：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-320">You just said:</span></span>   | <span data-ttu-id="2dbe7-321">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-321">20</span></span>           |
        | <span data-ttu-id="2dbe7-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="2dbe7-322">TranslationResultLabel</span></span> |    <span data-ttu-id="2dbe7-323">转换：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-323">Translation:</span></span>    | <span data-ttu-id="2dbe7-324">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-324">20</span></span>           |

        ![输入用户界面标签的相应值。](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="2dbe7-326">此外，请字体样式**加粗**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="2dbe7-327">这将使文本易于阅读。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-327">This will make the text easier to read.</span></span>

        ![粗体的字体。](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="2dbe7-329">每个*UI 文本对象*中创建[第 5 章](#chapter-5--create-the-results-class)，创建一个新*子* **UI 文本对象**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="2dbe7-330">这些子对象将显示应用程序的输出。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-330">These children will display the output of the application.</span></span> <span data-ttu-id="2dbe7-331">创建*子*通过右键单击目标的父对象 (例如*MicrophoneStatusLabel*)，然后选择**UI** ，然后选择**文本**.</span><span class="sxs-lookup"><span data-stu-id="2dbe7-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="2dbe7-332">对于每个这些子对象，选择它，并使用下表来检查器面板中设置参数。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="2dbe7-333">有关**Rect 转换**组件：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="2dbe7-334">名称</span><span class="sxs-lookup"><span data-stu-id="2dbe7-334">Name</span></span>                  | <span data-ttu-id="2dbe7-335">转换的*位置*</span><span class="sxs-lookup"><span data-stu-id="2dbe7-335">Transform - *Position*</span></span> | <span data-ttu-id="2dbe7-336">宽度</span><span class="sxs-lookup"><span data-stu-id="2dbe7-336">Width</span></span>      | <span data-ttu-id="2dbe7-337">Height</span><span class="sxs-lookup"><span data-stu-id="2dbe7-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="2dbe7-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="2dbe7-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="2dbe7-340">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-340">300</span></span>        | <span data-ttu-id="2dbe7-341">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-341">30</span></span>        |
        | <span data-ttu-id="2dbe7-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-342">AzureResponseText</span></span>     | <span data-ttu-id="2dbe7-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="2dbe7-344">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-344">300</span></span>        | <span data-ttu-id="2dbe7-345">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-345">30</span></span>        |
        | <span data-ttu-id="2dbe7-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-346">DictationText</span></span>         | <span data-ttu-id="2dbe7-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="2dbe7-348">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-348">300</span></span>        | <span data-ttu-id="2dbe7-349">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-349">30</span></span>        |
        | <span data-ttu-id="2dbe7-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-350">TranslationResultText</span></span> | <span data-ttu-id="2dbe7-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="2dbe7-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="2dbe7-352">300</span><span class="sxs-lookup"><span data-stu-id="2dbe7-352">300</span></span>        | <span data-ttu-id="2dbe7-353">30</span><span class="sxs-lookup"><span data-stu-id="2dbe7-353">30</span></span>        |

    2. <span data-ttu-id="2dbe7-354">有关**文本 （脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="2dbe7-355">名称</span><span class="sxs-lookup"><span data-stu-id="2dbe7-355">Name</span></span>                  | <span data-ttu-id="2dbe7-356">Text</span><span class="sxs-lookup"><span data-stu-id="2dbe7-356">Text</span></span>          | <span data-ttu-id="2dbe7-357">字号</span><span class="sxs-lookup"><span data-stu-id="2dbe7-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="2dbe7-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="2dbe7-359">??</span><span class="sxs-lookup"><span data-stu-id="2dbe7-359">??</span></span>       | <span data-ttu-id="2dbe7-360">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-360">20</span></span>           |
        | <span data-ttu-id="2dbe7-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-361">AzureResponseText</span></span>     |      <span data-ttu-id="2dbe7-362">??</span><span class="sxs-lookup"><span data-stu-id="2dbe7-362">??</span></span>       | <span data-ttu-id="2dbe7-363">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-363">20</span></span>           |
        | <span data-ttu-id="2dbe7-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-364">DictationText</span></span>         |      <span data-ttu-id="2dbe7-365">??</span><span class="sxs-lookup"><span data-stu-id="2dbe7-365">??</span></span>       | <span data-ttu-id="2dbe7-366">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-366">20</span></span>           |
        | <span data-ttu-id="2dbe7-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="2dbe7-367">TranslationResultText</span></span> |      <span data-ttu-id="2dbe7-368">??</span><span class="sxs-lookup"><span data-stu-id="2dbe7-368">??</span></span>       | <span data-ttu-id="2dbe7-369">20</span><span class="sxs-lookup"><span data-stu-id="2dbe7-369">20</span></span>           |

9. <span data-ttu-id="2dbe7-370">接下来，选择每个文本组件的中心对齐选项：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![对齐文本。](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="2dbe7-372">若要确保**子 UI 文本**对象是易于阅读、 更改其*颜色*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="2dbe7-373">执行此操作通过在栏上单击到 （当前黑色） 的下一步*颜色*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![输入相应的 UI 文本输出的值。](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="2dbe7-375">然后，在新，少*颜色*窗口中，更改*十六进制颜色*到：**0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![更新颜色为蓝色。](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="2dbe7-377">下面是如何**UI**应所示。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="2dbe7-378">在中*层次结构面板*:</span><span class="sxs-lookup"><span data-stu-id="2dbe7-378">In the *Hierarchy Panel*:</span></span>

        ![提供的结构中具有层次结构。](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="2dbe7-380">在中*场景*并*游戏视图*:</span><span class="sxs-lookup"><span data-stu-id="2dbe7-380">In the *Scene* and *Game Views*:</span></span>

        ![具有同一结构中的场景和游戏视图。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="2dbe7-382">第 5 章-创建结果类</span><span class="sxs-lookup"><span data-stu-id="2dbe7-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="2dbe7-383">您需要创建的第一个脚本是*结果*类，该类负责提供一种方法，以查看转换的结果。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="2dbe7-384">类存储并显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="2dbe7-385">从 Azure 响应结果。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-385">The response result from Azure.</span></span>
- <span data-ttu-id="2dbe7-386">麦克风状态。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-386">The microphone status.</span></span> 
- <span data-ttu-id="2dbe7-387">听写 （语音到文本） 的结果。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="2dbe7-388">转换的结果。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-388">The result of the translation.</span></span>

<span data-ttu-id="2dbe7-389">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-389">To create this class:</span></span> 

1.  <span data-ttu-id="2dbe7-390">在中右击*项目面板*，然后**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="2dbe7-391">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-391">Name the folder **Scripts**.</span></span> 
 
    ![创建脚本的文件夹。](images/AzureLabs-Lab1-31.png)

    ![打开脚本文件夹。](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="2dbe7-394">与**脚本**文件夹中创建，双击它打开。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="2dbe7-395">然后在该文件夹，右键单击，并选择**创建 >** 然后**C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="2dbe7-396">脚本命名为*结果*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-396">Name the script *Results*.</span></span> 

    ![创建第一个脚本。](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="2dbe7-398">双击新*结果*脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="2dbe7-399">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="2dbe7-400">在类中插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="2dbe7-401">然后添加*Awake()* 类初始化时将调用的方法。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="2dbe7-402">最后，添加方法负责将输出到 UI 的各种结果信息。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="2dbe7-403">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="2dbe7-404">第 6 章-创建*MicrophoneManager*类</span><span class="sxs-lookup"><span data-stu-id="2dbe7-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="2dbe7-405">要创建的第二个类是*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="2dbe7-406">此类负责：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-406">This class is responsible for:</span></span>

- <span data-ttu-id="2dbe7-407">正在检测录制设备附加到的耳机或计算机 （无论是默认值）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="2dbe7-408">捕获音频 （语音），并使用听写将其存储为字符串。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="2dbe7-409">一旦语音已暂停，提交到转换器类听写。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="2dbe7-410">主机可以停止语音捕获所需的方法。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="2dbe7-411">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-411">To create this class:</span></span> 
1.  <span data-ttu-id="2dbe7-412">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2dbe7-413">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2dbe7-414">脚本命名为*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="2dbe7-415">双击要使用 Visual Studio 中打开的新脚本。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="2dbe7-416">更新命名空间，如下所示，在顶部相同*MicrophoneManager*类：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="2dbe7-417">然后，添加以下变量内的*MicrophoneManager*类：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="2dbe7-418">为代码*Awake()* 并*start （)* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="2dbe7-419">类初始化时将会调用：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="2dbe7-420">你可以*删除* *update （)* 方法因为此类不会使用它。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="2dbe7-421">现在，你需要应用用于启动和停止语音捕获，并将其传递给方法*转换器*类，您很快就会生成。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="2dbe7-422">将以下代码复制并粘贴下方*start （)* 方法。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="2dbe7-423">尽管此应用程序不会使用它， *StopCapturingAudio()* 方法还提供了在这里，你应该实现停止捕获你的应用程序中的音频的功能。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="2dbe7-424">现在需要添加语音停止时，将调用一个听写处理程序。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="2dbe7-425">然后，此方法将传递到听写的文本*转换器*类。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="2dbe7-426">请确保在返回到 Unity 之前的 Visual Studio 中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="2dbe7-427">此时你会注意到出现在错误*Unity 编辑器控制台*面板 ("name 转换器不存在...")。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="2dbe7-428">这是因为该代码引用*转换器*类，该类将在下一章中创建。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="2dbe7-429">第 7 章 – 对 Azure 和转换器的服务调用</span><span class="sxs-lookup"><span data-stu-id="2dbe7-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="2dbe7-430">若要创建所需的最后一个脚本是*转换器*类。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="2dbe7-431">此类负责：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-431">This class is responsible for:</span></span>

-   <span data-ttu-id="2dbe7-432">进行身份验证应用程序与*Azure*，对于 exchange**身份验证令牌**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="2dbe7-433">使用**身份验证令牌**提交的文本 (从收到*MicrophoneManager*类) 以进行转换。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="2dbe7-434">接收已转换的结果并将其传递给*结果*类要在 UI 中进行可视化处理。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="2dbe7-435">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-435">To create this Class:</span></span> 
1.  <span data-ttu-id="2dbe7-436">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="2dbe7-437">在中右击**项目面板**，**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="2dbe7-438">调用脚本*转换器*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="2dbe7-439">双击新*转换器*脚本以将其打开**使用 Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="2dbe7-440">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="2dbe7-441">然后添加以下变量内的*转换器*类：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="2dbe7-442">插入到语言的语言**枚举**只是示例。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="2dbe7-443">可随意添加更多，如果您想;[API 支持 60 多个语言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)（包括克林贡语） ！</span><span class="sxs-lookup"><span data-stu-id="2dbe7-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="2dbe7-444">没有[交互性更强的页覆盖可用语言](https://www.microsoft.com/translator/business/languages/)，不过请注意页面才会显示工作时的站点语言设置为 en-（和将可能重定向到您的母语的 Microsoft 网站）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="2dbe7-445">你可以在底部的页或通过更改 URL 的网站语言。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="2dbe7-446">**AuthorizationKey**值，在上面的代码片段中，必须**密钥**收到你在订阅时*Azure 文本翻译 API*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="2dbe7-447">中已包含此[第 1 章](#chapter-1--the-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="2dbe7-448">为代码*Awake()* 并*start （)* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="2dbe7-449">在这种情况下，代码将调用*Azure*使用授权密钥，以获取*令牌*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="2dbe7-450">该令牌将在 10 分钟后过期。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="2dbe7-451">根据您的应用程序的方案，可能需要进行多次调用相同协同例程。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="2dbe7-452">以下是协同程序获取令牌：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="2dbe7-453">如果编辑 IEnumerator 方法的名称**GetTokenCoroutine()** ，则需要更新*StartCoroutine*并*StopCoroutine*调用上述代码中的字符串值。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="2dbe7-454">[Unity 文档根据](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，以停止特定*协同程序*，您需要使用的字符串值方法。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="2dbe7-455">接下来，添加 （与它正下方的"支持"流方法） 协同例程来获取接收的文本的翻译*MicrophoneManager*类。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="2dbe7-456">此代码将创建一个查询字符串来将发送到*Azure 文本翻译 API*，然后使用内部的 Unity UnityWebRequest 类将调用 Get 具有查询字符串的终结点。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="2dbe7-457">然后使用结果将转换结果对象中。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="2dbe7-458">下面的代码演示实现过程：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="2dbe7-459">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="2dbe7-460">章 8 – 配置 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="2dbe7-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="2dbe7-461">返回在 Unity 编辑器中，单击并拖动 *结果* 类 *从* **脚本** 文件夹 **Main Camera** 中对象 *层次结构面板* 。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="2dbe7-462">单击**Main Camera**并查看*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="2dbe7-463">您将在新添加发现*脚本*组件，有四个字段的值为空。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="2dbe7-464">这些是对在代码中的属性的输出引用。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="2dbe7-465">拖动相应**文本**中的对象*层次结构面板*到四个槽，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![使用指定的值更新目标的引用。](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="2dbe7-467">接下来，单击并拖动*转换器*类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="2dbe7-468">然后，单击并拖动*MicrophoneManager*类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="2dbe7-469">最后，单击**Main Camera**并查看*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="2dbe7-470">您将注意到在拖动的脚本中，有两个下拉列表框，您可以设置的语言。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![请确保输入预期的翻译语言。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="2dbe7-472">第 9 章 – 混合现实中的测试</span><span class="sxs-lookup"><span data-stu-id="2dbe7-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="2dbe7-473">此时您需要测试已正确地实现场景。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="2dbe7-474">请确保：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-474">Ensure that:</span></span>

- <span data-ttu-id="2dbe7-475">中所述的所有设置[第 1 章](#chapter-1--the-azure-portal)正确设置。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="2dbe7-476">*结果*，*转换器*，并*MicrophoneManager*，脚本附加到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="2dbe7-477">已放置你*Azure 文本翻译 API*服务**密钥**内**authorizationKey**变量内*转换器*脚本。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="2dbe7-478">中的所有字段*主相机检查器面板*正确分配。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="2dbe7-479">您的麦克风正在运行您的场景时 (如果没有，请检查是否附加的麦克风*默认*设备，并且您具有[它正确设置了在 Windows 内](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="2dbe7-480">可以通过按测试沉浸式头戴式**播放**按钮*Unity 编辑器*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="2dbe7-481">应用程序应通过附加的沉浸式头戴式正常运行。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="2dbe7-482">如果看到有关更改默认音频设备 Unity 控制台中的错误，场景可能无法按预期方式。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="2dbe7-483">这是由于混合的现实门户内置麦克风耳机具有它们的处理的方式。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="2dbe7-484">如果看到此错误，只需停止场景并重新启动它，并且应该可以正常为预期。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="2dbe7-485">章第 10-构建 UWP 解决方案和本地计算机上旁加载</span><span class="sxs-lookup"><span data-stu-id="2dbe7-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="2dbe7-486">此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="2dbe7-487">导航到**生成设置**:**文件 > 生成设置...**</span><span class="sxs-lookup"><span data-stu-id="2dbe7-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="2dbe7-488">从**生成设置**窗口中，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-488">From the **Build Settings** window, click **Build**.</span></span>

    ![生成 Unity 场景。](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="2dbe7-490">如果尚不存在，则勾选**UnityC#项目**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="2dbe7-491">单击“生成”  。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-491">Click **Build**.</span></span> <span data-ttu-id="2dbe7-492">将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="2dbe7-493">现在，创建该文件夹并将其命名*应用*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="2dbe7-494">然后使用*应用程序*文件夹选择，按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="2dbe7-495">Unity 将开始构建您的项目*应用*文件夹。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="2dbe7-496">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开*文件资源管理器*窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="2dbe7-497">第 11 章 – 部署你的应用程序</span><span class="sxs-lookup"><span data-stu-id="2dbe7-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="2dbe7-498">若要部署你的应用程序：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-498">To deploy your application:</span></span>

1.  <span data-ttu-id="2dbe7-499">导航到新的 Unity 生成 (*应用程序*文件夹)，然后打开解决方案文件与*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="2dbe7-500">在解决方案配置中，选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="2dbe7-501">在解决方案平台中，选择**x86**，**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="2dbe7-502">对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="2dbe7-503">不过，需要还执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2dbe7-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="2dbe7-504">知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="2dbe7-505">请确保*开发人员模式*是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="2dbe7-507">转到**生成菜单**，然后单击**部署解决方案**旁加载到您的 PC 应用程序。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="2dbe7-508">你的应用现在应出现在已安装的应用，准备好启动列表中。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="2dbe7-509">启动后，应用将提示你授予对麦克风访问权限。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="2dbe7-510">请务必单击**是**按钮。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="2dbe7-511">现已准备好开始翻译 ！</span><span class="sxs-lookup"><span data-stu-id="2dbe7-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="2dbe7-512">完成的翻译文本 API 应用程序</span><span class="sxs-lookup"><span data-stu-id="2dbe7-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="2dbe7-513">祝贺你，构建利用 Azure 翻译文本 API 将语音转换为已翻译的文本的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![最终产品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2dbe7-515">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="2dbe7-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="2dbe7-516">练习 1</span><span class="sxs-lookup"><span data-stu-id="2dbe7-516">Exercise 1</span></span>

<span data-ttu-id="2dbe7-517">可以在文本到语音转换将功能添加到应用程序中，以便在返回的文本所说？</span><span class="sxs-lookup"><span data-stu-id="2dbe7-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="2dbe7-518">练习 2</span><span class="sxs-lookup"><span data-stu-id="2dbe7-518">Exercise 2</span></span>

<span data-ttu-id="2dbe7-519">使用户可以更改应用本身的源和输出的语言 （from 和结束），因此应用程序不需要每次想要更改语言重新生成。</span><span class="sxs-lookup"><span data-stu-id="2dbe7-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
