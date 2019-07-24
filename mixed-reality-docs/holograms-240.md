---
title: MR 共享 240-多个 HoloLens 设备
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 了解共享全息影像的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 共享, 网络, 学院, 教程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522331"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>尊敬的共享 240:多个 HoloLens 设备

随着我们在空间中的发展, 我们将在世界各地提供全息影像。 通过使用各种[坐标系统](coordinate-systems.md)跟踪对象的位置和方向, HoloLens 保留了全息影像。 当我们在设备之间共享这些坐标系统时, 我们可以创建共享体验, 使我们能够参与共享全息环境。

在本教程中, 我们将:

* 为共享体验设置网络。
* 跨 HoloLens 设备共享全息影像。
* 了解我们的共享全息领域中的其他人员。
* 创建可面向其他玩家的共享交互式体验, 并在其上启动炮弹!

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>尊敬的共享 240:多个 HoloLens 设备</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用随 Internet 访问权限安装的正确[工具](install-the-tools.md)配置的 WINDOWS 10 电脑。
* 至少[为开发配置了](using-visual-studio.md#enabling-developer-mode)两个 HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)。 需要 Unity 2017.2 或更高版本。
  * 如果仍需要 Unity 5.6 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。
  * 如果仍需要 Unity 5.5 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。
  * 如果仍需要 Unity 5.4 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。
* 取消将文件存档到桌面或其他易于访问的位置。 将文件夹名称保留为**SharedHolograms**。

>[!NOTE]
>如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)找到。

## <a name="chapter-1---holo-world"></a>第1章-Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

在本章中, 我们将设置第一个 Unity 项目, 并逐步完成生成和部署过程。

### <a name="objectives"></a>目标

* 安装 Unity 以开发全息版应用。
* 查看全息图!

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择 "**打开**"。
* 输入位置作为之前 unarchived 的**SharedHolograms**文件夹。
* 选择 "**项目名称**", 然后单击 "**选择文件夹**"。
* 在**层次结构**中, 右键单击**主相机**, 然后选择 "**删除**"。
* 在**HoloToolkit/prototyping/相机**文件夹中, 找到**摄像机的主**prefab。
* 将**主相机**拖放到**层次结构**中。
* 在**层次结构**中, 单击 "**创建**" 并**创建空**。
* 右键单击新的 " **GameObject** ", 然后选择 "**重命名**"。
* 将 GameObject 重命名为**HologramCollection**。
* 选择**层次结构**中的**HologramCollection**对象。
* 在**检查器**中, 将**转换位置**设置为:**X-BLADE0, Y:-0.25, Z:2**。
* 在 "**项目" 面板**的 "**全息影像**" 文件夹中, 找到 " **EnergyHub**资产"。
* 将**EnergyHub**对象从 "**项目" 面板**中拖放到**层次结构**中, 将其作为**HologramCollection 的子项**。
* 选择**文件 > 将场景另存为 ...**
* 将场景命名为**SharedHolograms** , 然后单击 "**保存**"。
* 按下 Unity 中的 "**播放**" 按钮, 预览全息影像。
* 按第二次**播放**以停止预览模式。

**将项目从 Unity 导出到 Visual Studio**
* 在 Unity 中, 选择 "**文件 > 生成设置**"。
* 单击 "**添加打开的场景**" 添加场景。
* 选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"。
* 将**SDK**设置为**通用 10**。
* 将**目标设备**设置为**HoloLens** , 将 " **UWP" 生成类型**设置为 " **D3D**"。
* 检查**Unity C#项目**。
* 单击“生成” 。
* 在出现的 "文件资源管理器" 窗口中, 创建一个名为 "App" 的**新文件夹**。
* 单击**应用**文件夹。
* 按 "**选择文件夹**"。
* 当 Unity 完成后, 将显示文件资源管理器窗口。
* 打开**应用程序**文件夹。
* 打开**SharedHolograms**以启动 Visual Studio。
* 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **X86**"。
* 单击 "本地计算机" 旁边的下拉箭头, 然后选择 "**远程设备**"。
    * 将**地址**设置为 HoloLens 的名称或 IP 地址。 如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项** **" 或 "我的 IP 地址是什么？"。**
    * 将**身份验证模式**设置为 "**通用**"。
    * 单击 "**选择**"
* 单击 "**调试" > "开始但不调试**" 或按**Ctrl + F5**。 如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
* 放在你的 HoloLens 上, 找到 EnergyHub 全息图。

## <a name="chapter-2---interaction"></a>第2章-交互

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

在本章中, 我们将与全息影像交互。 首先, 我们将添加一个光标以直观显示[注视](gaze.md)。 接下来, 我们将添加[手势](gestures.md), 并使用我们的手在空间中放置全息影像。

### <a name="objectives"></a>目标

* 使用 "注视输入" 控制光标。
* 使用手势输入与全息影像交互。

### <a name="instructions"></a>说明

**凝视**
* 在 "**层次结构" 面板**中, 选择 " **HologramCollection** " 对象。
* 在**检查器面板**中, 单击 "**添加组件**" 按钮。
* 在菜单中, 在 "搜索" 框中键入 "**注视经理**"。 选择搜索结果。
* 在**HoloToolkit-Sharing-240\Prefabs\Input**文件夹中, 找到**光标**资产。
* 将**光标**资产拖放到**层次结构**中。

