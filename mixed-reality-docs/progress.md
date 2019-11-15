---
title: 显示进度
description: 进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，控件，ui，ux
ms.openlocfilehash: aafcd8eebbabfc5b53d09348d513f62def909da6
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105983"
---
# <a name="progress-indicator"></a>进度指示器

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。 这意味着，在进度指示器可见，并且还可以根据所使用的指示器指示等待时长时，用户无法与该应用交互。

<br>

---

## <a name="types-of-progress"></a>进度类型

向用户提供有关发生的情况的信息非常重要。 在混合现实中，如果你的应用程序没有提供良好的视觉反馈，则可以轻松地在物理环境或对象上对其进行工作。 对于需要几秒钟时间的情况，例如，当加载数据或场景正在更新时，最好是显示可视指示器。 有两个选项可用于向用户显示操作正在进行–**进度栏**或**进度环**。

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>进度条<br>
        进度栏显示任务完成的百分比。 它应在持续时间已知（确定性）的操作过程中使用，但是不应阻止用户与应用程序交互。<br>
        <br>
        *图像： HoloLens 中的进度栏示例*
    :::column-end:::
        :::column:::
        ![空间](images/spacer-20x582.png)<br>
       HoloLens](images/640px-progressbar.jpg) 中的 ![进度栏示例<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>进度环<br>
        进度环仅具有不确定状态，并且在操作完成之前阻止任何其他用户交互时使用。<br>
        <br>
        *图像： HoloLens 中的进度环形示例*
    :::column-end:::
        :::column:::
        ![空间](images/spacer-20x582.png)<br>
       HoloLens 中的 ![进度环示例](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>自定义对象的进度<br>
        你可以通过使用你自己的自定义 2D/3D 对象自定义进度控件来添加到应用的个性和品牌标识。<br>
        <br>
        *Image：自定义网格示例（HoloLens）的进度*
    :::column-end:::
        :::column:::
        ![空间](images/spacer-20x582.png)<br>
       在 HoloLens 中 ![自定义网格示例的进度](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>最佳做法
* 将[billboarding 或标记一起](billboarding-and-tag-along.md)紧密地转换为进度的显示，因为用户可以轻松地将其标头移到空空间，并丢失上下文。 如果用户无法看到任何内容，你的应用可能看起来好像已崩溃。 Billboarding 和标记一起内置于 prefab 中。
* 提供有关用户发生的情况的状态信息始终是好的。 进度 prefab 提供了各种视觉样式，包括用于提供状态的 Windows 标准环形类型进度。 如果希望进度的样式与应用的品牌保持一致，还可以将自定义网格与动画一起使用。

<br>

---

## <a name="progress-indicator-in-mrtkmixed-reality-toolkit-for-unity"></a>Unity 的 MRTK （混合现实工具包）中的进度指示器

* [MRTK-进度指示器 prototyping](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-场景转换服务](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a>另请参阅

* [光标](cursors.md)
* [手动 ray](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [起源](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [邻近菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [提示](tooltip.md)
* [盖板](slate.md)
* [滑块](slider.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [Surface 磁性](surface-magnetism.md)
