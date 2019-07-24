---
title: MR 和 Azure 312-机器人集成
description: 完成本课程, 了解如何使用 Microsoft Bot Framework v4 创建和部署 bot, 并在混合现实应用程序中与其通信。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, 计算机视觉, hololens, 沉浸, vr, microsoft bot framework v4, web 应用机器人, bot framework, microsoft 机器人
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63542860"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

# <a name="mr-and-azure-312-bot-integration"></a>MR 和 Azure 312:机器人集成

在本课程中, 你将了解如何使用 Microsoft Bot Framework V4 创建和部署机器人, 并通过 Windows Mixed Reality 应用程序与它进行通信。 

![](images/AzureLabs-Lab312-00.png)

**Microsoft 机器人 Framework V4**是一组 api, 旨在向开发人员提供用于构建可扩展、可缩放机器人应用程序的工具。 有关详细信息, 请访问[Microsoft Bot Framework 页](https://dev.botframework.com/)或[V4 Git 存储库](https://github.com/Microsoft/botbuilder-dotnet/wiki)。

完成本课程后, 你将构建一个 Windows Mixed Reality 应用程序, 该应用程序将能够执行以下操作:

1. 使用**点击手势**启动机器人来侦听用户语音。
2. 如果用户已提到某些内容, 机器人会尝试提供响应。
3. 在 Unity 场景中, 在机器人附近显示 "bot 回复" 作为文本。

在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 312:机器人集成</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 HoloLens, 但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸 (VR) 耳机。 由于沉浸式 (VR) 耳机没有可访问的摄像机, 因此需要连接到电脑的外部照相机。 在本课程中, 您将看到有关支持沉浸式 (VR) 耳机时可能需要执行的任何更改的说明。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外, 请注意, 本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容 (2018 年7月)。 你可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件:

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC, 用于沉浸式 (VR) 耳机开发
- [Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- Azure 和 Azure 机器人检索的 Internet 访问。 有关详细信息,[请访问此链接](https://dev.botframework.com/)。

### <a name="before-you-start"></a>开始之前

1.  为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。
2.  设置并测试你的 HoloLens。 如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。 

有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens)。

有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。

## <a name="chapter-1--create-the-bot-application"></a>第1章–创建机器人应用程序

第一步是创建机器人作为本地 ASP.Net Core Web 应用程序。 完成并测试后, 将其发布到 Azure 门户。

1.  打开 Visual Studio。 创建一个新项目, 选择 " **ASP NET Core Web 应用程序**" 作为项目类型 (你将在 ".net core" 部分下找到), 并**MyBot**调用它。 单击 **“确定”** 。

2.  在将显示的窗口中选择 "**空**"。 此外, 请确保将目标设置为**ASP NET Core 2.0** , 并将身份验证设置为 "**无身份验证**"。 单击 **“确定”** 。  

    ![创建机器人应用程序](images/AzureLabs-Lab312-01.png)

3.  解决方案现在将打开。 右键单击 "**解决方案资源管理器**中的" 解决方案**Mybot** ", 然后单击"**管理解决方案的 NuGet 包**"。 

    ![创建机器人应用程序](images/AzureLabs-Lab312-02.png)

4.  在 "**浏览**" 选项卡中 , 搜索 "", 并确保已选中 "**包括预发行版**"。 选择包版本**4.0.1-预览**, 并勾选项目框。 然后单击 "**安装**"。 你现在已安装了**Bot Framework v4**所需的库。 关闭 NuGet 页。

    ![创建机器人应用程序](images/AzureLabs-Lab312-03.png)

5.  右键单击你*项目*， **MyBot**，在 **解决方案资源管理器**，然后单击 **添加** **|** **类**。

    ![创建机器人应用程序](images/AzureLabs-Lab312-04.png)

6.  将类命名为**MyBot** , 然后单击 "**添加**"。

    ![创建机器人应用程序](images/AzureLabs-Lab312-05.png)

7.  重复上述步骤, 以创建名为**ConversationContext**的另一个类。 

8.  在**解决方案资源管理器**中右键单击**wwwroot** , 并单击 "**添加** **|** **新项**"。 选择 " **HTML 页**" (你将在 "Web" 子部分下发现)。 将文件命名为 **.html**。 单击**添加**。

    ![创建机器人应用程序](images/AzureLabs-Lab312-06.png)

9.  **解决方案资源管理器**中的类/对象的列表应类似于下图。

    ![创建机器人应用程序](images/AzureLabs-Lab312-07.png)

10. 双击 " **ConversationContext** " 类。 此类负责保存机器人用于维护会话上下文的变量。 这些会话上下文值在此类的实例中维护, 因为每次收到活动时, **MyBot**类的任何实例都将刷新。 将下面的代码添加到类:

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

11. 双击 " **MyBot** " 类。 此类将承载来自客户的任何传入活动所调用的处理程序。 在此类中, 你将添加用于构建机器人和客户之间的会话的代码。 如前文所述, 每次收到活动时都会初始化此类的实例。 将以下代码添加到此类:

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

12. 双击**Startup**类。 此类将初始化机器人。 将下面的代码添加到类:

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

13. 打开**Program**类文件, 验证其中的代码与以下代码相同:

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

14. 记住要保存所做的更改, 若要执行此操作, 请从 Visual Studio 顶部的工具栏**中转到** > "**全部保存**"。

## <a name="chapter-2---create-the-azure-bot-service"></a>第2章-创建 Azure Bot 服务

既然已经为机器人生成了代码, 就必须将其发布到 Azure 门户上的*Web 应用机器人*服务的实例。 本章介绍如何在 Azure 上创建和配置机器人服务, 然后将代码发布到该服务。

1.  首先, 登录到 Azure 门户 (https://portal.azure.com) 。 

    1. 如果还没有 Azure 帐户, 则需要创建一个。 如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。

2.  登录后, 单击左上角的 "**创建资源**", 搜索 " *Web 应用程序*", 然后单击 " **Enter**"。

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-08.png)
 
3.  新页面将提供*Web 应用机器人*服务的说明。 在此页的左下角, 选择 "**创建**" 按钮以创建与此服务的关联。

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-09.png)
 
4.  单击 "**创建**" 后:

    1. 为此服务实例插入所需的**名称**。
    2. 选择**订阅**。
    3. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。

        > 若要了解有关 Azure 资源组的详细信息,[请访问此链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. 确定资源组的位置 (如果要创建新的资源组)。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。
    5. 选择适合你的**定价层**, 如果这是第一次创建*Web 应用机器人*服务, 则你应该可以使用免费层 (名为 F0)
    6. **应用名称**可以与*Bot 名称*相同。 
    7. 将*机器人模板*保留为 "**基本C#" ()** 。
    8. 应已为你的帐户自动填写*应用服务计划/位置*。
    9. 设置要用于托管机器人的**Azure 存储**。 如果还没有, 可以在此处创建一个。
    10. 还需要确认是否已了解应用于此服务的条款和条件。
    11. 单击 "创建"。
 
        ![创建 Azure Bot 服务](images/AzureLabs-Lab312-10.png)

5.  单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。

6.  创建服务实例后, 门户中将显示一个通知。

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-11.png) 
 
7.  单击通知以浏览新服务实例。 

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-12.png)
 
