---
title: 入门教程-6。 浏览高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129596"
---
# <a name="6-exploring-advanced-input-options"></a>6. 浏览高级输入选项

在本教程中，你将了解 HoloLens 2 的几个高级输入选项，包括使用语音命令、平移手势和目视跟踪。

## <a name="objectives"></a>目标

* 使用声音命令和关键字触发事件
* 使用跟踪的指针通过跟踪的手平移纹理和3D 对象
* 利用 HoloLens 2 目视跟踪功能选择对象

## <a name="enabling-voice-commands"></a>启用语音命令
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

在本部分中，你将实现一个语音命令，让用户在八对象上播放声音。 为此，您将创建一个新的语音命令，然后配置该事件，以便在口述语音命令关键字时触发所需的操作。

为实现此目的需要执行的主要步骤如下：

1. 克隆默认输入系统配置文件
2. 克隆默认的语音命令配置文件
3. 创建新的语音命令
4. 添加和配置语音输入处理程序（脚本）组件
5. 实现语音命令的响应事件

### <a name="1-clone-the-default-input-system-profile"></a>1. 克隆默认输入系统配置文件

在 "层次结构" 窗口中，选择 " **MixedRealityToolkit** " 对象，然后在 "检查器" 窗口中，选择 "**输入**" 选项卡并克隆**DefaultHoloLens2InputSystemProfile** ，将其替换为你自己的可自定义**输入系统配置文件**：

![mrlearning](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提醒，可以参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)说明。

### <a name="2-clone-the-default-speech-commands-profile"></a>2. 克隆默认语音命令配置文件

展开 "**语音**" 部分，克隆**DefaultMixedRealitySpeechCommandsProfile**以将其替换为你自己的可自定义**语音命令配置文件**：

