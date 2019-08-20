---
title: MR 输入 211-手势
description: 按照以下编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 来了解手势概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 学院, 教程, 手势
ms.openlocfilehash: 694f51f1b56588e100d6d2676a8194d7e9936133
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559884"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

# <a name="mr-input-211-gesture"></a>MR 输入 211:手势

[手势](gestures.md)会使用户意向变为操作。 借助笔势, 用户可以与全息影像交互。 在本课程中, 我们将了解如何跟踪用户的动手, 响应用户输入, 并根据手头状态和位置向用户提供反馈。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

在[先生/女士 101](holograms-101.md)中, 我们使用了一种简单的点击手势来与全息影像交互。 现在, 我们将转到轻攻攻攻, 并探索新的概念:

* 检测何时跟踪用户的手并向用户提供反馈。
* 使用导航手势旋转全息影像。
* 请在用户即将退出查看时提供反馈。
* 使用操作事件可允许用户使用其手移动全息影像。

在本课程中, 我们将重新访问 Unity 项目**模型资源管理器, 该资源管理器**是在[MR Input 210](holograms-210.md)中生成的。 我们 astronaut 的朋友会回来, 帮助我们探索这些新的手势概念。

>[!IMPORTANT]
>以下各章中嵌入的视频使用较旧版本的 Unity 和混合现实工具包记录。 虽然分步说明准确且最新, 但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。 视频仍包含在 posterity 中, 因为涵盖的概念仍适用。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 输入 211:手势</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。
* 一些基本C#的编程能力。
* 应已完成[尊敬的基本知识 101](holograms-101.md)。
* 应已完成[MR 输入 210](holograms-210.md)。
* [为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)。 需要 Unity 2017.2 或更高版本。
* 取消将文件存档到桌面或其他易于访问的位置。

>[!NOTE]
>如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)找到。

### <a name="errata-and-notes"></a>勘误表和说明

* 需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用 (*取消选中*) "启用仅我的代码", 以便在代码中命中断点。

## <a name="chapter-0---unity-setup"></a>第0章-Unity 设置

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择 "**打开**"。
3. 导航到之前未存档的**手势**文件夹。
4. 查找并选择 "**启动**/**模型资源管理器**" 文件夹。
5. 单击 "**选择文件夹**" 按钮。
6. 在 "**项目**" 面板中, 展开 "**场景**" 文件夹。
7. 双击 " **ModelExplorer**场景" 将其加载到 Unity。

### <a name="building"></a>生成

1. 在 Unity 中, 选择 "**文件 > 生成设置**"。
2. 如果场景 **/ModelExplorer**未列在 "**生成**" 中, 请单击 "**添加打开的场景**" 添加场景。
3. 如果要专门针对 HoloLens 进行开发, 请将 "**目标设备**" 设置为 " **hololens**"。 否则, 请将其留在**任何设备**上。
4. 确保将 "**生成类型**" 设置为 " **D3D** ", 并将 " **SDK** " 设置为 "**最新安装**的" (应为 SDK 16299 或更高版本)
5. 单击“生成”。
6. 创建名为 "App" 的**新文件夹**。
7. 单击**应用**文件夹。
8. 按**选择文件夹**, Unity 将开始为 Visual Studio 生成项目。

当 Unity 完成后, 将显示文件资源管理器窗口。

1. 打开**应用程序**文件夹。
2. 打开**ModelExplorer Visual Studio 解决方案**。

如果部署到 HoloLens:

1. 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x86**"。
2. 单击 "本地计算机" 按钮旁的下拉箭头, 然后选择 "**远程计算机**"。
3. 输入**HoloLens 设备 IP 地址**, 并将身份验证模式设置为**通用 (未加密的协议)** 。 单击 "**选择**"。 如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。
4. 在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。 如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
5. 当应用程序已部署后, 使用**选择手势**关闭**Fitbox** 。

如果要部署到沉浸式耳机:

1. 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x64**"。
2. 确保将部署目标设置为 "**本地计算机**"。
3. 在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。
4. 当应用程序已部署后, 通过将触发器拖到运动控制器上来关闭**Fitbox** 。

>[!NOTE]
>你可能会注意到 Visual Studio 错误面板中出现一些红色错误。 可以放心地忽略它们。 切换到 "输出" 面板以查看实际的生成进度。 "输出" 面板中的错误将要求您进行修复 (通常是由于脚本中的错误而导致的)。

