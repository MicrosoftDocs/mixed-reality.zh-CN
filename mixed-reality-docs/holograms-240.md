---
title: MR 共享 240-多个 HoloLens 设备
description: 遵循此编码使用 Unity、 Visual Studio 和 HoloLens 若要了解详细信息的共享全息演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 共享、 网络、 学院、 教程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592263"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>共享 240 MR:多个 HoloLens 设备

全息提供我们的世界中存在剩余到位，随着我们空间中。 HoloLens 使用各种就地保留全息[坐标系](coordinate-systems.md)来跟踪的位置和方向的对象。 当我们共享这些设备之间的坐标系统时，我们可以创建可用于共享 holographic 世界中的共享的体验。

在本教程中，我们将：

* 设置共享体验的网络。
* 在 HoloLens 设备之间共享全息。
* 发现我们共享 holographic 世界中的其他人员。
* 创建共享的交互式体验，可在其中面向其他玩家-并启动它们的炮弹 ！

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>共享 240 MR:多个 HoloLens 设备</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)具有 Internet 访问权限。
* 至少两个 HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
  * 如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。
  * 如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。
  * 如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。
* 取消存档到您的桌面或其他轻松地访问位置的文件。 保留文件夹名称作为**SharedHolograms**。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)。

## <a name="chapter-1---holo-world"></a>第 1 章-Holo 世界

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

在本章中，我们将安装我们的第一个 Unity 项目并单步执行生成和部署过程。

### <a name="objectives"></a>目标

* 设置 Unity 开发全息版的应用程序。
* 请参阅你全息图 ！

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择**打开**。
* 输入与位置**SharedHolograms**你之前未存档的文件夹。
* 选择**项目名称**然后单击**选择文件夹**。
* 在中**层次结构**，右键单击**Main Camera** ，然后选择**删除**。
* 在中**HoloToolkit 共享-240/预设/相机**文件夹中，找到**Main Camera**预设。
* 拖放到**Main Camera**成**层次结构**。
* 在中**层次结构**，单击**创建**并**创建空白**。
* 右键单击新**GameObject** ，然后选择**重命名**。
* 重命名为 GameObject **HologramCollection**。
* 选择**HologramCollection**对象中**层次结构**。
* 在中**Inspector**设置**转换位置**到：**X:0，Y:-0.25，Z:2**.
* 在中**全息**中的文件夹**项目面板**，找到**EnergyHub**资产。
* 拖放到**EnergyHub**对象从**项目面板**到**层次结构**作为**子 HologramCollection**。
* 选择**文件 > 另存为场景...**
* 命名该场景**SharedHolograms**然后单击**保存**。
* 按**播放**在 Unity 中以预览你全息按钮。
* 按**播放**停止预览模式下的第二个时机。

**导出到 Visual Studio 从 Unity 项目**
* 在 Unity 中，选择**文件 > 生成设置**。
* 单击**添加打开场景**添加场景。
* 选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。
* 设置**SDK**到**通用 10**。
* 设置**目标设备**到**HoloLens**并**UWP 生成类型**到**D3D**。
* 检查**UnityC#项目**。
* 单击“生成” 。
* 在文件资源管理器窗口中显示，创建**新文件夹**名为"应用"。
* 单击一下**应用**文件夹。
* 按**选择文件夹**。
* Unity 完成操作后，将出现一个文件资源管理器窗口。
* 打开**应用**文件夹。
* 打开**SharedHolograms.sln**以启动 Visual Studio。
* 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X86**。
* 单击本地计算机旁边的下拉箭头，然后选择**远程设备**。
    * 设置**地址**的名称或 IP 地址在 HoloLens。 如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**问 Cortana 或 **"你好，小娜，我的 IP 地址是什么？"**
    * 将保留**身份验证模式**设置为**通用**。
    * 单击**选择**
* 单击**调试 > 启动不调试**或按**Ctrl + F5**。 如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
* 在你 HoloLens 上并查找 EnergyHub 全息图。

## <a name="chapter-2---interaction"></a>第 2 章-交互

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

在本章中，我们将与我们全息中进行交互。 首先，我们将添加要可视化的游标我们[注视](gaze.md)。 然后，我们将添加[手势](gestures.md)和用我们一只手我们全息置于空间。

### <a name="objectives"></a>目标

* 使用输入来控制游标的视线移动。
* 使用笔势输入与全息进行交互。

### <a name="instructions"></a>说明

**Gaze**
* 在中**层次结构面板**选择**HologramCollection**对象。
* 在中**检查器面板**单击**添加组件**按钮。
* 在菜单中，在搜索框中键入**注视 Manager**。 选择搜索结果。
* 在中**HoloToolkit 共享 240\Prefabs\Input**文件夹中，找到**光标**资产。
* 拖放到**游标**拖动到资产**层次结构**。

