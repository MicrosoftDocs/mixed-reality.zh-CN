---
title: 农历模块
description: LunarModule 是来自 Microsoft 的混合现实设计实验室的开放源代码示例应用。 与此项目中，可以了解如何扩展了手跟踪 Hololens 的基本手势和 Xbox 控制器输入、 创建对象，它是被动的做法到图面上映射和平面查找和实施简单的菜单系统。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实，示例应用程序，设计，HoloLens 的 Windows
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592482"
---
# <a name="lunar-module"></a>农历模块

>[!NOTE]
>本文讨论了我们已在中创建一个探索示例[混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)，其中我们共享有关我们的知识和建议的混合现实应用程序开发。 当我们进行新的发现，我们与设计相关文章和代码将发展。

[农历模块](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)是来自 Microsoft 的混合现实设计实验室的开放源代码示例应用。 与此项目中，可以了解如何扩展了手跟踪 Hololens 的基本手势和 Xbox 控制器输入、 创建对象，它是被动的做法到图面上映射和平面查找和实施简单的菜单系统。 所有项目的组件都可在自己的混合的现实应用体验中使用。

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>有关 Windows Mixed Reality 反思经典体验

空气中的高向上，小船 Apollo 模块使人联想到系统地调查交错的地形下面。 无所畏惧的试验，检测适合登录区域。 下降总有成效，但幸运的是，这一过程变得很多时候之前...

![Atari 的 1979年阴历 Lander 从原始接口](images/640px-atari-lunar-lander.png)<br>
*Atari 的 1979年阴历 Lander 从原始接口*

[阴历 Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game))是拱廊经典播放器尝试试验全收 lander 到阴历地形平面位置上。 在二十世纪七十年代出生的任何人都具有最有可能花费小时中拱廊的粘附到从天空直线下降此向量发货自己眼。 当播放器导航所需的登录区域向其发运地形扩展，以显示详细越来越多的信息。 成功意味着在水平和垂直速度的安全阈值内的登录。 花费的时间登录，以及剩余燃油，基于登录区域的大小乘以得分。

