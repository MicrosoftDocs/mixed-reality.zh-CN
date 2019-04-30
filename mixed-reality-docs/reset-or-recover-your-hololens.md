---
title: 重置或恢复在 HoloLens
description: 有关重新启动或重置你 HoloLens 的基本和高级说明。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作说明，重新启动、 重置、 恢复，硬重置、 软重置、 电源周期 HoloLens，关闭
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591765"
---
# <a name="reset-or-recover-your-hololens"></a>重置或恢复在 HoloLens

如果遇到问题的可能想要尝试重新启动你 HoloLens，重置，或甚至重新刷新与恢复设备。 本文档将指导你完成连续的建议步骤。

## <a name="perform-a-device-reboot"></a>执行重启设备

如果你 HoloLens 时遇到问题或无响应，首先请尝试重新启动它通过以下方法。

### <a name="perform-a-safe-reboot-via-cortana"></a>执行安全的重新启动通过 Cortana

重新启动 HoloLens 的最安全方法是通过 Cortana。 HoloLens 有问题时，这通常是一个很好的第一个步骤：
1. 在你的设备上
2. 请确保上提供支持，用户登录并在设备不会等待对其进行解锁的密码。
3. 说"你好，小娜，重新启动"或"你好，小娜，重新启动。"
4. 当她确认她将要求你确认。 等待声音播放后完成她问题，该值指示她，倾听您的第二个，然后说"是"。
5. 设备将立即重新启动/重新启动。

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>执行安全的重新启动，通过 Windows Device Portal

如果上述不起作用，您可以尝试重新启动设备，通过[Windows Device Portal](using-the-windows-device-portal.md)。 在右上角没有重启/关机选项的设备。

### <a name="perform-a-safe-reboot-via-the-power-button"></a>执行安全的电源按钮通过重新启动

如果你仍不能重启你的设备，你可以尝试发出的电源按钮通过重新启动：
1. 按住电源按钮 5 秒
   1. 在 1 秒后将看到所有 5 个 Led 照亮，然后缓慢关闭从右到左
   2. 在 5 秒后所有 Led 将都处于关闭状态，指示已成功发出关闭命令
   3. 请注意，务必要停止按按钮后立即所有 Led 已关闭
2. 等待 1 分钟才能完全成功关闭。 请注意，即使显示处于关闭状态，关闭可能仍由正在进行中
3. 通过按住电源按钮 1 秒，再次在设备上的电源

### <a name="perform-an-unsafe-forced-reboot"></a>执行不安全的强制重启

如果上述方法都能够成功重新启动你的设备，您可以强制重新启动。 请注意，此方法等效于从 HoloLens，拉取电池在这种情况下，是一种危险操作，这可能会导致你的设备处于损坏状态。 

>[!WARNING]
>这是可能有害的方法，仅用于事件上述方法均无效。

1. 按下并保持至少 10 秒的电源按钮
   * 可以保留的时间超过 10 秒的按钮
   * 则可以安全地忽略任何 LED 活动
2. 释放按钮并等待 2-3 秒
3. 通过按住电源按钮 1 秒，再次在设备上的电源

## <a name="reset-the-device-to-a-factory-clean-state"></a>将设备重置为出厂干净状态

如果你 HoloLens 后重新启动后仍然遇到问题，可以尝试重置为出厂干净状态。 如果重置你的设备，将擦除所有个人数据、 应用和设置。 重置将仅安装的 Windows Holographic 安装的版本，并且必须重新初始化的所有步骤 (校准，连接到 WiFi、 创建用户帐户，下载应用程序，等等...)。
1. 启动**设置**应用程序->**更新** -> **重置**
2. 选择**重置设备**选项和读取确认对话框
3. 如果您同意遵守重置你的设备，设备将重新启动，显示旋转齿轮与进度栏的一组
4. 等待大约 30 分钟才能完成此过程
5. 重置将完成，并且设备将重新启动到全新体验

## <a name="perform-a-full-device-recovery"></a>执行完整的设备恢复

如果在之后执行上面的选项中，你的设备**仍**冻结，则可以恢复它使用 Windows Device Recovery Tool 的无响应，或正在经历的更新或软件问题。 恢复你的设备是类似于在意义上说，它将擦除设备，包括应用、 游戏、 照片、 用户帐户，和的详细信息上的所有用户内容重置。 如果可能，请备份你想要保留的任何信息。

若要完全恢复将 HoloLens:
1. 从您的 PC 断开所有手机和 Windows 设备的都连接
2. 安装并启动[Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) 在 PC 上
3. 连接到 PC 使用 micro USB 电缆它随附在 HoloLens
   * 请注意并非所有 USB 电缆都都生来平等。 即使你已使用另一根电缆已成功，此流将公开其中电缆可能也无法执行，新的状态。 在 HoloLens 附带的一个是最佳和最经过严格测试的选项
4. 如果该工具会自动检测你的设备，它将显示 HoloLens 磁贴。 单击它，然后按照说明进行操作以完成过程

>[!NOTE]
>WDRT 可以恢复到较旧版本的 Windows 全息版; 你的设备可能需要安装更新后闪烁

如果无法自动检测你的设备，请尝试以下工具：
1. 重新启动您的 PC 和重试 （这会修复大多数问题）
2. 单击**检测不到我的设备按钮**，选择**Microsoft HoloLens**，然后按照屏幕上的说明的其余部分
