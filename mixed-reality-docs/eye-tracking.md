---
title: 眼动跟踪
description: HoloLens 2 允许开发人员使用有关用户正在查看的内容的信息，从而实现全新的上下文和人工理解。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼睛跟踪，混合现实，输入，眼睛，校准
ms.openlocfilehash: 88c1827d3656ceb851e8f778daa2303b88dd17c8
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913219"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2 中的眼动跟踪

![MRTK 中的眼睛跟踪演示](images/mrtk_et_scenemenu.jpg)

HoloLens 2 允许开发人员使用有关用户正在查看的内容的信息，从而实现全新的上下文和人工理解。 本页告诉开发人员如何从各种用例的目视跟踪中获益，以及在设计基于目视的用户交互时要查找的内容。 

目视跟踪 API 的设计目的在于用户的隐私，避免传递任何可识别信息，尤其是任何生物识别。 对于支持目视跟踪的应用程序，用户需要授予应用程序权限才能使用目视跟踪信息。 


### <a name="device-support"></a>设备支持
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

<br>

## <a name="calibration"></a>校准 
为了使目视跟踪能准确地工作，每个用户都需要经历[跟踪用户校准](calibration.md)，用户必须查看一组全息目标。 这允许设备调整系统，以便为用户提供更舒适和更高的质量查看体验，并确保同时进行准确的目视跟踪。 

目视跟踪应该适用于大多数用户，但在极少数情况下，用户可能无法成功校准。 校准可能因多种原因而失败，其中包括但不限于： 
* 用户以前选择退出校准过程
* 用户已分散注意力，未遵循校准目标
* 用户具有特定类型的 contact 重用功能区和眼镜，其中系统尚不支持 
* 用户具有某些眼睛 physiology、目视的状况，或者系统尚不支持的目视外科  
* 外部因素抑制了可靠的眼睛跟踪，如污迹面板上的污迹、眼镜、强烈的直接阳光和 occlusions，因为眼睛正面的头发

开发人员应确保向用户提供对目视跟踪数据可能不可用的适当支持（无法成功校准）。 我们已在本页底部的部分中提供了有关后备解决方案的建议。 

若要了解有关校准的详细信息以及如何确保流畅的体验，请查看我们的[眼睛跟踪用户校准](calibration.md)页面。

<br>

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
例如，这种情况的范围包括：只需查看全息影像并显示 *"选择"* （另请参阅 "注视" 和 "[提交](gaze-and-commit.md)"），或者说 *"put ..."* ，然后查看用户想要放置全息图，并说 *".。。出现 "* 。 在[混合现实工具包 - 视线支持的目标选择](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)和[混合现实工具包 - 视线支持的目标定位](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)中可以找到相关示例。

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
有关用户所在位置或位置的信息可以是非常强大的工具，它可帮助评估设计的可用性并识别工作流中的问题，使其更有效。
目视跟踪可视化和分析是各种应用程序领域的常见做法。 在 HoloLens 2 中，我们提供了一种新的维度来理解，因为3D 全息图可以放置在真实的上下文中并进行相应的评估。 [混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)提供了用于记录和加载目视跟踪数据的基本示例，以及如何对其进行可视化。
Microsoft 致力于推动创新，同时确保向用户提供有关如何使用其眼睛跟踪信息的信息。  我们将与我们的开发人员和 UX 团队合作，为第三方提供指导，以确保在用户的中心获得经验。  


此领域的其他应用场景包括： 
-   **远程目视视觉视觉对象：** 远程目视目视可视化：直观显示远程协作者正在查看的内容，以便能够提供即时反馈并加速更准确的信息处理。
-   **用户研究研究：** 关注跟踪可帮助研究人员更深入地了解用户如何感觉和与自然环境交互，而不干扰，设计 instinctual 的人机交互。 目视跟踪可以提供调查中的参与者不能直接表述的信息，这种情况可能很容易被研究人员错过。 
-   **培训和性能监视：** 通过在执行流中更有效地识别瓶颈，来实践和优化任务的执行。 目视跟踪可以提供自然、实时和客观的信息，以帮助提高工作场所的培训、工作效率和安全性。 
-   **设计评估、营销和消费者研究：** 使用目视跟踪，商业公司可以在真实环境中执行市场营销和消费者调查，或者分析捕获用户对改善产品或空间设计的关注的内容。 

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
 