## <a name="chapter-1---hand-detected-feedback"></a>第1章-手动检测的反馈

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目标

* 订阅手动跟踪事件。
* 使用光标反馈向用户显示要跟踪的用户。

>[!NOTE]
>在 HoloLens 2 上, 只要指针可见 (而不仅仅是指手指处于向上状态时), 就会触发指针。

### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中, 展开 " **InputManager** " 对象。
* 查找并选择 " **GesturesInput** " 对象。

**InteractionInputSource.cs**脚本将执行以下步骤:

1. 订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。
2. 设置 HandDetected 状态。
3. 取消订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。

接下来, 我们将根据用户的操作, 将游标从[MR 输入 210](holograms-210.md)升级到显示反馈的游标。

1. 在 "**层次结构**" 面板中, 选择**光标**对象并将其删除。
2. 在 "**项目**" 面板中, 搜索 " **CursorWithFeedback** " 并将其拖到 "**层次结构**" 面板中。
3. 在 "**层次结构**" 面板中单击 " **InputManager** ", 然后将**CursorWithFeedback**对象从**层次结构**拖到**检查器**。
4. 在**层次结构**中单击 " **CursorWithFeedback** "。
5. 在 "**检查器**" 面板中, 展开**对象游标**脚本上的 "**游标状态数据**"。

**游标状态数据**的工作方式如下所示:

* 任何**观察**状态都意味着未检测到任何手形, 用户只需查看。
* 任何**交互**状态都表示检测到手型或控制器。
* 任何**悬停**状态都意味着用户正在查看全息影像。

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中, 使用**File > 生成设置**重新生成应用程序。
* 打开**应用程序**文件夹。
* 如果它尚未打开, 请打开**ModelExplorer Visual Studio 解决方案**。
  * (如果在安装过程中已经在 Visual Studio 中生成或部署了此项目, 则可以打开 VS 的实例, 并在出现提示时单击 "全部重新加载")。
* 在 Visual Studio 中, 单击 "**调试"-> "无调试开始**" 或按**Ctrl + F5**。
* 在应用程序部署到 HoloLens 后, 请使用 "轻攻攻" 手势关闭 fitbox。
* 将您的手转到视图, 并将您的索引手指指向天空, 开始进行手动跟踪。
* 向左、向右、向下和向下移动。
* 监视在检测到您的手形后光标发生变化的方式, 并从视图中丢失。
* 如果你使用的是沉浸式耳机, 则必须连接并断开控制器的连接。 此反馈在沉浸式设备上变得不太感兴趣, 因为连接的控制器始终为 "可用"。

## <a name="chapter-2---navigation"></a>第2章-导航

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目标

* 使用导航手势事件来轮换 astronaut。

### <a name="instructions"></a>说明

若要在应用中使用导航笔势, 我们将在导航手势发生时编辑**GestureAction.cs**来旋转对象。 此外, 我们还会将反馈添加到要在导航可用时显示的光标。

1. 在 "**层次结构**" 面板中, 展开 " **CursorWithFeedback**"。
2. 在**全息影像**文件夹中, 找到 " **ScrollFeedback**资产"。
3. 将**ScrollFeedback** prefab 拖放到**层次结构**中的**CursorWithFeedback** GameObject。
4. 单击**CursorWithFeedback**。
5. 在**检查器**面板中, 单击 "**添加组件**" 按钮。
6. 在菜单中, 在 "搜索" 框中键入**CursorFeedback**。 选择搜索结果。
7. 将**ScrollFeedback**对象从**层次结构**中拖放到**检查器**的**光标反馈**组件中的 "**滚动检测到的游戏对象**" 属性上。
8. 在 "**层次结构**" 面板中, 选择 " **AstroMan** " 对象。
9. 在**检查器**面板中, 单击 "**添加组件**" 按钮。
10. 在菜单中, 键入 "搜索框**手势" 操作**。 选择搜索结果。

接下来, 在 Visual Studio 中打开**GestureAction.cs** 。 在编码练习 2. c 中, 编辑脚本以执行以下操作:

1. 只要执行导航手势, 就会**旋转 AstroMan**对象。
2. 计算**rotationFactor**以控制应用于对象的旋转量。
3. 当用户向左或向右移动对象时, 绕 y 轴**旋转对象**。

在脚本中完成编码演练 2. c, 或将代码替换为以下已完成的解决方案:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

