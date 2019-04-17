---
title: 公告板和尾随
description: 公告板的对象始终定位自身面临着用户。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，公告板，尾随
ms.openlocfilehash: 8215b96aff1f3c2d43e959f04ad83d41ffd32b2a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592629"
---
# <a name="billboarding-and-tag-along"></a>公告板和尾随

公告板是混合现实中应用于对象的行为概念。 公告板的对象始终定位自身面临着用户。 这会非常有用的文本和静态对象 （世界锁定） 的用户的环境中的放置位置的面前系统会模糊或不可读，如果用户四处移动。

![HoloLens 的菜单系统的角度来看，始终面临用户](images/billboarding-fragments.gif)<br>
*HoloLens 的菜单系统的角度来看，始终面临用户*

公告板启用的对象可以自由地旋转中的用户环境。 它们还可以限制于单个轴具体取决于设计注意事项。 请记住，billboarded 的对象可能剪辑或遮蔽本身，如果放置太靠近其他对象，或在 HoloLens，太靠近扫描图面。 若要避免此问题，应考虑的总占用量为公告板启用轴上旋转时，可能会产生一个对象。

## <a name="what-is-a-tag-along"></a>什么是尾随？

尾随是可以添加到全息，包括 billboarded 的对象的行为概念。 这种交互是实现头锁定内容的效果的更自然且友好的方式。 尾随对象尝试从不离开用户的视图。 这样，用户可以自由地与前面的它们时仍然会看到其直接视图之外全息进行交互。

![HoloLens pin 面板是尾随的行为方式的一个极好示例](images/tagalong-1000px.jpg)<br>
*HoloLens 开始菜单是尾随行为的一个极好示例*

尾随对象具有可以精细调整他们的行为的方式的参数。 内容可以是入或移出用户的直通根据需要，围绕其环境中的移动用户。 当用户移动时，内容将尝试通过指向视图的边缘滑动人员在用户的外围中，具体取决于用户的移动速度可能会使对临时视图之外的内容。 时用户 gazes 针对尾随对象，它更充分发挥视图。 将始终被"快速消失"，以便用户永远不会忘记其内容是在哪个方向的内容。

其他参数可以使感觉附加到用户的头通过使用橡胶带尾随对象。 抑制加速或减速效果赋予对象使其感觉更实际存在的权重。 此 spring 行为是可帮助用户生成尾随的工作原理的准确心理模型功能可见性:。 音频可帮助用户在尾随模式下具有对象时提供的其他提示。 音频应强调的速度移动;一个快速头轮次应提供更明显的声音效果，而根本速度自然的每个步骤应该会有最小的音频，如果有影响。

就像真正头锁定内容尾随对象具有非常庞大的或 nauseating 如果他们大幅变化移动或 spring 太多的用户视图中。 为用户查找，然后快速停止，其方式告诉他们已停止。 其平衡告知他们，其头已停止启用以及其视觉看到打开世界上停止。 但是，如果用户已停止时，尾随上继续移动，它可能将其理解混淆。

## <a name="see-also"></a>请参阅
* [游标](cursors.md)
* [交互基础知识](interaction-fundamentals.md)
* [Comfort](comfort.md)
