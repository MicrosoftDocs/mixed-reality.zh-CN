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
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

# <a name="mr-and-azure-311---microsoft-graph"></a>MR 和 Azure 311-Microsoft Graph

在本课程中，您将学习如何使用*Microsoft Graph*登录到 Microsoft 帐户使用混合的现实应用程序中的安全身份验证。 然后，将检索，并在应用程序界面中显示计划的会议。

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph*是一组 Api 设计用于启用对很多 Microsoft 服务的访问。 Microsoft 介绍 Microsoft Graph 为矩阵的资源通过关系连接，也就是说，它允许应用程序访问各种类型的连接的用户数据。 有关详细信息，请访问[Microsoft Graph 页](https://developer.microsoft.com/graph)。

开发将包括会指导用户以注视，然后点击球体，会提示用户以安全地登录到 Microsoft 帐户应用的创建。 登录到他们的帐户，用户将能够查看当天的计划会议的列表。

已完成本课程，您将具有混合的现实 HoloLens 应用程序，将能够执行以下操作：

1.  使用手势，点击一个对象，它会提示用户能够登录到 Microsoft 帐户 （移出应用程序，以用户身份登录，然后返回到应用程序）。
2.  查看当天的计划会议的列表。 

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务集成与你的 Unity 项目。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 311:Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。

我们建议以下硬件和软件本课程：

- 开发计算机
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- Internet 访问的 Azure 设置和 Microsoft Graph 数据检索
- 一个有效**的 Microsoft 帐户**（个人或工作/学校）
- 几个会议计划为当前日期，使用相同的 Microsoft 帐户

### <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。 

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>第 1 章-在应用程序注册门户中创建您的应用程序

开始时，你将需要创建并注册你的应用程序中**应用程序注册门户**。

本章还会发现服务密钥，您可以调用*Microsoft Graph*访问你帐户的内容。

1.  导航到[Microsoft 应用程序注册门户](https://apps.dev.microsoft.com)，并使用你的 Microsoft 帐户登录。 你已登录后，你将重定向到**应用程序注册门户**。

2.  在中**我的应用程序**部分中，单击按钮**添加应用**。

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **应用程序注册门户**颜色可能有所不同，具体取决于是否您以前使用过*Microsoft Graph*。 下面的屏幕截图显示这些不同的版本。

3.  为应用程序，单击添加名称**创建**。

    ![](images/AzureLabs-Lab311-03.png)

4.  一旦创建该应用程序后，你将重定向到应用程序主页面。 复制**应用程序 Id**并且请务必记下此值到某个安全位置，在代码中，将很快就使用它。

    ![](images/AzureLabs-Lab311-04.png)

5.  在中**平台**部分中，请确保**本机应用程序**显示。 如果*不*上单击**添加平台**，然后选择**本机应用程序**。

    ![](images/AzureLabs-Lab311-05.png)

6.  在同一页中和名为的部分中，向下滚动**Microsoft Graph 权限**将需要添加其他应用程序权限。 单击**外**旁边**委托的权限**。

    ![](images/AzureLabs-Lab311-06.png)

7.  由于您希望应用程序以访问用户的日历，检查调用框中**Calendars.Read**然后单击**确定**。

    ![](images/AzureLabs-Lab311-07.png)

8.  滚动到底部并单击**保存**按钮。

    ![](images/AzureLabs-Lab311-08.png)

9.  将确认你保存，并可以从注销**应用程序注册门户**。

## <a name="chapter-2---set-up-the-unity-project"></a>第 2 章-设置 Unity 项目

以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。

    ![](images/AzureLabs-Lab311-09.png)

2.  需要提供 Unity 项目名称。 插入**MSGraphMR**。 请确保项目模板设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![](images/AzureLabs-Lab311-10.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![](images/AzureLabs-Lab311-11.png)

4.  转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。

    ![](images/AzureLabs-Lab311-12.png)

5.  在仍处于**文件 > 生成设置**，请确保：

    1. **设备为目标**设置为**HoloLens**
    2. **生成的类型**设置为**D3D**
    3. **SDK**设置为**最新安装**
    4. **Visual Studio 版本**设置为**最新安装**
    5. **生成并运行**设置为**本地计算机**
    6. 保存场景，并将其添加到生成。

        1. 选择执行此**添加打开场景**。 保存窗口将显示。

            ![](images/AzureLabs-Lab311-13.png)

        2. 为此，和任何未来、 场景创建新文件夹。 选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![](images/AzureLabs-Lab311-14.png)

        3. 打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_ComputerVisionScene**，然后单击**保存**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > 请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。 创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。

    7.  中的剩余设置，*生成设置*，应暂时保留为默认值。

6.  在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。 

    ![](images/AzureLabs-Lab311-16.png)

7. 在此面板中，需要验证几个设置：

    1. 在中**其他设置**选项卡：

        1.  **脚本编写** **运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。

        2. **脚本编写后端**应为 **.NET**

        3. **API 兼容性级别**应为 **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，检查**虚拟现实支持**，请确保**Windows Mixed RealitySDK**添加。

        ![](images/AzureLabs-Lab311-19.png)

8.  回到*生成设置*， *UnityC#项目*不再灰显; 请查看这旁边的复选框。

9.  关闭*生成设置*窗口。

10.  保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。

## <a name="chapter-3---import-libraries-in-unity"></a>第 3 章-Unity 中的导入库

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5---create-meetingsui-class)。

若要使用*Microsoft Graph*在你需要进行的 Unity 中使用的**Microsoft.Identity.Client** DLL。 可以使用 Microsoft Graph SDK，但是，它将生成 Unity 项目 （即编辑项目的后期生成） 后需要添加 NuGet 包。 它被认为更简单直接导入所需的 Dll 到 Unity。

> [!NOTE]
> 这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。 这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。

若要导入*Microsoft Graph*到你自己的项目， [MSGraph_LabPlugins.zip 文件下载](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)。 此包已创建具有版本已经过测试的库。

如果你想要了解有关如何将自定义 Dll 添加到你的 Unity 项目的详细信息[单击此链接](https://docs.unity3d.com/Manual/UsingDLL.html)。

若要将包导入：

1.  使用将 Unity 包添加到 Unity **资产* > *导入包* > *自定义包** 菜单选项。 选择刚下载的包。

2.  在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。

    ![](images/AzureLabs-Lab311-20.png)

3.  单击**导入**按钮将项添加到你的项目。

4.  转到**MSGraph**下的文件夹**插件**中*项目面板*，然后选择名为插件**Microsoft.Identity.Client**。

    ![](images/AzureLabs-Lab311-21.png)

5.  与*插件*选择，确保**Any 平台**处于未选中状态，然后确保**WSAPlayer**也是未选中，则单击**应用**. 这只是为了确认正确配置文件。

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 将标记这些插件将它们配置为仅使用在 Unity 编辑器中。 有一组不同的项目会导出从 Unity 为通用 Windows 应用程序后，将使用 WSA 文件夹中的 Dll。

6.  接下来，您需要打开**WSA**文件夹，在**MSGraph**文件夹。 您将看到刚配置的相同文件的副本。 选择该文件，然后在该检查器：

    -   确保**Any 平台**是**取消选中**，并且**仅** **WSAPlayer**是**检查**。

    -   请确保**SDK**设置为**UWP**，并**脚本编写后端**设置为 **.net**

    -   絋粄**不处理**是**检查**。

        ![](images/AzureLabs-Lab311-23.png)

7.  单击 **“应用”**。

## <a name="chapter-4---camera-setup"></a>第 4 章-照相机设置

在这一章期间将设置您的场景 Main Camera:

1.  在中*层次结构面板*，选择**Main Camera**。

2.  选择后，你将能够看到的所有组件**Main Camera**中*Inspector*面板。

    1.  **相机对象**必须命名为**Main Camera** （请注意拼写 ！）

    2.  Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）

    3.  请确保**转换位置**设置为**0，0，0**

    4.  设置**清除标志**到**纯色**

    5.  设置**背景色**的照相机组件**黑色、 Alpha 0** **(十六进制代码: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  中的最后一个对象结构*层次结构面板*应类似于下图中所示：

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>第 5 章-创建 MeetingsUI 类

您需要创建的第一个脚本是**MeetingsUI**，负责托管和填充 （欢迎消息、 说明和会议详细信息） 的应用程序的 UI。

若要创建此类：

1.  右键单击**资产**中的文件夹*项目面板*，然后选择 **创建*> *文件夹**。 将文件夹命名为**脚本**。

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  打开**脚本**文件夹然后，在该文件夹中，右键单击，**创建* > *C\# 脚本**。 脚本命名为**MeetingsUI。**

    ![](images/AzureLabs-Lab311-28.png)

3.  双击新**MeetingsUI**脚本以将其与打开*Visual Studio*。

4.  插入以下命名空间：

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  在类中插入以下变量：

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

6.  然后，替换**start （)** 方法并添加**Awake()** 方法。 类初始化时将会调用：

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

7.  添加方法负责创建*会议 UI*并使用当前的会议请求时填充它：

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

8. **删除** **update （)** 方法，和**保存所做的更改**之前返回到 Unity 的 Visual Studio 中。 

## <a name="chapter-6---create-the-graph-class"></a>章 6-创建图形类

要创建的下一步脚本位于**Graph**脚本。 此脚本负责进行调用以对用户进行身份验证和当前日期从用户的日历中检索已安排的会议。

若要创建此类：

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。 脚本命名为**Graph**。

3.  双击要使用 Visual Studio 中打开的脚本。

4.  插入以下命名空间：

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
    > 你会注意到在此脚本中代码的部分封装[预编译指令](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)，这是为了避免生成 Visual Studio 解决方案时出现问题的库。

5.  删除**start （)** 并**update （)** 方法，因为它们不会使用。

