---
title: 笔势
description: 手势允许用户在混合现实中采取措施。
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的现实，手势，交互，设计
ms.openlocfilehash: afebefddfd620b4697b86616e8ecc930b271dca2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590107"
---
# <a name="gestures"></a>笔势

手势允许混合现实中的用户采取的措施。 交互基于**注视**到目标和**手势**或**语音**在已针对任何元素上进行操作。 手势互补并不提供空间，精确位置而带来 HoloLens 和立即与内容交互的简单起见，用户可以开始工作而无需任何其他附件。

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> 笔势</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> 明确的手</td><td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

## <a name="gaze-and-commit"></a>提供注视提交

若要执行的操作，请将手势使用[头的视线移动](gaze.md)作为目标的机制。 组合**注视**并**敲击**手势导致**注视提交**交互。 为提供注视提交的替代方法是**点提交**，通过已启用[动作控制器](motion-controllers.md)。 在 HoloLens 运行的应用程序只需支持的视线移动提交，因为 HoloLens 不支持动态控制器。 HoloLens 和沉浸式耳机运行的应用应支持同时提供注视驱动和指向驱动交互，让他们使用哪些输入设备中的用户进行选择。

## <a name="the-two-core-gestures-of-hololens"></a>两个核心的 HoloLens 的手势

HoloLens 当前识别两个核心组件手势-**敲击**并**布隆**。 这些两个核心交互是一名开发人员可以访问的空间输入数据的最低级别。 它们形成各种可能的用户操作的基础。

### <a name="air-tap"></a>敲击

