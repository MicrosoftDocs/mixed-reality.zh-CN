---
title: MR 空间 220-空间音效
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 来了解空间音效概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 学院, 教程, 空间音效
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526939"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR 空间 220:空间音效

[空间音效](spatial-sound.md)breathes 影像, 并使其在世界中存在。 全息影像同时包含光和声音, 如果你发生丢失全息影像的情况, 空间音效可以帮助你找到它们。 空间音效并不像您在广播上听到的典型声音, 而是位于3D 空间中的声音。 利用空间音效, 你可以制作出全息影像, 就像你, 甚至是你自己的背景上! 在本课程中, 你将:

* 将你的开发环境配置为使用 Microsoft 空间音质。
* 使用空间音效来增强交互。
* 将空间音效与空间映射结合使用。
* 了解合理设计和混合最佳实践。
* 使用声音增强特殊效果, 并使用户进入混合现实世界。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 空间 220:空间音效</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>系统必备

* 配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。
* 一些基本C#的编程能力。
* 应已完成[尊敬的基本知识 101](holograms-101.md)。
* [为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)。 需要 Unity 2017.2 或更高版本。
  * 如果仍需要 Unity 5.6 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。 此版本可能不再是最新版本。
  * 如果仍需要 Unity 5.5 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。 此版本可能不再是最新版本。
  * 如果仍需要 Unity 5.4 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。 此版本可能不再是最新版本。
* 取消将文件存档到桌面或其他易于访问的位置。

>[!NOTE]
>如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)找到。

### <a name="errata-and-notes"></a>勘误表和说明

* 需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用 (*取消选中*) "启用仅我的代码", 以便在代码中命中断点。

## <a name="chapter-1---unity-setup"></a>第1章-Unity 设置

### <a name="objectives"></a>目标

* 更改 Unity 的声音配置, 以使用 Microsoft 空间音质。
* 将三维声音添加到 Unity 中的对象。

### <a name="instructions"></a>说明

* 启动 Unity。
* 选择 "**打开**"。
* 导航到桌面并找到以前未存档的文件夹。
* 单击 " **Starting\Decibel** " 文件夹, 然后按 "**选择文件夹**" 按钮。
* 等待项目在 Unity 中加载。
* 在 " **项目**" 面板中, 打开**Scenes\Decibel.unity**。
* 在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **P0LY**"。
* 在检查器中, 展开 " **AudioSource** ", 注意没有 " **Spatialize** " 复选框。

默认情况下, Unity 不会加载 spatializer 插件。 以下步骤将在项目中启用空间音质。

* 在 Unity 的顶部菜单中, 参阅**编辑 > 音频 > 项目设置**。
* 找到**Spatializer 插件**下拉列表, 并选择 " **MS HRTF Spatializer**"。
* 在 "**层次结构**" 面板中, 选择 " **HologramCollection > P0LY**"。
* 在 "**检查器**" 面板中, 找到 "**音频源**" 组件。
* 选中 " **Spatialize** " 复选框。
* 将**空间混合**滑块一直拖到**3d**上, 或在编辑框中输入**1** 。

现在, 我们将在 Unity 中生成项目, 并在 Visual Studio 中配置该解决方案。

1. 在 Unity 中, 选择 "**文件 > 生成设置**"。
2. 单击 "**添加打开的场景**" 添加场景。
3. 选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"。
4. 如果要专门针对 HoloLens 进行开发, 请将 "**目标设备**" 设置为 " **hololens**"。 否则, 请将其留在**任何设备**上。
5. 确保将 "**生成类型**" 设置为 " **D3D** ", 并将 " **SDK** " 设置为 "**最新安装**的" (应为 SDK 16299 或更高版本)
6. 单击“生成” 。
7. 创建名为 "App" 的**新文件夹**。
8. 单击**应用**文件夹。
9. 按 "**选择文件夹**"。

当 Unity 完成后, 将显示文件资源管理器窗口。

1. 打开**应用程序**文件夹。
2. 打开 "**分贝 Visual Studio 解决方案**"。