你会注意到, 其他导航事件已经填充了某些信息。 我们将 GameObject 推送到工具包的 InputSystem's 模式堆栈上, 这样用户就无需在旋转开始后在 Astronaut 上保持焦点。 同样, 在完成该笔势后, 将从堆栈中弹出 GameObject。

### <a name="build-and-deploy"></a>生成和部署

1. 重新生成 Unity 中的应用程序, 然后从 Visual Studio 生成并部署, 以便在 HoloLens 中运行。
2. 注视 astronaut, 光标两侧应会出现两个箭头。 此新视觉对象指示 astronaut 可以旋转。
3. 将手置于 "就绪" 位置 (食指指向天空), 以便 HoloLens 开始跟踪。
4. 若要旋转 astronaut, 请将食指降低到挤压位置, 然后向左或向右移动以触发 NavigationX 手势。

## <a name="chapter-3---hand-guidance"></a>第三章-手写指南

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目标

* 使用 "**手动指南分数**" 有助于预测何时会丢失手动跟踪。
* 提供**有关光标的反馈**, 以便在用户尝试观看相机边缘时显示。

### <a name="instructions"></a>说明

1. 在 "**层次结构**" 面板中, 选择 " **CursorWithFeedback** " 对象。
2. 在**检查器**面板中, 单击 "**添加组件**" 按钮。
3. 在菜单中, 键入搜索框的**指导**。 选择搜索结果。
4. 在 "**项目**"面板中, 找到 " **HandGuidanceFeedback**资产"。
5. 将**HandGuidanceFeedback**资产拖放到 "**检查器**" 面板中的 "**手写指南" 指示符**属性上。

### <a name="build-and-deploy"></a>生成和部署

* 重新生成 Unity 中的应用程序, 然后从 Visual Studio 生成并部署, 以在 HoloLens 上体验应用。
* 将你的手转到视图中, 并抬起你的索引手指进行跟踪。
* 开始旋转 astronaut, 使其具有导航手势 (将您的索引手指同时一起)。
* 向左、向右、向上、向下移动。
* 当手接近该笔势帧的边缘时, 光标旁边应会出现一个箭头, 警告您将丢失手动跟踪。 箭头指示移动哪一方向, 以防丢失跟踪。

## <a name="chapter-4---manipulation"></a>第4章-操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目标

* 使用操作事件将 astronaut 移动到手中。
* 提供有关游标的反馈, 以让用户知道何时可以使用操作。

### <a name="instructions"></a>说明

GestureManager.cs 和 AstronautManager.cs 将允许我们执行以下操作:

1. 使用 speech 关键字 "**Move Astronaut**" 启用**操作**手势, 并使用 "**旋转 Astronaut**" 来禁用它们。
2. 切换到响应**操作笔势识别器**。

让我们开始吧。

1. 在 "**层次结构**" 面板中, 创建一个新的空 GameObject。 将其命名为 "**AstronautManager**"。
2. 在**检查器**面板中, 单击 "**添加组件**" 按钮。
3. 在菜单中, 在 "搜索" 框中键入 " **Astronaut Manager**"。 选择搜索结果。
4. 在**检查器**面板中, 单击 "**添加组件**" 按钮。
5. 在菜单中, 在 "搜索" 框中键入 "**语音输入源**"。 选择搜索结果。

现在, 我们将添加控制 astronaut 交互状态所需的语音命令。

1. 展开**检查器**中的 "**关键字**" 部分。
2. 单击 **+** 右侧添加一个新的关键字。
3. 将关键字键入为**Move Astronaut**。 如果需要, 可以随意添加密钥快捷方式。
4. 单击 **+** 右侧添加一个新的关键字。
5. 将关键字键入为**轮换 Astronaut**。 如果需要, 可以随意添加密钥快捷方式。
6. 可在**GestureAction.cs**中的**ISpeechHandler. OnSpeechKeywordRecognized**处理程序中找到相应的处理程序代码。

![如何设置第4章的语音输入源](images/holograms211-speech.png)

接下来, 我们将在游标上设置操作反馈。

1. 在 "**项目**"面板中, 找到 " **PathingFeedback**资产"。
2. 将**PathingFeedback** prefab 拖放到**层次结构**中的**CursorWithFeedback**对象上。
3. 在 "**层次结构**" 面板中, 单击 " **CursorWithFeedback**"。
4. 将**PathingFeedback**对象从**层次结构**中拖放到**检查器**的 "**游标反馈**" 组件中的 "**检测到路径" 游戏对象**属性上。

