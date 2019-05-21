---
title: MR 空间 220-空间声音
description: 按照本演练使用 Unity、 Visual Studio 和 HoloLens 学习空间声音概念的详细信息进行编码操作。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程、 空间声音
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590397"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR 空间 220:空间音效

[空间声音](spatial-sound.md)到全息 breathes 生活并为他们提供了在我们的世界中的存在。 全息组成浅色和声音，和如果碰巧被忽视您全息，空间声音可以帮助您找到它们。 空间声音不类似于典型的声音，您将听到广播，它是在 3D 空间中放置的声音。 使用空间的声音，您可以使声音起来像是后端，旁边，或甚至在您头上全息 ！ 在本课程中，你将：

* 配置开发环境，使用 Microsoft 空间声音。
* 使用空间声音来增强的交互。
* 与空间映射结合使用空间的声音。
* 了解合理的设计和混合使用最佳做法。
* 使用声音来增强特殊效果并将用户带到混合现实世界。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 空间 220:空间音效</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>系统必备

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。
* 一些基本C#编程功能。
* 您应当已完成[MR 基础知识 101](holograms-101.md)。
* HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
  * 如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。 此版本中可能不再保持最新状态。
  * 如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。 此版本中可能不再保持最新状态。
  * 如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。 此版本中可能不再保持最新状态。
* 取消存档到您的桌面或其他轻松地访问位置的文件。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)。

### <a name="errata-and-notes"></a>勘误表和说明

* "启用仅我的代码"必须禁用 (*未选中*) 在 Visual Studio 工具-> 选项-> 调试以便你的代码中命中断点。

## <a name="chapter-1---unity-setup"></a>第 1 章-Unity 安装程序

### <a name="objectives"></a>目标

* Unity 的声音配置更改为使用 Microsoft 空间声音。
* 将三维声音添加到 Unity 中的对象。

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择**打开**。
* 导航到你的桌面和查找文件夹你之前未存档。
* 单击**Starting\Decibel**文件夹，然后按**选择文件夹**按钮。
* 等待要在 Unity 中加载的项目。
* 在中 **项目**面板中，打开**Scenes\Decibel.unity**。
* 在中**层次结构**面板中，展开**HologramCollection** ，然后选择**P0LY**。
* 在检查器中，展开**AudioSource**请注意，没有任何**Spatialize**复选框。

默认情况下，Unity 不会加载 spatializer 插件。 以下步骤将在项目中启用空间声音。

* 在 Unity 的顶部菜单中，转到**编辑 > 项目设置 > 音频**。
* 查找**Spatializer 插件**下拉列表中，然后选择**MS HRTF Spatializer**。
* 在中**层次结构**面板中，选择**HologramCollection > P0LY**。
* 在中**Inspector**面板中，找到**音频源**组件。
* 检查**Spatialize**复选框。
* 拖动**空间 Blend**滑块一直向**3D**，或输入**1**编辑框中。

现在，Unity 中生成项目并在 Visual Studio 中配置该解决方案。

1. 在 Unity 中，选择**文件 > 生成设置**。
2. 单击**添加打开场景**添加场景。
3. 选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。
4. 如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。 否则，将其保持打开**任何设备**。
5. 请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。
6. 单击“生成” 。
7. 创建**新文件夹**名为"应用"。
8. 单击一下**应用**文件夹。
9. 按**选择文件夹**。

Unity 完成操作后，将出现一个文件资源管理器窗口。

1. 打开**应用**文件夹。
2. 打开**分贝 Visual Studio 解决方案**。

如果部署到 HoloLens:

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。
2. 单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。
3. 输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。 单击**选择**。 如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。
4. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。 如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。

如果部署到沉浸式头戴式：

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。
2. 请确保部署目标设置为**本地计算机**。
3. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。

## <a name="chapter-2---spatial-sound-and-interaction"></a>第 2 章-空间声音和交互

### <a name="objectives"></a>目标

* 增强使用声音的 hologram 真实性。
* 直接使用声音的用户的视线移动。
* 提供使用声音的手势反馈。

### <a name="part-1---enhancing-realism"></a>第 1 部分-增强真实性

#### <a name="key-concepts"></a>关键概念

* Spatialize 全息图声音。
* 声音源应置于全息图上的适当位置。

将声音的适当位置取决于全息图。 例如，如果全息图的人，声音源应靠近嘴巴不使用英尺。

#### <a name="instructions"></a>说明

以下说明将附加到一张全息图 spatialized 的声音。