**手势**
* 在中**层次结构面板**选择**HologramCollection**对象。
* 单击**添加组件**并键入**笔势管理器**搜索字段中。 选择搜索结果。
* 在中**层次结构面板**，展开**HologramCollection**。
* 选择子**EnergyHub**对象。
* 在中**检查器面板**单击**添加组件**按钮。
* 在菜单中，在搜索框中键入**全息图放置**。 选择搜索结果。
* 通过选择保存场景**文件 > 保存场景**。

**部署和享受**
* 生成并部署到你 HoloLens，使用上一章中的说明。
* 一旦在 HoloLens 上启动该应用程序，移动您，注意 EnergyHub 如何遵循你的视线移动。
* 请注意，光标出现时您展示全息图，及时不观望在一张全息图将更改为点光的方式。
* 执行以无线方式点击以放置全息图。 在这次是在我们的项目，您可以仅将 hologram 一次 （重新部署再试一次）。

## <a name="chapter-3---shared-coordinates"></a>第 3 章 — 共享坐标

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

它很有趣，请参阅并全息，与之交互，但让我们进一步。 我们将设置我们第一次的共享体验的每个人都可以同时看到一张全息图。

### <a name="objectives"></a>目标

* 设置共享体验的网络。
* 建立的常见的参考点。
* 跨设备共享坐标系统。
* 每个人都看到同一个全息图 ！

>[!NOTE]
>**InternetClientServer**并**PrivateNetworkClientServer**功能必须声明应用程序无法连接到共享服务器。 这是为您已在全息 240 但记住这一点对于您自己的项目。
>1. 在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置
>2. 单击"Windows 应用商店"选项卡
>3. 在"发布设置 > 功能"部分中，检查**InternetClientServer**功能并**PrivateNetworkClientServer**功能

### <a name="instructions"></a>说明

* 在中**项目面板**导航到**HoloToolkit 共享 240\Prefabs\Sharing**文件夹。
* 拖放到**共享**到 prefab**层次结构面板**。

接下来我们需要启动该共享服务。 仅**一台 PC**中的共享体验需要执行此步骤。
* 在 Unity-顶部手工菜单中选择**HoloToolkit 共享 240 菜单**。
* 选择**启动共享服务**下拉列表中的项。
* 检查**专用网络**选项，然后单击**允许访问**防火墙提示符出现时。
* 请记下共享服务控制台窗口中显示的 IPv4 地址。 这是该服务正在运行的计算机相同的 IP。

说明的其余部分并遵照**所有 Pc** ，将加入的共享的体验。
* 在中**层次结构**，选择**共享**对象。
* 中**Inspector**，然后在**共享阶段**组件，更改**服务器地址**从运行 SharingService.exe 的计算机的 IPv4 地址 localhost。
* 在中**层次结构**选择**HologramCollection**对象。
* 在中**Inspector**单击**添加组件**按钮。
* 在搜索框中，键入**导入导出定位点管理器**。 选择搜索结果。
* 在中**项目面板**导航到**脚本**文件夹。
* 双击**HologramPlacement**脚本以在 Visual Studio 中打开它。
* 将下面的代码替换为内容。

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

* 返回在 Unity 中，选择**HologramCollection**中**层次结构面板**。
* 在中**检查器面板**单击**添加组件**按钮。
* 在菜单中，在搜索框中键入**应用程序状态管理器**。 选择搜索结果。

**部署和享受**
* 构建于 HoloLens 设备的项目。
* 将指定一个 HoloLens 将部署到第一个。 将需要等待要上传到该服务之前可以放置 EnergyHub 的定位点 (这可能需要大约 30-60 秒)。 上传完成之前，将忽略点击手势。
* 已放 EnergyHub 后，其位置将上载到服务，然后将部署到所有其他 HoloLens 设备。
* 当新 HoloLens 首次加入会话时，EnergyHub 的位置可能不正确的设备上。 但是，一旦已从服务下载的定位点和 EnergyHub 位置，EnergyHub 应跳转到新的共享位置。 如果此情况发生在大约 30-60 秒，引导到原始 HoloLens 所在设置定位点来收集多个环境线索时。 如果该位置仍不会锁定，重新部署到设备。
* 当设备已全部准备好并运行该应用程序，查找 EnergyHub。 可以在所有达成全息图的位置和方向面向文本？

## <a name="chapter-4---discovery"></a>第 4 章-发现

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

现在，每个人都可以看到相同的 hologram ！ 现在让我们查看其他连接到共享 holographic 世界。 在本章中，我们将获取的头位置和相同的共享会话中的所有其他 HoloLens 设备旋转。

### <a name="objectives"></a>目标

* 发现彼此共享我们的经验。
* 选择并共享播放机头像。
* 附加所有人的头旁边的播放机虚拟形象。

### <a name="instructions"></a>说明