6.  外侧**Graph**类中，插入下列所需表示每日计划的会议的 JSON 对象反序列化的对象：

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

7.  内部**Graph**类中，添加以下变量：

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
    > 更改 **appId** 值为 **应用程序 Id** 中记下 **[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)，步骤 4** 。 此值应与中显示的相同**应用程序注册门户**在您的应用程序注册页中。

8.  内**Graph**类中，将方法添加**SignInAsync()** 并**AquireTokenAsync()**，用于将提示用户插入登录凭据。

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

9.  添加以下两种方法：

    1.  **BuildTodayCalendarEndpoint()**，哪些生成指定日和时间跨度内，在其中检索计划的会议的 URI。

    2.  **ListMeetingsAsync()**，该请求来自已安排的会议*Microsoft Graph*。

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

10. 现在已完成**Graph**脚本。 **保存所做的更改**之前返回到 Unity 的 Visual Studio 中。

## <a name="chapter-7---create-the-gazeinput-script"></a>章 7-创建 GazeInput 脚本

现在将创建**GazeInput**。 此类处理和跟踪的用户的视线移动，使用**Raycast**来自**Main Camera**前, 滚投影。

若要创建脚本：

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。 脚本命名为**GazeInput**。

3.  双击要使用 Visual Studio 中打开的脚本。

