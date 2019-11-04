---
title: HoloLens 故障排除
description: Microsoft HoloLens 的故障排除步骤。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 问题、错误、故障排除、修复、帮助、支持、HoloLens
ms.openlocfilehash: 855bb0cafb0d3fba0d8d97c93d9415b51bcc2fb3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438281"
---
# <a name="hololens-troubleshooting"></a>HoloLens 故障排除

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>HoloLens 无响应或不启动

如果 HoloLens 无法启动：
* 如果电源按钮的 Led 指示灯未亮起，或只有1个 LED 闪烁，则您可能需要为 HoloLens 充电。
* 如果在按下电源按钮时指示灯亮起但在显示器上看不到任何内容，请按住电源按钮，直到电源按钮关闭所有5个 Led。

如果 HoloLens 已冻结或无响应：
* 按下电源按钮关闭 HoloLens，直到电源按钮的所有5个 Led 关闭，或者如果 Led 无响应，则为10秒。 再次按下 "电源" 按钮，启动。

如果以下步骤不起作用：
* 你可以尝试[恢复你的设备](reset-or-recover-your-hololens.md)。

## <a name="holograms-dont-look-good-or-are-moving-around"></a>全息影像看起来不好或正在四处移动。

如果你的全息影像不稳定、jumpy 或不正确，请尝试以下其中一项修复：
* 清洗设备面板，确保没有任何阻碍传感器的情况。
* 请确保空间中有足够的光线。
* 尝试浏览并查看你的环境，以便 HoloLens 可以更完整地扫描它们。
* 尝试运行校准应用。 它校准你的 HoloLens，最适合你的眼睛。 请参阅 "**设置**" > " **System** > **实用工具**"。 在校准下，选择 "**打开校准**"。
* 如果运行校准应用后仍遇到问题，请使用传感器优化应用来优化设备传感器。 请参阅 "**设置**" > " **System** > **实用工具**"。 在 "传感器调整" 下，选择 "**打开传感器优化**"。

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens 未响应我的手势。

若要确保 HoloLens 能看到你的手势，请将你的手置于手势帧中，这会在你的任意一侧延伸几个英尺。 当 HoloLens 能看到你的手时，光标将从点变为圆圈。 详细了解如何使用[笔势](gaze-and-commit.md#composite-gestures)。

如果你的环境太暗，则 HoloLens 可能看不到你的手，因此请确保有足够的光线。

如果你的面板具有指纹或涂抹，请使用 HoloLens 随附的 microfiber 清洁抹布来轻轻地清理面板。

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens 未响应语音命令。

如果 Cortana 没有响应语音命令，请确保 Cortana 已打开。 在 "所有应用" 列表中，选择 "Cortana >" 菜单 > 笔记本 ">" 设置 "进行更改。 若要详细了解你可以说的内容，请参阅使用语音控制 HoloLens。

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>我无法放置全息影像或查看以前放置的全息影像。

如果 HoloLens 无法映射或加载空间，它将进入限制模式，并且你将无法放置全息影像或查看已放置的全息影像。 可以尝试以下操作：
* 请确保环境中有足够的光线，以便 HoloLens 能够查看和映射空间。
* 请确保已连接到 Wi-fi 网络。 如果你未连接到 Wi-fi，则 HoloLens 无法识别并加载已知的空间。
* 如果需要创建新空间，请连接到 Wi-fi，然后重启 HoloLens。
* 若要查看正确的空间是否处于活动状态，或要手动加载空间，请参阅 "**设置**" > **系统** > **空间**"。
* 如果加载了正确的空间并且仍有问题，则空间可能已损坏。 若要解决此问题，请选择空间，然后选择 "删除"。 删除空间后，HoloLens 将开始映射你的环境并创建新空间。

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>我的 HoloLens 经常进入限制模式或显示 "跟踪丢失" 消息。

如果你的设备通常显示 "限制模式" 或 "跟踪丢失" 消息，请尝试从[我的全息影像看起来不太好或正在四处移动](#holograms-dont-look-good-or-are-moving-around)。

## <a name="my-hololens-cant-tell-what-space-im-in"></a>我的 HoloLens 无法判断我所在的空间。

如果你的 HoloLens 无法自动识别并加载你所在的空间，请确保你已连接到 Wi-fi，房间内有充足的光线，并且没有对周围的任何重大更改。 还可以通过转到 "**设置**" > **系统** > **空间**，手动加载空间或管理空间。

## <a name="im-getting-a-low-disk-space-error"></a>我收到 "磁盘空间不足" 错误。

你需要通过执行以下一项或多项操作来释放一些存储空间：
* 删除某些未使用的空间。 切换到 "**设置**" > **系统** > **空间**"，选择不再需要的空间，然后选择"**删除**"。
* 删除某些已放置的全息影像。
* 删除照片应用中的某些图片和视频。
* 从 HoloLens 卸载某些应用。 在 "所有应用" 列表中，点击并按住你要卸载的应用，然后选择 "**卸载**"。

## <a name="my-hololens-cant-create-a-new-space"></a>我的 HoloLens 无法创建新的空间。

最可能的问题是在存储空间不足的情况下运行。 请尝试上述其中一个[提示](#im-getting-a-low-disk-space-error)以释放一些磁盘空间。