* 在中**项目面板**导航到**全息**文件夹。
* 拖放到**PlayerAvatarStore**成**层次结构**。
* 在中**项目面板**导航到**脚本**文件夹。
* 双击**AvatarSelector**脚本以在 Visual Studio 中打开它。
* 将下面的代码替换为内容。

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

* 在中**层次结构**选择**HologramCollection**对象。
* 在中**Inspector**单击**添加组件**。
* 在搜索框中，键入**本地播放机管理器**。 选择搜索结果。
* 在中**层次结构**选择**HologramCollection**对象。
* 在中**Inspector**单击**添加组件**。
* 在搜索框中，键入**远程播放机管理器**。 选择搜索结果。
* 打开**HologramPlacement** Visual Studio 中的脚本。
* 将下面的代码替换为内容。

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

* 打开**AppStateManager** Visual Studio 中的脚本。
* 将下面的代码替换为内容。

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

**部署和享受**
* 生成并部署到 HoloLens 设备项目。
* 当您听到声音执行 ping 操作时，找到头像选择菜单并选择与-敲击手势头像。
* 如果您不希望在任何全息，浅光标周围的点将变为不同的颜色时你 HoloLens 与服务进行通信： 初始化 （深紫色）、 下载导入/导出位置数据 （黄色） 的定位点 （绿色）上传的定位点 （蓝色）。 如果你浅光标周围的点为默认颜色 （淡紫色），你已准备好在你的会话中与其他玩家进行交互 ！
* 查看其他人连接到你的空间-会有一个 holographic 机器人浮动上面其即时权限提升和模拟其头动作 ！

## <a name="chapter-5---placement"></a>第 5 章-放置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

在本章中，我们将能够在实际的图面上放置的定位点。 我们将使用共享的坐标中的中间点之间连接的共享体验到的每个人都放置该定位点。

### <a name="objectives"></a>目标

* 将全息放置在基于玩家的头位置空间映射。

### <a name="instructions"></a>说明

* 在中**项目面板**导航到**全息**文件夹。
* 拖放到**CustomSpatialMapping**拖动到 prefab**层次结构**。
* 在中**项目面板**导航到**脚本**文件夹。
* 双击**AppStateManager**脚本以在 Visual Studio 中打开它。
* 将下面的代码替换为内容。

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

* 在中**项目面板**导航到**脚本**文件夹。
* 双击**HologramPlacement**脚本以在 Visual Studio 中打开它。
* 将下面的代码替换为内容。

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

**部署和享受**
* 生成并部署到 HoloLens 设备项目。
* 应用程序准备就绪后，在一个圆周中构建并请注意 EnergyHub 的每个用户中心中的显示方式。
* 点击放置 EnergyHub。
* 请尝试将全息图移动到新位置的语音命令重置目标以选取 EnergyHub 并作为一个组协同工作。

## <a name="chapter-6---real-world-physics"></a>第 6 章-实际的物理引擎

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

在这一章中我们将添加全息弹实际的图面。 观看您与项目由你和你的朋友启动填满的空间 ！

### <a name="objectives"></a>目标

* 启动炮弹弹实际的图面。
* 共享敌人发射的炮弹，因此其他播放机可以查看它们。

### <a name="instructions"></a>说明

* 在中**层次结构**选择**HologramCollection**对象。
* 在中**Inspector**单击**添加组件**。
* 在搜索框中，键入**Projectile 启动器**。 选择搜索结果。

**部署和享受**
* 生成并部署到 HoloLens 设备。
* 当所有设备上运行应用时，执行以无线方式点击以启动 projectile 在现实世界图面。
* 请参阅与其他播放机的虚拟形象在 projectile 冲突时会发生什么情况 ！

## <a name="chapter-7---grand-finale"></a>第 7 章 — 凯旋

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

在本章中，我们将发现一个门户，它只能发现与协作。

### <a name="objectives"></a>目标

* 协同工作以启动在定位点来发现机密门户足够炮弹 ！

### <a name="instructions"></a>说明

* 在中**项目面板**导航到**全息**文件夹。
* 拖放到**Underworld**作为资产**HologramCollection 子**。
* 与**HologramCollection**处于选中状态，单击**添加组件**按钮**Inspector**。
* 在菜单中，在搜索框中键入**ExplodeTarget**。 选择搜索结果。
* 与**HologramCollection**选定，从**层次结构**拖动**EnergyHub**对象传递给**目标**字段中**Inspector**。
* 与**HologramCollection**选定，从**层次结构**拖动**Underworld**对象传递给**Underworld** 字段**检查器**。

**部署和享受**
* 生成并部署到 HoloLens 设备。
* 当应用启动时，共同协作以启动在 EnergyHub 炮弹。
* Underworld 出现时，启动炮弹在 underworld 机器人 （命中三倍的额外有趣机器人）。
