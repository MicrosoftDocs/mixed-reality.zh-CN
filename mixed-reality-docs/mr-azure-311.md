---
title: MR 和 Azure 311-Microsoft Graph
description: 完成本课程, 了解如何利用 Microsoft Graph, 并在混合现实应用程序中连接到用于驱动工作效率的数据。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, microsoft graph, hololens, 沉浸, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694529"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

# <a name="mr-and-azure-311---microsoft-graph"></a>MR 和 Azure 311-Microsoft Graph

在本课程中, 你将了解如何使用*Microsoft Graph*在混合现实应用程序中使用安全身份验证登录到 Microsoft 帐户。 然后, 你将在应用程序界面中检索并显示你的计划会议。

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph*是一组 api, 旨在实现对许多 Microsoft 服务的访问。 Microsoft 将 Microsoft Graph 描述为一系列按关系连接的资源, 这意味着, 应用程序可以访问所有种类的已连接用户数据。 有关详细信息, 请访问[Microsoft Graph 页](https://developer.microsoft.com/graph)。

开发过程中, 将会创建一个应用程序, 在该应用程序中, 用户将会被指示到, 然后点击一个球, 这将提示用户安全登录到 Microsoft 帐户。 登录到帐户后, 用户将能够看到一天计划的会议列表。

完成本课程后, 你将拥有一个混合现实 HoloLens 应用程序, 该应用程序将能够执行以下操作:

1.  使用点击手势, 点击对象, 这将提示用户登录到 Microsoft 帐户 (移出应用程序以登录, 然后再次返回到应用)。
2.  查看当天计划的会议列表。 

在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 311:Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>系统必备

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外, 请注意, 本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容 (2018 年7月)。 你可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件:

- 开发 PC
- [Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 已启用开发人员模式的[Microsoft HoloLens](hololens-hardware-details.md)
- Azure 安装和 Microsoft Graph 数据检索的 Internet 访问
- 有效的**Microsoft 帐户**(个人或工作/学校)
- 使用同一个 Microsoft 帐户安排当天计划的几个会议

### <a name="before-you-start"></a>开始之前

1.  为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。
2.  设置并测试你的 HoloLens。 如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。 

有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens)。

有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>第1章-在应用程序注册门户中创建应用

首先, 需要在**应用程序注册门户**中创建并注册应用程序。

在本章中, 你还将找到服务密钥, 你可以通过它调用*Microsoft Graph*来访问你的帐户内容。

1.  导航到[Microsoft 应用程序注册门户](https://apps.dev.microsoft.com)并登录到你的 microsoft 帐户。 登录后, 将重定向到**应用程序注册门户**。

2.  在 "**我的应用程序**" 部分中, 单击 "**添加应用**" 按钮。

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **应用程序注册门户**的外观可能会不同, 具体取决于你之前是否使用过*Microsoft Graph*。 下面的屏幕截图显示这些不同版本。

3.  添加应用程序的名称, 然后单击 "**创建**"。

    ![](images/AzureLabs-Lab311-03.png)

4.  创建应用程序后, 将重定向到应用程序主页。 复制 "**应用程序 Id** ", 并确保在 "安全" 的位置记录此值, 并在代码中立即使用。

    ![](images/AzureLabs-Lab311-04.png)

5.  在 "**平台**" 部分中, 确保显示 "**本机应用程序**"。 如果*未*单击 "**添加平台**", 请选择 "**本机应用程序**"。

    ![](images/AzureLabs-Lab311-05.png)

6.  在同一页中向下滚动, 并在 " **Microsoft Graph 权限**" 部分中向下滚动, 你将需要为应用程序添加其他权限。 单击 "**委派权限**" 旁的 "**添加**"。

    ![](images/AzureLabs-Lab311-06.png)

7.  由于你希望你的应用程序访问用户的日历, 因此**选中名为**Calendar 的框, 然后单击 **"确定"** 。

    ![](images/AzureLabs-Lab311-07.png)

8.  滚动到底部, 然后单击 "**保存**" 按钮。

    ![](images/AzureLabs-Lab311-08.png)

9.  你的保存将会得到确认, 你可以从**应用程序注册门户**注销。

## <a name="chapter-2---set-up-the-unity-project"></a>第2章-设置 Unity 项目

下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

1.  打开*Unity* , 并单击 "**新建**"。

    ![](images/AzureLabs-Lab311-09.png)

2.  需要提供 Unity 项目名称。 插入**MSGraphMR**。 请确保将项目模板设置为**3d**。 将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![](images/AzureLabs-Lab311-10.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑** > **首选项**", 然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![](images/AzureLabs-Lab311-11.png)

4.  转到 "**文件** > **生成设置**" 并选择 "**通用 Windows 平台**", 然后单击 "**切换平台**" 按钮以应用所选内容。

    ![](images/AzureLabs-Lab311-12.png)

5.  仍在**文件** > **生成设置**中时, 请确保:

    1. **目标设备**设置为**HoloLens**
    2. **生成类型**设置为**D3D**
    3. **SDK**设置为 "**最新安装**"
    4. **Visual Studio 版本**设置为 "**最新安装**"
    5. "**生成并运行**" 设置为 "**本地计算机**"
    6. 保存场景并将其添加到生成中。

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。

            ![](images/AzureLabs-Lab311-13.png)

        2. 为此以及任何将来的场景创建新文件夹。 选择 "**新建文件夹**" 按钮, 创建一个新文件夹, 将其命名为**场景**。

            ![](images/AzureLabs-Lab311-14.png)

        3. 打开新创建的**场景**文件夹, 然后在 "文件名 *: 文本*" 字段中, 键入**MR_ComputerVisionScene**, 然后单击 "**保存**"。

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > 请注意, 必须将 Unity 场景保存在 "*资产*" 文件夹中, 因为它们必须与 Unity 项目相关联。 创建场景文件夹 (以及其他类似文件夹) 是构造 Unity 项目的典型方式。

    7.  现在, "*生成设置*" 中的其余设置应保留为默认值。

6.  在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。 

    ![](images/AzureLabs-Lab311-16.png)

7. 在此面板中, 需要验证几项设置:

    1. 在 "**其他设置**" 选项卡中:

        1.  **脚本编写** **运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。

        2. **脚本编写后端**应为 **.net**

        3. **API 兼容级别**应为 **.net 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 查看**支持的虚拟现实**, 确保已添加**Windows Mixed reality SDK** 。

        ![](images/AzureLabs-Lab311-19.png)

8.  返回*生成设置*, *Unity C#项目*不再灰显;选中此旁边的复选框。

9.  关闭 "*生成设置*" 窗口。

10.  保存场景和项目 (**文件** > **保存场景/文件** > **保存项目**)。

## <a name="chapter-3---import-libraries-in-unity"></a>第3章-在 Unity 中导入库

> [!IMPORTANT]
> 如果要跳过本课程的*Unity 设置*组件, 并继续直接进入代码, 请随时下载此[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), 将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目, 然后从[第5章继续](#chapter-5---create-meetingsui-class).

若要在 Unity 内使用*Microsoft Graph* , 需要**使用 "** 但是, 可以使用 Microsoft Graph SDK, 但在生成 Unity 项目后, 它将要求添加 NuGet 包 (这意味着编辑项目后期生成)。 将所需的 Dll 直接导入到 Unity 中是更简单的方法。

> [!NOTE]
> 当前 Unity 中存在一个已知问题, 需要在导入后重新配置插件。 解决 bug 后, 将不再需要这些步骤 (本部分中的 4-7)。

若要将*Microsoft Graph*导入到自己的项目中, 请[下载 MSGraph_LabPlugins 文件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)。 已使用经过测试的库版本创建此包。

如果希望了解有关如何将自定义 Dll 添加到 Unity 项目的详细信息, 请[访问此链接](https://docs.unity3d.com/Manual/UsingDLL.html)。

导入包:

1.  使用 "**资产** > **导入包** > **自定义包**" 菜单选项将 unity 包添加到 unity。 选择刚刚下载的包。

2.  在弹出的 "**导入 Unity 包**" 框中, 确保选择了 "所有" (并包括)**插件**。

    ![](images/AzureLabs-Lab311-20.png)

3.  单击 "**导入**" 按钮, 将项添加到项目。

4.  在 "*项目" 面板*中的 "**插件**" 下, 单击 " **MSGraph** " 文件夹, 然后**选择名为**"" 的插件。

    ![](images/AzureLabs-Lab311-21.png)

5.  选择该*插件*后, 请确保未选中**任何平台**, 然后确保**WSAPlayer**未被选中, 然后单击 "**应用**"。 这只是为了确认已正确配置文件。

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 标记这些插件会将它们配置为仅在 Unity 编辑器中使用。 在将项目从 Unity 导出为通用 Windows 应用程序之后, WSA 文件夹中将使用不同的 Dll 集。

6.  接下来, 需要在**MSGraph**文件夹中打开**WSA**文件夹。 你将看到刚才配置的同一文件的副本。 选择该文件, 然后在检查器中:

    -   请确保**未选中** **任何平台**, 并且**仅** **选中** **WSAPlayer** 。

    -   确保将**SDK**设置为**UWP**, 并将 "**脚本后端**" 设置为 "**点网络**"

    -   确保**选中**"**不处理**"。

        ![](images/AzureLabs-Lab311-23.png)

7.  单击 **“应用”** 。

## <a name="chapter-4---camera-setup"></a>第4章-照相机设置

在本章中, 你将设置场景的主照相机:

1.  在 "*层次结构" 面板*中, 选择 "**摄像机**"。

2.  选择后, 你将能够在 "*检查器*" 面板中看到**主相机**的所有组件。

    1.  **照相机对象**必须命名为 "**主相机**" (请注意拼写正确!)

    2.  必须将主相机**标记**设置为**MainCamera** (请注意拼写!)

    3.  请确保将**转换位置**设置为**0, 0, 0**

    4.  将**清除标志**设置为**纯色**

    5.  将相机组件的**背景色**设置为**黑色、Alpha 0** **(十六进制代码: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  "*层次结构" 面板*中的最后一个对象结构应类似于下图所示:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>第5章-创建 MeetingsUI 类

需要创建的第一个脚本是**MeetingsUI**, 负责承载和填充应用程序的 UI (欢迎消息、说明和会议详细信息)。

若要创建此类:

1.  右键单击 "*项目" 面板*中的 "**资产**" 文件夹, 然后选择 "**创建** > **文件夹**"。 命名文件夹**脚本**。

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  打开 "**脚本**" 文件夹, 然后在该文件夹中右键单击 "**创建** >   **C#脚本**"。 将脚本命名为**MeetingsUI。**

    ![](images/AzureLabs-Lab311-28.png)

3.  双击新的**MeetingsUI**脚本以通过*Visual Studio*打开它。

4.  插入以下命名空间:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  在类中插入以下变量:

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

6.  然后替换**Start ()** 方法并添加一个**唤醒 ()** 方法。 当类初始化时, 将调用以下内容:

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

7.  添加负责创建*会议 UI*的方法, 并在请求时向其填充当前会议:

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

8. **删除** **Update ()** 方法, 并在 Visual Studio 返回到 Unity 之前**保存更改**。 

## <a name="chapter-6---create-the-graph-class"></a>第6章-创建图形类

要创建的下一个脚本是**图形**脚本。 此脚本负责进行调用以对用户进行身份验证, 并从用户日历中检索当天的计划会议。

若要创建此类:

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中, 单击 "**创建** >   **C#脚本**"。 将脚本命名为**Graph**。

3.  双击脚本以通过 Visual Studio 打开它。

4.  插入以下命名空间:

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
    > 你将注意到, 此脚本中的部分代码围绕[预编译指令](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)环绕, 这是为了避免生成 Visual Studio 解决方案时库出现问题。

5.  删除**Start ()** 和**Update ()** 方法, 因为它们不会被使用。

6.  在**图形**类外部, 插入以下对象, 这些对象是反序列化表示每日计划会议的 JSON 对象所必需的:

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

7.  在**图形**类中, 添加以下变量:

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
    > 更改 **appId** 值为 **应用程序 Id** 中记下 **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)，步骤 4** 。 此值应与应用程序注册页面中显示的应用程序注册**门户**中的值相同。

8.  在**Graph**类中, 添加方法**SignInAsync ()** 和**AquireTokenAsync ()** , 这将提示用户插入登录凭据。

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

9.  添加以下两个方法:

    1.  **BuildTodayCalendarEndpoint ()** , 用于生成指定在其中检索计划会议的日期和时间范围的 URI。

    2.  **ListMeetingsAsync ()** , 它从*Microsoft Graph*请求计划会议。

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

10. 你现在已经完成了**图形**脚本。 在返回到 Unity 之前, 在 Visual Studio 中**保存更改**。

## <a name="chapter-7---create-the-gazeinput-script"></a>第7章-创建 GazeInput 脚本

现在会创建**GazeInput**。 此类处理并跟踪用户的注视, 并使用**Raycast**来自**主摄像机**的 "向前投影"。

创建脚本:

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中, 单击 "**创建** >   **C#脚本**"。 将脚本命名为**GazeInput**。

3.  双击脚本以通过 Visual Studio 打开它。

4.  更改命名空间代码以匹配下面的代码, 并 **\[将 "\]** GazeInput" 标记添加到你的类的上方, 以便能够对其进行序列化:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  在**GazeInput**类中, 添加以下变量:

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

6.  将**CreateCursor ()** 方法添加到场景中, 并从**Start ()** 方法调用方法:

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

7.  下面的方法可启用注视 Raycast 并跟踪聚焦对象。

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

8.  在返回到 Unity 之前, 在 Visual Studio 中**保存更改**。

## <a name="chapter-8---create-the-interactions-class"></a>第8章-创建交互类

你现在需要创建**交互**脚本, 该脚本负责:

-   处理**点击**交互和**照相机注视**, 使用户能够与场景中的 "button" 中的日志交互。

-   在场景中的 "button" 对象中创建用于用户交互的日志。

创建脚本:

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中, 单击 "**创建** >   **C#脚本**"。 命名脚本**交互**。

3.  双击脚本以通过 Visual Studio 打开它。

4.  插入以下命名空间:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  将**交互**类的继承从*MonoBehaviour*更改为**GazeInput**。

    ~~公共类交互:MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  在**交互**类中插入以下变量:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  替换**Start**方法;请注意, 它是一个重写方法, 它调用 "基" 注视类方法。 在类初始化、注册输入识别并在场景中创建 "登录"*按钮*时, 将调用**Start ()** :

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

8.  添加**CreateSignInButton ()** 方法, 该方法将实例化场景中的 "登录"*按钮*并设置其属性:

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

9.  添加**GestureRecognizer_Tapped ()** 方法, 该方法将响应*点击*用户事件。

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

10. **删除** **Update ()** 方法, 然后在 Visual Studio 中**保存更改**, 然后返回到 Unity。

## <a name="chapter-9---set-up-the-script-references"></a>第9章-设置脚本引用

在本章中, 需要将**交互**脚本放到**主摄像机**上。 然后, 该脚本会处理需要的其他脚本。

-  从 "*项目" 面板*的 "**脚本**" 文件夹中, 将脚本**交互**拖动到 "**相机**" 对象, 如下图所示。

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>第10章-设置标记

处理注视的代码将使用标记**SignInButton**来标识用户将与之交互的对象, 以便登录*Microsoft Graph*。

若要创建标记:

1.  在 Unity 编辑器中, 单击 "*层次结构" 面板*中的**主相机**。

2.  在*检查器面板*中, 单击 " **MainCamera** "*标记*以打开下拉列表。 单击 "**添加标记 ...** "

    ![](images/AzureLabs-Lab311-30.png)

3.  单击 **+** 按钮。

    ![](images/AzureLabs-Lab311-31.png)

4.  将标记名称写入为**SignInButton** , 然后单击 "保存"。

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>第11章-将 Unity 项目生成到 UWP

此项目的 Unity 部分所需的所有内容现在均已完成, 因此可以从 Unity 构建它。

1.  导航到 *生成设置* (**文件*>*生成设置**)。

    ![](images/AzureLabs-Lab311-33.png)

2.  如果尚未这样做, 请勾选 **\# Unity C 项目**。

3.  单击“生成” 。 Unity 将启动**文件资源管理器**窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为**应用**。 选择**应用**文件夹后, 单击 "**选择文件夹**"。

4.  Unity 将开始向**应用**文件夹生成项目。

5.  Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "**文件资源管理器**" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。

## <a name="chapter-12---deploy-to-hololens"></a>第12章-部署到 HoloLens

在 HoloLens 上部署:

1.  你将需要 HoloLens 的 IP 地址 (用于远程部署), 并确保你的 HoloLens 处于**开发人员模式。** 要实现此目的，请执行以下操作：

    1.  在戴上 HoloLens 的同时, 请打开**设置**。

    2.  中转到**网络 & Internet** > **wi-fi** > **高级选项**

    3.  记下**IPv4**地址。

    4.  接下来, 导航回 "**设置**", 然后为**开发人员** **更新 & 安全性** > 

    5.  设置**开发人员模式**。

2.  导航到新的 Unity 生成 (**应用**文件夹), 并在**Visual Studio**中打开解决方案文件。

3.  在**解决方案配置**中, 选择 "**调试**"。

4.  在**解决方案平台**中, 选择 " **X86, 远程计算机**"。 系统将提示你插入远程设备的**IP 地址**(在本例中, 你记下了此项)。

    ![](images/AzureLabs-Lab311-34.png)

5.  中转到 "**生成**" 菜单, 然后单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。

6.  应用现在应显示在你的 HoloLens 上已安装的应用列表中, 可以启动了!

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens 应用程序

恭喜, 你构建了一个利用 Microsoft Graph 的混合现实应用来读取和显示用户日历数据。

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

使用 Microsoft Graph 显示有关用户的其他信息

-   用户电子邮件/电话号码/个人资料图片

### <a name="exercise-1"></a>练习1

实现语音控制以导航 Microsoft Graph UI。