8. 单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的 Azure 服务实例。 

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-13.png)
 
9.  此时, 你需要设置一个称为 "**直接连线**" 的功能, 以允许客户端应用程序与此 Bot 服务通信。 单击 "**频道**", 然后在 "**添加特色频道**" 部分中, 单击 "**配置直接连线通道**"。

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-14.png)

10. 在此页中, 你将找到允许客户端应用程序通过机器人进行身份验证的**机密密钥**。 单击 "**显示**" 按钮, 然后复制其中一个所显示的密钥, 因为稍后会在项目中使用此项。 

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>第3章–将机器人发布到 Azure Web 应用机器人服务

现在, 你的服务已准备就绪, 你需要将你之前构建的机器人代码发布到新创建的 Web 应用机器人服务。

> [!NOTE] 
> 每次更改机器人解决方案/代码时, 都必须将机器人发布到 Azure 服务。

1.  返回到你之前创建的 Visual Studio 解决方案。 
2.  右键单击 " **MyBot** " 项目, 在 "**解决方案资源管理器**", 然后单击 "**发布**"。

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-16.png)

3.  在 "*选取发布目标*" 页上, 单击 "**应用服务**", 然后**选择 "现有**", 最后单击 "**创建配置文件**" (如果不可见, 则可能需要单击 "*发布*" 按钮旁的下拉箭头)。

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-17.png)

