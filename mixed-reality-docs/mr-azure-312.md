---
title: MR 和 Azure 312-机器人集成
description: 完成本课程，了解如何使用 Microsoft Bot Framework v4 创建和部署 bot，并在混合现实应用程序中与其通信。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，计算机视觉，hololens，沉浸，vr，microsoft bot framework v4，web 应用机器人，bot framework，microsoft 机器人
ms.openlocfilehash: dc428f01a8333bf812fe03c59a46b7a2fa20df83
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438484"
---
>[!NOTE]
><span data-ttu-id="e2f37-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e2f37-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="e2f37-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e2f37-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="e2f37-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e2f37-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="e2f37-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e2f37-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="e2f37-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e2f37-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="e2f37-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="e2f37-110">MR 和 Azure 312：机器人集成</span><span class="sxs-lookup"><span data-stu-id="e2f37-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="e2f37-111">在本课程中，你将了解如何使用 Microsoft Bot Framework V4 创建和部署机器人，并通过 Windows Mixed Reality 应用程序与它进行通信。</span><span class="sxs-lookup"><span data-stu-id="e2f37-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="e2f37-112">**Microsoft 机器人 Framework V4**是一组 api，旨在向开发人员提供用于构建可扩展、可缩放机器人应用程序的工具。</span><span class="sxs-lookup"><span data-stu-id="e2f37-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="e2f37-113">有关详细信息，请访问[Microsoft Bot Framework 页](https://dev.botframework.com/)或[V4 Git 存储库](https://github.com/Microsoft/botbuilder-dotnet/wiki)。</span><span class="sxs-lookup"><span data-stu-id="e2f37-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="e2f37-114">完成本课程后，你将构建一个 Windows Mixed Reality 应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e2f37-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="e2f37-115">使用**点击手势**启动机器人来侦听用户语音。</span><span class="sxs-lookup"><span data-stu-id="e2f37-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="e2f37-116">如果用户已提到某些内容，机器人会尝试提供响应。</span><span class="sxs-lookup"><span data-stu-id="e2f37-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="e2f37-117">在 Unity 场景中，在机器人附近显示 "bot 回复" 作为文本。</span><span class="sxs-lookup"><span data-stu-id="e2f37-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="e2f37-118">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="e2f37-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="e2f37-119">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="e2f37-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="e2f37-120">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="e2f37-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="e2f37-121">设备支持</span><span class="sxs-lookup"><span data-stu-id="e2f37-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e2f37-122">摘要</span><span class="sxs-lookup"><span data-stu-id="e2f37-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e2f37-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e2f37-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e2f37-124"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="e2f37-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e2f37-125">MR 和 Azure 312：机器人集成</span><span class="sxs-lookup"><span data-stu-id="e2f37-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="e2f37-126">✔️</span><span class="sxs-lookup"><span data-stu-id="e2f37-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e2f37-127">✔️</span><span class="sxs-lookup"><span data-stu-id="e2f37-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="e2f37-128">尽管本课程主要侧重于 HoloLens，但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸（VR）耳机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="e2f37-129">由于沉浸式（VR）耳机没有可访问的摄像机，因此需要连接到电脑的外部照相机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="e2f37-130">在本课程中，您将看到有关支持沉浸式（VR）耳机时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="e2f37-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2f37-131">必备条件</span><span class="sxs-lookup"><span data-stu-id="e2f37-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="e2f37-132">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="e2f37-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="e2f37-133">另外，请注意，本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容（2018年7月）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="e2f37-134">你可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="e2f37-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="e2f37-135">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="e2f37-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="e2f37-136">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="e2f37-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="e2f37-137">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="e2f37-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e2f37-138">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="e2f37-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e2f37-139">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="e2f37-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e2f37-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e2f37-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="e2f37-141">启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="e2f37-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="e2f37-142">Azure 和 Azure 机器人检索的 Internet 访问。</span><span class="sxs-lookup"><span data-stu-id="e2f37-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="e2f37-143">有关详细信息，[请访问此链接](https://dev.botframework.com/)。</span><span class="sxs-lookup"><span data-stu-id="e2f37-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="e2f37-144">开始之前</span><span class="sxs-lookup"><span data-stu-id="e2f37-144">Before you start</span></span>

1.  <span data-ttu-id="e2f37-145">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="e2f37-146">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e2f37-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="e2f37-147">如果需要支持设置 HoloLens，请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="e2f37-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="e2f37-148">在开始开发新的 HoloLens 应用程序时，最好执行校准和传感器调整（有时它可以帮助为每个用户执行这些任务）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="e2f37-149">有关校准的帮助信息，请单击此链接，了解[到 HoloLens 校准文章](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="e2f37-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="e2f37-150">有关传感器优化的帮助，请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f37-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="e2f37-151">第1章–创建机器人应用程序</span><span class="sxs-lookup"><span data-stu-id="e2f37-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="e2f37-152">第一步是创建机器人作为本地 ASP.Net Core Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="e2f37-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="e2f37-153">完成并测试后，将其发布到 Azure 门户。</span><span class="sxs-lookup"><span data-stu-id="e2f37-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="e2f37-154">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e2f37-154">Open Visual Studio.</span></span> <span data-ttu-id="e2f37-155">创建一个新项目，选择 " **ASP NET Core Web 应用程序**" 作为项目类型（你将在 ".net core" 部分下找到），并**MyBot**调用它。</span><span class="sxs-lookup"><span data-stu-id="e2f37-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="e2f37-156">单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-156">Click **OK**.</span></span>

2.  <span data-ttu-id="e2f37-157">在将显示的窗口中选择 "**空**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="e2f37-158">此外，请确保将目标设置为**ASP NET Core 2.0** ，并将身份验证设置为 "**无身份验证**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="e2f37-159">单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-159">Click **OK**.</span></span>  

    ![创建机器人应用程序](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="e2f37-161">解决方案现在将打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-161">The solution will now open.</span></span> <span data-ttu-id="e2f37-162">右键单击 "**解决方案资源管理器**中的" 解决方案**Mybot** "，然后单击"**管理解决方案的 NuGet 包**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![创建机器人应用程序](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="e2f37-164">在 "**浏览**" 选项卡中，搜索 ""，并确保已选中 "**包括预发行版** **"。**</span><span class="sxs-lookup"><span data-stu-id="e2f37-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="e2f37-165">选择包版本**4.0.1-预览**，并勾选项目框。</span><span class="sxs-lookup"><span data-stu-id="e2f37-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="e2f37-166">然后单击 "**安装**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-166">Then click on **Install**.</span></span> <span data-ttu-id="e2f37-167">你现在已安装了**Bot Framework v4**所需的库。</span><span class="sxs-lookup"><span data-stu-id="e2f37-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="e2f37-168">关闭 NuGet 页。</span><span class="sxs-lookup"><span data-stu-id="e2f37-168">Close the NuGet page.</span></span>

    ![创建机器人应用程序](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="e2f37-170">右键单击*项目*" **MyBot**"，在 "**解决方案资源管理器**"，然后单击 "**添加** **|** **类**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![创建机器人应用程序](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="e2f37-172">将类命名为**MyBot** ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![创建机器人应用程序](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="e2f37-174">重复上述步骤，以创建名为**ConversationContext**的另一个类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="e2f37-175">右键单击 "**解决方案资源管理器**中的**wwwroot** ，然后单击"**添加** **|** **新项**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="e2f37-176">选择 " **HTML 页**" （你将在 "Web" 子部分下发现）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="e2f37-177">将文件命名为 **.html**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-177">Name the file **default.html**.</span></span> <span data-ttu-id="e2f37-178">单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-178">Click **Add**.</span></span>

    ![创建机器人应用程序](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="e2f37-180">**解决方案资源管理器**中的类/对象的列表应类似于下图。</span><span class="sxs-lookup"><span data-stu-id="e2f37-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![创建机器人应用程序](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="e2f37-182">双击 " **ConversationContext** " 类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="e2f37-183">此类负责保存机器人用于维护会话上下文的变量。</span><span class="sxs-lookup"><span data-stu-id="e2f37-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="e2f37-184">这些会话上下文值在此类的实例中维护，因为每次收到活动时， **MyBot**类的任何实例都将刷新。</span><span class="sxs-lookup"><span data-stu-id="e2f37-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="e2f37-185">将下面的代码添加到类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="e2f37-186">双击 " **MyBot** " 类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="e2f37-187">此类将承载来自客户的任何传入活动所调用的处理程序。</span><span class="sxs-lookup"><span data-stu-id="e2f37-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="e2f37-188">在此类中，你将添加用于构建机器人和客户之间的会话的代码。</span><span class="sxs-lookup"><span data-stu-id="e2f37-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="e2f37-189">如前文所述，每次收到活动时都会初始化此类的实例。</span><span class="sxs-lookup"><span data-stu-id="e2f37-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="e2f37-190">将以下代码添加到此类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="e2f37-191">双击**Startup**类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="e2f37-192">此类将初始化机器人。</span><span class="sxs-lookup"><span data-stu-id="e2f37-192">This class will initialize the bot.</span></span> <span data-ttu-id="e2f37-193">将下面的代码添加到类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="e2f37-194">打开**Program**类文件，验证其中的代码与以下代码相同：</span><span class="sxs-lookup"><span data-stu-id="e2f37-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="e2f37-195">记住要保存所做的更改，若要执行此操作，请从 Visual Studio 顶部的工具栏中的 "**文件** > "**全部保存**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="e2f37-196">第2章-创建 Azure Bot 服务</span><span class="sxs-lookup"><span data-stu-id="e2f37-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="e2f37-197">既然已经为机器人生成了代码，就必须将其发布到 Azure 门户上的*Web 应用机器人*服务的实例。</span><span class="sxs-lookup"><span data-stu-id="e2f37-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="e2f37-198">本章介绍如何在 Azure 上创建和配置机器人服务，然后将代码发布到该服务。</span><span class="sxs-lookup"><span data-stu-id="e2f37-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="e2f37-199">首先，登录到 Azure 门户（ https://portal.azure.com) 。</span><span class="sxs-lookup"><span data-stu-id="e2f37-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="e2f37-200">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="e2f37-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="e2f37-201">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="e2f37-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="e2f37-202">登录后，单击左上角的 "**创建资源**"，搜索 " *Web 应用程序*"，然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="e2f37-204">新页面将提供*Web 应用机器人*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="e2f37-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="e2f37-205">在此页的左下角，选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="e2f37-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="e2f37-207">单击 "**创建**" 后：</span><span class="sxs-lookup"><span data-stu-id="e2f37-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="e2f37-208">为此服务实例插入所需的**名称**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="e2f37-209">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="e2f37-210">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="e2f37-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="e2f37-211">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="e2f37-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="e2f37-212">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="e2f37-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="e2f37-213">若要了解有关 Azure 资源组的详细信息，[请访问此链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="e2f37-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="e2f37-214">确定资源组的位置（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="e2f37-215">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="e2f37-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="e2f37-216">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="e2f37-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="e2f37-217">选择适合你的**定价层**，如果这是第一次创建*Web 应用机器人*服务，则你应该可以使用免费层（名为 F0）</span><span class="sxs-lookup"><span data-stu-id="e2f37-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="e2f37-218">**应用名称**可以与*Bot 名称*相同。</span><span class="sxs-lookup"><span data-stu-id="e2f37-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="e2f37-219">将*机器人模板*保留为 "**基本C#" （）** 。</span><span class="sxs-lookup"><span data-stu-id="e2f37-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="e2f37-220">应已为你的帐户自动填写*应用服务计划/位置*。</span><span class="sxs-lookup"><span data-stu-id="e2f37-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="e2f37-221">设置要用于托管机器人的**Azure 存储**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="e2f37-222">如果还没有，可以在此处创建一个。</span><span class="sxs-lookup"><span data-stu-id="e2f37-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="e2f37-223">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="e2f37-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="e2f37-224">单击 "创建"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-224">Click Create.</span></span>
 
        ![创建 Azure Bot 服务](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="e2f37-226">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="e2f37-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="e2f37-227">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="e2f37-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="e2f37-229">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="e2f37-229">Click on the notification to explore your new Service instance.</span></span> 

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="e2f37-231">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="e2f37-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="e2f37-232">你将转到新的 Azure 服务实例。</span><span class="sxs-lookup"><span data-stu-id="e2f37-232">You will be taken to your new Azure Service instance.</span></span> 

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="e2f37-234">此时，你需要设置一个称为 "**直接连线**" 的功能，以允许客户端应用程序与此 Bot 服务通信。</span><span class="sxs-lookup"><span data-stu-id="e2f37-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="e2f37-235">单击 "**频道**"，然后在 "**添加特色频道**" 部分中，单击 "**配置直接连线通道**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="e2f37-237">在此页中，你将找到允许客户端应用程序通过机器人进行身份验证的**机密密钥**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="e2f37-238">单击 "**显示**" 按钮，然后复制其中一个所显示的密钥，因为稍后会在项目中使用此项。</span><span class="sxs-lookup"><span data-stu-id="e2f37-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="e2f37-240">第3章–将机器人发布到 Azure Web 应用机器人服务</span><span class="sxs-lookup"><span data-stu-id="e2f37-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="e2f37-241">现在，你的服务已准备就绪，你需要将你之前构建的机器人代码发布到新创建的 Web 应用机器人服务。</span><span class="sxs-lookup"><span data-stu-id="e2f37-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="e2f37-242">每次更改机器人解决方案/代码时，都必须将机器人发布到 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="e2f37-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="e2f37-243">返回到你之前创建的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="e2f37-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="e2f37-244">右键单击 " **MyBot** " 项目，在 "**解决方案资源管理器**"，然后单击 "**发布**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="e2f37-246">在 "*选取发布目标*" 页上，单击 "**应用服务**"，然后**选择 "现有**"，最后单击 "**创建配置文件**" （如果不可见，则可能需要单击 "*发布*" 按钮旁的下拉箭头）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="e2f37-248">如果尚未登录到 Microsoft 帐户，则必须在此处执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e2f37-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="e2f37-249">在 "**发布**" 页上，你将发现你必须设置用于*Web 应用程序机器人*服务创建的同一**订阅**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="e2f37-250">然后，将 "**视图**" 设置为 "**资源组**"，并在下拉文件夹结构中，选择之前创建的**资源组**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="e2f37-251">单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-251">Click **OK**.</span></span> 

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="e2f37-253">现在，单击 "**发布**" 按钮，并等待机器人发布（可能需要几分钟时间）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="e2f37-255">第4章–设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="e2f37-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="e2f37-256">下面是用于使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="e2f37-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="e2f37-257">打开*Unity* ，并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-257">Open *Unity* and click **New**.</span></span> 

    ![设置 Unity 项目](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="e2f37-259">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="e2f37-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="e2f37-260">插入**HoloLens 机器人**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-260">Insert **HoloLens Bot**.</span></span> <span data-ttu-id="e2f37-261">请确保将项目模板设置为**3d**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="e2f37-262">将位置设置为合适的**位置**（请记住，更接近根目录更好）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="e2f37-263">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-263">Then, click **Create project**.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="e2f37-265">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="e2f37-266">转到 "**编辑 > 首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="e2f37-267">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="e2f37-268">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="e2f37-268">Close the **Preferences** window.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="e2f37-270">接下来，转到 "**文件 > 生成设置**"，选择 "**通用 Windows 平台**"，然后单击 "**切换平台**" 按钮以应用所选内容。</span><span class="sxs-lookup"><span data-stu-id="e2f37-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="e2f37-272">尽管仍处于**文件 > 生成设置**，但请确保：</span><span class="sxs-lookup"><span data-stu-id="e2f37-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="e2f37-273">**目标设备**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e2f37-273">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="e2f37-274">对于沉浸式耳机，将 "**目标设备**" 设置为 "*任何设备*"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="e2f37-275">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="e2f37-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="e2f37-276">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="e2f37-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="e2f37-277">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="e2f37-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="e2f37-278">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="e2f37-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="e2f37-279">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="e2f37-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="e2f37-280">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e2f37-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="e2f37-281">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="e2f37-281">A save window will appear.</span></span>
        
            ![设置 Unity 项目](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="e2f37-283">为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 "**新建文件夹**" 按钮以创建新文件夹，将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![设置 Unity 项目](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="e2f37-285">打开新创建的**场景**文件夹，然后*在 "文件名：文本" 字段*中，键入**BotScene**，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="e2f37-287">现在，"**生成设置**" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="e2f37-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="e2f37-288">在 "*生成设置*" 窗口中，单击 "**播放机设置**" 按钮，这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="e2f37-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![设置 Unity 项目](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="e2f37-290">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="e2f37-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="e2f37-291">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="e2f37-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="e2f37-292">**脚本运行时版本**应为**试验性（NET 4.6 等效项）** ;更改此要求将需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="e2f37-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="e2f37-293">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="e2f37-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="e2f37-294">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="e2f37-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="e2f37-296">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="e2f37-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="e2f37-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="e2f37-297">**InternetClient**</span></span>
        - <span data-ttu-id="e2f37-298">**十分**</span><span class="sxs-lookup"><span data-stu-id="e2f37-298">**Microphone**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="e2f37-300">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="e2f37-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="e2f37-302">"返回*生成设置* _" C# Unity_项目不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="e2f37-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="e2f37-303">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="e2f37-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="e2f37-304">保存场景和项目（**file > SAVE 场景/file > SAVE project**）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="e2f37-305">第5章–照相机设置</span><span class="sxs-lookup"><span data-stu-id="e2f37-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2f37-306">如果要跳过本课程的*Unity 设置*组件，并继续直接进入代码，请随时下载[312 此 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后继续从[第7章](#chapter-8--create-the-botobjects-class)：</span><span class="sxs-lookup"><span data-stu-id="e2f37-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="e2f37-307">在 "*层次结构" 面板*中，选择 "**摄像机**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="e2f37-308">选择后，你将能够在 "*检查器" 面板*中看到**主相机**的所有组件。</span><span class="sxs-lookup"><span data-stu-id="e2f37-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="e2f37-309">**照相机对象**必须命名为 "**主相机**" （请注意拼写）</span><span class="sxs-lookup"><span data-stu-id="e2f37-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="e2f37-310">必须将主相机**标记**设置为**MainCamera** （请注意拼写）</span><span class="sxs-lookup"><span data-stu-id="e2f37-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="e2f37-311">请确保将**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="e2f37-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="e2f37-312">将**清除标志**设置为**纯色**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="e2f37-313">将相机组件的**背景**色设置为**黑色、Alpha 0 （十六进制代码： #00000000）**</span><span class="sxs-lookup"><span data-stu-id="e2f37-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![照相机设置](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="e2f37-315">第6章–导入 Newtonsoft.json 库</span><span class="sxs-lookup"><span data-stu-id="e2f37-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="e2f37-316">为了帮助您反序列化和序列化接收并发送到机器人服务的对象，您需要下载**newtonsoft.json**库。</span><span class="sxs-lookup"><span data-stu-id="e2f37-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="e2f37-317">你将在[此处找到已使用正确的 Unity 文件夹结构组织的兼容版本](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="e2f37-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="e2f37-318">若要将 Newtonsoft.json 库导入项目，请使用本课程附带的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="e2f37-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="e2f37-319">使用 "**资产** > **导入包** > **自定义包**" 菜单选项将*unitypackage*添加到 Unity。</span><span class="sxs-lookup"><span data-stu-id="e2f37-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="e2f37-321">在弹出的 "**导入 Unity 包**" 框中，确保选择了 "所有" （并包括）**插件**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="e2f37-323">单击 "**导入**" 按钮，将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="e2f37-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="e2f37-324">在项目视图中，在 "**插件**" 下，单击 " **newtonsoft.json** " 文件夹，然后选择 "newtonsoft.json" 插件。</span><span class="sxs-lookup"><span data-stu-id="e2f37-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="e2f37-325">选择 Newtonsoft.json 插件后，请确保**未选中** **任何平台**，并确保还**未选中**" **WSAPlayer** "，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="e2f37-326">这只是为了确认已正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2f37-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="e2f37-327">标记这些插件会将它们配置为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="e2f37-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="e2f37-328">在从 Unity 导出项目后，将使用 WSA 文件夹中的一组不同的组。</span><span class="sxs-lookup"><span data-stu-id="e2f37-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="e2f37-329">接下来，需要在**newtonsoft.json**文件夹中打开**WSA**文件夹。</span><span class="sxs-lookup"><span data-stu-id="e2f37-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="e2f37-330">你将看到刚才配置的同一文件的副本。</span><span class="sxs-lookup"><span data-stu-id="e2f37-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="e2f37-331">选择该文件，然后在 "检查器" 中，确保</span><span class="sxs-lookup"><span data-stu-id="e2f37-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="e2f37-332">**未选中** **任何平台**</span><span class="sxs-lookup"><span data-stu-id="e2f37-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="e2f37-333">**仅** **检查** **WSAPlayer**</span><span class="sxs-lookup"><span data-stu-id="e2f37-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="e2f37-334">不**检查** **进程**</span><span class="sxs-lookup"><span data-stu-id="e2f37-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="e2f37-335">第7章–创建 BotTag</span><span class="sxs-lookup"><span data-stu-id="e2f37-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="e2f37-336">创建名为**BotTag**的新的**标记**对象。</span><span class="sxs-lookup"><span data-stu-id="e2f37-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="e2f37-337">选择场景中的主相机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="e2f37-338">单击 "检查器" 面板中的 "标记" 下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="e2f37-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="e2f37-339">单击 "**添加标记**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-339">Click on **Add Tag**.</span></span>

    ![照相机设置](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="e2f37-341">单击 **+** 符号。</span><span class="sxs-lookup"><span data-stu-id="e2f37-341">Click on the **+** symbol.</span></span> <span data-ttu-id="e2f37-342">将新**标记**命名为**BotTag**，*保存*。</span><span class="sxs-lookup"><span data-stu-id="e2f37-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![照相机设置](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="e2f37-344">**不要**将**BotTag**应用于主摄像机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="e2f37-345">如果你意外地执行了此操作，请确保将主相机标签更改回*MainCamera*。</span><span class="sxs-lookup"><span data-stu-id="e2f37-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="e2f37-346">第8章–创建 BotObjects 类</span><span class="sxs-lookup"><span data-stu-id="e2f37-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="e2f37-347">你需要创建的第一个脚本是**BotObjects**类，该类是一个空类，它是一个空类，可将一系列其他类对象存储在同一脚本中并由场景中的其他脚本访问。</span><span class="sxs-lookup"><span data-stu-id="e2f37-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="e2f37-348">此类的创建只是一种体系结构选择，这些对象可以托管在你稍后将在本课程中创建的机器人脚本中。</span><span class="sxs-lookup"><span data-stu-id="e2f37-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="e2f37-349">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-349">To create this class:</span></span> 

1.  <span data-ttu-id="e2f37-350">右键单击 "*项目" 面板*，然后**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="e2f37-351">命名文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-351">Name the folder **Scripts**.</span></span> 

    ![创建脚本文件夹。](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="e2f37-353">双击 "**脚本**" 文件夹将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="e2f37-354">然后在该文件夹中，右键单击，然后选择 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="e2f37-355">将脚本命名为**BotObjects**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="e2f37-356">双击新的**BotObjects**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="e2f37-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="e2f37-357">删除脚本的内容，并将其替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2f37-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="e2f37-358">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="e2f37-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="e2f37-359">第9章–创建 GazeInput 类</span><span class="sxs-lookup"><span data-stu-id="e2f37-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="e2f37-360">要创建的下一个类是**GazeInput**类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="e2f37-361">此类负责：</span><span class="sxs-lookup"><span data-stu-id="e2f37-361">This class is responsible for:</span></span>

- <span data-ttu-id="e2f37-362">创建一个游标，用来表示播放*机的外观*。</span><span class="sxs-lookup"><span data-stu-id="e2f37-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="e2f37-363">检测在播放机看上碰到的对象，并保存对检测到的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="e2f37-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="e2f37-364">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-364">To create this class:</span></span> 

1.  <span data-ttu-id="e2f37-365">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e2f37-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="e2f37-366">右键单击文件夹内部，**创建 > C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="e2f37-367">调用脚本**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="e2f37-368">双击新的**GazeInput**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="e2f37-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="e2f37-369">在类名的顶部插入以下行：</span><span class="sxs-lookup"><span data-stu-id="e2f37-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="e2f37-370">然后，将以下变量添加到**GazeInput**类中的**Start （）** 方法之上：</span><span class="sxs-lookup"><span data-stu-id="e2f37-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="e2f37-371">应添加**Start （）** 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="e2f37-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="e2f37-372">当类初始化时，将调用此操作：</span><span class="sxs-lookup"><span data-stu-id="e2f37-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="e2f37-373">实现一个方法，该方法将实例化并设置注视光标：</span><span class="sxs-lookup"><span data-stu-id="e2f37-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="e2f37-374">实现将从主相机设置 Raycast 的方法，并跟踪当前聚焦的对象。</span><span class="sxs-lookup"><span data-stu-id="e2f37-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="e2f37-375">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="e2f37-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="e2f37-376">第10章–创建机器人类</span><span class="sxs-lookup"><span data-stu-id="e2f37-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="e2f37-377">现在要创建的脚本称为**机器人**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="e2f37-378">这是应用程序的核心类，它存储：</span><span class="sxs-lookup"><span data-stu-id="e2f37-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="e2f37-379">Web 应用机器人凭据</span><span class="sxs-lookup"><span data-stu-id="e2f37-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="e2f37-380">收集用户语音命令的方法</span><span class="sxs-lookup"><span data-stu-id="e2f37-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="e2f37-381">启动与 Web 应用机器人的会话所需的方法</span><span class="sxs-lookup"><span data-stu-id="e2f37-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="e2f37-382">向 Web 应用机器人发送消息所需的方法</span><span class="sxs-lookup"><span data-stu-id="e2f37-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="e2f37-383">若要将消息发送到机器人服务， **SendMessageToBot （）** 协同程序将生成一个活动，该活动是由 Bot 框架识别为用户发送的数据的对象。</span><span class="sxs-lookup"><span data-stu-id="e2f37-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="e2f37-384">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-384">To create this class:</span></span> 

1. <span data-ttu-id="e2f37-385">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="e2f37-386">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="e2f37-387">将脚本**Bot**命名为。</span><span class="sxs-lookup"><span data-stu-id="e2f37-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="e2f37-388">双击新脚本以通过 Visual Studio 将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="e2f37-389">在**机器人**类的顶部，将命名空间更新为与以下相同：</span><span class="sxs-lookup"><span data-stu-id="e2f37-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="e2f37-390">在**机器人**类中添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="e2f37-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="e2f37-391">请确保将你的**机器人机密密钥**插入到**botSecret**变量。</span><span class="sxs-lookup"><span data-stu-id="e2f37-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="e2f37-392">你将在本课程的第 **[2 章](#chapter-2---create-the-azure-bot-service)"步骤 10**" 中记下你的**机器人机密密钥**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="e2f37-393">现在需要添加**唤醒（）** 和**Start （）** 的代码。</span><span class="sxs-lookup"><span data-stu-id="e2f37-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="e2f37-394">添加语音捕获开始和结束时由语音库调用的两个处理程序。</span><span class="sxs-lookup"><span data-stu-id="e2f37-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="e2f37-395">当用户停止说话时， *DictationRecognizer*将自动停止捕获用户语音。</span><span class="sxs-lookup"><span data-stu-id="e2f37-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="e2f37-396">下面的处理程序收集用户语音输入的结果，并调用负责将消息发送到 Web 应用机器人服务的协同程序。</span><span class="sxs-lookup"><span data-stu-id="e2f37-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="e2f37-397">调用以下协同程序来开始与机器人的对话。</span><span class="sxs-lookup"><span data-stu-id="e2f37-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="e2f37-398">你会注意到，一旦完成会话调用，它将通过传递一系列参数（将活动设置为以空消息形式发送到机器人服务）来调用**SendMessageToCoroutine （）** 。</span><span class="sxs-lookup"><span data-stu-id="e2f37-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="e2f37-399">这样做是为了提示机器人服务启动对话框。</span><span class="sxs-lookup"><span data-stu-id="e2f37-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="e2f37-400">调用以下协同程序生成要发送到机器人服务的活动。</span><span class="sxs-lookup"><span data-stu-id="e2f37-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="e2f37-401">在将活动发送到机器人服务后，调用以下协同程序来请求响应。</span><span class="sxs-lookup"><span data-stu-id="e2f37-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="e2f37-402">要添加到此类中的最后一个方法是在场景中显示消息所必需的：</span><span class="sxs-lookup"><span data-stu-id="e2f37-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="e2f37-403">你可能会在 Unity 编辑器控制台中看到一个错误，缺少**SceneOrganiser**类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="e2f37-404">请忽略此消息，因为稍后会在本教程中创建此类。</span><span class="sxs-lookup"><span data-stu-id="e2f37-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="e2f37-405">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="e2f37-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="e2f37-406">第11章–创建交互类</span><span class="sxs-lookup"><span data-stu-id="e2f37-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="e2f37-407">现在要创建的类称为**交互**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="e2f37-408">此类用于检测 HoloLens 点击用户的输入。</span><span class="sxs-lookup"><span data-stu-id="e2f37-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="e2f37-409">如果用户在查看场景中的*机器人*对象时点击，并准备好侦听语音输入，则机器人对象会将颜色更改为**红色**，并开始侦听语音输入。</span><span class="sxs-lookup"><span data-stu-id="e2f37-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="e2f37-410">此类继承自**GazeInput**类，因此，可以从该类引用**Start （）** 方法和变量，这是通过使用**base**表示的。</span><span class="sxs-lookup"><span data-stu-id="e2f37-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="e2f37-411">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-411">To create this class:</span></span>

1.  <span data-ttu-id="e2f37-412">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="e2f37-413">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="e2f37-414">命名脚本**交互**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="e2f37-415">双击新脚本以通过 Visual Studio 将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="e2f37-416">在**交互**类的顶部，将命名空间和类继承更新为与以下相同：</span><span class="sxs-lookup"><span data-stu-id="e2f37-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="e2f37-417">在**交互**类中添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="e2f37-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="e2f37-418">然后添加**Start （）** 方法：</span><span class="sxs-lookup"><span data-stu-id="e2f37-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="e2f37-419">添加当用户在 HoloLens 相机前面执行分流手势时触发的处理程序</span><span class="sxs-lookup"><span data-stu-id="e2f37-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="e2f37-420">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="e2f37-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="e2f37-421">第12章–创建 SceneOrganiser 类</span><span class="sxs-lookup"><span data-stu-id="e2f37-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="e2f37-422">此实验室中所需的最后一个类称为**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="e2f37-423">此类将通过将组件和脚本添加到主相机并在场景中创建相应的对象，以编程方式设置场景。</span><span class="sxs-lookup"><span data-stu-id="e2f37-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="e2f37-424">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="e2f37-424">To create this class:</span></span>

1.  <span data-ttu-id="e2f37-425">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="e2f37-426">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="e2f37-427">将脚本命名为**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="e2f37-428">双击新脚本以通过 Visual Studio 将其打开。</span><span class="sxs-lookup"><span data-stu-id="e2f37-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="e2f37-429">在**SceneOrganiser**类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="e2f37-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="e2f37-430">然后添加**唤醒（）** 和**Start （）** 方法：</span><span class="sxs-lookup"><span data-stu-id="e2f37-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="e2f37-431">添加以下方法，负责在场景中创建机器人对象并设置参数和组件：</span><span class="sxs-lookup"><span data-stu-id="e2f37-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="e2f37-432">添加以下方法，负责在场景中创建 UI 对象，以表示来自机器人的响应：</span><span class="sxs-lookup"><span data-stu-id="e2f37-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="e2f37-433">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="e2f37-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="e2f37-434">在 Unity 编辑器中，将 " **SceneOrganiser** " 脚本从 "脚本" 文件夹拖到主摄像机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="e2f37-435">场景 Organiser 组件现在应显示在 "照相机" 对象上，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="e2f37-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="e2f37-437">第13章–生成之前</span><span class="sxs-lookup"><span data-stu-id="e2f37-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="e2f37-438">若要对应用程序进行全面测试，需要将其旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e2f37-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="e2f37-439">在执行此操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="e2f37-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="e2f37-440">[**第4章**](#chapter-4--set-up-the-unity-project)中提到的所有设置都已正确设置。</span><span class="sxs-lookup"><span data-stu-id="e2f37-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="e2f37-441">脚本**SceneOrganiser**已附加到**摄像机主**对象。</span><span class="sxs-lookup"><span data-stu-id="e2f37-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="e2f37-442">在**机器人**类中，请确保已将**机器人机密密钥**插入到**botSecret**变量。</span><span class="sxs-lookup"><span data-stu-id="e2f37-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="e2f37-443">第14章–生成并旁加载到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e2f37-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="e2f37-444">此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。</span><span class="sxs-lookup"><span data-stu-id="e2f37-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="e2f37-445">导航到 "**生成设置**"，"**文件 > 生成设置 ...** "。</span><span class="sxs-lookup"><span data-stu-id="e2f37-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="e2f37-446">在**生成设置**窗口中，单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-446">From the **Build Settings** window, click **Build**.</span></span>

    ![从 Unity 生成应用](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="e2f37-448">如果尚未这样做，请勾选**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="e2f37-449">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-449">Click **Build**.</span></span> <span data-ttu-id="e2f37-450">Unity 将启动**文件资源管理器**窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e2f37-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="e2f37-451">立即创建该文件夹并将其命名为**应用**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="e2f37-452">选择**应用**文件夹后，单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="e2f37-453">Unity 将开始向**应用**文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="e2f37-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="e2f37-454">Unity 完成生成（可能需要一些时间）后，它会在生成的位置打开 "**文件资源管理器**" 窗口（检查任务栏，因为它可能不会始终出现在窗口之上，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="e2f37-455">第15章–部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e2f37-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="e2f37-456">在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="e2f37-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="e2f37-457">你将需要 HoloLens 的 IP 地址（用于远程部署），并确保你的 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="e2f37-458">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e2f37-458">To do this:</span></span>

    1. <span data-ttu-id="e2f37-459">在戴上 HoloLens 的同时，请打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="e2f37-460">中转到**网络 & Internet > wi-fi > 高级选项**</span><span class="sxs-lookup"><span data-stu-id="e2f37-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="e2f37-461">记下**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="e2f37-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="e2f37-462">接下来，导航回 "**设置**"，然后为**开发人员更新 & Security >**</span><span class="sxs-lookup"><span data-stu-id="e2f37-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="e2f37-463">设置开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="e2f37-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="e2f37-464">导航到新的 Unity 生成（**应用**文件夹），并在**Visual Studio**中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="e2f37-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="e2f37-465">在**解决方案配置**中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="e2f37-466">在**解决方案平台**中，选择 " **X86**，**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="e2f37-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="e2f37-468">请在 "**生成" 菜单**中，单击 "**部署解决方案**"，将应用程序旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e2f37-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="e2f37-469">应用现在应显示在你的 HoloLens 上已安装的应用列表中，可以启动了！</span><span class="sxs-lookup"><span data-stu-id="e2f37-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2f37-470">若要部署到沉浸式耳机，请将 "**解决方案平台**" 设置为 "*本地计算机*"，并将**配置**设置为 "*调试*"，将 " *x86* " 设置为**平台**。</span><span class="sxs-lookup"><span data-stu-id="e2f37-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="e2f37-471">然后，使用 "**生成" 菜单**选择 "*部署解决方案*"，将部署到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="e2f37-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="e2f37-472">第16章–在 HoloLens 上使用应用程序</span><span class="sxs-lookup"><span data-stu-id="e2f37-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="e2f37-473">启动应用程序后，会看到机器人作为你前面的蓝色球。</span><span class="sxs-lookup"><span data-stu-id="e2f37-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="e2f37-474">在 gazing 时使用**点击手势**来启动会话。</span><span class="sxs-lookup"><span data-stu-id="e2f37-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="e2f37-475">等待会话启动（在发生此情况时，UI 将显示一条消息）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="e2f37-476">收到来自机器人的介绍性消息后，再次在机器人上点击，使其变为红色并开始倾听你的声音。</span><span class="sxs-lookup"><span data-stu-id="e2f37-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="e2f37-477">停止对话后，应用程序会将消息发送到机器人，并立即收到将在 UI 中显示的响应。</span><span class="sxs-lookup"><span data-stu-id="e2f37-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="e2f37-478">重复此过程，将更多的消息发送到机器人（必须在每次想要 sen 邮件时点击一次）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="e2f37-479">此对话演示了机器人如何保留信息（你的姓名），同时还提供了已知信息（如已贮存的项目）。</span><span class="sxs-lookup"><span data-stu-id="e2f37-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="e2f37-480">询问机器人的一些问题：</span><span class="sxs-lookup"><span data-stu-id="e2f37-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="e2f37-481">已完成的 Web 应用机器人（v4）应用程序</span><span class="sxs-lookup"><span data-stu-id="e2f37-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="e2f37-482">恭喜，你构建了一个利用 Azure Web 应用机器人、Microsoft Bot Framework v4 的混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="e2f37-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![最终产品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="e2f37-484">额外练习</span><span class="sxs-lookup"><span data-stu-id="e2f37-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="e2f37-485">练习1</span><span class="sxs-lookup"><span data-stu-id="e2f37-485">Exercise 1</span></span>

<span data-ttu-id="e2f37-486">此实验室中的会话结构非常基本。</span><span class="sxs-lookup"><span data-stu-id="e2f37-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="e2f37-487">使用 Microsoft LUIS 为机器人指定自然语言理解功能。</span><span class="sxs-lookup"><span data-stu-id="e2f37-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="e2f37-488">练习2</span><span class="sxs-lookup"><span data-stu-id="e2f37-488">Exercise 2</span></span>

<span data-ttu-id="e2f37-489">此示例不包括终止会话和重新启动新会话。</span><span class="sxs-lookup"><span data-stu-id="e2f37-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="e2f37-490">若要使机器人功能完成，请尝试将结束实现到会话中。</span><span class="sxs-lookup"><span data-stu-id="e2f37-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
