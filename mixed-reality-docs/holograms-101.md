---
title: MR 基本 101-设备的完整项目
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 了解 Windows Mixed Reality 的基本知识。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实, Windows Mixed Reality, HoloLens, 全息影像, 学院, 教程
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524024"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>MR 要点 101:完成具有设备的项目

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

本教程将引导你完成 Unity 中内置的一个完整项目, 该项目演示了 HoloLens 上核心 Windows Mixed Reality 功能, 包括[注视](gaze.md)、[手势](gestures.md)、[语音输入](voice-input.md)、[空间音效](spatial-sound.md)和[空间映射](spatial-mapping.md).

教程大约需要1小时才能完成。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 要点 101:完成具有设备的项目</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>系统必备

* 配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。
* [为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)。 需要 Unity 2017.2 或更高版本。
  * 如果仍需要 Unity 5.6 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。
  * 如果仍需要 Unity 5.5 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。
  * 如果仍需要 Unity 5.4 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。
* 取消将文件存档到桌面或其他易于访问的位置。 将文件夹名称保留为**日式折纸**。

>[!NOTE]
>如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)找到。

## <a name="chapter-1---holo-world"></a>第1章-"Holo" 世界

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

在本章中, 我们将设置第一个 Unity 项目, 并逐步完成生成和部署过程。

### <a name="objectives"></a>目标

* 为全息版开发设置 Unity。
* 制作全息影像。
* 查看您创建的全息影像。

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择 "**打开**"。
* 输入 "位置" 作为以前未存档的**日式折纸**文件夹。
* 选择 "**日式折纸**" 并单击 "**选择文件夹**"。
* 由于**日式折纸**项目不包含场景, 因此请使用将空的默认场景保存到新文件中:文件 / **另存为**。
* 将新场景命名为**日式折纸**, 并按 "**保存**" 按钮。

#### <a name="setup-the-main-virtual-camera"></a>设置主虚拟摄像机

* 在 "**层次结构" 面板**中, 选择 "**主相机**"。
* **检查器**将其转换位置设置为**0, 0, 0**。
* 找到 "**清除标志**" 属性, 然后将下拉列表中的**Skybox**更改为**纯色**。
* 单击 "**背景**" 字段打开颜色选取器。
* 将**R、G、B 和 A**设置为**0**。

#### <a name="setup-the-scene"></a>设置场景

* 在 "**层次结构" 面板**中, 单击 "**创建**" 并**创建空**。
* 右键单击新的 " **GameObject** ", 然后选择 "重命名"。 将 GameObject 重命名为**OrigamiCollection**。
* 从 " 项目" 面板 (展开 "资产" 并选择全息影像, 或双击 "项目" 面板中的 "全息影像" 文件夹):
  * 将**阶段**拖到层次结构中, 使其成为**OrigamiCollection**的子级。
  * 将**Sphere1**拖到层次结构中, 使其成为**OrigamiCollection**的子元素。
  * 将**Sphere2**拖到层次结构中, 使其成为**OrigamiCollection**的子元素。
* 右键单击 "**层次结构" 面板**中的**方向浅**对象, 然后选择 "**删除**"。
* 从 "**全息影像**" 文件夹中, 将**灯光**拖到**层次结构面板**的根。
* 在**层次结构**中, 选择 " **OrigamiCollection**"。
* 在**检查器**中, 将转换位置设置为**0、-0.5、2.0**。
* 按下 Unity 中的 "**播放**" 按钮, 预览全息影像。
* 预览窗口中应会显示日式折纸对象。
* 按第二次**播放**以停止预览模式。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>将项目从 Unity 导出到 Visual Studio

* 在 Unity 中, 选择 "**文件 > 生成设置**"。
* 选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"。
* 将**SDK**设置为**通用 10** , 将**类型**设置为**D3D**。
* 检查**Unity C#项目**。
* 单击 "**添加打开的场景**" 添加场景。
* 单击“生成” 。
* 在出现的 "文件资源管理器" 窗口中, 创建一个名为 "App" 的**新文件夹**。
* 单击**应用文件夹**。
* 按 "**选择文件夹**"。
* 当 Unity 完成后, 将显示文件资源管理器窗口。
* 打开**应用程序**文件夹。
* 打开 (双击) "**日式折纸**"。
* 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **X86**"。
* 单击 "设备" 按钮旁边的箭头, 并选择 "**远程计算机**" 以通过 wi-fi 进行部署。
  * 将**地址**设置为 HoloLens 的名称或 IP 地址。 如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项** **" 或 "我的 IP 地址是什么？"。**
  * 如果 HoloLens 通过 USB 连接, 则可以选择 "**设备**通过 usb 进行部署"。
  * 将**身份验证模式**设置为 "**通用**"。
  * 单击 "**选择**"

* 单击 "**调试" > "开始但不调试**" 或按**Ctrl + F5**。 如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))。

