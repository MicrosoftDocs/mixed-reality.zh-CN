---
title: 入门教程-6。 浏览高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 75a14697953026474d8ca00e6473145d7b12a482
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334351"
---
# <a name="6-exploring-advanced-input-options"></a>6. 浏览高级输入选项

在本教程中，将探索 HoloLens 2 的几个高级输入选项，包括使用语音命令、平移手势和目视跟踪。 

## <a name="objectives"></a>目标

- 使用声音命令和关键字触发事件
- 使用跟踪的指针通过跟踪的手平移纹理和3D 对象
- 利用 HoloLens 2 目视跟踪功能选择对象

## <a name="enabling-voice-commands"></a>启用语音命令

本部分实现了两个语音命令。 首先，通过显示 "切换诊断"，可以切换帧速率诊断面板。 其次，可以通过语音命令播放声音。 首先查看负责配置语音命令的 MRTK 配置文件和设置。

1. 在 BaseScene 层次结构中，选择 MixedRealityToolkit。 然后，在 "检查器" 面板中，选择 "输入"，然后单击 "DefaultMixedRealityInputSystemProfile" 左侧的 "小克隆" 按钮，以打开 "克隆配置文件" 弹出窗口。 在弹出窗口中，单击 "克隆" 以创建新的配置文件 MixedRealityInputSystemProfile。

    ![mrlearning-base-ch5-1-step1a .png](images/mrlearning-base-ch5-1-step1a.png)

    这也会自动填充 MixedRealityToolkitConfigurationProfile 和新创建的 MixedRealityInputSystemProfile。

    ![mrlearning-base-ch5-1-step1b .png](images/mrlearning-base-ch5-1-step1b.png)