如果部署到 HoloLens:

1. 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x86**"。
2. 单击 "本地计算机" 按钮旁的下拉箭头, 然后选择 "**远程计算机**"。
3. 输入**HoloLens 设备 IP 地址**, 并将身份验证模式设置为**通用 (未加密的协议)** 。 单击 "**选择**"。 如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。
4. 在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。 如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。

如果要部署到沉浸式耳机:

1. 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x64**"。
2. 确保将部署目标设置为 "**本地计算机**"。
3. 在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。

## <a name="chapter-2---spatial-sound-and-interaction"></a>第2章-空间音效和交互

### <a name="objectives"></a>目标

* 使用声音提高全息图的真实感。
* 使用声音定向用户的注视。
* 使用声音提供手势反馈。

### <a name="part-1---enhancing-realism"></a>第1部分-增强真实性

#### <a name="key-concepts"></a>关键概念

* Spatialize 全息影像声音。
* 应将声音源置于全息图上的适当位置。

声音的适当位置将取决于全息图。 例如, 如果全息影像是人, 则声音源应位于嘴附近, 而不是英尺附近。

#### <a name="instructions"></a>说明

以下说明将 spatialized 声音附加到全息图。

* 在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **P0LY**"。
* 在 "**检查器**" 面板的**AudioSource**中, 单击 " **AudioClip** " 旁边的圆圈, 并从弹出窗口中选择 " **PolyHover** "。
* 单击 "**输出**" 旁边的圆圈, 并从弹出窗口中选择 " **SoundEffects** "。

项目分贝使用 Unity **AudioMixer**组件来启用调整声音组的音量级别。 通过以这种方式对声音进行分组, 可以在保持每个声音的相对音量的同时调整总体音量。

* 在**AudioSource**中, 展开 "**三维声音设置**"。
* 将**Doppler 级别**设置为**0**。

如果将 Doppler 级别设置为零, 则将禁用由运动 (一张全息图或用户) 导致的螺距变化。 Doppler 的典型示例是一种快速移动的汽车。 当汽车接近固定的侦听器时, 引擎的跨度会上升。 当它通过侦听程序时, 间距会降低距离。

### <a name="part-2---directing-the-users-gaze"></a>第2部分-定向用户的注视

#### <a name="key-concepts"></a>关键概念

* 使用声音吸引重要的全息影像。
* 此耳有助于指导眼睛的外观。
* 大脑有一些预期的预期。

了解预期的一个示例就是, 鸟瞰一般都是人的水平。 如果用户听到了鸟瞰声, 其初始反应就是查找。 如果在用户下放置鸟, 会使其面向正确的声音方向, 但无法根据需要查找的预期来找到全息影像。

#### <a name="instructions"></a>说明

以下说明允许 P0LY 隐藏在您后面, 以便您可以使用声音查找全息图。

* 在 "**层次结构**" 面板中, 选择 "**管理器**"。
* 在**检查器**面板中, 找到 "**语音输入处理程序**"。
* 在**语音输入处理程序**中, 展开 "**转到隐藏**"。
* 将**No 函数**更改为**PolyActions. GoHide**。

