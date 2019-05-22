---
title: MR 基础知识 101-与设备的完整项目
description: 请按照本演练中使用 Unity、 Visual Studio 和 HoloLens 了解 Windows Mixed Reality 的基础知识编码。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实，Windows Mixed Reality、 HoloLens、 全息图，学院，教程
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591557"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>MR 基础知识 101:与设备的完整项目

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

本教程将引导您完成在 Unity 中，用于演示在 HoloLens 包括核心 Windows Mixed Reality 功能构建的完整项目[注视](gaze.md)，[手势](gestures.md)，[语音输入](voice-input.md)，[空间声音](spatial-sound.md)并[空间映射](spatial-mapping.md)。

本教程需要大约 1 小时才能完成。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 基础知识 101:与设备的完整项目</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。
* HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
  * 如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。
  * 如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。
  * 如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。
* 取消存档到您的桌面或其他轻松地访问位置的文件。 保留文件夹名称作为**Origami**。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)。

## <a name="chapter-1---holo-world"></a>第 1 章-"Holo"世界

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

在本章中，我们将安装我们的第一个 Unity 项目并单步执行生成和部署过程。

### <a name="objectives"></a>目标

* 为 holographic 开发设置 Unity。
* 请一张全息图。
* 所做的一张全息图，请参阅。

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择**打开**。
* 输入与位置**Origami**文件夹你之前未存档。
* 选择**Origami**然后单击**选择文件夹**。
* 由于**Origami**项目不包含一个场景，保存到新文件使用空的默认场景：**文件** / **另存为场景**。
* 命名新的场景**Origami**然后按**保存**按钮。

#### <a name="setup-the-main-virtual-camera"></a>安装程序主虚拟照相机

* 在中**层次结构面板**，选择**Main Camera**。
* 在中**Inspector**将其转换位置设置为**0,0,0**。
* 查找**清除标志**属性，并将更改从下拉列表中**Skybox**到**纯色**。
* 单击**背景**字段以打开颜色选取器。
* 设置**R、 G、 B 和 A**到**0**。

#### <a name="setup-the-scene"></a>设置场景

* 在中**层次结构面板**，单击**创建**并**创建空白**。
* 右键单击新**GameObject**和选择重命名。 重命名为 GameObject **OrigamiCollection**。
* 从**全息**项目面板中的文件夹 （展开资产和选择全息或双击项目面板中的全息文件夹）：
  * 拖动**阶段**到层次结构的子级**OrigamiCollection**。
  * 拖动**Sphere1**到层次结构的子级**OrigamiCollection**。
  * 拖动**Sphere2**到层次结构的子级**OrigamiCollection**。
* 右键单击**定向光**对象中**层次结构面板**，然后选择**删除**。
* 从**全息**文件夹中，拖动**灯**到的根目录**层次结构面板**。
* 在中**层次结构**，选择**OrigamiCollection**。
* 在中**Inspector**，将转换位置设置为**0、-0.5、 2.0**。
* 按**播放**在 Unity 中以预览你全息按钮。
* 您应看到预览窗口中的 Origami 对象。
* 按**播放**停止预览模式下的第二个时机。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>导出到 Visual Studio 从 Unity 项目

* 在 Unity 中，选择**文件 > 生成设置**。
* 选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。
* 设置**SDK**到**通用 10**并**生成类型**到**D3D**。
* 检查**UnityC#项目**。
* 单击**添加打开场景**添加场景。
* 单击“生成” 。
* 在文件资源管理器窗口中显示，创建**新文件夹**名为"应用"。
* 单击一下**应用程序文件夹**。
* 按**选择文件夹**。
* Unity 完成操作后，将出现一个文件资源管理器窗口。
* 打开**应用**文件夹。
* 打开 （双击） **Origami.sln**。
* 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X86**。
* 单击设备按钮旁边的箭头，然后选择**远程计算机**通过 Wi-fi 部署。
  * 设置**地址**的名称或 IP 地址在 HoloLens。 如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**问 Cortana 或 **"你好，小娜，我的 IP 地址是什么？"**
  * 如果通过 USB 连接了 HoloLens，则可能会改为选择**设备**通过 USB 部署。
  * 将保留**身份验证模式**设置为**通用**。
  * 单击**选择**

* 单击**调试 > 启动不调试**或按**Ctrl + F5**。 如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))。

* Origami 项目将现在构建、 部署到你 HoloLens，然后运行。
* 在你 HoloLens 上并浏览以查看新全息。

## <a name="chapter-2---gaze"></a>第 2 章-的视线移动

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

