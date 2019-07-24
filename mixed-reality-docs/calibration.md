---
title: 校准
description: 校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。 HoloLens 和 Windows Mixed Reality 沉浸式耳机提供自定义 IPD 的方式。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 校准, 舒适, 视觉对象, 质量, ipd
ms.openlocfilehash: 5f8e6aef1df0efe4c64c807e627f69c7949363f2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974805"
---
# <a name="improve-visual-quality-and-comfort"></a>改善视觉质量和舒适
HoloLens、HoloLens 2 和 Windows Mixed Reality 沉浸式耳机提供不同的方法来改善视觉体验的质量。 

## <a name="hololens"></a>HoloLens

校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。

### <a name="during-setup"></a>安装期间

![第二步的 IPD finger 对齐屏幕](images/ipd-finger-alignment-300px.jpg)<br>

*第二步的 IPD finger 对齐屏幕*

在 HoloLens 上, 系统会在安装过程中提示你校准视觉对象。 这允许设备根据用户的[interpupillary 距离](https://en.wikipedia.org/wiki/Interpupillary_distance)(IPD) 调整全息图显示。 使用不正确的 IPD 时, 全息影像可能出现不稳定或距离不正确。

Cortana 引入后, 第一个安装步骤是校准。 建议你在此设置阶段完成校准步骤, 但可以通过等待 Cortana 提示你说 "跳过" 来跳转到。

要求用户将其手指与每个眼睛一系列六个目标对齐。 在此过程中, HoloLens 为用户设置了正确的 IPD。 如果需要更新或调整新用户的校准, 可以使用校准应用在安装程序外运行。

### <a name="calibration-app"></a>校准应用

可随时通过校准应用执行校准。 校准应用默认安装, 并可通过 "开始" 菜单或 "设置" 应用进行访问。 如果要改善视觉对象的质量或为新用户校准视觉对象, 则建议使用校准。

**启动应用程序开始**
1. 使用[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 选择 **+** 若要查看所有应用。
3. 启动**校准**。

![从 shell 访问校准应用程序](images/calibration-shell.png)

![启动后显示为活动多维数据集的校准应用](images/calibration-livecube-200px.png)

**从设置启动应用**
1. 使用[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 选择 **+** 若要查看所有应用，如果**设置**不固定到开始。
3. 启动**设置**。
4. 导航到 "**系统** > **实用程序**" 并选择 "**打开校准**"。

![从 "设置" 应用启动校准应用](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a>HoloLens 2

### <a name="calibration"></a>校准 

在 HoloLens 2 上, 系统会提示你在设备安装过程中校准你的视觉对象。 要求用户查看固定目标集。 这允许设备调整全息图呈现, 使用户能够准确定位全息影像、更舒适的3D 查看体验和改进的显示质量。 所有调整都是动态发生的, 无需手动优化。 

### <a name="calibration-when-sharing-a-device"></a>共享设备时的校准 

Hololens 2 设备可以在不同人员之间共享, 无需每个人进行设备设置。 如果用户是设备的新用户, 则在将设备放在 head 上时, Hololens 2 将提示用户校准视觉对象。 如果用户已在设备上校准视觉对象, 则在用户将设备放在打印头上时, 将无缝调整显示器的质量和舒适的观看体验。  

### <a name="launching-the-calibration-app-from-settings"></a>从设置启动校准应用
1. 使用 "开始手势" 转到 "开始" 菜单。
2. 选择 **+** 若要查看所有应用，如果**设置**不固定到开始。
3. 启动**设置**。
4. 导航到 "**系统** > **实用程序**" 并选择 "**打开校准**"。

## <a name="immersive-headsets"></a>沉浸式头戴显示设备

若要更改耳机内的 IPD, 请打开设置应用并导航到**混合现实** > **耳机显示**, 并移动滑块控件。 你将在你的耳机上实时看到更改。 如果你知道 IPD, 可能是由于访问 optometrist, 你也可以直接输入。

你还可以通过转到电脑上的 "**设置** > "**混合现实** > **耳机显示**来调整此设置。

如果头戴显示设备不支持 IPD 自定义, 则会禁用此设置。

## <a name="see-also"></a>请参阅
* [HoloLens 的环境注意事项](environment-considerations-for-hololens.md)
