---
title: MR 输入213
description: 按照此编码教程使用 Unity、Visual Studio 和沉浸式耳机来了解动作控制器的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，沉浸式，运动总监，学院，教程
ms.openlocfilehash: 273d1bf384d588ab24bfe29e30f299b7a41fe541
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926822"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。  因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。  这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 输入213：运动控制器

混合现实世界中的运动控制器增加了另一层的交互性。 借助[运动控制器](motion-controllers.md)，我们可以以更自然的方式与对象直接交互，类似于真实生活中的物理交互，增加浸入式和感到满意的应用体验。

在 MR 输入213中，我们将通过创建一个简单的空间绘制体验来浏览运动控制器的输入事件。 对于此应用程序，用户可以在具有各种类型的画笔和颜色的三维空间中进行绘制。

## <a name="topics-covered-in-this-tutorial"></a>本教程中介绍的主题

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**控制器可视化**|**控制器输入事件**|**自定义控制器和 UI**|
|了解如何在 Unity 的游戏模式和运行时中呈现运动控制器模型。|了解不同类型的按钮事件及其应用程序。|了解如何在控制器顶部覆盖 UI 元素或对其进行完全自定义。|

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 输入213：运动控制器</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>必备条件

请参阅[本页上的](install-the-tools.md)沉浸式耳机安装清单。

