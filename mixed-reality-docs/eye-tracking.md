---
title: 眼动跟踪
description: HoloLens 2 为开发人员提供了使用用户所注视对象的相关信息的功能，将全息体验中的环境和人类理解能力提高到了一个新境界。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼睛跟踪，混合现实，输入，眼睛，校准
ms.openlocfilehash: 60de5ceb9f55ca7e2f74856af9bd75567763e382
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441118"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2 中的眼动跟踪

![MRTK 中的眼睛跟踪演示](images/mrtk_et_scenemenu.jpg)

HoloLens 2 为开发人员提供了使用用户所注视对象的相关信息的功能，将全息体验中的环境和人类理解能力提高到了一个新境界。 此页概述了面向开发人员和设计人员的这项新功能，这些功能可让开发人员和设计人员从各种用例和基本开发人员指南中获益。 


## <a name="calibration"></a>校准 
为了使目视跟踪能准确地工作，每个用户都需要经历[跟踪用户校准](calibration.md)，用户必须查看一组全息目标。 这允许设备调整系统，以便为用户提供更舒适和更高的质量查看体验，并确保同时进行准确的目视跟踪。 目视跟踪应该适用于大多数用户，但在极少数情况下，用户可能无法成功校准。
若要了解有关校准的详细信息以及如何确保流畅的体验，请查看我们的[眼睛跟踪用户校准](calibration.md)页面。


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
     <td>眼睛-注视</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="available-eye-tracking-data"></a>可用的目视跟踪数据