**姿态**
* 在 "**层次结构" 面板**中, 选择 " **HologramCollection** " 对象。
* 单击 "**添加组件**", 并在搜索字段中键入**笔势管理器**。 选择搜索结果。
* 在 "**层次结构" 面板**中, 展开 " **HologramCollection**"。
* 选择 "子**EnergyHub** " 对象。
* 在**检查器面板**中, 单击 "**添加组件**" 按钮。
* 在 "搜索 **" 框中**, 键入 "搜索" 对话框。 选择搜索结果。
* 通过选择 "文件" **> 保存**场景来保存场景。

**部署和体验**
* 使用上一章中的说明生成并部署到 HoloLens。
* 在您的 HoloLens 上启动该应用程序后, 请四处移动您的头, 注意 EnergyHub 如何进入您的注视。
* 请注意, 在您看出全息影像时光标如何显示, 当不 gazing 在全息图上时, 也会改变点光。
* 执行轻按下以放置全息影像。 此时, 我们的项目中只能放置一次全息图一次 (重新部署后重试)。

## <a name="chapter-3---shared-coordinates"></a>第3章-共享坐标

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

与全息影像进行查看和交互很有趣, 但让我们进一步了解一下。 我们将设置我们的第一个共享体验-每个人都可以同时查看。

### <a name="objectives"></a>目标

* 为共享体验设置网络。
* 建立一个公共参考点。
* 跨设备共享坐标系统。
* 所有人都看到同一个全息图!

>[!NOTE]
>必须为应用声明**InternetClientServer**和**PrivateNetworkClientServer**功能才能连接到共享服务器。 此操作已在全息影像240中完成, 但请记住你自己的项目。
>1. 在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置
>2. 单击 "Windows 应用商店" 选项卡
>3. 在 "发布设置 > 功能" 部分中, 查看**InternetClientServer**功能和**PrivateNetworkClientServer**功能

### <a name="instructions"></a>说明

* 在 "**项目" 面板**中, 导航到**HoloToolkit-Sharing-240\Prefabs\Sharing**文件夹。
* 将**共享**prefab 拖放到**层次结构面板**。

接下来, 我们需要启动共享服务。 共享体验中只有**一台 PC**需要执行此步骤。
* 在 Unity 中-在顶部菜单中, 选择 " **HoloToolkit-240" 菜单**。
* 在下拉栏中选择 "**启动共享服务**" 项。
* 选中 "**专用网络**" 选项, 并在出现防火墙提示时单击 "**允许访问**"。
* 记下 "共享服务控制台" 窗口中显示的 IPv4 地址。 此 IP 与运行服务的计算机的 IP 相同。

按照将加入共享体验的**所有 pc**上的其余说明进行操作。
* 在**层次结构**中, 选择**共享**对象。
* 在**检查器**的**共享阶段**组件上, 将**服务器地址**从 "localhost" 更改为运行 SharingService 的计算机的 IPv4 地址。
* 在**层次结构**中, 选择 " **HologramCollection** " 对象。
* 在**检查器**中, 单击 "**添加组件**" 按钮。
* 在搜索框中, 键入 "**导入导出定位点管理器**"。 选择搜索结果。
* 在 "**项目" 面板**中, 导航到**Scripts**文件夹。
* 双击**HologramPlacement**脚本, 在 Visual Studio 中将其打开。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 返回 Unity, 在 "**层次结构" 面板**中选择 " **HologramCollection** "。
* 在**检查器面板**中, 单击 "**添加组件**" 按钮。
* 在菜单中, 在 "搜索" 框中键入 "**应用状态管理器**"。 选择搜索结果。

**部署和体验**
* 生成适用于 HoloLens 设备的项目。
* 指定要首先部署到的一个 HoloLens。 你将需要等待定位点上载到服务, 然后才能放置 EnergyHub (这可能需要大约30-60 秒)。 完成上传之前, 将忽略攻丝手势。
* 放置 EnergyHub 后, 其位置将被上传到服务, 然后你可以将其部署到所有其他 HoloLens 设备。
* 新的 HoloLens 首次加入会话时, 该设备上的 EnergyHub 位置可能不正确。 但是, 一旦从服务下载了定位点和 EnergyHub 位置, EnergyHub 应跳转到新的共享位置。 如果这不是在约30-60 秒内发生的, 则在设置定位点时转到原始 HoloLens 的位置, 以收集更多的环境线索。 如果位置仍未锁定, 请重新部署到设备。
* 当设备全部准备就绪并运行应用程序时, 请查找 EnergyHub。 你是否完全同意了全息图的位置以及文本的方向:

## <a name="chapter-4---discovery"></a>第4章-发现

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

现在, 所有人都可以看到相同的全息图! 现在, 让我们看看与共享全息环境连接的其他人。 在本章中, 我们将抓住同一共享会话中所有其他 HoloLens 设备的打印头位置和旋转。

### <a name="objectives"></a>目标

