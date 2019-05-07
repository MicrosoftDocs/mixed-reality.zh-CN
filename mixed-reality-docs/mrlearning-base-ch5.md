---
title: MR 学习基本模块-高级输入
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: c28b607e3532a7c964ab74fdb7a7d514c9293579
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929580"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 学习基本模块-高级输入

在本课中，我们将了解几个高级输入的 HoloLens 2，包括使用语音命令、 平移手势和的眼跟踪选项。 

## <a name="objectives"></a>目标

- 了解如何在触发事件使用语音命令和关键字
- 使用跟踪的手平移纹理和三维对象
- 利用 HoloLens 2 的眼跟踪功能，以选择对象

## <a name="instructions"></a>说明

### <a name="enabling-voice-commands"></a>启用语音命令

在本部分中，我们将实施两个语音命令。 首先，通过依次选择"切换诊断"。 打开帧速率诊断面板的能力 第二个，播放声音，语音命令的能力。 首先，我们将探讨 MRTK 配置文件和设置负责配置语音命令。 

1. 在基本场景的层次结构中选择"MixedRealityToolkit。" 在检查器面板中，向下滚动输入的系统设置。 双击以打开输入的系统配置文件。 克隆在输入的系统配置文件，使其可编辑，正如我们在获知[第 1 课](mrlearning-base-ch1.md) 

在输入的系统的配置文件，你将看到各种设置。 语音命令，请向下转至在那里显示，"语音命令设置"。 

