---
title: 重置或恢复 HoloLens
description: 用于重新启动或重置 HoloLens 的基本和高级说明。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作方法、重新启动、重置、恢复、硬重置、软重置、电源周期、HoloLens、关机
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524031"
---
# <a name="reset-or-recover-your-hololens"></a>重置或恢复 HoloLens

如果你在使用 HoloLens 时遇到问题, 你可能想要尝试重新启动、重置甚至重新启动设备恢复。 本文档将指导你逐步完成推荐的步骤。

## <a name="perform-a-device-reboot"></a>执行设备重新启动

如果 HoloLens 遇到问题或无响应, 请首先尝试通过以下方法之一重启它。

### <a name="perform-a-safe-reboot-via-cortana"></a>通过 Cortana 执行安全重新启动

重新启动 HoloLens 的最安全方式是通过 Cortana。 此问题通常是在遇到 HoloLens 问题时的最大第一步:
1. 放入设备
2. 请确保它已打开, 用户已登录, 并且设备不会等待密码来解锁。
3. 说 "你好 Cortana, reboot" 或 "你好 Cortana, restart"。
4. 确认她确认会要求您进行确认。 等待第二个声音在她完成她的问题后播放, 指出她正在倾听你, 然后说 "是"。
5. 设备现在将重新启动/重新启动。

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>通过 Windows 设备门户执行安全重新启动

如果上述操作不起作用, 你可以尝试通过[Windows 设备门户](using-the-windows-device-portal.md)重新启动设备。 在右上角, 可以选择重新启动/关闭设备。

### <a name="perform-a-safe-reboot-via-the-power-button"></a>通过 "电源" 按钮执行安全重新启动

如果仍无法重新启动设备, 则可以尝试通过 "电源" 按钮发出重新启动:
1. 按住电源按钮5秒钟
   1. 1秒后, 会看到所有5个 Led 都发亮, 然后从右到左缓慢关闭
   2. 5秒钟后, 所有 Led 都将关闭, 指示已成功发出关闭命令
   3. 请注意, 必须在所有 Led 都关闭后立即按下按钮, 这一点很重要。
2. 等待1分钟, 让关闭完全成功。 请注意, 即使显示器已关闭, 关闭仍可能仍在进行中
3. 按住电源按钮1秒钟, 再次打开设备

### <a name="perform-an-unsafe-forced-reboot"></a>执行不安全的强制重新启动

如果上述方法均无法成功重新启动设备, 则可以强制重新启动。 请注意, 此方法等效于从 HoloLens 拉取电池, 因此, 这是一项危险操作, 它可能会使你的设备处于损坏状态。 

>[!WARNING]
>这是一种潜在的有害方法, 只应在上述所有方法都不起作用的情况下使用。

1. 按住电源按钮至少10秒钟
   * 可以按住按钮超过10秒
   * 可以安全地忽略任何 LED 活动
2. 释放按钮并等待2-3 秒
3. 按住电源按钮1秒钟, 再次打开设备

## <a name="reset-the-device-to-a-factory-clean-state"></a>将设备重置为出厂清除状态

如果在重新启动后, HoloLens 仍遇到问题, 可以尝试将其重置为出厂清理状态。 如果重置设备, 将擦除所有个人数据、应用和设置。 重置将仅安装的 Windows Holographic 安装的版本，并且必须重新初始化的所有步骤 (校准，连接到 WiFi、 创建用户帐户，下载应用程序，等等...)。
1. 启动**设置**应用 >**更新** -> **重置**
2. 选择 "**重置设备**" 选项并阅读确认对话框
3. 如果你同意重置设备, 则设备将重新启动并显示一组旋转齿轮和一个进度栏
4. 等待大约30分钟, 以便完成此过程
5. 重置将完成, 并且设备将重新启动进入全新体验

## <a name="perform-a-full-device-recovery"></a>执行完整设备恢复

如果在执行上述选项后, 你的设备**仍**会被冻结、无响应或遇到更新或软件问题, 你可以使用 Windows 设备恢复工具恢复它。 恢复设备类似于重置设备, 因为它会擦除设备上的所有用户内容, 包括应用、游戏、照片、用户帐户等。 如果可能, 请备份任何要保留的信息。

若要完全恢复 HoloLens:
1. 断开所有手机和 Windows 设备与电脑的连接
2. 在电脑上安装和启动[Windows 设备恢复工具](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq)(WDRT)
3. 使用随附的微 USB 电缆将你的 HoloLens 连接到你的电脑
   * 请注意, 并不是所有的 USB 电缆都是相等的。 即使您已成功使用了另一条电缆, 此流也将公开缆线可能不会执行的新状态。 你的 HoloLens 附带的是最佳且最经过测试的选项
4. 如果该工具自动检测到你的设备, 它将显示一个 HoloLens 磁贴。 单击它, 然后按照说明完成该过程

>[!NOTE]
>WDRT 可以将你的设备恢复到较旧版本的 Windows 全息版;你可能需要在闪烁后安装更新

如果该工具无法自动检测到你的设备, 请尝试以下操作:
1. 重新启动计算机, 然后重试 (这会修复大多数问题)
2. 单击 "**未检测到我的设备" 按钮**, 选择 " **Microsoft HoloLens**", 然后按照屏幕上的其余说明操作
