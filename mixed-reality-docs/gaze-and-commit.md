---
title: 注视并提交
description: "\"注视并提交\" 输入模型的一般概述-使用目视或头输入。"
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合现实，注视，注视目标，交互，设计，眼睛跟踪，头跟踪
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441123"
---
# <a name="gaze-and-commit"></a>注视并提交

"_注视" 和 "提交_" 是一种基本的输入模型，它与使用鼠标的计算机进行交互的方式密切相关：_点 & 单击_。
在此页上，我们将介绍两种类型的目视输入（打印头和眼睛眼睛）以及不同类型的提交操作。 
_注视和提交_被视为具有间接操作的最大输入模型。
这意味着它最适用于与不在一起的全息内容交互。

混合现实耳机可以使用用户头部的位置和方向来确定其头向量。 你可以将其视为从用户两眼之间直指前方的激光。 这可粗略呈现出用户正查看的位置。 您的应用程序可以将此射线与虚拟或现实对象交叉，并在该位置绘制光标，以使用户了解当前的目标。

除了注视眼睛外，某些混合现实耳机（如 HoloLens 2）还包括可生成眼睛良好矢量的眼睛跟踪系统。 这可精细测量用户正在查看的位置。 在这两种情况下，注视都表示用户意向的重要信号。 系统更好地解释并预测用户的预期操作，提高用户满意度，提高性能。

下面是一些示例，说明混合现实开发人员如何从打印头或眼睛中获益：
* 您的应用程序可以在场景中与全息影像交叉，以确定用户注意的位置（更准确地说看注视）。
* 您的应用程序可以根据用户的 "注视" 通道手势和控制器按下，使用户能够无缝选择、激活、抓取、滚动或与全息影像交互。
* 您的应用程序可让用户在实际的表面上放置全息影像，方法是将其表面与空间映射网格进行交叉处理。
* 您的应用程序可以知道用户*不*在查找重要对象的方向时，这可能会导致您的应用程序将视觉和音频提示转换为该对象。

<br>


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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>头部凝视和提交</td>
        <td>✔️ 推荐</td>
        <td>✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</td>
        <td>➕ 备用选项</td>
    </tr>
         <tr>
        <td>眼睛凝视和提交</td>
        <td>❌ 不可用</td>
        <td>✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</td>
        <td>❌ 不可用</td>
    </tr>
</table>


## <a name="gaze"></a>凝视

### <a name="eye--or-head-gaze"></a>眼后看好了吗？
当面对问题时，需要考虑几个注意事项，无论你使用的是 "眼睛和提交" 还是 "良好和提交" 输入模型。 如果要开发沉浸式头戴式耳机或 HoloLens （第一代），则选择简单：打印头和提交。 如果你正在开发 HoloLens 2，则所做的选择会更难，因为了解其中每个选项的优点和难题非常重要。
在下表中，我们编译了一些广泛的专业人员和职业，以对比眼睛和眼睛的目标。 这从很大程度上来看，我们建议在此处了解各种混合现实中的眼睛目标：
* [Hololens 2 上的目视跟踪](eye-tracking.md)：在 hololens 2 上提供新的目视跟踪功能（包括一些开发人员指南）。 
* [目视的交互](eye-gaze-interaction.md)：计划使用目视跟踪作为输入时的设计注意事项和建议。

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>目视瞄准目标</strong></td>
        <td><strong>头-注视目标</strong></td>
    </tr>
    <tr>
        <td>Fast!</td>
        <td>比较</td>
    </tr>
    <tr>
        <td>低工作量（几乎所有必要的主体移动）</td>
        <td>可能是 fatiguing 的 discomfort （例如，颈部紧张）</td>
    </tr>
    <tr>
        <td>不需要游标，但建议使用微妙的反馈</td>
        <td>需要显示游标</td>
    </tr>
    <tr>
        <td>无平滑的眼睛运动-例如，不适用于绘图</td>
        <td>更多受控和显式</td>
    </tr>
    <tr>
        <td>对于非常小的目标（例如，小按钮或 weblinks）很难</td>
        <td>非常! 好的回退！</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

无论你使用的是眼睛还是目视，你的眼睛和提交输入模型都附带了不同的设计约束集，这将在[眼睛眼睛和提交](gaze-and-commit-eyes.md)和[提交](gaze-and-commit-head.md)文章中单独介绍。

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        对于 "注视"，大多数应用程序都应使用[游标](cursors.md)（或其他听觉/视觉指示）来让用户信任他们要与之交互的内容。 通常将此光标置于世界上，其中其打印头看起来先与一个对象（可能是全息图或真实表面）相交。<br>
        <br>
        对于眼睛，我们通常建议*不要*显示游标，因为这可能会使用户迅速变得杂乱。 相反，突出强调视觉对象目标或使用非常模糊的光标，以使用户与之交互的对象更有把握。 有关详细信息，请查看有关 HoloLens 2 上[基于目视的输入的设计指南](eye-tracking.md)。
    :::column-end:::
        :::column:::
       ![直观光标的示例以显示注视](images/cursor.jpg)<br>
       *图像：显示注视的视觉对象光标示例*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>提交