## <a name="fallback-solutions-when-eye-tracking-is-not-available"></a>目视跟踪不可用时的回退解决方案

在极少数情况下，目视跟踪数据可能不可用。
这可能是由于下面列出了最常见的原因：
* 系统未能[校准用户](calibration.md)。
* 用户跳过了[校准](calibration.md)。   
* 用户进行了校准，但决定不向应用程序授予使用其眼睛跟踪数据的权限。    
* 用户具有唯一的眼镜，或系统尚不支持的某种眼睛状态。    
* 外部因素抑制了一种可靠的眼睛跟踪，如在眼睛前面的头发上出现污迹面板或眼镜、强烈直接阳光和 occlusions。   

因此，开发人员应确保为这些用户提供适当的后备支持。 在 " [DirectX 中的目视跟踪](gaze-in-directx.md#fallback-when-eye-tracking-is-not-available)" 页上，我们介绍了检测目视跟踪数据是否可用所需的 api。 

尽管某些用户可能已特意决定撤消对其眼睛跟踪数据的访问，但对于不提供对其眼睛跟踪数据的访问权限的隐私性的用户体验的不满，这一点很有可能是不可能的。  
因此，如果你的应用程序使用目视跟踪，并且这是体验的重要部分，我们建议你清楚地将此信息传递给用户。     
请通知用户，目视跟踪对于你的应用程序至关重要（甚至可能会列出一些增强的功能）以充分利用你的应用程序，从而帮助用户更好地了解他们所放弃的内容。    
帮助用户确定目视跟踪可能不工作的原因（基于上述检查），并提供一些建议来快速解决潜在问题。  
例如，如果您可以检测到系统支持目视跟踪，则用户会进行校准，甚至会获得其权限，但不会收到任何眼睛跟踪数据，这可能会导致某些其他问题，如污迹或眼睛封闭像素。    
但请注意，在某些情况下，眼睛跟踪可能只是不能正常工作。    
因此，在应用中启用眼睛跟踪时，可以通过允许消除甚至禁用提醒来过于这种情况。

### <a name="fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>使用红眼作为主要输入指针的应用回退
如果你的应用程序使用目视看眼作为指针输入来快速选择场景中的全息影像，但眼睛跟踪数据不可用，则建议回退到打印头并开始显示眼睛良好的光标。 建议使用超时值（例如500–1500毫秒）来确定是否要切换。 这是为了防止在系统每次由于快速目视动作或传情动漫或传情动漫而发生跟踪时弹出游标。 如果你是一名 Unity 开发人员，则已在混合现实工具包中处理自动回退到打印头。 如果你是 DirectX 开发人员，则需要自行处理此开关。

### <a name="fallback-for-other-eye-tracking-specific-applications"></a>其他目视跟踪特定应用程序的回退
您的应用程序可以采用专门为眼睛定制的独特方式（例如，为头像形象提供动画或基于眼睛的关注热图，它依赖于有关视觉对象的精确信息）。 在这种情况下，不会有任何明确的回退。 如果目视跟踪不可用，则可能只需禁用这些功能。
同样，我们建议你清楚地将其传达给可能未意识到该功能无法正常工作的用户。

<br>

在此页面中，你可以获得一个良好的概述，使你开始了解 HoloLens 2 的眼睛跟踪和目视眼睛输入的角色。 若要开始开发，请查看我们的信息，了解如何[与全息影像交互](eye-gaze-interaction.md)、[在 Unity 中目视](https://aka.ms/mrtk-eyes)看，以及如何[在 DirectX 中观看眼](gaze-in-directx.md)。


## <a name="see-also"></a>另请参阅
* [校准](calibration.md)
* [舒适](comfort.md)
* [基于眼睛凝视的交互](eye-gaze-interaction.md)
* [目视观察 DirectX](gaze-in-directx.md)
* [目视看 Unity （混合现实工具包）](https://aka.ms/mrtk-eyes)
* [凝视和提交](gaze-and-commit.md)
* [语音输入](voice-design.md)