4.  更改命名空间代码，以匹配所示，以及添加 '**\[System.Serializable\]** 上面标记您**GazeInput**类，以便它可以序列化：

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  内部**GazeInput**类中，添加以下变量：

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

6.  添加**CreateCursor()** 方法以在场景中，创建 HoloLens 游标并调用方法中的，从**start （)** 方法：

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

7.  以下方法启用注视 Raycast 并跟踪的已设定焦点的对象。

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

8.  **保存所做的更改**之前返回到 Unity 的 Visual Studio 中。

## <a name="chapter-8---create-the-interactions-class"></a>章 8-创建交互类

您现在需要创建**交互**脚本，它负责：

-   处理**点击**交互并**照相机注视**，这使用户能够与场景中的"按钮"中的日志进行交互。

-   要与之交互的用户场景中的"按钮"对象中创建日志。

若要创建脚本：

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。 脚本命名为**交互**。

3.  双击要使用 Visual Studio 中打开的脚本。

4.  插入以下命名空间：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  更改的继承**交互**类派生*MonoBehaviour*到**GazeInput**。

    ~~公共类的交互：MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  内部**交互**类插入以下变量：

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  替换**启动**方法; 请注意，它是一个替代方法，它调用 base 的视线移动类方法。 **Start （)** 类初始化输入识别的注册和创建的登录时将调用*按钮*场景中：

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

