---
title: 入门教程-6。 浏览高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 0f01b789cfc358500ec94a10f82315bca55dd622
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702010"
---
# <a name="6-exploring-advanced-input-options"></a>6.浏览高级输入选项

在本教程中, 我们将探讨 HoloLens 2 的几个高级输入选项, 包括使用语音命令、平移手势和目视跟踪。 

## <a name="objectives"></a>目标

- 使用声音命令和关键字触发事件
- 使用跟踪的指针通过跟踪的手平移纹理和3D 对象
- 利用 HoloLens 2 目视跟踪功能选择对象

## <a name="instructions"></a>说明

### <a name="enabling-voice-commands"></a>启用语音命令

在本部分中, 我们将实现两个语音命令。 首先, 我们将介绍如何通过 "切换诊断" 来切换帧速率诊断面板。 其次, 我们将看看使用语音命令播放声音的能力。 首先, 我们将探讨用于配置语音命令的 MRTK 配置文件和设置。 

1. 在 "基本场景层次结构" 中, 选择 "MixedRealityToolkit"。 在 "检查器" 面板中, 向下滚动到 "输入系统设置"。 双击输入系统配置文件将其打开。 克隆输入系统配置文件以使其可编辑, 如我们在[第1课](mrlearning-base-ch1.md)中所学到的那样 

在输入系统配置文件中, 有各种设置。 对于语音命令, 请选择 "语音命令设置"。 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 克隆语音命令配置文件, 使其可在[第1课](mrlearning-base-ch1.md)中了解。 双击语音命令配置文件, 可在其中看到一系列设置。 有关这些设置的完整说明, 请参阅[MRTK speech 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。 

>注意:默认情况下，一般行为是自动启动。 如果需要, 可以将其更改为手动启动。 但在本示例中, 我们会将其保留为自动启动。 MRTK 附带了几个默认的语音命令, 如菜单、切换诊断和切换探查器。 我们将使用关键字 "切换诊断", 以打开和关闭诊断帧速率计数器。 在以下步骤中，我们还将添加一个新的语音命令。
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 添加新的语音命令。 若要添加新的语音命令, 请单击 "+ 添加新语音命令" 按钮。 您将看到一条新行, 显示在现有语音命令列表下。 键入要使用的语音命令。 在此示例中, 我们将使用命令 "播放音乐"。

>提示：还可为语音命令设置键码。 这允许语音命令在按键时触发事件。    

4. 添加响应语音命令的功能。 选择未附加任何其他输入脚本的基本场景层次结构中的任何对象 (例如, 无操作处理程序)。 在检查器面板中, 单击 "添加组件"。 键入 "语音输入处理程序" 将其选中。

   ![Lesson5 Chapter1.txt Step4im](images/Lesson5_chapter1_step4im.PNG)

   

默认情况下, 你将看到两个复选框。 其中一个是 "是否需要焦点" 复选框。 这意味着, 只要您将鼠标指针置于带有眼睛眼睛眼睛、眼睛眼睛、控制控制或手工看的对象上, 就会触发语音命令。 取消选中此复选框, 以便用户不必查看对象即可使用语音命令。

5. 添加响应语音命令的功能。 为此, 请单击语音输入处理程序中的 "+" 按钮, 然后选择要响应的关键字。

   > 注意:这些关键字是根据在上一步骤中编辑的配置文件填充的。

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. 在关键字旁边, 可以看到一个下拉菜单。 选择 "切换诊断", 以便每当用户显示短语 "切换诊断" 时, 都会触发一个操作。 请注意, 您可能需要通过按下箭头旁边的箭头来展开元素0。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 添加 "诊断演示控制" 脚本, 以打开和关闭计数器计数器诊断。 为此, 请按 "添加组件", 然后搜索 "诊断演示控件脚本", 然后从菜单添加它。 此脚本可以添加到任何对象。 但为了简单起见, 我们会将其添加到与语音输入处理程序相同的对象。 

   > 注意:此脚本仅包含在这些模块中, 不包含在原始 MRTK 中。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 在语音输入处理程序中添加新的响应。 为此, 请单击下面的 "+" 按钮, 其中显示了 "响应" () (在上图中, 标记为绿色箭头)。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 将包含诊断演示的对象控制脚本到您刚刚在步骤8中创建的新响应。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 现在, 选择 "不函数" 下拉列表, 然后选择 "诊断演示控件"。 然后选择 "开启切换诊断 ()" 功能, 该功能可打开和关闭诊断。  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 请注意，在设备上生成之前，需要启用麦克风设置。 为此, 请单击 "文件", 然后依次单击 "生成设置" 和 "播放机设置", 并确保已设置麦克风功能。

接下来, 我们将使用八对象添加从语音命令播放音频文件的功能。 从[第4课](mrlearning-base-ch4.md)中回忆, 我们添加了播放音频剪辑的功能, 使其能够接触八对象。 我们会将此音频源同样用于音乐语音命令。

11. 选择 "基本场景" 层次结构中的八对象。

12. 添加另一个语音输入处理程序 (重复步骤4和 5), 但包含八对象。 

13. 添加 "播放音乐" 语音命令, 而不是从步骤6添加 "切换诊断语音" 命令, 如下图所示。
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 对于步骤8和 9, 添加一个新的响应, 并将八对象拖到空的响应槽。

15. 选择不显示函数的下拉菜单。 然后选择 "音频源", 然后选择 "PlayOneShot" (AudioClip)。

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 在此示例中, 我们将使用[第4课](mrlearning-base-ch4.md)中的相同音频剪辑。 进入你的项目面板, 搜索 "MRTK_Gem" 音频剪辑, 然后将其拖到 "音频源" 槽中, 如下图所示。 现在, 你的应用程序将响应语音命令 "切换诊断" 以切换 "帧速率" 计数器面板, 并播放音乐来播放 MRTK_Gem 歌曲。
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>平移手势 

在本部分中, 我们将学习如何使用平移手势。 这适用于使用手指或手滚动内容滚动。 你还可以使用平移手势来旋转对象、循环浏览三维对象的集合, 甚至滚动 2D UI。 我们还将了解如何使用平移手势来弯曲纹理, 以及如何移动3D 对象的集合。

1. 创建一个四面体。 在 "基本场景层次结构" 中, 右键单击, 选择 "3D 对象", 然后选择 "四个"。

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 适当地重新定位四面体。 对于我们的示例, 我们将 x = 0、y = 0 和 z = 1.5 远离相机, 以实现从 HoloLens 2 获得的舒适位置。

   > 注意:如果故障诊断块或位于前一课中的任何内容之前, 请务必将其移动, 使其不会阻止其他任何对象。

3. 将材料应用到四面体。 此材料将是我们要使用平移手势滚动浏览的材料。 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在 "项目" 面板中, 在搜索框中键入 "平移内容"。 将该材料拖放到场景中的四面体。 

> 注意:平移内容材料不包括在 MRTK 中, 而是在上一课中导入的此模块的资产包中的资产。 

> 注意:添加平移内容时，其外观可能像是已拉伸过。 若要修正，可以调整四面体大小的 x、y 和 z 值，直到其外观让你满意。

若要使用平移手势，需要在对象中添加一个碰撞体。 你可能会看到，四面体已有一个网格碰撞体。 但是，该网格碰撞体并不理想，因为它非常小，很难将其选中。 我们建议将网格碰撞体替换为盒碰撞体。

5. 右键单击 "检查器" 面板上的 "故障诊断" 中的网格碰撞器。 然后单击 "删除组件" 将其删除。
    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)
