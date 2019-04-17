---
title: 案例研究-为 HoloTour 空间合理的设计
description: 若要创建真正沉浸式 3D 虚拟介绍 Microsoft HoloLens，全景视频和 holographic 风景是仅公式的一部分。
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HoloLens，HoloTour，空间的声音，案例研究
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592747"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>案例研究-为 HoloTour 空间合理的设计

若要创建真正沉浸式 3D 虚拟介绍 Microsoft HoloLens，全景视频和 holographic 风景是仅公式的一部分。 Jason Syltebo 讨论了如何声音的音频设计器已捕获和处理以让您感到起来是实际在每个 HoloTour 中的位置。

## <a name="the-tech"></a>技术人员

漂亮的图像和 holographic 场景中 HoloTour 看到只有一个创建来说混合的现实体验的一部分。 虽然全息仅可以直观地显示在用户之前[空间声音](spatial-sound.md)HoloLens 功能允许音频来自所有方向，这为用户提供了更完整的感官体验。

空间声音使我们能够提供音频提示以指示的方向中的用户应打开，或让用户知道有为其查看在其空间内的多个全息。 我们可以还将声音附加直接到一张全息图，并不断更新的方向和全息图是从用户以使其看起来像声音即将直接从该对象的距离。

使用 HoloTour，我们想要充分利用的 HoloLens 空间声音功能，以创建全方位的环境的环境，视频以显示特定位置 sonic 突出显示与同步。

## <a name="behind-the-scenes"></a>幕后

我们创建两个不同位置的 HoloTour 的体验：罗马和 Machu Picchu。 可信且具有吸引力使认为这些教程来我们想要避免使用泛型的声音并改为捕获音频直接从我们已与其中的位置。

### <a name="capturing-the-audio"></a>捕获音频

在我们[案例研究有关可视内容捕获为 HoloTour](case-study-capturing-and-creating-content-for-holotour.md)，我们讨论了我们照相机远程测试机组的自定义设计。 它包括 14 GoPro 相机 3D 打印住房中包含的设计到三脚架的特定维度。 若要捕获此远程测试机组中的音频，我们添加了摄影机、 送入坐在三脚架基 compact 4 通道录制单元下的四麦克风数组。 我们选择了的麦克风的不只执行，但其中有非常小的占用空间，以便不遮蔽照相机的视图。

![自定义照相机和麦克风远程测试机组](images/camera-rig-microphones-300px.png)<br>
*自定义照相机和麦克风远程测试机组*

此设置捕获从我们的照相机，从而为我们提供足够的信息来重新创建三维听觉全景使用空间的声音，我们更高版本无法同步到 360 度视频的精确位置的四个方向中的声音。

照相机数组音频的挑战之一是位于在捕获时记录的控制之下。 即使视频捕获很不错，声音捕获可能会由于 sirens、 飞机上或高即将结束时，例如禁用相机声音有问题。 若要确保我们，我们需要的所有元素，我们使用一系列的立体声和 mono 移动录制单位的每个位置感兴趣的特定点上获取异步的环境元素。 此捕获很重要，因为它使声音的设计器能够找出可用于在后期生产环境中编写感兴趣和添加更多的方向性的干净且可用内容。

任何给定的捕获一天会生成大量的文件。 这是非常重要的系统来跟踪哪些文件与特定位置或照相机截图相对应。 我们录制单位按日期已设置为自动命名的文件和获取数值，我们会备份这些天结束时对外部驱动器。 最起码口头如果音频录制的开头是内容的非常重要，因为这样的简单上下文标识应文件名会成为问题。 这也是我们能够以可视方式平板相机远程测试机组捕捉视频和音频已记录为单独的媒体并在 post 期间同步所需的重要的。

### <a name="editing-the-audio"></a>编辑音频

回到后捕获行程 studio，组装方向和沉浸式的听觉体验的第一步是查看所有挑选出所采取的最佳和标识无法在创造性地应用任何突出显示的位置的音频捕获集成。 然后，将音频是编辑和清理。 例如，可以替换为云汽车触角持续时间长达 1 秒钟左右即并重复几次，并将其使用安静的环境中的同一个捕获的音频部分拼接。