![Lesson5 第 1 章 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 克隆语音命令配置文件，使其可编辑，正如我们在获知[第 1 课](mrlearning-base-ch1.md)。 双击语音命令配置文件，您会注意到一系列的设置。 有关这些设置的完整说明，请参阅[MRTK 语音文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。 

>注意：默认情况下，常规行为是自动启动。 可更改以手动启动如果需要，但对于此示例中我们将其保留在自动启动。 MRTK 附带了几个默认语音命令 （如菜单、 切换诊断和切换事件探查器）。 我们将使用关键字"切换诊断"以打开和关闭诊断帧速率计数器。 下面的步骤中，我们还将添加一个新的语音命令。
>
> ![Lesson5 第 1 章 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 添加一个新的语音命令。 若要添加新的语音命令，请单击"+ 添加新的语音命令"按钮并将看到显示向下的现有语音命令在列表下方的新行。 键入你想要使用的语音命令。 在此示例 musicample 我们要使用命令"播放音乐"。

>提示：此外可以设置语音命令的键盘代码。 这允许语音命令，以在按下键盘键时触发。   

4. 添加响应语音命令的能力。 在不具有任何其他附加到它 （例如，没有操作处理程序。） 的输入的脚本的基本场景层次结构中选择的任何对象在检查器窗格中，单击"添加组件"。 键入"语音输入的处理程序。" 选择它。
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

默认情况下，你将看到 2 个复选框，其中一个是"为所需的焦点"复选框。 这意味着，只要你指向与的视线移动 ray、 （关注注视、 head 注视、 控制器视线移动或手动提供注视） 的对象将触发语音命令。 取消选中此复选框可使它，以便用户无需查看要使用语音命令的对象。

5. 添加响应语音命令的能力。 若要执行此操作，请单击语音输入处理程序中的"+"按钮，然后选择你想要响应的关键字。

   > 注意：这些关键字都基于上一步中编辑的配置文件填充。

![Lesson5 第 1 章 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. "关键字"旁边，您将看到一个下拉列表菜单。 选择"切换诊断"。 这将使它，以便每当用户所讲的短语，"切换诊断"时它将触发操作。 请注意，您可能需要通过按其旁边的箭头展开"元素 0"。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 添加"诊断演示控制脚本"来打开和关闭之间切换的帧速率计数器诊断。 若要执行此操作，按"添加组件"按钮并搜索"诊断演示控制脚本"，然后从菜单中添加它。 此脚本可以添加到任何对象，但为简单起见，我们将其添加到与语音输入的处理程序相同的对象。 

   > 注意： 此脚本是仅包含在这些模块，则不包含与原始 MRTK。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 语音输入处理程序中添加一个新的响应。 为此请单击"+"按钮下方中标"响应 （）"（标记在上图中的绿色箭头）。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 将具有到在步骤 8 中创建新响应诊断演示控件脚本的对象。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 现在选择"函数"下拉列表中，选择诊断演示控件，然后"上切换诊断 （）。" 此函数来开启和关闭你的诊断。  ![Lesson5 第 1 章 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 请注意，向你的设备生成前你需要启用 mic 设置。 若要执行该单击文件，转到生成设置，从此处，播放机设置，并确保设置麦克风的功能。

接下来，我们将添加播放语音命令使用"八"对象中的音频文件。 还记得[第 4 课](mrlearning-base-ch4.md)，我们添加了播放音频剪辑不接触八对象。 我们将为我们音乐的语音命令来利用此相同的音频源。

11. 在基本场景的层次结构中选择的八对象。

12. 添加另一个语音输入处理程序 （重复执行步骤 4 和 5)，但与八对象。 

13. 而不是从第 6 步中添加"切换诊断"语音命令，添加"播放音乐"语音命令，如下图中所示。
    
     ![Lesson5 第 1 章 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 与步骤 8 和 9，添加一个新的响应，并且将八拖到空槽上响应。

15. 选择下拉菜单中显示"没有函数"，选择"音频源，"然后选择"PlayOneShot (AudioClip)。"

![Lesson5 第 1 章 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 音频剪辑，此示例中我们将使用从相同的音频剪辑[第 4 课](mrlearning-base-ch4.md)。 转到项目面板，搜索"MRTK_Gem"音频剪辑并将其拖到音频源槽，如下图中所示。 现在，你的应用程序应该能够响应语音命令"切换诊断"以切换帧速率计数器面板和"播放音乐"播放 MRTK_Gem 歌曲。
     ![Lesson5 第 1 章 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>平移手势 

在本章中，我们将了解如何使用平移手势。 它可用于滚动 （使用手指或手动滚动浏览内容。）此外可以使用平移手势来旋转对象，若要循环三维对象或甚至滚动 2D UI 的集合。 我们将学习如何使用平移手势 warp 纹理。 我们将探讨如何移动三维对象的集合。

1. 创建四。 在基本场景层次结构中，右键单击，选择"3D 对象，"然后选择"四。"

![Lesson5 第 2 章 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 根据需要四会重新定位。 对于本示例中，我们将设置 x = 0，y = 0 和 z = 1.5 开照相机的 HoloLens 2 中的合适位置。

   > 注意：如果四块 （为 infront 的） 任何内容从前面的课程，一定要将其移动，以便它不会阻止任何其他对象。

3. 适用于四核的材料。 本材料将是我们将使用平移手势滚动的材料。 

![Lesson5 第 2 章 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在将项目面板中，键入在搜索框"平铺内容。 将该材料拖到您的场景中四。 

> 注意："平移内容"材料不包含在 MRTK，但它是此模块的资产包中的资产，如在前面的课程中导入。 

> 注意：当添加平铺内容时，它可能看起来外延式。 通过调整 x，y 和 z 值的四核大小的值，直到它的外观满意，可以解决此问题。

若要使用平移手势，将你的对象需要一个碰撞体。 您可能会看到四已有一个网格碰撞体。 但是，网格碰撞体并不理想，因为它是极其精简且难以进行选择。 我们建议使用盒状碰撞体替换网格碰撞体。

5. 右键单击网格碰撞器上四 （在检查器面板中），然后单击"删除组件"。 将其删除 
   ![Lesson5 第 2 章 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 现在将盒状碰撞体添加通过单击"添加组件"并搜索"框的碰撞体"。 默认值添加盒状碰撞体仍是不可过于省略，因此，单击"编辑碰撞体"按钮以对其进行编辑。 在按下它时，可以调整在场景编辑器中使用 x、 y 和 z 值或元素的大小。 对于本示例中，我们想要后面四稍有扩展盒状碰撞体。 在场景编辑器中，从后，向外应用 （请参阅下图） 将盒状碰撞体。 这将执行的操作是允许用户不仅使用他们的手指，但其整个手动滚动。 
    ![Lesson5 第 2 章 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 进行交互。 由于我们要与四直接进行交互，因此我们想要使用"附近可触摸交互"组件 （我们也使用这第 4 课中用于播放音乐从八）。 单击"添加组件"并搜索"附近的可触摸交互"并选择它，如以下图像中所示。 

8. 添加识别平移手势的能力。 单击"添加组件"，然后键入"分发交互平移。" 必须手动 ray （允许您在远处平移） 和食指之间进行选择。 对于本例，请将其保留在索引手指。 
    ![Lesson5 第 2 章 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 第 2 章 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 在手动交互平移脚本中，"lock 水平"和"lock 垂直"复选框将会锁定移动，分别。 自动换行纹理设置将使纹理 （纹理映射） 按照用户的平移移动。 对于此示例中，我们将选中此框。 此外，还有"velocity active"的平移手势如果未选中，将无法工作。 选中此框以及。 现在，您应该启用平移的四核。

   

   接下来，我们将了解如何向三维对象的平移。 

10. 右键单击四部分对象，选择三维对象，然后单击"多维数据集"。 缩放多维数据集，以便它大约为 x = 0.1，y = 0.1 和 z = 0.1。 复制该多维数据集 3 次 （通过右键单击多维数据集并按重复，或通过按下控件/命令 D）。 它们彼此隔开均匀。 您的场景应类似于下面的图片。

![Lesson5 第 2 章 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 同样，选择四核和下手动交互平移脚本，我们想要的平移操作设置为每个多维数据集。 "平移事件接收器"下，我们想要指定将接收事件的对象数。 有 4 个多维数据集，因为类型"4"，然后按 enter。 应显示 4 个空字段。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 将每个中的多维数据集拖到每个空元素槽。
     ![Lesson5 第 2 章 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. "与平移移动"脚本添加到所有多维数据集。 若要执行此操作，按按住控制/命令，选择每个对象。 然后，在检查器窗格中，单击"添加组件"并搜索"移动且使用 pan。" 单击该脚本，它将添加到每个多维数据集。 现在将与平移手势移动三维对象 ！ 如果删除网格呈现上在四核，您现在应该可以漫游的三维对象的列表不可见的四核。

### <a name="eye-tracking"></a>眼睛追踪

在本章中，我们将探索如何能够在我们的演示中的眼跟踪。 它们正在 gazed 时与关注的视线移动时，我们将缓慢构建我们 3D 菜单项。 我们也会触发一个有趣选择 gazed 时项时起作用。

1. 请确保正确配置的混合现实工具包配置文件。 在撰写本文时，混合的现实工具包配置文件配置不包括跟踪功能，默认情况下的关注。 若要添加的眼跟踪功能，请按照"设置所需的眼跟踪 MRTK 配置文件"部分中的说明中所述[混合现实工具包文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )。 确保该的眼跟踪已正确配置文档上面的链接，包括启用 GazeProvider （附加到摄像机的组件） 中的眼跟踪和启用模拟的眼跟踪在 Unity 编辑器中的任何剩余步骤。 请注意 MRTK 的未来版本可能包括默认情况下的眼跟踪。

    上面的链接提供有关的简要说明：

    - 创建关注注视数据提供程序用于在 MRTK 配置文件中
    - 启用对此提供程序中的眼跟踪
    - 用于模拟的眼跟踪在编辑器中设置
    - 编辑 Visual Studio 解决方案的功能，以便在生成的应用程序中的眼跟踪

2. 将关注跟踪目标组件添加到目标对象。 若要允许对关注的视线移动事件做出响应的对象，我们将需要将 EyeTrackingTarget 组件添加我们想要与使用关注的视线移动进行交互的每个对象。 将此组件添加到每个网格集合的一部分的九个三维对象。 提示： 若要批量添加 EyeTrackingTarget 组件在层次结构中选择多个项。
    ![Lesson5 第 3 章步骤 2](images/Lesson5Chapter3Step2.JPG)

3. 接下来我们将添加一些令人兴奋的交互的 EyeTrackingTutorialDemo 脚本。 EyeTrackingTutorialDemo 脚本是作为本教程系列的存储库的一部分，并且不包含默认情况下使用混合现实工具包。 对于网格集合中每个三维对象，通过搜索"添加组件"菜单中的组件中添加 EyeTrackingTutorialDemo 脚本。
   ![Lesson5 第 3 章步骤 3](images/Lesson5Chapter3Step3.JPG)

   4. 查看目标的同时旋转对象。 我们想要配置启动时我们看一下我们三维对象。 若要执行此操作，插入一个新域 EyeTrackingTarget 组件的"时查找在目标"部分中，如下图中所示。 

![Lesson5 第 3 章 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 第 3 章 Step4b](images/Lesson5Chapter3Step4b.JPG)



在新创建的字段，将当前的游戏对象添加到空的字段，并选择 EyeTrackingTutorialDemo > RotateTarget() 中如下图所示。 现在三维对象已配置为启动时它正在 gazed 时具有眼跟踪。 

5. 将功能添加到"故障目标"，在正在 gazed 时选择 （敲击，或说"选择"）。 类似于第 4 步，我们要触发 EyeTrackingTutorialDemo > BlipTarget() 将其分配给 EyeTrackingTarget 分量的游戏对象的"select （）"字段中，如下图中所示。 与此现已配置，你会注意到游戏对象时触发的选择操作，如空气点击或语音命令中稍有故障"选择。" 
    ![Lesson5 第 3 章步骤 5](images/Lesson5Chapter3Step5.JPG)
6. 请确保为 HoloLens 2 生成前正确配置了密切关注的跟踪功能。 在撰写本文时，Unity 尚没有设置提供注视输入 （适用于眼睛跟踪） 功能的能力。 设置此功能是必需的眼跟踪 HoloLens 2 上工作。 按照以下说明在混合的现实工具包文档以启用注视输入的功能： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>祝贺你！ 
已成功添加到应用程序跟踪功能的基本关注。 这些操作是仅使用的眼跟踪，提供了可能的开头。 本章还得出结论第 5 课，其中我们介绍了高级输入功能，例如语音命令平移手势，并密切关注跟踪。 

[下一课：农历模块程序集示例体验](mrlearning-base-ch6.md)