4. 如果尚未登录到 Microsoft 帐户, 则必须在此处执行此操作。
5. 在 "**发布**" 页上, 你将发现你必须设置用于*Web 应用程序机器人*服务创建的同一**订阅**。 然后, 将 "**视图**" 设置为 "**资源组**", 并在下拉文件夹结构中, 选择之前创建的**资源组**。 单击 **“确定”** 。 

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-18.png)

6.  现在, 单击 "**发布**" 按钮, 并等待机器人发布 (可能需要几分钟时间)。

    ![将机器人发布到 Azure Web 应用机器人服务](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>第4章–设置 Unity 项目

下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

1.  打开*Unity* , 并单击 "**新建**"。 

    ![设置 Unity 项目](images/AzureLabs-Lab312-20.png)

2.  现在需要提供 Unity 项目名称。 插入**Hololens 机器人**。 请确保将项目模板设置为**3d**。 将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![设置 Unity 项目](images/AzureLabs-Lab312-21.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑 > 首选项**", 然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![设置 Unity 项目](images/AzureLabs-Lab312-22.png)

4.  接下来, 转到 "**文件 > 生成设置**", 选择 "**通用 Windows 平台**", 然后单击 "**切换平台**" 按钮以应用所选内容。

    ![设置 Unity 项目](images/AzureLabs-Lab312-23.png)

5.  尽管仍处于**文件 > 生成设置**, 但请确保:

    1.  **目标设备**设置为**Hololens**

        > 对于沉浸式耳机, 将 "**目标设备**" 设置为 "*任何设备*"。

    2.  **生成类型**设置为**D3D**

    3.  **SDK**设置为 "**最新安装**"

    4.  **Visual Studio 版本**设置为 "**最新安装**"

    5.  "**生成并运行**" 设置为 "**本地计算机**"

    6.  保存场景并将其添加到生成中。 

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。
        
            ![设置 Unity 项目](images/AzureLabs-Lab312-24.png)

        2. 为此创建新文件夹, 并为将来的任何场景创建一个新文件夹, 然后选择 "**新建文件夹**" 按钮以创建新文件夹, 将其命名为**场景**。

             ![设置 Unity 项目](images/AzureLabs-Lab312-25.png)

        3. 打开新创建的**场景**文件夹, 然后*在 "文件名*: 文本" 字段中, 键入**BotScene**, 然后单击 "**保存**"。

            ![设置 Unity 项目](images/AzureLabs-Lab312-26.png)

    7. 现在, "**生成设置**" 中的其余设置应保留为默认值。

6. 在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。 

    ![设置 Unity 项目](images/AzureLabs-Lab312-27.png)

7. 在此面板中, 需要验证几项设置:

    1. 在 "**其他设置**" 选项卡中:

        1. **脚本运行时版本**应为**试验性 (NET 4.6 等效项)** ;更改此要求将需要重新启动编辑器。
        2. **脚本编写后端**应为 **.net**
        3. **API 兼容级别**应为 **.net 4.6**

            ![设置 Unity 项目](images/AzureLabs-Lab312-28.png)
      
    2. 在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:

        - **InternetClient**
        - **十分**

            ![设置 Unity 项目](images/AzureLabs-Lab312-29.png)

    3. 在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。

        ![设置 Unity 项目](images/AzureLabs-Lab312-30.png)

8.  "返回*生成设置* _" C# Unity_项目不再灰显;勾选此的旁边的复选框。 
9.  关闭 "生成设置" 窗口。
10. 保存场景和项目 (**file > SAVE 场景/file > SAVE project**)。


## <a name="chapter-5--camera-setup"></a>第5章–照相机设置

> [!IMPORTANT]
> 如果要跳过本课程的*Unity 设置*组件, 并继续直接进入代码, 请随时下载[312 此 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), 将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目, 然后继续从[第7章](#chapter-7-–-create-the-botobjects-class):

1.  在 "*层次结构" 面板*中, 选择 "**摄像机**"。 
2.  选择后, 你将能够在 "*检查器" 面板*中看到**主相机**的所有组件。

    1. **照相机对象**必须命名为 "**主相机**" (请注意拼写)
    2. 必须将主相机**标记**设置为**MainCamera** (请注意拼写)
    3. 请确保将**转换位置**设置为**0, 0, 0**
    4. 将**清除标志**设置为**纯色**。
    5. 将相机组件的**背景**色设置为**黑色、Alpha 0 (十六进制代码: #00000000)**

    ![照相机设置](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>第6章–导入 Newtonsoft.json 库

为了帮助您反序列化和序列化接收并发送到机器人服务的对象, 您需要下载**newtonsoft.json**库。 你将在[此处找到已使用正确的 Unity 文件夹结构组织的兼容版本](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。 

若要将 Newtonsoft.json 库导入项目, 请使用本课程附带的 Unity 包。

1.  使用 "**资产** > **导入包** > **自定义包**" 菜单选项将*unitypackage*添加到 Unity。

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab312-34.png)

2.  在弹出的 "**导入 Unity 包**" 框中, 确保选择了 "所有" (并包括)**插件**。

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab312-35.png)

3.  单击 "**导入**" 按钮, 将项添加到项目。

4.  在项目视图中, 在 "**插件**" 下, 单击 " **newtonsoft.json** " 文件夹, 然后选择 "newtonsoft.json" 插件。

    ![](images/AzureLabs-Lab312-35b.png)

5.  选择 Newtonsoft.json 插件后, 请确保**未选中** **任何平台**, 并确保还**未选中**" **WSAPlayer** ", 然后单击 "**应用**"。 这只是为了确认已正确配置文件。

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > 标记这些插件会将它们配置为仅在 Unity 编辑器中使用。 在从 Unity 导出项目后, 将使用 WSA 文件夹中的一组不同的组。

6.  接下来, 需要在**newtonsoft.json**文件夹中打开**WSA**文件夹。 你将看到刚才配置的同一文件的副本。 选择该文件, 然后在 "检查器" 中, 确保
    -   **未选中** **任何平台** 
    -   **仅** **已选中** **WSAPlayer**
    -   不**检查** **进程**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>第7章–创建 BotTag

1.  创建名为**BotTag**的新的**标记**对象。 选择场景中的主相机。 单击 "检查器" 面板中的 "标记" 下拉菜单。 单击 "**添加标记**"。

    ![照相机设置](images/AzureLabs-Lab312-32.png)
 
2.  单击 **+** 符号。 将新**标记**命名为**BotTag**,*保存*。

    ![照相机设置](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **不要**将**BotTag**应用于主摄像机。 如果你意外地执行了此操作, 请确保将主相机标签更改回*MainCamera*。

## <a name="chapter-8--create-the-botobjects-class"></a>第8章–创建 BotObjects 类

你需要创建的第一个脚本是**BotObjects**类, 该类是一个空类, 它是一个空类, 可将一系列其他类对象存储在同一脚本中并由场景中的其他脚本访问。

此类的创建只是一种体系结构选择, 这些对象可以托管在你稍后将在本课程中创建的机器人脚本中。

若要创建此类: 

1.  右键单击 "*项目" 面板*, 然后**创建 > 文件夹**。 命名文件夹**脚本**。 

    ![创建脚本文件夹。](images/AzureLabs-Lab312-36.png)

2.  双击 "**脚本**" 文件夹将其打开。 然后在该文件夹中, 右键单击, 然后选择 "**创建C# > 脚本**"。 将脚本命名为**BotObjects**。 

3.  双击新的**BotObjects**脚本以通过**Visual Studio**打开它。

4.  删除脚本的内容, 并将其替换为以下代码:

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

6.  在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-9--create-the-gazeinput-class"></a>第9章–创建 GazeInput 类

要创建的下一个类是**GazeInput**类。 此类负责:

- 创建一个游标, 用来表示播放机的外观。
- 检测在播放机看上碰到的对象, 并保存对检测到的对象的引用。

若要创建此类: 

1.  中转到前面创建的 "**脚本**" 文件夹。 
2.  右键单击文件夹内部,**创建 > C#脚本**。 调用脚本**GazeInput**。 
3.  双击新的**GazeInput**脚本以通过**Visual Studio**打开它。
4.  在类名的顶部插入以下行:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  然后, 将以下变量添加到**GazeInput**类中的**Start ()** 方法之上:

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

6.  应添加**Start ()** 方法的代码。 当类初始化时, 将调用此操作:

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

7.  实现一个方法, 该方法将实例化并设置注视光标: 

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

8.  实现将从主相机设置 Raycast 的方法, 并跟踪当前聚焦的对象。

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
 
9.  在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-10--create-the-bot-class"></a>第10章–创建机器人类

现在要创建的脚本称为**机器人**。 这是应用程序的核心类, 它存储: 

- Web 应用机器人凭据
- 收集用户语音命令的方法
- 启动与 Web 应用机器人的会话所需的方法 
- 向 Web 应用机器人发送消息所需的方法 

若要将消息发送到机器人服务, **SendMessageToBot ()** 协同程序将生成一个活动, 该活动是由 Bot 框架识别为用户发送的数据的对象。 
 
若要创建此类: 

1. 双击 "**脚本**" 文件夹以将其打开。 
2. 右键单击 "**脚本**" 文件夹中, 单击 "**创建C# > 脚本**"。 将脚本**Bot**命名为。 
3. 双击新脚本以通过 Visual Studio 将其打开。
4. 在**机器人**类的顶部, 将命名空间更新为与以下相同:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. 在**机器人**类中添加以下变量:

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
    > 请确保将你的**机器人机密密钥**插入到**botSecret**变量。 你将已记下你 **智能机器人应用程序机密密钥** 在本课程中，开头中 **[第 2 章](#chapter-2---create-the-azure-bot-service)，第 10 步** 。

7. 现在需要添加**唤醒 ()** 和**Start ()** 的代码。 

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

8. 添加语音捕获开始和结束时由语音库调用的两个处理程序。 当用户停止说话时, *DictationRecognizer*将自动停止捕获用户语音。

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

1. 下面的处理程序收集用户语音输入的结果, 并调用负责将消息发送到 Web 应用机器人服务的协同程序。

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

10. 调用以下协同程序来开始与机器人的对话。 你会注意到, 一旦完成会话调用, 它将通过传递一系列参数 (将活动设置为以空消息形式发送到机器人服务) 来调用**SendMessageToCoroutine ()** 。 这样做是为了提示机器人服务启动对话框。

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

11. 调用以下协同程序生成要发送到机器人服务的活动。 

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

12. 在将活动发送到机器人服务后, 调用以下协同程序来请求响应。 

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

13. 要添加到此类中的最后一个方法是在场景中显示消息所必需的:

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
    > 你可能会在 Unity 编辑器控制台中看到一个错误, 缺少**SceneOrganiser**类。 请忽略此消息, 因为稍后会在本教程中创建此类。

14.  在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-11--create-the-interactions-class"></a>第11章–创建交互类

现在要创建的类称为**交互**。 此类用于检测 HoloLens 点击用户的输入。 

如果用户在查看场景中的*机器人*对象时点击, 并准备好侦听语音输入, 则机器人对象会将颜色更改为**红色**, 并开始侦听语音输入。 

此类继承自**GazeInput**类, 因此, 可以从该类引用**Start ()** 方法和变量, 这是通过使用**base**表示的。 
 
若要创建此类:

1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中, 单击 "**创建C# > 脚本**"。 命名脚本**交互**。 
3.  双击新脚本以通过 Visual Studio 将其打开。
4.  在**交互**类的顶部, 将命名空间和类继承更新为与以下相同:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  在**交互**类中添加以下变量:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  然后添加**Start ()** 方法:

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

7.  添加当用户在 HoloLens 相机前面执行分流手势时触发的处理程序

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

8. 在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-12--create-the-sceneorganiser-class"></a>第12章–创建 SceneOrganiser 类

此实验室中所需的最后一个类称为**SceneOrganiser**。 此类将通过将组件和脚本添加到主相机并在场景中创建相应的对象, 以编程方式设置场景。
 
若要创建此类:

1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中, 单击 "**创建C# > 脚本**"。 将脚本命名为**SceneOrganiser**。 
3.  双击新脚本以通过 Visual Studio 将其打开。
4.  在**SceneOrganiser**类中, 添加以下变量:

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

6.  然后添加**唤醒 ()** 和**Start ()** 方法:

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

7.  添加以下方法, 负责在场景中创建机器人对象并设置参数和组件:

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

7.  添加以下方法, 负责在场景中创建 UI 对象, 以表示来自机器人的响应:

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

8.  在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。
9.  在 Unity 编辑器中, 将 " **SceneOrganiser** " 脚本从 "脚本" 文件夹拖到主摄像机。 场景 Organiser 组件现在应显示在 "照相机" 对象上, 如下图所示。

    ![创建 Azure Bot 服务](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>第13章–生成之前

若要对应用程序进行全面测试, 需要将其旁加载到 HoloLens。
在执行此操作之前, 请确保:

-   [**第4章**](#Chapter-4-–-Set-up-the-unity-project)中提到的所有设置都已正确设置。 
-   脚本**SceneOrganiser**已附加到**摄像机主**对象。 
-   在**机器人**类中, 请确保已将**机器人机密密钥**插入到**botSecret**变量。

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>第14章–生成并旁加载到 HoloLens

此项目的 Unity 部分所需的所有内容现在均已完成, 因此可以从 Unity 构建它。

1.  导航到 "**生成设置**", "**文件 > 生成设置 ...** "。
2.  在**生成设置**窗口中, 单击 "**生成**"。

    ![从 Unity 生成应用](images/AzureLabs-Lab312-38.png)

3.  如果尚未这样做, 请勾选**Unity C#项目**。
4.  单击“生成” 。 Unity 将启动**文件资源管理器**窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为**应用**。 选择**应用**文件夹后, 单击 "**选择文件夹**"。 
5.  Unity 将开始向**应用**文件夹生成项目。 
6.  Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "**文件资源管理器**" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。

## <a name="chapter-15--deploy-to-hololens"></a>第15章–部署到 HoloLens

在 HoloLens 上部署:

1.  你将需要 HoloLens 的 IP 地址 (用于远程部署), 并确保你的 HoloLens 处于**开发人员模式**。 要实现此目的，请执行以下操作：

    1. 在戴上 HoloLens 的同时, 请打开**设置**。
    2. 中转到**网络 & Internet > wi-fi > 高级选项**
    3. 记下**IPv4**地址。
    4. 接下来, 导航回 "**设置**", 然后为**开发人员更新 & Security >** 
    5. 设置开发人员模式。

2.  导航到新的 Unity 生成 (**应用**文件夹), 并在**Visual Studio**中打开解决方案文件。
3.  在**解决方案配置**中, 选择 "**调试**"。
4.  在**解决方案平台**中, 选择 " **X86**,**远程计算机**"。 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab312-39.png)
 
5.  请在 "**生成" 菜单**中, 单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。
6.  应用现在应显示在你的 HoloLens 上已安装的应用列表中, 可以启动了!

    > [!NOTE]
    > 若要部署到沉浸式耳机, 请将 "**解决方案平台**" 设置为 "*本地计算机*", 并将**配置**设置为 "*调试*", 将 " *x86* " 设置为**平台**。 然后, 使用 "**生成" 菜单**选择 "*部署解决方案*", 将部署到本地计算机。 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>第16章–在 HoloLens 上使用应用程序

- 启动应用程序后, 会看到机器人作为你前面的蓝色球。

- 在 gazing 时使用**点击手势**来启动会话。 
 
- 等待会话启动 (在发生此情况时, UI 将显示一条消息)。 收到来自机器人的介绍性消息后, 再次在机器人上点击, 使其变为红色并开始倾听你的声音。 

- 停止对话后, 应用程序会将消息发送到机器人, 并立即收到将在 UI 中显示的响应。 

- 重复此过程, 将更多的消息发送到机器人 (必须在每次想要 sen 邮件时点击一次)。

此对话演示了机器人如何保留信息 (你的姓名), 同时还提供了已知信息 (如已贮存的项目)。

#### <a name="some-questions-to-ask-the-bot"></a>询问机器人的一些问题:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>已完成的 Web 应用机器人 (v4) 应用程序

恭喜, 你构建了一个利用 Azure Web 应用机器人、Microsoft Bot Framework v4 的混合现实应用。

![最终产品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

此实验室中的会话结构非常基本。 使用 Microsoft LUIS 为机器人指定自然语言理解功能。

### <a name="exercise-2"></a>练习2

此示例不包括终止会话和重新启动新会话。 若要使机器人功能完成, 请尝试将结束实现到会话中。
