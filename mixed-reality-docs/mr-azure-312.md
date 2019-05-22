---
title: MR 和 Azure 312-智能机器人应用程序集成
description: 完成此课程以了解如何创建和部署智能机器人，使用 Microsoft Bot Framework v4 和混合的现实应用程序中与之进行通信。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 计算机视觉、 hololens，令人着迷，vr microsoft bot framework v4、 web app 机器人、 bot framework、 microsoft 智能机器人应用程序
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593044"
---
>[!NOTE]
><span data-ttu-id="a0f0c-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a0f0c-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a0f0c-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a0f0c-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a0f0c-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a0f0c-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="a0f0c-110">MR 和 Azure 312:智能机器人应用程序集成</span><span class="sxs-lookup"><span data-stu-id="a0f0c-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="a0f0c-111">在本课程中，您将学习如何创建和部署使用 Microsoft Bot Framework V4 智能机器人应用程序并与之通信通过 Windows Mixed Reality 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="a0f0c-112">**Microsoft Bot Framework V4**是一组 Api 设计的开发人员提供工具以生成可扩展和可缩放的智能机器人应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="a0f0c-113">有关详细信息，请访问[Microsoft Bot Framework 页](https://dev.botframework.com/)或[V4 Git 存储库](https://github.com/Microsoft/botbuilder-dotnet/wiki)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="a0f0c-114">完成此课程后，您便会生成一个 Windows Mixed Reality 应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="a0f0c-115">使用**点击手势**开始侦听用户语音的智能机器人应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="a0f0c-116">当用户具有所说的内容时，智能机器人应用程序将尝试提供了一个响应。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="a0f0c-117">显示为文本，附近机器人，Unity 场景中定位的智能机器人答复。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="a0f0c-118">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="a0f0c-119">本课程旨在教您如何将 Azure 服务集成与你的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="a0f0c-120">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="a0f0c-121">设备支持</span><span class="sxs-lookup"><span data-stu-id="a0f0c-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a0f0c-122">课程</span><span class="sxs-lookup"><span data-stu-id="a0f0c-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a0f0c-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a0f0c-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a0f0c-124"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="a0f0c-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a0f0c-125">MR 和 Azure 312:智能机器人应用程序集成</span><span class="sxs-lookup"><span data-stu-id="a0f0c-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="a0f0c-126">✔️</span><span class="sxs-lookup"><span data-stu-id="a0f0c-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a0f0c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="a0f0c-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a0f0c-128">尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="a0f0c-129">因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="a0f0c-130">按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0f0c-131">先决条件</span><span class="sxs-lookup"><span data-stu-id="a0f0c-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a0f0c-132">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a0f0c-133">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="a0f0c-134">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="a0f0c-135">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a0f0c-136">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="a0f0c-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a0f0c-137">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="a0f0c-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a0f0c-138">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="a0f0c-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a0f0c-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="a0f0c-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a0f0c-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a0f0c-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a0f0c-141">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="a0f0c-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a0f0c-142">为 Azure 和 Azure 智能机器人应用程序检索的 Internet 访问。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="a0f0c-143">有关详细信息[请单击以下链接](https://dev.botframework.com/)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="a0f0c-144">开始之前</span><span class="sxs-lookup"><span data-stu-id="a0f0c-144">Before you start</span></span>

1.  <span data-ttu-id="a0f0c-145">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="a0f0c-146">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="a0f0c-147">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="a0f0c-148">它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="a0f0c-149">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="a0f0c-150">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="a0f0c-151">第 1 章 – 创建智能机器人应用程序</span><span class="sxs-lookup"><span data-stu-id="a0f0c-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="a0f0c-152">第一步是创建为本地 ASP.Net Core Web 应用程序智能机器人。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="a0f0c-153">一旦完成并对其进行测试后，会将其发布到 Azure 门户。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="a0f0c-154">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-154">Open Visual Studio.</span></span> <span data-ttu-id="a0f0c-155">创建新项目，选择**ASP NET Core Web 应用程序**作为项目类型 （它会在.NET Core 的子节下），并调用它**MyBot**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="a0f0c-156">单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-156">Click **OK**.</span></span>

2.  <span data-ttu-id="a0f0c-157">选择将显示在窗口中**空**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="a0f0c-158">此外请确保目标设置为**ASP NET Core 2.0**和身份验证设置为**无身份验证**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="a0f0c-159">单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-159">Click **OK**.</span></span>  

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="a0f0c-161">现在将打开该解决方案。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-161">The solution will now open.</span></span> <span data-ttu-id="a0f0c-162">右键单击解决方案**Mybot**中**解决方案资源管理器**，然后单击**为解决方案管理 NuGet 包**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="a0f0c-164">在**浏览**选项卡上，搜索**Microsoft.Bot.Builder.Integration.AspNet.Core** (请确保您拥有**包括预发行版**检查)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="a0f0c-165">选择的包版本**4.0.1-preview**，并选中项目框。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="a0f0c-166">然后单击**安装**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-166">Then click on **Install**.</span></span> <span data-ttu-id="a0f0c-167">您现在已安装所需的库**Bot Framework v4**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="a0f0c-168">关闭 NuGet 页。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-168">Close the NuGet page.</span></span>

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="a0f0c-170">右键单击你*项目*， **MyBot**，在 **解决方案资源管理器**，然后单击 **添加** **|** **类**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="a0f0c-172">将类命名**MyBot** ，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="a0f0c-174">重复上一个点，以创建名为的另一个类**ConversationContext**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="a0f0c-175">右键单击**wwwroot**中**解决方案资源管理器**，然后单击**添加** **|** **新项**.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="a0f0c-176">选择**HTML 页**（它会在子节 Web 下）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="a0f0c-177">将文件命名**default.html**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-177">Name the file **default.html**.</span></span> <span data-ttu-id="a0f0c-178">单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-178">Click **Add**.</span></span>

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="a0f0c-180">类的列表中的对象 /**解决方案资源管理器**应如下图所示。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="a0f0c-182">双击**ConversationContext**类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="a0f0c-183">此类负责保存智能机器人应用程序用于维护该会话的上下文的变量。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="a0f0c-184">因为，这些会话上下文值将保留在此类的实例中的任何实例**MyBot**类将刷新每次收到活动。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="a0f0c-185">将以下代码添加到类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="a0f0c-186">双击**MyBot**类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="a0f0c-187">此类将托管客户从调用的任何传入活动的处理程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="a0f0c-188">在此类将添加用于生成智能机器人应用程序与客户之间的会话的代码。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="a0f0c-189">前面曾提到，初始化此类的实例每次收到活动。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="a0f0c-190">将以下代码添加到此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="a0f0c-191">双击**启动**类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="a0f0c-192">此类将初始化智能机器人应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-192">This class will initialize the bot.</span></span> <span data-ttu-id="a0f0c-193">将以下代码添加到类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="a0f0c-194">打开**程序**类文件，并验证是否在其代码是相同的如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="a0f0c-195">请记住保存所做的更改，为此，请转到**文件** > **全部保存**，Visual Studio 顶部工具栏中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="a0f0c-196">章 2-创建 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="a0f0c-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="a0f0c-197">既然您已经针对自动程序生成代码，您必须将其发布到的实例*Web App 机器人*服务，在 Azure 门户上的。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="a0f0c-198">这一章将演示如何创建和配置 Azure 上的智能机器人应用程序服务和然后将代码发布到它。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="a0f0c-199">首先，登录到 Azure 门户 (https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="a0f0c-200">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a0f0c-201">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="a0f0c-202">你登录后，单击**创建资源**在左上角，并搜索*Web App 机器人*，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="a0f0c-204">该新页面将提供的说明*Web App 机器人*服务。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="a0f0c-205">在左下角此页上，选择**创建**按钮，以创建与此关联服务。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="a0f0c-207">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="a0f0c-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="a0f0c-208">插入所需**名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="a0f0c-209">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="a0f0c-210">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a0f0c-211">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a0f0c-212">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="a0f0c-213">如果你想要阅读更多有关 Azure 资源组，[请访问以下链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="a0f0c-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="a0f0c-214">（如果要创建新的资源组） 确定你的资源组的位置。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="a0f0c-215">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="a0f0c-216">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="a0f0c-217">选择**定价层**适合您，如果这是第一个时间来创建*Web App 机器人*服务，应可供你免费层 （名为 F0）</span><span class="sxs-lookup"><span data-stu-id="a0f0c-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="a0f0c-218">**应用名称**可以只在相同*智能机器人应用程序名称*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="a0f0c-219">将保留*智能机器人应用程序模板*作为**基本 (C#)**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="a0f0c-220">*应用服务计划/位置*应该已自动填充为你的帐户。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="a0f0c-221">设置**Azure 存储**你想要使用托管在智能机器人应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="a0f0c-222">如果你还没有，可以在此处创建它。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="a0f0c-223">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="a0f0c-224">单击创建。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-224">Click Create.</span></span>
 
        ![创建 Azure 机器人服务](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="a0f0c-226">一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="a0f0c-227">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="a0f0c-229">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-229">Click on the notification to explore your new Service instance.</span></span> 

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="a0f0c-231">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="a0f0c-232">你将转到新的 Azure 服务实例。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-232">You will be taken to your new Azure Service instance.</span></span> 

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="a0f0c-234">此时，你需要设置名为的功能**Direct Line**以允许客户端应用程序与此智能机器人应用程序服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="a0f0c-235">单击**通道**，然后在**添加特色的频道**部分中，单击**配置 Direct Line 通道**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="a0f0c-237">在此页中将查找**机密密钥**，将允许客户端应用程序，以使用智能机器人应用程序进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="a0f0c-238">单击**显示**按钮，然后将会更高版本中您的项目需要它时所采取的显示密钥中的一个副本。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="a0f0c-240">第 3 – 章将智能机器人应用程序发布到 Azure Web App 机器人服务</span><span class="sxs-lookup"><span data-stu-id="a0f0c-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="a0f0c-241">现在，你的服务已准备就绪，您需要将智能机器人应用程序代码，以前，构建到您新创建的 Web 应用程序智能机器人应用程序服务的发布。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="a0f0c-242">必须将智能机器人发布到 Azure 服务，每次对智能机器人应用程序解决方案进行更改时 o。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="a0f0c-243">返回到以前创建的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="a0f0c-244">右键单击你**MyBot**项目，在**解决方案资源管理器**，然后单击**发布**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="a0f0c-246">上*选取发布目标*页上，单击**应用服务**，然后**选择现有**，最后单击**创建配置文件**（您可能需要单击旁边的下拉箭头*发布*按钮，则此项不可见)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="a0f0c-248">如果您尚未登录到你的 Microsoft 帐户，你必须在这里完成。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="a0f0c-249">上**发布**您会发现有设置相同的页面**订阅**用于*Web App 机器人*服务创建。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="a0f0c-250">然后设置**视图**作为**资源组**，然后在下拉列表文件夹结构中，选中**资源组**之前创建。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="a0f0c-251">单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-251">Click **OK**.</span></span> 

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="a0f0c-253">现在，单击**发布**按钮，并等待智能机器人应用程序要发布 （可能需要几分钟时间）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="a0f0c-255">第 4 章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="a0f0c-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="a0f0c-256">以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a0f0c-257">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-257">Open *Unity* and click **New**.</span></span> 

    ![设置 Unity 项目](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="a0f0c-259">现在，需要提供的 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="a0f0c-260">插入**Hololens 机器人**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="a0f0c-261">请确保项目模板设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="a0f0c-262">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a0f0c-263">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-263">Then, click **Create project**.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="a0f0c-265">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a0f0c-266">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a0f0c-267">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a0f0c-268">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-268">Close the **Preferences** window.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="a0f0c-270">接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="a0f0c-272">在仍处于**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="a0f0c-273">**设备为目标**设置为**Hololens**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="a0f0c-274">对于沉浸式耳机，设置**目标设备**到*任一设备*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="a0f0c-275">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="a0f0c-276">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="a0f0c-277">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="a0f0c-278">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="a0f0c-279">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="a0f0c-280">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a0f0c-281">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-281">A save window will appear.</span></span>
        
            ![设置 Unity 项目](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="a0f0c-283">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![设置 Unity 项目](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="a0f0c-285">打开新建**场景**文件夹，然后在*文件的名称*： 文本字段中，键入**BotScene**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="a0f0c-287">中的剩余设置，**生成设置**，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="a0f0c-288">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![设置 Unity 项目](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="a0f0c-290">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="a0f0c-291">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="a0f0c-292">**脚本运行时版本**应 **（NET 4.6 等效） 的实验性**; 更改这将需要重新启动编辑器中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="a0f0c-293">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="a0f0c-294">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="a0f0c-296">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a0f0c-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-297">**InternetClient**</span></span>
        - <span data-ttu-id="a0f0c-298">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-298">**Microphone**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="a0f0c-300">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="a0f0c-302">回到*生成设置* _Unity C#_ 项目不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="a0f0c-303">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="a0f0c-304">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="a0f0c-305">第 5 章-照相机设置</span><span class="sxs-lookup"><span data-stu-id="a0f0c-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0f0c-306">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 7 章](#chapter-7-–-create-the-botobjects-class)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="a0f0c-307">在中*层次结构面板*，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="a0f0c-308">选择后，你将能够看到的所有组件**Main Camera**中*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="a0f0c-309">**相机对象**必须命名为**Main Camera** （请注意拼写）</span><span class="sxs-lookup"><span data-stu-id="a0f0c-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="a0f0c-310">Main Camera**标记**必须设置为**MainCamera** （请注意拼写）</span><span class="sxs-lookup"><span data-stu-id="a0f0c-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="a0f0c-311">请确保**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="a0f0c-312">设置**清除标志**到**纯色**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="a0f0c-313">设置**背景**照相机组件到色**黑色、 Alpha 0 (十六进制代码: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![照相机设置](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="a0f0c-315">第 6 章-导入 Newtonsoft 库</span><span class="sxs-lookup"><span data-stu-id="a0f0c-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="a0f0c-316">若要帮助您反序列化和序列化对象接收和发送到机器人服务需要下载**Newtonsoft**库。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="a0f0c-317">您会发现[兼容的版本与此处正确的 Unity 文件夹结构已组织](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="a0f0c-318">若要 Newtonsoft 库导入到你的项目，使用了随附此课程的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="a0f0c-319">添加 *.unitypackage*到使用 Unity**资产** > **导入包** > **自定义包**菜单选项。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![导入 Newtonsoft 库](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="a0f0c-321">在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![导入 Newtonsoft 库](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="a0f0c-323">单击**导入**按钮将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="a0f0c-324">转到**Newtonsoft**下的文件夹**插件**在项目视图中，选择 Newtonsoft 插件。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="a0f0c-325">使用所选 Newtonsoft 插件，请确保**Any 平台**是**取消选中**，然后确保**WSAPlayer**也是**未选中**，然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="a0f0c-326">这只是为了确认正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="a0f0c-327">将标记这些插件将它们配置为仅使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="a0f0c-328">有一组不同的它们从 Unity 项目会导出后，将使用 WSA 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="a0f0c-329">接下来，您需要打开**WSA**文件夹，在**Newtonsoft**文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="a0f0c-330">您将看到刚配置的相同文件的副本。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="a0f0c-331">选择的文件，然后在检查器中，确保的</span><span class="sxs-lookup"><span data-stu-id="a0f0c-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="a0f0c-332">**任何平台**是**未选中状态**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="a0f0c-333">**仅** **WSAPlayer**是**检查**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="a0f0c-334">**不处理**是**检查**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="a0f0c-335">第 7 – 章创建 BotTag</span><span class="sxs-lookup"><span data-stu-id="a0f0c-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="a0f0c-336">创建一个新**标记**对象调用**BotTag**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="a0f0c-337">选择场景中的 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="a0f0c-338">单击标记下拉列表中的检查器面板菜单。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="a0f0c-339">单击**将标记添加**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-339">Click on **Add Tag**.</span></span>

    ![照相机设置](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="a0f0c-341">单击 **+** 符号。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-341">Click on the **+** symbol.</span></span> <span data-ttu-id="a0f0c-342">指定新**标记**作为**BotTag**，*保存*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![照相机设置](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="a0f0c-344">**不这样做**应用**BotTag**到 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="a0f0c-345">如果已意外地执行此操作，请确保更改标记返回到 Main Camera *MainCamera*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="a0f0c-346">第 8 章 – 创建 BotObjects 类</span><span class="sxs-lookup"><span data-stu-id="a0f0c-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="a0f0c-347">您需要创建的第一个脚本是**BotObjects**类，该类是创建一系列的其他类对象可存储在同一个脚本和其他脚本场景中访问的空类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="a0f0c-348">此类的创建是纯粹的体系结构的选择，这些对象可以改为托管，你将稍后在本课程中创建的智能机器人应用程序脚本中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="a0f0c-349">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-349">To create this class:</span></span> 

1.  <span data-ttu-id="a0f0c-350">在中右击*项目面板*，然后**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="a0f0c-351">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-351">Name the folder **Scripts**.</span></span> 

    ![创建脚本的文件夹。](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="a0f0c-353">双击**脚本**文件夹将其打开。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="a0f0c-354">然后在该文件夹，右键单击，并选择**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="a0f0c-355">脚本命名为**BotObjects**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="a0f0c-356">双击新**BotObjects**脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="a0f0c-357">删除脚本的内容，并使用以下代码替换它：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="a0f0c-358">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="a0f0c-359">第 9 章 – 创建 GazeInput 类</span><span class="sxs-lookup"><span data-stu-id="a0f0c-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="a0f0c-360">要创建的下一步类是**GazeInput**类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="a0f0c-361">此类负责：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-361">This class is responsible for:</span></span>

- <span data-ttu-id="a0f0c-362">表示将创建游标*注视*的播放机。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="a0f0c-363">检测的播放机中，提供注视被命中的对象和保存对检测到的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="a0f0c-364">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-364">To create this class:</span></span> 

1.  <span data-ttu-id="a0f0c-365">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="a0f0c-366">在文件夹中，右键单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="a0f0c-367">调用脚本**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="a0f0c-368">双击新**GazeInput**脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="a0f0c-369">插入类名的右侧顶部的以下行：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="a0f0c-370">然后添加以下变量内的**GazeInput**类，更高版本**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="a0f0c-371">为代码**start （)** 应添加方法。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="a0f0c-372">类初始化时，这将会调用：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="a0f0c-373">实现将实例化和设置的视线移动游标的方法：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="a0f0c-374">实现的方法，将在安装程序从 Main Camera Raycast 和跟踪的当前具有焦点的对象。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="a0f0c-375">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="a0f0c-376">第 10 章 – 创建智能机器人应用程序类</span><span class="sxs-lookup"><span data-stu-id="a0f0c-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="a0f0c-377">要创建的脚本现在称为**机器人**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="a0f0c-378">这是你的应用程序的核心类，它将存储：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="a0f0c-379">你的 Web 应用程序智能机器人应用程序凭据</span><span class="sxs-lookup"><span data-stu-id="a0f0c-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="a0f0c-380">方法，收集用户语音命令</span><span class="sxs-lookup"><span data-stu-id="a0f0c-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="a0f0c-381">若要启动会话的 Web 应用程序智能机器人，所需的方法</span><span class="sxs-lookup"><span data-stu-id="a0f0c-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="a0f0c-382">若要将消息发送到 Web 应用程序智能机器人，所需的方法</span><span class="sxs-lookup"><span data-stu-id="a0f0c-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="a0f0c-383">若要将消息发送到 Bot Service **SendMessageToBot()** 协同程序将生成活动，这是识别智能机器人应用程序框架为用户发送的数据的对象。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="a0f0c-384">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-384">To create this class:</span></span> 

1. <span data-ttu-id="a0f0c-385">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="a0f0c-386">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="a0f0c-387">脚本命名为**机器人**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="a0f0c-388">双击要使用 Visual Studio 中打开的新脚本。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="a0f0c-389">更新命名空间，如下所示，在顶部相同**机器人**类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="a0f0c-390">内部**机器人**类添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="a0f0c-391">请确保插入你**智能机器人应用程序机密密钥**成**botSecret**变量。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="a0f0c-392">你将已记下你 **智能机器人应用程序机密密钥** 在本课程中，开头中 **[第 2 章](#chapter-2---create-the-azure-bot-service)，第 10 步** 。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="a0f0c-393">为代码**Awake()** 并**start （)** 现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="a0f0c-394">添加两个处理程序在语音捕获开始和结束时调用由语音库。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="a0f0c-395">*DictationRecognizer*将自动停止捕获用户之声，当用户停止说到。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="a0f0c-396">下面的处理程序收集用户语音输入的结果，并调用协同程序负责将消息发送到 Web 应用智能机器人应用程序服务。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="a0f0c-397">下面的协同例程调用以开始与智能机器人应用程序的会话。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="a0f0c-398">你会注意到，会话调用完成后，它将调用**SendMessageToCoroutine()** 表示通过一系列将设置要发送到 Bot 服务作为一条空消息的活动的参数。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="a0f0c-399">这样做是为了提示要启动对话的智能机器人应用程序服务。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="a0f0c-400">下面的协同例程调用以生成要发送到机器人服务的活动。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="a0f0c-401">下面的协同例程调用以将活动发送到智能机器人应用程序服务后请求响应。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="a0f0c-402">场景中显示该消息所需的最后一个方法添加到此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="a0f0c-403">您可能会看到一个在 Unity 编辑器控制台中，有关缺少**SceneOrganiser**类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="a0f0c-404">忽略此消息，因为将稍后在本教程中创建此类。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="a0f0c-405">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="a0f0c-406">第 11 章 – 创建交互类</span><span class="sxs-lookup"><span data-stu-id="a0f0c-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="a0f0c-407">要创建此类现被称为**交互**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="a0f0c-408">此类用于检测来自用户的 HoloLens 点击输入。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="a0f0c-409">如果用户点击时查看*机器人*场景和智能机器人应用程序中的对象已准备好侦听语音输入，智能机器人应用程序对象将更改颜色**红色**并开始侦听语音输入。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="a0f0c-410">此类继承自**GazeInput**类，并因此是能够引用**start （)** 方法，并从该类，表示通过使用变量**基**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="a0f0c-411">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-411">To create this class:</span></span>

1.  <span data-ttu-id="a0f0c-412">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="a0f0c-413">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="a0f0c-414">脚本命名为**交互**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="a0f0c-415">双击要使用 Visual Studio 中打开的新脚本。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="a0f0c-416">更新命名空间和类继承，如下所示，在顶部相同**交互**类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="a0f0c-417">内部**交互**类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="a0f0c-418">然后添加**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="a0f0c-419">添加用户执行点击手势 HoloLens 照相机的前面时，将触发该处理程序</span><span class="sxs-lookup"><span data-stu-id="a0f0c-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="a0f0c-420">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="a0f0c-421">第 12 章 – 创建 SceneOrganiser 类</span><span class="sxs-lookup"><span data-stu-id="a0f0c-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="a0f0c-422">在此实验中所需的最后一个类称为**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="a0f0c-423">此类将在安装程序场景以编程方式，通过将组件和脚本添加到 Main Camera，并在场景中创建相应的对象。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="a0f0c-424">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-424">To create this class:</span></span>

1.  <span data-ttu-id="a0f0c-425">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="a0f0c-426">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="a0f0c-427">脚本命名为**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="a0f0c-428">双击要使用 Visual Studio 中打开的新脚本。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="a0f0c-429">内部**SceneOrganiser**类添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="a0f0c-430">然后添加**Awake()** 并**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="a0f0c-431">添加以下方法，负责在场景中创建智能机器人应用程序对象和设置参数和组件：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="a0f0c-432">添加以下方法，负责创建 UI 对象在场景中，表示从智能机器人应用程序的响应：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="a0f0c-433">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="a0f0c-434">在 Unity 编辑器中，拖动**SceneOrganiser**到 Main Camera 脚本文件夹中的脚本。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="a0f0c-435">Main Camera 对象上现在应显示场景组织者组件，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="a0f0c-437">第 13 章 – 生成前</span><span class="sxs-lookup"><span data-stu-id="a0f0c-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="a0f0c-438">若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="a0f0c-439">执行操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="a0f0c-440">中所述的所有设置[**第 4 章**](#Chapter-4-–-Set-up-the-unity-project)正确设置。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="a0f0c-441">该脚本**SceneOrganiser**附加到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="a0f0c-442">在**机器人**类中，请确保已插入您**智能机器人应用程序机密密钥**到**botSecret**变量。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="a0f0c-443">第 14 章 – 生成和旁的加载到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="a0f0c-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="a0f0c-444">此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="a0f0c-445">导航到**生成设置**，**文件 > 生成设置...**.</span><span class="sxs-lookup"><span data-stu-id="a0f0c-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="a0f0c-446">从**生成设置**窗口中，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-446">From the **Build Settings** window, click **Build**.</span></span>

    ![从 Unity 构建应用程序](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="a0f0c-448">如果尚不存在，则勾选**UnityC#项目**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="a0f0c-449">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-449">Click **Build**.</span></span> <span data-ttu-id="a0f0c-450">将启动 unity**文件资源管理器**窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="a0f0c-451">现在，创建该文件夹并将其命名**应用**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="a0f0c-452">然后使用**应用程序**文件夹选择，单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="a0f0c-453">Unity 将开始构建您的项目**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="a0f0c-454">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="a0f0c-455">章 15-将部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="a0f0c-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="a0f0c-456">若要部署在 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="a0f0c-457">你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="a0f0c-458">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-458">To do this:</span></span>

    1. <span data-ttu-id="a0f0c-459">戴上您 HoloLens，同时打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="a0f0c-460">转到**网络和 Internet > 的 Wi-fi > 高级选项**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="a0f0c-461">请注意**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="a0f0c-462">接下来，导航回到**设置**，然后**更新和安全 > 适用于开发人员**</span><span class="sxs-lookup"><span data-stu-id="a0f0c-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="a0f0c-463">设置开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="a0f0c-464">导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="a0f0c-465">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="a0f0c-466">在中**解决方案平台**，选择**x86**，**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="a0f0c-468">转到**生成菜单**，然后单击**部署解决方案**旁, 加载到你 HoloLens 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="a0f0c-469">在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！</span><span class="sxs-lookup"><span data-stu-id="a0f0c-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="a0f0c-470">若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="a0f0c-471">然后将其部署到本地计算机，使用**生成菜单**，选择*部署解决方案*。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="a0f0c-472">第 16 章 – 在 HoloLens 上使用应用程序</span><span class="sxs-lookup"><span data-stu-id="a0f0c-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="a0f0c-473">一旦启动该应用程序，您将看到在您面前蓝色球体智能机器人应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="a0f0c-474">使用**点击手势**时观望在球体，若要启动的会话。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="a0f0c-475">等待会话启动 （的 UI 将显示一条消息时都是这样）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="a0f0c-476">一旦从智能机器人应用程序接收的介绍性消息，再次点击上智能机器人应用程序以便它将变为红色，并开始侦听语音。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="a0f0c-477">在停止通信后，你的应用程序将在消息发送到智能机器人应用程序并立即将收到一个响应，它将显示在 UI 中。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="a0f0c-478">重复该过程以将更多的消息发送到智能机器人 （您需要点击每次想发送一条消息的时）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="a0f0c-479">此会话演示如何智能机器人应用程序可以保留信息 （你的名称），同时还提供已知的信息 （如所存储的项）。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="a0f0c-480">要让机器人的一些问题：</span><span class="sxs-lookup"><span data-stu-id="a0f0c-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="a0f0c-481">完成的 Web 应用程序智能机器人应用程序 (v4) 应用程序</span><span class="sxs-lookup"><span data-stu-id="a0f0c-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="a0f0c-482">祝贺你，构建利用 Azure Web App 机器人、 Microsoft Bot Framework v4 的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![最终产品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="a0f0c-484">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="a0f0c-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="a0f0c-485">练习 1</span><span class="sxs-lookup"><span data-stu-id="a0f0c-485">Exercise 1</span></span>

<span data-ttu-id="a0f0c-486">在此实验中的会话结构是非常基本的。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="a0f0c-487">使用 Microsoft LUIS 为智能机器人提供自然语言理解功能。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="a0f0c-488">练习 2</span><span class="sxs-lookup"><span data-stu-id="a0f0c-488">Exercise 2</span></span>

<span data-ttu-id="a0f0c-489">此示例不包括终止会话并重新启动一个新。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="a0f0c-490">若要使功能完成的智能机器人应用程序，请尝试实现的对话，闭包。</span><span class="sxs-lookup"><span data-stu-id="a0f0c-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
