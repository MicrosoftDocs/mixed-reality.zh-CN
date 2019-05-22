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
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

# <a name="mr-and-azure-312-bot-integration"></a>MR 和 Azure 312:智能机器人应用程序集成

在本课程中，您将学习如何创建和部署使用 Microsoft Bot Framework V4 智能机器人应用程序并与之通信通过 Windows Mixed Reality 应用程序。 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4**是一组 Api 设计的开发人员提供工具以生成可扩展和可缩放的智能机器人应用程序。 有关详细信息，请访问[Microsoft Bot Framework 页](https://dev.botframework.com/)或[V4 Git 存储库](https://github.com/Microsoft/botbuilder-dotnet/wiki)。

完成此课程后，您便会生成一个 Windows Mixed Reality 应用程序，将能够执行以下操作：

1. 使用**点击手势**开始侦听用户语音的智能机器人应用程序。
2. 当用户具有所说的内容时，智能机器人应用程序将尝试提供了一个响应。
3. 显示为文本，附近机器人，Unity 场景中定位的智能机器人答复。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务集成与你的 Unity 项目。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 312:智能机器人应用程序集成</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。 因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。 按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 为 Azure 和 Azure 智能机器人应用程序检索的 Internet 访问。 有关详细信息[请单击以下链接](https://dev.botframework.com/)。

### <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。 

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

## <a name="chapter-1--create-the-bot-application"></a>第 1 章 – 创建智能机器人应用程序

第一步是创建为本地 ASP.Net Core Web 应用程序智能机器人。 一旦完成并对其进行测试后，会将其发布到 Azure 门户。

1.  打开 Visual Studio。 创建新项目，选择**ASP NET Core Web 应用程序**作为项目类型 （它会在.NET Core 的子节下），并调用它**MyBot**。 单击 **“确定”**。

2.  选择将显示在窗口中**空**。 此外请确保目标设置为**ASP NET Core 2.0**和身份验证设置为**无身份验证**。 单击 **“确定”**。  

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-01.png)

3.  现在将打开该解决方案。 右键单击解决方案**Mybot**中**解决方案资源管理器**，然后单击**为解决方案管理 NuGet 包**。 

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-02.png)

4.  在**浏览**选项卡上，搜索**Microsoft.Bot.Builder.Integration.AspNet.Core** (请确保您拥有**包括预发行版**检查)。 选择的包版本**4.0.1-preview**，并选中项目框。 然后单击**安装**。 您现在已安装所需的库**Bot Framework v4**。 关闭 NuGet 页。

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-03.png)

5.  右键单击你*项目*， **MyBot**，在 **解决方案资源管理器**，然后单击 **添加** **|** **类**。

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-04.png)

6.  将类命名**MyBot** ，然后单击**添加**。

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-05.png)

7.  重复上一个点，以创建名为的另一个类**ConversationContext**。 

8.  右键单击**wwwroot**中**解决方案资源管理器**，然后单击**添加** **|** **新项**. 选择**HTML 页**（它会在子节 Web 下）。 将文件命名**default.html**。 单击**添加**。

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-06.png)