在本章中，我们将推出的三种方式进行交互的第一个与你全息-[注视](gaze.md)。

### <a name="objectives"></a>目标

* 可视化你的视线移动使用 world 锁定的游标。

### <a name="instructions"></a>说明

* 返回到你的 Unity 项目，并关闭生成设置窗口中，如果它仍处于打开状态。
* 选择**全息**中的文件夹**项目面板**。
* 拖动**游标**对象插入**层次结构面板**根级别。
* 双击**游标**对象，若要更详细地介绍它。
* 右键单击**脚本**项目面板中的文件夹。
* 单击**创建**子菜单。
* 选择**C#脚本**。
* 脚本命名为**WorldCursor**。 注意：该名称区分大小写。 不需要添加.cs 扩展名。
* 选择**游标**对象中**层次结构面板**。
* 拖放到**WorldCursor**脚本**检查器面板**。
* 双击**WorldCursor**脚本以在 Visual Studio 中打开它。
* 为此代码复制并粘贴**WorldCursor.cs**并**全部保存**。

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* 重新生成该应用程序从**文件 > 生成设置**。
* 返回到之前用于将部署到你 HoloLens 的 Visual Studio 解决方案。
* 选择全部重新加载出现提示时。
* 单击**调试-> 启动不调试**或按**Ctrl + F5**。
* 现在看起来在场景周围，并请注意，光标如何与对象的形状进行交互。

## <a name="chapter-3---gestures"></a>第 3 章-手势

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

在本章中，我们将添加对的支持[手势](gestures.md)。 当用户选择纸张球体时，我们将使处于开启使用 Unity 的物理引擎的重力球体。

### <a name="objectives"></a>目标

* 控制你全息与选择的笔势。

### <a name="instructions"></a>说明

我们首先将创建一个脚本，然后可以检测到选择手势。

* 在中**脚本**文件夹中，创建一个名为脚本**GazeGestureManager**。
* 拖动**GazeGestureManager**拖动到脚本**OrigamiCollection**层次结构中的对象。
* 打开**GazeGestureManager** Visual Studio 中编写脚本，并添加以下代码：

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* 在脚本文件夹中名为这次创建另一个脚本**SphereCommands**。
* 展开**OrigamiCollection**层次结构视图中的对象。
* 拖动**SphereCommands**拖动到脚本**Sphere1**层次结构面板中的对象。
* 拖动**SphereCommands**拖动到脚本**Sphere2**层次结构面板中的对象。
* 在 Visual Studio 中打开脚本进行编辑，并将默认代码替换此为：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* 导出、 生成和应用部署到你 HoloLens。
* 查看其中一个球体。
* 执行选择手势并观看球体拖放到下面图面上。

## <a name="chapter-4---voice"></a>第 4 章-语音

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

在本章中，我们将添加两个支持[语音命令](voice-input.md):"重置的 world"返回到其原始位置，则删除的球体和"删除球体"以使处于球体。

### <a name="objectives"></a>目标

* 在背景中添加始终侦听语音命令。
* 创建一张全息图，待语音命令做出反应。

### <a name="instructions"></a>说明

* 在中**脚本**文件夹中，创建一个名为脚本**SpeechManager**。
* 拖动**SpeechManager**拖动到脚本**OrigamiCollection**层次结构中的对象
* 打开**SpeechManager** Visual Studio 中的脚本。
* 为此代码复制并粘贴**SpeechManager.cs**并**全部保存**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* 打开**SphereCommands** Visual Studio 中的脚本。
* 更新脚本，以读取，如下所示：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* 导出、 生成和应用部署到你 HoloLens。
* 看到一个球体，就会说"**Drop 球体**"。
* 说"**重置世界**"将恢复到其初始位置。

## <a name="chapter-5---spatial-sound"></a>第 5 章-空间声音

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

在本章中，我们将将音乐添加到应用程序中，然后触发特定操作的声音效果。 我们将使用[空间声音](spatial-sound.md)以便声音 3D 空间中的特定位置。

### <a name="objectives"></a>目标

* 听到全息在您的世界。

### <a name="instructions"></a>说明

* 在顶部菜单中，Unity 选择**编辑 > 项目设置 > 音频**
* 在右侧的检查器窗格中，找到**Spatializer 插件**设置并选择**MS HRTF Spatializer**。
* 从**全息**文件夹中的项目面板中，拖动**环境**对象拖到**OrigamiCollection**层次结构面板中的对象。
* 选择**OrigamiCollection**并找到**音频源**组件检查器面板中。 更改这些属性：
  * 检查**Spatialize**属性。
  * 检查**唤醒状态上播放**。
  * 更改**空间 Blend**到**3D**通过将滑块拖到最右侧。 当移动滑块时，值应从 0 更改为 1 中。
  * 检查**循环**属性。
  * 展开**3D 声音设置**，并输入**0.1**有关**Doppler 级别**。
  * 设置**卷卷绕**到**对数卷绕**。
  * 设置**最大距离**到**20**。