* 了解共享体验。
* 选择并共享播放机头像。
* 将播放机头像附加到每个人的标题旁边。

### <a name="instructions"></a>说明

* 在 "**项目" 面板**中, 导航到 "**全息影像**" 文件夹。
* 将**PlayerAvatarStore**拖放到**层次结构**中。
* 在 "**项目" 面板**中, 导航到**Scripts**文件夹。
* 双击**AvatarSelector**脚本, 在 Visual Studio 中将其打开。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* 在**层次结构**中, 选择 " **HologramCollection** " 对象。
* 在**检查器**中单击 "**添加组件**"。
* 在搜索框中, 键入 "**本地播放机管理器**"。 选择搜索结果。
* 在**层次结构**中, 选择 " **HologramCollection** " 对象。
* 在**检查器**中单击 "**添加组件**"。
* 在搜索框中, 键入 "**远程播放机管理器**"。 选择搜索结果。
* 在 Visual Studio 中打开**HologramPlacement**脚本。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 在 Visual Studio 中打开**AppStateManager**脚本。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**部署和体验**
* 生成项目并将其部署到 HoloLens 设备。
* 听到 ping 声音时, 请找到头像选择菜单, 并选择一个具有 "轻攻器" 手势的头像。
* 如果你不想查看任何全息影像, 则当你的 HoloLens 与服务进行通信时, 光标周围的点亮将变为不同的颜色: 正在初始化 (深紫色), 下载定位点数据 (绿色)、导入/导出位置数据 (黄色)、正在上载定位点 (蓝色)。 如果光标周围的点亮是默认颜色 (浅紫色), 则已准备好与会话中的其他玩家交互!
* 查看与你的空间连接的其他人员-将有一个全息机器人浮在其肩上并模拟其头运动!

## <a name="chapter-5---placement"></a>第5章-位置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

在本章中, 我们将定位标记, 使其能够放置在实际的表面上。 我们将使用共享坐标将该定位点置于连接到共享体验的每个用户之间的中间点。

### <a name="objectives"></a>目标

* 根据玩家的头位置, 将全息影像置于空间地图上。

### <a name="instructions"></a>说明

* 在 "**项目" 面板**中, 导航到 "**全息影像**" 文件夹。
* 将**CustomSpatialMapping** prefab 拖放到**层次结构**中。
* 在 "**项目" 面板**中, 导航到**Scripts**文件夹。
* 双击**AppStateManager**脚本, 在 Visual Studio 中将其打开。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* 在 "**项目" 面板**中, 导航到**Scripts**文件夹。
* 双击**HologramPlacement**脚本, 在 Visual Studio 中将其打开。
* 将内容替换为以下代码。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**部署和体验**
* 生成项目并将其部署到 HoloLens 设备。
* 当应用程序准备就绪时, 请将其放在一个圆圈上, 并注意 EnergyHub 如何出现在每个人的中心。
* 点击以放置 EnergyHub。
* 尝试使用语音命令 "重置目标" 来选择 EnergyHub 备份, 并以组的形式协同工作, 以便将全息图移动到新位置。

## <a name="chapter-6---real-world-physics"></a>第6章-真实物理

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

在本章中, 我们将添加从实际表面弹跳的全息影像。 观看您和您的朋友所启动的项目的空间。

### <a name="objectives"></a>目标

* 启动炮弹, 从实际表面弹跳。
* 共享炮弹, 使其他玩家可以看到它们。

### <a name="instructions"></a>说明

* 在**层次结构**中, 选择 " **HologramCollection** " 对象。
* 在**检查器**中单击 "**添加组件**"。
* 在搜索框中, 键入 " **Projectile 启动**程序"。 选择搜索结果。

**部署和体验**
* 生成并部署到 HoloLens 设备。
* 当应用程序在所有设备上运行时, 请在实际的表面上执行轻点击以启动 projectile。
* 了解 projectile 与其他玩家的头像发生冲突时会发生什么情况!

## <a name="chapter-7---grand-finale"></a>第7章-总计 Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

在本章中, 我们将发现一个只能通过协作发现的门户。

### <a name="objectives"></a>目标

* 协同工作, 在定位点上启动足够的炮弹来发现机密门户!

### <a name="instructions"></a>说明

* 在 "**项目" 面板**中, 导航到 "**全息影像**" 文件夹。
* 将**Underworld**资产拖放为 HologramCollection 的**子项**。
* 选择**HologramCollection**后, 在**检查器**中单击 "**添加组件**" 按钮。
* 在菜单中, 在 "搜索" 框中键入**ExplodeTarget**。 选择搜索结果。
* 选择**HologramCollection**后, 从**层次结构**中,**将 EnergyHub**对象拖到**检查器**中的**目标**字段。
* 选择**HologramCollection**后, 从**层次结构**中,**将 Underworld**对象拖到**检查器**中的**Underworld**字段。

**部署和体验**
* 生成并部署到 HoloLens 设备。
* 当应用程序启动时, 在 EnergyHub 上协作以启动炮弹。
* 显示 underworld 时, 启动炮弹 at underworld 机器人 (单击机器人三次, 以获得更多乐趣)。
