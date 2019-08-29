---
title: 校准
description: 校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。 HoloLens 和 Windows Mixed Reality 沉浸式耳机提供自定义 IPD 的方式。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 校准, 舒适, 视觉对象, 质量, ipd
ms.openlocfilehash: e86319dadeda02f71427b87980268eaf18942c49
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122082"
---
# <a name="improve-visual-quality-and-comfort"></a>改善视觉质量和舒适
HoloLens、HoloLens 2 和 Windows Mixed Reality 沉浸式耳机提供不同的方法来改善视觉体验的质量。 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>校准

Hololens 2 旨在为客户提供最高质量的视觉图像和舒适。 使用目视跟踪技术来改善查看和与虚拟环境交互的用户体验。  

在 HoloLens 2 上, 系统会提示你在设备安装过程中校准你的视觉对象。 要求用户查看一组固定目标。 这允许设备将全息图调整为用户, 以确保准确定位全息影像、舒适的3D 查看体验和改进的显示质量。 所有调整都是动态进行的, 无需手动优化。 通过使用眼睛作为特征点, 设备会单独调整到每个用户, 并且视觉对象随着耳机变化的使用而进行调整。 目视跟踪由系统在内部使用, 开发人员无需执行任何操作即可利用此功能。 事实上, 开发人员不能使用此信息。
请参阅[目视跟踪 api](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) , 了解有关目视跟踪系统为开发人员提供的数据类型的详细信息。

在 Hololens 2 上, 执行校准还可以确保为每个用户提供准确的目视跟踪。 眼动跟踪可让应用程序实时跟踪用户正在注视的位置。 这是开发人员可利用的主要功能, 实现全新级别的上下文、人工理解和智能体验中的交互。  

校准数据存储在本地设备上, 且不与任何帐户信息关联。 没有已使用该设备的用户没有校准的记录。 这意味着, 用户首次使用设备时, 将提示用户进行校准, 还会提示选择 "之前" 或 "校准不成功" 的用户。 在 "**设置** > " "**隐私** > "**跟踪**器中, 始终可以从设备中删除校准数据。 

### <a name="calibration-failures"></a>校准失败
校准应该适用于大多数用户, 但在某些情况下, 用户可能无法成功校准。  
校准失败的一些示例如下:
- 用户发生了分散注意力, 并没有在校准体验期间查看校准目标
- 脏或有划痕的设备面板或设备面板未正确定位 
- 某些类型的 contact 重用功能区和眼镜 (彩色触点重用功能区、toric contact 重用功能区、红外阻挡眼镜、和等)
- 有脏或有划痕
- 更明显的组成部分, 一些 eyelash 扩展
- 眼睛和/或设备面板的 Occlusions (眼镜)
- 眼睛 physiology, 某些眼睛情况和/或目视外科 (一些狭窄的眼睛、长 eyelashes、amblyopia、nystagmus、LASIK 或其他眼睛 surgeries 等的一些情况)

如果校准失败, 请尝试以下修复之一: 
- 清理设备面板
- 清理眼镜
- 将设备面板一直推送到
- 请确保不会阻碍传感器或眼睛 (例如头发) 
- 请确保房间内有足够的光线, 并且不受直射直射
- 请确保在校准过程中仔细关注目标

如果你遵循了所有准则, 并且校准仍失败, 则可以在 "**设置** > " "**系统** > **校准**" 中禁用校准提示: *"如果新用户使用此 Hololens, 则会自动要求运行目视校准"* 。 请注意, 这可能会导致更糟的全息图呈现质量和 discomfort。

### <a name="launching-the-calibration-app-from-settings"></a>从设置启动校准应用
1. 前往 HoloLens 2 上的 "设置" 页
    * 使用 *"开始手势"* 打开 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。 或者, 您也可以直接说 *"开始"* 。
    * 如果**设置**未固定到 "开始", 请选择 "**所有应用**" 以查看所有应用
    * 启动**设置**
2. 导航到**系统** > 校准 > **目视校准**, 并选择 "**运行目视校准**"


### <a name="calibration-when-sharing-a-devicesession"></a>共享设备/会话时的校准
Hololens 2 可以在不同人员之间共享, 而无需每个人完成设备设置体验。
如果用户是设备的新用户, 则在将设备放在 head 上时, Hololens 2 将提示用户校准视觉对象。 如果用户之前在设备上校准了视觉对象, 则在用户将设备放在打印头上时, 显示器将无缝调整以获得质量和舒适的观看体验。 


## <a name="hololens-v1"></a>HoloLens (v1)
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


## <a name="immersive-headsets"></a>沉浸式头戴显示设备

若要更改耳机内的 IPD, 请打开设置应用并导航到**混合现实** > **耳机显示**, 并移动滑块控件。 你将在你的耳机上实时看到更改。 如果你知道 IPD, 可能是由于访问 optometrist, 你也可以直接输入。

你还可以通过转到电脑上的 "**设置** > "**混合现实** > **耳机显示**来调整此设置。

如果头戴显示设备不支持 IPD 自定义, 则会禁用此设置。

## <a name="see-also"></a>请参阅
* [HoloLens 的环境注意事项](environment-considerations-for-hololens.md)
