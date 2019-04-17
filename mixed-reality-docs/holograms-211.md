---
title: MR 输入 211 的手势
description: 按照本演练使用 Unity、 Visual Studio 和 HoloLens 学习手势概念的详细信息进行编码操作。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程中，手势
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592683"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

# <a name="mr-input-211-gesture"></a>MR 输入 211:手势

[手势](gestures.md)转变为操作的用户的意图。 使用手势，用户可以与全息交互。 在本课程中，我们将了解如何跟踪用户的手、 响应用户输入，并向用户提供反馈的基于状态和位置。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

在中[MR 基础知识 101](holograms-101.md)，我们用简单敲击手势来与我们全息交互。 现在，我们将以无线方式点击动作可以超越并浏览到新的概念：

* 正在跟踪用户的手时进行检测并向用户提供反馈。
* 使用导航笔势轮换我们全息。
* 当用户的手即将超出视图时，请提供反馈。
* 将使用操作事件，以便用户可以移动则用手全息。

在本课程中，我们将再度讨论 Unity 项目**模型资源管理器**，它我们构建[MR 输入 210](holograms-210.md)。 我们顶级的朋友是返回到我们的探索这些新手势概念在帮助我们。

>[!IMPORTANT]
>使用 Unity 和混合现实工具包的较旧版本记录中的以下章节每个嵌入的视频。 准确且最新的分步说明时，可能会看到脚本和已过期的相应视频中的视觉对象。 保持为长期的视频和因为涵盖了概念仍然适用。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 输入 211:手势</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。
* 一些基本C#编程功能。
* 您应当已完成[MR 基础知识 101](holograms-101.md)。
* 您应当已完成[MR 输入 210](holograms-210.md)。
* HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
* 取消存档到您的桌面或其他轻松地访问位置的文件。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)。

### <a name="errata-and-notes"></a>勘误表和说明

* "启用仅我的代码"必须禁用 (*未选中*) 在 Visual Studio 工具-> 选项-> 调试以便你的代码中命中断点。

