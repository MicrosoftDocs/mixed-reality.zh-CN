---
title: 案例研究-HoloTour 的空间音效设计
description: 若要创建适用于 Microsoft HoloLens 的真正沉浸式3D 虚拟教程，全景视频和全息版风景只是公式的一部分。
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，HoloTour，空间音效，案例研究
ms.openlocfilehash: e1da80bd647084aa4d7839c0f1b1848b46c2b1b4
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641147"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>案例研究-HoloTour 的空间音效设计

若要创建适用于 Microsoft HoloLens 的真正沉浸式3D 虚拟教程，全景视频和全息版风景只是公式的一部分。 音频设计人员 Jason Syltebo 讨论了如何捕获和处理声音，以使您感到真实在 HoloTour 的每个位置。

## <a name="the-tech"></a>技术人员

你在 HoloTour 中看到的精美图像和全息场景只是创建可信混合现实体验的一部分。 尽管全息影像只能在用户的正面直观显示，但 HoloLens 的[空间音效](spatial-sound.md)功能允许来自所有方向的音频，这为用户提供了更完整的传感器体验。

使用空间声音，我们可以提供音频提示来指示用户应关闭的方向，或让用户知道在其空间内有更多的全息影像。 我们还可以将声音直接附加到全息图，并持续更新布局的方向和距离，使其看起来像是从该对象直接发出的。

通过 HoloTour，我们想要利用 HoloLens 的空间音效功能来创建360度的环境环境，并将其与视频同步，以展示特定位置的 sonic 亮点。

## <a name="behind-the-scenes"></a>幕后

我们创建了两个不同位置的 HoloTour 体验：罗马和 Machu Picchu。 为了使这些教程感觉真实且引人注目，我们希望避免使用一般声音，而直接从我们与的位置捕获音频。

### <a name="capturing-the-audio"></a>捕获音频

在我们[关于捕获 HoloTour 视觉内容的案例研究](case-study-capturing-and-creating-content-for-holotour.md)中，我们谈论了照相机远程测试的自定义设计。 它包含在三维打印架中包含的14个 GoPro 摄像机，适用于特定尺寸的架。 若要从该远程测试机组捕获音频，请在相机下添加一个四重麦克风阵列，这些阵列送入了一个紧凑型四通道的录音单元中，该单位是一颗 我们选择的麦克风不仅表现良好，而且占用的空间非常小，因此无法遮蔽照相机的视图。

![自定义相机和麦克风远程测试机组](images/camera-rig-microphones-300px.png)<br>
*自定义相机和麦克风装置*

此设置从照相机的确切位置以四个方向捕获声音，为我们提供了足够的信息来重新创建使用空间声音的3D 听觉全景，稍后我们可以同步到360的视频。

照相机阵列音频面临的难题之一是，在捕获时所记录的受到。 即使视频捕获非常好，声音捕获仍会出现问题，因为相机声音，如 sirens、飞机或高释放。 为了确保我们具有我们所需的所有元素，我们使用了一系列立体声和单声道移动录音单元来获取每个位置的特定兴趣点上的异步环境元素。 此捕获非常重要，因为它使声音设计器能够查找可在后期生产中使用的清理和可用内容，并添加更多方向性。

给定的捕获日期会生成大量文件。 开发系统以跟踪与特定位置或相机拍摄相对应的文件，这一点很重要。 我们的记录单位设置为按日期自动命名文件并获得数字，我们会在一天结束时将这些文件恢复到外部驱动器。 最起码，口头方式传达 slating 的音频录制非常重要，因为这样可以轻松地识别内容，而文件名会成为一个问题。 当视频和音频记录为单独的媒体并且需要在 post 期间进行同步时，我们也很重要。

### <a name="editing-the-audio"></a>编辑音频

在拍摄捕获行程后的工作室，汇编方向和沉浸式听觉体验的第一步是查看某个位置的所有音频捕获，并确定最佳做法，并确定在集成度. 然后，将编辑并清理音频。 例如，如果有一个很大的汽车，则可以将其替换为同一个捕获中的安静环境音频部分，并在其中拼接。

