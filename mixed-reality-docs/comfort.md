---
title: 舒适
description: 在自然查看人工 visual 系统依赖于多个源的信息，或"提示，"将解释 3D 形状和对象的相对位置。
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: 混合现实，设计，改善环境，HoloLens 2 HoloLens （第 1 代）
ms.openlocfilehash: 3dac997923b3f2319cb97137c1bbd9a12c4126b1
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993627"
---
# <a name="comfort"></a>舒适

在自然查看人工 visual 系统依赖于多个源的信息，或"提示，"将解释 3D 形状和对象的相对位置。 一些提示仅依赖于单个关注 （monocular 提示），包括[线性角度来看](https://en.wikipedia.org/wiki/Perspective_(graphical))，[熟悉大小](https://en.wikipedia.org/wiki/Size#Perception_of_size)，光散射、[深度字段模糊](https://en.wikipedia.org/wiki/Depth_of_field)，和[便利设施](https://en.wikipedia.org/wiki/Accommodation_(eye))。 其他提示依赖两只眼睛 （放大镜提示），并包括[vergence](https://en.wikipedia.org/wiki/Vergence) （实质上是查看对象所需的眼睛相对旋转） 和[放大镜差异](https://en.wikipedia.org/wiki/Stereopsis)（模式的差异之间的两只眼睛背面场景的投影）。 若要确保最大舒适头装载显示器上的，务必为设计人员和开发人员创建和显示内容中一种方法，以模拟这些提示在自然世界中的运作方式。 从物理角度看，也很重要设计不需要的颈部或手臂 fatiguing 动作的内容。 在本文中，我们将逐一要时刻牢记，若要实现这些目标的关键注意事项。

## <a name="vergence-accommodation-conflict"></a>Vergence 便利设施冲突

若要清楚地查看对象，人们必须[容纳](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)，或调整自己眼的焦点，对对象的距离。 在同一时间两只眼睛的旋转角度必须[聚合](https://en.wikipedia.org/wiki/Convergence_(eye))对对象的距离，以避免出现双映像。 自然查看 vergence 和便利设施链接。 查看内容 (例如接近你鼻子 housefly) 附近时您的眼睛跨和适应 near 点。 相反，如果在光学无穷大 （大约从开始在 6 分钟或更远的正常视力） 查看的内容，你自己的行的建立直通连接变得并行，向无穷远适应你自己的可重用功能区。 

在最头装载显示用户将始终都能适应焦点距离 （以获得 sharp 图像） 的显示器，但聚合的距离 （以获取单个映像） 感兴趣的对象。 当用户适应，并集中到不同的距离时，之间的两个提示的自然链接必须被破坏，这可能会导致 visual 不适或疲劳。

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>适用于 holographic 设备指南

HoloLens 显示固定为光学的距离大约 2.0 m 的用户。 因此，用户必须始终都能适应附近 2.0 m 来维护清晰的图像的设备中。 应用程序开发人员可指导用户的眼睛，方法是将内容和全息放各种深入探索聚合。 从 vergence 便利设施冲突不适可以避免或最小化通过保留的内容向其用户 2.0 m 尽可能接近聚合 （即在场景中具有许多深度，放置从用户尽可能 2.0 m 附近的感兴趣的区域）。 内容不能放置附近 2.0 m，不适从 vergence 便利设施冲突时，最大不同距离之间来回切换的用户的视线移动时。 换而言之，它是更舒适地看一下静态 hologram 保持 50 cm 消失比若要查看一张全息图 50 cm 消失，随着时间的推移将靠近或远离你。

![放置全息从用户的最佳距离。](images/distanceguiderendering-950px.png)<br>
*将用户从全息的最佳距离*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>HoloLens 的最佳实践 （第 1 代） 和 HoloLens 2

最大舒适**全息图放置的最佳区域是 1.25 m 和 5 分钟之间**。 设计器结构鼓励用户进行交互的内容场景中每种情况下，应尝试 1m 或内容距离较远 (例如调整[内容大小和默认的位置参数](gaze-targeting.md))。 

尽管内容有时可能需要更接近于 1 百万显示，但我们建议不要以往显示更接近于 40 cm 全息。 因此，我们建议从开始到**淡出 40 cm 的内容并将呈现剪辑平面放入在 30 cm**以避免任何更接近对象。

将移动的深度的对象是更有可能比静态对象以生成由于 vergence 便利设施存在冲突的不适。 同样，要求用户快速切换焦点近和远焦点 （例如，由于需要直接交互弹出 hologram) 可能导致 visual 不适和疲劳。 因此，**额外格外小心，应以何种频率最大程度减少用户是： 查看深度; 中移动的内容或快速之间切换焦点近和远全息**。 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>HoloLens 2 和交互距离附近的其他注意事项

在设计为直接 (near) HoloLens 2 中的交互内容或**中的内容必须放置的位置更接近于 1 百万的任何应用程序，应采取格外小心以确保用户舒适**。 由于 vergence 便利设施冲突不适的几率降低观看距离会呈指数增加。 此外，用户可能会遇到增加的 bluriness 附近交互的距离，查看内容，因此，我们建议测试内容呈现同时也为更接近最佳全息图放置 (小于下剪裁平面的 1.0 m) 区域中时为确保它保持清晰而舒适地查看。 

**我们建议创建基于用户希望查看的内容的接近 (小于 1.0 m) 的时间量，在深度移动应用的"深度 budget"**。 例如，避免将用户放在这些情况下多个 25%的时间。 如果超出深度预算，我们建议仔细用户测试，以确保它保持舒适的体验。 

一般情况下，我们还建议仔细测试，以在附近交互距离确保 （例如，速度移动，可访问性等） 的任何交互要求保持熟练的用户。 


### <a name="guidance-for-immersive-devices"></a>适用于沉浸式设备指南

沉浸式设备的指南和最佳实践 HoloLens 仍然适用，但显示，具体取决于焦点距离的舒适区域的特定值移动。 一般情况下，向这些显示焦点距离是之间 1.25 m-2.5 m。 如有疑问，避免的呈现感兴趣的对象太靠近用户和改为尝试保留 1 百万的多数内容或远一点。

## <a name="interpupillary-distance-and-vertical-offset"></a>Interpupillary 距离和垂直偏移量

查看数字内容标头装载时显示 (HMD) 相对于数字内容的显示位置的查看者的眼睛的位置至关重要。 具体而言，这两个 interpupillary 距离 ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) 和垂直偏移量 (VO) 非常重要，舒适地观看的 HMDs 中的数字内容。 