现在, 我们需要将代码添加到**GestureAction.cs** , 以启用以下内容:

1. 将代码添加到**IManipulationHandler. OnManipulationUpdated**函数, 该函数将在检测到**操作**笔势时移动 astronaut。
2. 计算**移动向量**, 以根据手头位置确定应将 astronaut 移动到的位置。
3. **将 Astronaut 移动**到新位置。

完成编码练习 4. 在**GestureAction.cs**中, 或使用下面的已完成解决方案:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中重新生成, 然后在 Visual Studio 中生成并部署, 以在 HoloLens 中运行该应用。
* 将你的手移到 HoloLens 前面, 并抬起你的食指, 以便能够进行跟踪。
* 将光标放在 astronaut 上。
* 说 "Move Astronaut" 将 Astronaut 与操作手势一起移动。
* 光标两侧应出现四个箭头, 指示程序将立即响应操作事件。
* 将索引向下减小到拇指, 并使其 pinched 在一起。
* 在四处移动手时, astronaut 也会移动 (这是操作)。
* 抬起索引手指, 停止操作 astronaut。
* 注意：如果在移动手前未说 "移动 Astronaut", 则将改用导航手势。
* 说 "旋转 Astronaut" 返回到 rotatable 状态。

## <a name="chapter-5---model-expansion"></a>第5章-模型扩展

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目标

* 将 Astronaut 模型扩展为用户可与之交互的多个较小的部分。
* 使用导航和操作笔势分别移动各个部分。

### <a name="instructions"></a>说明

在本部分中, 我们将完成下列任务:

1. 添加新的关键字 "**展开模型**", 展开 astronaut 模型。
2. 添加新的关键字 "**重置模型**", 以将模型返回到其原始形式。

为此, 我们将向上一章的语音输入源添加另外两个关键字。 我们还将演示另一种处理识别事件的方法。

1. 在**检查器**中单击 " **AstronautManager** ", 然后展开**检查器**中的 "**关键字**" 部分。
2. 单击 **+** 右侧添加一个新的关键字。
3. 将关键字键入为**展开 "模型**"。 如果需要, 可以随意添加密钥快捷方式。
4. 单击 **+** 右侧添加一个新的关键字。
5. 将关键字键入为 "**重置模型**"。 如果需要, 可以随意添加密钥快捷方式。
6. 在**检查器**面板中, 单击 "**添加组件**" 按钮。
7. 在菜单中, 在 "搜索" 框中键入**语音输入处理程序**。 选择搜索结果。
8. 勾选**是全局侦听器**, 因为我们希望这些命令可以正常运行, 而不考虑我们的 GameObject。
9. 单击 **+** 按钮，然后选择**展开模型**从关键字下拉列表。
10. 单击 **+** 下的响应，并将**AstronautManager**从**层次结构**到**None （对象）** 字段。
11. 现在, 单击 "**无函数**" 下拉列表, 选择 " **AstronautManager**", 然后选择 " **ExpandModelCommand**"。
12. 单击语音输入处理程序的 **+** 按钮，然后选择**重置模型**从关键字下拉列表。
13. 单击 **+** 下的响应，并将**AstronautManager**从**层次结构**到**None （对象）** 字段。
14. 现在, 单击 "**无函数**" 下拉列表, 选择 " **AstronautManager**", 然后选择 " **ResetModelCommand**"。

![如何设置第5章的语音输入源和处理程序](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>生成和部署

* 试试看吧！ 生成应用并将其部署到 HoloLens。
* 说**展开 "模型**" 以查看扩展的 astronaut 模型。
* 使用**导航**旋转 astronaut 花色的各个部分。
* 假设**移动 Astronaut** , 然后使用**操作**来移动 Astronaut 花色的各个部分。
* 说**旋转 Astronaut**再次旋转棋子。
* 假设**Reset Model**将 astronaut 返回到其原始形式。

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**了 MR 输入 211:手势**。

* 你知道如何检测和响应手动跟踪、导航和操作事件。
* 了解导航和操作笔势之间的差异。
* 你知道如何更改光标以提供有关何时检测到手、即将丢失以及何时对象支持不同交互 (导航与操作) 的视觉反馈。