* 在中**层次结构**面板中，展开**HologramCollection** ，然后选择**P0LY**。
* 中**Inspector**面板**AudioSource**，旁边单击该圆圈**AudioClip** ，然后选择**PolyHover**在弹出窗口中。
* 单击该圆圈旁边**输出**，然后选择**SoundEffects**在弹出窗口中。

项目级分贝使用 Unity **AudioMixer**组件以便调整的声音的组的声音级别。 通过分组声音这种方式，可以同时保持相对每个声音的音量调整总数量。

* 在中**AudioSource**，展开**3D 声音设置**。
* 设置**Doppler 级别**到**0**。

无需禁用更改引起的运动 （不管是全息图或用户） 的间距的级别设置 Doppler。 Doppler 一个典型示例是快速发展的汽车。 随着汽车的临近保持静止的侦听器，该引擎的音调上升。 它通过侦听器后，与距离会降低间距。

### <a name="part-2---directing-the-users-gaze"></a>第 2 部分-将定向用户的视线移动

#### <a name="key-concepts"></a>关键概念

* 使用声音呼吁人们关注重要全息。
* 耳朵帮助指导眼睛应在其中查找操作。
* 大脑有一些已学习的预期。

已学习的期望的一个示例是鸟通常是上面的人。 如果用户能听到鸟声音，其第一反应是查找。 放置鸟如下用户可能会导致它们面向正确的方向的声音，但无法找到基于的无需查找的假定条件下的全息图。

#### <a name="instructions"></a>说明

下面的说明启用 P0LY 隐藏后端，以便可以使用声音来查找全息图。

* 在中**层次结构**面板中，选择**经理**。
* 在中**Inspector**面板中，找到**语音输入处理程序**。
* 在中**语音输入处理程序**，展开**转隐藏**。
* 更改**没有函数**到**PolyActions.GoHide**。

