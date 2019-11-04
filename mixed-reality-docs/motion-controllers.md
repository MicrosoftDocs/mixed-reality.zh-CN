---
title: 运动控制器
description: 混合现实运动控制器的详细信息。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器，运动控制器
ms.openlocfilehash: 84ebc6c0d7c63e58346b6ee9e565811bc40571b5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437856"
---
# <a name="motion-controllers"></a>运动控制器

:::row:::
    :::column:::
        运动控制器是允许用户在混合现实中采取措施的[硬件附件](hardware-accessories.md)。 动作控制器优于[手势](gaze-and-commit.md#composite-gestures)的优势在于，控制器在空间中有精确的位置，允许与数字对象进行精细的交互。 对于 Windows Mixed Reality 沉浸式耳机，运动控制器是用户在其世界中采取措施的主要方式。<br>
        <br>
        *映像： Windows Mixed Reality 运动控制器*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality 运动控制器](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>设备支持

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>具有</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
</tr>
<tr>
     <td>运动控制器</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>硬件详细信息

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality 动作控制器使用沉浸式耳机中的传感器提供精确而快速的移动性跟踪，这意味着无需在空间中的墙壁上安装硬件。 这些运动控制器将提供与 Windows Mixed Reality 沉浸式耳机相同的设置和可移植性。 我们的设备合作伙伴计划投放市场并在零售货架上销售这些控制器。

![了解控制器](images/controllerimage-750px.png)<br>
*了解控制器*

**功能**
* 光学跟踪
* 界限
* 抓取按钮
* 控制
* 触摸板

## <a name="setup"></a>“安装程序”

### <a name="before-you-begin"></a>开始之前

**你将需要：**
* 两个运动控制器的集合。
* 四个 AA 电池。
* 支持蓝牙4.0 的 PC。

**检查 Windows、Unity 和驱动程序更新**
* 若要进行混合现实开发，请参阅安装适用于 Windows、Unity 等的首选版本的[工具](install-the-tools.md)。
* 请确保具有最新的[耳机和运动控制器驱动程序](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。

### <a name="pairing-controllers"></a>配对控制器

可以使用 Windows 设置（如任何其他蓝牙设备）将运动控制器绑定到主机。

1. 将 2 AA 电池插入控制器背面。 暂时停止电池护盖。
2. 如果你使用的是外部 USB 蓝牙适配器而不是内置蓝牙收音机，请在继续操作之前查看[蓝牙最佳实践](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)。 对于带有内置收音机的桌面配置，请确保天线已连接。
3.  -> **设备**中打开 " **Windows 设置**" -> **将蓝牙或其他设备添加** -> **蓝牙**，并删除之前的 "运动控制器–右侧" 和 "运动控制器–左侧" 的任何实例。 查看列表底部的 "其他设备" 类别。
4. 选择 "**添加蓝牙或其他设备**"，并查看它是否开始发现蓝牙设备。
5. 按住控制器的 Windows 按钮，在 buzzes 后打开控制器。
6. 按住 "配对" 按钮（电池盒中的选项卡），直至 Led 开始闪烁。

:::row:::
    :::column:::
7. 等待 "运动控制器-左" 或 "运动控制器-右" 显示到列表的底部。 选择要配对。 控制器将在连接时振动一次。<br>
        <br>
        *Image：选择要配对的 "运动控制器";如果有多个实例，请从列表底部选择一个实例*
    :::column-end:::
        :::column:::
       ![选择要配对的运动控制器，如果有多个实例，请从显示的列表底部选择一个](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. 你会看到，控制器在 **"鼠标、键盘、& 笔" 类别**下的 "蓝牙设置" 中显示为 "**已连接**"。 此时，你可能会收到固件更新–请参阅[下一部分](motion-controllers.md#updating-controller-firmware)。
9. 重新连接电池盖子。
10. 对第二个控制器重复步骤1-9。

<br>

:::row:::
    :::column:::
        成功配对两个控制器后，设置在 **"鼠标、键盘、& 笔" 类别**下应如下所示 <br>
        <br>
        *图像：连接的运动控制器*
    :::column-end:::
        :::column:::
       ![已连接动作控制器](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

如果在配对后关闭控制器，则其状态将显示为配对。 如果控制器始终位于 "其他设备" 下，则类别配对可能仅部分完成，需要再次执行才能使控制器正常运行。

### <a name="updating-controller-firmware"></a>正在更新控制器固件

* 如果沉浸式耳机连接到您的 PC，并且有新的控制器固件可用，则该固件将在下一次打开时自动推送到运动控制器。 控制器固件更新通过一种在循环动作中照亮 LED 象限的模式来表示，并且需要1-2 分钟。


:::row:::
    :::column:::
* 固件更新完成后，控制器将重新启动并重新连接。 这两个控制器现在都应连接。 <br>
        <br>
        *映像：在蓝牙设置中连接的控制器*
    :::column-end:::
        :::column:::
       ![已连接控制器](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* 验证控制器是否正常工作：
    1. 启动**混合现实门户**，并输入混合现实主页。
    2. 移动控制器并验证跟踪、测试按钮并验证[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)是否正常工作。 如果没有，请检查[运动控制器故障排除](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="gazing-and-pointing"></a>Gazing 和指向

Windows Mixed Reality 支持两个用于交互、**注视和提交** **和提交的关键模型：**
* 使用 "**注视" 和 "提交**"，用户可通过其[注视](gaze-and-commit.md)来定位对象，并使用手接器、游戏板、clicker 或声音来选择对象。
* 通过**点和提交**，用户可以在目标对象上目标为支持指针的运动控制器，然后使用控制器的触发器选择对象。

支持使用运动控制器的应用也应尽可能启用注视驱动的交互，使用户能够选择他们使用的输入设备。

### <a name="managing-recoil-when-pointing"></a>在指向时管理 recoil

使用运动控制器进行指向和提交时，用户将使用控制器进行定位，然后通过拉取其触发器来采取措施。 请求触发器 vigorously 的用户最终可能会在其触发器拉取的末尾比预期的更高。

若要管理用户拉取触发器时可能发生的任何此类 recoil，则当触发器的模拟轴值超过0.0 时，应用程序可以对齐其目标射线。 然后，只要在短时间窗口中最后一次按下时，就可以使用该目标射线来执行操作，然后将触发器值达到1.0。 使用较高级别的[复合分流手势](gaze-and-commit.md#composite-gestures)时，Windows 将管理此目标光线捕获和超时。

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指针姿势

Windows Mixed Reality 支持多种形式的运动控制器，其中每个控制器的设计在用户的手位置和自然的 "前进" 方向上不同，应用程序在呈现控制器.

为了更好地表示这些控制器，可以针对每个交互源来调查两种类型的姿势，**手柄姿势**和**指针姿势**。

### <a name="grip-pose"></a>抓握姿势

**手柄姿势**表示由 HoloLens 检测到的掌托的位置，或包含运动控制器的掌托的位置。

在沉浸式耳机上，手柄姿势最适合用于呈现**用户的手**或**持有用户的对象**，例如剑或机枪。 可视化运动控制器时也使用手柄姿势，因为用于运动控制器的 Windows 提供的**呈现模型**使用手柄姿势作为原点和旋转中心。

手柄姿势的定义具体如下：
* **手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。 在 Windows Mixed Reality 运动控制器上，此位置通常与 "抓住" 按钮对齐。
* **手柄方向的右轴**：当你完全打开手形成一个平面的5指形姿势时，它是一种普通于手掌的光线（从左到右，从右手掌向前）
* **抓握方向的正向轴**：在部分合上（就像持有控制器一样），通过非拇指指的电子管来指向 "转发" 的射线。
* **手柄方向的上轴**：向右和向后定义隐含的上轴。

### <a name="pointer-pose"></a>指针姿势

**指针姿势**代表着控制器的末端。

系统提供的指针姿势最适合用于在**呈现控制器模型本身**时进行 raycast。 如果要渲染某个其他虚拟对象来替代控制器（如虚拟压力），则应使用该虚拟对象的最自然的光线，如沿应用定义的机枪模型的桶向下移动的射线。 由于用户可以看到虚拟对象，而不是物理控制器，因此，使用虚拟对象指向虚拟对象可能会更自然地使用应用。

## <a name="controller-tracking-state"></a>控制器跟踪状态

与耳机一样，Windows Mixed Reality 运动控制器不需要外部跟踪传感器的设置。 相反，控制器由耳机本身中的传感器跟踪。

如果用户将控制器移出耳机的视图，则在大多数情况下，Windows 将继续推断控制器位置，并将其提供给应用。 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。

此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。 许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>显式跟踪状态的推理

希望根据跟踪状态以不同方式对位置进行处理的应用可能会进一步检查控制器状态的属性，如 SourceLossRisk 和 PositionAccuracy：

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高准确度</b> </td><td style="background-color: green; color: white"> &lt; 1。0 </td><td style="background-color: green; color: white"> “高” </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精度（存在丢失的风险）</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> “高” </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>准确度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>无位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>



这些运动控制器跟踪状态的定义如下：
* **高准确度：** 尽管运动控制器位于耳机的视图中，但它通常会根据视觉对象跟踪提供高准确性位置。 请注意，在暂时离开耳机传感器时，移动控制器（如用户的另一方面）将继续根据控制器的惯性跟踪来返回较短的长时间（例如，用户）自动.
* **高精度（存在丢失的风险）：** 当用户将运动控制器移出耳机的视图边缘后，耳机不久就无法直观地跟踪控制器的位置。 此应用通过查看**SourceLossRisk**到1.0，来了解控制器何时到达此 FOV 边界。 此时，应用程序可以选择暂停需要稳定的高质量姿势流的控制器手势。
* **近似准确性：** 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。 此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。 许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。 输入要求更高的应用可通过检查**PositionAccuracy**属性，从**高**准确度到**接近**准确性，并为用户提供更宽松的 hitbox在此期间。
* **无位置：** 尽管控制器可以在很长时间内正常运行，但有时系统也知道，甚至在目前不会有任何意义。 例如，刚刚打开的控制器可能从未被直观观察，或者用户可能会关闭控制器，然后由其他人选取。 在这种情况下，系统不会提供应用程序的任何位置，并且**TryGetPosition**将返回 false。

## <a name="interactions-low-level-spatial-input"></a>交互：低级别空间输入

各种双手和运动控制器的核心交互是**选择**、**菜单**、**抓住**、**触摸板**、**操纵杆**和**Home**。
* **选择**"是"，这是用于激活全息影像的主要交互，其中包含一个按下的发布。 对于运动控制器，可以使用控制器的触发器执行 Select 按下。 通过[语音命令](voice-input.md)"select" 执行选择的其他方法。 可以在任何应用中使用相同的选择交互。 将选择作为鼠标单击的等效操作，即一次学习的通用操作，然后应用于所有应用。
* **菜单**是用于对对象进行操作的辅助交互，用于获取上下文菜单或执行其他辅助操作。 使用运动控制器，可以使用控制器的*菜单*按钮执行菜单操作。 （即其上带有汉堡 "menu" 图标的按钮）
* **抓住**，用户可以直接对对象执行操作，以便对其进行操作。 借助运动控制器，你可以通过紧密地挤压你的前来执行抓住操作。 运动控制器可能检测到带有抓取按钮、棕榈触发器或其他传感器的抓住。
* **触摸板**允许用户在运动控制器的触摸板图面上调整两个尺寸的操作，并通过单击触摸板上的 "向下" 来提交操作。 触摸板提供按下状态、接触状态和标准化的 XY 坐标。 X 和 Y 范围介于循环触摸板范围内的-1 到1之间，中心位于（0，0）。 对于 X，-1 位于左侧，1位于右侧。 对于 Y，-1 位于底部，1位于顶部。
* 使用**操纵杆**，用户可以通过在其循环范围内移动运动控制器的操纵杆，并通过单击操纵杆提交操作来调整两个尺寸的操作。 Thumbsticks 还提供按下状态和标准化的 XY 坐标。 X 和 Y 范围介于循环触摸板范围内的-1 到1之间，中心位于（0，0）。 对于 X，-1 位于左侧，1位于右侧。 对于 Y，-1 位于底部，1位于顶部。
* **Home**是一种特殊的系统操作，用于返回到 "开始" 菜单。 这类似于按键盘上的 Windows 键或 Xbox 控制器上的 Xbox 按钮。 可以通过按下动作控制器上的 "Windows" 按钮来回家。 请注意，你还可以通过说 "你好 Cortana，回家" 开始。 应用无法专门对 home 操作做出反应，因为这些操作由系统处理。

## <a name="composite-gestures-high-level-spatial-input"></a>复合手势：高级空间输入

可在一段时间内跟踪[手手势](gaze-and-commit.md#composite-gestures)和运动控制器以检测一组通用的高级 **[复合手势](gaze-and-commit.md#composite-gestures)** 。 这使您的应用程序能够检测高级**分流**、**定格**、**操作**和**导航**手势，无论用户最终使用的是手还是控制器。

## <a name="rendering-the-motion-controller-model"></a>呈现运动控制器模型

**3d 控制器模型**Windows 可让应用程序在系统中当前处于活动状态的每个运动控制器呈现模型。 通过让应用在运行时动态加载和表述这些系统提供的控制器模型，你可以确保你的应用程序与将来的任何控制器设计兼容。

这些呈现模型应呈现在控制器的**手柄姿势**上，因为模型的原点与物理世界中的这一点对齐。 如果要渲染控制器模型，则可能需要从**指针姿势**raycast 到场景，这表示该控制器的物理设计需要点，这表示用户自然需要点点。

有关如何在 Unity 中动态加载控制器模型的详细信息，请参阅在[unity 中呈现运动控制器模型](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity)部分。

**2d 控制器线条**图虽然我们建议将应用内控制器提示和命令附加到应用内控制器模型本身，但某些开发人员可能希望在平面 "教程" 或 "操作方法" UI 中使用运动控制器的2D 线条图表示形式。 对于这些开发人员，我们制作了 "png 运动控制器" 线条图片文件，其中黑色和白色均可用（右键单击以保存）。

![运动控制器线条图预览](images/motioncontrollers-black-preview-300px.png)

["" 中的整分辨率运动控制器线条艺术](images/motioncontrollers-white.png)
 
["" 中的整分辨率动作控制器线条图黑色 ""](images/motioncontrollers-black.png)

## <a name="faq"></a>常见问题解答

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>是否可以将运动控制器配对到多台电脑？

运动控制器支持与单台 PC 配对。 按照[动作控制器设置](motion-controllers.md#setup)来配对控制器的说明进行操作。

### <a name="how-do-i-update-motion-controller-firmware"></a>如何实现更新运动控制器固件？

运动控制器固件是耳机驱动程序的一部分，如果需要，它将在连接时自动更新。 固件更新通常需要1-2 分钟的时间，具体取决于蓝牙无线电和链接质量。 在极少数情况下，控制器固件更新可能需要长达10分钟的时间，这可能表示 Bluetooth 连接或无线电干扰较差。 请参阅[发烧指南中的蓝牙最佳实践](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)，以解决连接问题。 固件更新之后，控制器将重新启动并重新连接到主机计算机（你可能会注意到，Led 对于跟踪非常明亮）。 如果固件更新中断（例如，控制器断电），则在下次打开控制器时，将再次尝试该固件更新。

### <a name="how-i-can-check-battery-level"></a>如何检查电池电量级别？

在[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)中，您可以打开控制器以查看其在虚拟模型反面上的电量级别。 没有物理电池电量指标。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>是否可以使用这些不带耳机的控制器？ 仅针对游戏杆/触发器/etc 输入？

不适用于通用 Windows 应用程序。

## <a name="troubleshooting"></a>“疑难解答”

请参阅发烧指南中的[运动控制器故障排除](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="filing-motion-controller-feedbackbugs"></a>存档运动控制器反馈/bug

使用 "Mixed Reality-> 输入" 类别在反馈中心[向我们提供反馈](give-us-feedback.md)。

## <a name="see-also"></a>另请参阅
* [Unity 中的手势和运动控制器](gestures-and-motion-controllers-in-unity.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [手势](gaze-and-commit.md#composite-gestures)
* [MR 输入213：运动控制器](mixed-reality-213.md)
* [发烧本指南： Windows Mixed Reality 主页](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [发烧本指南：在 Windows Mixed Reality 中使用游戏 & 应用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [内部输出跟踪的工作原理](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
