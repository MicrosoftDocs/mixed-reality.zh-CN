---
title: 入门教程 - 6. 探索高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376084"
---
# <a name="6-exploring-advanced-input-options"></a>6.探索高级输入选项

本教程探讨 HoloLens 2 的几个高级输入选项，包括语音命令、平移手势和眼动跟踪的用法。

## <a name="objectives"></a>目标

* 使用语音命令和关键字触发事件
* 使用跟踪手平移纹理和 3D 对象
* 利用 HoloLens 2 眼动跟踪功能选择对象

## <a name="enabling-voice-commands"></a>启用语音命令
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

在本部分，你将实现一个语音命令来让用户在 Octa 对象中播放声音。 为此，你将创建一个新的语音命令，然后配置事件，以便在讲出语音命令关键字时触发所需的操作。

若要实现此目的，请执行以下主要步骤：

1. 克隆默认的输入系统配置文件
2. 克隆默认的语音命令配置文件
3. 创建新的语音命令
4. 添加并配置“语音输入处理程序(脚本)”组件
5. 实现语音命令的响应事件

### <a name="1-clone-the-default-input-system-profile"></a>1.克隆默认的输入系统配置文件

在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“输入”选项卡，并克隆“DefaultHoloLens2InputSystemProfile”，以将其替换为你自己的可自定义**输入系统配置文件**：   

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提示，可参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明。

### <a name="2-clone-the-default-speech-commands-profile"></a>2.克隆默认的语音命令配置文件

展开“语音”部分，克隆“DefaultMixedRealitySpeechCommandsProfile”以将其替换为你自己的可自定义**语音命令配置文件**：  

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3.创建新的语音命令

在“语音命令”部分，单击“+ 添加新的语音命令”按钮以在现有语音命令列表的底部添加一个新的语音命令，然后在“关键字”字段中输入适当的单词或短语，例如“播放音乐”：    

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> 如果计算机上没有麦克风，而你想要使用编辑器中的模拟功能来测试语音命令，可将一个 KeyCode 分配到语音命令，以便在按下相应的键时触发该命令。

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4.添加并配置“语音输入处理程序(脚本)”组件

在“层次结构”窗口中选择“Octa”对象，并将“语音输入处理程序(脚本)”组件添加到该 Octa 对象。   然后取消选中“需要焦点”复选框，使用户无需查看 Octa 对象即可触发语音命令： 

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5.实现语音命令的响应事件

在“语音输入处理程序(脚本)”组件中，单击 **+** 小按钮将一个关键字元素添加到关键字列表中：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

单击新建的“元素 0”将其展开，然后从“关键字”下拉列表中，选择前面创建的“播放音乐”关键字：   

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> 关键字下拉列表中的关键字是根据语音命令配置文件中“语音命令”列表内定义的关键字填充的。

创建新的 **Response ()** 事件，配置 **Octa** 对象用于接收该事件，将 **AudioSource.PlayOneShot** 定义为要触发的操作，然后将适当的音频剪辑（例如 MRTK_Gem 音频剪辑）分配到“音频剪辑”字段： 

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> 有关如何实现事件和分配音频剪辑的提示，可参阅[实现 On Touch Started 事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)中的说明。

## <a name="the-pan-gesture"></a>平移手势

平移手势非常有用，可让你用手指或手滚动浏览内容。 此示例首先演示如何滚动 2D UI，然后演示如何将其展开，以便能够滚动浏览 3D 对象的集合。

若要实现此目的，请执行以下主要步骤：

1. 创建可用于平移的 Quad 对象
2. 添加“近距交互可触摸对象(脚本)”组件
3. 添加“手动交互平移缩放(脚本)”组件
4. 添加要滚动的 2D 内容
5. 添加要滚动的 3D 内容
6. 添加“平移移动(脚本)”组件

> [!NOTE]
> MRTK 中未包含“平移移动(脚本)”组件。 本教程的资产中随附了该组件。

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1.创建可用于平移的 Quad 对象

