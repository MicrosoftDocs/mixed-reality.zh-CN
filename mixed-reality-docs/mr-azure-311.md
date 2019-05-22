---
title: MR 和 Azure 311-Microsoft Graph
description: 完成此课程以了解如何利用 Microsoft Graph 和连接到驱动生产力，混合的现实应用程序中的数据。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 microsoft graph，沉浸式、 hololens、 vr
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590126"
---
>[!NOTE]
><span data-ttu-id="b3262-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="b3262-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b3262-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="b3262-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b3262-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="b3262-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b3262-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="b3262-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b3262-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b3262-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b3262-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="b3262-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="b3262-110">MR 和 Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="b3262-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="b3262-111">在本课程中，您将学习如何使用*Microsoft Graph*登录到 Microsoft 帐户使用混合的现实应用程序中的安全身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3262-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="b3262-112">然后，将检索，并在应用程序界面中显示计划的会议。</span><span class="sxs-lookup"><span data-stu-id="b3262-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="b3262-113">*Microsoft Graph*是一组 Api 设计用于启用对很多 Microsoft 服务的访问。</span><span class="sxs-lookup"><span data-stu-id="b3262-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="b3262-114">Microsoft 介绍 Microsoft Graph 为矩阵的资源通过关系连接，也就是说，它允许应用程序访问各种类型的连接的用户数据。</span><span class="sxs-lookup"><span data-stu-id="b3262-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="b3262-115">有关详细信息，请访问[Microsoft Graph 页](https://developer.microsoft.com/graph)。</span><span class="sxs-lookup"><span data-stu-id="b3262-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="b3262-116">开发将包括会指导用户以注视，然后点击球体，会提示用户以安全地登录到 Microsoft 帐户应用的创建。</span><span class="sxs-lookup"><span data-stu-id="b3262-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="b3262-117">登录到他们的帐户，用户将能够查看当天的计划会议的列表。</span><span class="sxs-lookup"><span data-stu-id="b3262-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="b3262-118">已完成本课程，您将具有混合的现实 HoloLens 应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b3262-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="b3262-119">使用手势，点击一个对象，它会提示用户能够登录到 Microsoft 帐户 （移出应用程序，以用户身份登录，然后返回到应用程序）。</span><span class="sxs-lookup"><span data-stu-id="b3262-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="b3262-120">查看当天的计划会议的列表。</span><span class="sxs-lookup"><span data-stu-id="b3262-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="b3262-121">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="b3262-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="b3262-122">本课程旨在教您如何将 Azure 服务集成与你的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="b3262-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="b3262-123">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="b3262-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="b3262-124">设备支持</span><span class="sxs-lookup"><span data-stu-id="b3262-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b3262-125">课程</span><span class="sxs-lookup"><span data-stu-id="b3262-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b3262-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b3262-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b3262-127"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="b3262-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b3262-128">MR 和 Azure 311:Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="b3262-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="b3262-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b3262-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="b3262-130">先决条件</span><span class="sxs-lookup"><span data-stu-id="b3262-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b3262-131">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="b3262-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b3262-132">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。</span><span class="sxs-lookup"><span data-stu-id="b3262-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b3262-133">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。</span><span class="sxs-lookup"><span data-stu-id="b3262-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b3262-134">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="b3262-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b3262-135">开发计算机</span><span class="sxs-lookup"><span data-stu-id="b3262-135">A development PC</span></span>
- [<span data-ttu-id="b3262-136">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="b3262-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b3262-137">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="b3262-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b3262-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b3262-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b3262-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b3262-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b3262-140">一个[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="b3262-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b3262-141">Internet 访问的 Azure 设置和 Microsoft Graph 数据检索</span><span class="sxs-lookup"><span data-stu-id="b3262-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="b3262-142">一个有效**的 Microsoft 帐户**（个人或工作/学校）</span><span class="sxs-lookup"><span data-stu-id="b3262-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="b3262-143">几个会议计划为当前日期，使用相同的 Microsoft 帐户</span><span class="sxs-lookup"><span data-stu-id="b3262-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="b3262-144">开始之前</span><span class="sxs-lookup"><span data-stu-id="b3262-144">Before you start</span></span>

1.  <span data-ttu-id="b3262-145">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="b3262-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b3262-146">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b3262-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="b3262-147">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="b3262-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b3262-148">它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。</span><span class="sxs-lookup"><span data-stu-id="b3262-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b3262-149">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="b3262-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="b3262-150">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="b3262-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="b3262-151">第 1 章-在应用程序注册门户中创建您的应用程序</span><span class="sxs-lookup"><span data-stu-id="b3262-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="b3262-152">开始时，你将需要创建并注册你的应用程序中**应用程序注册门户**。</span><span class="sxs-lookup"><span data-stu-id="b3262-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="b3262-153">本章还会发现服务密钥，您可以调用*Microsoft Graph*访问你帐户的内容。</span><span class="sxs-lookup"><span data-stu-id="b3262-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="b3262-154">导航到[Microsoft 应用程序注册门户](https://apps.dev.microsoft.com)，并使用你的 Microsoft 帐户登录。</span><span class="sxs-lookup"><span data-stu-id="b3262-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="b3262-155">你已登录后，你将重定向到**应用程序注册门户**。</span><span class="sxs-lookup"><span data-stu-id="b3262-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="b3262-156">在中**我的应用程序**部分中，单击按钮**添加应用**。</span><span class="sxs-lookup"><span data-stu-id="b3262-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="b3262-157">**应用程序注册门户**颜色可能有所不同，具体取决于是否您以前使用过*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="b3262-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="b3262-158">下面的屏幕截图显示这些不同的版本。</span><span class="sxs-lookup"><span data-stu-id="b3262-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="b3262-159">为应用程序，单击添加名称**创建**。</span><span class="sxs-lookup"><span data-stu-id="b3262-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="b3262-160">一旦创建该应用程序后，你将重定向到应用程序主页面。</span><span class="sxs-lookup"><span data-stu-id="b3262-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="b3262-161">复制**应用程序 Id**并且请务必记下此值到某个安全位置，在代码中，将很快就使用它。</span><span class="sxs-lookup"><span data-stu-id="b3262-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="b3262-162">在中**平台**部分中，请确保**本机应用程序**显示。</span><span class="sxs-lookup"><span data-stu-id="b3262-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="b3262-163">如果*不*上单击**添加平台**，然后选择**本机应用程序**。</span><span class="sxs-lookup"><span data-stu-id="b3262-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="b3262-164">在同一页中和名为的部分中，向下滚动**Microsoft Graph 权限**将需要添加其他应用程序权限。</span><span class="sxs-lookup"><span data-stu-id="b3262-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="b3262-165">单击**外**旁边**委托的权限**。</span><span class="sxs-lookup"><span data-stu-id="b3262-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="b3262-166">由于您希望应用程序以访问用户的日历，检查调用框中**Calendars.Read**然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="b3262-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="b3262-167">滚动到底部并单击**保存**按钮。</span><span class="sxs-lookup"><span data-stu-id="b3262-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="b3262-168">将确认你保存，并可以从注销**应用程序注册门户**。</span><span class="sxs-lookup"><span data-stu-id="b3262-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="b3262-169">第 2 章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b3262-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="b3262-170">以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="b3262-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b3262-171">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="b3262-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="b3262-172">需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="b3262-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="b3262-173">插入**MSGraphMR**。</span><span class="sxs-lookup"><span data-stu-id="b3262-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="b3262-174">请确保项目模板设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="b3262-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="b3262-175">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="b3262-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b3262-176">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="b3262-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="b3262-177">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="b3262-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b3262-178">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="b3262-178">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b3262-179">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="b3262-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b3262-180">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="b3262-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="b3262-181">转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。</span><span class="sxs-lookup"><span data-stu-id="b3262-181">Go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="b3262-182">在仍处于**文件 > 生成设置**，请确保：</span><span class="sxs-lookup"><span data-stu-id="b3262-182">While still in **File > Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="b3262-183">**设备为目标**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b3262-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="b3262-184">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="b3262-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="b3262-185">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="b3262-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="b3262-186">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="b3262-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="b3262-187">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="b3262-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="b3262-188">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="b3262-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="b3262-189">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="b3262-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b3262-190">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="b3262-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="b3262-191">为此，和任何未来、 场景创建新文件夹。</span><span class="sxs-lookup"><span data-stu-id="b3262-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="b3262-192">选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="b3262-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="b3262-193">打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_ComputerVisionScene**，然后单击**保存**.</span><span class="sxs-lookup"><span data-stu-id="b3262-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="b3262-194">请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="b3262-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="b3262-195">创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="b3262-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="b3262-196">中的剩余设置，*生成设置*，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="b3262-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="b3262-197">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="b3262-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="b3262-198">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="b3262-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="b3262-199">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="b3262-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b3262-200">**脚本编写** **运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="b3262-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="b3262-201">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="b3262-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="b3262-202">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="b3262-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="b3262-203">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="b3262-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="b3262-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b3262-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="b3262-205">中的后面部分面板**XR 设置**(下面找到**发布设置**)，检查**虚拟现实支持**，请确保**Windows Mixed RealitySDK**添加。</span><span class="sxs-lookup"><span data-stu-id="b3262-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="b3262-206">回到*生成设置*， *UnityC#项目*不再灰显; 请查看这旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="b3262-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="b3262-207">关闭*生成设置*窗口。</span><span class="sxs-lookup"><span data-stu-id="b3262-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="b3262-208">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="b3262-208">Save your scene and project (**FILE > SAVE SCENES / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="b3262-209">第 3 章-Unity 中的导入库</span><span class="sxs-lookup"><span data-stu-id="b3262-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3262-210">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5---create-meetingsui-class)。</span><span class="sxs-lookup"><span data-stu-id="b3262-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="b3262-211">若要使用*Microsoft Graph*在你需要进行的 Unity 中使用的**Microsoft.Identity.Client** DLL。</span><span class="sxs-lookup"><span data-stu-id="b3262-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="b3262-212">可以使用 Microsoft Graph SDK，但是，它将生成 Unity 项目 （即编辑项目的后期生成） 后需要添加 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="b3262-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="b3262-213">它被认为更简单直接导入所需的 Dll 到 Unity。</span><span class="sxs-lookup"><span data-stu-id="b3262-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="b3262-214">这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。</span><span class="sxs-lookup"><span data-stu-id="b3262-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="b3262-215">这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。</span><span class="sxs-lookup"><span data-stu-id="b3262-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="b3262-216">若要导入*Microsoft Graph*到你自己的项目， [MSGraph_LabPlugins.zip 文件下载](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="b3262-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="b3262-217">此包已创建具有版本已经过测试的库。</span><span class="sxs-lookup"><span data-stu-id="b3262-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="b3262-218">如果你想要了解有关如何将自定义 Dll 添加到你的 Unity 项目的详细信息[单击此链接](https://docs.unity3d.com/Manual/UsingDLL.html)。</span><span class="sxs-lookup"><span data-stu-id="b3262-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="b3262-219">若要将包导入：</span><span class="sxs-lookup"><span data-stu-id="b3262-219">To import the package:</span></span>

1.  <span data-ttu-id="b3262-220">使用将 Unity 包添加到 Unity **资产* > *导入包* > *自定义包** 菜单选项。</span><span class="sxs-lookup"><span data-stu-id="b3262-220">Add the Unity Package to Unity by using the **Assets* > *Import Package* > *Custom Package** menu option.</span></span> <span data-ttu-id="b3262-221">选择刚下载的包。</span><span class="sxs-lookup"><span data-stu-id="b3262-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="b3262-222">在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="b3262-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="b3262-223">单击**导入**按钮将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="b3262-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="b3262-224">转到**MSGraph**下的文件夹**插件**中*项目面板*，然后选择名为插件**Microsoft.Identity.Client**。</span><span class="sxs-lookup"><span data-stu-id="b3262-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="b3262-225">与*插件*选择，确保**Any 平台**处于未选中状态，然后确保**WSAPlayer**也是未选中，则单击**应用**.</span><span class="sxs-lookup"><span data-stu-id="b3262-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="b3262-226">这只是为了确认正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="b3262-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="b3262-227">将标记这些插件将它们配置为仅使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="b3262-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="b3262-228">有一组不同的项目会导出从 Unity 为通用 Windows 应用程序后，将使用 WSA 文件夹中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="b3262-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="b3262-229">接下来，您需要打开**WSA**文件夹，在**MSGraph**文件夹。</span><span class="sxs-lookup"><span data-stu-id="b3262-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="b3262-230">您将看到刚配置的相同文件的副本。</span><span class="sxs-lookup"><span data-stu-id="b3262-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="b3262-231">选择该文件，然后在该检查器：</span><span class="sxs-lookup"><span data-stu-id="b3262-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="b3262-232">确保**Any 平台**是**取消选中**，并且**仅** **WSAPlayer**是**检查**。</span><span class="sxs-lookup"><span data-stu-id="b3262-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="b3262-233">请确保**SDK**设置为**UWP**，并**脚本编写后端**设置为 **.net**</span><span class="sxs-lookup"><span data-stu-id="b3262-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="b3262-234">絋粄**不处理**是**检查**。</span><span class="sxs-lookup"><span data-stu-id="b3262-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="b3262-235">单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="b3262-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="b3262-236">第 4 章-照相机设置</span><span class="sxs-lookup"><span data-stu-id="b3262-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="b3262-237">在这一章期间将设置您的场景 Main Camera:</span><span class="sxs-lookup"><span data-stu-id="b3262-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="b3262-238">在中*层次结构面板*，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="b3262-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="b3262-239">选择后，你将能够看到的所有组件**Main Camera**中*Inspector*面板。</span><span class="sxs-lookup"><span data-stu-id="b3262-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="b3262-240">**相机对象**必须命名为**Main Camera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="b3262-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="b3262-241">Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="b3262-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="b3262-242">请确保**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="b3262-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="b3262-243">设置**清除标志**到**纯色**</span><span class="sxs-lookup"><span data-stu-id="b3262-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="b3262-244">设置**背景色**的照相机组件**黑色、 Alpha 0** **(十六进制代码: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="b3262-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="b3262-245">中的最后一个对象结构*层次结构面板*应类似于下图中所示：</span><span class="sxs-lookup"><span data-stu-id="b3262-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="b3262-246">第 5 章-创建 MeetingsUI 类</span><span class="sxs-lookup"><span data-stu-id="b3262-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="b3262-247">您需要创建的第一个脚本是**MeetingsUI**，负责托管和填充 （欢迎消息、 说明和会议详细信息） 的应用程序的 UI。</span><span class="sxs-lookup"><span data-stu-id="b3262-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="b3262-248">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="b3262-248">To create this class:</span></span>

1.  <span data-ttu-id="b3262-249">右键单击**资产**中的文件夹*项目面板*，然后选择 \**创建*> \*文件夹\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3262-249">Right-click on the **Assets** folder in the *Project Panel*, then select \**Create* > \*Folder\*\*.</span></span> <span data-ttu-id="b3262-250">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="b3262-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="b3262-251">打开**脚本**文件夹然后，在该文件夹中，右键单击，\**创建* > \*C\# 脚本\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3262-251">Open the **Scripts** folder then, within that folder, right-click, \**Create* > \*C\# Script\*\*.</span></span> <span data-ttu-id="b3262-252">脚本命名为**MeetingsUI。**</span><span class="sxs-lookup"><span data-stu-id="b3262-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="b3262-253">双击新**MeetingsUI**脚本以将其与打开*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="b3262-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="b3262-254">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="b3262-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="b3262-255">在类中插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="b3262-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="b3262-256">然后，替换**start （)** 方法并添加**Awake()** 方法。</span><span class="sxs-lookup"><span data-stu-id="b3262-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="b3262-257">类初始化时将会调用：</span><span class="sxs-lookup"><span data-stu-id="b3262-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="b3262-258">添加方法负责创建*会议 UI*并使用当前的会议请求时填充它：</span><span class="sxs-lookup"><span data-stu-id="b3262-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="b3262-259">**删除** **update （)** 方法，和**保存所做的更改**之前返回到 Unity 的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b3262-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="b3262-260">章 6-创建图形类</span><span class="sxs-lookup"><span data-stu-id="b3262-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="b3262-261">要创建的下一步脚本位于**Graph**脚本。</span><span class="sxs-lookup"><span data-stu-id="b3262-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="b3262-262">此脚本负责进行调用以对用户进行身份验证和当前日期从用户的日历中检索已安排的会议。</span><span class="sxs-lookup"><span data-stu-id="b3262-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="b3262-263">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="b3262-263">To create this class:</span></span>

1.  <span data-ttu-id="b3262-264">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="b3262-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b3262-265">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="b3262-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b3262-266">脚本命名为**Graph**。</span><span class="sxs-lookup"><span data-stu-id="b3262-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="b3262-267">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="b3262-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b3262-268">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="b3262-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b3262-269">你会注意到在此脚本中代码的部分封装[预编译指令](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)，这是为了避免生成 Visual Studio 解决方案时出现问题的库。</span><span class="sxs-lookup"><span data-stu-id="b3262-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="b3262-270">删除**start （)** 并**update （)** 方法，因为它们不会使用。</span><span class="sxs-lookup"><span data-stu-id="b3262-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="b3262-271">外侧**Graph**类中，插入下列所需表示每日计划的会议的 JSON 对象反序列化的对象：</span><span class="sxs-lookup"><span data-stu-id="b3262-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="b3262-272">内部**Graph**类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="b3262-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="b3262-273">更改 **appId** 值为 **应用程序 Id** 中记下 **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)，步骤 4** 。</span><span class="sxs-lookup"><span data-stu-id="b3262-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="b3262-274">此值应与中显示的相同**应用程序注册门户**在您的应用程序注册页中。</span><span class="sxs-lookup"><span data-stu-id="b3262-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="b3262-275">内**Graph**类中，将方法添加**SignInAsync()** 并**AquireTokenAsync()**，用于将提示用户插入登录凭据。</span><span class="sxs-lookup"><span data-stu-id="b3262-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="b3262-276">添加以下两种方法：</span><span class="sxs-lookup"><span data-stu-id="b3262-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="b3262-277">**BuildTodayCalendarEndpoint()**，哪些生成指定日和时间跨度内，在其中检索计划的会议的 URI。</span><span class="sxs-lookup"><span data-stu-id="b3262-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="b3262-278">**ListMeetingsAsync()**，该请求来自已安排的会议*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="b3262-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="b3262-279">现在已完成**Graph**脚本。</span><span class="sxs-lookup"><span data-stu-id="b3262-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="b3262-280">**保存所做的更改**之前返回到 Unity 的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b3262-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="b3262-281">章 7-创建 GazeInput 脚本</span><span class="sxs-lookup"><span data-stu-id="b3262-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="b3262-282">现在将创建**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="b3262-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="b3262-283">此类处理和跟踪的用户的视线移动，使用**Raycast**来自**Main Camera**前, 滚投影。</span><span class="sxs-lookup"><span data-stu-id="b3262-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="b3262-284">若要创建脚本：</span><span class="sxs-lookup"><span data-stu-id="b3262-284">To create the script:</span></span>

1.  <span data-ttu-id="b3262-285">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="b3262-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b3262-286">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="b3262-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b3262-287">脚本命名为**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="b3262-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="b3262-288">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="b3262-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b3262-289">更改命名空间代码，以匹配所示，以及添加 '**\[System.Serializable\]** 上面标记您**GazeInput**类，以便它可以序列化：</span><span class="sxs-lookup"><span data-stu-id="b3262-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="b3262-290">内部**GazeInput**类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="b3262-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="b3262-291">添加**CreateCursor()** 方法以在场景中，创建 HoloLens 游标并调用方法中的，从**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="b3262-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="b3262-292">以下方法启用注视 Raycast 并跟踪的已设定焦点的对象。</span><span class="sxs-lookup"><span data-stu-id="b3262-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="b3262-293">**保存所做的更改**之前返回到 Unity 的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b3262-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="b3262-294">章 8-创建交互类</span><span class="sxs-lookup"><span data-stu-id="b3262-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="b3262-295">您现在需要创建**交互**脚本，它负责：</span><span class="sxs-lookup"><span data-stu-id="b3262-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="b3262-296">处理**点击**交互并**照相机注视**，这使用户能够与场景中的"按钮"中的日志进行交互。</span><span class="sxs-lookup"><span data-stu-id="b3262-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="b3262-297">要与之交互的用户场景中的"按钮"对象中创建日志。</span><span class="sxs-lookup"><span data-stu-id="b3262-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="b3262-298">若要创建脚本：</span><span class="sxs-lookup"><span data-stu-id="b3262-298">To create the script:</span></span>

1.  <span data-ttu-id="b3262-299">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="b3262-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b3262-300">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="b3262-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b3262-301">脚本命名为**交互**。</span><span class="sxs-lookup"><span data-stu-id="b3262-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="b3262-302">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="b3262-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b3262-303">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="b3262-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="b3262-304">更改的继承**交互**类派生*MonoBehaviour*到**GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="b3262-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="b3262-305">~~公共类的交互：MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="b3262-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="b3262-306">内部**交互**类插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="b3262-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="b3262-307">替换**启动**方法; 请注意，它是一个替代方法，它调用 base 的视线移动类方法。</span><span class="sxs-lookup"><span data-stu-id="b3262-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="b3262-308">**Start （)** 类初始化输入识别的注册和创建的登录时将调用*按钮*场景中：</span><span class="sxs-lookup"><span data-stu-id="b3262-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="b3262-309">添加**CreateSignInButton()** 方法，将实例化的登录*按钮*场景中并设置其属性：</span><span class="sxs-lookup"><span data-stu-id="b3262-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="b3262-310">添加**GestureRecognizer_Tapped()** 方法，为响应*点击*用户事件。</span><span class="sxs-lookup"><span data-stu-id="b3262-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="b3262-311">**删除** **update （)** 方法，然后**保存所做的更改**之前返回到 Unity 的 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b3262-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="b3262-312">第 9 章 — 设置脚本引用</span><span class="sxs-lookup"><span data-stu-id="b3262-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="b3262-313">您需要将放在本章**交互**拖动到脚本**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="b3262-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="b3262-314">然后，该脚本将处理放置他们需要为其他脚本。</span><span class="sxs-lookup"><span data-stu-id="b3262-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="b3262-315">从**脚本**中的文件夹*项目面板*，将脚本**交互**到**Main Camera**对象，如如下图所示。</span><span class="sxs-lookup"><span data-stu-id="b3262-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="b3262-316">第 10 章 — 设置标记</span><span class="sxs-lookup"><span data-stu-id="b3262-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="b3262-317">处理的视线移动的代码将使用标记**SignInButton**若要确定哪个对象的用户将与之交互来登录到*Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="b3262-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="b3262-318">若要创建标记：</span><span class="sxs-lookup"><span data-stu-id="b3262-318">To create the Tag:</span></span>

