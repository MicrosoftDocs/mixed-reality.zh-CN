---
title: 头部凝视和提交
description: 头部凝视和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 混合现实, 凝视, 设定凝视目标, 交互, 设计
ms.openlocfilehash: aeca5ceacf5ae350aa06cb58cc68162f885f6d78
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387679"
---
# <a name="head-gaze-and-commit"></a>头部凝视和提交
"头盔" 和 "提交" 是一种输入模型, 它涉及到对象的方向为 "前进" (head 方向), 然后使用辅助输入 (例如, 手型按键或语音命令选择) 对对象进行操作。 它被视为带有间接操作的最大输入模型, 这意味着它最适用于与超出扶手的内容进行交互。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>输入模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>头部凝视和提交</td>
        <td>✔️ 推荐</td>
        <td>✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</td>
        <td>➕ 备用选项</td>
    </tr>
</table>

## <a name="head-gaze"></a>头部凝视
混合现实头戴显示设备根据用户头部的位置和方向来确定他们的头部方向向量。 你可以将其视为从用户两眼之间直指前方的激光。 这可粗略呈现出用户正查看的位置。 您的应用程序可以将此射线与虚拟或现实对象交叉, 并在该位置绘制光标, 以使用户了解当前的目标。

除了注视眼睛外, 某些混合现实耳机 (如 HoloLens 2) 还包括可生成眼睛良好矢量的眼睛跟踪系统。 这可精细测量用户正在查看的位置。 可以使用眼睛来构建注视和提交交互。 但这是一组截然不同的设计约束, 将在[目视的文章](eye-tracking.md)中单独介绍。

## <a name="commit"></a>提交
以对象或 UI 元素为目标后, 用户可以使用辅助输入交互或单击此元素。 这称为模型的提交步骤。 支持以下提交方法：