6. 现在, 通过单击 "添加组件", 然后搜索 "box 碰撞器", 默认的添加框碰撞器仍然太小, 因此, 请单击 "编辑碰撞器" 按钮进行编辑。 按下该对象后，可以使用 x、y 和 z 值或场景编辑器中的元素来调整其大小。 对于本示例，我们希望盒碰撞体稍微靠在四面体的后面。 在场景编辑器中，将盒碰撞体往后朝外拖动（参考下图）。 这样, 用户不仅可以使用手指, 而且能滚动整个手。 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 使对象具有交互能力。 由于我们希望直接与四个部分交互, 我们想要使用在第4课中使用的近乎交互可触摸组件来播放八对象中的音乐。 单击 "添加组件", 然后搜索 "near 交互可触摸" 并选择它, 如下图所示。 

8. 添加识别平移手势的功能。 单击 "添加组件", 然后键入 "手动交互平移", 可以选择 "手动" (允许从远处平移) 和 "食指"。 本示例将其保留为食指。 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 在手型交互平移脚本中, "锁定水平" 和 "锁定垂直" 复选框分别锁定移动。 "换行纹理" 设置使纹理 (纹理映射) 跟随用户的平移移动。 对于本示例, 您将选中该复选框。 还有速度活动, 如果未选中, 则平移手势将不起作用。 同样请选中此框。 现在, 您将拥有一个启用了平移的四个部分。

   

   接下来，我们了解如何平移 3D 对象。 

