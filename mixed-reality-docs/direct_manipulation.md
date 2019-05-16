---
title: 直接操作
description: 直接操作输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: 混合现实、 提供注视、 面向交互的视线移动设计，附近，手 HoloLens
ms.openlocfilehash: 803157bb248a5541ed524ac4f828ccbba9d59ce1
ms.sourcegitcommit: 82d4e5cf4ad46bfdc44d0606844e28c75b6e67ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730503"
---
# <a name="direct-manipulation"></a>直接操作

HoloLens 2 提供了直接操作输入的模式，可让您接触全息 dircly 用手。 直接操作的目标是的行为就像在现实生活中的对象。 可以只需按下，激活按钮和甚至和选取、 获取，并移动对象。 在这些情况下，2D 内容表现得像虚拟触摸屏。

直接操作为便于用户了解，并且它太有趣。 它被视为"附近将"输入的模型，这意味着它最适用于与 arm 的覆盖范围内的内容进行交互。

直接操作是基于可见的这意味着用户友好。 没有符号的手势，教用户。 围绕可以接触或获取一个可见元素而构建的所有交互。

## <a name="device-support"></a>设备支持

| 输入的模型 | [HoloLens （第 1 代）](https://review.docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details?branch=master) | HoloLens 2 |[沉浸式耳机](https://review.docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details?branch=master)|
|:-------- | :-------| :--------| :------------|
| 直接操作 | 不支持的 ❌ | ✔️ 建议 | 一种替代方法 ➕[点，并提交](https://review.docs.microsoft.com/en-us/windows/mixed-reality/point-and-commit?branch=master)建议。

直接操作是 HoloLens 2 上的主输入的模型，并利用新的明确的手动跟踪系统。 输入的模型，还可以在通过动作控制器使用的沉浸式耳机，但不是建议为外部对象操作的交互的主要方式。  直接 manipluation 上不可用 HoloLens v1。

## <a name="collidable-fingertip"></a>Collidable 指尖

HoloLens 2 上用户的实际动手识别和被解释为左侧和右侧框架模型。 若要实现的触摸直接与手全息想法，理想情况下，5 碰撞体可以附加到 5 轻松获得相关的每个现有框架模型。 但是，实际上，由于缺少触觉反馈，10 collidable 轻松访问引起的意外的且不可预测的冲突与全息。 

因此，我们建议仅在每个索引手指将碰撞体。 Collidable 索引都可以看到可以仍作为涉及其他手指，如 1 手指按、 1 指点击，2 手指按和 5 手指按不同的触摸手势的活动触摸点，如下图中所示。

![Collidable 指尖图像](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>球体碰撞体

而不是使用随机的一般形状，我们建议使用球体碰撞体，并以可视方式呈现它接近目标提供更好的提示。 球的直径应匹配索引指以增加触摸的准确性的粗细。 它将很容易通过调用手 API 检索手指粗细的变量。

### <a name="fingertip-cursor"></a>指尖游标

除了呈现 collidable 球体上索引指尖，我们创建了一个高级的解决方案，指尖游标，若要以交互方式实现更好的附近目标体验。 它是附加在索引指尖环形游标。 根据邻近，动态的互动方式到的目标方向和大小，详情如下方面：

* 当索引手指移动到一张全息图时，游标始终是并行到全息图的图面，逐渐会相应地缩小其大小。
* 只要上方的手指触摸表面，光标缩小到一个点，并发出一个触摸事件。

借助交互式的反馈，用户可以实现近乎导向目标任务，例如触发的 web 内容上的超链接或按下按钮，如下所示的高精度。 

![指尖光标图像](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>边界框与邻近着色器

全息图本身还需要提供视频和音频反馈以补偿触觉反馈缺乏的能力。 为此，我们使用邻近着色器生成的边界框的概念。 边界框是包含一个三维对象的最小容量耗尽区域。 边界框提供了名为邻近着色器的交互式呈现机制。 邻近着色器的行为：

* 当索引手指范围内时，指尖聚焦被强制转换的边界框面上。
* 时指尖更接近于图面，则会相应地将聚焦。
* 只要指尖 touch 面，边界框的整个更改颜色，或者生成视觉效果以反映触摸状态。
* 同时，可以激活声音效果来增强 visual 触摸反馈。

![边界框与邻近着色器图像](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Pressable 按钮

用 collidable 指尖，用户现已准备好的非常基本 holographic UI 组件，pressable 按钮进行交互。 Pressable 按钮是为直接手指按量身打造的 holographic 按钮。 同样，由于触觉反馈缺乏 pressable 按钮提供一些机制来解决触觉反馈相关的问题。

* 第一种机制是边界框与邻近着色器，在上一部分中详细介绍。 它可用于提供更好地为用户方法，使邻近按钮联系。
* 第二个是困扰。 它将创建有意义的 press 后指尖联系按钮。 机制是按钮紧密与指尖深度轴一起移动。 在达到指定的深度 （按下时） 或通过它传递后使 （在发布） 的深度时，可以触发按钮。
* 应添加声音效果来增强的反馈，当触发按钮。

![Pressable 按钮图像](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>2D 盖板交互

2D 盖板是 holographic 容器托管 2D 应用内容，如 web 浏览器。 用来与通过直接操作 2D 平板式交互设计概念是利用与物理触摸屏进行交互的心理模型。

若要与盖板联系人进行交互：

* 使用索引手指按超链接或按钮。
* 使用索引手指来滚动静态内容向上和向下。
* 用户使用两个索引根手指放大 in 和 out 根据相对的根手指的动作的静态内容。

![2D 盖板图像](images/2D-Slate-Interaction-720px.jpg)

用于操作 2D 平板本身：

* 方法将双手边角和边缘，以显示最接近的操作等方面。
* 获取操作等和执行通过角等统一缩放和重排通过边缘等。
* 获取二维显示静态图像，使你迁移整个盖板顶部 holobar。

![盖板操作的图像](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>三维对象操作

HoloLens 2，的允许用户启用其只手来直接操作通过应用于每个三维对象的边界框三维 hologramphic 对象。 边界框提供了更好地通过其邻近着色器的深度感知。 与边界框中，有两种设计方法，以便 3D 对象进行操作。

### <a name="affordance-based-manipulation"></a>基于功能可见性： 的操作

这允许您操作三维对象通过边界框和在其周围操作等。 只要用户的手即将于一个三维对象，边界框和接近功能可见性： 将揭示出理解。 用户可以获取要移动的整个对象、 边缘等旋转和角等均匀缩放的边界框。

![三维对象操作图像](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>非功能可见性： 基于操作

在此机制中，没有功能可见性： 附加到的边界框。 用户可以仅显示边界框，然后直接与之交互。 如果用一只手获取边界框，平移和旋转的对象将关联到动作和方向的分值。 当对象获取与两只手中时，用户可以转换、 缩放和旋转根据相对两只手的动作。

执行特定操作要求精度，我们建议你使用**功能可见性： 基于操作**，因为它提供高级别的粒度。 灵活操作时，我们建议你使用**非功能可见性： 操作**是因为这样可以即时和氛围体验。

## <a name="instinctual-gestures"></a>Instinctual 手势

与 HoloLens 不同 （第 1 代），我们教用户布隆和空气点击等几个预定义的笔势。 对于 HoloLens 2，我们不要求用户记住任何符号的手势。 Instinctual 所有所需的用户笔势，用户需要与全息和内容，进行交互。 要实现 instinctual 手势，方式是指导用户执行 UI 等的设计通过笔势。

例如，如果我们建议您对对象随取即行或使用双指挤压控点，该对象或控点应很小。 如果我们希望您能执行五个手指随取即行，该对象或控点应为相对较大。 类似于按钮，小按钮会限制用户使用一根手指，按它，而大按钮鼓励用户使用其搁按。

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>双手和 6 DoF 控制器之间的对称设计

您可能已经注意到是现在我们可以得出手中 VR AR 和动作控制器之间的交互 parallels。 这两个输入可用于触发相应的环境中的直接操作。 HoloLens 2 中获取和使用近距离中的工作原理在手拖动为随取即行按钮相同的方法类似于执行 WMR 中的动作控制器上。 这为用户提供了两个平台之间的交互熟悉程度，并可能会有用应决定移植到另一个您应用程序。

## <a name="optimize-with-eye-tracking"></a>充分利用的眼跟踪与

如果它正常运行按预期运行，但也很快就如果您不能再移动您的手任意位置而不会无意中触发一张全息图，令人沮丧，直接操作可以感觉神奇。
眼睛追踪可能有助于更好地标识用户的意图。

* **当**:减少错误地触发操作响应。 眼睛追踪允许更好地了解哪些用户当前参与。
例如，假设你正在阅读通过全息版的 （说明） 文本时达到超过获取实际工作的工具。

  这样，您甚至没有之前 （甚至是外部用户的字段视野 (FOV) 可能） 将您注意到一些交互式 holographic 按钮跨意外移动您的手。

  长话短说：如果用户尚未探讨一张全息图一段时间，但它检测触摸或掌握现有的事件，则很可能用户实际上并不想要与该全息图进行交互。

* **哪一个**:除了寻址 false 正激活，另一个示例包括更好地确定哪些全息抓取或仔细清除从你的观点可能会精确相交点，尤其是当多个全息位于接近每个其他。

  HoloLens 2 上的眼跟踪具有某些限制如何准确地时它可以确定红眼的视线移动，这仍会非常有帮助的深度不一致会由于交互附近用输入一只手进行交互时。  这意味着它是有时难以确定您的手是超前还是一张全息图，以准确地说例如获取操作小组件的前面。

* **下一**:使用快速-引发手势查看哪些用户的使用信息。 获取一张全息图，大致它将向你预期目标。  

    虽然这可能是有时正常、 快速执行手势的工作原理可能会导致在高度不准确的目标。 这是其中的眼跟踪可以帮助解决驱使手形图标到预期位置重新引发向量。

## <a name="see-also"></a>请参阅

* [视线移动和提交](gaze-and-commit.md)
* [指向并提交](point-and-commit.md)
* [交互基础知识](interaction-fundamentals.md)