- Air 攻攻
- 说语音命令、选择或目标语音命令之一
- 在[HoloLens Clicker](hardware-accessories.md#hololens-clicker)上按单个按钮
- 按下 Xbox 游戏板上的 "A" 按钮
- 按 Xbox 自适应控制器上的 "A" 按钮

### <a name="head-gaze-and-air-tap-gesture"></a>头部凝视和隔空敲击手势
隔空敲击是一种手部直立的点击手势。 若要执行分流, 请将索引向下移动到准备好的位置, 然后使用拇指来凸出, 并使索引抓手指返回到释放状态。 在 HoloLens (第一代) 上, 分流是最常见的辅助输入。

![将手指放在预备位置，然后点击或单击](images/readyandpress.jpg)<br>

HoloLens 2 上也提供了空中点击。 它已从原始版本中宽松。 几乎所有类型的 pinches 现在都受支持, 只要手直立并且仍保持。 这使用户更容易学习和执行手势。 这种新的 "air" 将通过相同的 API 替换旧的, 因此, 在重新编译 HoloLens 2 后, 现有应用程序将自动具有新行为。

### <a name="head-gaze-and-select-voice-command"></a>头部凝视和“选择”语音命令
语音命令是混合现实中的主要交互方法之一。 它提供一种非常强大的无人参与机制来控制系统。 可使用不同类型的语音交互模型：

- 执行单击传动或提交作为辅助输入的通用命令选择。
- 诸如关闭或使其变得更大的对象命令会执行, 并提交给操作作为辅助输入。
- 全局 commnads (如 "开始") 不需要目标。
- 像 Cortana 这样的对话用户界面或实体具有 AI 自然语言功能。
- 自定义命令

若要查找更多详细信息以及可用命令的 comprenhesive 列表以及如何使用它们, 请查看我们的[语音命令](voice-design.md)指南。


### <a name="head-gaze-and-hololens-clicker"></a>头部凝视和 HoloLens 遥控器
HoloLens Clicker 是专门为 HoloLens 构建的第一个外围设备。 它随附于 HoloLens (第一代) 开发版本。 通过 HoloLens Clicker, 用户可单击最小手动运动, 并提交为辅助输入。 HoloLens Clicker 使用蓝牙低功耗 (BTLE) 连接到 HoloLens (第一代) 或 HoloLens 2。

![HoloLens 遥控器](images/hololens-clicker-500px.jpg)<br>
*HoloLens 遥控器*

有关设备配对的详细信息和说明，请参阅[此处](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>头部凝视和 Xbox 无线控制器
Xbox 无线控制器使用 "A" 按钮执行单击传动作为辅助输入。 设备映射到一组默认操作，以帮助导航和控制系统。 如果要自定义控制器, 请使用 Xbox Accesories 应用程序配置 Xbox 无线控制器。

![Xbox 无线控制器](images/xboxcontroller.jpg)<br>
*Xbox 无线控制器*

[将 Xbox 控制器与电脑配对](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>头部凝视和 Xbox 自适应控制器
Xbox 自适应控制器主要用于满足移动性有限的游戏玩家的需求, 是一种统一的设备, 有助于使混合现实更易于访问。

Xbox 自适应控制器使用 "A" 按钮执行单击传动作为辅助输入。 设备映射到一组可帮助导航和控制系统的默认操作。 如果要自定义控制器, 请使用 Xbox Accesories 应用程序配置 Xbox 自适应控制器。

![Xbox 自适应控制器](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox 自适应控制器*

连接外部设备, 如交换机、按钮、装入和操纵杆, 以创建唯一的自定义控制器体验。 按钮、操纵杆和触发器输入由通过 3.5 mm 插座和 USB 端口连接的辅助设备控制。

![Xbox 自适应控制器端口](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox 自适应控制器端口*

[设备配对说明](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 网站上提供了更多信息</a>


## <a name="design-guidelines"></a>设计指南
> [!NOTE]
> [即将推出](index.md)有关凝视设计的更多指南。

## <a name="head-gaze-targeting"></a>头部凝视目标设定
所有交互的基础都是用户能够将想要与之交互的元素设定为目标，而无论使用何种输入模态。 在 Windows Mixed Reality 中，通常通过用户凝视来完成此操作。
为了使用户能够成功使用体验, 系统计算对用户意图的理解以及用户的实际意图必须尽可能接近。 按照系统正确解释用户目标操作的程度，满意度提高，性能提高。


## <a name="target-sizing-and-feedback"></a>目标大小调整和反馈
看起来矢量已经重复显示, 可用于精细定位, 但通常最适用于毛目标-获取稍大的目标。 在大多数情况下, 最小目标大小为1到1.5 度允许成功的用户操作, 尽管目标为3度, 但通常允许更快。 请注意，即使对于 3D 元素，用户设定为目标的尺寸实际上也是 2D 区域，3D 元素的投影即是可设定为目标的区域。 提供一些突出的提示, 指出某个元素处于 "活动" 状态 (用户以其为目标) 非常有帮助。 这可能包括处理方式 (如可见的 "悬停" 效果、音频突出显示或单击), 或通过元素清晰显示光标。

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*2 米远处的最佳目标大小*

![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-640px.jpg)<br>
*突出显示凝视目标对象的示例*

## <a name="target-placement"></a>目标位置
用户经常找不到在其视图字段中定位很高或极低的 UI 元素, 这就是他们对其主要关注点的关注点 (大约在眼睛上)。 将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。 考虑到用户在任何时候都倾向于关注一个相对较小的可视区域（注意力视锥大约为 10 度），通过将 UI 元素分组到在概念上相关的位置，可以在用户的视线通过某个区域时利用各项目之间的注意力链锁作用。 在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。

![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)<br>
*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*

## <a name="improving-targeting-behaviors"></a>改进目标设定行为
如果可以确定 (或大致了解) 针对某个内容的用户意向, 则在交互时接受接近的未命中尝试就是非常有帮助的。 下面是一些可在混合现实体验中结合使用的成功方法:

### <a name="head-gaze-stabilization-gravity-wells"></a>头部凝视防抖动（“重力井”）
这应该是最多或全部开启。 此方法可删除用户在查找和讲话行为上可能具有的移动的自然头和抖动。

### <a name="closest-link-algorithms"></a>最邻近链接算法
这些方法在交互内容稀少的区域效果最好。 如果很有可能确定用户尝试与之交互的概率很高, 则可以通过假定某些级别来补充其目标功能。

### <a name="backdating-and-postdating-actions"></a>Backdating 和 postdating 操作
此机制非常适合需要快速完成的任务。 当用户通过一系列的目标和激活设法使其进行迁移时, 有必要采取一些意向, 并允许错过的步骤来处理用户在点击点之前或之后稍微有针对性的目标 (50 毫秒之前/之后)rly 测试)。

### <a name="smoothing"></a>平滑处理
此机制对于路径移动非常有用, 因为自然移动特征会降低轻微的抖动和 wobble。 对路径运动进行平滑处理时, 按移动的大小和距离而不是一段时间来平滑。

### <a name="magnetism"></a>磁吸
此机制可被视为最近的链接算法的更通用版本, 即在目标位置绘制光标, 或者只是明显增加 hitboxes, 因为用户可以通过使用某些交互式布局知识来更好地利用这些目标方法用户意向。 这对于小型目标尤其有用。

### <a name="focus-stickiness"></a>焦点粘性
在确定要将焦点放到哪些附近的交互式元素时, 焦点将为当前聚焦的元素提供偏移。 当在两个元素之间的中间点处浮动时, 这有助于减少不稳定的焦点切换行为。


## <a name="composite-gestures"></a>复合手势

### <a name="air-tap"></a>隔空敲击
Air 攻攻敲击手势 (以及下面的其他手势) 仅对特定攻丝做出反应。 若要检测其他点击, 如菜单或抓住, 你的应用程序必须直接使用上面两个关键组件手势部分中所述的低级交互。

### <a name="tap-and-hold"></a>Tap and hold
按住是指保持隔空敲击手指向下的位置。 与 arm 移动 (如选取对象, 而不是激活对象或 mousedown 辅助交互, 如显示上下文菜单) 结合使用时, 点击和保持的组合允许使用各种更复杂的 "单击并拖动" 交互。
但在设计此手势时请务必小心，因为用户在做出任何扩展手势的过程都很可能放松手部姿势。

### <a name="manipulation"></a>操作
当您想让全息图对用户的手的变动做出回应1:1 时, 可以使用操作手势移动、调整或旋转全息图。 此类 1:1 运动可让用户进行实际绘制或绘画。
操作手势的初始定位应通过凝视或指向来完成。 点击并保持开始后, 对象的任何操作都将由手动移动处理, 使用户能够在操作时进行浏览。

### <a name="navigation"></a>导航
导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。 点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。 可以沿 X、Y 或 Z 轴移动，起点为 0，移动范围为 -1 到 1。
导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。

使用 rails 导航, 是指在该轴上达到特定阈值之前识别特定轴中的运动的能力。 当开发人员在应用程序中启用多个轴的移动时, 这种方法非常有用, 例如, 如果将应用程序配置为识别 X、Y 轴上的导航笔势, 同时还指定了具有 rails 的 X 轴。 在这种情况下, 系统将识别 x 轴上的手动运动, 只要它们保留在 X 轴上的假想导轨 (引导) 内, 也会在 Y 轴上进行手动移动。

在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。 这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。 用户可以通过选择按钮或口述 "< 滚动/拖动/缩放 > 工具", 来选择要执行的操作, 方法是在应用程序上方的工具间切换。

[有关复合手势的详细信息](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>手势识别器

使用手势识别的一个优点是, 只能为当前目标全息图可以接受的手势配置笔势识别器。 平台仅根据需要消除歧义以区分这些特定支持的手势。 通过这种方式, 仅支持 "分流" 的全息图可以接受按下和释放之间的任何时间长度, 而同时支持点击和按住的全息影像可以在保持时间阈值后将点击提升为保留。

## <a name="hand-recognition"></a>手部识别
HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。 当手处于就绪状态（手背朝向自己，食指向上）或按下状态（手背朝向自己，食指向下）时，HoloLens 可检测到手部。 当双手处于其他姿势时, HoloLens 将忽略 themz。
对于 HoloLens 检测到的每一种情况, 你可以访问其位置而无需方向和按下状态。 当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。

## <a name="gesture-frame"></a>手势范围
对于 HoloLens 上的手势, 手型必须在笔势框架内, 范围是笔势感应摄像机可以正确查看的范围, 从鼻子到 waist, 以及需要肩负之间。 用户需要在这一认知领域进行培训, 以实现操作的成功, 并为他们提供便利。 许多用户最初会假设该笔势帧必须在其视图中通过 HoloLens 显示, 并将其 uncomfortably, 以便进行交互。 使用 HoloLens Clicker 时, 不一定要将指针放在手势帧中。

特别是连续的手势时, 用户在移动全息对象时, 可能会有这样的风险: 将其指针移到手势帧外, 而在移动全息对象时, 还会失去预期结果。

应考虑以下三个事项：

- 手势帧存在和大致边界的用户教育。 这会在安装 HoloLens 期间进行。

- 当用户的手势接近或中断应用程序内的手势帧边界时, 通知用户, 使丢失的手势导致意外的结果。 研究显示了此类通知系统的重要质量。 在中心游标上, HoloLens shell 提供此类通知的很好的示例, 指示边界交叉的发生方向。

- 应尽可能避免穿过手势范围的边界。 通常, 这意味着应在边界停止笔势的结果, 而不是反转。 例如, 如果用户在房间内移动某个全息对象, 则在该笔势帧被破坏时, 移动应停止, 并且不会返回到开始点。 用户可能会遇到一些挫折, 但可能会更快地了解边界, 无需每次都重新启动其全部预期操作。


## <a name="see-also"></a>请参阅
* [使用手直接操作](direct-manipulation.md)
* [使用手指向和提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [头部凝视和停留](gaze-and-dwell.md)
* [语音命令](voice-design.md)





