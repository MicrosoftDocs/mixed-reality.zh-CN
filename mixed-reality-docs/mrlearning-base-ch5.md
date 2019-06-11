---
title: MR 学习基础模块 - 高级输入
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719895"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 学习基础模块 - 高级输入

本课探讨 HoloLens 2 的几个高级输入选项，包括语音命令、平移手势和眼动跟踪的用法。 

## <a name="objectives"></a>目标

- 了解如何使用语音命令和关键字触发事件
- 使用跟踪手平移纹理和 3D 对象
- 利用 HoloLens 2 的眼动跟踪功能选择对象

## <a name="instructions"></a>说明

### <a name="enabling-voice-commands"></a>启用语音命令

在本部分，我们将实现两个语音命令。 首先，通过讲出“切换诊断”来切换帧速率诊断面板。 然后，使用语音命令播放声音。 我们先探讨负责配置语音命令的 MRTK 配置文件和设置。 

1. 在基本场景层次结构中选择“MixedRealityToolkit”。 在检查器面板中，向下滚动到输入系统设置。 双击输入系统配置文件将其打开。 克隆输入系统配置文件以使其可编辑，如[第 1 课](mrlearning-base-ch1.md)中所述 

在输入系统配置文件中，会看到各种设置。 对于语音命令，向下滚动到标有“语音命令设置”的部分。 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 克隆语音命令配置文件以使其可编辑，如[第 1 课](mrlearning-base-ch1.md)中所述 双击语音命令配置文件，此时会看到一系列的设置。 有关这些设置的完整说明，请参阅 [MRTK 语音文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。 

>注意：默认情况下，一般行为是自动启动。 可根据需要将其更改为手动启动，但对于本示例，我们将其保留为自动启动。 MRTK 附带了多个默认语音命令（例如菜单、切换诊断和切换探查器）。 我们将使用关键字“切换诊断”来启用和禁用诊断帧速率计数器。 在以下步骤中，我们还将添加一个新的语音命令。
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 添加新的语音命令。 若要添加新的语音命令，请单击“+ 添加新语音命令”按钮。现有语音命令列表的下面会显示一个新行。 键入要使用的语音命令。 在此音乐示例中，我们将使用命令“播放音乐”。

>提示：还可为语音命令设置键码。 这样，在按下某个键盘按键时，会触发语音命令。   

4. 添加响应语音命令的功能。 在基本场景层次结构中，选择未附有任何其他输入脚本（例如，未附加操纵处理程序）的任何对象。在检查器面板中，单击“添加组件”。 键入“语音输入处理程序”。 选择该组件。
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

默认情况下会看到 2 个复选框，其中一个是“需要聚焦”复选框。 这表示，只要你使用视线（眼睛视线、头部跟踪视线、控制器视线或手部跟踪视线）指向对象，就会触发语音命令。 如果取消选中此复选框，则用户无需注视对象就能使用语音命令。

5. 添加响应语音命令的功能。 为此，请单击语音输入处理程序中的“+”按钮，然后选择要响应的关键字。

   > 注意：这些关键字是根据在上一步骤中编辑的配置文件填充的。

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. 在“关键字”旁边，会看到一个下拉菜单。 选择“切换诊断”。 这样，每当用户讲出短语“切换诊断”时，就会触发某个操作。 请注意，可能需要通过按下“元素 0”旁边的箭头将其展开。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 添加“诊断演示控件脚本”来启用和禁用帧速率计数器诊断。 为此，请按“添加组件”按钮，搜索“诊断演示控件脚本”，然后从菜单中添加此脚本。 此脚本可添加到任何对象，但为了简单起见，我们将其添加到语音输入处理程序所在的同一对象。 

   > 注意：此脚本仅包含在这些模块中，而未包含在原始的 MRTK 中。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 在语音输入处理程序中添加新的响应。 为此，请单击带有“response ()”字样的元素（在上图中标有绿色箭头）下方的“+”按钮。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 将包含诊断演示控件脚本的对象拖放到刚刚在步骤 8 中创建的新响应。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 现在请选择“无函数”下拉列表，选择诊断演示控件，然后选择“on toggle diagnostics ()”。 此函数会启用或禁用诊断。  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 请注意，在设备上生成之前，需要启用麦克风设置。 为此，请单击“文件”，转到“生成设置”>“播放器设置”，并确保已设置麦克风功能。

接下来，我们将添加使用“八面体”对象从语音命令播放音频文件的功能。 回顾[第 4 课](mrlearning-base-ch4.md)，我们已添加通过触摸八面体对象播放音频剪辑的功能。 我们会将此音频源同样用于音乐语音命令。

11. 在基本场景层次结构中选择八面体对象。

12. 添加另一个语音输入处理程序（重复步骤 4 至 5），但使用八面体对象。 

13. 不要添加步骤 6 中所述的“切换诊断”语音命令，而是如下图所示添加“播放音乐”语音命令。
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 如步骤 8 和 9 中所述添加新的响应，并将八面体拖放到响应中的空槽。

15. 选择带有“无函数”字样的下拉菜单，选择“音频源”，然后选择“PlayOneShot (AudioClip)”。

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 对于本示例中的音频剪辑，我们将使用[第 4 课](mrlearning-base-ch4.md)中所述的相同音频剪辑。 转到项目面板，搜索“MRTK_Gem”音频剪辑并将其拖入音频源槽，如下图所示。 现在，应用程序应该可以响应语音命令“切换诊断”来切换帧速率计数器面板，并响应“播放音乐”来播放 MRTK_Gem 歌曲。
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>平移手势 

本章介绍如何使用平移手势。 滚动功能（使用手指或手滚动浏览内容）非常有用。还可以使用平移手势来旋转对象、循环 3D 对象的集合，甚至滚动 2D UI。 我们将了解如何使用平移手势来扭曲纹理。 此外，我们将了解如何移动 3D 对象的集合。

1. 创建一个四面体。 在基本场景层次结构中单击右键，选择“3D 对象”，然后选择“四面体”。

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 适当地重新定位四面体。 在本示例中，我们相对于相机位置设置了 x = 0，y = 0 和 z = 1.5，以便在 HoloLens 2 中获得一个舒适的操作位置。

   > 注意：如果四面体块位于前面课程中任何内容的前面，请务必将其移动，使其不会阻挡任何其他对象。

3. 将材料应用到四面体。 此材料将是我们要使用平移手势滚动浏览的材料。 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在项目面板上的搜索框中键入“平移内容”。 将该材料拖放到场景中的四面体。 

> 注意：“平移内容”材料未包含在 MRTK 中，它是此模块的资产包中的一个资产，已在前面的课程中导入。 

> 注意：添加平移内容时，其外观可能像是已拉伸过。 若要修正，可以调整四面体大小的 x、y 和 z 值，直到其外观让你满意。

若要使用平移手势，需要在对象中添加一个碰撞体。 你可能会看到，四面体已有一个网格碰撞体。 但是，该网格碰撞体并不理想，因为它非常小，很难将其选中。 我们建议将网格碰撞体替换为盒碰撞体。

5. 右键单击四面体上的网格碰撞器（在检查器面板中），然后单击“删除组件”将其删除。 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 现在，通过单击“添加组件”并搜索“盒碰撞体”，来添加盒碰撞体。 默认添加的盒碰撞体仍旧太小，因此，请单击“编辑碰撞体”按钮对其进行编辑。 按下该对象后，可以使用 x、y 和 z 值或场景编辑器中的元素来调整其大小。 对于本示例，我们希望盒碰撞体稍微靠在四面体的后面。 在场景编辑器中，将盒碰撞体往后朝外拖动（参考下图）。 这样，用户不仅可以使用手指，而且还可以用手滚动浏览。 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 使对象具有交互能力。 由于我们想要直接与四面体交互，因此需要使用“近距交互可触摸”组件（在第 4 课中，我们也使用了此组件来从八面体播放音乐）。 单击“添加组件”，搜索“近距交互可触摸”并将其选中，如下图所示。 

8. 添加识别平移手势的功能。 单击“添加组件”并键入“手动交互平移”。 可以选择手部跟踪光线（可从远处平移）或食指。 本示例将其保留为食指。 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 在手动交互平移脚本中，选中“水平锁定”和“垂直锁定”复选框会锁定相应方向的移动。 扭曲纹理设置会使纹理（纹理映射）遵循用户的平移动作。 本示例选中了该框。 此外，还有一个“活动速率”复选框，如果不选中它，平移手势将不起作用。 同样请选中此框。 现已创建一个启用了平移的四面体。

   

   接下来，我们了解如何平移 3D 对象。 

10. 右键单击四面体对象，选择 3D 对象，然后单击“立方体”。 缩放该立方体，使其维度大致为 x = 0.1，y = 0.1 和 z = 0.1。 复制该立方体 3 次（右键单击该立方体并按“复制”，或按 Ctrl/Command 键 + D）。 以均匀的间距排布这些立方体。 场景应如下图所示。

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 再次选择四面体，在手动交互平移脚本下，我们需要为每个立方体设置平移操作。 在“平移事件接收器”下，我们需要指定接收事件的对象数。 由于存在 4 个立方体，因此请键入“4”并按 Enter。 应会显示 4 个空字段。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 将每个立方体拖入每个空元素槽。
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 将“平移移动”脚本添加到所有立方体。 为此，请在按住 Ctrl/Command 键的同时选择每个对象。 然后，在检查器面板中，单击“添加组件”并搜索“平移移动”。 单击脚本，它随即会添加到每个立方体。 现在，使用平移手势即可移动 3D 对象！ 如果删除了四面体上的网格渲染器，则四面体会随即不可见，只能通过 3D 对象列表来平移它。

### <a name="eye-tracking"></a>眼动跟踪

本章探讨如何在演示中启用眼动跟踪。 我们将在眼睛凝视 3D 菜单项时，缓慢地将其旋转。 此外，在选择所凝视的项时，我们还会触发一种有趣的效果。

1. 请确保已正确配置混合现实工具包配置文件。 在撰写本文时，混合现实工具包配置文件配置默认并不包括眼动跟踪功能。 若要添加眼动跟踪功能，请遵照[混合现实工具包文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )的“设置眼动跟踪所需的 MRTK 配置文件”部分中提供的说明。 确保遵循上述文档链接中的所有剩余步骤正确配置眼动跟踪，包括在 GazeProvider（附加到相机的组件）中启用眼动跟踪，并在 Unity 编辑器中启用眼动跟踪的模拟。 请注意，将来的 MRTK 版本默认可能会包含眼动跟踪。

    上述链接提供了有关以下操作的简要说明：

    - 创建可在 MRTK 配置文件中使用的视线数据提供程序
    - 在视线提供程序中启用眼动跟踪
    - 在编辑器中模拟眼动跟踪的设置
    - 编辑 Visual Studio 解决方案的功能，以便在生成的应用程序中进行眼动跟踪

2. 将眼动跟踪目标组件添加到目标对象。 要使某个对象对凝视事件做出响应，需在我们要使用视线交互的每个对象中添加 EyeTrackingTarget 组件。 将此组件添加到网格集合中的每个（共九个）3D 对象。 提示：在层次结构中选择多个项可以批量添加 EyeTrackingTarget 组件。
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. 接下来，我们将添加 EyeTrackingTutorialDemo 脚本以完成一些有意思的交互。 EyeTrackingTutorialDemo 脚本已包含在本教程系列的存储库中，默认未包含在混合现实工具包中。 对于网格集合中的每个 3D 对象，请通过在“添加组件”菜单中搜索该组件来添加 EyeTrackingTutorialDemo 脚本。
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

   4. 在注视目标的同时旋转对象。 我们希望将此 3D 对象配置为在注视时旋转。 为此，请在 EyeTrackingTarget 组件的“注视目标时”节中插入一个新字段，如下图所示。 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



在新建的字段中，将当前游戏对象添加到空字段，并选择“EyeTrackingTutorialDemo”>“RotateTarget()”，如下图所示。 现在，该 3D 对象已配置为在使用眼动跟踪凝视它时会自动旋转。 

5. 将功能到在执行选择（隔空敲击，或讲出“选择”）时凝视的“光点目标”。 类似于步骤 4，我们需要通过将“EyeTrackingTutorialDemo”>“BlipTarget()”分配到 EyeTrackingTarget 组件的游戏对象“select()”字段来触发它，如下图所示。 完成此项配置后，你会注意到，每当触发一个选择操作（例如隔空敲击或发出语音命令“选择”），游戏对象中都会出现一个微小的光点。 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. 在 HoloLens 2 中生成之前，请确保已正确配置眼动跟踪功能。 在撰写本文时，无法在 Unity 中设置视线输入（眼动跟踪）功能。 必须设置此功能，才能在 HoloLens 2 中运行眼动跟踪。 请遵照混合现实工具包文档中的以下说明启用视线输入功能： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>祝贺你！ 
现已将基本的眼动跟踪功能成功添加到应用程序。 这些操作仅为眼动跟踪实现的探索领域开了一个头。 本章也是第 5 课的最后一个部分。在第 5 课中，我们学习了语音命令、平移手势和眼动跟踪等高级输入功能。 

[下一课：登月舱模块装配示例体验](mrlearning-base-ch6.md)

