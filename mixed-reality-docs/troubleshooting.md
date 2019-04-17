---
title: HoloLens 故障排除
description: 对于 Microsoft HoloLens 的故障排除步骤。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 问题、 bug、 进行故障排除、 修复、 帮助、 支持、 HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590109"
---
# <a name="hololens-troubleshooting"></a>HoloLens 故障排除

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>我 HoloLens 无响应或无法启动

如果你 HoloLens 无法启动：
* 如果由电源按钮不指示灯都会保持运行，或只有 1 LED 短暂地闪烁，您可能需要从你 HoloLens 收取相关费用。
* 如果指示灯亮起时按下电源按钮，但您不能在显示器上看到任何内容，，保留电源按钮，直到所有 5 个 Led 的电源按钮都将关闭。

如果你 HoloLens 变得冻结或无响应：
* 通过按电源按钮，直到所有 5 个 Led 的电源按钮本身，打开或关闭 10 秒钟，如果的 Led 为无响应关闭你 HoloLens。 按下电源按钮再次启动。

如果这些步骤不起作用：
* 你可以尝试[恢复你的设备](reset-or-recover-your-hololens.md)。

## <a name="holograms-dont-look-good-or-are-moving-around"></a>全息看起来不好或四处移动。

如果你全息不稳定、 动摇，或者看起来不合适，请尝试这些修复程序之一：
* 清理设备面板，并确保执行任何操作都不阻止传感器。
* 请确保你的聊天室中没有足够 light。
* 请尝试移动办公了并查看周围的环境是 HoloLens 可以对其进行扫描更完整地。
* 尝试运行校准应用。 它并校验适合你自己在 HoloLens。 转到**设置** > **系统** > **实用程序**。 在下校准，选择**打开校准**。
* 如果仍在运行校准应用程序后遇到问题，可以使用传感器优化应用程序来优化设备传感器。 转到**设置** > **系统** > **实用程序**。 在下传感器优化，选择**打开传感器优化**。

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens 不响应我笔势。

若要确保 HoloLens 可以看到你笔势，请在手势框架中，扩展了几个立足于您的任何一侧保留您的手。 时 HoloLens 可以看到您的手，光标就会将更改从一个圆点为一个环。 深入了解如何使用[手势](gestures.md)。

如果你的环境是否太暗，HoloLens 不可能会看到您的手，因此请确保足够指示灯亮起。

如果你面板具有指纹或涂抹，请使用清洁随附 HoloLens 轻轻地清理在面板的布种微纤维。

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens 不应对我语音命令。

如果 Cortana 语音命令没有响应，请确保启用 Cortana。 在所有应用列表中，选择 Cortana > 菜单 > 笔记本 > 设置进行更改。 若要了解有关您可以说的详细信息，请参阅使用语音控制 HoloLens。

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>无法将放置全息或请参阅我以前放置的全息。

如果 HoloLens 不能映射或加载你的空间，它将进入 Limited 模式下，并将无法放置全息或请参阅的全息已放置。 可以尝试以下操作：
* 请确保有足以阐明您的环境中使 HoloLens 可看到并映射空间。
* 请确保已连接到 Wi-fi 网络。 如果您没有连接到 Wi-fi，HoloLens 不能标识和加载已知的空间。
* 如果需要创建一个新的空间，连接到 Wi-fi，然后重新启动你 HoloLens。
* 若要查看正确的空间是否处于活动状态，或手动加载一个空格，请转到**设置** > **系统** > **空格**。
* 如果加载正确的空间，并且仍遇到问题，空间可能已损坏。 若要解决此问题，选择的空间，然后选择删除。 一旦删除了空格，HoloLens 将开始映射周围的环境并创建一个新的空间。

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>我 HoloLens 频繁进入 Limited 模式下，或者会显示"跟踪丢失"消息。

如果你的设备通常会显示"限制的模式"或"跟踪丢失"消息，请尝试从建议[我全息看起来不好或四处移动](#holograms-dont-look-good-or-are-moving-around)。

## <a name="my-hololens-cant-tell-what-space-im-in"></a>我 HoloLens 不能告诉我在何种空间。

如果你 HoloLens 无法自动识别并加载您在的空间，请确保已连接到的 Wi-fi、 有很多的空间中的光和未存在于环境的任何重大更改。 此外可以手动加载一个空格，或通过转到管理你空格**设置** > **系统** > **空格**。

## <a name="im-getting-a-low-disk-space-error"></a>我收到"磁盘空间不足"错误。

你将需要释放一些存储空间，通过执行一个或多个以下操作：
* 删除一些未使用的空间。 转到**设置** > **系统** > **空间**，选择一个空格，也不再需要并选择**删除**.
* 删除一些已放置的全息。
* 删除某些图片和视频的照片应用中。
* 从你 HoloLens 卸载某些应用程序。 在所有应用程序列表中，点击并按住应用的程序想要卸载，然后选择**卸载**。

## <a name="my-hololens-cant-create-a-new-space"></a>我 HoloLens 不能创建一个新的空间。

最可能的问题是，您要运行存储空间不足。 请尝试之一[上述提示](#im-getting-a-low-disk-space-error)以释放一些磁盘空间。
