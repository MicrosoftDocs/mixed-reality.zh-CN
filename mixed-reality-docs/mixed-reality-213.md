---
title: MR 输入 213
description: 请按照本编码教程中使用 Unity、 Visual Studio 和沉浸式耳机，若要了解 motion 控制器的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit unity，令人着迷，动作控制器、 学院、 教程
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592988"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 输入 213:运动控制器

混合的现实世界中的动作控制器添加另一个级别的交互功能。 与[动作控制器](motion-controllers.md)，我们可以直接与对象进行交互以更自然的方式，类似于我们在现实生活中的物理交互增加浸入式并喜欢以你的应用体验。

在 MR 输入 213，我们将通过创建简单的空间绘制体验探讨运动控制器的输入的事件。 与此应用，用户就可以绘制各种类型的画笔和颜色的三维空间中。

## <a name="topics-covered-in-this-tutorial"></a>在本教程中涵盖的主题

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**控制器可视化效果**|**控制器输入的事件**|**自定义控制器和 UI**|
|了解如何呈现 Unity 的游戏模式和运行时中的动作控制器模型。|了解不同类型的按钮事件和他们的应用程序。|了解如何覆盖在控制器上的 UI 元素或完全自定义。|

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 输入 213:运动控制器</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>系统必备

有关，请参阅沉浸式耳机的安装清单[本页](install-the-tools.md)。