8.  添加**CreateSignInButton()** 方法，将实例化的登录*按钮*场景中并设置其属性：

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

9.  添加**GestureRecognizer_Tapped()** 方法，为响应*点击*用户事件。

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

10. **删除** **update （)** 方法，然后**保存所做的更改**之前返回到 Unity 的 Visual Studio 中。

## <a name="chapter-9---set-up-the-script-references"></a>第 9 章 — 设置脚本引用

您需要将放在本章**交互**拖动到脚本**Main Camera**。 然后，该脚本将处理放置他们需要为其他脚本。

-  从**脚本**中的文件夹*项目面板*，将脚本**交互**到**Main Camera**对象，如如下图所示。

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>第 10 章 — 设置标记

处理的视线移动的代码将使用标记**SignInButton**若要确定哪个对象的用户将与之交互来登录到*Microsoft Graph*。

若要创建标记：

1.  在 Unity 编辑器中单击**Main Camera**中*层次结构面板*。

2.  在中*检查器面板*上单击**MainCamera** *标记*打开下拉列表。 单击**添加标记...**

    ![](images/AzureLabs-Lab311-30.png)

3.  单击 **+** 按钮。

    ![](images/AzureLabs-Lab311-31.png)

4.  写入形式的标记名称**SignInButton**并单击保存。

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>第 11 章 — 生成到 UWP 的 Unity 项目

此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。

1.  导航到 *生成设置* (**文件* > *生成设置**)。

    ![](images/AzureLabs-Lab311-33.png)

2.  如果尚不存在，则勾选**Unity C\#项目**。

3.  单击“生成” 。 将启动 unity**文件资源管理器**窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名**应用**。 然后使用**应用程序**文件夹选择，单击**选择文件夹**。

4.  Unity 将开始构建您的项目**应用**文件夹。

5.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

## <a name="chapter-12---deploy-to-hololens"></a>章 12-将部署到 HoloLens

若要部署在 HoloLens 上：

1.  你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式。** 要实现此目的，请执行以下操作：

    1.  戴上您 HoloLens，同时打开**设置**。

    2.  转到**网络和 Internet** > **的 Wi-fi** > **高级选项**

    3.  请注意**IPv4**地址。

    4.  接下来，导航回到**设置**，然后**更新和安全** > **面向开发人员**

    5.  设置**上的开发人员模式**。

2.  导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。

3.  在中**解决方案配置**选择**调试**。

4.  在中**解决方案平台**，选择**x86，远程计算机**。 系统会提示要插入**IP 地址**的远程设备 (HoloLens，在这种情况下，记下)。

    ![](images/AzureLabs-Lab311-34.png)

5.  转到**构建**菜单，并单击**部署解决方案**旁加载到你 HoloLens 应用程序。

6.  在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens 应用程序

祝贺你，构建利用 Microsoft Graph，将读取并显示用户日历数据的混合的现实应用。

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

使用 Microsoft Graph 来显示有关用户的其他信息

-   用户电子邮件 / 电话号码 / 配置文件图片

### <a name="exercise-1"></a>练习 1

实现语音控件导航 Microsoft 图形 UI。