_在谈论看一看目标_的不同方法之后，让我们更深入地谈谈 "注视" 和 "_提交_" 中的_提交_部分。
以对象或 UI 元素为目标后，用户可以使用辅助输入交互或单击此元素。 这称为输入模型的提交步骤。 

支持以下提交方法：
- 空中攻攻形手势（即，在您自己的前方抬起，并将您的食指和拇指结合在一起）
- 说 _"选择"_ 或一个目标语音命令
- 在[HoloLens Clicker](hardware-accessories.md#hololens-clicker)上按单个按钮
- 按下 Xbox 游戏板上的 "A" 按钮
- 按 Xbox 自适应控制器上的 "A" 按钮

### <a name="gaze-and-air-tap-gesture"></a>注视和气攻敲击手势
隔空敲击是一种手部直立的点击手势。 若要执行分流，请将索引向下移动到准备好的位置，然后使用拇指来凸出，并使索引抓手指返回到释放状态。 在 HoloLens （第一代）上，分流是最常见的辅助输入。


:::row:::
    :::column:::
       在就绪位置 ![手指](images/readyandpress-ready.jpg)<br>
       **手指处于就绪位置**<br>
    :::column-end:::
    :::column:::
       ![按下手指以点击或单击](images/readyandpress-press.jpg)<br>
        **按下手指点击或单击**<br>
    :::column-end:::
:::row-end:::


HoloLens 2 上也提供了空中点击。 它已从原始版本中宽松。 几乎所有类型的 pinches 现在都受支持，只要手直立并且仍保持。 这使用户更容易学习和执行手势。 这种新的 "air" 将通过相同的 API 替换旧的，因此，在重新编译 HoloLens 2 后，现有应用程序将自动具有新行为。

<br>

---

### <a name="gaze-and-select-voice-command"></a>注视并单击 "选择" 语音命令
语音命令是混合现实中的主要交互方法之一。 它提供一种非常强大的无人参与机制来控制系统。 有不同类型的语音交互模型：

- 执行单击传动或提交作为辅助输入的一般 "Select" 命令。
- 对象命令（例如，"关闭" 或 "使其变大"）作为辅助输入执行并提交到操作。
- 全局命令（例如，"中转到开始"）不需要目标。
- 像 Cortana 这样的对话用户界面或实体具有 AI 自然语言功能。
- 自定义语音命令

若要了解更多详细信息以及可用语音命令的完整列表以及如何使用这些命令，请查看我们的[语音](voice-design.md)命令指南。

<br>

---


### <a name="gaze-and-hololens-clicker"></a>注视和 HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker 是专门为 HoloLens 构建的第一个外围设备。 它随附于 HoloLens （第一代）开发版本。 通过 HoloLens Clicker，用户可单击最小手动运动，并提交为辅助输入。 HoloLens Clicker 使用蓝牙低功耗（BTLE）连接到 HoloLens （第一代）或 HoloLens 2。<br>
        <br>
        [有关将设备配对的详细信息和说明](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *映像： HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>注视和 Xbox 无线控制器

:::row:::
    :::column:::
        Xbox 无线控制器使用 "A" 按钮执行单击传动作为辅助输入。 设备映射到一组可帮助导航和控制系统的默认操作。 如果要自定义控制器，请使用 Xbox 附件应用程序来配置 Xbox 无线控制器。<br>
        <br>
        [如何将 Xbox 控制器与电脑配对](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *映像： Xbox 无线控制器*
    :::column-end:::
        :::column:::
       ![Xbox 无线控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>注视和 Xbox 自适应控制器
Xbox 自适应控制器主要用于满足移动性有限的游戏玩家的需求，是一种统一的设备，有助于使混合现实更易于访问。

Xbox 自适应控制器使用 "A" 按钮执行单击传动作为辅助输入。 设备映射到一组可帮助导航和控制系统的默认操作。 如果要自定义控制器，请使用 Xbox 附件应用程序来配置 Xbox 自适应控制器。

![Xbox 自适应控制器](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox 自适应控制器*

连接外部设备，如交换机、按钮、装入和操纵杆，以创建唯一的自定义控制器体验。 按钮、操纵杆和触发器输入由通过 3.5 mm 插座和 USB 端口连接的辅助设备控制。

![Xbox 自适应控制器端口](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox 自适应控制器端口*

[设备配对说明](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 网站上提供了更多信息</a>

<br>

---

## <a name="composite-gestures"></a>复合手势

### <a name="air-tap"></a>隔空敲击
Air 攻攻敲击手势（以及下面的其他手势）仅对特定攻丝做出反应。 若要检测其他点击，如菜单或抓住，你的应用程序必须直接使用上面两个关键组件手势部分中所述的低级交互。

### <a name="tap-and-hold"></a>Tap and hold
按住是指保持隔空敲击手指向下的位置。 与 arm 移动（如选取对象，而不是激活对象或 mousedown 辅助交互，如显示上下文菜单）结合使用时，点击和保持的组合允许使用各种更复杂的 "单击并拖动" 交互。
但在设计此手势时请务必小心，因为用户在做出任何扩展手势的过程都很可能放松手部姿势。

### <a name="manipulation"></a>操作
当您想让全息图对用户的手的变动做出回应1:1 时，可以使用操作手势移动、调整或旋转全息图。 此类 1:1 运动可让用户进行实际绘制或绘画。
操作手势的初始定位应通过凝视或指向来完成。 点击并保持开始后，对象的任何操作都将由手动移动处理，使用户能够在操作时进行浏览。

### <a name="navigation"></a>导航
导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。 点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。 可以沿 X、Y 或 Z 轴移动，起点为 0，移动范围为 -1 到 1。
导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。

使用 rails 导航，是指在该轴上达到特定阈值之前识别特定轴中的运动的能力。 当开发人员在应用程序中启用多个轴的移动时，这种方法非常有用，例如，如果将应用程序配置为识别 X、Y 轴上的导航笔势，同时还指定了具有 rails 的 X 轴。 在这种情况下，系统将识别 x 轴上的手动运动，只要它们保留在 X 轴上的假想导轨（引导）内，也会在 Y 轴上进行手动移动。

在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。 这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。 用户可以通过选择按钮或口述 "< 滚动/拖动/缩放 > 工具"，来选择要执行的操作，方法是在应用程序上方的工具间切换。

[有关复合手势的详细信息](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>手势识别器

使用手势识别的一个优点是，只能为当前目标全息图可以接受的手势配置笔势识别器。 平台仅根据需要消除歧义以区分这些特定支持的手势。 通过这种方式，仅支持 "分流" 的全息图可以接受按下和释放之间的任何时间长度，而同时支持点击和按住的全息影像可以在保持时间阈值后将点击提升为保留。

## <a name="hand-recognition"></a>手部识别
HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。 当手处于就绪状态（手背朝向自己，食指向上）或按下状态（手背朝向自己，食指向下）时，HoloLens 可检测到手部。 当双手处于其他姿势时，HoloLens 会将其忽略。
对于 HoloLens 检测到的每一种情况，你可以访问其位置而无需方向和按下状态。 当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。

## <a name="gesture-frame"></a>手势范围
对于 HoloLens 上的手势，手型必须在笔势框架内，范围是笔势感应摄像机可以正确查看的范围，从鼻子到 waist，以及需要肩负之间。 用户需要在这一认知领域进行培训，以实现操作的成功，并为他们提供便利。 许多用户最初会假设该笔势帧必须在其视图中通过 HoloLens 显示，并将其 uncomfortably，以便进行交互。 使用 HoloLens Clicker 时，不一定要将指针放在手势帧中。

特别是连续的手势时，用户在移动全息对象时，可能会有这样的风险：将其指针移到手势帧外，而在移动全息对象时，还会失去预期结果。

应考虑以下三个事项：

- 手势帧存在和大致边界的用户教育。 这会在安装 HoloLens 期间进行。

- 当用户的手势接近或中断应用程序内的手势帧边界时，通知用户，使丢失的手势导致意外的结果。 研究显示了此类通知系统的重要质量。 在中心游标上，HoloLens shell 提供此类通知的很好的示例，指示边界交叉的发生方向。

- 应尽可能避免穿过手势范围的边界。 通常，这意味着应在边界停止笔势的结果，而不是反转。 例如，如果用户在房间内移动某个全息对象，则在该笔势帧被破坏时，移动应停止，并且不会返回到开始点。 用户可能会遇到一些挫折，但可能会更快地了解边界，无需每次都重新启动其全部预期操作。



## <a name="see-also"></a>另请参阅
* [基于目视的交互](eye-gaze-interaction.md)
* [HoloLens 2 上的目视跟踪](eye-tracking.md)
* [凝视和停留](gaze-and-dwell.md)
* [直接操作](direct-manipulation.md)
* [动手手势](gaze-and-commit.md#composite-gestures)
* [动手并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)