9.  类的列表中的对象 /**解决方案资源管理器**应如下图所示。

    ![创建智能机器人应用程序](images/AzureLabs-Lab312-07.png)

10. 双击**ConversationContext**类。 此类负责保存智能机器人应用程序用于维护该会话的上下文的变量。 因为，这些会话上下文值将保留在此类的实例中的任何实例**MyBot**类将刷新每次收到活动。 将以下代码添加到类：

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

11. 双击**MyBot**类。 此类将托管客户从调用的任何传入活动的处理程序。 在此类将添加用于生成智能机器人应用程序与客户之间的会话的代码。 前面曾提到，初始化此类的实例每次收到活动。 将以下代码添加到此类：

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

12. 双击**启动**类。 此类将初始化智能机器人应用程序。 将以下代码添加到类：

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

13. 打开**程序**类文件，并验证是否在其代码是相同的如下所示：

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

14. 请记住保存所做的更改，为此，请转到**文件** > **全部保存**，Visual Studio 顶部工具栏中。

## <a name="chapter-2---create-the-azure-bot-service"></a>章 2-创建 Azure 机器人服务

既然您已经针对自动程序生成代码，您必须将其发布到的实例*Web App 机器人*服务，在 Azure 门户上的。 这一章将演示如何创建和配置 Azure 上的智能机器人应用程序服务和然后将代码发布到它。

1.  首先，登录到 Azure 门户 (https://portal.azure.com)。 

    1. 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**创建资源**在左上角，并搜索*Web App 机器人*，然后单击**Enter**。

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-08.png)
 
3.  该新页面将提供的说明*Web App 机器人*服务。 在左下角此页上，选择**创建**按钮，以创建与此关联服务。

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-09.png)
 
4.  一旦你单击**创建**:

    1. 插入所需**名称**此服务实例。
    2. 选择**订阅**。
    3. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

        > 如果你想要阅读更多有关 Azure 资源组，[请访问以下链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. （如果要创建新的资源组） 确定你的资源组的位置。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。
    5. 选择**定价层**适合您，如果这是第一个时间来创建*Web App 机器人*服务，应可供你免费层 （名为 F0）
    6. **应用名称**可以只在相同*智能机器人应用程序名称*。 
    7. 将保留*智能机器人应用程序模板*作为**基本 (C#)**。
    8. *应用服务计划/位置*应该已自动填充为你的帐户。
    9. 设置**Azure 存储**你想要使用托管在智能机器人应用程序。 如果你还没有，可以在此处创建它。
    10. 您还需要确认你已了解的条款和条件应用于此服务。
    11. 单击创建。
 
        ![创建 Azure 机器人服务](images/AzureLabs-Lab312-10.png)

5.  一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。

6.  创建服务实例后，在门户中将显示一条通知。

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-11.png) 
 
7.  单击通知以了解新的服务实例。 

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-12.png)
 
8. 单击**转到资源**通知探索新的服务实例中的按钮。 你将转到新的 Azure 服务实例。 

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-13.png)
 
9.  此时，你需要设置名为的功能**Direct Line**以允许客户端应用程序与此智能机器人应用程序服务进行通信。 单击**通道**，然后在**添加特色的频道**部分中，单击**配置 Direct Line 通道**。

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-14.png)

10. 在此页中将查找**机密密钥**，将允许客户端应用程序，以使用智能机器人应用程序进行身份验证。 单击**显示**按钮，然后将会更高版本中您的项目需要它时所采取的显示密钥中的一个副本。 

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>第 3 – 章将智能机器人应用程序发布到 Azure Web App 机器人服务

现在，你的服务已准备就绪，您需要将智能机器人应用程序代码，以前，构建到您新创建的 Web 应用程序智能机器人应用程序服务的发布。

> [!NOTE] 
> 必须将智能机器人发布到 Azure 服务，每次对智能机器人应用程序解决方案进行更改时 o。

1.  返回到以前创建的 Visual Studio 解决方案。 
2.  右键单击你**MyBot**项目，在**解决方案资源管理器**，然后单击**发布**。

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-16.png)

3.  上*选取发布目标*页上，单击**应用服务**，然后**选择现有**，最后单击**创建配置文件**（您可能需要单击旁边的下拉箭头*发布*按钮，则此项不可见)。

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-17.png)

4. 如果您尚未登录到你的 Microsoft 帐户，你必须在这里完成。
5. 上**发布**您会发现有设置相同的页面**订阅**用于*Web App 机器人*服务创建。 然后设置**视图**作为**资源组**，然后在下拉列表文件夹结构中，选中**资源组**之前创建。 单击 **“确定”**。 

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-18.png)

6.  现在，单击**发布**按钮，并等待智能机器人应用程序要发布 （可能需要几分钟时间）。

    ![将智能机器人应用程序发布到 Azure Web App 机器人服务](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>第 4 章-设置 Unity 项目

以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。 

    ![设置 Unity 项目](images/AzureLabs-Lab312-20.png)

2.  现在，需要提供的 Unity 项目名称。 插入**Hololens 机器人**。 请确保项目模板设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![设置 Unity 项目](images/AzureLabs-Lab312-21.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![设置 Unity 项目](images/AzureLabs-Lab312-22.png)

4.  接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。

    ![设置 Unity 项目](images/AzureLabs-Lab312-23.png)

5.  在仍处于**文件 > 生成设置**并确保选中：

    1.  **设备为目标**设置为**Hololens**

        > 对于沉浸式耳机，设置**目标设备**到*任一设备*。

    2.  **生成的类型**设置为**D3D**

    3.  **SDK**设置为**最新安装**

    4.  **Visual Studio 版本**设置为**最新安装**

    5.  **生成并运行**设置为**本地计算机**

    6.  保存场景，并将其添加到生成。 

        1. 选择执行此**添加打开场景**。 保存窗口将显示。
        
            ![设置 Unity 项目](images/AzureLabs-Lab312-24.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

             ![设置 Unity 项目](images/AzureLabs-Lab312-25.png)

        3. 打开新建**场景**文件夹，然后在*文件的名称*： 文本字段中，键入**BotScene**，然后单击**保存**。

            ![设置 Unity 项目](images/AzureLabs-Lab312-26.png)

    7. 中的剩余设置，**生成设置**，应暂时保留为默认值。

6. 在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。 

    ![设置 Unity 项目](images/AzureLabs-Lab312-27.png)

7. 在此面板中，需要验证几个设置：

    1. 在中**其他设置**选项卡：

        1. **脚本运行时版本**应 **（NET 4.6 等效） 的实验性**; 更改这将需要重新启动编辑器中。
        2. **脚本编写后端**应为 **.NET**
        3. **API 兼容性级别**应为 **.NET 4.6**

            ![设置 Unity 项目](images/AzureLabs-Lab312-28.png)
      
    2. 内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**
        - **Microphone**

            ![设置 Unity 项目](images/AzureLabs-Lab312-29.png)

    3. 中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

        ![设置 Unity 项目](images/AzureLabs-Lab312-30.png)

8.  回到*生成设置* _Unity C#_ 项目不再灰显; 选中它旁边的复选框。 
9.  关闭生成设置窗口。
10. 保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。


## <a name="chapter-5--camera-setup"></a>第 5 章-照相机设置

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 7 章](#chapter-7-–-create-the-botobjects-class)。

1.  在中*层次结构面板*，选择**Main Camera**。 
2.  选择后，你将能够看到的所有组件**Main Camera**中*检查器面板*。

    1. **相机对象**必须命名为**Main Camera** （请注意拼写）
    2. Main Camera**标记**必须设置为**MainCamera** （请注意拼写）
    3. 请确保**转换位置**设置为**0，0，0**
    4. 设置**清除标志**到**纯色**。
    5. 设置**背景**照相机组件到色**黑色、 Alpha 0 (十六进制代码: #00000000)**

    ![照相机设置](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>第 6 章-导入 Newtonsoft 库

若要帮助您反序列化和序列化对象接收和发送到机器人服务需要下载**Newtonsoft**库。 您会发现[兼容的版本与此处正确的 Unity 文件夹结构已组织](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。 

若要 Newtonsoft 库导入到你的项目，使用了随附此课程的 Unity 包。

1.  添加 *.unitypackage*到使用 Unity**资产** > **导入包** > **自定义包**菜单选项。

    ![导入 Newtonsoft 库](images/AzureLabs-Lab312-34.png)

2.  在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。

    ![导入 Newtonsoft 库](images/AzureLabs-Lab312-35.png)

3.  单击**导入**按钮将项添加到你的项目。

4.  转到**Newtonsoft**下的文件夹**插件**在项目视图中，选择 Newtonsoft 插件。

    ![](images/AzureLabs-Lab312-35b.png)

5.  使用所选 Newtonsoft 插件，请确保**Any 平台**是**取消选中**，然后确保**WSAPlayer**也是**未选中**，然后单击**应用**。 这只是为了确认正确配置文件。

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > 将标记这些插件将它们配置为仅使用在 Unity 编辑器中。 有一组不同的它们从 Unity 项目会导出后，将使用 WSA 文件夹中。

6.  接下来，您需要打开**WSA**文件夹，在**Newtonsoft**文件夹。 您将看到刚配置的相同文件的副本。 选择的文件，然后在检查器中，确保的
    -   **任何平台**是**未选中状态** 
    -   **仅** **WSAPlayer**是**检查**
    -   **不处理**是**检查**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>第 7 – 章创建 BotTag

1.  创建一个新**标记**对象调用**BotTag**。 选择场景中的 Main Camera。 单击标记下拉列表中的检查器面板菜单。 单击**将标记添加**。

    ![照相机设置](images/AzureLabs-Lab312-32.png)
 
2.  单击 **+** 符号。 指定新**标记**作为**BotTag**，*保存*。

    ![照相机设置](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **不这样做**应用**BotTag**到 Main Camera。 如果已意外地执行此操作，请确保更改标记返回到 Main Camera *MainCamera*。

## <a name="chapter-8--create-the-botobjects-class"></a>第 8 章 – 创建 BotObjects 类

您需要创建的第一个脚本是**BotObjects**类，该类是创建一系列的其他类对象可存储在同一个脚本和其他脚本场景中访问的空类。

此类的创建是纯粹的体系结构的选择，这些对象可以改为托管，你将稍后在本课程中创建的智能机器人应用程序脚本中。

若要创建此类： 

1.  在中右击*项目面板*，然后**创建 > 文件夹**。 将文件夹命名为**脚本**。 

    ![创建脚本的文件夹。](images/AzureLabs-Lab312-36.png)

2.  双击**脚本**文件夹将其打开。 然后在该文件夹，右键单击，并选择**创建 >C#脚本**。 脚本命名为**BotObjects**。 

3.  双击新**BotObjects**脚本以将其与打开**Visual Studio**。

4.  删除脚本的内容，并使用以下代码替换它：

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

6.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-9--create-the-gazeinput-class"></a>第 9 章 – 创建 GazeInput 类

要创建的下一步类是**GazeInput**类。 此类负责：

- 表示将创建游标*注视*的播放机。
- 检测的播放机中，提供注视被命中的对象和保存对检测到的对象的引用。

若要创建此类： 

1.  转到**脚本**之前创建的文件夹。 
2.  在文件夹中，右键单击**创建 >C#脚本**。 调用脚本**GazeInput**。 
3.  双击新**GazeInput**脚本以将其与打开**Visual Studio**。
4.  插入类名的右侧顶部的以下行：

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  然后添加以下变量内的**GazeInput**类，更高版本**start （)** 方法：

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

6.  为代码**start （)** 应添加方法。 类初始化时，这将会调用：

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

7.  实现将实例化和设置的视线移动游标的方法： 

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

8.  实现的方法，将在安装程序从 Main Camera Raycast 和跟踪的当前具有焦点的对象。

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
 
9.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-10--create-the-bot-class"></a>第 10 章 – 创建智能机器人应用程序类

要创建的脚本现在称为**机器人**。 这是你的应用程序的核心类，它将存储： 

- 你的 Web 应用程序智能机器人应用程序凭据
- 方法，收集用户语音命令
- 若要启动会话的 Web 应用程序智能机器人，所需的方法 
- 若要将消息发送到 Web 应用程序智能机器人，所需的方法 

若要将消息发送到 Bot Service **SendMessageToBot()** 协同程序将生成活动，这是识别智能机器人应用程序框架为用户发送的数据的对象。 
 
若要创建此类： 

1. 双击**脚本**文件夹，将其打开。 
2. 内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为**机器人**。 
3. 双击要使用 Visual Studio 中打开的新脚本。
4. 更新命名空间，如下所示，在顶部相同**机器人**类：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. 内部**机器人**类添加以下变量：

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
    > 请确保插入你**智能机器人应用程序机密密钥**成**botSecret**变量。 你将已记下你 **智能机器人应用程序机密密钥** 在本课程中，开头中 **[第 2 章](#chapter-2---create-the-azure-bot-service)，第 10 步** 。

7. 为代码**Awake()** 并**start （)** 现在需要添加。 

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

8. 添加两个处理程序在语音捕获开始和结束时调用由语音库。 *DictationRecognizer*将自动停止捕获用户之声，当用户停止说到。

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

1. 下面的处理程序收集用户语音输入的结果，并调用协同程序负责将消息发送到 Web 应用智能机器人应用程序服务。

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

10. 下面的协同例程调用以开始与智能机器人应用程序的会话。 你会注意到，会话调用完成后，它将调用**SendMessageToCoroutine()** 表示通过一系列将设置要发送到 Bot 服务作为一条空消息的活动的参数。 这样做是为了提示要启动对话的智能机器人应用程序服务。

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

11. 下面的协同例程调用以生成要发送到机器人服务的活动。 

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

12. 下面的协同例程调用以将活动发送到智能机器人应用程序服务后请求响应。 

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

13. 场景中显示该消息所需的最后一个方法添加到此类：

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
    > 您可能会看到一个在 Unity 编辑器控制台中，有关缺少**SceneOrganiser**类。 忽略此消息，因为将稍后在本教程中创建此类。

14.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-11--create-the-interactions-class"></a>第 11 章 – 创建交互类

要创建此类现被称为**交互**。 此类用于检测来自用户的 HoloLens 点击输入。 

如果用户点击时查看*机器人*场景和智能机器人应用程序中的对象已准备好侦听语音输入，智能机器人应用程序对象将更改颜色**红色**并开始侦听语音输入。 

此类继承自**GazeInput**类，并因此是能够引用**start （)** 方法，并从该类，表示通过使用变量**基**。 
 
若要创建此类：

1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为**交互**。 
3.  双击要使用 Visual Studio 中打开的新脚本。
4.  更新命名空间和类继承，如下所示，在顶部相同**交互**类：

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  内部**交互**类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  然后添加**start （)** 方法：

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

7.  添加用户执行点击手势 HoloLens 照相机的前面时，将触发该处理程序

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

8. 请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-12--create-the-sceneorganiser-class"></a>第 12 章 – 创建 SceneOrganiser 类

在此实验中所需的最后一个类称为**SceneOrganiser**。 此类将在安装程序场景以编程方式，通过将组件和脚本添加到 Main Camera，并在场景中创建相应的对象。
 
若要创建此类：

1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为**SceneOrganiser**。 
3.  双击要使用 Visual Studio 中打开的新脚本。
4.  内部**SceneOrganiser**类添加以下变量：

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

6.  然后添加**Awake()** 并**start （)** 方法：

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

7.  添加以下方法，负责在场景中创建智能机器人应用程序对象和设置参数和组件：

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

7.  添加以下方法，负责创建 UI 对象在场景中，表示从智能机器人应用程序的响应：

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

8.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。
9.  在 Unity 编辑器中，拖动**SceneOrganiser**到 Main Camera 脚本文件夹中的脚本。 Main Camera 对象上现在应显示场景组织者组件，如下图中所示。

    ![创建 Azure 机器人服务](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>第 13 章 – 生成前

若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。
执行操作之前，请确保：

-   中所述的所有设置[**第 4 章**](#Chapter-4-–-Set-up-the-unity-project)正确设置。 
-   该脚本**SceneOrganiser**附加到**Main Camera**对象。 
-   在**机器人**类中，请确保已插入您**智能机器人应用程序机密密钥**到**botSecret**变量。

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>第 14 章 – 生成和旁的加载到 HoloLens

此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。

1.  导航到**生成设置**，**文件 > 生成设置...**.
2.  从**生成设置**窗口中，单击**生成**。

    ![从 Unity 构建应用程序](images/AzureLabs-Lab312-38.png)

3.  如果尚不存在，则勾选**UnityC#项目**。
4.  单击“生成” 。 将启动 unity**文件资源管理器**窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名**应用**。 然后使用**应用程序**文件夹选择，单击**选择文件夹**。 
5.  Unity 将开始构建您的项目**应用**文件夹。 
6.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

## <a name="chapter-15--deploy-to-hololens"></a>章 15-将部署到 HoloLens

若要部署在 HoloLens 上：

1.  你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。 要实现此目的，请执行以下操作：

    1. 戴上您 HoloLens，同时打开**设置**。
    2. 转到**网络和 Internet > 的 Wi-fi > 高级选项**
    3. 请注意**IPv4**地址。
    4. 接下来，导航回到**设置**，然后**更新和安全 > 适用于开发人员** 
    5. 设置开发人员模式。

2.  导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。
3.  在中**解决方案配置**选择**调试**。
4.  在中**解决方案平台**，选择**x86**，**远程计算机**。 

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab312-39.png)
 
5.  转到**生成菜单**，然后单击**部署解决方案**旁, 加载到你 HoloLens 应用程序。
6.  在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！

    > [!NOTE]
    > 若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。 然后将其部署到本地计算机，使用**生成菜单**，选择*部署解决方案*。 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>第 16 章 – 在 HoloLens 上使用应用程序

- 一旦启动该应用程序，您将看到在您面前蓝色球体智能机器人应用程序。

- 使用**点击手势**时观望在球体，若要启动的会话。 
 
- 等待会话启动 （的 UI 将显示一条消息时都是这样）。 一旦从智能机器人应用程序接收的介绍性消息，再次点击上智能机器人应用程序以便它将变为红色，并开始侦听语音。 

- 在停止通信后，你的应用程序将在消息发送到智能机器人应用程序并立即将收到一个响应，它将显示在 UI 中。 

- 重复该过程以将更多的消息发送到智能机器人 （您需要点击每次想发送一条消息的时）。

此会话演示如何智能机器人应用程序可以保留信息 （你的名称），同时还提供已知的信息 （如所存储的项）。

#### <a name="some-questions-to-ask-the-bot"></a>要让机器人的一些问题：

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>完成的 Web 应用程序智能机器人应用程序 (v4) 应用程序

祝贺你，构建利用 Azure Web App 机器人、 Microsoft Bot Framework v4 的混合的现实应用。

![最终产品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

在此实验中的会话结构是非常基本的。 使用 Microsoft LUIS 为智能机器人提供自然语言理解功能。

### <a name="exercise-2"></a>练习 2

此示例不包括终止会话并重新启动一个新。 若要使功能完成的智能机器人应用程序，请尝试实现的对话，闭包。