敲击是与手持设备竖直的情况下，类似于鼠标单击的点击手势，或选择。 这用于大多数 HoloLens 体验中等效于"单击"上 UI 元素后面向其与[注视](gaze.md)。 它是一种通用操作，了解一次，然后应用跨所有应用。 若要执行选择的其他方法是通过按一个按钮上[HoloLens Clicker](hardware-accessories.md#hololens-clicker)或通过说话语音命令的"Select"。

![对于 HoloLens 上的手势的就绪状态](images/image9.png)<br>
*有关在 HoloLens 上敲击的就绪状态。*

空敲击是离散的手势。 选择已完成或不是，是一项操作，或不所采取的一种体验。 很有可能，但不而无需某种特定用途，建议从主要组件 （例如双点击手势以不同于单点击才有意义） 的组合创建其他离散手势。

![在准备好的位置，然后单击或点击动作手指](images/readyandpress.jpg)<br>
*如何执行敲击：引发食指到准备就绪的位置、 按手指下点击或选择，然后将其备份以释放。*

### <a name="bloom"></a>布隆

布隆是"home"手势，它保留供的单独。 它是一个特殊的系统操作，可用于返回到开始菜单。 它相当于键盘或 Xbox 控制器上的 Xbox 按钮上按 Windows 键。 用户可以使用任一工具。

![布隆手势 HoloLens 上](images/image10-640px.png)

为在 HoloLens 上的布隆手势，保留您的手，一起棕，与您能够轻松利用。 然后，打开您的手。 请注意，您可以也始终返回到开始通过说"你好，小娜，转到主页"。 随着这些参数由系统进行处理，应用将专门针对家庭的操作，不能做出响应。

![布隆手势](images/bloom-giphy.gif)<br>
*如何在 HoloLens 上执行布隆手势。*

## <a name="composite-gestures"></a>复合手势

应用程序可以识别多个不仅仅是单个的分流点。 通过组合点击保存和发布通过的手形图标移动，可以执行更复杂的复合手势。 低级别空间中的输入数据 （敲击和布隆） 的开发人员有权访问上生成这些复合或高级手势。

<table>
<tr>
<th> 复合手势</th><th> 如何将应用</th>
</tr><tr>
<td>敲击</td><td>以无线方式点击手势 （以及其他手势下面） 只对特定点击作出反应。 若要检测其他分流点，如菜单或掌握，您的应用程序必须直接使用上述两个关键组件手势部分中所述的较低级别交互。</td>
</tr><tr>
<td>Tap and hold</td><td><p>保留只需维护敲击的向下指位置。 以无线方式 tap 和 hold 相结合使各种更复杂&quot;单击并拖动&quot;与结合使用时交互的 arm 如而不是在激活的对象中选取的移动或&quot;mousedown&quot;辅助的交互，如显示上下文菜单。</p><p>时，此笔势但是，为用户设计可能很容易出现的任何扩展手势过程放宽其手 postures，应使用警告。</p></td>
</tr><tr>
<td>操作</td><td><p>操作手势可用于移动、 调整大小或旋转一张全息图时所需的全息图做出反应 1:1 到用户&#39;s 手动移动。 此类 1:1 移动的一个用途是允许用户绘制或绘制世界中。</p><p>应通过的视线移动或指向操作手势的初始目标。 一旦点击并按住启动，该对象的任何操作然后处理手动移动，则释放要一下，尽管它们操作的用户。</p></td>
</tr><tr>
<td>导航</td><td><p>导航笔势操作如虚拟游戏杆和可用于导航的 UI 小组件，如径向菜单。 点击并按住启动手势，然后将移动您的手规范化 3D 多维数据集，以按下了初始中心内。 为 1，其中 0 表示起始点，可以从值-1 移动您的手沿 X、 Y 或 Z 轴。</p><p>导航可以用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标中键，然后向上和向下移动鼠标滚动 2D UI。</p><p>使用 rails 导航是指识别中某轴移动，直到该轴上达到特定阈值的能力。 启用多个轴中的移动后的应用程序中由开发人员，例如，此操作才有用，如果应用程序配置为识别跨 X，Y 轴的导航操作但还指定 X 轴使用 rails。 在这种情况下系统将在 X 轴的手移动，只要它们仍保持在假想 rails （指南） 在 X 轴，如果识别手动移动，也会发生 Y 轴。</p><p>在 2D 应用程序，用户可以使用垂直导航笔势滚动、 缩放，或拖动在应用程序。 这会注入到应用，以模拟相同类型的触摸手势的虚拟根手指收尾工作了。 用户可以选择何种操作的应用，通过选择按钮或说上方的滚动条上的工具之间切换会发生&#39;&lt;滚动/拖/缩放&gt;工具&#39;。</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>笔势识别器

使用手势识别的一个好处是，您可以配置仅用于当前目标全息图可以接受的手势的手势识别程序。 该平台将执行仅消除二义性要区分这些特定的受支持的手势。 这样一来，只需支持敲击一张全息图可以接受任意长度的按下和释放之间的时间，一张全息图时支持同时点击并按住可升级到保留点击后保留时间阈值。

## <a name="hand-recognition"></a>手动识别

HoloLens 识别手势通过跟踪的一个或两个手中可看到设备的位置。 HoloLens 时它们中任何一种是看到了手**就绪状态**（背面手形图标索引手指您朝上） 或**按下状态**（背面食指您朝下手形）。 其他带来手中时，HoloLens 将忽略它们。

对于每个指针的 HoloLens 检测，可以访问它 （不带方向） 的位置和其按下的状态。 当手形图标接近手势帧的边缘时，你要还提供方向矢量，让他们知道如何移动其手，若要获取其返回 HoloLens 可以看到它可以向用户显示。

## <a name="gesture-frame"></a>手势帧

对于 HoloLens 的手势，手形图标必须是"手势在范围内"，（非常大致从鼻子到处理，以及在了肩膀之间） 手势感知照相机可以适当地看到某个范围内。 用户需要在此区域中 （许多用户最初假定手势框架必须在内通过 HoloLens，其视图和其手臂 uncomfortably 存放以进行交互） 的识别操作的成功和其自己舒适的训练。 在使用 HoloLens Clicker，手不需要为手势范围内。

在连续手势的情况下特别是，会出现风险移动中 （例如移动某些 holographic 对象） 时的中间笔势，笔势帧之外太多的事情并丢失它们的预期的结果的用户。

有三个您应考虑的事项：
* 手势帧存在并近似边界 （这教给 HoloLens 安装过程中） 上的用户培训。
* 当其手势是接近最大/重大手势帧边界内应用程序，不需要的结果都将导致丢失的手势程度时通知用户。 研究显示的此类通知系统的关键质量和 HoloLens shell 提供了此类型的通知 （视觉对象，指示的方向跨越正在进行中的边界对中央游标） 的一个很好示例。
* 应尽量减少中断手势帧边界的后果。 一般情况下，这意味着应停止在边界，但不是会反转手势的结果。 例如，如果用户在一个房间跨移动某些 holographic 对象，移动应停止时手势帧被破坏，但**不**返回到起始点。 用户可能会遇到一些挫折然后，但可能更快地了解边界，而无需每次重新启动其完整的预期的操作。

## <a name="see-also"></a>请参阅
* [目标的视线移动](gaze-targeting.md)
* [语音设计](voice-design.md)
* [MR 输入 211:手势](holograms-211.md)
* [手势和 Unity 中的动作控制器](gestures-and-motion-controllers-in-unity.md)
* [提供注视、 手势和 DirectX 中的动作控制器](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [运动控制器](motion-controllers.md)