10. 右键单击 "四个对象", 选择 "3D 对象", 然后单击 "多维数据集"。 缩放该立方体，使其维度大致为 x = 0.1，y = 0.1 和 z = 0.1。 右键单击多维数据集并按重复, 或按 ctrl/command D 将其均匀地复制, 从而将该多维数据集复制三次。 场景应类似于下图。

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 再次选择 "故障", 然后在 "手形交互" 平移脚本下, 将 "平移操作" 设置为每个多维数据集。 在 "平移事件接收方" 下, 我们希望指定接收事件的对象数。 由于有四个多维数据集, 请键入 "4", 然后按 enter。 应显示四个空字段。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 将每个多维数据集拖放到每个空元素槽。
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 通过按住 ctrl/command 并选择每个对象, 将 Move 脚本添加到所有多维数据集。 从检查器面板中, 单击 "添加组件", 然后搜索 "移动并平移"。 单击该脚本, 然后将其添加到每个多维数据集。 现在, 3D 对象会随平移手势一起移动。 如果删除了四面体上的网格渲染器，则四面体会随即不可见，只能通过 3D 对象列表来平移它。

### <a name="eye-tracking"></a>眼动跟踪

在本部分中, 我们将探讨如何在演示中启用目视跟踪。 当您的3D 菜单项 gazed 时, 我们将慢慢旋转它们。 此外，在选择所凝视的项时，我们还会触发一种有趣的效果。

1. 确保已正确配置 MRTK 配置文件。 在撰写本文时，混合现实工具包配置文件配置默认并不包括眼动跟踪功能。 若要添加目视跟踪功能, 请按照[混合现实工具包文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )中所述的 "设置目视跟踪所需的 MRTK 配置文件" 部分中的说明进行操作。 请确保按上述文档链接中的任何剩余步骤正确配置目视跟踪, 包括在 GazeProvider 中启用目视跟踪 (附加到相机的组件), 并在 Unity 编辑器中启用目视跟踪模拟。 请注意, 默认情况下, MRTK 的未来版本可能包括目视跟踪。

    上述链接提供了有关以下操作的简要说明：

    - 创建眼睛数据提供程序以在 MRTK 配置文件中使用
    - 在视线提供程序中启用眼动跟踪
    - 在编辑器中设置目视跟踪模拟
    - 编辑 Visual Studio 解决方案的功能，以便在生成的应用程序中进行眼动跟踪

2. 将眼动跟踪目标组件添加到目标对象。 若要允许对象响应眼睛眼睛事件, 我们需要使用目视注视将 EyeTrackingTarget 组件添加到要与之交互的每个对象上。 将此组件添加到网格集合中的每个（共九个）3D 对象。 提示：选择层次结构中的多个项, 以批量添加 EyeTrackingTarget 组件。
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. 接下来，我们将添加 EyeTrackingTutorialDemo 脚本以完成一些有意思的交互。 本教程系列存储库中包含了 EyeTrackingTutorialDemo 脚本。 默认情况下, 它不包含在混合现实工具包中。 对于网格集合中的每个三维对象, 通过在 "添加组件" 菜单中搜索组件来添加 EyeTrackingTutorialDemo 脚本。
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

4. 在注视目标的同时旋转对象。 我们想要在查看三维对象时将其配置为旋转。 为此, 请在 "EyeTrackingTarget" 组件的 "查找目标" 部分中插入一个新字段, 如下图所示。 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



在新创建的字段中, 将当前游戏对象添加到空字段, 然后选择 EyeTrackingTutorialDemo > RotateTarget (), 如下图所示。 现在，该 3D 对象已配置为在使用眼动跟踪凝视它时会自动旋转。 

5. 添加 "故障目标" 的功能, 即通过使用 "gazed" 选择的 "选择"。 与步骤4类似, 我们想要通过将 EyeTrackingTutorialDemo 的 BlipTarget () 分配给 "EyeTrackingTarget" 组件的游戏对象的 "选择 ()" 字段来触发该 >, 如下图所示。 现在已配置此配置, 每当触发选择操作 (例如, 分流或语音命令 "select") 时, 就会注意到游戏对象中的故障。 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. 在 HoloLens 2 中生成之前，请确保已正确配置眼动跟踪功能。 在撰写本文时, Unity 尚不能为眼睛跟踪功能设置注视输入。 若要在 HoloLens 2 中使用目视跟踪, 需要设置此功能。 请遵照混合现实工具包文档中的以下说明启用视线输入功能： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


## <a name="congratulations"></a>祝贺

已成功将基本的目视跟踪功能添加到应用程序。 这些操作仅为眼动跟踪实现的探索领域开了一个头。 本章还结束第5课, 其中介绍了高级输入功能, 如语音命令、平移手势和目视跟踪。 

[下一课：7.创建农历模块示例应用程序](mrlearning-base-ch6.md)