在“层次结构”窗口中右键单击某个空白区域，然后选择“3D 对象” > “Quad”，将一个四面体添加到场景中。   为此对象指定适当的名称（例如 **PanGesture**），并将其定位在合适的位置，例如 X = 0，Y = -0.2，Z = 2。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 有关如何在场景中添加 Unity 基元（例如 3D 四面体）的提示，可参阅[将立方体添加到场景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)中的说明。

与任何其他交互方式一样，平移手势也需要一个碰撞体。 默认情况下，四面体具有网格碰撞体。 但是，该网格碰撞体并不理想，因为它非常小。 为使用户能够更轻松地与碰撞体交互，我们将使用一个盒碰撞体替换网格碰撞体。

在仍选中了 PanGesture 对象的情况下，单击“网格碰撞体”组件的“设置”图标，然后选择“删除组件”以删除网格碰撞体：   

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

在“检查器”窗口中，使用“添加组件”按钮添加一个**盒碰撞体**，然后将盒碰撞体的 Z 轴“大小”更改为 0.15，以增大盒碰撞体的厚度：  

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2.添加“近距交互可触摸对象(脚本)”组件

在仍选中了“PanGesture”对象的情况下，将“近距交互可触摸(脚本)”组件添加到 PanGesture 对象，然后单击“拟合边界”和“拟合中点”按钮，以更新“近距交互可触摸(脚本)”组件的“局部中点”和“边界”属性，使之与 BoxCollider 匹配：    

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3.添加“手动交互平移缩放(脚本)”组件

在仍选中了“PanGesture”对象的情况下，将“手动交互平移缩放(脚本)”组件添加到 PanGesture 对象，然后选中“水平锁定”复选框，以便仅允许垂直滚动：   

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4.添加要滚动的 2D 内容

在“项目”面板中搜索 **PanContent** 材料，然后单击并将其拖放到“PanGesture”对象的网格渲染器“材料”元素 0 属性：  

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

在“检查器”窗口中，展开新添加的“PanContent”材料组件，然后将其“图块”Y 轴值更改为 0.5，使之与 X 轴值匹配，并使图块显示为正方形：  

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

如果现在进入“游戏”模式，可以使用编辑器中模拟功能的平移手势来测试滚动 2D 内容：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5.添加要滚动的 3D 内容

在“层次结构”窗口中，**创建四个立方体**作为 **PanGesture** 对象的子对象，并将其变换**标度**设置为 X = 0.15，Y = 0.15，Z = 0.15：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

若要均匀隔开立方体并节省时间，请将“网格对象集合(脚本)”组件添加到立方体的父对象（即 **PanGesture** 对象），并按如下所述配置“网格对象集合(脚本)”： 

* 将“行数”更改为 1，使所有立方体在一行中对齐 
* 将“单元格宽度”更改为 0.25，以隔开行中的立方体 

然后单击“更新集合”按钮以应用新配置： 

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6.添加“平移移动(脚本)”组件

在“层次结构”窗口中选择所有**立方体子对象**，然后在“检查器”窗口中，使用“添加组件”按钮将“平移移动(脚本)”组件添加到所有立方体：  

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> 有关如何在“层次结构”窗口中选择多个对象的提示，可参阅[将“操作处理程序(脚本)”组件添加到所有对象](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)中的说明。

在仍选中了所有立方体的情况下，单击“PanGesture”对象并将其拖放到“平移输入源”字段中：  

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 每个立方体上的“平移移动(脚本)”组件将会侦听 PanGesture 对象（在上一步骤中已将其分配为“平移输入源”）上的“HandInteractionPanZoom (脚本)”组件发送的 Pan Updated 事件，并相应地更新每个立方体的位置。

在“层次结构”窗口中选择“PanGesture”对象，然后在“检查器”中**取消选中**“网格渲染器”复选框，以禁用“网格渲染器”组件：  

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

如果现在进入“游戏”模式，可以使用编辑器中模拟功能的平移手势来测试滚动 3D 内容：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>眼动跟踪

本部分探讨如何在项目中启用眼动跟踪。 此示例将实现相应的功能，使 3DObjectCollection 中的每个对象在用户视线的注视下缓慢旋转，并在通过隔空敲击或语音命令选择要注视的对象时触发光点效果。