IPD 指瞳孔、 或的个人的眼睛中心之间的距离。 VO 是指相对于水平轴的查看者查看每只眼睛向显示的数字内容的潜在垂直偏移量 （值得注意的是，这不是相同水平偏移量，或放大镜差异）。 错误匹配一个或两个到单个用户的这些因素可以恶化效果不适引起 vergence 便利设施发生冲突，但也可能甚至原因不适 V A 冲突最小化 （例如，用于显示在 2.0 的 m 重要的内容时HoloLens 的距离）。 

### <a name="guidance-for-holographic-devices"></a>适用于 holographic 设备指南

#### <a name="hololens-1st-gen"></a>HoloLens （第 1 代）

对于 HoloLens （第 1 代），估计和在设备过程中设置 IPD[校准](calibration.md)。 为新用户添加到已设置设备，必须在运行校准或 IPD 必须手动设置。 VO 完全取决于适合的设备。 具体而言，为了尽量减少 VO，在设备需要将停留在其上用户的头，以便显示信息是与他/她眼睛轴的级别。 

#### <a name="hololens-2"></a>HoloLens 2

对于 HoloLens 2，估计和在关注/设备过程中设置 IPD[校准](calibration.md)。 为新用户添加到已设置设备，必须运行校准确保 IPD 设置正确。 VO 自动中考虑 HoloLens 2。 

### <a name="guidance-for-immersive-devices"></a>适用于沉浸式设备指南

Windows Mixed Reality 沉浸式 HMDs 具有 IPD 或 VO 没有自动校准。 可以在软件中手动设置 IPD (在混合现实门户设置中，请参阅[校准](calibration.md))，或者某些 HMDs 具有允许用户调整到合适位置可重用功能区的间距 （即，这大致机械滑块匹配其 IPD）。 

## <a name="rendering-rates"></a>呈现费率

混合的现实应用程序是唯一的因为用户可以自由地在世界中，就好像它们是真实的对象与虚拟内容，例如进行交互。 若要维护此印象，务必呈现全息，使其出现在世界稳定并平稳地动态变化。 在呈现[最小值为 60 每秒帧数 (FPS)](understanding-performance-for-mixed-reality.md)可帮助实现此目标。 有支持在 framerates 高于 60 FPS 呈现一些混合现实设备，这些设备强烈建议以呈现较高的 framerates 以提供最佳用户体验。