![关键字转为隐藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>第3部分-手势反馈

#### <a name="key-concepts"></a>关键概念

* 使用声音为用户提供积极的手势确认
* 不要严重影响用户的声音,
* 微妙的声音效果最好-不要会掩盖体验

#### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中, 展开 " **HologramCollection**"。
* 展开 " **EnergyHub** ", 然后选择 "**基本**"。
* 在**检查器**面板中, 单击 "**添加组件**" 并添加**手势声音处理程序**。
* 在**手势声音处理程序**中, 单击 "**导航已启动的剪辑**和**导航已更新的剪辑**" 旁边的圆圈, 并从弹出窗口中选择 " **RotateClick** "。
* 双击 "GestureSoundHandler" 以在 Visual Studio 中加载。

手势声音处理程序执行以下任务:

* 创建和配置**AudioSource**。
* 将**AudioSource**放在适当**GameObject**的位置。
* 播放与该笔势关联的**AudioClip** 。

#### <a name="build-and-deploy"></a>生成和部署

1. 在 Unity 中, 选择 "**文件 > 生成设置**"。
2. 单击“生成” 。
3. 单击**应用**文件夹。
4. 按 "**选择文件夹**"。

检查工具栏是否显示 "发布"、"x86" 或 "x64", 以及 "远程设备"。 如果不是, 则这是 Visual Studio 的代码实例。 可能需要从应用程序文件夹重新打开解决方案。

* 如果系统提示, 请重新加载项目文件。
* 如前所述, 从 Visual Studio 部署。

部署应用程序后:

* 观察在 P0LY 移动时声音如何变化。
* 说 *"转到隐藏"* , 使 P0LY 移到你后面的位置。 通过声音查找。
* 注视能源中心的底部。 点击并向左或向右拖动以旋转全息影像, 并注意单击声音如何确认手势。

注意:这里有一个文本面板, 将与您一起标记。 这将包含可在本课程中使用的可用语音命令。

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>第3章-空间音质和空间映射

### <a name="objectives"></a>目标

* 使用声音确认全息影像与真实环境之间的交互。
* 使用实物遮蔽声音。

### <a name="part-1---physical-world-interaction"></a>第1部分-物理世界交互

#### <a name="key-concepts"></a>关键概念

* 当遇到图面或其他对象时, 物理对象通常会发出声音。
* 声音应在体验中是适当的上下文。

例如, 对表设置杯会使声音更安静, 而不是在金属片上放置 boulder。

#### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中, 展开 " **HologramCollection**"。
* 展开 " **EnergyHub**", 选择 "**基本**"。
* 在 "**检查器**" 面板中, 单击 "**添加组件**", 然后单击 "添加**声音和操作**"。
* 在中,**单击以放置声音和操作**:
  * **在点击时选中 "父项"** 。
  * 设置要**放置**的**放置声音**。
  * 将**拾取声音**设置为**装货**。
  * 在 "**分拣" 操作**和 **"放置" 操作**中, 按右下方的 "+"。 将 EnergyHub 从场景拖到**无 (对象)** 字段。
    * 在 **"分拣操作**" 下, 单击 "**无函数** -> **EnergyHubBase** -> **ResetAnimation**"。
    * 在 **"放置时" 操作**下, 单击 "**无函数** -> **EnergyHubBase** -> **OnSelect**"。

![点击以放入声音和操作](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>第2部分-声音封闭

#### <a name="key-concepts"></a>关键概念

* 声音, 如光源, 可以是封闭像素。

典型的示例是音乐会厅。 当某个侦听器在大厅外且门闭合时, 音乐听起来 muffled。 通常还会减少容量。 打开门后, 就会听到真实音量的所有声音。 高频声音通常会超出低频率。

#### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **P0LY**"。
* 在**检查器**面板中, 单击 "**添加组件**" 并添加**音频发射器**。

音频发射器类提供以下功能:

* 还原对**AudioSource**卷的任何更改。
* 按照**AudioEmitter**连接到的**GameObject**的方向, 从用户的位置执行**RaycastNonAlloc** 。

RaycastNonAlloc 方法用作性能优化, 以限制分配和返回的结果数。

* 对于遇到的每个**IAudioInfluencer** , 将调用**ApplyEffect**方法。
* 对于不再遇到的每个以前的**IAudioInfluencer** , 请调用**RemoveEffect**方法。

请注意, AudioEmitter 对人为时间刻度的更新, 而不是每个框架的更新。 这样做是因为, 人们通常不能以足够快的速度移动, 因此, 需要比每个季度或半秒钟的频率更频繁地进行更新。 从一个位置到另一个位置快速传送的全息影像可能会突破错觉。

* 在 "**层次结构**" 面板中, 展开 " **HologramCollection**"。
* 展开 " **EnergyHub** " 并选择 " **BlobOutside**"。
* 在**检查器**面板中, 单击 "**添加组件**" 并添加**音频 Occluder**。
* 在**音频 Occluder**中, 将 "**截止频率**" 设置为**1500**。

此设置将 AudioSource 频率限制为 1500 Hz 和更低。

* 将**Volume Pass**设置为**0.9**。

此设置将 AudioSource 的量降低到其当前级别的 90%。

音频 Occluder 实现 IAudioInfluencer:

* 使用附加到**AudioSource**托管的**AudioLowPassFilter**的封闭**效果。**
* 将卷衰减应用于 AudioSource。
* 通过设置非特定截止频率并禁用筛选器来禁用该效果。

用于中性的频率为 22 kHz (22000 Hz)。 选择此频率的原因是, 它的最大频率为人体耳可以听到的最大公称, 这不会影响声音。

* 在 "**层次结构**" 面板中, 选择 " **SpatialMapping**"。
* 在**检查器**面板中, 单击 "**添加组件**" 并添加**音频 Occluder**。
* 在**音频 Occluder**中, 将 "**截止频率**" 设置为**750**。

如果多个 occluders 位于用户与**AudioEmitter**之间的路径中, 则会将最低频率应用于筛选器。

* 将**Volume Pass**设置为**0.75**。

如果多个 occluders 位于用户与**AudioEmitter**之间的路径中, 则会应用添加性地。

* 在 "**层次结构**" 面板中, 选择 "**管理器**"。
* 在 "**检查器**" 面板中, 展开 "**语音输入处理程序**"。
* 在**语音输入处理程序**中, 展开 "**转到**"。
* 将**No 函数**更改为**PolyActions. GoCharge**。

![关键字走电](images/gocharge.png)

* **在此处**展开。
* 将**No 函数**更改为**PolyActions. 卷土重来**。

![关键字过来这里](images/comehere.png)

#### <a name="build-and-deploy"></a>生成和部署

* 如前所述, 在 Unity 中生成项目, 并在 Visual Studio 中部署。

部署应用程序后:

* 说 *"走电"* , 让 P0LY 进入能量中心。

请注意声音的变化。 这听起来 muffled。 如果你能够在你与能源中心之间定位墙壁或其他对象, 你应该注意到 muffling 的声音, 因为现实世界封闭了。

* 说 *"现在*就可以", 让 P0LY 离开能源中心, 并将其放在您前面。

请注意, 一旦 P0LY 退出能源中心, 就会删除声音封闭。 如果你仍在封闭, P0LY 可能会被现实世界封闭像素。 尝试移动以确保对 P0LY 有清楚的视觉。

### <a name="part-3---room-models"></a>第3部分-房间模型

#### <a name="key-concepts"></a>关键概念

* 空间大小提供了 subliminal 的队列, 它们有助于进行合理的本地化。
* 房间模型是按**AudioSource**设置的。
* [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供用于设置房间模型的代码。
* 对于混合现实体验, 请选择最适合于现实世界空间的房间模型。

如果要创建虚拟现实方案, 请选择最适合虚拟环境的房间模型。

## <a name="chapter-4---sound-design"></a>第4章-声音设计

### <a name="objectives"></a>目标

* 了解有效的声音设计的注意事项。
* 了解混合技巧和指导原则。

### <a name="part-1---sound-and-experience-design"></a>第1部分-声音和体验设计

本部分介绍关键的声音, 并体验设计注意事项和指导原则。

#### <a name="normalize-all-sounds"></a>规范化所有声音

这样就无需使用特殊案例代码调整每个声音的音量级别, 这可能非常耗时, 并且限制了轻松更新声音文件的能力。

#### <a name="design-for-an-untethered-experience"></a>设计 untethered 体验

HoloLens 是完全包含的 untethered 全息计算机。 你的用户可以在移动时使用你的体验。 务必通过浏览来测试您的音频组合。

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>从逻辑位置在全息影像上发出声音

在现实生活中, 狗不会吠其尾部, 人类的语音不会来自其英尺。 避免在全息影像的意外部分发出声音。

对于小全息影像, 从几何图形中心开始发出声音是合理的。

#### <a name="familiar-sounds-are-most-localizable"></a>熟悉的声音是最可本地化的

人为语音和音乐非常易于本地化。 如果有人调用了您的姓名, 则可以从语音的方向和距离。 简短, 不熟悉的声音更难本地化。

#### <a name="be-cognizant-of-user-expectations"></a>Cognizant 用户期望

生活经验使我们能够确定声音位置。 这就是人们语音特别容易本地化的原因之一。 发出声音时, 请注意用户的预期预期。

例如, 当有人听到了他们通常会查找的鸟瞰歌曲时, 因为鸟瞰通常会位于视线的上方 (飞行或树形上)。 用户打开正确的声音方向并不是很常见, 而是在无法找到全息影像时在错误的垂直方向上看起来不确定的。

#### <a name="avoid-hidden-emitters"></a>避免隐藏发射器

在实际情况下, 如果听到声音, 通常可以识别出发出声音的对象。 在您的体验中, 这也应为 true。 用户听听声音非常不安, 知道声音出自何处, 看不到对象。

此准则有一些例外情况。 例如, 字段中的 crickets 等环境声音无需可见。 生活经验为我们熟悉这些声音的来源, 无需查看。

### <a name="part-2---sound-mixing"></a>第2部分-混音

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>在 HoloLens 上将混合目标设定为 70% 的卷

混合现实体验允许在现实世界中查看全息影像。 它们还应该允许听真实世界声音。 利用 70% 的音量目标, 用户可以在他们周围倾听世界, 并获得你的体验。

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>100% 卷上的 HoloLens 应 drown 外部声音

100% 的卷级别与虚拟现实体验类似。 用户在视觉上传输到不同的世界。 相同的呼叫时应为 true。

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>使用 Unity AudioMixer 调整声音类别

设计你的组合时, 创建声音类别并能够将其音量增加或减少为一个单元通常很有帮助。 这会保留每个声音的相对级别, 同时使整体组合的快速而简单的更改。 常见类别包括:声音效果、环境、语音转移和背景音乐。

#### <a name="mix-sounds-based-on-the-users-gaze"></a>基于用户的注视混合声音

通常, 根据用户所在的位置 (或不需要) 来更改声音混合, 这通常很有用。 此方法的一个常见用途是降低全息帧之外的全息影像的音量级别, 使用户能够更轻松地将重点放在其前面的信息上。 另一种用途是增加声音量, 以吸引用户关注重要事件。

#### <a name="building-your-mix"></a>构建混合

在构建组合时, 建议从体验背景音频开始, 并根据重要性添加层。 通常, 这会导致每个层都大于上一个层。

应该构想你的混合为反转漏斗图, 最重要的是最不重要的 (通常是 quietest 的声音), 因此建议将你的混合与下图类似。

![声音混合结构](images/soundlevels.png)

语音转移是一个有趣的方案。 根据你创建的体验, 你可能想要使用立体声 (未本地化) 声音或 spatialize 你的语音转移。 两个 Microsoft 发布的体验演示了每个方案的极佳示例。

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)使用立体声声音。 当讲述人描述正在查看的位置时, 声音是一致的, 并且不会根据用户的位置而变化。 这使讲述人可以在不离开环境 spatialized 声音的情况下描述场景。

[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)使用 spatialized 的语音。 侦探的声音用于帮助用户关注重要的线索, 就像实际人在房间里。 这样, 就可以更好地浸入式解决谜的体验。

### <a name="part-3--performance"></a>第3部分-性能

#### <a name="cpu-usage"></a>CPU 使用情况

使用空间音效时, 10-12 发射器会消耗约 12% 的 CPU。

#### <a name="stream-long-audio-files"></a>流式传输长音频文件

音频数据可能很大, 尤其是在常见采样速率 (44.1 和 48 kHz) 上。 一般规则是, 应流式传输超过 5-10 秒的音频文件, 以降低应用程序内存使用量。

在 Unity 中, 可以在文件的导入设置中标记音频文件以进行流式传输。

![音频导入设置](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>第5章-特殊效果

### <a name="objectives"></a>目标

* 将深度添加到 "幻窗口"。
* 将用户带入虚拟世界。

### <a name="magic-windows"></a>魔术窗口

#### <a name="key-concepts"></a>关键概念

* 将视图创建到隐藏世界中, 这在视觉上非常引人注目。
* 当全息图或用户处于隐藏世界附近时, 通过添加音频效果来增强真实性。

#### <a name="instructions"></a>说明

* 在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **Underworld**"。
* 展开 " **Underworld** " 并选择 " **VoiceSource**"。
* 在**检查器**面板中, 单击 "**添加组件**" 并添加 "**用户语音效果**"。

**AudioSource**组件将添加到**VoiceSource**中。

* 在**AudioSource**中, 将 "**输出**" 设置为**UserVoice (混音器)** 。
* 选中 " **Spatialize** " 复选框。
* 将**空间混合**滑块一直拖到**3d**上, 或在编辑框中输入**1** 。
* 展开 "**三维声音设置**"。
* 将**Doppler 级别**设置为**0**。
* 在 "**用户语音效果**" 中, 将**父对象**从场景中设置为**Underworld** 。
* 将**最大距离**设置为**1**。

设置**最大距离**会告诉**用户语音效果**在启用此效果之前, 用户必须先到父对象。

* 在 "**用户语音效果**" 中, 展开 " **Chorus 参数**"。
* 将**深度**设置为**0.1**。
* 依次点击 " **1**"、" **2 卷**" 和 " **3 卷**到**0.8**"。
* 将**原始**音量设置为**0.5**。

以前的设置配置用于向用户语音添加丰富的 Unity **AudioChorusFilter**的参数。

* 在 "**用户语音效果**" 中, 展开 " **Echo Parameters**"。
* 将**延迟**设置为**300**
* 将**衰减比率**设置为**0.2**。
* 将**原始**音量设置为**0**。

以前的设置配置用于使用户的语音回显的 Unity **AudioEchoFilter**的参数。

用户语音效果脚本负责:

* 测量用户与脚本附加到的**GameObject**之间的距离。
* 确定用户是否面向**GameObject**。

对于启用的效果, 用户必须面向 GameObject, 而不考虑距离。

* 将**AudioChorusFilter**和**AudioEchoFilter**应用和配置到**AudioSource**。
* 禁用筛选器以禁用该效果。

用户语音效果使用[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)中的 Mic Stream 选择器组件选择高质量的语音流并将其路由到 Unity 的音频系统。

* 在 "**层次结构**" 面板中, 选择 "**管理器**"。
* 在 "**检查器**" 面板中, 展开 "**语音输入处理程序**"。
* 在**语音输入处理程序**中, 展开**Show Underworld**。
* 将**No 函数**更改为**UnderworldBase. OnEnable**。

![关键字显示 Underworld](images/showunderworld.png)

* 展开 "**隐藏 Underworld**"。
* 将**No 函数**更改为**UnderworldBase. OnDisable**。

![关键字隐藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>生成和部署

* 如前所述, 在 Unity 中生成项目, 并在 Visual Studio 中部署。

部署应用程序后:

* 面部面 (墙壁、楼层、桌子), 并说 *"Show Underworld"* 。

将显示 underworld, 所有其他全息影像都将隐藏。 如果看不到 underworld, 请确保您面对的是实际的表面。

* Underworld 全息图1米内的方法, 开始谈话。

现在音频效果适用于你的语音!

* 退出 underworld 并注意如何不再应用该效果。
* 说 *"隐藏 Underworld"* 以隐藏 Underworld。

Underworld 将隐藏, 并且以前隐藏的全息影像会重新出现。

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**了 MR 空间 220:空间音质**。

听世界, 让你的体验生活生动!
