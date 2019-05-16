---
title: Head 注视和提交
description: Head 注视和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实的视线移动，注视目标交互，设计
ms.openlocfilehash: 95f2cef8c10ce3d0d2a218953613fef6f0a00362
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730821"
---
# <a name="head-gaze-and-commit"></a>Head 注视和提交
Head 注视和提交是包括针对具有转发指点您头 （head 的方向） 的方向的对象输入的模型，然后对其进行操作的辅助数据库输入此类为以无线方式点击手手势或语音命令"Select"。 它被视为具有间接操作，这意味着它最适用于与超出手臂达到了的内容进行交互的"得"输入的模型。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>输入的模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>Head 注视和提交</td>
        <td>✔️ 建议</td>
        <td>建议使用 ✔️ (第三个选项-<a href="interaction-fundamentals.md">查看其他选项</a>)</td>
        <td>➕ 备用选项</td>
    </tr>
</table>

## <a name="head-gaze"></a>Head 视线移动
混合的现实耳机使用位置和方向的用户的头来确定其头方向向量。 您可以将此视为直接在用户的眼球之间直接向前点从激光。 这是相当粗略的用户正在近似值。 你的应用程序可以与此虚拟还是实际对象与射线相交和在该位置以让用户知道什么它们当前面向绘制光标。

除了头的视线移动，如 HoloLens 2 所示一些混合的现实耳机包含的眼跟踪生成的眼睛注视向量的系统。 这提供了用户正在细粒度的度量的值。 可以生成的视线移动并提交交互使用关注的视线移动，但这会带来一组非常不同的设计的限制，这将在单独介绍[眼跟踪文章](eye-tracking.md)。

## <a name="commit"></a>提交
面向对象或 UI 元素之后, 用户可以进行交互或者"单击"上使用辅助输入。 这被称为模型提交步骤。 支持以下的提交方法：