* 现在, 日式折纸项目将生成、部署到 HoloLens, 然后运行。
* 放在你的 HoloLens 上, 并查看你的新全息影像。

## <a name="chapter-2---gaze"></a>第2章-注视

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

在本章中, 我们将介绍第三种与全息影像交互的方式--[注视](gaze.md)。

### <a name="objectives"></a>目标

* 使用全球锁定的光标直观显示注视。

### <a name="instructions"></a>说明

* 返回到 Unity 项目, 并关闭 "生成设置" 窗口 (如果它仍处于打开状态)。
* 在 "**项目" 面板**中选择**全息影像**文件夹。
* 将**光标**对象拖到**层次结构面板**中的根级别。
* 双击**光标**对象以详细查看它。
* 右键单击 "项目" 面板中的 "**脚本**" 文件夹。
* 单击 "**创建**" 子菜单。
* 选择 **C# "脚本**"。
* 将脚本命名为**WorldCursor**。 注意:该名称区分大小写。 无需添加 .cs 扩展名。
* 选择 "**层次结构" 面板**中的**光标**对象。
* 将**WorldCursor**脚本拖放到**检查器面板**。
* 双击**WorldCursor**脚本, 在 Visual Studio 中将其打开。
* 将此代码复制并粘贴到**WorldCursor.cs** , 并**保存全部**。

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

* 从**文件 > 生成设置**重新生成应用。
* 返回到以前用于部署到 HoloLens 的 Visual Studio 解决方案。
* 出现提示时, 选择 "全部重新加载"。
* 单击 "**调试-> 启动但不调试**" 或按**Ctrl + F5**。
* 现在, 浏览场景并注意光标如何与对象的形状交互。

## <a name="chapter-3---gestures"></a>第3章-手势

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

在本章中, 我们将添加对[手势](gestures.md)的支持。 当用户选择某一回形针时, 我们将使用 Unity 的物理引擎开启重心来使球落在一起。

### <a name="objectives"></a>目标

* 用选择手势控制全息影像。

### <a name="instructions"></a>说明

首先, 我们将创建一个脚本, 然后可以检测选择的手势。

* 在 "**脚本**" 文件夹中, 创建一个名为**GazeGestureManager**的脚本。
* 将**GazeGestureManager**脚本拖到层次结构中的**OrigamiCollection**对象。
* 在 Visual Studio 中打开**GazeGestureManager**脚本, 并添加以下代码:

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

* 在 Scripts 文件夹中创建另一个脚本, 这一次名为**SphereCommands**。
* 展开层次结构视图中的**OrigamiCollection**对象。
* 将**SphereCommands**脚本拖到 "层次结构" 面板中的 " **Sphere1** " 对象。
* 将**SphereCommands**脚本拖到 "层次结构" 面板中的 " **Sphere2** " 对象。
* 在 Visual Studio 中打开脚本进行编辑, 并将默认代码替换为以下代码:

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

* 导出应用, 生成应用并将其部署到 HoloLens。
* 查看球之一。
* 执行 "选择手势" 并观看以下图面上的球。

## <a name="chapter-4---voice"></a>第4章-语音

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

在本章中, 我们将添加对两个[语音命令](voice-input.md)的支持:"重置世界": 将已删除的球返回到其原始位置, 并将 "击落球" 设置为球落。

### <a name="objectives"></a>目标

* 添加始终在后台侦听的语音命令。
* 创建可响应语音命令的全息图。

### <a name="instructions"></a>说明

* 在 "**脚本**" 文件夹中, 创建一个名为**SpeechManager**的脚本。
* 将**SpeechManager**脚本拖到层次结构中的**OrigamiCollection**对象上
* 在 Visual Studio 中打开**SpeechManager**脚本。
* 将此代码复制并粘贴到**SpeechManager.cs** , 并**保存全部**内容:

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

* 在 Visual Studio 中打开**SphereCommands**脚本。
* 按如下所示更新脚本以进行读取:

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

* 导出应用, 生成应用并将其部署到 HoloLens。
* 查看某一球, 说 "**击落球**"。
* 说 "**重置世界**", 将其返回到其初始位置。

## <a name="chapter-5---spatial-sound"></a>第5章-空间音效

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

在本章中, 我们将向应用程序添加音乐, 并触发对某些操作的声音影响。 我们将使用[空间音效](spatial-sound.md)为声音指定3d 空间中的特定位置。

### <a name="objectives"></a>目标

* 收听世界上的全息影像。

### <a name="instructions"></a>说明

* 在 Unity 中从顶部菜单中选择 "**编辑 > 项目设置 > 音频**"
* 在右侧的检查器面板中, 找到 " **Spatializer" 插件**设置, 然后选择 " **MS HRTF Spatializer**"。
* 在 " 项目" 面板中, 将 "**环境**" 对象拖到 "层次结构" 面板中的**OrigamiCollection**对象上。
* 选择**OrigamiCollection**并在 "检查器" 面板中查找**音频源**组件。 更改这些属性:
  * 检查**Spatialize**属性。
  * 选中 "**在唤醒状态播放**"。
  * 通过将滑块一直拖到右侧, 将**空间混合**更改为**三维**。 移动滑块时, 值应从0更改为1。
  * 检查**循环**属性。
  * 展开 "**三维声音设置**", 然后为 " **Doppler" 级别**输入**0.1** 。
  * 将**Volume Rolloff**设置为**对数 Rolloff**。
  * 将**最大距离**设置为**20**。
