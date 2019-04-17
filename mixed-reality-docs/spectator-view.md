---
title: Spectator 视图
description: 作为一种方式的演示的外部显示器上的混合的现实体验或录制视频的混合的现实体验可视化全息从外部设备。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator 视图，iPhone、 iOS、 iPad，OpenCV、 照相机、 ARKit、 HoloLens、 混合现实、 MixedRealityToolkit，演示中，记录
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592439"
---
# <a name="spectator-view-for-hololens"></a>HoloLens spectator 视图

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>当前的重构

> [!NOTE]
>HoloLens spectator 视图是正在积极地重构。 此工作旨在合并在预览 Pro 代码库和将支持扩展到 HoloLens 2。 

若要查看当前 Spectator 视图重构的状态，请参阅 MixedRealityToolkit 和 MixedRealityToolkit Unity 存储库中的功能/spectatorView 分支：

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

和

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>概述

当戴上 HoloLens，我们经常忘记的一个人谁不包含该列不能体验我们可以神奇。 Spectator 视图允许其他人在 2D 屏幕上看到 HoloLens 用户在他们的世界中所看到的内容。
Spectator 视图 （预览版） 是快速且经济实惠方法中 HD，录制全息时 Spectator 视图 Pro 适用于的全息专业的高质量录音。

下表显示选项和其功能。 选择最适合你的视频录制需要的选项：

|                                      | Spectator 视图 （预览版） |              Spectator 查看 Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 质量                         |         全高清         |        专业质量与 （这由 DSLR）      |
| 简易照相机移动                      |            ✔            |                                             |
| 第三个人视图                    |            ✔            |                      ✔                      |
| 为流式传输到屏幕           |            ✔            |                      ✔                      |
| 可移植                             |            ✔            |                                             |
| 无线                             |            ✔            |                                             |
| 其他所需的硬件         |     iPhone （或 iPad）    | HoloLens + 远程测试机组 + 三脚架 + DSLR + PC + Unity |
| 硬件投资                  |           低           |                     高                    |
| 跨平台                       |           iOS           |                                             |
| 查看器可以进行交互                  |            ✔            |                                             |
| (UNET scripting) 所需的网络 |            ✔            |                      ✔                      |
| 运行时安装程序持续时间               |         即时         |                     慢速                    |

## <a name="spectator-view-preview"></a>Spectator 视图 （预览版）

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>用例

- 与全息 HD 中：使用 Spectator 视图 （预览版），您可以记录使用 iPhone 的混合的现实体验。 在完整 HD 中记录并将抗锯齿应用于全息和甚至阴影。 它是捕获视频全息经济高效且快速方法。
- 现场演示：Stream 实时混合的现实体验到 Apple TV 直接从 iPhone 或 iPad，延隔免费 ！
- 与来宾共享体验：允许非 HoloLens 用户体验全息直接通过其手机或平板电脑。

### <a name="current-features"></a>当前功能

- 将电话添加到该会话的自动发现的网络。
- 自动会话处理，以便用户添加到正确的会话。
- 全息，以便每个人都看到全息完全相同的位置的空间同步。
- iOS 支持 （ARKit 启用设备）。
- 多个 iOS 来宾。
- 录制的视频 + 全息 + 环境音效 + 全息图声音。
- 共享工作表，因此可以保存视频、 电子邮件发送它，或与其他支持的应用共享。


>[!NOTE] 
>Spectator 视图 （预览） 代码不能用于 Spectator 视图专业人员的版本代码。 我们建议您在需要的全息视频录制的新项目中实现它。

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>许可证