1.  <span data-ttu-id="b3262-319">在 Unity 编辑器中单击**Main Camera**中*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="b3262-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="b3262-320">在中*检查器面板*上单击**MainCamera** *标记*打开下拉列表。</span><span class="sxs-lookup"><span data-stu-id="b3262-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="b3262-321">单击**添加标记...**</span><span class="sxs-lookup"><span data-stu-id="b3262-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="b3262-322">单击 **+** 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3262-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="b3262-323">写入形式的标记名称**SignInButton**并单击保存。</span><span class="sxs-lookup"><span data-stu-id="b3262-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="b3262-324">第 11 章 — 生成到 UWP 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b3262-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="b3262-325">此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。</span><span class="sxs-lookup"><span data-stu-id="b3262-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b3262-326">导航到 *生成设置* (\**文件* > \*生成设置\*\*)。</span><span class="sxs-lookup"><span data-stu-id="b3262-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="b3262-327">如果尚不存在，则勾选**Unity C\#项目**。</span><span class="sxs-lookup"><span data-stu-id="b3262-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="b3262-328">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="b3262-328">Click **Build**.</span></span> <span data-ttu-id="b3262-329">将启动 unity**文件资源管理器**窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b3262-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b3262-330">现在，创建该文件夹并将其命名**应用**。</span><span class="sxs-lookup"><span data-stu-id="b3262-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="b3262-331">然后使用**应用程序**文件夹选择，单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="b3262-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="b3262-332">Unity 将开始构建您的项目**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="b3262-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="b3262-333">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="b3262-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="b3262-334">章 12-将部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="b3262-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="b3262-335">若要部署在 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="b3262-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="b3262-336">你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式。**</span><span class="sxs-lookup"><span data-stu-id="b3262-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="b3262-337">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b3262-337">To do this:</span></span>

    1.  <span data-ttu-id="b3262-338">戴上您 HoloLens，同时打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="b3262-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="b3262-339">转到**网络和 Internet** > **的 Wi-fi** > **高级选项**</span><span class="sxs-lookup"><span data-stu-id="b3262-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="b3262-340">请注意**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="b3262-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="b3262-341">接下来，导航回到**设置**，然后**更新和安全** > **面向开发人员**</span><span class="sxs-lookup"><span data-stu-id="b3262-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="b3262-342">设置**上的开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="b3262-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="b3262-343">导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="b3262-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b3262-344">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="b3262-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="b3262-345">在中**解决方案平台**，选择**x86，远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="b3262-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="b3262-346">系统会提示要插入**IP 地址**的远程设备 (HoloLens，在这种情况下，记下)。</span><span class="sxs-lookup"><span data-stu-id="b3262-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="b3262-347">转到**构建**菜单，并单击**部署解决方案**旁加载到你 HoloLens 应用程序。</span><span class="sxs-lookup"><span data-stu-id="b3262-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="b3262-348">在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！</span><span class="sxs-lookup"><span data-stu-id="b3262-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="b3262-349">Microsoft Graph HoloLens 应用程序</span><span class="sxs-lookup"><span data-stu-id="b3262-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="b3262-350">祝贺你，构建利用 Microsoft Graph，将读取并显示用户日历数据的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="b3262-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b3262-351">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="b3262-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b3262-352">练习 1</span><span class="sxs-lookup"><span data-stu-id="b3262-352">Exercise 1</span></span>

<span data-ttu-id="b3262-353">使用 Microsoft Graph 来显示有关用户的其他信息</span><span class="sxs-lookup"><span data-stu-id="b3262-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="b3262-354">用户电子邮件 / 电话号码 / 配置文件图片</span><span class="sxs-lookup"><span data-stu-id="b3262-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b3262-355">练习 1</span><span class="sxs-lookup"><span data-stu-id="b3262-355">Exercise 1</span></span>

<span data-ttu-id="b3262-356">实现语音控件导航 Microsoft 图形 UI。</span><span class="sxs-lookup"><span data-stu-id="b3262-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