为某个位置建立视频编辑后，声音设计器可以同步相应的音频。 此时，我们使用了相机远程处理捕获和移动捕获来确定哪些元素或组合可用于构建沉浸式音频场景。 我们发现的一项技术非常有用，就是将所有声音元素添加到音频编辑器中，并构建快速的线性模拟来试验各种混合创意。 这为我们提供了一段时间来构建实际 HoloTour 场景提供了更好的建议。

### <a name="assembling-the-scene"></a>组合场景

构建三维环境场景的第一步是创建一个一般背景环境循环声音平台，它将支持场景中的其他功能和交互式声音元素。 在此过程中，我们采取了一种方法，该方法面向由任何特定场景的特定需求和设计标准确定的不同实现技术。 某些场景可能会使用同步的相机捕获进行索引，而有些场景可能需要更多的特选方法，该方法使用更单独的声音、交互式元素和音乐，并在 HoloTour 中获得更多的迷人。

使用相机捕获音频进行索引时，我们将启用了空间声音的环境音频发射器与相机方向的方向坐标相对应，以使 "北方相机" 视图播放来自西北麦克风的音频，同样其他关键指导。 这些发射器是世界上锁定的，这意味着用户可以自由地将其与这些发射器相关联，而声音将相应变化，从而有效地对该位置的声音建模。 倾听 Piazza Navona 或 Pantheon，了解使用良好的相机捕获音频的场景示例。

一种不同的方法，涉及到循环立体声环境与位于场景周围的空间声音发射器一起播放一种随机声音，这些声音在量、间距和触发频率方面是随机的。 这将创建一个具有更强方向性的环境。 例如，在 Aguas Calientes 中，可以倾听全景的每个象限如何具有专门突出显示地域特定区域的特定发射器，但要一起工作以创建总体沉浸式环境。

## <a name="tips-and-tricks"></a>提示和技巧

当你将音频组合到一起时，还有一些其他方法可用于进一步突出显示方向性和浸入式，从而充分利用了 HoloLens 的空间音效功能。 我们提供了以下部分的列表-在下一次尝试 HoloTour 时，请对其进行侦听。
* **查找目标**：仅在查看全息帧的特定对象或区域时才触发这些声音。 例如，在罗马的 Piazza Navona 中查看街道端咖啡馆的方向时，将会略微触发繁忙餐馆的声音。
* **本地愿景**：尽管 HoloTour 的旅程包含某些节拍，但你的浏览指南（通过全息影像）将深入探讨主题。 例如，作为 Pantheon 的外观，以显示 oculus，reverberating 音频作为来自 Pantheon 内部的3D 发射器，鼓励用户浏览内部模型。
* **增强方向**性：在许多场景中，我们以各种方式将声音置于多方向中。 例如，在 Pantheon 场景中，fountain 的声音作为单独的发射器放置在靠近用户的位置，因此他们可以在播放空间中找到 "sonic 视差"。 在秘鲁的 Salinas de Maras 场景中，某些小流的单独观点被放置为单独的发射器，以构建一个更具沉浸的环境环境，并将用户与该位置的真实声音包围起来。
* **样条发射器**：此特殊空间声发射器相对于其所附加到的对象的视觉位置在3d 空间中移动。 例如，在 Machu Picchu 中，我们使用样条发射器给出了不同的方向性和运动。
* **音乐和 SFX**： HoloTour 的某些方面，表示更风格或更迷人的方法使用音乐和声音效果来提高情绪影响。 在罗马教程末尾的 gladiator 中，使用 whooshes 或 stingers 等特殊效果有助于增强标签在场景中的效果。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>音频设计器 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅
* [空间音效](spatial-sound.md)
* [空间音效设计](spatial-sound-design.md)
* [Unity 中的空间音效](spatial-sound-in-unity.md)
* [视频： Microsoft HoloLens： HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
