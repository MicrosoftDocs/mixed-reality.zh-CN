---
title: 运动控制器
description: 混合现实运动控制器的详细信息。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器，motion 控制器
ms.openlocfilehash: fc6b0dcf7f338224af9ea9bc59e07187c33adda2
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024551"
---
# <a name="motion-controllers"></a>运动控制器

运动控制器[硬件附件](hardware-accessories.md)，可让用户在混合现实中采取措施。 通过动作控制器的一个优点[手势](gestures.md)是控制器有空间中的精确位置允许使用数字对象能够进行细化管理交互。 有关 Windows Mixed Reality 沉浸式耳机，motion 控制器是用户将他们的世界中执行操作的主要方法。

![Windows Mixed Reality 运动控制器](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>设备支持

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>功能</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
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

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality 运动控制器提供了在沉浸式头戴式耳机，这意味着无需安装在你的空间中的墙上的硬件中使用传感器在字段的视图中移动的精确且高度可响应的跟踪。 这些动作控制器将提供安装程序和可移植性作为 Windows Mixed Reality 沉浸式耳机一样的轻松。 设备合作伙伴计划营销和销售此假日零售书架上的这些控制器。

![了解你的控制器](images/controllerimage-750px.png)<br>
*了解你的控制器*

**功能：**
* 光学跟踪
* 触发器
* 获取按钮
* 摇杆
* 触摸板

## <a name="setup"></a>安装

### <a name="before-you-begin"></a>开始之前

**你将需要：**
* 一组两个动作控制器。
* 四个 AA 电池。
* PC 蓝牙 4.0 的支持。

**检查 Windows、 Unity 和驱动程序更新**
* 请访问[安装的工具](install-the-tools.md)Windows，Unity 中，首选版本等进行混合的现实开发。
* 请确保你具有的最新[耳机和动作控制器驱动程序](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。

### <a name="pairing-controllers"></a>配对控制器

运动控制器可以与主机电脑绑定使用像任何其他蓝牙设备的 Windows 设置。

1. 插入控制器的后 2 AA 电池。 现在应将关闭电池盖。
2. 如果您使用外部 USB 蓝牙适配器而不内置的蓝牙无线功能，请查看[蓝牙最佳实践](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)继续操作之前。 与内置无线电收发器的桌面配置，请确保天线连接。
3. 打开**Windows 设置** -> **设备** -> **添加 Bluetooth 打印机或其他设备** -> **蓝牙**并删除"运动控制器-右侧"和"运动控制器 – 左"的任何早期实例。 另请查看其他设备类别，它位于列表的底部。
4. 选择**添加 Bluetooth 打印机或其他设备**并查看其开始发现蓝牙设备。
5. 按住控制器的 Windows 按钮，以打开控制器，一次将其释放 buzzes。
6. 按下并保持配对按钮 （电池隔离舱中的选项卡），直到 Led 开始触发。
7. 等待"运动控制器-左"或"运动控制器-右侧"若要向列表的底部显示。 选择对此选项。 连接时，将一次振动控制器。

   ![如果多个实例从中选择一个显示底部的列表，请选择运动控制器进行配对，](images/450px-bluetooth-add-a-device-300px.png)<br>
   *选择"运动 controller"到对;如果有多个实例，从列表的底部选择一个*
   
8. 你将看到显示在下的蓝牙设置控制器 **"鼠标、 键盘和笔"类别**作为**已连接**。 此时，你可能会收到固件更新 – 请参阅[下一节](motion-controllers.md#updating-controller-firmware)。
9. 重新附加电池盖。
10. 对第二个控制器重复步骤 1-9。

已成功对这两个控制器之后, 您的设置应如下所示下 **"鼠标、 键盘和笔"类别** 

   ![运动控制器连接](images/450px-motion-controller-connected-300px.png)<br>
   *运动控制器连接*

如果控制器关闭配对后，其状态将显示为成对。 如果控制器使其保持永久在"其他设备"类别配对可能已仅部分完成并需要重新执行获取控制器的功能。

### <a name="updating-controller-firmware"></a>更新控制器固件

* 如果沉浸式头戴式耳机连接到您的 PC，并且新控制器固件可用，固件将推送到运动控制器自动的下次要开启。 控制器固件更新所指示的循环的动态、 人大开眼界 LED 象限的模式，需要 1-2 分钟的时间。
* 固件更新完成后，将重新启动并重新连接的所有控制器。 现在应已连接这两个控制器。 
    
    ![连接控制器](images/cyk-connected-300px.jpg)<br>
    *控制器中的蓝牙设置连接*

* 正确验证您的控制器工作：
    1. 启动**混合现实门户**并输入你的混合现实主页。
    2. 将移动你的控制器和验证跟踪测试按钮，并验证[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)工作原理。 如果不这样做，请学习[动作控制器故障排除](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="gazing-and-pointing"></a>观望和指向

Windows Mixed Reality 进行交互，支持两个主要模型**注视并提交**并**点并提交**:
* 与**注视并提交**，用户为目标的对象及其[注视](gaze.md)，然后选择具有手动分流点以无线方式、 游戏板、 clicker 或他们的语音的对象。
* 与**点，并提交**，用户可以在目标对象的支持指向的运动控制器为目标，然后选择具有控制器的触发器的对象。

此外应指向与运动控制器支持的应用程序实现的视线移动驱动交互，在可能的情况，以便用户在如何选择输入他们使用的设备。

### <a name="managing-recoil-when-pointing"></a>当指向管理 recoil

当使用运动控制器可以指向和提交时，用户将用控制器为目标并采取操作，方法是提取它的触发器。 请求触发器积极的用户可能最终会比它们有意瞄准其触发器请求结束时更高版本的控制器。

若要管理的用户请求触发器时，可能发生的任何此类 recoil，您的应用程序可以在触发器的模拟的轴值高于 0.0 对齐其目标 ray。 然后可以执行使用该目标 ray 几个帧更高版本后触发器值达到 1.0，只要最终按在短时间窗口内发生的操作。 当使用更高级别的[复合手势](gestures.md#composite-gestures)，Windows 将管理此为您面向 ray 捕获和超时。

## <a name="grip-pose-vs-pointing-pose"></a>与指针姿势手柄姿势

Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。

若要更好地表示这些控制器，有两种类型的可以为每个交互源，调查的带来**手柄姿势**并**指针姿势**。

### <a name="grip-pose"></a>手柄姿势

**手柄姿势**表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。

在沉浸式耳机手柄姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。 作为可视化的运动控制器，也会使用手柄姿势**可呈现模型**提供由 Windows 动作控制器使用手柄姿势作为其起点和旋转中心。

手柄姿势定义具体而言，如下所示：
* **抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。 Windows Mixed Reality 动作在控制器上，此位置通常与掌握按钮对齐。
* **抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）
* **抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。
* **抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。

### <a name="pointer-pose"></a>指针姿势

**指针姿势**表示转发指向控制器的提示。

你是，到 raycast 最合适使用系统提供的指针姿势**呈现控制器模型本身**。 当您呈现某些其他虚拟对象代替控制器，例如虚拟手段，您应点与最自然会为该虚拟对象，如应用程序定义枪模型的笔杆都沿着一条射线。 由于用户可以看到虚拟对象，而不是物理的控制器，指向与虚拟对象可能会使那些使用您的应用程序更加自然。

## <a name="controller-tracking-state"></a>控制器跟踪状态

耳机，如 Windows Mixed Reality 运动控制器不需要外部跟踪传感器的任何设置。 相反，控制器会跟踪耳机本身中的传感器。

如果用户移出耳机的字段的视图控制器，在大多数情况下 Windows 会继续推断控制器位置并将它们提供给应用程序。 当控制器已失去时长不足，控制器的位置将会断开与近似准确性位置可视化跟踪。

此时，系统会将主体锁定的用户，跟踪用户的位置，随着对象移动，同时仍提供的控制器，则返回 true 方向使用其内部方向传感器到控制器。 使用控制器指向并激活用户界面元素的许多应用程序可以无需用户注意到正常运行中近似的准确性。

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>有关显式跟踪状态的推论

想要将基于跟踪状态以不同方式的位置的应用程序可能会更进一步并检查控制器的状态，例如 SourceLossRisk 和 PositionAccuracy 上的属性：

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>（在丢失的风险） 的高精度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>近似值的准确性</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>不到位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>



这些动作控制器跟踪状态定义，如下所示：
* **高精度：** 在 motion 控制器耳机的字段的视图中时，它通常将提供高准确性位置，基于可视化跟踪。 请注意，移动控制器的暂时离开视图的字段或暂时不可用遮盖耳机传感器 (例如，用户的另一只手) 将继续返回高准确性带来基于控制器的惯性跟踪在短时间本身。
* **（在丢失的风险） 的高精度：** 当用户移动的运动控制器超过耳机的视角的边缘时，耳机很快将无法直观地跟踪控制器的位置。 应用已知道控制器当通过查看达到此 FOV 边界**SourceLossRisk**达到 1.0。 此时，应用程序可以选择暂停需要稳定的高质量带来的控制器手势。
* **近似值的准确性：** 当控制器已失去时长不足，控制器的位置将会断开与近似准确性位置可视化跟踪。 此时，系统会将主体锁定的用户，跟踪用户的位置，随着对象移动，同时仍提供的控制器，则返回 true 方向使用其内部方向传感器到控制器。 控制器用于指向并激活用户界面元素的许多应用程序可以作为正常段中近似的准确性在运行而无需用户注意到。 具有较输入要求的应用可以选择感应从此下降**高**精度为**近似**准确性通过检查**PositionAccuracy**属性，用于可以向用户授予在允许较大 hitbox 屏外目标在此期间的示例。
* **不到位置：** 控制器可以长时间运行近似值的准确性，而有时系统就知道目前没有意义甚至正文锁定的位置。 例如，只需开启控制器可能永远不会观察到以可视方式，或者用户可能放下一个控制器，然后选取其他人。 在这些情况下，系统将不会提供到应用程序中的任意位置并**TryGetPosition**将返回 false。

## <a name="interactions-low-level-spatial-input"></a>交互：低级别的空间输入

双手和动作控制器跨核心交互都会**选择**，**菜单**，**掌握**，**触摸板**， **摇杆**，并**主页**。
* **选择**是主要的交互以激活包含一个版本后跟按一张全息图。 对于动画控制器，您执行选择按下的某个使用控制器的触发器。 执行 Select 的其他方法是通过说话[语音命令](voice-input.md)"Select"。 任何应用程序中，可以使用相同的选择交互。 将选择视为等效于鼠标单击，了解一次，然后应用跨所有应用的通用操作。
* **菜单**是对一个对象，用于提取一个上下文菜单或其他一些辅助操作的辅助交互。 使用 motion 控制器可能需要使用的控制器菜单操作*菜单*按钮。 （即与它的汉堡"菜单"图标的按钮）
* **掌握**是用户可以直接在其准备对其进行处理的对象上执行操作的方式。 使用 motion 控制器，可以通过紧密挤压在前执行掌握现有操作。 运动控制器可能检测到与随取即行按钮、 palm 触发器或其他传感器掌握。
* **触摸板**允许用户调整面沿两个维度中的动作控制器的触摸板的操作的触摸板上单击向下执行该操作。 触摸板提供按下的状态、 接触的状态和规范化的 XY 坐标。 X 和 Y 从-1 到 1 范围内的循环触摸板，通过在 center 范围 （0，0）。 适用于 X，在左侧是-1 和 1 位于右侧。 为 Y，底部是-1，1 是在最前面。
* **摇杆**允许用户通过移动其循环范围内的动作控制器摇杆调整两个维度中的操作由摇杆上单击向下执行该操作。 Thumbsticks 还提供按下的状态，并且规范化 XY 坐标。 X 和 Y 从-1 到 1 范围内的循环触摸板，通过在 center 范围 （0，0）。 适用于 X，在左侧是-1 和 1 位于右侧。 为 Y，底部是-1，1 是在最前面。
* **主页**是一种特殊的系统操作，用于返回到开始菜单。 它将类似于键盘或 Xbox 控制器上的 Xbox 按钮上按 Windows 键。 您可以通过按运动控制器上的 Windows 按钮主页转。 请注意，您可以也始终返回到开始通过说"你好，小娜，转到主页"。 随着这些参数由系统进行处理，应用无法专门针对主操作做出响应。

## <a name="composite-gestures-high-level-spatial-input"></a>复合手势：高级空间输入

这两 [另一方面手势](gestures.md) 和运动控制器可以跟踪随时间来检测常见套高级别的 **[复合手势](gestures.md#composite-gestures)** 。 这让你的应用来检测高级**点击**，**保存**，**操作**并**导航**笔势，是否使用用户最终手或控制器。

## <a name="rendering-the-motion-controller-model"></a>呈现运动控制器模型

**3D 控制器模型**Windows 将提供给应用的每个运动控制器可呈现模型系统中当前处于活动状态。 通过让您的应用程序动态加载并清楚地说明这些系统提供的控制器模型在运行时，可以确保您的应用程序是向前兼容到任何未来控制器设计。

这些可呈现模型应全部呈现在**手柄姿势**的控制器，该模型的原点与现实生活中此点。 如果呈现的控制器模型，您可能然后希望 raycast 到从您的场景**指针姿势**，它表示的射线沿其用户自然希望要指向，提供该控制器的物理设计。

有关如何加载动态在 Unity 中的控制器模型的详细信息，请参阅[呈现在 Unity 中的动作控制器模型](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity)部分。

**2D 控制器艺术线条**虽然我们建议将应用程序内控制器的提示和命令附加到应用程序内控制器模型本身，一些开发人员可能希望使用平面"教程"或"操作指南"中的 2D 行画面的运动控制器的表示形式用户界面。 对于这些开发人员，我们做出了.png 运动控制器行画文件形式提供下面这两个黑色和白色 （右键单击可以保存）。

![运动控制器艺术线条的预览](images/motioncontrollers-black-preview-300px.png)

 [高分辨率运动控制器行中的画面 '' 白色 ' '](images/motioncontrollers-white.png)
 
 [高分辨率运动控制器行中的画面 '' 黑色 ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>常见问题

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>我对 motion 到多台 Pc 的控制器？

运动控制器都支持具有一台 PC 配对。 按说明[动作控制器安装](motion-controllers.md#setup)配对，你的控制器。

### <a name="how-do-i-update-motion-controller-firmware"></a>如何更新运动控制器固件？

运动控制器固件是耳机驱动程序的一部分，将会自动更新连接上必要。 固件更新通常需要花费 1-2 分钟，具体取决于 Bluetooth 无线电和链接质量。 在极少数情况下，控制器固件更新可能需要最多 10 分钟，这可以表示蓝牙连接质量不佳或无线电干扰。 请参阅[蓝牙酷爱钻研技术指南中的最佳实践](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)若要排查连接问题。 固件更新后，控制器将重新启动并重新连接到主机 （您可能注意到转跟踪片光明的 Led） 的 PC。 如果中断固件更新 （例如，控制器停止电源供电），它将在下一步控制器开机的时再试它。

### <a name="how-i-can-check-battery-level"></a>如何检查电池电量水平？

在中[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)，你可以打开你的控制器，虚拟模型的反向端看到其电池剩余电量。 没有物理电池电量级别的指示器。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>您可以使用没有头戴式耳机这些控制器？ 只需为游戏杆/触发器/等的输入？

不适用于通用 Windows 应用程序。

## <a name="troubleshooting"></a>疑难解答

请参阅[动作控制器故障排除](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)酷爱钻研技术指南中。

## <a name="filing-motion-controller-feedbackbugs"></a>归档运动控制器反馈/bug

[向我们提供反馈](give-us-feedback.md)在反馈中心，使用"混合的现实-> 输入"类别。

## <a name="see-also"></a>请参阅
* [Unity 中的手势和运动控制器](gestures-and-motion-controllers-in-unity.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [手势](gestures.md)
* [MR 输入 213：运动控制器](mixed-reality-213.md)
* [他酷爱钻研技术的指南：你的主 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [他酷爱钻研技术的指南：在 Windows 混合现实中使用游戏和应用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [内部扩展跟踪的工作原理](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
