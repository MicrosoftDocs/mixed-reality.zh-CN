---
title: 混合现实中的共享体验
description: 全息版应用可能会从一项 HoloLens 共享空间锚点, 从而使用户能够在真实世界的同一位置跨多个设备渲染全息影像。
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 共享体验, 混合现实, 全息影像, 空间锚, 多用户, 多
ms.openlocfilehash: fbc636a5d65e605ae9e9f9655eb15550ff8de7b7
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020206"
---
# <a name="shared-experiences-in-mixed-reality"></a>混合现实中的共享体验

全息影像不需要仅对一个用户保密。 全息版应用可能会从一个 HoloLens、iOS 或 Android 设备共享[空间锚点](coordinate-systems.md), 使用户能够在真实世界的同一位置跨多个设备渲染一张全息影像。

## <a name="six-questions-to-define-shared-scenarios"></a>定义共享方案的六个问题

在开始设计共享体验之前, 定义目标方案非常重要。 这些方案有助于阐明要设计的内容, 并建立一个共同术语, 以帮助比较和对比你的体验中所需的功能。 了解核心问题和解决方案的不同途径是发现此新介质固有机会的关键所在。

通过我们的 HoloLens 合作伙伴机构的内部原型和探索, 我们创建了六个问题来帮助你定义共享方案。 这些问题形成了一个框架, 而不是一种全面的设计, 旨在帮助用户更好地提取方案的重要属性。

### <a name="1-how-are-they-sharing"></a>1.它们如何共享？

演示可能由单个虚拟用户导致, 而多个用户可进行协作, 或者教师可以向使用虚拟材料的虚拟学生提供指导, 这种体验的复杂程度取决于用户拥有的代理级别或在方案中可以有。

![表中的 holograph](images/man-and-women-with-holograph-on-table-500px.png)

有多种方法可以共享, 但我们发现, 其中的大多数方法分为三类:
* **演示**:向多个用户显示相同内容时。 例如：教授使用同一全息材料向每个人提供一张讲座给多名学生。 但教授可能会有自己的提示和注释, 而其他人可能看不到这些内容。
* **协作**:当人们共同努力实现某些共同的目标时。 例如：教授介绍了如何执行心率的项目。 学生配对并创建共享的技能实验室体验, 使医疗学生可以在心形模型上开展协作并进行学习。
* **指南**:当一个人正在帮助他人解决一种更多的一对一样式交互中的问题时。 例如：教授在他/她在共享体验中执行 "心率" 的 "视觉" 技能实验室时向学生提供指导。

### <a name="2-what-is-the-group-size"></a>2.什么是组大小？

