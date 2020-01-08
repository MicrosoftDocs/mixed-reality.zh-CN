---
title: 入门教程-7。 创建农历模块示例应用程序
description: 在本课中，您将组合从前面的课程中学到的多个概念，以创建独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3127ffceea08202fe9d978ad77f8fddb6fba60a3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334377"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 创建农历模块示例应用程序

在本教程中，将多个概念与前面的课程结合起来，以创建独特的示例体验。 你将了解如何创建农历模块程序集应用程序，用户需要使用跟踪的手选取阴历模块部件，并尝试组装农历模块。 我们使用 pressable 按钮切换放置提示、重置我们的体验，以及将农历模块置于空间中！ 在将来的教程中，我们将继续基于这一体验来构建，其中包括使用 Azure 空间锚点实现空间对齐的强大多用户用例。

## <a name="objectives"></a>目标

- 结合以前课程中的多个概念来创建一个独特的体验
- 了解如何切换对象
- 使用可按按钮触发复杂事件
- 使用刚体的物理特性和力量
- 探索如何使用工具提示

## <a name="configuring-the-lunar-module"></a>配置登月舱

在本部分中，我们将介绍创建示例体验所需的各种组件。

1. 将农历模块程序集 prefab 添加到基础场景中。 为此，请在 "项目" 选项卡中导航到 "资产" > BaseModuleAssets > Prototyping "。 你将看到两个火箭启动器 prototyping，将火箭 Launcher_Tutorial prefab 拖到场景中，并根据需要进行定位。

    >[!NOTE]
    >火箭 Launcher_Complete prefab 是已完成的启动程序，旨在供参考。

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    如果在层次结构中展开 "火箭 Launcher_Tutorial 游戏" 对象并进一步展开农历模块对象，则会找到多个具有称为 "x 射线" 的子对象。 "X ray" 材料允许使用略微半透明的颜色，该颜色将用作用户的放置提示。

    ![Lesson6 Chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    用户将与农历模块的以下部分进行交互，如下图所示：

    1. 探测器外壳
    2. 油箱
    3. 电池
    4. 插接门户
    5. 外部传感器

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    >在基本场景层次结构中看到的游戏对象名称与场景中对象的名称不对应。

2. 将音频源添加到 LunarModule 游戏对象。 确保在场景层次结构中选择 "LunarModule"，并单击 "添加组件"。 搜索 "音频源" 并将其添加到游戏对象。 现在，将 "AudioClip" 字段留空，但将特殊 Blend 设置从0更改为1，以便启用空间音频。 稍后将使用此音频源播放启动声音。

    ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. 添加脚本切换放置提示。 单击 "添加组件"，然后搜索切换放置提示。 这是一个自定义脚本，它使你可以打开和关闭透明提示（具有 x 光材料的对象），如前文所述。

    ![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. 由于我们有五个对象，请键入 "5" 作为游戏对象数组大小。 然后，将看到五个新元素出现。

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    将每个半透明对象拖到 "名称" （游戏对象）框中。 将以下对象从场景中的农历模块拖到对象数组字段中，如上面的图像所示：

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    现在已配置切换位置提示脚本，这使我们可以打开和关闭提示。

5. 添加 "启动农历模块" 脚本。 单击 "添加组件" 按钮，搜索 "启动农历模块" 并将其选中。 此脚本将启动农历模块。 按下某个已配置的按钮时，它会将向上强制添加到农历模块的硬正文部分，并使模块向上启动。 如果你在室内，登月舱可能会撞到你的天花板网。 如果你所在的区域具有高上限或无上限，则阴历模块会无限期地进入空间。

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. 调整推力，使登月舱将顺利地往上飞。 尝试使用值 0.01。 将“Rb”字段留空。 Rb 代表刚性体，此字段将在运行时自动填充。

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

## <a name="lunar-module-parts-overview"></a>农历模块部件概述

农历 Module Part 父对象是用户与之交互的对象的集合。 下面的列表中提供了用括号标记名称的游戏对象名称：

- 背包（能源单元）
- GasTank （燃料箱）
- TopLeftBody（探测器外壳）
- Nose（插接门户）
- LeftTwirler（外部传感器）

请注意，其中每个对象都有一个操作处理程序，如第4课中所述。 此功能使用户能够获取和操作该对象。 另请注意，设置 "双向操作类型" 设置为 "移动和旋转"。 此选项只允许用户移动对象，而不会更改其大小（这是程序集应用程序所需的功能）。
此外，未选中 "远端操作"，只允许模块部件直接交互。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

Part Assembly Demo script （如上所示）是管理用户在农历模块上的用户所放置对象的脚本。

"要放置的对象" 字段是选择的转换（如上图所示），背包/燃料箱与它连接到的对象相关联。

近距离和远距离设置确定了单元的位置或可释放的位置。 例如，背包/燃油水箱需要0.1 个单位，远离农历模块，才能将其放入到位。 "远处距离" 设置设置对象可以从农历模块分离之前的位置。 在本例中，用户必须用手抓住 backpack/油箱，将它从登月舱拉出 0.2 个单位才能防止它贴靠回原位。

工具提示对象是场景中的工具提示标签。 当对对象进行对齐时，将禁用该标签。

音频源会自动进行。

## <a name="configuring-the-placement-hints-button"></a>配置放置提示按钮

在[第2课](mrlearning-base-ch2.md)中，您学习了如何设置按钮并对其进行配置，如更改项的颜色或使其在推送时播放声音。 在为切换放置提示配置按钮时，我们将继续使用这些原则。

目标是配置按钮，以便每次用户按下 "位置提示" 按钮时，它都会切换半透明放置提示的可见性。

1. 在基本场景层次结构中选择放置提示对象时，将阴历模块移到检查器面板中的 "仅限空的运行时" 槽。

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. 单击 "无函数" 下拉列表。 向下移动到 "TogglePlacementHints"，并选择该菜单下的 "ToggleGameObjects （）"。 ToggleGameObjects （）打开和关闭放置提示，使其在每次按下按钮时可见或不可见。

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

## <a name="configuring-the-reset-button"></a>配置重置按钮

在某些情况下，用户会犯错误，意外地丢弃对象或只是想要重置体验。 "重置" 按钮增加了重新启动体验的能力。

1. 选择 "重置" 按钮。 在基本场景中，其名称为 ResetRoundButton。

2. 将农历模块从基本场景层次结构拖到 "检查器" 面板上按下的按钮下的空槽。

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. 选择 "无函数" 下拉菜单并将鼠标悬停在 LaunchLunarModule 上，然后选择 "resetModule" （）。

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    >请注意，默认情况下，GameObject 配置为 ResetPlacement。 这会为 RocketLauncher_Tutorial 的每个子对象广播名为 ResetPlacement 的消息。 具有 ResetPlacement （）方法的任何对象通过重置其位置来响应该消息。

## <a name="configuring-the-launch-button"></a>配置启动按钮

本部分介绍如何配置 "启动" 按钮，该按钮允许用户按下按钮并将阴历模块启动到空间中。

1. 选择 "启动" 按钮。 在基本场景中，它称为 LaunchRoundButton。 将农历模块拖到检查器面板中 "Touch 结束" 下的空槽。

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. 选择 "无函数" 下拉菜单并将鼠标悬停在 LaunchLunarModule 上，然后选择 "StopThruster" （）。 这可控制用户要为农历模块指定多少主旨是。

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. 将农历模块从基本场景层次结构拖到 "检查器" 面板中按下的按钮下的空槽。

4. 单击 "无函数" 下拉菜单，然后单击 "LaunchLunarModule"，并选择 "StartThruster （）"。

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. 将音乐添加到农历模块，以便在火箭停止时播放音乐。 为此，请将农历模块拖到 "按下" 按钮下的下一个空槽（）。

6. 选择 "无函数" 下拉菜单，悬停在 AudioSource 上，然后选择 PlayOneShot （AudioClip）。 随意浏览各种 MRTK 中附带的声音。 在此示例中，我们将使用 "MRTK_Gem"。

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

## <a name="congratulations"></a>祝贺

已完全配置此应用程序。 现在，当按下 "播放" 时，可以完全组装农历模块、切换提示、启动农历模块，并将其重置为重新开始。