![mrlearning](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. 创建新的语音命令

在 "**语音命令**" 部分中，单击 " **+ 添加新语音命令**" 按钮，在现有语音命令列表的底部添加新的语音命令，然后在**关键字**字段中输入合适的词或短语，例如**播放音乐**：

![mrlearning](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> 如果您的计算机没有麦克风，并且您想要使用编辑器内模拟来测试语音命令，则可以将 KeyCode 分配给语音命令，以便在按下相应的键时触发它。

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. 添加和配置语音输入处理程序（脚本）组件

在 "层次结构" 窗口中，选择 "**八**" 对象，并将**语音输入处理程序（脚本）** 组件添加到八对象。 然后取消选中 "**是否需要焦点**" 复选框，以便用户无需查看八对象即可触发语音命令：

![mrlearning](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. 实现语音命令的响应事件

在语音输入处理程序（脚本）组件上，单击 "小 **+** " 按钮添加关键字，然后在 "**关键字**" 下拉列表中，选择之前创建的 "**播放音乐**" 关键字：

![mrlearning](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> 关键字下拉列表中的关键字根据语音命令配置文件中的 "语音命令" 列表中定义的关键字进行填充。

创建新的**响应（）** 事件，配置**八**对象以接收事件，将**AudioSource**定义为要触发的操作，并将适当的音频剪辑分配给**音频剪辑**字段，例如 MRTK_Gem 音频剪辑：

![mrlearning](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> 若要提醒如何实现事件和分配音频剪辑，可以参阅按[触控开始执行事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)说明。

## <a name="the-pan-gesture"></a>平移手势

平移手势对于使用手指或手滚动内容滚动很有用。 在此示例中，您将首先了解如何滚动 2D UI，然后将其展开以便能够滚动浏览三维对象的集合。

为实现此目的需要执行的主要步骤如下：

1. 创建可用于平移的四个对象
2. 添加 Near 交互可触摸（脚本）组件
3. 添加手写交互平移缩放（脚本）组件
4. 添加要滚动的2D 内容
5. 添加三维内容滚动
6. 添加带平移（脚本）组件的移动

> [!NOTE]
> 带平移（脚本）组件的移动不是 MRTK 的一部分。 本教程提供了本教程的资产。

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. 创建可用于平移的四个对象

在 "层次结构" 窗口中，右键单击空白区域，并选择 " **3D 对象** > **四**个"，将 "四个" 添加到场景中。 为它提供适当的名称（例如**PanGesture**），并将其放置在合适的位置，例如 X = 0、Y =-0.2、Z = 2。

![mrlearning](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 有关如何向场景中添加 Unity 基元（如三维四类）的提醒，可以参阅[将多维数据集添加到场景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)说明。

与任何其他交互一样，平移手势还需要碰撞器。 默认情况下，四个网络有一个网格碰撞器。 但是，网格碰撞器并不理想，因为它非常精简。 为了使用户能够更轻松地与碰撞器进行交互，我们将使用箱碰撞器替换网格碰撞器。

在仍选择 PanGesture 对象的情况下，单击**网格碰撞**器组件的**设置**图标，然后选择 "**删除组件**" 以删除网格碰撞器：

![mrlearning](images/mrlearning-base/tutorial5-section2-step1-2.png)

在 "检查器" 窗口中，使用 "**添加组件**" 按钮添加一个**框碰撞**器，然后将 box 碰撞器**大小**Z 改为0.15 以增加框碰撞器的厚度：

![mrlearning](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. 添加 Near 交互可触摸（脚本）组件

在仍选择**PanGesture**对象的情况下，将**near 交互可触摸（脚本）** 组件添加到 PanGesture 对象，然后单击 "**修复边界**" 和 "**修复中心**" 按钮，更新接近交互可触摸（脚本）的局部中心和边界属性，使之与 BoxCollider 匹配：

![mrlearning](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. 添加手写交互平移缩放（脚本）组件

在仍选择**PanGesture**对象的情况下，将**手写交互平移缩放（脚本）** 组件添加到 PanGesture 对象，然后选中 "**锁定水平**" 复选框以仅允许垂直滚动：

![mrlearning](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. 添加要滚动的2D 内容

在 "项目" 面板中，搜索**PanContent**材料，然后单击并将其拖动到**PanGesture**对象的 "网状呈现器**材料**元素 0" 属性：

![mrlearning](images/mrlearning-base/tutorial5-section2-step4-1.png)

在 "检查器" 窗口中，展开新添加的 " **PanContent**材料" 组件，然后将其 "**平铺**Y" 值更改为0.5，使其与 X 值匹配，磁贴显示为方形：

![mrlearning](images/mrlearning-base/tutorial5-section2-step4-2.png)

如果你现在进入游戏模式，则可以使用编辑器内模拟中的平移手势来测试是否滚动2D 内容：

![mrlearning](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. 添加要滚动的3D 内容

在 "层次结构" 窗口中，将**四个多维数据集创建**为**PanContent**的子对象，并将其转换**比例**设置为 X = 0.15，Y = 0.15，Z = 0.15：

![mrlearning](images/mrlearning-base/tutorial5-section2-step5-1.png)

若要将多维数据集均匀地缩小，并保存一些时间，请将网格对象集合（脚本）组件添加到多维数据集的父对象（即 PanGesture 对象），并按如下所示配置网格对象集合（脚本）：

* 将**Num 行**更改为1，使所有多维数据集在一行上对齐
* 将**单元格宽度**更改为0.25，以将行内的多维数据集变为空白

然后单击 "**更新集合**" 按钮应用新配置：

![mrlearning](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. 添加带平移（脚本）组件的移动

在 "层次结构" 窗口中，选择所有**多维数据集子对象**，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**Move （Script）** 组件添加到所有多维数据集：

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> 有关如何在 "层次结构" 窗口中选择多个对象的提醒，tou 可以参考[将操作处理程序（脚本）组件添加到所有对象](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)指令中。

在仍选择了所有多维数据集的情况下，单击 " **PanGesture** " 对象并将其拖至 "**平移输入源**" 字段：

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 每个多维数据集上的 "在移动时使用平移（脚本）" 组件会侦听 PanGesture 对象上的 HandInteractionPanZoom （Script）组件发送的平移更新事件，在上面的步骤中已将该对象指定为平移输入源，并更新每个多维数据集的位置并.

在 "层次结构" 窗口中，选择 " **PanGesture** " 对象，然后在 "检查器" 中**取消选中**"**网格呈现**器" 复选框，以禁用网格呈现器组件：

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-3.png)

如果你现在进入游戏模式，则可以使用编辑器内模拟中的平移手势测试滚动3D 内容：

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>眼动跟踪

在本部分中，你将了解如何在项目中启用目视跟踪。 在此示例中，你将实现一些功能，使3DObjectCollection 中的每个对象在用户眼睛眼睛查看时慢慢旋转，并在通过 "轻敲" 或 "语音" 命令选择要查看的对象时触发故障效果。

为实现此目的需要执行的主要步骤如下：

1. 将目视跟踪目标（脚本）组件添加到所有目标对象
2. 将目视跟踪教程演示（脚本）组件添加到所有目标对象
3. 在查看目标事件时实现
4. 实现所选事件
5. 为编辑器内模拟启用模拟的目视跟踪
6. 在 Visual Studio 项目的应用功能中启用注视输入

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. 将目视跟踪目标（脚本）组件添加到所有目标对象

在 "层次结构" 窗口中，展开 " **3DObjectCollection** " 对象并选择所有**子对象**，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**眼睛跟踪目标（脚本）** 组件添加到所有子对象：

![mrlearning](images/mrlearning-base/tutorial5-section3-step1-1.png)

在仍选择所有**子对象**的情况下，按如下所示配置**目视跟踪目标（脚本）** 组件：

* 更改**选择操作**以**选择**，将此对象的 "空中点击" 操作定义为 "选择"
* 展开**语音选择**，将语音命令列表**大小**设置为1，然后在显示的新元素列表中，将**元素 0**更改为**选择**，以将此对象的语音命令操作定义为 "选择"

![mrlearning](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. 将目视跟踪教程演示（脚本）组件添加到所有目标对象

在仍选择所有**子对象**的情况下，使用 "**添加组件**" 按钮将**目视跟踪教程演示（脚本）** 组件添加到所有子对象：

![mrlearning](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> 眼睛跟踪目标（脚本）组件不是 MRTK 的一部分。 本教程提供了本教程的资产。

### <a name="3-implement-the-while-looking-at-target-event"></a>3. 在查看目标事件时实现

在 "层次结构" 窗口中，选择 "**奶酪**" 对象，然后在 "**查看目标（）** " 事件时创建一个新的，配置**奶酪**对象以接收事件，并将**EyeTrackingTutorialDemo**定义为要触发的操作：

![mrlearning](images/mrlearning-base/tutorial5-section3-step3-1.png)

对3DObjectCollection 中的每个子对象**重复**此操作。

> [!TIP]
> 有关如何实现事件的提醒，可参阅 "[手动跟踪手势" 和 "种不可交互" 按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)说明。

### <a name="4-implement-the-on-selected-event"></a>4. 实现所选事件

在 "层次结构" 窗口中，选择 "**奶酪**" 对象，然后**在所选（）事件上**创建新的，将**奶酪**对象配置为接收事件，并将**EyeTrackingTutorialDemo**定义为要触发的操作：

![mrlearning](images/mrlearning-base/tutorial5-section3-step4-1.png)

对3DObjectCollection 中的每个子对象**重复**此操作。

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. 为编辑器内模拟启用模拟的目视跟踪

在 "层次结构" 窗口中，选择 " **MixedRealityToolkit** " 对象，然后在 "检查器" 窗口中，选择 "**输入**" 选项卡，展开 "**输入数据访问接口**" 部分，然后展开 "**输入模拟服务**" 部分，并克隆**DefaultMixedRealityInputSimulationProfile** ，将其替换为你自己的可自定义**输入模拟配置文件**：

![mrlearning](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提醒，可以参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)说明。

在 "**目视模拟**" 部分中，选中 "**模拟眼睛位置**" 复选框以启用目视跟踪模拟：

![mrlearning](images/mrlearning-base/tutorial5-section3-step5-2.png)

如果你现在进入游戏模式，则可以通过调整视图来测试你实现的旋转和故障效果，使光标点击其中一个对象，并使用 "手动交互" 或 "语音" 命令选择对象：

![mrlearning](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> 如果未使用 DefaultHoloLens2ConfigurationProfile 克隆可自定义的 MRTK 配置文件，如[配置混合现实工具包](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)说明中所述，可能无法在项目中启用目视跟踪并且需要启用。 为此，可以参阅[MRTK 说明中的目视跟踪](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)入门。

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. 在 Visual Studio 项目的应用功能中启用注视输入

在从 Visual Studio 生成应用并将其部署到设备之前，必须在项目的应用功能中启用 "注视输入"。 为此，可以按照[HoloLens 2 说明测试 Unity 应用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)。

## <a name="congratulations"></a>祝贺你

已成功将基本的目视跟踪功能添加到应用程序。 这些操作仅为眼动跟踪实现的探索领域开了一个头。 在本教程中，您还了解了其他高级输入功能，如语音命令和平移手势。

[下一课： 7. 创建农历模块示例应用程序](mrlearning-base-ch6.md)