**一对一**共享体验可提供强大的基线, 理想情况下, 可以在此级别创建概念证明。 但请注意, 与大型组 (超过6人) 的共享可能会导致从技术 (数据和网络) 到社交 (有[多个头像](https://vimeo.com/160704056)) 的困难。 当你从**小** **组到大型组**时, 复杂性会以指数方式增加。

我们发现组的需求可能分为三个大小类别:
* 1:1
* 小型 < 7
* 大型 > = 7

组大小对重要问题有影响, 因为它会影响:
* 全息空间中人员的表示形式
* 对象的小数位数
* 环境规模

### <a name="3-where-is-everyone"></a>3.所有人位于何处？

当在同一位置发生共享体验时, 混合现实的强度会成为一种情况。 我们称之为该**归置**。 相反, 当分配组时, 至少有一个参与者不在同一物理空间 (如使用 VR 时), 我们称之为远程体验。 通常情况下, 您的组具有共同加入和远程参与者 (例如, 会议室中的两个组)。

![表上有 holograph 的三个用户](images/three-people-with-holograph-on-table-500px.png)

以下类别有助于传达用户所在的位置:
* 归置:所有用户都将处于相同的物理空间。
* 远程所有用户都将位于不同的物理空间。
* 全部你的用户将会混合使用和远程共享空间。

此问题之所以重要的原因有一些, 因为它会影响:
* 用户如何通信？
* 例如：是否应使用头像？
* 他们看到的对象。 是否共享所有对象？
* 是否需要适应自己的环境？

### <a name="4-when-are-they-sharing"></a>4.它们何时共享？

我们通常会在遇到共享体验时考虑**同步**体验:我们正在共同完成这一过程。 但包括由其他用户添加的单个虚元素, 你有一个**异步**方案。 在虚拟环境中, 假设有一个便笺或语音备忘录。 如何在设计中处理100虚拟备忘录？ 如果他们来自具有不同隐私级别的数十个用户怎么办？

假设你的体验是以下一类时间:
* **同步**:同时共享全息体验。 例如：两名学生同时执行技能实验室。
* **异步**:在不同时间共享全息体验。 例如：两名学生都在执行技能实验室, 但在不同的时间使用不同的部分。
* **两者**:你的用户有时会以异步方式同步共享, 而其他时间则可能。 例如：教授在以后对学生执行的分配进行评分, 并在下一天保留学生的注释。

此问题之所以重要的原因有一些, 因为它会影响:
* 对象和环境暂留。 例如：存储状态, 以便可以检索它们。
* 用户透视。 例如：或许记得在离开便笺时用户正在查看的内容。

### <a name="5-how-similar-are-their-physical-environments"></a>5.它们的物理环境有多相似？

除了共存体验外, 两种相同的现实环境的可能性很小, 除非这些环境的设计是相同的。 更有可能拥有**类似**的环境。 例如, 会议室是类似的, 他们通常会有一个集中定位的表。 另一方面, 生活中的房间通常是**不同**的, 可以在无限布局数组中包含任意数量的家具。

![表上的 Holograph](images/holograph-on-table-500px.png)

假设你的共享体验符合以下两个类别之一:
* **类似**:往往具有相似家具、环境光线和声音、物理房间大小的环境。 例如：教授在讲座厅, 学生处于讲座厅 B。讲座厅的椅子可能比 B 小, 但两者都可能有物理办公桌来放置全息影像。
* **不同**:家具设置、房间大小、轻薄和声音注意事项中的环境完全不同。 例如：教授处于专注房间, 而学生位于一家用学生和老师填写的大型讲座厅。

考虑环境会产生什么影响, 这一点很重要:
* 用户将如何体验这些对象。 例如：如果你的体验最适用于表, 并且用户没有表？ 或在平面地面表面上, 但用户的空间很混乱。
* 对象的小数位数。 例如：在表中放置一个 "6 英尺" 人机模型可能会很困难, 但心形模型会很好。

### <a name="6-what-devices-are-they-using"></a>6.它们使用哪些设备？

今天, 你通常可能会看到两个**沉浸式设备**之间的共享体验 (这些设备可能略有不同的按钮和相对功能, 但不是很大) 或两个**全息设备**(给定解决方案的目标)在这些设备上。 但请考虑,**二维设备**(移动/桌面参与者或观察者) 需要考虑, 尤其是在**混合2d 和3d 设备**的情况下。 了解你的参与者将使用的设备类型很重要, 不仅因为它们采用不同的保真度和数据约束和机会, 而且是因为用户对每个平台都有独特的期望。

## <a name="exploring-the-potential-of-shared-experiences"></a>了解共享体验的潜力

可以结合上述问题的答案来更好地了解你的共享方案, 并在扩展体验时 crystallizing 问题。 对于 Microsoft 的团队而言, 这有助于建立道路地图来改善我们目前使用的体验、了解这些复杂问题的细微差别, 以及如何利用混合现实中的共享体验。

例如, 请考虑从 HoloLens 启动的 Skype 方案之一: 用户使用了如何使用远程定位的专家[来修复损坏的轻型交换机](https://www.youtube.com/watch?v=iBfzs3G8BEA)和帮助。

![通过 Skype for HoloLens 修复带有协助的光源开关](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>专家提供从其<b>2d</b>桌面计算机到<b>三维混合现实</b>设备用户的<b>1:1</b>指导。本<b>指南</b>是<b>同步</b>的, 物理环境是<b>不同</b>的。</i>

这种体验就是我们当前经验的一项变化, 即, 将视频和语音的模式应用到新媒体。 但正如我们所期待的, 我们必须更好地定义应用场景和构建体验的机会, 以反映混合现实的强度。

请考虑 NASA 的 Jet 喷气实验室开发的[OnSight 协作工具](https://www.youtube.com/watch?v=ZOWQp0-Bkkw)。 使用 Mars 火星任务中数据的科学家可在 Martian 横向的数据内实时与同事进行协作。

![在以远程方式分开的同事之间进行协作, 为 Mars 火星计划工作](images/onsight-nasa-jpl.gif)

<i>科研人员使用三维<b>和二维</b>设备<b></b> , 通过一组较<b>小</b>的<b>远程</b>同事来浏览环境。<b>协作</b>是<b>同步</b>的 (但可以异步进行进行), 而物理环境则<b>与此类似</b>。</i>

像 OnSight 这样的体验会带来新的合作机会。 从物理上指出虚拟环境中的元素, 并在其解释其观点时共享其外观。 OnSight 使用浸入式和状态的镜头来重新考虑混合现实中的共享体验。

直观的协作是对话的成为, 并了解如何将此直觉应用到混合现实的复杂性, 这一点非常重要。 如果我们不仅可以在混合现实中重新创建共享体验, 还可以提升它们, 但对于未来的工作来说, 这是一项转变。 在混合现实中设计共享体验是一项新的令人兴奋的空间-我们只是一开始。

## <a name="get-started-building-shared-experiences"></a>开始构建共享体验

根据您的应用程序和方案, 将有各种要求来实现您所需的体验。 其中一些包括
* 匹配-正在进行:能够创建会话、播发会话并发现和邀请特定人员, 同时在本地和远程加入会话。
* 定位点共享:能够在一个公共的本地空间内协调多个设备上的坐标, 因此, 对于所有人来说, 全息影像会出现在同一位置。
* 上网能够在所有参与者之间实时同步用户和全息影像的位置、交互和移动。
* 状态存储:能够在空间中存储全息图的特性和位置, 以便进行中型会话加入, 稍后重新调用, 并针对网络问题提供可靠性。


共享体验的关键是多个用户在自己的设备上看到相同的全息影像, 常常通过共享锚点来跨设备对齐坐标来完成。
若要共享锚, 请使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间锚点</a>:
* 首先, 用户放置全息影像。
* 应用程序创建[空间锚点](coordinate-systems.md), 以便在世界上准确固定此全息图。
* 可以通过<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间锚点</a>将锚点共享到 HoloLens、IOS 和 Android 设备。 

使用共享空间定位点, 每个设备上的应用现在都有一个可放置内容的通用坐标系统。 现在, 应用可以确保在同一位置定位和定位全息影像。
在 HoloLens 设备上, 你还可以从一个设备离线共享锚点。  使用以下链接来确定最适合你的应用程序。


## <a name="evaluating-tech-options"></a>评估技术选项:
有各种服务和技术选项可用于帮助构建多用户混合现实体验。  选择路径可能比较困难, 因此, 要采用以方案为中心的角度, 下面详细介绍了一些选项。

## <a name="shared-static-holograms-no-interactions"></a>共享静态全息影像 (无交互):
在应用中利用<a href="https://docs.microsoft.com/azure/spatial-anchors/" target="_blank">Azure 空间锚</a>。  通过跨设备启用并共享空间锚, 你可以创建一个应用程序, 让用户同时查看同一位置的全息影像。  需要跨设备进行额外的同步, 以使用户能够与全息影像交互, 并查看影像的移动或状态更新。

## <a name="share-1st-person-perspective"></a>共享第一人称观点:
如果有受支持的 Miracast 接收方 (如 PC 或电视), 则对本地用户利用内置 Miracast 支持, 无需其他应用代码。

在应用中利用<a href="https://github.com/microsoft/mixedreality-webrtc" target="_blank">MixedReality-WebRTC</a> , 对于远程用户, 或在你具有要共享的非 Miracast 设备时。  启用 WebRTC 连接将在用户之间启用1:1 音频/视频流, 并使用数据通道在设备间进行消息传送。  混合现实实现通过向其他人提供 HoloLens 用户视图的混合现实视频流, 针对 HoloLens 进行优化。  如果要将视频流扩展到多个远程客户端, 通常使用<a href="https://webrtcglossary.com/mcu/" target="_blank">MCU 服务提供程序</a>(多点会议单位), 例如 SignalWire。  可通过<a href="https://github.com/andywolk/azure-freeswitch-gpu-windows" target="_blank">Freeswitch</a>获取对 Azure 的一键式 SignalWire 部署。  请注意, 这是付费服务, SignalWire 不属于 Microsoft。

## <a name="presenter-spectator-applications-and-demos"></a>Spectator 应用程序和演示:
在应用中利用<a href="https://github.com/microsoft/MixedReality-SpectatorView" target="_blank">MixedReality-SpectatorView</a> 。  启用其他设备 (HL、Android、iOS 和摄像机), 查看 HoloLens 从同一位置的不同透视中看到的内容, 并接收有关与全息影像交互的主机 HoloLens 用户交互的更新。  观看、拍摄照片 *, 并使用同一应用的 spectator 伴随的空间透视图, 记录主机对应用程序中的全息影像的处理情况的视频。

*注意：图片是通过 iOS/Android 设备上的屏幕截图拍摄的。

## <a name="multi-user-collaborative-experience"></a>多用户协作体验:
首先介绍[多用户学习教程](mrlearning-sharing(photon)-ch1.md), 该教程利用了用于本地用户和<a href="https://www.photonengine.com/PUN" target="_blank">Photon SDK</a>的<a href="https://docs.microsoft.com/azure/spatial-anchors/" target="_blank">Azure 空间锚点</a>来同步场景中的内容/状态。  创建本地协作应用程序, 其中每个用户在场景中的全息影像上都有自己的观点, 每个用户都可以完全与全息影像交互。  所有设备都提供更新, 交互冲突管理由 Photon 处理。  请注意, Photon 是一种非 Microsoft 产品, 因此, 可能需要使用 Photon 进行计费关系, 以实现更高的使用量。

## <a name="future-work"></a>未来工作:
组件功能和接口将帮助提供跨各种方案和基础技术的常见一致性和可靠支持。  在此之前, 请选择与你要在应用程序中实现的方案相符的最佳路径。

不同的方案或希望使用不同的技术/服务？  
请在此页底部的相应存储库中提供 GitHub 问题的反馈, 或在<a href="https://holodevelopers.slack.com/">HoloDevelopers 的时差</a>上联系。


## <a name="see-also"></a>请参阅
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* [DirectX 中的共享空间定位点](shared-spatial-anchors-in-directx.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)
* [旁观视图](spectator-view.md)