**深入探讨**

若要绘制全息看上去像[它们在真实或虚拟世界中稳定](hologram-stability.md)，应用需要呈现来自用户的位置的图像。 图像呈现所需时间，因为 HoloLens 和其他 Windows Mixed Reality 设备将预测时图像所示显示中用户的头将在其中。 此预测算法是一个近似值。 Windows Mixed Reality 算法和硬件调整要衡量预测头位置和实际头位置之间差异的呈现的图像。 此过程使用户看到图像看上去像它已从正确的位置，从呈现和全息感觉稳定。 更新最适合头位置中的小更改，它们在不能完全的一些呈现的图像的差异，如所引起的运动视差。

**通过在最小的帧速率是 60 FPS 呈现，您都做两件事情来帮助进行稳定全息：**
1. 减少 judder 的外观，其中的特征是不均匀的动作和 double 的映像。 更快的 hologram 运动，呈现较低费率都与得更明显 judder。 因此，努力始终保持 60 FPS （或你的设备的最大呈现速率） 可帮助避免移动全息 judder。
2. 最大程度减少总体延迟。 在使用游戏线程和呈现线程引擎保持同步，在 30 FPS 运行运行可以添加额外延迟 33.3ms。 通过减少延迟，这会降低预测错误，并增大全息图稳定性。

**性能分析**

有多种工具，可用于应用程序如帧速率进行基准测试：
* GPUView
* Visual Studio 图形调试器
* 3D 引擎，例如 Unity 中的帧调试程序中内置的探查器

## <a name="self-motion-and-user-locomotion"></a>自动作和用户 locomotion

唯一的限制是物理空间; 的大小如果你想要允许用户移动得更远的虚拟环境中比其实际聊天室，则必须实现一种形式的完全是虚拟的动作。 但是，与用户的实际的物理运动不匹配的持续虚拟动作通常可以引入运动病。 此结果是*视觉提示*为自动作从*虚拟世界*与冲突[vestibular 提示](https://en.wikipedia.org/wiki/Vestibular_system)为自动作来自*现实世界*。

幸运的是，有用于实现用户 locomotion，可帮助避免此问题的提示：
* 始终将用户放在其移动; 控件意外自动作是特别容易出现问题
* 人类是重力的对方向非常敏感。 因此，用户启动垂直动作尤其应该避免。

### <a name="guidance-for-holographic-devices"></a>适用于 holographic 设备指南

允许用户移动到大型的虚拟环境中的其他位置的一种方法是意味着它们在场景中移动一个小的对象。 可以按如下所示来实现这种效果：
   1. 提供他们想要移动其中用户可以选择一个点，在虚拟环境中的接口。
   2. 选择它后收缩场景渲染到围绕所需的位置的磁盘。
   3. 同时它能让所选的位置，用户便可以将其移动，就好像它是一个小的对象。 然后，用户可以移动接近其英尺为单位的所选内容。
   4. 在取消选择，继续呈现整个场景。

### <a name="guidance-for-immersive-devices"></a>适用于沉浸式设备指南

使用上述 holographic 设备方法不会无法正常工作沉浸式设备中，因为它要求应用程序以呈现大型黑色 void 或另一个默认环境，同时移动"磁盘"。 此种处理方式会中断的意义上的深入探讨。 用户 locomotion 在沉浸式头戴式中一项技巧是"blink"方法。 此实现中为用户提供对其动作的控制和提供一个简短的形象的移动，但可以在非常短，用户就很难感觉 disoriented 通过完全是虚拟自动作：
   1. 提供他们想要移动其中用户可以选择一个点，在虚拟环境中的接口。
   2. 选择它后很快就不用了呈现出的同时开始针对该位置非常快速模拟 (100 m/s) 动作。
   3. 淡入淡出呈现完成转换后备份中。

## <a name="heads-up-displays"></a>平视显示

在第一人称 videogames 危险警告显示 (HUDs) 永久介绍直接在屏幕上的播放机运行状况、 最小映射和清单等信息。 HUDs 可以有效地将通知而无需在玩游戏体验凸出玩家。 在混合的现实体验 HUDs 有可能会导致重大不适，并且必须适应更多沉浸式上下文。 具体而言，HUDs 严格锁定到用户的头方向是可能会产生不适。 如果应用需要 HUD，我们建议*正文*锁定而不头锁定。 可以立即将转换由用户，但直到达到旋转的阈值不与用户的 head 会旋转时都显示一组作为实现此种处理方式。 一旦达到该旋转，可能会重定向 HUD 显示在用户的字段的视图中的信息。 实施 1 对 1 的 HUD 旋转和转换相对于用户的头应始终避免动作。

## <a name="text-legibility"></a>文本以增强可读性

减少眼睛疲劳和维护用户舒适，尤其是在应用程序或需要用户在 HMD 中读取的情况下，可以帮助最佳文本以增强可读性。 文本以增强可读性取决于许多因素，包括各种显示属性 （例如，像素密度、 亮度、 对比度）、 可重用功能区属性 （例如，色差） 和文本/字体属性 （例如，特定字体特征等权重、 间距、 具有衬线等，字体，背景的颜色的颜色)。  