若要实现此目的，请执行以下主要步骤：

1. 将“眼动跟踪目标(脚本)”组件添加到所有目标对象
2. 将“眼动跟踪教程演示(脚本)”组件添加到所有目标对象
3. 实现 While Looking At Target 事件
4. 实现 On Selected 事件
5. 为编辑器中的模拟启用模拟眼动跟踪
6. 在 Visual Studio 项目的应用功能中启用视线输入

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1.将“眼动跟踪目标(脚本)”组件添加到所有目标对象

在“层次结构”窗口中展开“3DObjectCollection”对象并选择所有**子对象**，然后在“检查器”窗口中，使用“添加组件”按钮将“眼动跟踪目标(脚本)”组件添加到所有子对象：   

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

在仍选中了所有**子对象**的情况下，按如下所述配置“眼动跟踪目标(脚本)”组件： 

* 将“选择操作”更改为“选择”，以将此对象的隔空敲击操作定义为“选择”  
* 展开“语音选择”并将语音命令列表的“大小”设置为 1，然后在显示的新元素列表中，将“元素 0”更改为“选择”，以将此对象的语音命令操作定义为“选择”    

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2.将“眼动跟踪教程演示(脚本)”组件添加到所有目标对象

在仍选中了所有**子对象**的情况下，使用“添加组件”按钮将“眼动跟踪教程演示(脚本)”组件添加到所有子对象：  

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> MRTK 中不包含“眼动跟踪目标(脚本)”组件。 本教程的资产中随附了该组件。

### <a name="3-implement-the-while-looking-at-target-event"></a>3.实现 While Looking At Target 事件

在“层次结构”窗口中选择“Cheese”对象，创建一个新的 **While Looking At Target ()** 事件，将“Cheese”对象配置为接收该事件，然后将“EyeTrackingTutorialDemo.RotateTarget”定义为要触发的操作：   

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

针对 3DObjectCollection 中的每个子对象**重复**上述步骤。

> [!TIP]
> 有关如何实现事件的提示，可参阅[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)中的说明。

### <a name="4-implement-the-on-selected-event"></a>4.实现 On Selected 事件

在“层次结构”窗口中选择“Cheese”对象，创建一个新的 **On Selected ()** 事件，将“Cheese”对象配置为接收该事件，然后将“EyeTrackingTutorialDemo.BlipTarget”定义为要触发的操作：   

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

针对 3DObjectCollection 中的每个子对象**重复**上述步骤。

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5.为编辑器中的模拟启用模拟眼动跟踪

在“层次结构”窗口中选择“MixedRealityToolkit”对象，在“检查器”窗口中选择“输入”选项卡，展开“输入数据提供程序”部分，展开“输入模拟服务”部分，然后克隆“DefaultMixedRealityInputSimulationProfile”，以将其替换为你自己的可自定义**输入模拟配置文件**：     

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提示，可参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明。

在“眼动模拟”部分，选中“模拟眼睛位置”复选框以启用眼动跟踪模拟：  

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

如果现在进入“游戏”模式，可以测试实现的旋转和光点效果，方法是调整视图，使游标位于某个对象上，然后使用手动交互或语音命令来选择对象：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> 如果尚未根据[配置混合现实工具包](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)中的说明使用 DefaultHoloLens2ConfigurationProfile 克隆可自定义的 MRTK 配置配置文件，则眼动跟踪可能未在项目中启用，现在需要启用。 为此，可参阅 [MRTK 中的眼动跟踪入门](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)中的说明。

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6.在 Visual Studio 项目的应用功能中启用视线输入

在从 Visual Studio 生成应用并将其部署到设备之前，必须在项目的应用功能中启用“视线输入”。 为此，可以按照[在 HoloLens 2 上测试 Unity 应用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)中的说明进行操作。

## <a name="congratulations"></a>祝贺

现已将基本的眼动跟踪功能成功添加到应用程序。 这些操作仅为眼动跟踪实现的探索领域开了一个头。 本教程还介绍了其他高级输入功能，例如语音命令和平移手势。

[下一课：7.创建登月舱示例应用程序](mrlearning-base-ch6.md)