* 本教程需要[Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>项目文件

* 下载项目所需[的文件](https://github.com/Microsoft/MixedReality213/archive/master.zip)，并将文件解压缩到桌面。

>[!NOTE]
>如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/MixedReality213)找到。

## <a name="unity-setup"></a>Unity 设置

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目标

* 优化 Unity 以实现 Windows Mixed Reality 开发
* 设置混合现实照相机
* 设置环境

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择 "**打开**"。
* 导航到桌面并找到之前 unarchived 的**MixedReality213**文件夹。
* 单击“选择文件夹”。
* Unity 完成加载项目文件后，你将能够看到 Unity 编辑器。
* 在 Unity 中，选择 "**文件 > 生成设置**"。

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* 选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**" 按钮。
* 将目标设备设置为**任何设备**
* 将生成类型设置为**D3D**
* 将 SDK 设置为**安装的最新版本**
* 检查**Unity C#项目**
    * 这样，便可以修改 Visual Studio 项目中的脚本文件，而无需重新生成 Unity 项目。
* 单击 "**播放机设置**"。
* 在 "**检查器**" 面板中，向下滚动到底部
* 在 XR 设置中，检查**支持的虚拟现实**
* 在虚拟现实 Sdk 下，选择 " **Windows Mixed Reality** "

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* 关闭 "**生成设置**" 窗口。

### <a name="project-structure"></a>项目结构

本教程使用 **[混合现实工具包-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 。 可以在[此页](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到发布。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**已完成用于引用的场景**

* 你会在**场景**文件夹中找到两个已完成的 Unity 场景。
    * **MixedReality213**：通过单画笔完成场景
    * **MixedReality213Advanced**：已完成用于具有多个画笔的高级设计的场景

**教程的新场景设置**

* 在 Unity 中，单击 "**文件" > 新建场景**
* 删除**摄像机**和**方向灯**
* 在 "**项目" 面板**中，搜索并将以下 prototyping 拖到 "**层次结构**" 面板中：
    * 资产/HoloToolkit/Input/Prototyping/**MixedRealityCamera**
    * 资产/AppPrefabs/**环境**

    ![照相机和环境](images/mr213-cameraenvironment-300px.jpg)

* 混合现实工具包中有两个照相机 prototyping：
    * **MixedRealityCamera. prefab**：仅照相机
    * **MixedRealityCameraParent. prefab**：摄像 + Teleportation + 边界
    * 在本教程中，我们将使用不带 teleportation 功能的**MixedRealityCamera** 。 为此，我们添加了简单的**环境**prefab，其中包含一个基本楼层，使用户感觉不到接地。
    * 若要了解有关 teleportation 与**MixedRealityCameraParent**的详细信息，请参阅[高级设计-teleportation 和 locomotion](#advanced-design---teleportation-and-locomotion)

**Skybox 安装程序**

* 单击 "**窗口" > 照明 > 设置**
* 单击**Skybox 材料字段**右侧的圆圈
* 键入 "灰色" 并选择 " **SkyboxGray** " （资产/AppPrefabs/支持/材料/SkyboxGray）

    ![设置 skybox](images/mr123-skyboxsetting-400px.jpg)

* 检查**Skybox**选项以查看已分配的灰色渐变 Skybox

    ![切换 skybox 选项](images/mr213-skyboxcheck-400px.jpg)

* 带有 MixedRealityCamera、环境和灰色 skybox 的场景将如下所示。

    ![MixedReality213 环境](images/mr213-environment-600px.jpg)

* 单击 "**文件" > 将场景另存为**
* 用任意名称**将场景保存**在场景文件夹下

## <a name="chapter-1---controller-visualization"></a>第1章-控制器可视化

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目标

* 了解如何在 Unity 的游戏模式下和在运行时呈现运动控制器模型。

Windows Mixed Reality 提供适用于控制器可视化的动画控制器模型。 可在应用中使用以下几种方法来实现控制器可视化：

* 默认-使用默认控制器但不修改
* 混合-使用默认控制器，但自定义其部分元素或覆盖 UI 组件
* 替换-将你自己的自定义3D 模型用于控制器

在本章中，我们将了解这些控制器自定义的示例。

### <a name="instructions"></a>说明

* 在 "**项目**" 面板的 "搜索" 框中，键入**MotionControllers** 。 还可以在 "资产/HoloToolkit/输入/Prototyping/" 下找到它。
* 将**MotionControllers** prefab 拖到 "**层次结构**" 面板中。
* 单击 "**层次结构**" 面板中的**MotionControllers** prefab。

**MotionControllers prefab**

**MotionControllers** prefab 有一个**MotionControllerVisualizer**脚本，该脚本提供备用控制器型号的槽。 如果您为自己的自定义3D 模型（如手或剑）指定了一个，并选中 "始终使用备用的左/右模型"，则会看到它们，而不是默认模型。 我们将在第4章中使用此槽，用画笔替换控制器模型。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**说明**

* 在 "**检查器**" 面板中，双击 " **MotionControllerVisualizer** Script" 以查看 Visual Studio 中的代码

**MotionControllerVisualizer 脚本**

**MotionControllerVisualizer**和**MotionControllerInfo**类提供访问 & 修改默认控制器模型的方法。 **MotionControllerVisualizer**订阅 Unity 的**InteractionSourceDetected**事件，并在发现控制器模型时自动将其实例化。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

控制器模型是根据[glTF 规范](https://github.com/KhronosGroup/glTF)传递的。 创建此格式是为了提供通用格式，同时改进了在传输和解包3D 资产后的过程。 在这种情况下，我们需要在运行时检索并加载控制器模型，因为我们希望尽可能使用户体验尽可能顺畅，并不保证用户可能正在使用的运动控制器版本。 本课程通过混合现实工具包使用 Khronos 组的[UnityGLTF 项目](https://github.com/KhronosGroup/UnityGLTF)版本。

提供控制器后，脚本可以使用**MotionControllerInfo**查找特定控制器元素的转换，以便它们可以正确定位。

在后面的章节中，我们将了解如何使用这些脚本将 UI 元素附加到控制器。

*在某些脚本中，你将找到带有 #if 的代码块 **！UNITY_EDITOR**或**UNITY_WSA**。这些代码块仅在部署到 Windows 时在 UWP 运行时上运行。这是因为 Unity 编辑器和 UWP 应用运行时所使用的 Api 集是不同的。*

* **保存**场景并单击 "**播放**" 按钮。

你将能够在耳机中看到带有运动控制器的场景。 可以查看按钮单击、操纵杆运动和触摸板触摸突出显示的详细动画。

![MR213_Controller 可视化默认值](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第2章-将 UI 元素附加到控制器

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目标

* 了解运动控制器的元素
* 了解如何将对象附加到控制器的特定部分

在本章中，你将学习如何将用户界面元素添加到用户可随时轻松访问和操作的控制器。 你还将了解如何使用触摸板输入添加简单的颜色选取器 UI。

### <a name="instructions"></a>说明

* 在 "**项目**" 面板中，搜索 " **MotionControllerInfo** script"。
* 在搜索结果中，双击 " **MotionControllerInfo** script" 以查看 Visual Studio 中的代码。

**MotionControllerInfo 脚本**

第一步是选择要将 UI 附加到的控制器的元素。 这些元素在**MotionControllerInfo.cs**的**ControllerElementEnum**中定义。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **主页**
* **菜单**
* **掌握**
* **控制**
* **单击**
* **触摸板**
* **指针姿势**–此元素表示控制器向后方向的笔尖。

**说明**

* 在 "**项目**" 面板中，搜索 " **AttachToController** script"。
* 在搜索结果中，双击 " **AttachToController** script" 以查看 Visual Studio 中的代码。

**AttachToController 脚本**

**AttachToController**脚本提供了一种简单的方法，可将任何对象附加到指定的控制器左右手使用习惯和元素。

在**AttachElementToController （）** 中，

* 使用 MotionControllerInfo 检查左右手使用习惯 **。左右手使用习惯**
* 使用**MotionControllerInfo. TryGetElement （）** 获取控制器的特定元素
* 从控制器模型检索该元素的转换后，将其父对象置于其下，并将对象的本地位置 & 旋转到零。

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

使用**AttachToController**脚本的最简单方法是从其继承，就像我们在 ColorPickerWheel 的情况下所做的那样 **。** 只需重写**OnAttachToController**和**OnDetachFromController**函数，以便在检测到控制器/断开连接时执行设置/细分。

**说明**

* 在 "**项目**" 面板的 "搜索" 框中键入**ColorPickerWheel**。 还可以在 "资产/AppPrefabs/" 下找到它。
* 将**ColorPickerWheel** prefab 拖到 "**层次结构**" 面板中。
* 单击 "**层次结构**" 面板中的**ColorPickerWheel** prefab。
* 在 "**检查器**" 面板中，双击 " **ColorPickerWheel** Script" 以查看 Visual Studio 中的代码。

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 脚本**

由于**ColorPickerWheel**继承**了 AttachToController**，它会在 "**检查器**" 面板中显示**左右手使用习惯**和**元素**。 我们会将 UI 附加到左侧控制器上的触摸板元素。

![ColorPickerWheel 脚本](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel**重写**OnAttachToController**和**OnDetachFromController**以订阅输入事件，此事件将在下一章中用于使用触摸板输入的颜色选择。

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **保存**场景并单击 "**播放**" 按钮。

**将对象附加到控制器的替代方法**

建议你的脚本继承自**AttachToController** ，并重写**OnAttachToController**。 但这并不总是可行。 替代方法是将其用作独立组件。 如果要将现有的 prefab 附加到控制器而不重构脚本，这会很有用。 只需将 IsAttached 设置为 true，然后再执行任何设置。 执行此操作的最简单方法是使用协同程序作为 "Start"。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第3章-使用触摸板输入

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目标

* 了解如何获取触摸板输入数据事件
* 了解如何将触摸板轴位置信息用于应用体验

### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中，单击 " **ColorPickerWheel** "
* 在 "**检查器**" 面板中的 " **Animator**" 下，双击 " **ColorPickerWheelController** "
* 你将能够看到 " **Animator** " 选项卡已打开

**显示/隐藏具有 Unity 动画控制器的 UI**

若要显示和隐藏带有动画的**ColorPickerWheel** UI，我们使用[的是 Unity 的动画系统](https://docs.unity3d.com/Manual/AnimationOverview.html)。 如果将**ColorPickerWheel**的**Visible**属性设置为 true 或 False，则将**显示**和**隐藏**动画触发器。 在**ColorPickerWheelController**动画控制器中定义了**显示**和**隐藏**参数。

![Unity 动画控制器](images/mr123-animationcontroller-550px.jpg)

**说明**

* 在 "**层次结构**" 面板中，选择**ColorPickerWheel** prefab
* 在 "**检查器**" 面板中，双击 " **ColorPickerWheel** Script" 以查看 Visual Studio 中的代码

**ColorPickerWheel 脚本**

**ColorPickerWheel**订阅 Unity 的**InteractionSourceUpdated**事件来侦听触摸板事件。

在**InteractionSourceUpdated （）** 中，脚本首先检查以确保：

* 实际上是一个触摸板事件（.obj. 状态。**touchpadTouched**）
* 源自左侧控制器（.obj. 状态 **。左右手使用习惯**）

如果两者都为 true，则表示触摸板位置（.obj. 状态。**touchpadPosition**）分配给**selectorPosition**。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

在**Update （）** 中，根据**Visible**属性触发显示和隐藏颜色选取器的 animator 组件中的动画触发器

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

在**Update （）** 中， **selectorPosition**用于在色轮的网格碰撞器上强制转换射线，这将返回一个 UV 位置。 然后，可以使用此位置查找色轮纹理的像素坐标和颜色值。 其他脚本可以通过**SelectedColor**属性访问此值。

![颜色选取器轮 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>第4章-覆盖控制器模型

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目标

* 了解如何使用自定义3D 模型替代控制器模型。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中单击 " **MotionControllers** "。
* 单击**替换右侧控制器**字段右侧的圆圈。
* 键入 **"BrushController**"，并从结果中选择 prefab。 可以在 "资产/AppPrefabs/**BrushController**" 下找到它。
* 选中 "**始终使用备用模式**"

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

不需要在**层次结构**面板中包含**BrushController** prefab。 但是，若要查看子组件，请执行以下操作：

* 在 "**项目**" 面板中，键入**BrushController**并将**BrushController** prefab 拖到 "**层次结构**" 面板中。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

你会在**BrushController**中找到**Tip**组件。 我们将使用其转换来启动/停止绘制线条。

* 从**层次结构**面板中删除**BrushController** 。
* **保存**场景并单击 "**播放**" 按钮。 你将能够看到画笔模型已替换右手运动控制器。

## <a name="chapter-5---painting-with-select-input"></a>第5章-用选择输入进行绘制

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目标

* 了解如何使用 "选择按钮" 事件来启动和停止线条绘制

### <a name="instructions"></a>说明

* 在 "**项目**" 面板中搜索**BrushController** prefab。
* 在 "**检查器**" 面板中，双击 " **BrushController** Script" 以查看 Visual Studio 中的代码

**BrushController 脚本**

**BrushController**订阅 InteractionManager 的**InteractionSourcePressed**和**InteractionSourceReleased**事件。 触发**InteractionSourcePressed**事件后，画笔的**Draw**属性将设置为 true;触发**InteractionSourceReleased**事件后，画笔的**Draw**属性将设置为 false。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

**绘图**设置为 true 时，画笔将在实例化的 Unity **LineRenderer**中生成点。 对此 prefab 的引用将保存在画笔的**Stroke prefab**字段中。

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

若要从颜色选取器滚轮 UI 使用当前选定的颜色， **BrushController**需要具有对**ColorPickerWheel**对象的引用。 因为在运行时将**BrushController** prefab 实例化为替换控制器，所以必须在运行时设置对场景中对象的任何引用。 在此示例中，我们使用**GameObject**来查找**ColorPickerWheel**：

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **保存**场景并单击 "**播放**" 按钮。 你将能够使用右侧控制器上的 "选择" 按钮绘制线条并进行绘制。

## <a name="chapter-6---object-spawning-with-select-input"></a>第6章-带有选择输入的对象生成

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目标

* 了解如何使用 "选择并抓住" 按钮输入事件
* 了解如何实例化对象

### <a name="instructions"></a>说明

* 在 "**项目**" 面板的 "搜索" 框中，键入**ObjectSpawner** 。 还可以在 "资产/AppPrefabs/
* 将**ObjectSpawner** prefab 拖到 "**层次结构**" 面板中。
* 在 "**层次结构**" 面板中单击 " **ObjectSpawner** "。
* **ObjectSpawner**有一个名为 "**颜色源**" 的字段。
* 从 "**层次结构**" 面板中，将 " **ColorPickerWheel** " 引用拖到此字段中。

    ![对象 Spawner 检查器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* 单击 "**层次结构**" 面板中的**ObjectSpawner** prefab。
* 在 "**检查器**" 面板中，双击 " **ObjectSpawner** Script" 以查看 Visual Studio 中的代码。

**ObjectSpawner 脚本**

**ObjectSpawner**将基元网格（cube，圆柱体）的副本实例化为空间。 检测到**InteractionSourcePressed**时，它会检查左右手使用习惯，并检查其是否为**InteractionSourcePressType**或**InteractionSourcePressType。**

对于**抓住**事件，它会递增当前网格类型（球、cube、圆柱）的索引

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

对于**Select**事件，在**SpawnObject （）** 中，将实例化新的对象，并将其作为父级并将其发布到世界。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner**使用**ColorPickerWheel**设置显示对象材料的颜色。 将为生成的对象提供此材料的实例，以使它们保留其颜色。

* **保存**场景并单击 "**播放**" 按钮。

你将能够通过 "抓住" 按钮更改对象，并通过 "选择" 按钮生成对象。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>构建应用并将其部署到混合现实门户

* 在 Unity 中，选择 "**文件 > 生成设置**"。
* 单击 "**添加打开的场景**"，将当前场景添加到**生成的场景中**。
* 单击**生成**。
* 创建名为 "App" 的**新文件夹**。
* 单击**应用**文件夹。
* 单击“选择文件夹”。
* 当 Unity 完成后，将显示文件资源管理器窗口。
* 打开**应用程序**文件夹。
* 双击 " **YourSceneName** " Visual Studio 解决方案文件。
* 使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **X64**"。
* 单击 "设备" 按钮旁边的下拉箭头，然后选择 "**本地计算机**"。
* 单击菜单中的 "**调试-> 启动但不调试**"，或按**Ctrl + F5**。

现在，在混合现实门户中生成并安装应用。 可以通过混合现实门户中的 "开始" 菜单再次启动它。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>高级设计-具有径向布局的画笔工具

![MixedReality213 Main](images/mr213-main-600px.jpg)

在本章中，你将学习如何将默认运动控制器模型替换为自定义画笔工具集合。 对于引用，可以在 "**场景**" 文件夹下找到已完成的场景**MixedReality213Advanced** 。

### <a name="instructions"></a>说明

* 在 "**项目**" 面板的 "搜索" 框中，键入**BrushSelector** 。 还可以在 "资产/AppPrefabs/
* 将**BrushSelector** prefab 拖到 "**层次结构**" 面板中。
* 对于组织，创建名为 "**画笔**" 的空 GameObject
* 将以下 prototyping 从 "**项目**" 面板拖到 "**画笔**"
    * 资产/AppPrefabs/**BrushFat**
    * 资产/AppPrefabs/**BrushThin**
    * 资产/AppPrefabs/**橡皮擦**
    * 资产/AppPrefabs/**MarkerFat**
    * 资产/AppPrefabs/**MarkerThin**
    * 资产/AppPrefabs/**铅笔**

    ![画笔](images/mixedreality213-brushes-250px.png)

* 在 "**层次结构**" 面板中单击 " **MotionControllers** prefab"。
* 在 "**检查器**" 面板中，取消选中 "在**运动控制器可视化工具**上**始终使用替代右模型**"
* 在 "**层次结构**" 面板中，单击 " **BrushSelector** "
* **BrushSelector**有一个名为**ColorPicker**的字段
* 从 "**层次结构**" 面板中，将 " **ColorPickerWheel** " 拖动到**检查器**面板中的 " **ColorPicker** " 字段。

    ![将 ColorPickerWheel 分配给画笔选择器](images/mr213-brushselector-500px.jpg)

* 在 "**层次结构**" 面板中的 " **BrushSelector** prefab" 下，选择 " **Menu** " 对象。
* 在 "**检查器**" 面板中的**LineObjectCollection**组件下，打开 "**对象**数组" 下拉列表。 你将看到6个空槽。
* 从 "**层次结构**" 面板中，将 "**画笔**" 下的每个 prototyping 父级以任意顺序拖动到这些槽。 （请确保从场景中拖动 prototyping，而不是项目文件夹中的 prototyping。）

![画笔选择器](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

由于**BrushSelector**继承了**AttachToController**，它将在 "**检查器**" 面板中显示**左右手使用习惯**和**元素**选项。 我们选择了 "**向右**" 并将画笔工具**连接到右侧**的右控制器。

**BrushSelector**利用了两个实用工具：

* **椭圆形**：用于沿椭圆形状生成空间中的点。
* **LineObjectCollection**：使用由任意直线类（例如，椭圆形）生成的点来分配对象。 这就是我们用来沿椭圆形状放置画笔的内容。

结合使用时，可以使用这些实用程序创建放射状菜单。

**LineObjectCollection 脚本**

**LineObjectCollection**具有控件沿行分布的对象的大小、位置和旋转。 这对于创建径向菜单（如画笔选择器）很有用。 若要创建画笔的外观，使其在接近中心选定位置的情况下进行缩放， **ObjectScale**曲线会在中心处峰值，并在边缘处关闭 tapers。

**BrushSelector 脚本**

对于**BrushSelector**，我们选择了使用过程动画。 首先，画笔模型由**LineObjectCollection**脚本分布在一个椭圆中。 然后，每个画笔负责根据其**DisplayMode**值来维护其在用户的手边，这会根据所选内容进行更改。 我们选择了过程方法，因为当用户选择画笔时，画笔位置转换的概率很高。 Mecanim 动画可以合理地处理中断，但比简单的 Lerp 操作要复杂得多。

**BrushSelector**结合使用这两种方法。 检测到触摸板输入后，画笔选项将变为可见，并沿径向菜单向上缩放。 超时期限（指示用户进行了选择）之后，画笔选项将再次缩小，只留下所选的画笔。

**可视化触摸板输入**

即使在完全替换控制器模型的情况下，显示原始模型输入的输入也可能会很有帮助。 这有助于使用户的操作成为现实。 对于**BrushSelector** ，我们选择了在收到输入时使触摸板短暂可见。 这是通过从控制器检索触摸板元素，将其材料替换为自定义材料，然后根据收到的触摸板输入的最后时间向该材料的颜色应用渐变来完成的。

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**带有触摸板输入的画笔工具选择**

当画笔选择器检测到触摸板的按下输入时，它将检查输入的位置以确定其是否在左侧或右侧。

**笔划粗细与 selectPressedAmount**

可以通过**selectPressedAmount**获取按下量的模拟值，而不是**InteractionSourcePressed （）** 中的**InteractionSourcePressType 事件。** 可以在**InteractionSourceUpdated （）** 中检索此值。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**橡皮擦脚本**

**橡皮擦**是一种特殊类型的画笔，用于重写基**画笔**的**DrawOverTime （）** 函数。 绘图为 true 时，橡皮擦检查其刀尖是否与任何现有画笔笔划相交。 如果已添加到队列中，则会将它们添加到要缩减和删除的队列中。

## <a name="advanced-design---teleportation-and-locomotion"></a>高级设计-Teleportation 和 locomotion

如果要允许用户使用 teleportation 在场景周围移动，请使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。 还需要添加**InputManager**和**DefaultCursor**。 由于**MixedRealityCameraParent**已将**MotionControllers**和**边界**包含为子组件，因此应该删除现有的**MotionControllers**和**环境**prefab。

### <a name="instructions"></a>说明

* 在**层次结构**面板中删除 **"MixedRealityCamera**"、"**环境**" 和 " **MotionControllers** "
* 在 "**项目" 面板**中，搜索并将以下 prototyping 拖到 "**层次结构**" 面板中：
    * 资产/AppPrefabs/Input/Prototyping/**MixedRealityCameraParent**
    * 资产/AppPrefabs/Input/Prototyping/**InputManager**
    * 资产/AppPrefabs/Input/Prototyping/Cursor/**DefaultCursor**

    ![混合现实相机父项](images/mr213-cameraparent-300px.png)

* 在**层次结构**面板中，单击 "**输入管理器**"
* 在 "**检查器**" 面板中，向下滚动到**简单的单指针选择器**部分
* 从 "**层次结构**" 面板中，将**DefaultCursor**拖到**Cursor**字段

    ![分配 DefaultCursor](images/mr213-defaultcursor-500px.png)

* **保存**场景并单击 "**播放**" 按钮。 你将能够使用操纵杆向左或向右旋转。

## <a name="the-end"></a>结束

这就是本教程的结尾！ 已学习：

* 如何使用 Unity 的游戏模式和运行时中的运动控制器模型。
* 如何使用不同类型的按钮事件及其应用程序。
* 如何在控制器顶部覆盖 UI 元素或对其进行完全自定义。

现在，你可以开始创建自己的具有运动控制器的沉浸式体验！

## <a name="completed-scenes"></a>已完成场景

* 在 Unity 的 "**项目**" 面板中，单击 "**场景**" 文件夹。
* 你将发现两个 Unity 场景**MixedReality213**和**MixedReality213Advanced**。
    * **MixedReality213**：通过单画笔完成场景
    * **MixedReality213Advanced**：具有多个画笔并带有 "选择按钮的按量" 示例的已完成场景

## <a name="see-also"></a>另请参阅

* [MR 输入213项目文件](https://github.com/Microsoft/MixedReality213)
* [混合现实工具包-运动控制器测试场景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [混合现实工具包-抓取机制](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [运动控制器开发指南](motion-controllers.md)