![关键字：转隐藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>第 3 部分-手势的反馈

#### <a name="key-concepts"></a>关键概念

* 为用户提供使用声音正手势确认
* 不会给用户的方式的过度很大的声音 get
* 最佳的细微声音工作做不会掩盖体验

#### <a name="instructions"></a>说明

* 在中**层次结构**面板中，展开**HologramCollection**。
* 展开**EnergyHub** ，然后选择**Base**。
* 在中**Inspector**面板中，单击**添加组件**，并添加**笔势声音处理程序**。
* 中**笔势声音处理程序**，单击旁边的圆形可**导航开始剪辑**并**导航更新剪辑**，然后选择**RotateClick**从两个弹出窗口。
* 双击"GestureSoundHandler"若要在 Visual Studio 中加载。

声音笔势处理程序执行以下任务：

* 创建和配置**AudioSource**。
* 位置**AudioSource**的相应位置处**GameObject**。
* 播放**AudioClip**与手势相关。

#### <a name="build-and-deploy"></a>生成和部署

1. 在 Unity 中，选择**文件 > 生成设置**。
2. 单击“生成” 。
3. 单击一下**应用**文件夹。
4. 按**选择文件夹**。

检查工具栏上显示"发布"、"x86"或"x64"和"远程设备"。 如果没有，这是 Visual Studio 的编码的实例。 您可能需要重新打开应用程序文件夹中的解决方案。

* 如果系统提示，请重新加载项目文件。
* 与前面一样，从 Visual Studio 进行部署。

后部署该应用程序：

* 观察随着移动 P0LY 声音的更改。
* 说 *"转到隐藏"* 使 P0LY 移到后端的位置。 找到它的声音。
* 注视能源中心的基础。 点击和拖动左或向右旋转全息图，请注意如何产生咔嗒声确认手势。

注意：没有将与你的尾随的文本面板。 这将包含可以使用在本课程中可用的语音命令。

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>第 3 章 — 空间声音和空间映射

### <a name="objectives"></a>目标

* 确认全息和实际使用声音之间的交互。
* 遮蔽使用物理世界的声音。

### <a name="part-1---physical-world-interaction"></a>第 1 部分-物理世界交互

#### <a name="key-concepts"></a>关键概念

* 物理对象通常发出声音时遇到一个面或另一个对象。
* 声音应该是可以在进行适当的上下文。

例如，在表上设置一杯应发出比删除上一种裸机博尔德县更安静声音。

#### <a name="instructions"></a>说明

* 在中**层次结构**面板中，展开**HologramCollection**。
* 展开**EnergyHub**，选择**Base**。
* 在中**Inspector**面板中，单击**添加组件**，并添加**点击到位置与声音和操作**。
* 在中**到用声音和操作的位置点击**:
  * 检查**父置于点击**。
  * 设置**放置声音**到**位置**。
  * 设置**Pickup 声音**到**Pickup**。
  * 按 + 下同时底部**上 Pickup 操作**并**上放置操作**。 从到场景拖动 EnergyHub **None （对象）** 字段。
    * 下**上 Pickup 操作**，单击**否函数** -> **EnergyHubBase** -> **ResetAnimation**。
    * 下**上放置操作**，单击**否函数** -> **EnergyHubBase** -> **OnSelect**。

![点击到用声音和操作的位置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>第 2 部分-声音封闭

#### <a name="key-concepts"></a>关键概念

* 声音，光，如可以封闭的像素。

一个典型示例是 concert hall。 当侦听器都可以顺利之外 hall 和门已关闭，muffled 音乐听起来。 此外还有通常种数量缩减。 在门打开时，在实际容量听到声音的整个范围。 高频率声音通常多个低频率吸收。

#### <a name="instructions"></a>说明

* 在中**层次结构**面板中，展开**HologramCollection** ，然后选择**P0LY**。
* 在中**Inspector**面板中，单击**添加组件**，并添加**音频发射器**。

音频发射器类提供了以下功能：

* 将任何更改还原到的卷**AudioSource**。
* 执行**Physics.RaycastNonAlloc**从用户的位置的方向**GameObject**所属**AudioEmitter**附加。

RaycastNonAlloc 方法作为一种性能优化用于限制分配，以及返回的结果数。

* 每个**IAudioInfluencer**遇到调用**ApplyEffect**方法。
* 每个以前**IAudioInfluencer** ，它是不会再遇到的调用**RemoveEffect**方法。

请注意，AudioEmitter 上更新的人类时间刻度，而不是基于每个帧来。 这是因为人们通常不会移动速度足以处理要比每季度或约半秒钟更频繁地更新的效果。 全息快速从一个位置到另一个该 teleport 可能会中断视觉效果。

* 在中**层次结构**面板中，展开**HologramCollection**。
* 展开**EnergyHub** ，然后选择**BlobOutside**。
* 在中**Inspector**面板中，单击**添加组件**，并添加**音频 Occluder**。
* 在中**音频 Occluder**，请设置**截止频率**到**1500年**。

此设置将限制 AudioSource 频率到 1500 Hz 和更低版本。

* 设置**卷传递**到**0.9**。

此设置可 AudioSource 量减少到 90%的当前级别。

音频 Occluder 实现 IAudioInfluencer 到：

* 将封闭效果使用**AudioLowPassFilter**哪些获取附加到**AudioSource**托管的购买**AudioEmitter**。
* 适用于 AudioSource 卷衰减。
* 通过设置非特定语言的截止频率并禁用筛选器会禁用效果。

使用作为非特定语言的频率是 22 kHz (22000 Hz)。 由于上面的名义上的最大频率可以听到的声音对此进行任何明显影响人耳选择了此频率。

* 在中**层次结构**面板中，选择**SpatialMapping**。
* 在中**Inspector**面板中，单击**添加组件**，并添加**音频 Occluder**。
* 在中**音频 Occluder**，请设置**截止频率**到**750**。

当多个 occluders 位于中的用户之间的路径和**AudioEmitter**，最低频率应用于筛选器。

* 设置**卷传递**到**0.75**。

当多个 occluders 位于中的用户之间的路径和**AudioEmitter**，卷通过应用附加。

* 在中**层次结构**面板中，选择**经理**。
* 在中**Inspector**面板中，展开**语音输入处理程序**。
* 在中**语音输入处理程序**，展开**转费用**。
* 更改**没有函数**到**PolyActions.GoCharge**。

![关键字：转费用](images/gocharge.png)

* 展开**此处**。
* 更改**没有函数**到**PolyActions.ComeBack**。

![关键字：过来这里](images/comehere.png)

#### <a name="build-and-deploy"></a>生成和部署

* 与前面一样，Unity 中的项目在构建和部署 Visual Studio。

后部署该应用程序：

* 说 *"转费用"* 具有 P0LY 输入能源中心。

请注意声音中的更改。 它应听起来 muffled 和有点更安静。 如果能够自行定位与墙或其他您与能源中心之间的对象，您应注意到进一步 muffling 因为现实世界的封闭声音。

* 说 *"出现在此处"* 具有 P0LY 保留能源中心并准备好将自身定位。

请注意 P0LY 退出能源中心后，删除声音的阻挡物。 如果您依然是听力不好的阻挡物，P0LY 可能封闭的现实世界中。 尝试移动以确保有到 P0LY 清楚的认识。

### <a name="part-3---room-models"></a>第 3 部分-聊天室模型

#### <a name="key-concepts"></a>关键概念

* 空间大小提供张潜意识贡献声音本地化的队列。
* 每个设置的空间模型-**AudioSource**。
* [Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)聊天室模式设置为提供代码。
* 混合现实体验，选择最适合的实际空间空间模型。

如果要创建的虚拟现实方案，选择最适合虚拟环境的房间模型。

## <a name="chapter-4---sound-design"></a>第 4 章-合理的设计

### <a name="objectives"></a>目标

* 了解有关有效可靠的设计注意事项。
* 了解混合技术和指导原则。

### <a name="part-1---sound-and-experience-design"></a>第 1 部分-声音和体验设计

本部分讨论关键声音和体验设计注意事项和指南。

#### <a name="normalize-all-sounds"></a>规范化听上去

这不需要使用特殊大小写的代码，以调整每个声音，可能会非常耗时的音量级别，并限制能够轻松地更新声音文件。

#### <a name="design-for-an-untethered-experience"></a>针对无约束体验的设计

HoloLens 是完全包含、 无约束全息版的计算机。 你的用户可以并将使用你移动时的体验。 请确保测试音频混合周围的每个步骤。

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>发出声音从你全息上的逻辑位置

在现实生活中，dog 不会从其结尾吠和人的语音不是来自他/她英尺。 避免从意外部分你全息发出声音。

小全息是几何的合乎情理中心发出的声音。

#### <a name="familiar-sounds-are-most-localizable"></a>熟悉声音进行最本地化

人类声音和音乐也非常易于本地化。 如果有人调用你的名称，您就能够非常准确地远离确定从语音是何种方向和如何。 较短的不熟悉的声音是更难进行本地化。

#### <a name="be-cognizant-of-user-expectations"></a>要了解的用户的期望

生活体验起的作用我们能够标识声音的位置。 这是一个人的语音为何特别易于本地化的原因。 请务必将放置在声音时，应注意用户的已学习的期望。

例如，当有人会听到一鸟首歌曲时它们通常看起来，因为鸟往往上面直通 （飞编译或在树中）。 不常见的声音，按正确方向打开但查找中错误的垂直方向，并会变得混淆或感到沮丧时找不到全息图的用户。

#### <a name="avoid-hidden-emitters"></a>避免隐藏的发射器

在现实生活中，如果我们听到声音，我们可以通常确定发出声音的对象。 这还应包含在你的体验，则返回 true。 它可以会为用户听到声音，知道从哪里声音产生非常令其不安，不能以查看对象。

有一些例外情况，此原则。 例如，如 crickets 字段中的环境声音不需要可见。 生活体验为我们提供了熟悉这些声音而无需以查看它的源。

### <a name="part-2---sound-mixing"></a>第 2 部分-混音

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>目标为 70%卷上 HoloLens 混合

混合的现实体验支持全息现实世界中出现。 它们还应允许实际声音，以提出反馈意见。 70%卷目标可让用户了解其周围世界以及您的体验的声音。

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>在 100%卷 HoloLens 应淹没出外部声音

卷级别为 100%是类似于虚拟现实体验。 您可以看到，用户被传输到一个不同的世界。 相同应为 true 时传递语音。

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>使用 Unity AudioMixer 调整类别的声音

在设计您的混合时，最好经常创建声音类别，并且能够以增大或减小其作为一个单元的卷。 这将启用对整体组合的快速而简单的更改时保留的每个声音相对的级别。 常见类别包括：声音效果、 环境、 语音旁白和背景音乐。

#### <a name="mix-sounds-based-on-the-users-gaze"></a>基于用户的视线移动混合声音

通常可用于更改声音的组合在功能上的位置基于用户 （或不是） 查找。 此方法的一个常见用途是减少全息之外 Holographic 帧以方便用户将精力集中在它们的前面的信息上的音量级别。 另一个用途是声音的以提高突出用户的一个重要事件的音量。

#### <a name="building-your-mix"></a>构建您的混合

在生成您的混合时，建议开始体验的背景音频，添加层根据重要性。 通常情况下，这会导致要比之前更大的每一层。

期待您的混合会作为反转漏斗图中，使用最不重要 （和通常 quietest 声音） 在底部，我们建议结构您混合使用类似于下面的关系图。

![声音组合结构](images/soundlevels.png)

语音转移是一个有趣话题。 基于要创建的体验上你可能想让立体声 （未本地化） 功能或 spatialize 语音转移。 两个 Microsoft 发布体验说明每个方案的极好示例。

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)通过使用立体声语音。 讲述人描述时查看的位置，声音将是一致，并且不会不随用户的位置。 这使讲述人来描述而无需离开环境 spatialized 声音拍摄的场景。

[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)形式的侦探通过利用 spatialized 的语音。 侦探的语音使用以帮助使用户注意到了重要的启示，就像实际的人是在聊天室中。 这使解决神秘的深入体验更有意义。

### <a name="part-3--performance"></a>第 3-性能

#### <a name="cpu-usage"></a>CPU 使用率

时使用的空间声音，10-12 发射器将占用大约 12%的 CPU。

#### <a name="stream-long-audio-files"></a>Stream 长音频文件

音频数据可能很大，尤其是在常用的采样速率 (44.1 和 48 kHz)。 一般规则是应该传输时间超过 5-10 秒的音频文件以减少应用程序内存使用量。

在 Unity 中，可以将标记中的文件导入设置的流式处理的音频文件。

![音频导入设置](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>第 5 章-特殊效果

### <a name="objectives"></a>目标

* 将深度添加到"魔力 Windows"。
* 将用户引入虚拟世界。

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>关键概念

* 到隐藏的世界上创建视图，是极具视觉表现力。
* 通过添加音频效果，一张全息图或用户是隐藏的世界附近时增强真实性。

#### <a name="instructions"></a>说明

* 在中**层次结构**面板中，展开**HologramCollection** ，然后选择**Underworld**。
* 展开**Underworld** ，然后选择**VoiceSource**。
* 在中**Inspector**面板中，单击**添加组件**，并添加**用户语音效果**。

**AudioSource**组件将添加到**VoiceSource**。

* 在中**AudioSource**，请设置**输出**到**UserVoice (Mixer)**。
* 检查**Spatialize**复选框。
* 拖动**空间 Blend**滑块一直向**3D**，或输入**1**编辑框中。
* 展开**声音的三维设置**。
* 设置**Doppler 级别**到**0**。
* 在中**用户语音效果**，请设置**父对象**到**Underworld**从场景。
* 设置**最大距离**到**1**。

设置**最大距离**告知**用户语音效果**接近程度的用户必须对父对象之前已启用的效果。

* 在中**用户语音效果**，展开**合唱团参数**。
* 设置**深度**到**0.1**。
* 设置**点击 1 个卷**，**点击 2 卷**并**点击 3 个卷**到**0.8**。
* 设置**原生卷**到**0.5**。

以前的设置配置 Unity 的参数**AudioChorusFilter**用于将丰富功能添加到用户的声音。

* 在中**用户语音效果**，展开**Echo 参数**。
* 设置**延迟**到**300**
* 设置**Decay 比率**到**0.2**。
* 设置**原生卷**到**0**。

以前的设置配置 Unity 的参数**AudioEchoFilter**用于导致用户的声音回显。

用户语音效果脚本负责：

* 测量的用户之间的距离并**GameObject**脚本所附加到。
* 确定用户是否面向**GameObject**。

用户必须面向的 GameObject，而不考虑距离，对于要启用的效果。

* 将应用和配置**AudioChorusFilter**和一个**AudioEchoFilter**到**AudioSource**。
* 通过禁用筛选器中禁用效果。

用户语音效果使用的 Mic Stream 选择器组件，从[Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)，以选择高质量的语音流并将其路由到 Unity 的音频系统。

* 在中**层次结构**面板中，选择**经理**。
* 在中**Inspector**面板中，展开**语音输入处理程序**。
* 在中**语音输入处理程序**，展开**显示 Underworld**。
* 更改**没有函数**到**UnderworldBase.OnEnable**。

![关键字：显示 Underworld](images/showunderworld.png)

* 展开**隐藏 Underworld**。
* 更改**没有函数**到**UnderworldBase.OnDisable**。

![关键字：隐藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>生成和部署

* 与前面一样，Unity 中的项目在构建和部署 Visual Studio。

后部署该应用程序：

* 人脸的图面 （墙、 floor、 表） 和 say *"显示 Underworld"*。

将显示 underworld 并且所有其他全息将被隐藏。 如果您看不到 underworld，确保正面临着实际的图面。

* 方法在 1 米以内的 underworld 全息图并开始交谈。

现在是应用于语音的音频效果 ！

* 打开 underworld 离开并请注意，不会再应用效果的方式。
* 说 *"隐藏 Underworld"* 隐藏 underworld。

将隐藏 underworld 并且以前隐藏的所有全息将重新都出现。

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**MR 空间 220:空间声音**。

侦听世界上并通过声音将你的体验 ！
