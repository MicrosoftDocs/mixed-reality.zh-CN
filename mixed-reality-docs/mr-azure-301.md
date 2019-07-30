---
title: MR 和 Azure 301-语言翻译
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure 文本翻译 API。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, translator 文本, hololens, 沉浸, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554338"
---
>[!NOTE]
><span data-ttu-id="53dc5-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="53dc5-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="53dc5-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="53dc5-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="53dc5-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="53dc5-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="53dc5-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="53dc5-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="53dc5-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="53dc5-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="53dc5-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="53dc5-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="53dc5-110">MR 和 Azure 301:语言翻译</span><span class="sxs-lookup"><span data-stu-id="53dc5-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="53dc5-111">在本课程中, 你将学习如何使用 Azure 认知服务将翻译功能添加到混合现实应用程序, 并提供文本翻译 API。</span><span class="sxs-lookup"><span data-stu-id="53dc5-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![最终产品](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="53dc5-113">文本翻译 API 是一项近乎实时的翻译服务。</span><span class="sxs-lookup"><span data-stu-id="53dc5-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="53dc5-114">该服务是基于云的, 并且使用 REST API 调用, 应用程序可以使用神经计算机翻译技术将文本转换为其他语言。</span><span class="sxs-lookup"><span data-stu-id="53dc5-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="53dc5-115">有关详细信息, 请访问[Azure 文本翻译 API 页](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="53dc5-116">完成本课程后, 你将拥有一个混合现实应用程序, 该应用程序将能够执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="53dc5-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="53dc5-117">用户将进入连接到沉浸式 (VR) 耳机 (或 HoloLens 内置麦克风) 的麦克风。</span><span class="sxs-lookup"><span data-stu-id="53dc5-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="53dc5-118">此应用将捕获听写, 并将其发送到 Azure 文本翻译 API。</span><span class="sxs-lookup"><span data-stu-id="53dc5-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="53dc5-119">翻译结果将显示在 Unity 场景中的一个简单 UI 组中。</span><span class="sxs-lookup"><span data-stu-id="53dc5-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="53dc5-120">本课程将介绍如何从翻译人员服务获取结果到基于 Unity 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="53dc5-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="53dc5-121">您可以将这些概念应用到您可能生成的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="53dc5-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="53dc5-122">设备支持</span><span class="sxs-lookup"><span data-stu-id="53dc5-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="53dc5-123">摘要</span><span class="sxs-lookup"><span data-stu-id="53dc5-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="53dc5-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="53dc5-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="53dc5-125"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="53dc5-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="53dc5-126">MR 和 Azure 301:语言翻译</span><span class="sxs-lookup"><span data-stu-id="53dc5-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="53dc5-127">✔️</span><span class="sxs-lookup"><span data-stu-id="53dc5-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="53dc5-128">✔️</span><span class="sxs-lookup"><span data-stu-id="53dc5-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="53dc5-129">尽管本课程主要侧重于 Windows Mixed Reality 沉浸 (VR) 耳机, 但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="53dc5-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="53dc5-130">在本课程中, 你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="53dc5-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="53dc5-131">使用 HoloLens 时, 可能会在语音捕获过程中注意到某些回声。</span><span class="sxs-lookup"><span data-stu-id="53dc5-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53dc5-132">先决条件</span><span class="sxs-lookup"><span data-stu-id="53dc5-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="53dc5-133">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="53dc5-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="53dc5-134">另外请注意, 本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="53dc5-135">您可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="53dc5-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="53dc5-136">本课程建议采用以下硬件和软件:</span><span class="sxs-lookup"><span data-stu-id="53dc5-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="53dc5-137">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC, 用于沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="53dc5-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="53dc5-138">Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="53dc5-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="53dc5-139">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="53dc5-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="53dc5-140">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="53dc5-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="53dc5-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="53dc5-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="53dc5-142">启用了开发人员模式的[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="53dc5-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="53dc5-143">带有内置麦克风的一组耳机 (如果耳机没有内置麦克风和扬声器)</span><span class="sxs-lookup"><span data-stu-id="53dc5-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="53dc5-144">Azure 安装和翻译检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="53dc5-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="53dc5-145">开始之前</span><span class="sxs-lookup"><span data-stu-id="53dc5-145">Before you start</span></span>

- <span data-ttu-id="53dc5-146">为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="53dc5-147">本教程中的代码允许您从连接到您的 PC 的默认麦克风设备进行录制。</span><span class="sxs-lookup"><span data-stu-id="53dc5-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="53dc5-148">请确保将默认麦克风设备设置为计划用于捕获语音的设备。</span><span class="sxs-lookup"><span data-stu-id="53dc5-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="53dc5-149">若要允许你的电脑启用听写, 请转到 "**设置" > 隐私 > 语音 "、" 墨迹书写 & 键入**", 然后选择按钮"**打开语音服务并键入建议**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="53dc5-150">如果你使用的是连接到 (或内置于) 耳机的麦克风和耳机, 请确保在 "设置" 中打开 "在我磨损耳机、切换到耳机麦克风" **> 混合现实 > 音频和语音**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![混合现实设置](images/AzureLabs-Lab1-00-5.png)

   ![麦克风设置](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="53dc5-153">请注意, 如果你要为此实验室开发沉浸式耳机, 你可能会遇到音频输出设备问题。</span><span class="sxs-lookup"><span data-stu-id="53dc5-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="53dc5-154">这是由 Unity 中的问题引起的, 它在更高版本的 Unity (Unity 2018.2) 中是固定的。</span><span class="sxs-lookup"><span data-stu-id="53dc5-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="53dc5-155">此问题可防止 Unity 在运行时更改默认音频输出设备。</span><span class="sxs-lookup"><span data-stu-id="53dc5-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="53dc5-156">作为解决方法, 请确保已完成上述步骤, 并在此问题自行显示时关闭并重新打开编辑器。</span><span class="sxs-lookup"><span data-stu-id="53dc5-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="53dc5-157">第1章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="53dc5-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="53dc5-158">若要使用 Azure Translator API, 你将需要配置服务的实例, 使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="53dc5-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="53dc5-159">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="53dc5-160">如果还没有 Azure 帐户, 则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="53dc5-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="53dc5-161">如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="53dc5-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="53dc5-162">登录后, 单击左上角的 "**新建**", 搜索 "文本翻译 API"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="53dc5-163">选择**Enter**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-163">Select **Enter**.</span></span>

    ![新资源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="53dc5-165">在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="53dc5-166">新页将提供*文本翻译 API*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="53dc5-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="53dc5-167">在此页的左下角, 选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="53dc5-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![创建文本翻译 API 服务](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="53dc5-169">单击 "**创建**" 后:</span><span class="sxs-lookup"><span data-stu-id="53dc5-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="53dc5-170">为此服务实例插入所需的**名称**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="53dc5-171">选择相应的**订阅**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="53dc5-172">选择适合你的**定价层**, 如果这是第一次创建*文本翻译服务*, 则你应该可以使用免费层 (名为 F0)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="53dc5-173">选择一个**资源组**, 或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="53dc5-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="53dc5-174">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="53dc5-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="53dc5-175">建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="53dc5-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="53dc5-176">若要了解有关 Azure 资源组的详细信息, 请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="53dc5-177">确定资源组的**位置**(如果要创建新的资源组)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="53dc5-178">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="53dc5-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="53dc5-179">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="53dc5-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="53dc5-180">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="53dc5-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="53dc5-181">选择“创建”  。</span><span class="sxs-lookup"><span data-stu-id="53dc5-181">Select **Create**.</span></span>

        ![选择 "创建" 按钮。](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="53dc5-183">单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="53dc5-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="53dc5-184">创建服务实例后, 门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="53dc5-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure 服务创建通知](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="53dc5-186">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="53dc5-186">Click on the notification to explore your new Service instance.</span></span> 

    ![中转到资源弹出。](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="53dc5-188">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="53dc5-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="53dc5-189">你将转到新的文本翻译 API 服务实例。</span><span class="sxs-lookup"><span data-stu-id="53dc5-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![文本翻译 API 服务页](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="53dc5-191">在本教程中, 你的应用程序将需要调用你的服务, 这是通过使用你的服务的订阅密钥来完成的。</span><span class="sxs-lookup"><span data-stu-id="53dc5-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="53dc5-192">在*文本翻译*服务的 "*快速启动*" 页上, 导航到第一步,*获取你的密钥*, 然后单击 "**密钥**" (也可以通过单击位于 "服务" 导航菜单中的蓝色超链接项来实现此目的)。由键图标表示)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="53dc5-193">这会显示你的服务*密钥*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="53dc5-194">复制其中一个所显示的密钥, 因为稍后会在项目中使用此密钥。</span><span class="sxs-lookup"><span data-stu-id="53dc5-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="53dc5-195">第2章–设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="53dc5-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="53dc5-196">设置并测试混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="53dc5-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="53dc5-197">本课程不需要移动控制器。</span><span class="sxs-lookup"><span data-stu-id="53dc5-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="53dc5-198">如果需要支持设置沉浸式耳机, 请[遵循以下步骤](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="53dc5-199">下面是使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板:</span><span class="sxs-lookup"><span data-stu-id="53dc5-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="53dc5-200">打开*Unity* , 并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-200">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="53dc5-202">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="53dc5-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="53dc5-203">插入**MR_Translation**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="53dc5-204">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="53dc5-205">将位置设置为合适的*位置*(请记住, 更接近根目录更好)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="53dc5-206">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-206">Then, click **Create project**.</span></span>

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="53dc5-208">当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="53dc5-209">转到 "**编辑 > 首选项**", 然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="53dc5-210">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="53dc5-211">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="53dc5-211">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="53dc5-213">接下来, 通过单击 "**切换平台**" 按钮转到 "**文件 > 生成设置**", 并将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![生成设置窗口, 将平台切换到 UWP。](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="53dc5-215">请参阅**文件 > 生成设置**, 并确保:</span><span class="sxs-lookup"><span data-stu-id="53dc5-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="53dc5-216">"**目标设备**" 设置为 "**任何设备**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="53dc5-217">对于 Microsoft HoloLens, 将 "**目标设备**" 设置为 " *hololens*"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="53dc5-218">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="53dc5-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="53dc5-219">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="53dc5-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="53dc5-220">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="53dc5-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="53dc5-221">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="53dc5-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="53dc5-222">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="53dc5-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="53dc5-223">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="53dc5-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="53dc5-224">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="53dc5-224">A save window will appear.</span></span>

            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="53dc5-226">为此创建新文件夹, 并为将来的任何场景创建一个新文件夹, 然后选择 "**新建文件夹**" 按钮以创建新文件夹, 将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            !["创建新脚本" 文件夹](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="53dc5-228">打开新创建的**场景**文件夹, 然后*在 "文件名*: 文本" 字段中, 键入**MR_TranslationScene**, 然后按 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![为新场景指定名称。](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="53dc5-230">请注意, 必须将 Unity 场景保存在 "*资产*" 文件夹中, 因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="53dc5-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="53dc5-231">创建场景文件夹 (以及其他类似文件夹) 是构造 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="53dc5-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="53dc5-232">现在, "*生成设置*" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="53dc5-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="53dc5-233">在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="53dc5-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放机设置。](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="53dc5-235">在此面板中, 需要验证几项设置:</span><span class="sxs-lookup"><span data-stu-id="53dc5-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="53dc5-236">在 "**其他设置**" 选项卡中:</span><span class="sxs-lookup"><span data-stu-id="53dc5-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="53dc5-237">**脚本运行时版本**应**稳定**(与 .net 3.5 等效)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="53dc5-238">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="53dc5-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="53dc5-239">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="53dc5-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="53dc5-241">在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:</span><span class="sxs-lookup"><span data-stu-id="53dc5-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="53dc5-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="53dc5-242">**InternetClient**</span></span>
        2. <span data-ttu-id="53dc5-243">**十分**</span><span class="sxs-lookup"><span data-stu-id="53dc5-243">**Microphone**</span></span>

            ![正在更新发布设置。](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="53dc5-245">在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="53dc5-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 设置。](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="53dc5-247">返回**生成设置**, *Unity C#项目*不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="53dc5-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="53dc5-248">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="53dc5-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="53dc5-249">保存场景和项目 (**file > SAVE 场景/file > SAVE Project**)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="53dc5-250">第3章–照相机设置</span><span class="sxs-lookup"><span data-stu-id="53dc5-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53dc5-251">如果希望跳过本课程的*Unity 设置*组件, 并继续直接进入代码, 可以[下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), 将其作为[*自定义包*](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目, 然后从[第5章](#chapter-5--create-the-results-class)继续。</span><span class="sxs-lookup"><span data-stu-id="53dc5-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="53dc5-252">你仍需要创建一个 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="53dc5-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="53dc5-253">在 "*层次结构" 面板*中, 你会看到一个名为 "**主相机**" 的对象, 此对象表示你在应用程序中 "内部" 后的 "头" 点。</span><span class="sxs-lookup"><span data-stu-id="53dc5-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="53dc5-254">在您前面的 Unity 仪表板中, 选择 " **GameObject" 主摄像机**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="53dc5-255">你会注意到, "*检查器" 面板*(通常位于仪表板中) 将显示该*GameObject*的各种组件, 其中的 "*转换*" 位于顶部, 后面跟有*相机*和一些其他组件。</span><span class="sxs-lookup"><span data-stu-id="53dc5-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="53dc5-256">需要重置主摄像机的转换, 以便正确定位。</span><span class="sxs-lookup"><span data-stu-id="53dc5-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="53dc5-257">为此, 请选择相机*转换*组件旁边的**齿轮**图标, 然后选择 "**重置**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![重置照相机转换。](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="53dc5-259">*转换*组件如下所示:</span><span class="sxs-lookup"><span data-stu-id="53dc5-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="53dc5-260">*位置*设置为**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="53dc5-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="53dc5-261">*旋转*设置为**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="53dc5-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="53dc5-262">"*小数位数*" 设置为1、1 **、1**</span><span class="sxs-lookup"><span data-stu-id="53dc5-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![照相机的转换信息](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="53dc5-264">接下来, 选择了 "**相机**" 对象, 并查看位于 "*检查器" 面板*底部的 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="53dc5-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="53dc5-265">选择该按钮, 然后搜索 (通过在搜索字段中键入 "*音频源*" 或 "导航" 部分) 来查找称为 "**音频源**" 的组件, 并选择它 (按 enter 键也能正常运行)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="53dc5-266">*音频源*组件将添加到**摄像机**, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="53dc5-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![添加音频源组件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="53dc5-268">对于 Microsoft HoloLens, 你还需要更改**以下内容,** 这是你的摄像机上**相机**组件的一部分:</span><span class="sxs-lookup"><span data-stu-id="53dc5-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="53dc5-269">**清除标志:** 纯色。</span><span class="sxs-lookup"><span data-stu-id="53dc5-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="53dc5-270">**背景**"黑色, Alpha 0" –十六进制颜色: #00000000。</span><span class="sxs-lookup"><span data-stu-id="53dc5-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="53dc5-271">第4章-安装调试画布</span><span class="sxs-lookup"><span data-stu-id="53dc5-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="53dc5-272">若要显示转换的输入和输出, 需要创建一个基本 UI。</span><span class="sxs-lookup"><span data-stu-id="53dc5-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="53dc5-273">在本课程中, 您将创建一个画布 UI 对象, 其中包含多个 "Text" 对象来显示数据。</span><span class="sxs-lookup"><span data-stu-id="53dc5-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="53dc5-274">右键单击 "*层次结构" 面板*的空白区域, 在 " **UI**" 下, 添加**画布**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![添加新的画布 UI 对象。](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="53dc5-276">选中 Canvas 对象后, 在 "*检查器" 面板*(位于 "画布" 组件中) 将 "**渲染模式**" 更改为 "**世界上空间**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="53dc5-277">接下来, 在 "*检查器" 面板的 Rect 转换*中更改以下参数:</span><span class="sxs-lookup"><span data-stu-id="53dc5-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="53dc5-278">*POS* X 0 Y 0 Z 40 -  </span><span class="sxs-lookup"><span data-stu-id="53dc5-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="53dc5-279">*宽度*-500</span><span class="sxs-lookup"><span data-stu-id="53dc5-279">*Width* -    500</span></span>
    3. <span data-ttu-id="53dc5-280">*高度*-300</span><span class="sxs-lookup"><span data-stu-id="53dc5-280">*Height* -   300</span></span>
    4. <span data-ttu-id="53dc5-281">*X 0.13\*\*\*x*\* 0.13 **Z** 0.13  - </span><span class="sxs-lookup"><span data-stu-id="53dc5-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![更新画布的 rect 转换。](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="53dc5-283">右键单击 "*层次结构" 面板*中的 " **UI**" 下的**画布**, 然后添加**面板**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="53dc5-284">此**面板**将提供您将在场景中显示的文本的背景。</span><span class="sxs-lookup"><span data-stu-id="53dc5-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="53dc5-285">右键单击 "*层次结构" 面板*中的 " **UI**" 下的**面板**, 然后添加一个**文本对象**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="53dc5-286">重复相同的过程, 直到总共创建了四个 UI 文本对象 (提示: 如果已选择第一个 "文本" 对象, 则只需按 **"Ctrl" + "d"** 即可复制该对象, 直到总共有四个)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="53dc5-287">对于每个**文本对象**, 请选择它, 并使用下表在 "*检查器" 面板*中设置参数。</span><span class="sxs-lookup"><span data-stu-id="53dc5-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="53dc5-288">对于*Rect 转换*组件:</span><span class="sxs-lookup"><span data-stu-id="53dc5-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="53dc5-289">名称</span><span class="sxs-lookup"><span data-stu-id="53dc5-289">Name</span></span>                   | <span data-ttu-id="53dc5-290">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="53dc5-290">Transform - *Position*</span></span>             | <span data-ttu-id="53dc5-291">宽度</span><span class="sxs-lookup"><span data-stu-id="53dc5-291">Width</span></span>      | <span data-ttu-id="53dc5-292">Height</span><span class="sxs-lookup"><span data-stu-id="53dc5-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="53dc5-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="53dc5-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="53dc5-295">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-295">300</span></span>        | <span data-ttu-id="53dc5-296">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-296">30</span></span>        |
        | <span data-ttu-id="53dc5-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-297">AzureResponseLabel</span></span>     | <span data-ttu-id="53dc5-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="53dc5-299">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-299">300</span></span>        | <span data-ttu-id="53dc5-300">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-300">30</span></span>        |
        | <span data-ttu-id="53dc5-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-301">DictationLabel</span></span>         | <span data-ttu-id="53dc5-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="53dc5-303">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-303">300</span></span>        | <span data-ttu-id="53dc5-304">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-304">30</span></span>        |
        | <span data-ttu-id="53dc5-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-305">TranslationResultLabel</span></span> | <span data-ttu-id="53dc5-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="53dc5-307">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-307">300</span></span>        | <span data-ttu-id="53dc5-308">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-308">30</span></span>        |


    2. <span data-ttu-id="53dc5-309">对于**文本 (脚本)** 组件:</span><span class="sxs-lookup"><span data-stu-id="53dc5-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="53dc5-310">名称</span><span class="sxs-lookup"><span data-stu-id="53dc5-310">Name</span></span>                   | <span data-ttu-id="53dc5-311">Text</span><span class="sxs-lookup"><span data-stu-id="53dc5-311">Text</span></span>               | <span data-ttu-id="53dc5-312">字号</span><span class="sxs-lookup"><span data-stu-id="53dc5-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="53dc5-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="53dc5-314">麦克风状态:</span><span class="sxs-lookup"><span data-stu-id="53dc5-314">Microphone Status:</span></span> | <span data-ttu-id="53dc5-315">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-315">20</span></span>           |
        | <span data-ttu-id="53dc5-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-316">AzureResponseLabel</span></span>     | <span data-ttu-id="53dc5-317">Azure Web 响应</span><span class="sxs-lookup"><span data-stu-id="53dc5-317">Azure Web Response</span></span> | <span data-ttu-id="53dc5-318">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-318">20</span></span>           |
        | <span data-ttu-id="53dc5-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-319">DictationLabel</span></span>         |   <span data-ttu-id="53dc5-320">您刚才说:</span><span class="sxs-lookup"><span data-stu-id="53dc5-320">You just said:</span></span>   | <span data-ttu-id="53dc5-321">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-321">20</span></span>           |
        | <span data-ttu-id="53dc5-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="53dc5-322">TranslationResultLabel</span></span> |    <span data-ttu-id="53dc5-323">换算</span><span class="sxs-lookup"><span data-stu-id="53dc5-323">Translation:</span></span>    | <span data-ttu-id="53dc5-324">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-324">20</span></span>           |

        ![为 UI 标签输入相应的值。](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="53dc5-326">同时, 将字体样式设置为**粗体**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="53dc5-327">这会使文本更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="53dc5-327">This will make the text easier to read.</span></span>

        ![粗体。](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="53dc5-329">对于[第5章](#chapter-5--create-the-results-class)中创建的每个*UI 文本对象*, 创建新的*子* **UI 文本对象**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="53dc5-330">这些子级将显示应用程序的输出。</span><span class="sxs-lookup"><span data-stu-id="53dc5-330">These children will display the output of the application.</span></span> <span data-ttu-id="53dc5-331">右键单击目标父对象 (例如*MicrophoneStatusLabel*), 然后选择 "**用户界面**", 然后选择 "**文本**", 创建*子*对象。</span><span class="sxs-lookup"><span data-stu-id="53dc5-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="53dc5-332">对于其中的每个子项, 请选择它, 并使用下表在 "检查器" 面板中设置参数。</span><span class="sxs-lookup"><span data-stu-id="53dc5-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="53dc5-333">对于**Rect 转换**组件:</span><span class="sxs-lookup"><span data-stu-id="53dc5-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="53dc5-334">名称</span><span class="sxs-lookup"><span data-stu-id="53dc5-334">Name</span></span>                  | <span data-ttu-id="53dc5-335">转换*位置*</span><span class="sxs-lookup"><span data-stu-id="53dc5-335">Transform - *Position*</span></span> | <span data-ttu-id="53dc5-336">宽度</span><span class="sxs-lookup"><span data-stu-id="53dc5-336">Width</span></span>      | <span data-ttu-id="53dc5-337">Height</span><span class="sxs-lookup"><span data-stu-id="53dc5-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="53dc5-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="53dc5-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="53dc5-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="53dc5-340">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-340">300</span></span>        | <span data-ttu-id="53dc5-341">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-341">30</span></span>        |
        | <span data-ttu-id="53dc5-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="53dc5-342">AzureResponseText</span></span>     | <span data-ttu-id="53dc5-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="53dc5-344">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-344">300</span></span>        | <span data-ttu-id="53dc5-345">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-345">30</span></span>        |
        | <span data-ttu-id="53dc5-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="53dc5-346">DictationText</span></span>         | <span data-ttu-id="53dc5-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="53dc5-348">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-348">300</span></span>        | <span data-ttu-id="53dc5-349">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-349">30</span></span>        |
        | <span data-ttu-id="53dc5-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="53dc5-350">TranslationResultText</span></span> | <span data-ttu-id="53dc5-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="53dc5-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="53dc5-352">300</span><span class="sxs-lookup"><span data-stu-id="53dc5-352">300</span></span>        | <span data-ttu-id="53dc5-353">30</span><span class="sxs-lookup"><span data-stu-id="53dc5-353">30</span></span>        |

    2. <span data-ttu-id="53dc5-354">对于**文本 (脚本)** 组件:</span><span class="sxs-lookup"><span data-stu-id="53dc5-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="53dc5-355">名称</span><span class="sxs-lookup"><span data-stu-id="53dc5-355">Name</span></span>                  | <span data-ttu-id="53dc5-356">Text</span><span class="sxs-lookup"><span data-stu-id="53dc5-356">Text</span></span>          | <span data-ttu-id="53dc5-357">字号</span><span class="sxs-lookup"><span data-stu-id="53dc5-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="53dc5-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="53dc5-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="53dc5-359">??</span><span class="sxs-lookup"><span data-stu-id="53dc5-359">??</span></span>       | <span data-ttu-id="53dc5-360">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-360">20</span></span>           |
        | <span data-ttu-id="53dc5-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="53dc5-361">AzureResponseText</span></span>     |      <span data-ttu-id="53dc5-362">??</span><span class="sxs-lookup"><span data-stu-id="53dc5-362">??</span></span>       | <span data-ttu-id="53dc5-363">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-363">20</span></span>           |
        | <span data-ttu-id="53dc5-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="53dc5-364">DictationText</span></span>         |      <span data-ttu-id="53dc5-365">??</span><span class="sxs-lookup"><span data-stu-id="53dc5-365">??</span></span>       | <span data-ttu-id="53dc5-366">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-366">20</span></span>           |
        | <span data-ttu-id="53dc5-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="53dc5-367">TranslationResultText</span></span> |      <span data-ttu-id="53dc5-368">??</span><span class="sxs-lookup"><span data-stu-id="53dc5-368">??</span></span>       | <span data-ttu-id="53dc5-369">20</span><span class="sxs-lookup"><span data-stu-id="53dc5-369">20</span></span>           |

9. <span data-ttu-id="53dc5-370">接下来, 为每个文本组件选择 "中心" 对齐选项:</span><span class="sxs-lookup"><span data-stu-id="53dc5-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![对齐文本。](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="53dc5-372">若要确保**子 UI 文本**对象易于阅读, 请更改其*颜色*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="53dc5-373">通过单击 "*颜色*" 旁边的栏 (当前为 "黑色") 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="53dc5-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![输入 UI 文本输出的相应值。](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="53dc5-375">然后, 在 "新建"、"小"、"*颜色*" 窗口中, 将*Hex 颜色*改为:**0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="53dc5-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![将颜色更新为蓝色。](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="53dc5-377">下面是**UI**的外观。</span><span class="sxs-lookup"><span data-stu-id="53dc5-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="53dc5-378">在 "*层次结构" 面板*中:</span><span class="sxs-lookup"><span data-stu-id="53dc5-378">In the *Hierarchy Panel*:</span></span>

        ![具有所提供的结构中的层次结构。](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="53dc5-380">在*场景*和*游戏视图*中:</span><span class="sxs-lookup"><span data-stu-id="53dc5-380">In the *Scene* and *Game Views*:</span></span>

        ![使场景和游戏视图位于同一结构中。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="53dc5-382">第5章–创建结果类</span><span class="sxs-lookup"><span data-stu-id="53dc5-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="53dc5-383">需要创建的第一个脚本是*结果*类, 该类负责提供一种方式来查看翻译结果。</span><span class="sxs-lookup"><span data-stu-id="53dc5-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="53dc5-384">类存储并显示以下内容:</span><span class="sxs-lookup"><span data-stu-id="53dc5-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="53dc5-385">来自 Azure 的响应结果。</span><span class="sxs-lookup"><span data-stu-id="53dc5-385">The response result from Azure.</span></span>
- <span data-ttu-id="53dc5-386">麦克风状态。</span><span class="sxs-lookup"><span data-stu-id="53dc5-386">The microphone status.</span></span> 
- <span data-ttu-id="53dc5-387">听写 (语音到文本) 的结果。</span><span class="sxs-lookup"><span data-stu-id="53dc5-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="53dc5-388">转换的结果。</span><span class="sxs-lookup"><span data-stu-id="53dc5-388">The result of the translation.</span></span>

<span data-ttu-id="53dc5-389">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="53dc5-389">To create this class:</span></span> 

1.  <span data-ttu-id="53dc5-390">右键单击 "*项目" 面板*, 然后**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="53dc5-391">命名文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-391">Name the folder **Scripts**.</span></span> 
 
    ![创建脚本文件夹。](images/AzureLabs-Lab1-31.png)

    ![打开 "脚本" 文件夹。](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="53dc5-394">在 "**脚本**" 文件夹中, 双击以打开。</span><span class="sxs-lookup"><span data-stu-id="53dc5-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="53dc5-395">在该文件夹中, 右键单击, 然后选择 "**创建 >** 然后**C#** 选择" 脚本 "。</span><span class="sxs-lookup"><span data-stu-id="53dc5-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="53dc5-396">为脚本*结果*命名。</span><span class="sxs-lookup"><span data-stu-id="53dc5-396">Name the script *Results*.</span></span> 

    ![创建第一个脚本。](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="53dc5-398">双击新*结果*脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="53dc5-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="53dc5-399">插入以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="53dc5-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="53dc5-400">在类中插入以下变量:</span><span class="sxs-lookup"><span data-stu-id="53dc5-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="53dc5-401">然后添加*唤醒 ()* 方法, 在类初始化时将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="53dc5-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="53dc5-402">最后, 添加负责将各种结果信息输出到 UI 的方法。</span><span class="sxs-lookup"><span data-stu-id="53dc5-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="53dc5-403">在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="53dc5-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="53dc5-404">第6章–创建*MicrophoneManager*类</span><span class="sxs-lookup"><span data-stu-id="53dc5-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="53dc5-405">要创建的第二个类是*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="53dc5-406">此类负责:</span><span class="sxs-lookup"><span data-stu-id="53dc5-406">This class is responsible for:</span></span>

- <span data-ttu-id="53dc5-407">检测连接到耳机或计算机的记录设备 (以默认值为准)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="53dc5-408">捕获音频 (语音) 并使用听写将其存储为字符串。</span><span class="sxs-lookup"><span data-stu-id="53dc5-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="53dc5-409">暂停语音后, 将听写提交给转换器类。</span><span class="sxs-lookup"><span data-stu-id="53dc5-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="53dc5-410">承载一个方法, 该方法可以在需要时停止语音捕获。</span><span class="sxs-lookup"><span data-stu-id="53dc5-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="53dc5-411">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="53dc5-411">To create this class:</span></span> 
1.  <span data-ttu-id="53dc5-412">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="53dc5-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="53dc5-413">右键单击 "**脚本**" 文件夹中, 单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="53dc5-414">将脚本命名为*MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="53dc5-415">双击新脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="53dc5-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="53dc5-416">在*MicrophoneManager*类的顶部, 将命名空间更新为与以下相同:</span><span class="sxs-lookup"><span data-stu-id="53dc5-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="53dc5-417">然后, 在*MicrophoneManager*类中添加以下变量:</span><span class="sxs-lookup"><span data-stu-id="53dc5-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="53dc5-418">现在需要添加*唤醒 ()* 和*Start ()* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="53dc5-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="53dc5-419">当类初始化时, 将调用以下内容:</span><span class="sxs-lookup"><span data-stu-id="53dc5-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="53dc5-420">您可以*删除* *Update ()* 方法, 因为此类将不会使用它。</span><span class="sxs-lookup"><span data-stu-id="53dc5-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="53dc5-421">现在, 你需要应用程序用来启动和停止语音捕获, 并将其传递给*Translator*类的方法。</span><span class="sxs-lookup"><span data-stu-id="53dc5-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="53dc5-422">复制以下代码, 并将其粘贴到*Start ()* 方法下。</span><span class="sxs-lookup"><span data-stu-id="53dc5-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="53dc5-423">虽然此应用程序将不会使用它, 但在此还提供了*StopCapturingAudio ()* 方法, 因此, 如果要实现在应用程序中停止捕获音频的功能, 则也是如此。</span><span class="sxs-lookup"><span data-stu-id="53dc5-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="53dc5-424">现在需要添加语音停止时将调用的听写处理程序。</span><span class="sxs-lookup"><span data-stu-id="53dc5-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="53dc5-425">此方法随后将听写的文本传递到*转换器*类。</span><span class="sxs-lookup"><span data-stu-id="53dc5-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="53dc5-426">在返回到 Unity 之前, 请务必保存 Visual Studio 中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="53dc5-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="53dc5-427">此时, 你会注意到在*Unity 编辑器控制台*面板中出现错误 ("名称" 转换器不存在 ... ")。</span><span class="sxs-lookup"><span data-stu-id="53dc5-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="53dc5-428">这是因为代码引用了将在下一章中创建的*转换器*类。</span><span class="sxs-lookup"><span data-stu-id="53dc5-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="53dc5-429">第7章–调用 Azure 和转换器服务</span><span class="sxs-lookup"><span data-stu-id="53dc5-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="53dc5-430">需要创建的最后一个脚本是*转换器*类。</span><span class="sxs-lookup"><span data-stu-id="53dc5-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="53dc5-431">此类负责:</span><span class="sxs-lookup"><span data-stu-id="53dc5-431">This class is responsible for:</span></span>

-   <span data-ttu-id="53dc5-432">使用*Azure*对**身份验证令牌**进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="53dc5-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="53dc5-433">使用**身份验证令牌**提交要翻译的文本 (从*MicrophoneManager*类收到)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="53dc5-434">接收转换后的结果, 并将其传递到要在 UI 中可视化的*结果*类。</span><span class="sxs-lookup"><span data-stu-id="53dc5-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="53dc5-435">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="53dc5-435">To create this Class:</span></span> 
1.  <span data-ttu-id="53dc5-436">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="53dc5-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="53dc5-437">右键单击 "**项目" 面板**,  **C#创建 > 脚本**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="53dc5-438">调用脚本*转换器*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="53dc5-439">双击新的*转换器*脚本以**通过 Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="53dc5-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="53dc5-440">将以下命名空间添加到文件顶部:</span><span class="sxs-lookup"><span data-stu-id="53dc5-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="53dc5-441">然后在*转换器*类中添加以下变量:</span><span class="sxs-lookup"><span data-stu-id="53dc5-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="53dc5-442">插入语言**枚举**中的语言只是示例。</span><span class="sxs-lookup"><span data-stu-id="53dc5-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="53dc5-443">如果需要, 可以随意添加更多内容;此[API 支持超过60种语言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)(包括克)!</span><span class="sxs-lookup"><span data-stu-id="53dc5-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="53dc5-444">还有一个[涵盖可用语言的更交互式页面](https://www.microsoft.com/translator/business/languages/), 不过, 当站点语言设置为 "en-us" 时, 此页仅显示为 "en-us" (Microsoft 网站可能会重定向到你的本地语言)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="53dc5-445">您可以在页面底部或通过更改 URL 来更改站点语言。</span><span class="sxs-lookup"><span data-stu-id="53dc5-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="53dc5-446">在上述代码片段中, **authorizationKey**值必须是在订阅*Azure 文本翻译 API*时收到的**密钥**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="53dc5-447">[第1章](#chapter-1--the-azure-portal)中对此进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="53dc5-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="53dc5-448">现在需要添加*唤醒 ()* 和*Start ()* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="53dc5-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="53dc5-449">在这种情况下, 代码将使用授权密钥调用*Azure*以获取*令牌*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="53dc5-450">该令牌将在10分钟后过期。</span><span class="sxs-lookup"><span data-stu-id="53dc5-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="53dc5-451">根据应用的方案, 可能需要多次进行相同的协同程序调用。</span><span class="sxs-lookup"><span data-stu-id="53dc5-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="53dc5-452">获取令牌的协同程序如下所示:</span><span class="sxs-lookup"><span data-stu-id="53dc5-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="53dc5-453">如果编辑 IEnumerator 方法**GetTokenCoroutine ()** 的名称, 则需要更新上述代码中的*StartCoroutine*和*StopCoroutine*调用字符串值。</span><span class="sxs-lookup"><span data-stu-id="53dc5-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="53dc5-454">[按照 Unity 文档](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), 若要停止特定的*协同程序*, 需要使用字符串值方法。</span><span class="sxs-lookup"><span data-stu-id="53dc5-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="53dc5-455">接下来, 添加协同程序 (在其下方提供 "支持" 流方法), 以获取*MicrophoneManager*类收到的文本的翻译。</span><span class="sxs-lookup"><span data-stu-id="53dc5-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="53dc5-456">此代码将创建一个要发送到*Azure 文本翻译 API*的查询字符串, 然后使用内部 Unity UnityWebRequest 类通过查询字符串对终结点进行 "Get" 调用。</span><span class="sxs-lookup"><span data-stu-id="53dc5-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="53dc5-457">然后, 将使用该结果在结果对象中设置翻译。</span><span class="sxs-lookup"><span data-stu-id="53dc5-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="53dc5-458">下面的代码显示了实现:</span><span class="sxs-lookup"><span data-stu-id="53dc5-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="53dc5-459">在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="53dc5-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="53dc5-460">第8章–配置 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="53dc5-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="53dc5-461">返回在 Unity 编辑器中，单击并拖动 *结果* 类 *从* **脚本** 文件夹 **Main Camera** 中对象 *层次结构面板* 。</span><span class="sxs-lookup"><span data-stu-id="53dc5-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="53dc5-462">单击**主摄像机**, 查看*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="53dc5-463">你会注意到, 在新添加的*脚本*组件中, 有四个字段包含空值。</span><span class="sxs-lookup"><span data-stu-id="53dc5-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="53dc5-464">这些是对代码中的属性的输出引用。</span><span class="sxs-lookup"><span data-stu-id="53dc5-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="53dc5-465">将相应的**文本**对象从 "*层次结构" 面板*拖动到这四个槽, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="53dc5-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![用指定的值更新目标引用。](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="53dc5-467">接下来, 在 "**脚本**" 文件夹中单击 "*转换器*" 类并将其拖到 "*层次结构" 面板*中的 "**照相机**" 对象。</span><span class="sxs-lookup"><span data-stu-id="53dc5-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="53dc5-468">然后, 在 "*层次结构" 面板*中单击 "**脚本**" 文件夹中的*MicrophoneManager*类, 并将其拖到**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="53dc5-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="53dc5-469">最后, 单击**主摄像机**, 查看*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="53dc5-470">你会注意到, 在所拖动的脚本中, 有两个下拉框可用于设置语言。</span><span class="sxs-lookup"><span data-stu-id="53dc5-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![确保预期的翻译语言为输入。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="53dc5-472">第9章–在混合现实中测试</span><span class="sxs-lookup"><span data-stu-id="53dc5-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="53dc5-473">此时, 需要测试场景是否已正确实现。</span><span class="sxs-lookup"><span data-stu-id="53dc5-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="53dc5-474">请确保：</span><span class="sxs-lookup"><span data-stu-id="53dc5-474">Ensure that:</span></span>

- <span data-ttu-id="53dc5-475">[第1章](#chapter-1--the-azure-portal)中提到的所有设置都已正确设置。</span><span class="sxs-lookup"><span data-stu-id="53dc5-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="53dc5-476">*结果*、*转换器*和*MicrophoneManager*将脚本附加到**摄像机的主**对象。</span><span class="sxs-lookup"><span data-stu-id="53dc5-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="53dc5-477">已将*Azure 文本翻译 API*服务**密钥**放置在*转换器*脚本内的**authorizationKey**变量中。</span><span class="sxs-lookup"><span data-stu-id="53dc5-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="53dc5-478">*主相机检查器面板*中的所有字段均已正确分配。</span><span class="sxs-lookup"><span data-stu-id="53dc5-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="53dc5-479">你的麦克风在运行场景时工作 (如果没有, 请检查你的已连接麦克风是否为*默认*设备, 以及你是否在[Windows 中正确设置了它](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。</span><span class="sxs-lookup"><span data-stu-id="53dc5-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="53dc5-480">可以通过在*Unity 编辑器*中按 "**播放**" 按钮来测试沉浸式头戴式耳机。</span><span class="sxs-lookup"><span data-stu-id="53dc5-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="53dc5-481">该应用应通过附加的沉浸式耳机来运行。</span><span class="sxs-lookup"><span data-stu-id="53dc5-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="53dc5-482">如果在 Unity 控制台中看到有关默认音频设备变化的错误, 场景可能无法按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="53dc5-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="53dc5-483">这是因为混合现实门户使用内置麦克风处理随附的耳机的方式。</span><span class="sxs-lookup"><span data-stu-id="53dc5-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="53dc5-484">如果看到此错误, 只需停止场景并再次启动, 应按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="53dc5-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="53dc5-485">第10章–在本地计算机上构建 UWP 解决方案和旁加载</span><span class="sxs-lookup"><span data-stu-id="53dc5-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="53dc5-486">此项目的 Unity 部分所需的所有内容现在均已完成, 因此可以从 Unity 构建它。</span><span class="sxs-lookup"><span data-stu-id="53dc5-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="53dc5-487">导航到 "**生成设置**":**文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="53dc5-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="53dc5-488">在**生成设置**窗口中, 单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-488">From the **Build Settings** window, click **Build**.</span></span>

    ![构建 Unity 场景。](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="53dc5-490">如果尚未这样做, 请勾选**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="53dc5-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="53dc5-491">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="53dc5-491">Click **Build**.</span></span> <span data-ttu-id="53dc5-492">Unity 将启动*文件资源管理器*窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="53dc5-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="53dc5-493">立即创建该文件夹并将其命名为*应用*。</span><span class="sxs-lookup"><span data-stu-id="53dc5-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="53dc5-494">选择*应用*文件夹后, 按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="53dc5-495">Unity 将开始向*应用*文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="53dc5-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="53dc5-496">Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "*文件资源管理器*" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。</span><span class="sxs-lookup"><span data-stu-id="53dc5-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="53dc5-497">第11章-部署应用程序</span><span class="sxs-lookup"><span data-stu-id="53dc5-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="53dc5-498">若要部署应用程序:</span><span class="sxs-lookup"><span data-stu-id="53dc5-498">To deploy your application:</span></span>

1.  <span data-ttu-id="53dc5-499">导航到新的 Unity 生成 (*应用*文件夹), 并在*Visual Studio*中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="53dc5-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="53dc5-500">在解决方案配置中, 选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="53dc5-501">在解决方案平台中, 选择 " **x86**,**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="53dc5-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="53dc5-502">对于 Microsoft HoloLens, 你可能会发现将其设置为*远程计算机*会更容易, 因此你不会受限到计算机上。</span><span class="sxs-lookup"><span data-stu-id="53dc5-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="53dc5-503">不过, 还需要执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="53dc5-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="53dc5-504">知道您的 HoloLens 的**IP 地址**, 可在 "*设置" > 网络 & Internet > > "高级选项*" 中找到;IPv4 是应使用的地址。</span><span class="sxs-lookup"><span data-stu-id="53dc5-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="53dc5-505">确保*开发人员模式*已**打开**;在 "设置" 中找到 *> 更新开发人员 & 安全 >* 。</span><span class="sxs-lookup"><span data-stu-id="53dc5-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="53dc5-507">中转到 "**生成" 菜单**, 然后单击 "**部署解决方案**", 将应用程序旁加载到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="53dc5-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="53dc5-508">应用现在应显示在已安装的应用列表中, 可以启动。</span><span class="sxs-lookup"><span data-stu-id="53dc5-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="53dc5-509">启动后, 应用会提示你授权访问麦克风。</span><span class="sxs-lookup"><span data-stu-id="53dc5-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="53dc5-510">请确保单击 **"是"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="53dc5-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="53dc5-511">你现在已准备好开始翻译!</span><span class="sxs-lookup"><span data-stu-id="53dc5-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="53dc5-512">已完成的翻译文本 API 应用程序</span><span class="sxs-lookup"><span data-stu-id="53dc5-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="53dc5-513">恭喜, 你构建了一个混合现实应用, 它利用 Azure 翻译文本 API 将语音转换为翻译文本。</span><span class="sxs-lookup"><span data-stu-id="53dc5-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![最终产品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="53dc5-515">额外练习</span><span class="sxs-lookup"><span data-stu-id="53dc5-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="53dc5-516">练习1</span><span class="sxs-lookup"><span data-stu-id="53dc5-516">Exercise 1</span></span>

<span data-ttu-id="53dc5-517">是否可以向应用程序中添加文本到语音功能, 以使返回的文本被朗读？</span><span class="sxs-lookup"><span data-stu-id="53dc5-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="53dc5-518">练习2</span><span class="sxs-lookup"><span data-stu-id="53dc5-518">Exercise 2</span></span>

<span data-ttu-id="53dc5-519">使用户能够在应用程序中更改源和输出语言 ("从" 和 "到"), 因此在每次需要更改语言时无需重新生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="53dc5-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