一般情况下，我们建议测试特定的应用程序以提高可读性并进行字体大小大是可行的舒适的体验。 下面我们作为开发的起始点的常规指南。 请注意，所有字体大小以度为单位都报告[visual 角度](https://en.wikipedia.org/wiki/Visual_angle)而不是特定的物理大小，其中提供指南的最佳全息图放置区域内任何距离因为它的大小文本和它出现在查看器的距离。 

### <a name="guidance-for-holographic-devices"></a>适用于 holographic 设备指南

对于 holographic 的设备，白色/轻型背景上的呈现黑色/深文本提供最一致对比度，因为在后台将遮蔽呈现背后的真实世界的干扰。 呈现黑色/深色背景上的白色/轻型文本允许多个实际环境以显示通过，这可能会影响文本以增强可读性。 

#### <a name="hololens-1st-gen"></a>HoloLens （第 1 代）

（从字体基线 ascender 测量） 的最小的清晰字体大小为大约 0.35 °，熟练的字体大小至少大约 0.5 ° 用于读取内容向用户显示在 2 分钟的距离。 

#### <a name="hololens-2"></a>HoloLens 2

（从字体基线 ascender 测量） 的最小清晰字号至少大约是： 
   - 在 45 cm （直接操作距离） 为 0.4 °-0.5 ° 
   - 在 2.0 m 0.35 °-0.4 °
   
轻松清晰的字体大小 （从字体基线 ascender 测量） 至少大约是： 
   - 在 45 cm （直接操作距离） 0.65 °-0.8 °
   - 在 2.0 m 0.6 °-0.75 °

请注意，需要由于前面所述 vergence 便利设施冲突而是直接操作距离处的文本略大字体大小 （用户的眼睛会适应到 2.0 m 在 HoloLens，因此内容呈现在例如，45 cm可能出现更模糊到用户）。 

### <a name="guidance-for-immersive-devices"></a>适用于沉浸式设备指南

沉浸式设备通常具有较高的对比度率，因为完整封闭的外部环境中，但可能会由于的可重用功能区的前面显示放大倍数部分具有较低的有效像素密度。 

对于 Windows Mixed Reality 沉浸式 HMDs （从字体基线 ascender 测量） 的最小的清晰垂直字体大小是大约 0.7 0.9 ° 和熟练垂直字体大小为大约 1.0 ° 用于读取内容呈现到到 2 分钟用户。

## <a name="gaze-direction"></a>视线移动方向

为了避免眼睛和颈部的压力，以便避免过多的眼睛和颈部移动了应设计内容。
* **避免**的视线移动角均大于 10 度上面即将推出 （垂直移动）
* **避免**的视线移动角均大于 60 度下面即将推出 （垂直移动）
* **避免**颈部旋转超过 45 度中心-（水平运动）

最佳 （静止） 的视线移动角度视为下面水平、 10-20 度之间头倾向于倾斜向下略有不同，尤其是在活动期间。

![允许的视野 (FOV) 由运动的颈部范围](images/optimal-field-of-view-2-750px.png)<br>
*允许的视野 (FOV) 由运动的颈部范围*

## <a name="arm-positions"></a>Arm 位置

当用户需要保留的一种体验期间引发手的形状时，可能会累积肌肉疲劳。 此外 fatiguing，要求用户在重复进行长时间点击手势以无线方式。 因此，建议的体验，避免需要常量、 重复手势输入。 通过合并短暂的休息或提供混合使用手势和语音输入与应用交互，可以达到此目的。

## <a name="see-also"></a>请参阅
* [凝视](gaze.md)
* [全息影像稳定性](hologram-stability.md)
* [交互基础知识](interaction-fundamentals.md)
* [全息帧](holographic-frame.md)
* [校准](calibration.md)