- [OpenCV-（3 子句 BSD 许可）](https://opencv.org/license.html)
- [Unity ARKit-（MIT 许可证）](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>如何设置 Spectator 视图 （预览版）

### <a name="requirements"></a>要求

- [Spectator 视图插件和必需的 OpenCV 二进制文件](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)-可在下面找到如何 Spectator 视图本机插件的详细信息。 从生成的二进制文件中，你将需要：

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Spectator 视图使用的网络发现和空间同步 Unity 网络 (UNET)。 这意味着需要在设备之间同步期间应用程序的所有交互。
- Unity 2017.2.1p2 或更高版本
- 硬件
    - HoloLens
    - 运行 Windows 10 的 Windows 电脑
    - ARKit 兼容的设备 (iPhone 6s 及更高版本 / iPad Pro 2016 及更高版本 / iPad 2017 及更高版本) 的运行 iOS 11 或更高版本
    - 与 xcode 9.2 及以上版本的 Mac
- Apple 开发人员帐户，免费或[付费](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>构建 Spectator 视图本机插件

若要生成所需的文件，请执行以下步骤： https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>项目设置

1. 准备您的场景中，确保您的场景中的所有可见 gameobjects 包含在全球根 gameobject 之下。

    ![全球根](images/SpecViewPhoneWorldRoot2.PNG)

2. 添加 SpectatorView 预设 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) 到您的场景。
3. 添加 SpectatorViewNetworking 预设 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) 到您的场景。
4. 选择 SpectatorViewNetworking gameobject 并且 SpectatorViewNetworkingManager 组件上没有可以链接启用的一些事项。 如果保持不变，左侧有必要脚本在运行时将搜索此组件。
    - 标记检测 HoloLens-> SpectatorView/Hololens/MarkerDetection
    - 标记生成 3D-> SpectatorView/IPhone/SyncMarker/3DMarker

    ![SpectatorView 网络发现](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>网络应用程序

- Spectator 视图 UNET 用于其网络和管理为你的所有主机客户端连接。
- 任何应用程序特定的数据必须进行同步，并且您使用例如 SyncVars、 NetworkTransform、 NetworkBehavior 实现。
- 有关 Unity 网络的详细信息，请访问[之多人游戏和网络](https://docs.unity3d.com/Manual/UNet.html)。 （注意：已不推荐使用 UNet;Spectator 视图基本代码的当前重构将解决此问题）

### <a name="building-for-each-platform-hololens-or-ios"></a>为每个平台 （HoloLens 或 iOS）

- 为 iOS 生成时，请确保您删除 MRTK GLTF 组件，因为这不是尚未与此平台兼容。
- SpectatorView 预设的最高级别没有名为平台切换器的组件。 选择你想要构建面向的平台。
    - 如果选择 Hololens 可以看到下方的 iPhone gameobject SpectatorView 预设可变为不活动状态中的所有 gameobjects 和 Hololens 变为活动状态下的所有 gameobject。
    - 这可能需要一段时间，具体取决于平台选择 HoloToolkit 正在项目中添加或删除。

    ![平台切换器](images/SpecViewPhoneSwitcher.PNG)

- 请确保生成因 Unity 未解决问题而使用相同的 Unity 编辑器实例 （不要之间不关闭 Unity 生成） 的应用程序的所有版本。

### <a name="running-your-app"></a>运行您的应用程序

一旦已生成并部署了应用程序的所有 iPhone 和 HoloLens 上的版本，您应能够将它们连接。

1. 确保这两种设备位于同一 Wi-fi 网络。
2. 在这两个设备，以非特定顺序上启动应用程序。 在 iPhone 上启动应用程序的过程应触发 HoloLens 照相机来启用和开始拍摄照片。
3. 立即在 iPhone 应用启动时，它会查找楼层或表等的图面。 当找不到图面时，应会看到类似于下面的标记。 此标记向 HoloLens。

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. 一旦检测到标记的 HoloLens 它应会消失，这两种设备应连接并在空间上同步。

### <a name="recording-video"></a>录制视频

1. 若要捕获和保存从 iPhone 的视频，点击按住屏幕 1 秒。 这将打开录制菜单。
2. 点击红色录制按钮，这将启动开始记录屏幕之前的倒计时。
3. 若要完成录制点击并保留在屏幕的另一个 1 秒，然后点击停止按钮。
4. 录制的视频加载后，将显示一个预览按钮 （蓝色按钮），点击观看录制的视频。
5. 打开共享表并选择保存到本机照片。

### <a name="example-scene"></a>示例场景

可在示例场景[HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>疑难解答

**在 Unity 编辑器不会连接到托管的 HoloLens 设备的会话**

- 这可能是 Windows 防火墙。
- 转到 Windows 防火墙选项。
- 允许应用或功能通过 Windows 防火墙。
- 所有实例的 Unity 编辑器中的列表刻度线，域、 专用和公共。
- 然后返回到 Windows 防火墙选项。
- 单击高级的设置。
- 单击入站的规则。
- 在 Unity 编辑器的所有实例应都具有一个绿色对勾。
- 在 Unity 编辑器的任何实例，没有一个绿色的勾选标记：
    - 双击它。
    - 在操作对话框中选择允许连接。
    - 单击“确定”。
    - 重新启动 Unity 编辑器。

**在运行时 iPhone 屏幕上显示"查找 Floor..."但不显示 AR 标记。**

- 这部 iphone 手机寻找水平面尝试指向 iPhone 照相机向 floor 或表。 这将有助于 ARKit 发现图面必要论据在空间上与 HoloLens 的同步。

**HoloLens 照相机未开启自动当 iPhone 尝试加入。**

- 请确保 HoloLens 和 iPhone 相同的 Wi-fi 网络上运行。

**正在运行的其他 Spectator 视图应用其他 hololens 时启动 Spectator 视图应用程序在移动设备上的，打开其摄像机**

- 转到 NewDeviceDiscovery 组件并更改为两个唯一值的广播密钥和广播的端口。
- 转到 SpectatorViewDiscovery 并将广播密钥和广播端口更改为另一组唯一的数字。

**HoloLens 不会使用 mac 的 Unity 编辑器进行连接。**

- 这是一个已知的问题，无法链接到的 Unity 版本。 在 iPhone 中的生成仍适用，而且连接正常。

**HoloLens 照相机将启用，但不能扫描标记。**

- 请确保生成的应用程序使用相同的 Unity 编辑器实例 （不要之间不关闭 Unity 生成） 的所有版本。 这是由于未知问题而使用 Unity。

## <a name="spectator-view-pro"></a>Spectator 查看 Pro

![Spectator 视图设置](images/spectatorview-300px.png)

使用 Spectator 视图 Pro 涉及以下四个组件：
1. 具体而言，若要启用 spectator 视图，它为基础而构建的应用[混合现实中的共享体验](shared-experiences-in-mixed-reality.md)。
2. 用户戴上使用应用的 HoloLens。
3. Spectator 视图照相机远程测试机组提供第三个人角度来看视频。
4. 运行的共享的体验应用和组合的情况下为 spectator 视图视频全息的桌面 PC。

![Spectator 视图 Pro 设置](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>用例

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*可以共享您全息版的作品使用 spectator 视图，无论他们是静止图像、 视频剪辑或实时演示。*


有很好地配合此技术的三个关键方案：

**1.照片拍摄**<br>
使用此技术，您可以捕获你全息的高分辨率图像。 这些映像可用于展示在市场营销事件的内容，将发送到潜在的客户端，或甚至提交到 Windows 应用商店应用程序。 您可以决定你想要用于捕获这些映像的照片照相机，这种情况下您可能更倾向于质量 DSLR 照相机。


![Spectator 视图 Pro 照片捕获示例](images/fall-350px.jpg)<br>
*捕获的照片示例-从而使其显示在地板由岩浆。*


**2.视频捕获**<br>
视频是最佳的故事告诉机制，用于与许多人共享全息版的应用体验。 Spectator 视图，可以选择最的适合你想要展示你的应用的照相机、 可重用功能区和帧。 它会将你的基于视频硬件上的视频质量的控件中必须可用。

![Spectator 视图 Pro 视频捕获示例](images/spectatorviewvideo.gif)<br>
*视频捕获示例-录制混合的现实的协作体验。*


**3.实时演示**<br>
Spectator 视图是实时演示的首选的方法，如照相机的位置保持不稳定或控制。 因为您可以使用高质量视频摄像机，也可以生成高质量图像适用于大屏幕。 这也是适用于流式处理在屏幕上，可能给为其启用排队等候了预先参与者的现场演示。

### <a name="comparing-video-capture-techniques"></a>比较视频捕获方法

[混合现实捕获](mixed-reality-capture.md)(MRC) 提供了视频复合的 HoloLens 用户从第一个人-的-角度看到的内容。 Spectator 视图生成从第三个人角度看，允许视频观察程序中，若要查看具有全息和戴上 HoloLens 设备的用户环境的视频。 由于你有摄像机的选择，spectator 视图还可以生成更高的分辨率和比内置 HoloLens 照相机用于 MRC 映像更好的高质量图像。 出于此原因，spectator 视图更适合用于市场营销的视频，Windows 应用商店中的应用图像或投影为受众的实时视图。

![查看 Pro spectator Microsoft 主题演讲演示文稿中使用的专业照相机](images/spectator-view-professional-red-camera-300px.jpg)<br>
*查看 Pro spectator Microsoft 主题演讲演示文稿中使用的专业照相机*


Spectator 视图后如何 Microsoft HoloLens 具有体验时呈现给受众自一开始以来该产品已在 2015 年 1 月宣布必不可少的组成部分。 专业的安装程序使用具有很高的要求和成本高昂的价格标记使用它。 例如，照相机使用 genlock 信号以确保与跟踪系统 HoloLens 协调的精确计时。 在此设置中，移动 spectator 视图摄像头，可能会同时保持全息稳定来匹配人，他们将看到直接在 HoloLens 中的体验的体验。

Spectator 视图的开放源代码版本权衡移动照相机远程测试机组，以大幅降低总体安装程序的成本的功能。 此项目使用严格装载到 HoloLens 外部照相机高清晰照片和视频 holographic Unity 项目。 **在实时演示，照相机应保持在固定位置。** 照相机移动可能会导致全息图抖动或偏差。 这是因为视频帧的计时和全息在 PC 上的呈现方式可能不会精确同步。 因此，保持稳定照相机或限制移动将产生接近戴上 HoloLens 的人可以看到结果。

若要使应用能够准备好进行 spectator 视图，您将需要生成[共享体验](holograms-240.md)应用，并确保应用程序可以运行 HoloLens 以及 Unity 编辑器中的桌面。 桌面版本的应用会在该复合视频源和呈现全息中生成的其他组件。

## <a name="how-to-set-up-spectator-view-pro"></a>如何设置 Spectator 视图 Pro 

### <a name="requirements"></a>要求

![Spectator 视图 Pro 远程测试机组](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>硬件购物列表

下面是推荐的硬件列表，但太尝试使用其他兼容的单位。 

|硬件组件                                                                     |建议               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|适用于使用 HoloLens 模拟器 holographic 开发 PC 配置  |                              | 
|照相机，摄像机带有 out HDMI 或照片拍摄 SDK                                             | 对于照片和视频捕获，我们已测试[Canon EOS 5d 标记 III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III)照相机。 有关实时演示，我们已测试[Blackmagic 设计生产照相机 4k](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)。<br><br>请注意，使用 (例如 GoPro) 出 HDMI 任何照相机应适用。 使用我们的视频的许多[Canon EF 14 mm f/2.8 L II USM Ultra-wide 角度固定可重用功能区](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q)，但应选择满足你的需求的相机镜头。 | 
|捕获有关您的 PC 以获得颜色帧从照相机校准你远程测试机组并预览复合场景的卡 |  我们已测试[Blackmagic 设计强度 Pro 4k 捕获卡](https://www.amazon.com/dp/B00U3QNP7Q)。 | 
|电缆                                                                                 |  [为迷你 HDMI HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00)将您的照相机附加到捕获卡。 请确保你购买符合您的照相机 HDMI 外形规格。 (GoPro，例如，通过输出[Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1)。)<br><br>[HDMI 电缆](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1)用于查看源预览监视器或电视上复合 | 
|加工 aluminum 大括号，使你 HoloLens 连接到摄像机。 | [Aluminum 括号](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D 打印适配器以便连接到摄像机 hotshoe HoloLens 装入。| [3D 打印的适配器](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Hotshoe fastener 装载 hotshoe 适配器                                       |  [Hotshoe Fastener](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|已分类的 nuts、 bolt 和工具                                                |  [1/4 到 20 个"nuts](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20"x 3/4"Bolt](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[7/16 nut 驱动程序](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>软件组件

1. 从下载的软件[spectator 视图的 GitHub 项目](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)。
2. [Blackmagic 捕获卡 SDK](https://www.blackmagicdesign.com/support)。 \
 桌面的视频开发人员 SDK 在"下载最新"的搜索。
3. [Blackmagic 桌面视频运行时](https://www.blackmagicdesign.com/support)。 \
 在"下载最新"的桌面的视频软件更新的搜索。 \
 请确保版本编号匹配项的 SDK 版本。
4. [OpenCV 3.1](https://opencv.org/releases.html)校准或视频捕获，而无需 Blackmagic 捕获卡。
5. [Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) （可选）。 \
 如果您使用 Canon 摄像机，并且有权访问 Canon SDK，你可以为您的 PC 以获取更高分辨率图像接入照相机。
6. 适用于您全息版的应用程序开发的 unity。 \
 OSS 项目中找不到受支持的版本。
7. 使用最新的更新的 visual Studio 2015。

### <a name="building-your-own-spectator-view-pro-camera"></a>构建 Spectator 视图 Pro 照相机

**通知和免责声明：** 进行到 HoloLens 硬件 （包括但不是限于，设置"spectator 视图"将 HoloLens） 修改基本时应始终遵循安全防范措施。 进行任何修改之前，阅读所有说明和手册。 它由你负责按照所有说明并使用工具的指导。 购买或许可你 HoloLens 与有限的担保或不作任何担保。 请阅读在适用[HoloLens 许可协议或使用条款和销售](https://www.microsoft.com/hololens/support/warranty)若要了解保证选项。

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>远程测试机组程序集

![组装的 Spectator 视图 Pro 远程测试机组 HoloLens 和 DSLR 照相机的。](images/assembly.gif)<br>
*与 HoloLens 和 DSLR 相机已组装的 Spectator 视图 Pro 远程测试机组*


* 使用 T7 螺丝刀 headband 移除 HoloLens。 松散螺丝后，浏览它们与从另一侧一支文档活页夹。
* 删除螺丝上限内使用小型平面头螺丝刀 HoloLens 面板的前面。
* 使用 T15 螺丝刀 HoloLens 大括号，使你删除从删除小 torx bolt 和钩状附件。
* HoloLens 置于大括号对齐的面板内与前面的括号延伸公开漏洞。 HoloLens 的手臂应通过底部的大括号球瓶保持原位。
* 重新附加你和钩状附件来保护对括号 HoloLens。
* 附加到您的相机 hotshoe hotshoe fastener。
* 将装入适配器附加到 hotshoe fastener。
* 旋转适配器以便在窄端朝前且平行于照相机的可重用功能区。
* 使用 1/4"螺母使用 7/16 nut 驱动程序保护的位置中的适配器。
* 将针对适配器的括号置于前面的 HoloLens 的面板是尽可能接近前置照相机的可重用功能区位置。
* 将括号附加与 4 1/4"细节使用 7/16 nut 驱动程序。

#### <a name="pc-setup"></a>PC 安装程序
* 从软件组件部分安装软件。
* 将捕获卡添加到您的主板上打开 PCIe 槽。
* 插入从照相机 HDMI 电缆连接到外部 HDMI 槽 （HDMI 接程序） 捕获卡上。
* 插入从捕获卡上的中央 HDMI 插槽 （HDMI 扩展） HDMI 电缆连接到的可选预览监视器。

#### <a name="camera-setup"></a>照相机设置
* 更改您的照相机为视频模式，因此它会输出在完整 1920 x 1080 解析而裁剪后 3:4 照片分辨率。
* 找到照相机的 HDMI 设置并启用**镜像**或**双监视器**。
* 将输出分辨率设置为 1080 p。
* 关闭**屏幕显示上实时查看**因此复合源中不出现任何屏幕覆盖。
* 打开您的摄像机**实时视图**。
* 如果使用**Canon SDK**并且想要使用 flash 的单元，请禁用**无提示 LV 投篮机会控制在**。
* 插入从照相机 HDMI 电缆连接到外部 HDMI 槽 （HDMI 接程序） 捕获卡上。

#### <a name="calibration"></a>校准

设置后你 spectator 视图远程测试机组，必须以获取对你 HoloLens 照相机的位置和旋转偏移量进行调整。
* 打开下 Calibration\Calibration.sln 的校准 Visual Studio 解决方案。
* 在此解决方案中，您会发现文件 dependencies.props 这会创建用于第三方源的非独占位置的宏。
* 更新此文件的位置安装 OpenCV 3.1、 Blackmagic SDK 和 Canon SDK （如果适用）

![在 Visual Studio 中的依赖项位置快照](images/dependencies-600px.png)<br>
*在 Visual Studio 中的依赖项位置快照*


* 输出校准模式 Calibration\CalibrationPatterns\2_66_grid_FULL.png 平面、 刚性图面上。
* 通过 USB 将 HoloLens 插入您的 PC。
* 更新预处理器定义**HOLOLENS_USER**并**HOLOLENS_PW**中**stdafx.h**有 HoloLens' 设备门户凭据。
* HDMI 通过将您的照相机附加到您捕获的卡，并将其打开。
* 运行校准解决方案。
* 移动棋盘图案周围的视图如下：

![校准 Spectator 视图 Pro 远程测试机组](images/calibration.gif)<br>
*校准 Spectator 视图 Pro 远程测试机组*


* 棋盘视图中时，将自动执行图片。 然后转到下一步姿势之前查找白光 HoloLens 的面板上。
* 完成后，按**Enter**焦点创建校准应用**CalibrationData.txt**文件。
* 此文件将保存到**Documents\CalibrationFiles\CalibrationData.txt**
* 检查此文件以查看是否准确校准数据：
   * **DSLR RMS**应接近于 0。
   * **HoloLens RMS**应接近于 0。
   * **立体声 RMS**可能是 20-50，这是可以接受因为之间两个相机的视野可能不同。
   * **翻译**是连接的相机镜头到 HoloLens 的照相机的距离。 这是以米为单位。
   * **旋转**应接近标识。
   * **DSLR_fov** y 值应接近垂直视图的字段预期的方式从滤镜的焦点长度和正文的任何照相机裁剪因素。
* 如果上述值的任何不似乎有意义，重新校准。
* 此文件复制到**资产**目录中 Unity 项目。

### <a name="compositor"></a>Compositor

复合器是一个 Unity 扩展，以在 Unity 编辑器中的窗口的形式运行。 若要启用此功能，复合器 Visual Studio 解决方案首先需要生成。
* 打开下 Compositor\Compositor.sln 的复合器 Visual Studio 解决方案
* 使用上面的校准解决方案相同的条件更新 dependencies.props。 如果遵循了校准的步骤，此文件将具有已更新。
* 生成整个解决方案作为版本和体系结构与你的 Unity 版本的体系结构匹配。 如果有疑问，构建 x86 和 x64。
* 如果您生成适用于 x64 的解决方案，还生成 SpatialPerceptionHelper 项目为 x86 因为它将在 HoloLens 上运行。
* 如果它正在运行你的应用程序，请关闭 Unity。 Unity 需要进行重新启动，如果在运行时更改了 Dll。
* 运行 Compositor\CopyDLL.cmd 要复制到 Unity 项目构建此解决方案中的 Dll。 此脚本将 Dll 复制到包含的示例项目。 项目设置后，可以使用命令行自变量指向你的项目的资产目录复制以及运行 CopyDLL。
* 启动示例 Unity 应用程序。

### <a name="unity-app"></a>Unity 应用

为窗口在 Unity 编辑器中运行排序器。 包含的示例项目具有的所有内容设置为使用 spectator 视图一次复合器 Dll 被复制。

Spectator 视图需要应用程序作为运行[共享体验](holograms-240.md)。 这意味着在 HoloLens 发生任何应用程序状态更改需要联网更新过在 Unity 中运行应用程序。

如果从新的 Unity 项目开始，你需要先进行一些设置：
* 复制**资产/加载项/HolographicCameraRig**从示例项目到项目。
* 将最新 MixedRealityToolkit 添加到你的项目，包括**共享**， **csc.rsp**， **gmcs.rsp**，以及**smcs.rsp**。
* 添加你**CalibrationData.txt**文件解压缩到资产目录。

![Unity 资产目录快照](images/files-400px.png)

* 添加**HolographicCameraRig\Prefabs\SpectatorViewManager** prefab 向场景并填写字段：
   * **HolographicCameraManager**应与 HolographicCameraManager 预设可从 HolographicCameraRig prefab 目录填充。
   * **定位点**应与定位点预设可从 HolographicCameraRig prefab 目录填充。
   * **共享**应与共享预设可从 MixedRealityToolkit 填充。
   * 注意：如果任何这些预设已存在项目层次结构中，而不是这些客户都将使用现有预设。
   * **Spectator 视图 IP**应附加到你 spectator 视图远程测试机组你 HoloLens 的 IP。
   * **共享服务 IP**应运行 MixedRealityToolkit SharingService PC 的 IP。
   * 可选：如果有多个 spectator 查看远程测试机组附加到多个 PC 的**本地计算机 IP**应与 spectator 视图远程测试机组将与其的 PC 设置。

![在 Unity 中 spectator 视图管理器属性](images/spectatorviewmanager-500px.png)

* 启动 MixedRealityToolkit**共享服务**
* 生成和部署应用程序，如到 HoloLens D3D UWP 附加到 spectator 视图远程测试机组。
* 将应用部署到体验中的任何其他 HoloLens 设备。
* 检查**运行在后台**下的复选框**编辑/项目设置/播放机**。

![在 Unity 中的背景设置中运行](images/run-in-bg-400px.png)
* 启动复合器窗口下的**Spectator 视图排序器**

![在 Unity 中 spectator 视图的复合器视图](images/compositor-500px.png)

* 此窗口可以：
   * 开始录制视频
   * 拍摄一张照片
   * 更改全息图不透明度
   * 更改的帧偏移量 （它可调整颜色时间戳以的捕获卡滞后时间）
   * 打开捕获保存到的目录
   * （如果在项目中存在 SpatialMappingManager） 请求 spectator 视图照相机中的空间映射数据
   * 单独可视化场景的复合视图，以及颜色、 全息和 alpha 通道。
   * 打开您的照相机。
   * 在 Unity 中按简单不过了。
   * 照相机移动时，在 Unity 中的全息应身在何处在现实生活中相对于源您相机的颜色。

## <a name="see-also"></a>请参阅

* [混合的现实捕获](mixed-reality-capture.md) 
* [面向开发人员混合现实捕获](mixed-reality-capture-for-developers.md)
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* [GitHub 上的 spectator 视图 （预览） 代码](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Spectator 视图 （预览版） 在 GitHub 上的本机代码](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [GitHub 上 spectator Pro 视图代码](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