2. 在输入系统配置文件中，有各种设置。 对于语音命令，展开 "语音" 部分并按照上一步骤中所述的过程进行操作，以克隆 DefaultMixedRealitySpeechCommandsProfile 并将其替换为你自己的可编辑副本。

    ![mrlearning-base-ch5-1-step2 .png](images/mrlearning-base-ch5-1-step2.png)

    在语音命令配置文件中，你会注意到一系列设置。 有关这些设置的完整说明，请参阅[MRTK speech 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。

    默认情况下，一般行为是自动启动。 如果需要，可以将其更改为手动-启动。 但在此示例中，请将其保留为自动启动。 MRTK 附带了几个默认的语音命令，如菜单、切换诊断和切换探查器。 我们将使用关键字 "切换诊断" 来打开和关闭 "诊断帧速率" 计数器。 在以下步骤中，我们还将添加一个新的语音命令。

3. 添加新的语音命令。 为此，请单击 "+ 添加新的语音命令" 按钮。 你将看到一个新行，出现在现有语音命令列表下。 键入要使用的语音命令。 在此示例中，使用命令 "播放音乐"。

    ![mrlearning-base-ch5-1-step3 .png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >还可为语音命令设置键码。 这允许语音命令在按键时触发事件。

4. 添加响应语音命令的功能。 选择 BaseScene 层次结构中未附加任何其他输入脚本的任何对象，例如 MixedRealityPlayspace 游戏对象。 在检查器面板中，单击 "添加组件"，搜索 "语音"，然后选择语音输入处理程序脚本。

    ![mrlearning-base-ch5-1-step4 .png](images/mrlearning-base-ch5-1-step4.png)

    默认情况下，你将看到两个复选框。 其中一个是 "是否需要焦点" 复选框。 因此，只要您将鼠标指针指向具有眼睛眼睛、看好、看看或手工看的对象，就会触发语音命令。 取消选中此复选框，以便用户不必查看对象即可使用语音命令。

5. 添加响应语音命令的功能。 为此，请单击语音输入处理程序中的 "+" 按钮。

    ![mrlearning-base-ch5-1-step5 .png](images/mrlearning-base-ch5-1-step5.png)

6. 在关键字旁边，可以看到一个下拉菜单。 选择 "切换诊断"，以便每当用户显示短语 "切换诊断" 时，都会触发一个操作。 请注意，您可能需要通过按下箭头旁边的箭头来展开元素0。

    ![mrlearning-base-ch5-1-step6 .png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >根据你在步骤3中编辑的配置文件填充这些关键字。

7. 添加 "诊断系统" 语音控件脚本，以打开和关闭计数器计数器诊断。 为此，请按 "添加组件"，搜索 "诊断系统语音控制脚本"，然后从菜单添加它。 此脚本可添加到任何对象，但为了简单起见，我们将其添加到语音输入处理程序所在的同一对象。

    ![mrlearning-base-ch5-1-step7 .png](images/mrlearning-base-ch5-1-step7.png)

8. 在语音输入处理程序中添加新的响应。 为此，请单击 "+" 图标，将新响应添加到响应列表。

    ![mrlearning-base-ch5-1-step8 .png](images/mrlearning-base-ch5-1-step8.png)

9. 将具有诊断系统语音控制脚本的对象拖到您在上一步中刚创建的新响应。

    ![mrlearning-base-ch5-1-step9 .png](images/mrlearning-base-ch5-1-step9.png)

10. 单击 "函数" 下拉列表（其中不显示 "函数"），然后选择 "诊断系统语音控制"，然后选择 ToggleDiagnostics （）函数，以打开和关闭诊断。

    ![mrlearning-base-ch5-1-step10 .png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > 在生成到设备之前，你需要启用 mic 设置。 为此，请单击 "文件"，然后依次单击 "生成设置" 和 "播放机设置"，并确保已设置麦克风功能。

    接下来，使用八对象添加从语音命令播放音频文件的功能。 从[第4课](mrlearning-base-ch4.md)中回忆，已添加了从触摸八对象播放音频剪辑的能力。 我们会将此音频源同样用于音乐语音命令。

11. 选择 BaseScene 层次结构中的八对象。

12. 添加另一个语音输入处理程序（重复步骤4和5），但包含八对象。

13. 添加 "播放音乐" 语音命令，而不是从步骤6添加 "切换诊断语音" 命令，如下图所示。

    ![mrlearning-base-ch5-1-step13 .png](images/mrlearning-base-ch5-1-step13.png)

14. 对于步骤8和9，添加一个新的响应，并将八对象（具有诊断系统语音控制脚本的对象）添加到空的响应槽。

15. 选择不显示函数的下拉菜单。 然后选择 "音频源"，然后选择 "PlayOneShot" （AudioClip）。

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 在此示例中，我们将使用[第4课](mrlearning-base-ch4.md)中的相同音频剪辑。 进入项目面板，搜索 "MRTK_Gem" 音频剪辑，并将其拖动到音频源槽，如下图所示。 现在，你的应用程序将响应语音命令 "切换诊断" 以切换 "帧速率" 计数器面板，并播放音乐来播放 MRTK_Gem 的歌曲。

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

## <a name="the-pan-gesture"></a>平移手势

在本部分中，你将学习如何使用平移手势。 这适用于使用手指或手滚动内容滚动。 你还可以使用平移手势来旋转对象、循环浏览三维对象的集合，甚至滚动 2D UI。

1. 创建一个四面体。 在 BaseScene 层次结构中，右键单击，选择 "3D 对象"，然后选择 "四个"。

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 根据需要重定位四部分。 对于我们的示例，我们将 x = 0、y = 0 和 z = 1.5 远离相机，以实现从 HoloLens 2 获得的舒适位置。

    >[!NOTE]
    >如果故障诊断块或位于前一课中的任何内容之前，请务必将其移动，使其不会阻止其他任何对象。

3. 将材料应用到四面体。 此材料将是使用平移手势滚动的内容。

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在 "项目" 面板的 "搜索" 框中键入 "平移内容"。 将该材料拖到场景中的四个部分。

    >[!NOTE]
    >PanContent 资料不是 MRTK 的一部分，而是在上一课中导入的 BaseModuleAssets 资产中包含。

    若要使用平移手势，需要在对象中添加一个碰撞体。 你可能会看到，四面体已有一个网格碰撞体。 但是，该网格碰撞体并不理想，因为它非常小，很难将其选中。 我们建议将网格碰撞体替换为盒碰撞体。

5. 右键单击 "检查器" 面板上的 "故障诊断" 中的网格碰撞器。 然后单击 "删除组件" 将其删除。

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 现在，通过单击 "添加组件" 并搜索 "box 碰撞器" 来添加框碰撞器。 默认添加的框碰撞器仍然太小，因此请单击 "编辑碰撞器" 按钮进行编辑。 按下该对象后，可以使用 x、y 和 z 值或场景编辑器中的元素来调整其大小。 对于本示例，我们希望盒碰撞体稍微靠在四面体的后面。 在场景编辑器中，将盒碰撞体往后朝外拖动（参考下图）。 这样，用户不仅可以使用手指，而且能滚动整个手。

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. 使对象具有交互能力。 由于我们希望直接与四个部分交互，我们想要使用在第4课中使用的近乎交互可触摸组件来播放八对象中的音乐。 单击 "添加组件"，搜索 "near 交互可触摸" 并将其选中，如下图所示。

    ![mrlearning-base-ch5-2-step7a .png](images/mrlearning-base-ch5-2-step7a.png)

    如果你看到有关边界和/或中心与 BoxCollider 大小和/或中心不匹配的黄色警告，请单击 "修复边界" 和/或 "修复中心" 按钮，更新中心和边界值。

    ![mrlearning-base-ch5-2-step7b .png](images/mrlearning-base-ch5-2-step7b.png)

8. 添加识别平移手势的功能。 单击 "添加组件"，在搜索字段中键入 "手工交互"，然后添加 "手写交互平移缩放脚本" 组件。

    ![mrlearning-base-ch5-2-step8a .png](images/mrlearning-base-ch5-2-step8a.png)

    这样就可以使用启用了平移的四核。

    正如您所看到的，手动交互平移缩放脚本组件具有各种设置，作为可选的练习，您可以自由地使用它们。

    ![mrlearning-base-ch5-2-step8b .png](images/mrlearning-base-ch5-2-step8b.png)

9. 接下来，我们了解如何平移 3D 对象。

    在层次结构中，右键单击 "四个对象"，打开上下文弹出菜单，然后选择 "**三维对象** > **多维数据集**" 将多维数据集添加到场景中。

    确保将多维数据集的**位置**设置为_0，0，0，_ 使其在四部分中整齐放置。 将多维数据集缩小为_0.1、0.1、0.1_的**小数位数**。

    ![mrlearning-base-ch5-2-step9 .png](images/mrlearning-base-ch5-2-step9.png)

    右键单击多维数据集，打开上下文快捷菜单并选择 "**复制**"，从而将多维数据集重复三次。

    将多维数据集均匀隔开。 场景应类似于下图。

10. 按住 CTRL 键的同时选择 "层次结构" 面板中的每个**多维数据集**对象，将 MoveWithPan 脚本添加到所有多维数据集。 在 "检查器" 面板中，单击 "添加组件"，然后搜索并选择 "**移动以平移**脚本"，将其添加到所有多维数据集。

    ![mrlearning-base-ch5-2-step10a .png](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    >MoveWithPan 脚本不是 MRTK 的一部分，而是在上一课中导入的 BaseModuleAssets 资产中包含。

    在仍选中多维数据集的情况下，将 "层次结构" 面板中的 "**四**个对象" 拖到 "**带平移的移动**脚本" 组件的 "**平移输入源**" 字段

    ![mrlearning-base-ch5-2-step10b .png](images/mrlearning-base-ch5-2-step10b.png)

    现在，多维数据集将随平移手势一起移动。

    >[!TIP]
    >每个多维数据集上的 MoveWithPan 实例侦听从四个对象上的 HandInteractionPanZoom 实例发送的 PanUpdated 事件，这些事件已添加到每个多维数据集上的 "平移输入源" 字段中，并相应地更新相应的多维数据集对象的位置。

    如果仍选中多维数据集，则将它们沿其 Z 轴向前移动，使每个多维数据集的网格位于**四**个**箱的碰撞**器中，方法是将其**位置 Z**值更改为_0.7_。

    ![mrlearning-base-ch5-2-step10c .png](images/mrlearning-base-ch5-2-step10c.png)

    现在，如果通过在 "检查器" 面板中取消选中并禁用**四**个 "**网格呈现**器" 组件，则会看到一个不可见的四个部分，可在其中平移3d 对象的列表。

    ![mrlearning-base-ch5-2-step10d .png](images/mrlearning-base-ch5-2-step10d.png)

## <a name="eye-tracking"></a>眼动跟踪

在本部分中，我们将探讨如何在演示中启用目视跟踪。 当您的3D 菜单项 gazed 时，我们将慢慢旋转它们。 此外，在选择所凝视的项时，我们还会触发一种有趣的效果。

1. 确保为目视跟踪正确配置 MRTK 配置文件。 若要执行此操作，请转到[MRTK 说明中的目视跟踪](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)入门，并通过查看[设置目视跟踪分步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)部分中的步骤来验证是否正确配置了目视跟踪。 完成文档中的所有剩余步骤。

    >[!NOTE]
    >如果使用 DefaultHoloLens2InputSystemProfile （如[配置混合现实工具包](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)课程中所述）来克隆自定义 MRTK 配置文件，则默认情况下会在 unity 项目中启用目视跟踪，但仍需为 unity 编辑器设置目视跟踪模拟，并将 Visual Studio 配置为允许对生成进行目视跟踪。

    上述链接提供了有关以下操作的简要说明：

    - 创建 Windows Mixed Reality 眼睛数据提供程序以在 MRTK 配置文件中使用
    - 在连接到相机的目视提供者中启用目视跟踪
    - 在 Unity 编辑器中设置目视跟踪模拟
    - 编辑 Visual Studio 解决方案的功能，以便在生成的应用程序中进行眼动跟踪

2. 将眼动跟踪目标组件添加到目标对象。 若要允许对象响应眼睛眼睛事件，我们需要使用目视注视将 EyeTrackingTarget 组件添加到要与之交互的每个对象上。 将此组件添加到网格集合中的每个（共九个）3D 对象。

    >[!TIP]
    >你可以使用 Shift 和/或 CRTL 键选择层次结构中的多个项，然后大容量添加 EyeTrackingTarget 组件。

    ![Lesson5 Chapter3 步骤2](images/Lesson5Chapter3Step2.JPG)

3. 接下来，我们将为一些激动人心的交互添加 EyeTrackingTutorialDemo 脚本。 对于网格集合中的每个三维对象，通过在 "添加组件" 菜单中搜索组件来添加 EyeTrackingTutorialDemo 脚本。

    ![Lesson5 Chapter3 步骤3](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    >EyeTrackingTutorialDemo 脚本材料不是 MRTK 的一部分，而是在上一课中导入的 BaseModuleAssets 资产中包含。

4. 在注视目标的同时旋转对象。 我们想要在查看三维对象时将其配置为旋转。 为此，请在 "EyeTrackingTarget" 组件的 "查看目标" 部分中插入一个新字段，如下图所示。

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    在新创建的字段中，将当前游戏对象添加到空字段，然后选择 EyeTrackingTutorialDemo > RotateTarget （），如下图所示。 现在，该 3D 对象已配置为在使用眼动跟踪凝视它时会自动旋转。

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. 添加 "故障目标" 的功能，即通过使用 "gazed" 选择的 "选择"。 与步骤4类似，我们想要通过将 EyeTrackingTutorialDemo 分配给 EyeTrackingTarget 组件的游戏对象的 Select （）字段来触发 > BlipTarget （），如下图所示。 现在已配置此配置，每当触发选择操作（例如，分流或语音命令 "select"）时，就会注意到游戏对象中的故障。

    ![Lesson5 Chapter3 步骤5](images/Lesson5Chapter3Step5.JPG)

6. 在 HoloLens 2 中生成之前，请确保已正确配置眼动跟踪功能。 在撰写本文时，Unity 尚不能为眼睛跟踪功能设置注视输入。 若要在 HoloLens 2 中使用目视跟踪，需要设置此功能。 按照[HoloLens 2 说明测试 Unity 应用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)，以启用 "注视输入" 功能。

## <a name="congratulations"></a>祝贺

已成功将基本的目视跟踪功能添加到应用程序。 这些操作仅为眼动跟踪实现的探索领域开了一个头。 本章还结束第5课，其中介绍了高级输入功能，如语音命令、平移手势和目视跟踪。

[下一课： 7. 创建农历模块示例应用程序](mrlearning-base-ch6.md)
