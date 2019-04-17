---
title: 交互基础知识
description: 如我们构建了跨 HoloLens 体验 （第 1 代） HoloLens 2 和沉浸式耳机，我们已经开始写下我们发现用于共享的一些事项。
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实，交互设计
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590104"
---
# <a name="interaction-fundamentals"></a>交互基础知识

在跨 HoloLens 和沉浸式耳机，我们已构建的体验，我们已经开始写下我们发现用于共享的一些事项。 将它们视为用于混合的现实交互设计的基本构建块。

## <a name="device-support"></a>设备支持

下面是适用于可用的交互设计文章的设备类型或类型的概述。
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>输入</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">明确的手</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">密切关注面向</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">目标的视线移动</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">手势</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">语音设计</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> 游戏板</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">运动控制器</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>认知和空间功能</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">空间合理的设计</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">空间映射设计</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">全息</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>用户是照相机

![用户是照相机](images/useriscamera-640px.jpg)

始终考虑设计的用户的角度来看，随着有关其实际和虚拟世界。

**要提出的一些问题**
* 用户、 倾斜度、 站着，还是使用您的体验时的每个步骤？
* 你的内容 does 如何调整到不同的位置？
* 用户可以调整它？
* 用户是熟练使用您的应用程序？

**最佳做法**
* 用户是照相机和它们控制移动。 让这些驱动器。
* 如果你需要几乎传输用户，是对 vestibular 不适围绕这些问题的敏感。
* 使用较短的动画
* 向下/左/右从进行动画处理或淡入，而不是 Z
* 计时变慢
* 允许用户查看在后台世界

**要避免的问题**
* 不要摇动照相机或有意将其锁定到 3DOF 仅方向 (未转换），它可以让用户感到不安。
* 无突然移动。 如果你需要将内容与用户，将其移动速度慢、 更流畅地向其最大舒适。 用户将对大型菜单在它们即将做出反应。
* 不加速或启用用户的照相机。 用户很敏感加速 （angular 和平移）。

## <a name="leverage-the-users-perspective"></a>利用用户的角度来看

用户在沉浸式和全息版的设备上看到显示通过混合现实的世界。 在 HoloLens 上此效果称为[holographic 帧](holographic-frame.md)。

在 2D 开发中，频繁访问的内容和设置可能会位于屏幕以使其可以轻松进行访问的角。 但是，在全息版应用中，用户的视图的角落中的内容可能会不喜欢以访问。 在这种情况下，holographic 帧的中心是有关内容的主要位置。

用户可能需要指导来帮助查找重要的事件或对象超出其即时视图。 可以使用箭头、 光线跟踪信息、 字符磁头运动、 思想气泡、 指针、 空间声音和语音提示以帮助并指导用户到应用程序中的重要内容。

建议对未锁定内容到用户的舒适的屏幕。 如果你需要保留内容视图中，将其放在世界上并进行"尾随"类似开始菜单的内容。 获取用户的角度来看以及提取的内容会感觉更自然的环境中。

![开始菜单在到达帧的边缘时遵循的用户视图](images/tagalong-1000px.jpg)<br>
*开始菜单在到达帧的边缘时遵循的用户视图*

上 HoloLens，全息感觉实际时由于它们不被切断适合 holographic 范围内。 若要查看在框架内一张全息图的边界将移动用户。 在 HoloLens，务必简化您的 UI，使其适合用户的视图中专注于主要操作。 沉浸式耳机，务必维护持久虚拟世界中设备的视野效果。

## <a name="user-comfort"></a>用户舒适

若要确保最大[舒适](comfort.md)头装载显示器上非常重要的设计人员和开发人员创建和显示内容中一种方法，以模拟人类如何解释 3D 形状和自然的对象的相对位置世界。 从物理角度看，也很重要设计不需要的颈部或手臂 fatiguing 动作的内容。

无论开发 HoloLens 或沉浸式耳机，务必要呈现两只眼睛的视觉对象。 呈现危险警告显示一眼中仅可以使界面难以理解，以及导致 uneasiness 到用户的关注和大脑。

## <a name="share-your-experience"></a>共享你的体验

使用[混合现实捕获](mixed-reality-capture.md)，用户可以捕获照片或视频的任何时候用户体验。 请考虑你可能想要鼓励快照或视频应用程序中的体验。

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>利用 Windows Mixed Reality 家庭的基本 UI 元素

就像 Windows PC 体验始于桌面、 Windows Mixed Reality 开头主页。 [Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)利用理解和导航三维位置我们与生俱来的能力。 HoloLens，与您在家是物理空间。 沉浸式耳机，与您在家是一个虚拟位置。

您家也是在其中将使用开始菜单打开和放置应用程序和内容。 可以使用混合的现实内容填充您家并同时使用多个应用程序执行多任务。 在家中放置的内容继续保留在那里，即使您重新启动你的设备。

## <a name="see-also"></a>请参阅
* [目标的视线移动](gaze-targeting.md)
* [手势](gestures.md)
* [语音设计](voice-design.md)
* [运动控制器](motion-controllers.md)
* [空间合理的设计](spatial-sound-design.md)
* [空间映射设计](spatial-mapping-design.md)
* [Comfort](comfort.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