在深入了解有关目视输入的特定用例的详细信息之前，我们想要简要指出 HoloLens 2[目视跟踪 API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose)提供的功能。 开发人员可在大约_30 FPS （30 Hz）_ 的情况中访问一只眼睛眼睛（看原点和方向）。
有关如何访问目视跟踪数据的更多详细信息，请参阅我们的开发人员指南了解如何使用[DirectX 中的眼睛](gaze-in-directx.md)，并看看[Unity](https://aka.ms/mrtk-eyes)。

围绕实际目标围绕视觉角度，眼睛的眼睛约在1.5 度内（请参阅下图）。 由于预期的轻微 imprecisions，开发人员应计划围绕此下限值（例如 2.0-3.0 度）的某些边距，这可能会导致更舒适的体验。 下面将详细介绍如何处理小目标的选择。 要准确运行眼动跟踪，每个用户需要完成眼动跟踪用户校准。 

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*以2米距离为目标的最佳目标大小*

<br>

## <a name="use-cases"></a>用例
眼动跟踪可让应用程序实时跟踪用户正在注视的位置。 以下用例描述了在混合现实中，在 HoloLens 2 上使用目视跟踪可能会发生的一些交互。
请注意，这些用例不是全息 Shell 体验的一部分（即启动 HoloLens 2 时显示的接口）。
你可以在[混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)中试用其中一些功能，其中提供了几个有趣且功能强大的示例来使用目视跟踪，例如快速而轻松地使用目视跟踪的目标选项以及基于文本自动滚动用户查看的内容。 

### <a name="user-intent"></a>用户意图    
有关用户所在位置和内容的信息**为其他输入**提供了强大的上下文，例如语音、动手和控制器。
可在各种任务中使用此信息。
例如，这种情况的范围包括：只需查看全息影像并显示 *"选择"* （另请参阅 "注视" 和 "[提交](gaze-and-commit.md)"），或者说 *"put ..."* ，然后查看用户想要放置全息图，并说 *"。出现 "* 。 在[混合现实工具包 - 视线支持的目标选择](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)和[混合现实工具包 - 视线支持的目标定位](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)中可以找到相关示例。

此外，用户意向的示例可能包括使用用户查看的信息来增强使用所介绍的虚拟代理和交互式全息影像。 例如，虚拟代理可能会根据当前查看的内容来调整可用选项及其行为。 

### <a name="implicit-actions"></a>隐式操作
隐式操作的类别与用户意图密切相关。
其思路是，全息影像或用户界面元素会以 instinctual 的方式做出反应，甚至可能不会像用户同时与系统交互，而是让系统和用户保持同步。例如，**基于目视的自动滚动**，用户可以在其中读取长文本，该文本会在用户进入文本框底部时自动开始滚动，以使用户处于阅读流中而不抬起手指。  
这种情况的一个关键方面是，滚动速度可适应用户的读取速度。
另一个例子就是**受支持的目视缩放和平移**，用户可以感觉到他或她所关注的内容完全接近。 触发缩放和控制缩放速度可以通过语音或手写输入来控制，这对于向用户提供控制感受，同时避免被淹没非常重要。 下面将更详细地讨论这些设计注意事项。 放大后，用户可以顺利地执行操作，例如，街道的学习过程只需使用其眼睛来浏览其邻居即可。
[混合现实工具包 - 视线支持的导航](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html)示例中可以找到此类交互的演示。

隐式操作的其他用例包括：
- **智能通知：** 如果在你要查找的位置，通知弹出的厌恶， 考虑到用户正在关注的内容，你可以通过从当前 gazing 用户的位置偏移通知来更好地进行此体验。 这会限制干扰，并在用户完成读取后自动将其关闭。 
- **留心全息影像：** 在 gazed 时，会对影像进行细微反应。 这可能包括稍微光亮的 UI 元素，这是一种对虚拟狗的缓慢百花齐放花，开始回顾用户并 wagging 其尾部。 这种交互可能会在应用程序中提供更有趣的连接和满意度。

### <a name="attention-tracking"></a>注意力跟踪   
有关用户所在位置或内容的信息是一个非常强大的工具，可用于评估设计的可用性，并确定有效工作流中的问题。 目视跟踪可视化和分析是各种应用程序领域的常见做法。 在 HoloLens 2 中，我们提供了一种新的维度来理解，因为3D 全息图可以放置在真实的上下文中并进行相应的评估。 [混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)提供了用于记录和加载目视跟踪数据的基本示例，以及如何对其进行可视化。

此领域的其他应用场景包括： 
-   **远程目视视觉视觉对象：** 可视化远程协作者正在寻找的内容，以增加共享理解。
-   **用户研究研究：** 关注跟踪有助于更好地了解我们如何感知和与我们的环境接洽，这有助于更好地 instinctual 人工意向模型，以实现更高的人工计算机交互。 
-   **培训：** 通过更好地了解专家的视觉搜索模式和对复杂任务（例如，用于分析医疗数据或操作机械）的密切关注，改进了新手的培训。
-   **设计评估和市场研究：** 在评估网站和产品设计时，目视跟踪是一种用于市场研究的常用工具。 使用 HoloLens 2，可以通过将数字产品设计变型与物理环境合并来将此扩展到3D 空间。 

### <a name="additional-use-cases"></a>其他用例
- **游戏：** 您是否曾经想过强大？ 机会来了！ 可以通过起始在 levitate 全息影像。 从眼睛开始拍摄激光光标，试用[RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
将敌人变成石子，或将其冻结。 使用 X 光透视来扫描建筑物。 没有做不到，只有想不到！
请注意，用户要了解详细信息，请注意我们的[基于眼睛的输入设计准则](eye-gaze-interaction.md)。

- **表现力头像：** 目视跟踪通过使用实时眼睛跟踪数据来使真实的头像显示用户正在查看的内容，以更有意义的3D 头像为目标。 

- **文本条目：** 目视跟踪可用作低工作量文本输入的替代方案，特别是当语音或手不方便使用时。 

<br>

## <a name="using-eye-gaze-for-interaction"></a>使用目视查看交互
构建充分利用快速移动目视目标的交互可能会很困难。
一方面，眼睛的移动速度非常快，你需要小心地使用眼睛眼睛，因为否则用户可能会发现体验太多或分散注意力。 另一方面，你还可以创建真正的神奇体验，将激发你的用户！ 若要帮助你了解关键优势、挑战和设计建议，了解如何进行[互动](eye-gaze-interaction.md)。 

<br>
 
## <a name="dev-guidance-what-if-eye-tracking-is-not-available"></a>开发指南：如果目视跟踪不可用，该怎么办？
在某些情况下，由于各种原因（包括但不限于），应用无法接收任何目视跟踪数据：
* 用户跳过了眼睛跟踪校准。
* 用户进行了校准，但决定不向应用程序授予使用其眼跟踪数据的权限。
* 用户具有唯一的眼镜，或系统尚不支持的某种眼睛状态。
* 外部因素抑制了一种可靠的眼睛跟踪，如在眼睛前面的头发上出现污迹面板或眼镜、强烈直接阳光和 occlusions。

作为应用开发人员，这意味着你需要考虑如何支持目视跟踪数据可能不可用的用户。 下面我们首先介绍如何检测目视跟踪是否可用，以及如何解决不能用于不同应用程序的情况。

### <a name="1-how-to-detect-that-eye-tracking-is-available"></a>1. 如何检测目视跟踪可用
可以通过几个检查来确定是否有目视跟踪数据可用。 检查是否 。
* ...系统完全支持目视跟踪。 调用以下*方法*： [EyesPose. IsSupported （）](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* ...校准了用户。 调用以下*属性*： [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)

* ...用户已将你的应用权限授予使用其眼跟踪数据：检索当前的 _"GazeInputAccessStatus"_ 。 有关如何执行此操作的示例，请参阅[请求访问注视输入](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)。

此外，你可能需要通过在收到的目视跟踪数据更新之间添加超时，并以其他方式回退到下面所述的打印头来检查眼睛跟踪数据是否过时。 

如上所述，眼睛跟踪数据可能不可用的原因有多种。 尽管某些用户可能已特意决定撤消对其眼睛跟踪数据的访问，但对于不提供对其眼睛跟踪数据的访问权限的隐私性的用户体验的不满，这一点很有可能是不可能的。 因此，如果你的应用程序使用目视跟踪，并且这是体验的重要部分，我们建议你清楚地将此信息传递给用户。 请通知用户，目视跟踪对于你的应用程序至关重要（甚至可能会列出一些增强的功能）以充分利用你的应用程序，从而帮助用户更好地了解他们所放弃的内容。 帮助用户确定目视跟踪可能不工作的原因（基于上述检查），并提供一些建议来快速解决潜在问题。 例如，如果您可以检测到系统支持目视跟踪，则用户会进行校准，甚至会获得其权限，但不会收到任何眼睛跟踪数据，这可能会导致某些其他问题，如污迹或眼睛封闭像素。 但请注意，在某些情况下，眼睛跟踪可能只是不能正常工作。 因此，在应用中启用眼睛跟踪时，可以通过允许消除甚至禁用提醒来过于这种情况。

### <a name="2-fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>2. 使用目视视为主要输入指针的应用的回退
如果你的应用程序使用目视看眼作为指针输入来快速选择场景中的全息影像，但眼睛跟踪数据不可用，则建议回退到打印头并开始显示眼睛良好的光标。 建议使用超时值（例如500–1500毫秒）来确定是否要切换。 这是为了防止在系统每次由于快速目视动作或传情动漫或传情动漫而发生跟踪时弹出游标。 如果你是一名 Unity 开发人员，则已在混合现实工具包中处理自动回退到打印头。 如果你是 DirectX 开发人员，则需要自行处理此开关。

### <a name="3-fallback-for-other-eye-tracking-specific-applications"></a>3. 其他目视跟踪特定应用程序的回退
您的应用程序可以采用专门为眼睛定制的独特方式（例如，为头像形象提供动画或基于眼睛的关注热图，它依赖于有关视觉对象的精确信息）。 在这种情况下，不会有任何明确的回退。 如果目视跟踪不可用，则可能只需禁用这些功能。
同样，我们建议你清楚地将其传达给可能未意识到该功能无法正常工作的用户。

<br>

在此页面中，你可以获得一个良好的概述，使你开始了解 HoloLens 2 的眼睛跟踪和目视眼睛输入的角色。 若要开始开发，请查看我们的信息，了解如何[与全息影像交互](eye-gaze-interaction.md)、[在 Unity 中目视](https://aka.ms/mrtk-eyes)看，以及如何[在 DirectX 中观看眼](gaze-in-directx.md)。


## <a name="see-also"></a>另请参阅
* [校准](calibration.md)
* [舒适](comfort.md)
* [目视的交互](eye-gaze-interaction.md)
* [目视观察 DirectX](gaze-in-directx.md)
* [目视看 Unity （混合现实工具包）](https://aka.ms/mrtk-eyes)
* [注视并提交](gaze-and-commit.md)
* [语音输入](voice-design.md)