一旦建立一个位置的视频编辑声音的设计器可以同步对应的音频。 此时我们合作对照相机远程测试机组捕获和捕获移动，以决定哪些元素或组合，将工作来构建令人着迷的音频场景。 我们发现有用的技术是将所有声音元素添加到一个音频编辑器和生成快速线性模拟 ups 尝试使用不同的组合的想法。 这为我们提供更好地正确的想法构建实际的 HoloTour 场景的时候。

### <a name="assembling-the-scene"></a>组装场景

生成 3D 环境场景的第一步是创建将在一个场景中支持其他功能和交互的声音元素的常规背景环境循环声音的平台。 这样，我们采取针对不同的实现技术取决于特定需求和设计标准的任何特定场景的整体方法。 一些场景可能索引使用同步的摄像头捕获，而其他人可能需要一种多组织有序的方法更它们分别使用 HoloTour 更迷人时刻放置声音、 交互元素和音乐和声音效果。

索引时使用的相机捕获音频，我们放置空间启用声音的环境音频发射器对应于照相机方向的方向坐标以便北部照相机视图播放音频从北部麦克风和同样有关其他基数的说明。 这些发射器是现有的世界上锁定，这意味着用户可以自由地将其头与这些发射器和声音将更改相应地，有效地建模在该位置的声音。 到 Piazza Navona 或 Pantheon 侦听很好的相机捕获音频混合使用场景的示例。

另一种方法涉及使用放置播放随机化以卷、 俯仰和触发器的频率的一次性声音在场景周围的空间声音发射器播放循环立体声环境结合使用。 这将具有方向性增强意义上创建环境。 例如，在 Aguas Calientes 你可以侦听到每个象限的全景图的有意突出显示特定区域的地理位置，但协同工作以创建整体沉浸式环境的特定发射器的方式。

## <a name="tips-and-tricks"></a>提示和技巧

当你要将一起场景音频，有一些其他方法可用于进一步突出显示方向性和深入体验，充分利用 HoloLens 声音的空间功能。 我们提供了一些下面列表 — 侦听它们尝试 HoloTour 下一次。
* **查找目标**:这些是触发仅当你正在查看的特定对象或 holographic 框架区域的声音。 例如，查找街道端咖啡馆中罗马的 Piazza Navona 方向会略有触发忙餐厅的声音。
* **本地视觉**:旅程尽管 HoloTour 包含某些 beats 其中指导教程，但得益于全息，将了解如何深入的主题。 例如，在 Pantheon 外层溶解以以显示 oculus，reverberating 音频放如 Pantheon 的内侧 3D 发射器鼓励用户了解的内部模型中。
* **增强的方向性**:在许多场景，我们以各种方式将添加到方向性放置声音。 在 Pantheon 场景中，例如，喷泉声音已放单独发射器足够近，给用户，以便他们可以有 sonic 视差的意义上，因为它们周围的 play 空间遍历。 秘鲁的 Salinas de Maras 场景中作为单独发射器生成周围具有该位置的可信声音的用户更多沉浸式环境环境放置一些小的流的各个角度来看。
* **样条发射器**:此特殊的空间声音发射器移动在 3D 空间中相对于视觉对象附加到的位置。 此示例是中 Machu Picchu，其中我们使用自由绘制曲线发射器让不同的方向性和移动了解训练。
* **音乐和 SFX**:表示多风格或迷人方法的某些方面 HoloTour 使用音乐和声音效果以提高情绪的影响。 在 gladiator 一半罗马教程结束时，使用 whooshes 或 stingers 等特殊效果以帮助增强标签出现在场景中的效果。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>音频设计器 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [空间声音](spatial-sound.md)
* [空间合理的设计](spatial-sound-design.md)
* [在 Unity 中的空间声音](spatial-sound-in-unity.md)
* [MR Spatial 220](holograms-220.md)
* [视频：Microsoft HoloLens：HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