* 本教程需要[Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>项目文件

* [将文件下载](https://github.com/Microsoft/MixedReality213/archive/master.zip)所需的项目和文件提取到桌面。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/MixedReality213)。

## <a name="unity-setup"></a>Unity 安装程序

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目标

* 优化 Unity 为 Windows Mixed Reality 开发
* 设置混合的现实照相机
* 设置环境

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择**打开**。
* 导航到你的桌面和查找**MixedReality213 master**你之前未存档的文件夹。
* 单击“选择文件夹”。
* 完成 Unity 加载项目文件后，你将能够看到 Unity 编辑器。
* 在 Unity 中，选择**文件 > 生成设置**。

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* 选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**按钮。
* 目标设备设置为**任何设备**
* 将生成类型设置为**D3D**
* 设置为 SDK**最新安装**
* 检查**UnityC#项目**
    * 这允许您修改 Visual Studio 项目中的脚本文件而无需重新生成 Unity 项目。
* 单击**播放器设置**。
* 在中**Inspector**面板中，向下滚动到底部
* 在 XR 设置中，检查**虚拟现实支持**
* 在虚拟现实 Sdk 下选择**Windows Mixed Reality**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* 关闭**生成设置**窗口。

### <a name="project-structure"></a>项目结构

本教程使用**[混合现实工具包-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**。 您可以在找到版本[本页](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**已完成为你的引用的场景**
* 您会发现两个已完成的 Unity 场景下**场景**文件夹。
    * **MixedReality213**:已完成的场景中具有单个画笔
    * **MixedReality213Advanced**:完成高级设计使用多个画笔的场景

**本教程中的新场景安装程序**
* 在 Unity 中，单击**文件 > 新的场景**
* 删除**主照相机**和**定向光**
* 从**项目面板**，搜索并拖动到以下预设**层次结构**面板：
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![照相机和环境](images/mr213-cameraenvironment-300px.jpg)
* 有两个相机预设混合现实工具包中：
    * **MixedRealityCamera.prefab**:仅照相机
    * **MixedRealityCameraParent.prefab**:照相机 + Teleportation + 边界
    * 在本教程中，我们将使用**MixedRealityCamera**而无需 teleportation 功能。 因此，我们添加了简单**环境**预设包含基本的基底，若要让用户感到接地。
    * 若要详细了解与 teleportation **MixedRealityCameraParent**，请参阅[高级设计-Teleportation 和 locomotion](#advanced-design---teleportation-and-locomotion)

**Skybox 安装程序**
* 单击**窗口 > 照明 > 设置**
* 单击右侧的圆形**Skybox 材料字段**
* Gray 中键入，然后选择**SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![设置 skybox](images/mr123-skyboxsetting-400px.jpg)
* 检查**Skybox**选项才能够看到分配灰色渐变 skybox

![切换 skybox 选项](images/mr213-skyboxcheck-400px.jpg)
* 使用 MixedRealityCamera、 环境和灰色 skybox 场景将如下所示。

![MixedReality213 环境](images/mr213-environment-600px.jpg)
* 单击**文件 > 另存为场景**
* **保存**场景文件夹具有任何名称下的场景

## <a name="chapter-1---controller-visualization"></a>第 1 章-控制器可视化效果

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目标

* 了解如何呈现控制器模型在 Unity 的游戏模式下和在运行时的动作。

Windows Mixed Reality 提供动画的控制器模型为控制器的可视化效果。 有几种方法可以在应用中执行为控制器的可视化效果：
* 默认值-使用默认控制器，而无需修改
* 混合-使用默认控制器，但自定义的某些元素或覆盖 UI 组件
* 更换 — 使用你自己自定义控制器的三维模型

在本章中，我们将了解这些控制器的自定义的示例。

### <a name="instructions"></a>说明

* 在中**项目**面板中，键入**MotionControllers**在搜索框中。 此外可以在资产/HoloToolkit/输入/预设下找到它 /。
* 拖动**MotionControllers**到 prefab**层次结构**面板。
* 单击**MotionControllers**预设中**层次结构**面板。

**MotionControllers 预设**

**MotionControllers**预设已**MotionControllerVisualizer**为槽的备用控制器模型提供的脚本。 如果指定如手的形状或一双刃剑自己自定义三维模型，然后选中始终使用备用左/右模型，您将看到它们而不是默认模型。 我们将使用第 4 章中的此槽的控制器模型替换为画笔。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**说明**
* 在中**Inspector**面板中，双击**MotionControllerVisualizer**脚本，以查看 Visual Studio 中的代码

**MotionControllerVisualizer script**

**MotionControllerVisualizer**并**MotionControllerInfo**类提供了用来访问和修改默认控制器模型。 **MotionControllerVisualizer** Unity 的订阅**InteractionSourceDetected**事件和自动实例化控制器模型，何时找到它们。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

根据传递控制器模型[glTF 规范](https://github.com/KhronosGroup/glTF)。 已创建此格式提供一种通用格式，同时提高传输和解压缩三维资产后面的过程。 在这种情况下，我们需要检索和加载在运行时，控制器模型，因为我们想要让用户获得的体验尽可能流畅，并不保证哪个版本的运动控制器用户可能正在使用。 本课程中的，混合现实工具包，通过使用新版 Khronos 组[UnityGLTF 项目](https://github.com/KhronosGroup/UnityGLTF)。

一旦已传递控制器，可以使用脚本**MotionControllerInfo**特定控制器元素查找转换，以便它们可以正确地确定自己的位置。

在更高版本的章中，我们将了解如何使用这些脚本将 UI 元素附加到的控制器。

*在一些脚本，您会发现使用的代码块 **#if ！UNITY_EDITOR**或**UNITY_WSA**。部署到 Windows 时，只能在 UWP 运行时上运行这些代码块。这是因为 Unity 编辑器和 UWP 应用运行时使用的 Api 集不同。*
* **保存**场景和单击**播放**按钮。

你将能够看到与您的头戴式中动作控制器场景。 您可以看到详细的动画效果的按钮单击、 摇杆移动和触摸板触摸突出显示。

![MR213_Controller 可视化效果默认](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第 2 章-附加到控制器的 UI 元素

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目标

* 了解有关元素的动作控制器
* 了解如何将对象附加到的控制器的特定部分

在本章中，您将学习如何将用户界面元素添加到控制器的用户可以轻松地访问和处理在任何时间。 您将学习如何添加简单的颜色选取器 UI 使用触摸板输入。

### <a name="instructions"></a>说明

* 在中**项目**面板中，搜索**MotionControllerInfo**脚本。
* 从搜索结果中，双击**MotionControllerInfo**脚本，以查看 Visual Studio 中的代码。

**MotionControllerInfo script**

第一步是选择想要附加到的 UI 控制器的哪些元素。 这些元素中定义**ControllerElementEnum**中**MotionControllerInfo.cs**。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **主页**
* **菜单**
* **Grasp**
* **摇杆**
* **Select**
* **触摸板**
* **指针姿势**– 此元素表示指向向前方向的控制器的提示。

**说明**
* 在中**项目**面板中，搜索**AttachToController**脚本。
* 从搜索结果中，双击**AttachToController**脚本，以查看 Visual Studio 中的代码。

**AttachToController 脚本**

**AttachToController**脚本提供了简单的方法将任何对象附加到指定的控制器左右手使用习惯和元素。

In **AttachElementToController()**,
* 检查左右手使用习惯使用**MotionControllerInfo.Handedness**
* 获取控制器使用的特定元素**MotionControllerInfo.TryGetElement()**
* 检索的元素后从控制器模型，父对象下它将转换并设置为零的对象的本地位置和旋转。

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

若要使用的最简单方法**AttachToController**脚本是从它继承，如我们所做的情况下**ColorPickerWheel。** 只需重写**OnAttachToController**并**OnDetatchFromController**函数来执行您的安装程序 / 明细时检测到 / 断开连接控制器。

**说明**
* 在中**项目**面板中，在搜索框中键入**ColorPickerWheel**。 此外可以在资产/AppPrefabs 下找到它 /。
* 拖动**ColorPickerWheel**到 prefab**层次结构**面板。
* 单击**ColorPickerWheel**预设中**层次结构**面板。
* 在中**Inspector**面板中，双击**ColorPickerWheel**脚本，以查看 Visual Studio 中的代码。

![ColorPickerWheel 预设](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 脚本**

由于**ColorPickerWheel**继承**AttachToController**，它显示了**左右手使用习惯**并**元素**中**检查器**面板。 我们将把在左侧的控制器上的触摸板元素到连接的用户界面。

![ColorPickerWheel 脚本](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel**重写**OnAttachToController**并**OnDetatchFromController**订阅将用于与颜色选择下一步一章中的输入事件触摸板进行输入。

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
* **保存**场景和单击**播放**按钮。

**将对象附加到的控制器的另一种方法**

我们建议你的脚本，从继承**AttachToController**并重写**OnAttachToController**。 但是，这不总是可能。 一种替代方法使用它作为独立组件。 当你想要将现有预设可附加到一个控制器，而无需重构您的脚本时，这很有用。 只需让类等待 IsAttached 设置为 true，然后才能执行任何设置。 若要执行此操作的最简单方法是使用协同程序的 Start。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第 3 章 — 使用触摸板进行输入

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目标

* 了解如何将触摸板输入的数据事件
* 了解如何使用触摸板轴位置信息的应用体验

### <a name="instructions"></a>说明

* 在中**层次结构**面板中，单击**ColorPickerWheel**
* 在中**Inspector**面板下**Animatior**，双击**ColorPickerWheelController**
* 你将能够看到**动画器**打开选项卡

**显示/隐藏 UI 与 Unity 的动画控制器**

若要显示和隐藏**ColorPickerWheel**动画的 UI 中，我们将使用[Unity 的动画系统](https://docs.unity3d.com/Manual/AnimationOverview.html)。 设置**ColorPickerWheel**的**Visible**属性设置为 true 或 false 触发器**显示**并**隐藏**动画触发器。 **显示**并**隐藏**中定义参数**ColorPickerWheelController**动画控制器。

![Unity 动画控制器](images/mr123-animationcontroller-550px.jpg)

**说明**
* 在中**层次结构**面板中，选择**ColorPickerWheel**预设
* 在中**Inspector**面板中，双击**ColorPickerWheel**脚本，以查看 Visual Studio 中的代码

**ColorPickerWheel 脚本**

**ColorPickerWheel** Unity 的订阅**InteractionSourceUpdated**以侦听触摸板事件的事件。

在中**InteractionSourceUpdated()**，该脚本首先检查以确保其：
* 是实际的触摸板事件 (obj.state。**touchpadTouched**)
* 源自左控制器 (obj.state.source。**左右手使用习惯**)

如果两者均为 true，触摸板位置 (obj.state。**touchpadPosition**) 分配给**selectorPosition**。

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

在**update （)** 根据**可见**属性，它将触发颜色选取器的动画器组件中的显示和隐藏动画触发器

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

在中**update （)**， **selectorPosition**用于将一条颜色盘网格碰撞体，它将返回 UV 位置在强制转换。 此位置可以用于查找的像素坐标和颜色的颜色盘纹理值。 此值是通过其他脚本可以访问**SelectedColor**属性。

![颜色选取器滚轮光线投射的细节](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a>第 4 章-重写控制器模型

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目标

* 了解如何重写具有自定义的三维模型的控制器模型。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>说明

* 单击**MotionControllers**中**层次结构**面板。
* 单击右侧的圆形**备用右控制器**字段。
* 在键入**BrushController**，然后从结果选择预设。 你可以在资产/AppPrefabs 下找到它/**BrushController**。
* 检查**始终使用正确的备用模式**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController**预设不需要将其纳入**层次结构**面板。 但是，若要查看其子组件：
* 在中**项目**面板中，键入**BrushController**拖到**BrushController**到 prefab**层次结构**面板。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

您会发现**提示**组件**BrushController**。 我们将其转换要启动/停止绘制线条。
* 删除**BrushController**从**层次结构**面板。
* **保存**场景和单击**播放**按钮。 你将能够看到画笔模型替换为右侧运动控制器。

## <a name="chapter-5---painting-with-select-input"></a>第 5 章-使用选择的输入进行绘制

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目标

* 了解如何使用选择按钮事件来启动和停止为线图

### <a name="instructions"></a>说明

* 搜索**BrushController**预设中**项目**面板。
* 在中**Inspector**面板中，双击**BrushController**脚本，以查看 Visual Studio 中的代码

**BrushController 脚本**

**BrushController**订阅 InteractionManager **InteractionSourcePressed**并**InteractionSourceReleased**事件。 当**InteractionSourcePressed**触发事件时，将画笔的**绘制**属性设置为 true; 当**InteractionSourceReleased**触发事件时，将画笔的**绘制**属性设置为 false。

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

虽然**绘制**设置为 true，画笔会生成点在实例化 Unity **LineRenderer**。 此预设的引用保存在的画笔**笔划 Prefab**字段。

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

若要使用从颜色选取器滚轮 UI 中，当前选定的颜色**BrushController**需要具有对引用**ColorPickerWheel**对象。 因为**BrushController**在更换控制器的运行时实例化预设时，必须在运行时设置的场景中的对象的引用。 在这种情况下，我们使用**GameObject.FindObjectOfType**来查找**ColorPickerWheel**:

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
* **保存**场景和单击**播放**按钮。 你将能够绘制线条和绘制右侧的控制器上使用选择按钮。

## <a name="chapter-6---object-spawning-with-select-input"></a>第 6-章对象生成与 Select 一起输入

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目标

* 了解如何使用 Select，然后抓住按钮输入的事件
* 了解如何实例化对象

### <a name="instructions"></a>说明

* 在中**项目**面板中，键入**ObjectSpawner**在搜索框中。 此外可以在资产/AppPrefabs 下找到它 /
* 拖动**ObjectSpawner**到 prefab**层次结构**面板。
* 单击**ObjectSpawner**中**层次结构**面板。
* **ObjectSpawner**具有一个名为字段**颜色源**。
* 从**层次结构**面板中，将**ColorPickerWheel**到此字段的引用。

![对象 Spawner 检查器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* 单击**ObjectSpawner**预设中**层次结构**面板。
* 在中**Inspector**面板中，双击**ObjectSpawner**脚本，以查看 Visual Studio 中的代码。

**ObjectSpawner 脚本**

**ObjectSpawner**到空间实例化的基元的网格 （多维数据集、 球体、 cylinder） 副本。 当**InteractionSourcePressed**检测到它会检查旋向性以及它是否**InteractionSourcePressType.Grasp**或**InteractionSourcePressType.Select**事件。

有关**掌握**事件，则会递增当前网格类型 （球体、 立方体、 圆柱体） 的索引

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

有关**选择**事件，请在**SpawnObject()**，新对象是实例化、 无父级且已发布到世界。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner**使用**ColorPickerWheel**设置显示对象的材料的颜色。 生成的对象是给定此材料的实例，因此它们将保留其颜色。
* **保存**场景和单击**播放**按钮。

你将能够更改与掌握按钮对象并生成具有选择按钮的对象。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>生成并部署到混合现实门户应用
* 在 Unity 中，选择**文件 > 生成设置**。
* 单击**添加打开场景**若要添加到当前场景**生成中的场景**。
* 单击“生成” 。
* 创建**新文件夹**名为"应用"。
* 单击一下**应用**文件夹。
* 单击“选择文件夹”。
* Unity 完成操作后，将出现一个文件资源管理器窗口。
* 打开**应用**文件夹。
* 双击**YourSceneName.sln** Visual Studio 解决方案文件。
* 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X64**。
* 单击设备按钮旁边的下拉箭头，然后选择**本地计算机**。
* 单击**调试-> 启动不调试**中的菜单或按**Ctrl + F5**。

现在应用生成并安装在混合现实门户。 您可以再次启动通过混合现实门户中的开始菜单。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>高级的设计-画笔工具与射线布局

![MixedReality213 Main](images/mr213-main-600px.jpg)

在本章中，您将学习如何使用自定义画笔工具集合替换默认运动控制器模型。 为了便于参考，可以找到已完成的场景**MixedReality213Advanced**下**场景**文件夹。

### <a name="instructions"></a>说明

* 在中**项目**面板中，键入**BrushSelector**在搜索框中。 此外可以在资产/AppPrefabs 下找到它 /
* 拖动**BrushSelector**到 prefab**层次结构**面板。
* 对于组织中，创建名为空的 GameObject**画笔**
* 以下预设从拖动**项目**面板拖动到图表**画笔**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![画笔](images/mixedreality213-brushes-250px.png)
* 单击**MotionControllers**预设中**层次结构**面板。
* 在中**Inspector**面板中，取消选中**始终使用备用右模型**上**运动控制器可视化工具**
* 在中**层次结构**面板中，单击**BrushSelector**
* **BrushSelector**有一个名为**颜色选取器**
* 从**层次结构**面板中，将**ColorPickerWheel**到**颜色选取器**字段中**检查器**面板。

![分配 ColorPickerWheel 的画笔选择器](images/mr213-brushselector-500px.jpg)
* 在中**层次结构**面板下**BrushSelector**预设，请选择**菜单**对象。
* 在**Inspector**面板下**LineObjectCollection**组件中，打开**对象**数组下拉列表。 你将看到 6 个空插槽。
* 从**层次结构**面板中，将每个父级下预设**画笔**到按任意顺序这些槽的 GameObject。 （请确保自己从场景，而不在项目文件夹中预设拖动的预设。）

![画笔选择器](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector 预设**

由于**BrushSelector**继承**AttachToController**，它显示了**左右手使用习惯**并**元素**中的选项**检查器**面板。 我们选择了**右**并**指向会带来**若要将画笔工具附加到与正向右侧控制器。

**BrushSelector**使用两个实用程序：
* **椭圆**： 用于在空间沿椭圆形形状中生成点。
* **LineObjectCollection**： 将分发对象使用生成的任何行类 （例如，椭圆） 的点。 这是什么，我们将使用来放置我们画笔沿椭圆形形状。

结合使用时，可以使用这些实用程序来创建径向菜单。

**LineObjectCollection 脚本**

**LineObjectCollection**具有的大小、 位置和分布沿其行中的对象的旋转的控件。 这可用于创建类似的画笔选择器径向菜单。 若要创建的外观画笔该规模从它们接近所选中心位置，如 nothing **ObjectScale**边缘关闭曲线中的中心和音量补偿器的峰值。

**BrushSelector 脚本**

情况下**BrushSelector**，我们选择了使用过程的动画。 首先，通过一个椭圆中分布画笔模型**LineObjectCollection**脚本。 然后，每个画笔负责维护其基于用户的手中的位置及其**DisplayMode**更改基于对所选内容的值。 我们选择的原因是高概率的画笔在用户选择画笔被中断的位置转换过程的方法。 Mecanim 动画可以处理服务中断正常，但往往比简单 Lerp 操作更复杂。

**BrushSelector**使用这两者的组合。 检测到触摸板进行输入时，画笔选项变得可见和纵向扩展沿的射线的菜单。 （这表明用户已做出了选择） 超时期限过后画笔选项规模下再次离开仅选定的画笔。

**可视化触摸板进行输入**

甚至在控制器模型已被完全替换的情况下，它可以是有帮助，以显示原始模型输入输入。 这有助于在现实中接地用户的操作。 有关**BrushSelector**我们选择以使触摸板简要可见时收到了输入。 通过从替换自定义的材料，为其材料的控制器中检索的触摸板元素执行此操作，然后将过渡应用于该材料的颜色基于最后一次触摸板接收输入。

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

**画笔工具使用触摸板进行输入的选定内容**

当画笔选择器检测到触摸板的按下的输入时，它会检查输入以确定它是从左到右的位置。

**使用 selectPressedAmount 笔画粗细**

而不是**InteractionSourcePressType.Select**中的事件**InteractionSourcePressed()**，就可以通过按下的量的模拟值**selectPressedAmount**. 此值可以在中检索**InteractionSourceUpdated()**。

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

**橡皮擦**是一种特殊的重写基的画笔**画笔**的**DrawOverTime()** 函数。 绘制为真，橡皮擦将检查以确定其提示是否与任何现有的画笔笔画相交。 如果是这样，它们都添加到队列，向下要收缩和删除。

## <a name="advanced-design---teleportation-and-locomotion"></a>高级的设计-Teleportation 和 locomotion

如果你想要允许用户与使用摇杆 teleportation 在场景周围移动，请使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。 此外需要添加**InputManager**并**DefaultCusor**。 由于**MixedRealityCameraParent**已包括**MotionControllers**并**边界**作为子组件，应删除现有**MotionControllers**并**环境**预设。

### <a name="instructions"></a>说明

* 在中**层次结构**面板中，删除**MixedRealityCamera**，**环境**和**MotionControllers**
* 从**项目面板**，搜索并拖动到以下预设**层次结构**面板：
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![混合的现实照相机父](images/mr213-cameraparent-300px.png)
* 在中**层次结构**面板中，单击**输入管理器**
* 在中**Inspector**面板中，向下滚动到**简单单个指针选择器**部分
* 从**层次结构**面板中，将**DefaultCursor**到**游标**字段

![分配 DefaultCursor](images/mr213-defaultcursor-500px.png)
* **保存**场景和单击**播放**按钮。 你将能够使用摇杆左/右或 teleport 轮换一次。

## <a name="the-end"></a>结束

就是本教程结束 ！ 介绍了：
* 如何使用 Unity 的游戏模式和运行时中的动作控制器模型。
* 如何使用不同类型的按钮事件和他们的应用程序。
* 如何覆盖在控制器上的 UI 元素或完全自定义。

现已准备好开始使用 motion 控制器创建自己的沉浸式体验 ！

## <a name="completed-scenes"></a>已完成的场景

* 在 Unity 中的**项目**面板中单击**场景**文件夹。
* 您会发现两个 Unity sceens **MixedReality213**并**MixedReality213Advanced**。
    * **MixedReality213**:已完成的场景中具有单个画笔
    * **MixedReality213Advanced**:使用选择按钮的按量示例的多个画笔的已完成的场景

## <a name="see-also"></a>请参阅

* [MR 输入 213 项目文件](https://github.com/Microsoft/MixedReality213)
* [混合的现实工具包-运动控制器测试场景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [混合的现实工具包-随取即行机制](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [运动控制器开发指导原则](motion-controllers.md)