## <a name="chapter-0---unity-setup"></a>章 0-Unity 安装程序

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择**打开**。
3. 导航到**手势**文件夹你之前未存档。
4. 找到并选择**起始**/**模型资源管理器**文件夹。
5. 单击**选择文件夹**按钮。
6. 在中**项目**面板中，展开**场景**文件夹。
7. 双击**ModelExplorer**场景中，从而在 Unity 中加载它。

### <a name="building"></a>生成

1. 在 Unity 中，选择**文件 > 生成设置**。
2. 如果**场景/ModelExplorer**中未列出**生成中的场景**，单击**添加打开场景**添加场景。
3. 如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。 否则，将其保持打开**任何设备**。
4. 请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。
5. 单击“生成” 。
6. 创建**新文件夹**名为"应用"。
7. 单击一下**应用**文件夹。
8. 按**选择文件夹**和 Unity 将启动 Visual Studio 的生成项目。

Unity 完成操作后，将出现一个文件资源管理器窗口。

1. 打开**应用**文件夹。
2. 打开**ModelExplorer Visual Studio 解决方案**。

如果部署到 HoloLens:

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。
2. 单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。
3. 输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。 单击**选择**。 如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。
4. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。 如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
5. 当部署应用时，消除**Fitbox**与**选择手势**。

如果部署到沉浸式头戴式：

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。
2. 请确保部署目标设置为**本地计算机**。
3. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。
4. 当部署应用时，消除**Fitbox**拉开运动控制器上的触发器。

>[!NOTE]
>您可能注意到 Visual Studio 错误面板中的某些红色错误。 它可以安全地忽略它们。 切换到输出面板来查看实际生成进度。 输出面板中的错误将要求您的修补程序 （即最常在脚本中的错误，就会出现）。

## <a name="chapter-1---hand-detected-feedback"></a>第 1 章-手动检测到的反馈

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目标

* 移交订阅跟踪事件。
* 使用游标反馈以向用户显示手的形状在跟踪时。

### <a name="instructions"></a>说明

* 在中**层次结构**面板中，展开**InputManager**对象。
* 查找并选择**GesturesInput**对象。

**InteractionInputSource.cs**脚本执行以下步骤：

1. 订阅的 InteractionSourceDetected 和 InteractionSourceLost 事件。
2. 设置 HandDetected 状态。
3. 从 InteractionSourceDetected 和 InteractionSourceLost 事件取消订阅。

接下来，我们将升级从我们的光标[MR 输入 210](holograms-210.md)到一个显示了具体取决于用户的操作的反馈。

1. 在中**层次结构**面板中，选择**光标**对象，并将其删除。
2. 在中**项目**面板中，搜索**CursorWithFeedback**将其拖到**层次结构**面板。
3. 单击**InputManager**中**层次结构**面板，然后拖动**CursorWithFeedback**对象**层次结构**到InputManager 的**SimpleSinglePointerSelector**的**光标**字段中，在底部**Inspector**。
4. 单击**CursorWithFeedback**中**层次结构**。
5. 在中**Inspector**面板中，展开**游标状态数据**上**对象游标**脚本。

**游标状态数据**工作方式类似于此：

* 任何**观察**状态意味着检测到任何现有用户只需仔细。
* 任何**Interact**状态指的手形或控制器检测到。
* 任何**将鼠标悬停在**状态意味着用户查看一张全息图。

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中，使用**文件 > 生成设置**重新生成应用程序。
* 打开**应用**文件夹。
* 如果尚未打开，打开**ModelExplorer Visual Studio 解决方案**。
  * （如果你已生成/部署此项目在 Visual Studio 中的在设置过程，然后您可以打开与该实例并单击全部重新加载出现提示时）。
* 在 Visual Studio 中，单击**调试-> 启动不调试**或按**Ctrl + F5**。
* 在应用程序部署到 HoloLens 后，关闭使用-敲击手势 fitbox。
* 将您的手移到视图和食指指向天空启动手动跟踪。
* 向您的手左、 向右、 向上和向下。
* 观看光标时检测到您的手并将其从视图然后丢失的更改。
* 如果您在沉浸式头戴式耳机，您必须连接和断开你的控制器。 此反馈变得令人着迷的设备上还没那么有趣，如连接的控制器始终将"可用"。

## <a name="chapter-2---navigation"></a>第 2 章-导航

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目标

* 使用导航手势事件轮换顶级。

### <a name="instructions"></a>说明

若要在我们的应用程序中使用导航笔势，我们将编辑**GestureAction.cs**旋转对象时导航笔势时发生。 此外，我们将添加到要获得导航时显示的光标的反馈。

1. 在中**层次结构**面板中，展开**CursorWithFeedback**。
2. 在中**全息**文件夹中，找到**ScrollFeedback**资产。
3. 拖放到**ScrollFeedback**拖动到 prefab **CursorWithFeedback**中的 GameObject**层次结构**。
4. 单击**CursorWithFeedback**。
5. 在中**Inspector**面板中，单击**添加组件**按钮。
6. 在菜单中，在搜索框中键入**CursorFeedback**。 选择搜索结果。
7. 拖放到**ScrollFeedback**对象从**层次结构**拖到**滚动检测到游戏对象**中的属性**光标反馈**组件**Inspector**。
8. 在中**层次结构**面板中，选择**AstroMan**对象。
9. 在中**Inspector**面板中，单击**添加组件**按钮。
10. 在菜单中，在搜索框中键入**手势动作**。 选择搜索结果。

接下来，打开**GestureAction.cs** Visual Studio 中。 在编码练习 2.c，编辑脚本以执行以下操作：

1. **旋转 AstroMan**对象执行导航笔势。
2. 计算**rotationFactor**来控制应用于对象的旋转的量。
3. **旋转对象**绕 y 轴时用户将其手动移动左侧或右侧。

完成编码练习中的脚本或将已完成的解决方案以下代码替换为 2.c:

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

您会发现其他导航事件已填充一些信息。 我们将推送到该工具包的 GameObject InputSystem 的模式堆栈，因此用户无需维护专注于顶级，一旦已开始旋转。 相应地，我们弹出堆栈的 GameObject 手势完成。

### <a name="build-and-deploy"></a>生成和部署

1. 重新生成 Unity 中的应用程序然后生成并部署从 Visual Studio 在 HoloLens 中运行它。
2. 注视顶级，两个箭头应显示光标的任何一侧。 这个新的视觉指示可以旋转顶级。
3. 将您的手放在准备好的位置 （食指指向向天空） 以便 HoloLens 将开始跟踪您的手。
4. 若要旋转顶级，降低到 pinch 一个位置，索引手指，然后您的手左移或右移触发 NavigationX 手势。

## <a name="chapter-3---hand-guidance"></a>第 3 章-手指南

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目标

* 使用**分发指南分数**帮助预测时手动跟踪将会丢失。
* 提供**反馈对游标**以显示当用户的手接近视图的照相机的边缘。

### <a name="instructions"></a>说明

1. 在中**层次结构**面板中，选择**CursorWithFeedback**对象。
2. 在中**Inspector**面板中，单击**添加组件**按钮。
3. 在菜单中，在搜索框中键入**手指南**。 选择搜索结果。
4. 在中**项目**面板**全息**文件夹中，找到**HandGuidanceFeedback**资产。
5. 拖放到**HandGuidanceFeedback**拖动到资产**手指南指示器**中的属性**Inspector**面板。

### <a name="build-and-deploy"></a>生成和部署

* 重新生成 Unity 中的应用程序然后生成并从 Visual Studio 体验 HoloLens 上的应用程序部署。
* 将您的手放入视图，并引发手指索引获取跟踪。
* 开始旋转与导航笔势顶级 （捏合索引手指和拇指一起）。
* 最左侧、 右侧、，向上和向下移动您的手。
* 当您的手接近手势帧的边缘应旁边显示一个箭头光标以向您发出警告跟踪该手动将会丢失。 箭头指示哪个方向移动以防止丢失跟踪您的手。

## <a name="chapter-4---manipulation"></a>第 4 章-操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目标

* 使用操作事件移动用手顶级。
* 若要让用户知道可以使用操作时对游标提供反馈。

### <a name="instructions"></a>说明

GestureManager.cs 和 AstronautManager.cs 将使我们可以执行以下操作：

1. 使用语音关键字"**移动顶级**"以启用**操作**手势和"**旋转顶级**"来禁用它们。
2. 切换到响应**操作笔势识别器**。

让我们开始吧。

1. 在中**层次结构**面板中，创建新的空 GameObject。 其命名为"**AstronautManager**"。
2. 在中**Inspector**面板中，单击**添加组件**按钮。
3. 在菜单中，在搜索框中键入**顶级 Manager**。 选择搜索结果。
4. 在中**Inspector**面板中，单击**添加组件**按钮。
5. 在菜单中，在搜索框中键入**语音输入源**。 选择搜索结果。

我们现在将添加的语音命令，来控制顶级的交互状态。

1. 展开**关键字**主题中**Inspector**。
2. 单击**+** 右侧添加一个新的关键字。
3. 类型为关键字**移动顶级**。 随时根据需要添加一个键的快捷方式。
4. 单击**+** 右侧添加一个新的关键字。
5. 类型为关键字**旋转顶级**。 随时根据需要添加一个键的快捷方式。
6. 可在相应的处理程序代码**GestureAction.cs**，在**ISpeechHandler.OnSpeechKeywordRecognized**处理程序。

![如何设置第 4 章语音输入源](images/holograms211-speech.png)

接下来，我们将设置对游标的操作反馈。

1. 在中**项目**面板**全息**文件夹中，找到**PathingFeedback**资产。
2. 拖放到**PathingFeedback**拖动到 prefab **CursorWithFeedback**对象中**层次结构**。
3. 在中**层次结构**面板中，单击**CursorWithFeedback**。
4. 拖放到**PathingFeedback**对象从**层次结构**拖到**路径检测到游戏对象**中的属性**光标反馈**组件**Inspector**。

现在，我们需要将代码添加到**GestureAction.cs**以实现以下：

1. 将代码添加到**IManipulationHandler.OnManipulationUpdated**函数，它会将移动的顶级时**操作**检测到笔势。
2. 计算**移动矢量**来确定应将顶级转移到基于现有位置。
3. **移动**顶级到新位置。

完成编码练习中的 4.a **GestureAction.cs**，或使用我们已完成的解决方案如下：

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

* 在 Unity 中重新生成然后生成并从 Visual Studio HoloLens 中运行应用程序部署。
* 移动您的手 HoloLens 的前面，并引发索引手指，以便可以跟踪。
* 通过顶级焦点光标。
* 说移动顶级移动与操作笔势顶级。
* 四个箭头光标以指示该程序将立即响应操作事件周围应显示。
* 降低食指到您的拇指，并将其挤压在一起。
* 您的手周围移动时，也会移动顶级 （这是操作）。
* 引发食指停止操作顶级。
* 注意：如果您的手再不说出移动顶级，则将改为使用导航笔势。
* 说旋转顶级以返回到可旋转的状态。

## <a name="chapter-5---model-expansion"></a>第 5 章-模型扩展

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目标

* 展开顶级模型分为多个，较小部分用户可以与交互。
* 将移动每个部分使用单独的导航和操作的笔势。

### <a name="instructions"></a>说明

在本部分中，我们将完成以下任务：

1. 添加一个新的关键字"**展开模型**"以展开顶级模型。
2. 添加一个新的关键字"**重置模型**"可为其原始形式返回的模型。

我们将通过将两个多个关键字添加到语音输入源，从上一章来执行此操作。 我们还将演示另一种方法来处理识别事件。

1. 单击重新**AstronautManager**中**Inspector**展开**关键字**主题中**检查器**。
2. 单击**+** 右侧添加一个新的关键字。
3. 类型为关键字**展开模型**。 随时根据需要添加一个键的快捷方式。
4. 单击**+** 右侧添加一个新的关键字。
5. 类型为关键字**重置模型**。 随时根据需要添加一个键的快捷方式。
6. 在中**Inspector**面板中，单击**添加组件**按钮。
7. 在菜单中，在搜索框中键入**语音输入处理程序**。 选择搜索结果。
8. 检查**是全局侦听器**，因为我们希望这些命令来处理而不考虑 GameObject 中我们主要。
9. 单击**+** 按钮，然后选择**展开模型**从关键字下拉列表。
10. 单击**+** 下的响应，并将**AstronautManager**从**层次结构**到**None （对象）** 字段。
11. 现在，单击**否函数**下拉列表中，选择**AstronautManager**，然后**ExpandModelCommand**。
12. 单击语音输入处理程序的**+** 按钮，然后选择**重置模型**从关键字下拉列表。
13. 单击**+** 下的响应，并将**AstronautManager**从**层次结构**到**None （对象）** 字段。
14. 现在，单击**否函数**下拉列表中，选择**AstronautManager**，然后**ResetModelCommand**。

![如何设置语音输入源和处理程序第 5 章](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>生成和部署

* 试试看吧！ 生成并将应用部署到 HoloLens。
* 说**展开模型**，查看扩展的顶级模型。
* 使用**导航**旋转的顶级花色的各个部分。
* 说**移动顶级**，然后使用**操作**移动的顶级花色的各个部分。
* 说**旋转顶级**再次旋转部分。
* 说**重置模型**以返回到其原始形式的顶级。

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**MR 输入 211:手势**。

* 您知道如何进行检测和响应移交跟踪、 导航和操作事件。
* 了解导航和操作手势之间的差异。
* 您知道如何进行更改会丢失，手的形状时检测到手的形状是和对象时支持不同的交互 (导航 vs 操作) 提供可视反馈的光标。