* 在中**脚本**文件夹中，创建一个名为脚本**SphereSounds**。
* 拖放到**SphereSounds**到**Sphere1**并**Sphere2**层次结构中的对象。
* 打开**SphereSounds** Visual Studio 中更新以下代码，并**全部保存**。

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* 保存脚本，并返回到 Unity。
* 导出、 生成和应用部署到你 HoloLens。
* 移动更接近和最荒谬不过阶段并打开端端，若要听到的声音更改。

## <a name="chapter-6---spatial-mapping"></a>第 6 章-空间映射

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

现在，我们将使用[空间映射](spatial-mapping.md)在现实世界中的实际对象上放置游戏板。

### <a name="objectives"></a>目标

* 将引入虚拟世界的现实世界。
* 将放置在全息其中它们对你最重要。

### <a name="instructions"></a>说明

* 在 Unity 中，单击**全息**项目面板中的文件夹。
* 拖动**空间映射**到的根目录的资产**层次结构**。
* 单击**空间映射**层次结构中的对象。
* 在中**检查器面板**，更改下列属性：
  * 检查**绘制 Visual 网格**框。
  * 找到**绘制材料**并单击右侧的圆形。 类型"**线框**"顶部搜索字段中。 单击该结果，然后关闭窗口。 时执行此操作时，应获取绘制材料的值设置为透明框架。
* 导出、 生成和应用部署到你 HoloLens。
* 应用运行时，线框网格将覆盖在现实世界。
* 观看如何滚动球体将不会出现该阶段，注销再到在地板上 ！

现在我们将向您展示如何将 OrigamiCollection 移动到新位置：

* 在中**脚本**文件夹中，创建一个名为脚本**TapToPlaceParent**。
* 在中**层次结构**，展开**OrigamiCollection** ，然后选择**阶段**对象。
* 拖动**TapToPlaceParent**到阶段对象上的脚本。
* 打开**TapToPlaceParent**脚本在 Visual Studio 中，并将其更新为如下：

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* 导出、 生成和部署应用程序。
* 现在您现在应能够将游戏放在特定位置，通过它在观望，使用选择手势然后将移至新位置，并再次使用选择的手势。

## <a name="chapter-7---holographic-fun"></a>第 7 章 — Holographic 乐趣

### <a name="objectives"></a>目标

* 显示进行 holographic underworld 的入口。

### <a name="instructions"></a>说明

现在，我们将向您展示如何以发现 holographic underworld:

* 从**全息**项目面板中的文件夹：
  * 拖动**Underworld**到层次结构的子级**OrigamiCollection**。
* 在中**脚本**文件夹中，创建一个名为脚本**HitTarget**。
* 在中**层次结构**，展开**OrigamiCollection**。
* 展开**阶段**对象，并选择**目标**对象 （蓝色风扇）。
* 拖动**HitTarget**拖动到脚本**目标**对象。
* 打开**HitTarget**脚本在 Visual Studio 中，并将其更新为如下：

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* 在 Unity 中，选择**目标**对象。
* 两个公共属性即会显示在**命中目标**组件和到我们的场景中的引用对象的需求：
  * 拖动**Underworld**从**层次结构**到面板**Underworld**属性**命中目标**组件。
  * 拖动**阶段**从**层次结构**到面板**隐藏的对象**属性**命中目标**组件。
* 导出、 生成和部署应用程序。
* 将 Origami 集合放在地板上，然后使用选择手势进行删除球体。
* 当球达到目标 （蓝色风扇） 时，将发生爆炸式增长。 集合将被隐藏，到 underworld 漏洞会出现。

## <a name="the-end"></a>结束

就是本教程结束 ！

介绍了：

* 如何在 Unity 中创建全息版应用。
* 如何使提供注视、 手势、 语音、 声音、 使用和空间的映射。
* 如何生成和使用 Visual Studio 部署应用。

现已准备好开始创建您自己 holographic 体验 ！

## <a name="see-also"></a>请参阅

* [MR 基础知识 101E:使用模拟器的完整项目](holograms-101e.md)
* [Gaze](gaze.md)
* [手势](gestures.md)
* [语音输入](voice-input.md)
* [空间声音](spatial-sound.md)
* [空间映射](spatial-mapping.md)