* 在 "**脚本**" 文件夹中, 创建一个名为**SphereSounds**的脚本。
* 将**SphereSounds**拖放到层次结构中的**Sphere1**和**Sphere2**对象。
* 在 Visual Studio 中打开**SphereSounds** , 更新以下代码并**全部保存**。

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

* 保存该脚本并返回到 Unity。
* 导出应用, 生成应用并将其部署到 HoloLens。
* 从舞台更近和更密切地移动, 并翻到一边, 倾听声音发生变化。

## <a name="chapter-6---spatial-mapping"></a>第6章-空间映射

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

现在, 我们将使用[空间映射](spatial-mapping.md)将游戏板置于真实世界的真实对象上。

### <a name="objectives"></a>目标

* 将你的真实世界带入虚拟世界。
* 将全息影像置于最重要的位置。

### <a name="instructions"></a>说明

* 在 Unity 中, 在 "项目" 面板中单击 "**全息影像**" 文件夹。
* 将**空间映射**资产拖到**层次结构**的根。
* 单击层次结构中的**空间映射**对象。
* 在 "**检查器" 面板**中, 更改以下属性:
  * 选中 "**绘制可视网格**" 框。
  * 定位**绘图材料**, 并单击右侧的圆圈。 在顶部的搜索字段中键入 "**线框**"。 单击结果, 然后关闭窗口。 执行此操作时, 绘制材料的值应设置为线框。
* 导出应用, 生成应用并将其部署到 HoloLens。
* 当应用程序运行时, 线框网格将覆盖你的真实世界。
* 观看某个滚动球如何偏离舞台, 并观看地面!

现在, 我们将向你展示如何将 OrigamiCollection 移动到一个新位置:

* 在 "**脚本**" 文件夹中, 创建一个名为**TapToPlaceParent**的脚本。
* 在**层次结构**中, 展开 " **OrigamiCollection** ", 然后选择 "**暂存**" 对象。
* 将**TapToPlaceParent**脚本拖到 "暂存" 对象上。
* 在 Visual Studio 中打开**TapToPlaceParent**脚本, 并将其更新为以下内容:

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

* 导出、生成并部署应用。
* 现在, 您应该能够通过 gazing 将游戏置于特定位置, 使用 "选择手势", 然后移动到一个新位置, 然后再次使用 "选择手势"。

## <a name="chapter-7---holographic-fun"></a>第7章-全息娱乐

### <a name="objectives"></a>目标

* 显示全息 underworld 的入口。

### <a name="instructions"></a>说明

接下来, 我们将向您展示如何发现全息 underworld:

* 从 "项目" 面板中的 "**全息影像**" 文件夹:
  * 将**Underworld**拖到层次结构中, 使其成为**OrigamiCollection**的子元素。
* 在 "**脚本**" 文件夹中, 创建一个名为**HitTarget**的脚本。
* 在**层次结构**中, 展开 " **OrigamiCollection**"。
* 展开 "**暂存**" 对象并选择**目标**对象 (蓝色风扇)。
* 将**HitTarget**脚本拖到**目标**对象上。
* 在 Visual Studio 中打开**HitTarget**脚本, 并将其更新为以下内容:

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

* 在 Unity 中, 选择**目标**对象。
* 现在, 两个公共属性在**命中目标**组件上可见, 需要引用场景中的对象:
  * 将**Underworld**从 "**层次结构**" 面板拖到**命中目标**组件上的 " **Underworld** " 属性。
  * 从 "**层次结构**" 面板将 "**阶段**" 拖到对象上,**以隐藏** **命中目标**组件的属性。
* 导出、生成并部署应用。
* 将日式折纸收集到地面上, 然后使用 "选择手势" 创建球体放置。
* 当球到达目标 (蓝色风扇) 时, 将发生爆炸。 该集合将隐藏, 并且将显示 underworld 的孔。

## <a name="the-end"></a>结束

这就是本教程的结尾!

已学习:

* 如何在 Unity 中创建全息应用。
* 如何使用注视、手势、语音、声音和空间映射。
* 如何使用 Visual Studio 生成和部署应用。

你现在已准备好开始创建自己的全息体验!

## <a name="see-also"></a>请参阅

* [MR 基础知识 101E：使用仿真器完成项目](holograms-101e.md)
* [凝视](gaze.md)
* [手势](gestures.md)
* [语音输入](voice-input.md)
* [空间音效](spatial-sound.md)
* [空间映射](spatial-mapping.md)