游戏玩法，除了游戏的拱廊纪元将不断创新的控制方案。 从最简单的 4 向游戏杆和按钮配置 (图标所示[Pac Man](https://en.wikipedia.org/wiki/Pac-Man)) 到年代末和 00 秒 （如那些高尔夫模拟器和 rail 射击游戏中） 中所示的高度特定、 最复杂方案。 阴历 Lander 计算机中使用的输入的方案有两个原因是特别有趣： 找到的吸引力和深入探讨。

![Atari 的阴历 Lander 拱廊控制台](images/atariconsole.png)<br>
*Atari 的阴历 Lander 拱廊控制台*

为何 Atari 和许多其他游戏公司决定重新考虑输入？

最新、 flashiest 机器将自然地很逐步拱廊儿童。 但阴历 Lander 功能新颖的输入的修工的众包从尤为突出。

阴历 Lander 用于旋转左侧和右侧随附了两个按钮和一个**主旨是杆**控制的飞船生成一些咄咄逼人数量。 此级别为用户提供一定程度的正则游戏杆不能提供的注意技巧。 它也是恰好是普遍适用于现代航空考核中心的组件。 Atari 想阴历 Lander 以可访问这个的感觉，它们实际上试验农历模块中的用户。 此概念称为**触觉浸入式**。

触觉浸入式是传感器反馈执行重复操作的体验。 在这种情况下，重复操作的调整的限制级别和轮换其中眼睛看到和我们的耳朵听到，可帮助连接到的飞船登陆全收的图面上操作的播放机。 这一概念可以绑定到"流。"的心理概念 如果用户是完全在任务中具有适当混合使用质询和奖励，吸收或更简单地说，它们是"区域中。"

可以说，深入探讨混合现实中的最重要类型是空间浸入式。 混合现实的全部意义是欺骗自己认为这些现实世界中存在数字对象。 我们要在我们周围的环境，在空间上沉浸在整个环境并体验中合成全息。 这并不意味着我们无法仍会利用其他类型的深入探讨在我们的经验就像 Atari 一样在阴历 Lander 触觉浸入式。

## <a name="designing-with-immersion"></a>使用浸入式设计

我们如何可能用于触觉浸入式经典 Atari 更新、 容量耗尽续集？ 处理输入的方案之前, 三维空间的游戏构造需要予以解决。

![可视化中 HoloLens 的图面上映射](images/surfacemapping.png)<br>
*可视化中 HoloLens 空间映射*

通过利用用户的环境，我们实际上有无限地形选项登陆农历模块。 若要使游戏最接近原始标题，用户无法可能操作并放置在其环境中的不同问题的登录面板。

![农历模块在不断充电](images/640px-lm-hero.jpg)<br>
*农历模块在不断充电*

要求用户了解输入的方案，控制飞船，并且具有较小的目标上很多请求。 成功的游戏体验功能的质询和奖励达到最佳组合。 用户应该能够选择难度级别，最简单的模式只需要要求用户已成功在图面上驻留在用户定义的区域，扫描由 HoloLens。 一旦用户获取的游戏，它们可以然后充当困难他们认为适合。

### <a name="adding-input-for-hand-gestures"></a>添加输入手势

HoloLens 基输入的只有两个手势- [Air 点击和布隆](gestures.md)。 用户无需记住上下文的细微差别或者细目列表的特定手势这样可使平台的界面，用途广泛且易于学习。 虽然系统可能仅公开这些两个手势，为设备的 HoloLens 是能够同时跟踪两只手。 是到阴历 Lander 我们 ode[沉浸式应用程序](app-model.md)这意味着，我们能够以扩展基本手势，即可利用两只手并添加农历模块导航我们自己适合触觉表示的集。

回头看在原始控件方案**我们需要解决的主旨是和旋转**。 需要注意的是旋转的新上下文中添加的附加轴 (从技术上讲两个，但 Y 轴是不太重要的登录)。 两个不同的发货动作自然有助于使自身要映射到每个指针：

![点击和拖动手势 lander 所有三个轴上旋转](images/module-handdrag.gif)<br>
*点击和拖动手势 lander 所有三个轴上旋转*

**被迫接受了**

原始拱廊上的级别映射为值的小数位数，更高级别的已移动的更多的主旨是已应用到随附了。 重要的细微差别，此处指出是用户可以执行其手动从控件和维护所需的值。 实际上，我们可以使用点击和拖动行为来实现相同的结果。 从零开始的主旨是值。 在用户点击并拖动以增加值。 此时，它们可以让转到对其进行维护。 点击和拖动手势值的任何更改会从原始值的增量。

**旋转**

这是有点棘手。 在遇到 holographic"旋转"按钮以点击有利于可怕的体验。 不存在的物理控件为充分利用，因此行为必须来自操作的一个对象，表示 lander，或使用 lander 本身。 我们想出了使用点击并拖动到有效地"推送和拉取"用户可以使用它的方法在方向他们希望面临着。 任何时候用户点击并按住，初始化手势的位置的空间中的点变得旋转的原点。 拖动源将转换现有的转换 （X，Y，Z） 的增量，并将其应用到 lander 的旋转值的增量。 或再简单*相应地返回在空间中拖动左 <>-右、 向上 <>-向下转发 <>-旋转飞船*。

由于 HoloLens 可以跟踪两只手，旋转可以分配到右侧而主旨是由左侧控制。 注意技巧是在此游戏中成功的驱动因素。 *感觉*这些交互是绝对的最高优先级。 尤其是在上下文中的边用浸入式。 过快地做出反应的发货很难不必要地来进行控制，而一个太慢会要求用户在"推送和拉取"飞船上滑雪长一段时间。

### <a name="adding-input-for-game-controllers"></a>正在添加输入游戏控制器

HoloLens 上的手势提供细粒度控制新颖方法，而是仍缺少 'true' 获取从模拟控件的边用反馈。 连接 Xbox 游戏控制器允许将带回 physicality 这种情况下同时利用将附着要保留的细粒度控制。

有多种方法来将比较直接的控制方案应用到 Xbox 控制器。 由于我们要保持原始拱廊设置尽可能接近**被迫接受了**将最佳映射到触发器按钮。 这些按钮是模拟的控件，这意味着它们具有多个简单*打开和关闭*指出，他们可以实际响应将放入其压力的程度。 这为我们提供了类似构造作为**主旨是杆**。 不同于原始游戏和手笔势，此控件将剪切飞船的主旨是后用户停止触发器带来压力。 它仍提供用户同等程度的注意技巧原始拱廊游戏一样。

![左的摇杆进行映射，以偏航角和回滚、 右摇杆进行映射，以宣传和回滚](images/thumbsticksidebyside.gif)<br>
*左的摇杆进行映射，以偏航角和回滚;右摇杆进行映射，以宣传和回滚*

双 thumbsticks 自然地适用于控制的飞船旋转。 遗憾的是，有 3 个轴上的发货可以旋转和两个 thumbsticks 这两者都支持两个轴。 这种不匹配意味着任一一个摇杆控件一个轴;或重叠的 thumbsticks 的轴。 前一种解决方案最终不会感觉"中断"，因为 thumbsticks 本质上是混合使用其本地 X 和 Y 值。 后一种解决方案时，需要查找的冗余轴感觉最自然一些测试。 最后一个示例使用*偏航角*和*回滚*（Y 和 X 轴） 的左摇杆和*间距*并*回滚*（Z 和 X 轴） 的权利摇杆。 这感觉最自然作为*回滚*似乎也与独立配对*偏航角*并*间距*。 请注意，使用为这两个 thumbsticks*回滚*也恰好双击旋转值中; 它是非常有趣了具有 lander do 循环。

此示例应用演示了如何空间识别和触觉浸入式都明显改变了由于 Windows Mixed Reality 可扩展输入形式的体验。 尽管但阴历 Lander 可能接近年龄在 40 年，概念公开与小八边形与 legs 将 live 永远持续下去。 当设想未来，为什么不查看过去？

## <a name="technical-details"></a>技术细节

您可以找到脚本和预设农历模块示例应用程序上[混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX 设计人员 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [运动控制器](motion-controllers.md)
* [手势](gestures.md)
* [类型的混合的现实应用](types-of-mixed-reality-apps.md)