- 以无线方式手势
- 说话的语音命令"Select"或其中一个目标的语音命令
- 按上的单个按钮[HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- 按 Xbox 游戏板上的 A 按钮
- 按 Xbox 自适应控制器上的 A 按钮

### <a name="head-gaze-and-air-tap-gesture"></a>Head 注视和 air 的点击手势
空敲击是与手持设备竖直的情况下的点击手势。 若要执行敲击，引发食指到准备就绪的位置，然后用拇指捏合引发食指备份以释放。 HoloLens 1 上敲击是最常见的辅助输入。

![在准备好的位置，然后单击或点击动作手指](images/readyandpress.jpg)<br>

敲击，还可以在 HoloLens 2，并与原始版本放宽了。 现在支持几乎所有类型的 pinches，只要手形图标仍是靠背和小存货。 这使得更便于用户了解并执行手势。  此新敲击替换旧证书通过相同的 API，因此现有的应用程序会收到新行为会自动重新编译 HoloLens 2 后。

### <a name="head-gaze-and-select-voice-command"></a>Head 注视和"选择"语音命令
语音命令是在混合现实的主要交互方法之一。 它提供了非常强大的"免费手"机制来控制系统。 有不同类型的语音交互模型：

- "选择"的泛型命令允许执行"单击"传动或作为辅助输入的提交。
- 对象命令，如"关闭"或"使其更大"，允许执行并提交对作为辅助输入的操作。
- 全局 commnads 如"转到起始位置"，不需要一个目标。
- 会话的用户界面或实体等 Cortana 具有 AI 自然语言功能。
- 自定义 commnads

若要查找更多详细信息和可用的命令以及如何使用 comprenhesive 列表，请查看我们[语音设计](voice-design.md)指南。


### <a name="head-gaze-and-hololens-clicker"></a>Head 视线移动和 HoloLens Clicker
HoloLens Clicker 是专为 HoloLens 生成的第一个外围设备，包含与 HoloLens 1 Development Edition。 HoloLens Clicker 允许用户单击与最小手运动和提交作为辅助输入。 HoloLens clicker 连接到 HoloLens 1 或 2： 使用蓝牙低能耗 (BTLE)。

![](images/hololens-clicker-500px.jpg)<br>
HoloLens Clicker

可以找到更多的信息和说明设备配对[此处](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Head 注视和 Xbox 无线控制器
Xbox 无线控制器允许执行"单击"传动作为辅助输入通过使用一个按钮。 设备映射到一组默认的操作，可帮助导航和控制系统。 如果你想要自定义控制器，使用 Xbox 附件应用来配置你的 Xbox 无线控制器。

![](images/xboxcontroller.jpg)<br>
Xbox 无线控制器

[配对使用 PC 的 Xbox 控制器](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>自适应的 Head 注视和 Xbox 控制器
主要旨在满足使用有限的移动游戏玩家的需求，Xbox 自适应控制器是统一的中心的设备，可帮助使混合现实更易于访问。

Xbox 自适应控制器允许执行"单击"传动作为辅助输入通过使用一个按钮。 设备映射到一组默认的操作，可帮助导航和控制系统。 如果你想要自定义控制器，使用 Xbox 附件应用来配置你的 Xbox 自适应控制器。

![](images/xbox-adaptive-controller-devices.jpg)<br>
Xbox 自适应控制器

将交换机、 按钮、 装载和游戏杆创建唯一是你的自定义控制器体验等外部设备的连接。 与通过 3.5mm 插孔和 USB 端口连接的辅助设备控制按钮、 摇杆和触发器的输入。

![](images/xbox-adaptive-controller-ports.jpg)<br>
Xbox 自适应控制器端口

[设备配对的说明](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 站点上可用的详细信息。</a>


# <a name="head-gaze-design-guidelines"></a>Head 注视设计指南
> [!NOTE]
> 特定看设计的更多指导[即将推出](index.md)。

## <a name="head-gaze-targeting"></a>Head 视线移动目标
用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。 在 Windows Mixed Reality，通常这是使用用户的视线移动。
若要使用户能够成功使用体验，系统的计算的了解用户的意图和用户的实际目的，必须尽可能接近地对齐。 某种程度上，系统将解释用户的预期的操作正确，满意度增加和性能提高。


## <a name="target-sizing-and-feedback"></a>目标大小调整和反馈
视线移动矢量具有已重复显示可用于面向正常，但通常最适合总目标 （获取稍大些目标）。 1 到 1.5 度为单位的最小目标大小应在 3 个度的目标通常的速度更快，但在大多数情况下，允许用户成功操作。 请注意，用户目标实际上是三维元素-甚至的 2D 区域的大小无论投影面向它们应该是定目标区域。 提供一个元素是"活动"（该用户面向） 一些突出提示会非常有用-这可以包括处理，例如可见"悬停"效果、 音频突出显示或单击，或清除的元素的光标对齐方式。

![2 个计量距离处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*2 个计量距离处的最佳目标大小*

![突出显示的视线移动目标的对象的一个示例](images/gazetargeting-highlighting-640px.jpg)<br>
*突出显示的视线移动目标的对象的一个示例*

## <a name="target-placement"></a>目标位置
用户将通常无法天线的视野中, 找到很高或极低定位 UI 元素将重点放大部分其关注其主要焦点 （通常大约为水平视线） 周围的区域。 可帮助将大多数目标放入一些合理带围水平视线。 给定用户的情况下往往会将焦点置于将 UI 元素组合在一起的程度上它们从概念上讲相关一个相对较小可视区域上随时 （视觉 attentional 圆锥体约为 10 度），可以利用从关注链接行为项目到项目的用户将其提供注视转到区域。 在设计时用户界面，请记住在 HoloLens 和沉浸式耳机之间的字段的视图可能较大的变化。

![举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素](images/gazetargeting-grouping-1000px.jpg)<br>
*举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素*

## <a name="improving-targeting-behaviors"></a>提高目标行为
如果用户的意图以面向内容可以是确定 （或近似密切），它可以接受"near miss"会尝试在交互，就好像它们已正确目标很有帮助。 有了一些可纳入混合的现实体验的成功方法：

### <a name="head-gaze-stabilization-gravity-wells"></a>Head 注视稳定 ("重力 wells")
这应打开大多数/all 的时间。 此方法中删除用户可能有自然的 head 颈部 jit 编译器。 由于查找/谈到的行为也移动。

### <a name="closest-link-algorithms"></a>最接近链接算法
这些效果最佳稀疏的交互式内容与几个方面。 如果没有，您可以确定用户已尝试与之交互的可能性非常高，可以通过简单地假定某一级别的意图进行补充其目标的能力。

### <a name="backdatingpostdating-actions"></a>Backdating/postdating 操作
此机制可在需要速度的任务。 当用户要通过一系列的目标/激活 maneuvers 速度移动时，它可用于假定某些目的，并允许丢失的步骤执行操作目标的用户在具有焦点略有之前或之后 （50 毫秒前/后的有效期中点击略有前期测试）。

### <a name="smoothing"></a>平滑处理
此机制可用于的路径移动，减少由于自然磁头运动特征轻微抖动/原因。 通过路径动作，平滑大小/距离的移动而不是随着时间的推移通过平滑处理时

### <a name="magnetism"></a>消除
此机制可以看作"最靠近链接"算法的绘制光标向目标，或只需增加 hitboxes （无论是以可视方式还是不） 的更多常规版本用户达到可能的目标，如使用交互式布局与一些知识更好的方法用户的意图。 这可以是小型的目标对于特别有用。

### <a name="focus-stickiness"></a>焦点粘性
在确定其附近的焦点转至交互式元素，提供对当前已设定焦点的元素偏移。 这将有助于减少不正常时浮点位于自然干扰的两个元素之间的中点的切换行为的焦点。


## <a name="composite-gestures"></a>复合手势
应用程序可以识别多个不仅仅是单个的分流点。 通过组合点击保存和发布通过的手形图标移动，可以执行更复杂的复合手势。 低级别空间中的输入数据 （敲击和布隆） 的开发人员有权访问上生成这些复合或高级手势。

### <a name="air-tap"></a>敲击
以无线方式点击手势 （以及其他手势下面） 只对特定点击作出反应。 若要检测其他分流点，如菜单或掌握，您的应用程序必须直接使用上述两个关键组件手势部分中所述的较低级别交互。

### <a name="tap-and-hold"></a>Tap and hold
保留只需维护敲击的向下指位置。 以无线方式 tap 和 hold 的组合允许各种更复杂"单击并拖动"交互与来回移动，例如选取对象而不是在激活结合使用时或"鼠标按下"辅助交互，如显示上下文菜单。
时，此笔势但是，为用户设计可能很容易出现的任何扩展手势过程放宽其手 postures，应使用警告。

### <a name="manipulation"></a>操作
操作笔势可以用于移动、 调整大小或旋转一张全息图时所需的全息图 1:1 到用户的手移动做出反应。 此类 1:1 移动的一个用途是允许用户绘制或绘制世界中。
应通过的视线移动或指向操作手势的初始目标。 一旦点击并按住启动，该对象的任何操作然后处理手动移动，则释放要一下，尽管它们操作的用户。

### <a name="navigation"></a>导航
导航笔势操作如虚拟游戏杆和可用于导航的 UI 小组件，如径向菜单。 点击并按住启动手势，然后将移动您的手规范化 3D 多维数据集，以按下了初始中心内。 为 1，其中 0 表示起始点，可以从值-1 移动您的手沿 X、 Y 或 Z 轴。
导航可以用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标中键，然后向上和向下移动鼠标滚动 2D UI。

使用 rails 导航是指识别中某轴移动，直到该轴上达到特定阈值的能力。 启用多个轴中的移动后的应用程序中由开发人员，例如，此操作才有用，如果应用程序配置为识别跨 X，Y 轴的导航操作但还指定 X 轴使用 rails。 在这种情况下系统将在 X 轴的手移动，只要它们仍保持在假想 rails （指南） 在 X 轴，如果识别手动移动，也会发生 Y 轴。

在 2D 应用程序，用户可以使用垂直导航笔势滚动、 缩放，或拖动在应用程序。 这会注入到应用，以模拟相同类型的触摸手势的虚拟根手指收尾工作了。 用户可以选择何种操作进行的上述应用程序，通过选择按钮或说 < 滚动/拖/缩放 > 工具栏上的工具之间切换。

[复合笔势的详细信息](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>笔势识别器

使用手势识别的一个好处是，您可以配置仅用于当前目标全息图可以接受的手势的手势识别程序。 该平台将执行仅消除二义性要区分这些特定的受支持的手势。 这样一来，只需支持敲击一张全息图可以接受任意长度的按下和释放之间的时间，一张全息图时支持同时点击并按住可升级到保留点击后保留时间阈值。

## <a name="hand-recognition"></a>手动识别
HoloLens 识别手势通过跟踪的一个或两个手中可看到设备的位置。 HoloLens 它们处于就绪状态 （背面手形图标索引手指您朝上） 或按下的状态 （背面食指您朝下手形） 时看到了手中。 其他带来手中时，HoloLens 将忽略它们。
对于每个指针的 HoloLens 检测，可以访问它 （不带方向） 的位置和其按下的状态。 当手形图标接近手势帧的边缘时，你要还提供方向矢量，让他们知道如何移动其手，若要获取其返回 HoloLens 可以看到它可以向用户显示。

## <a name="gesture-frame"></a>手势帧
对于 HoloLens 的手势，手形图标必须是"手势在范围内"，（非常大致从鼻子到处理，以及在了肩膀之间） 手势感知照相机可以适当地看到某个范围内。 用户需要在此区域中 （许多用户最初假定手势框架必须在内通过 HoloLens，其视图和其手臂 uncomfortably 存放以进行交互） 的识别操作的成功和其自己舒适的训练。 在使用 HoloLens Clicker，手不需要为手势范围内。

在连续手势的情况下特别是，会出现风险移动中 （例如移动某些 holographic 对象） 时的中间笔势，笔势帧之外太多的事情并丢失它们的预期的结果的用户。

有三个您应考虑的事项：

- 手势帧存在并近似边界 （这教给 HoloLens 安装过程中） 上的用户培训。

- 当其手势是接近最大/重大手势帧边界内应用程序，不需要的结果都将导致丢失的手势程度时通知用户。 研究显示的此类通知系统的关键质量和 HoloLens shell 提供了此类型的通知 （视觉对象，指示的方向跨越正在进行中的边界对中央游标） 的一个很好示例。

- 应尽量减少中断手势帧边界的后果。 一般情况下，这意味着应停止在边界，但不是会反转手势的结果。 例如，如果用户在一个房间跨移动某些 holographic 对象，手势帧被破坏，但不是能返回到起始点时，应停止移动。 用户可能会遇到一些挫折然后，但可能更快地了解边界，而无需每次重新启动其完整的预期的操作。


## <a name="see-also"></a>请参阅
* [直接操作](direct-manipulation.md)
* [指向并提交](point-and-commit.md)
* [交互基础知识](interaction-fundamentals.md)
* [凝视和停留](gaze-targeting.md)
* [凝视和语音](voice-design.md)





