---
title: 连接到 HoloLens 的 Wi-fi
description: 有关如何连接到无线 internet 与 HoloLens 以及如何确定设备的 IP 地址的说明。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens、 wifi、 无线、 internet、 ip、 ip 地址
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592864"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>连接到 HoloLens 的 Wi-fi

HoloLens 包含 802.11ac 的支持，2 x 2 个 Wi-fi 无线电。 连接到 Wi-fi 网络的 HoloLens 是类似于 Windows 10 桌面或移动设备连接到 Wi-fi 网络。

![HoloLens 的 Wi-fi 设置](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>连接到 HoloLens 上的 Wi-fi 网络

1. [布隆](gestures.md#bloom)到**启动**菜单。
2. 选择**设置**应用程序从开始或从**的所有应用**开始菜单右侧的列表。
3. **设置**应用将自动放置在您的前面。
4. 选择**网络和 Internet**。
5. 确保 WLAN 已打开。
6. 从列表中选择的 Wi-fi 网络。
7. 键入的 Wi-fi 网络密码 （如果需要）。

## <a name="disabling-wi-fi-on-hololens"></a>禁用 HoloLens 的 Wi-fi

### <a name="using-the-settings-app-on-hololens"></a>在 HoloLens 上使用设置应用

1. [布隆](gestures.md#bloom)到**启动**菜单。
2. 选择**设置**应用程序从开始或从**的所有应用**开始菜单右侧的列表。
3. **设置**应用将自动放置在您的前面。
4. 选择**网络和 Internet**。
5. 选择将其移到"Off"位置的 Wi-fi 滑块交换机。 这将关闭 Wi-fi 无线电的 RF 组件并禁用所有 HoloLens 的 Wi-fi 功能。 

    >[!WARNING]
    >HoloLens 将不能自动加载你[空格](environment-considerations-for-hololens.md#spaces)Wi-fi 无线电被禁用时。
    
6. 将滑块开关移到"开"位置来启用 Wi-fi 无线电和还原 Microsoft HoloLens 上的 Wi-fi 功能。 所选的 Wi-fi 无线电的状态 （"开"的"关"） 将在重新启动后保留。

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>如何确认你连接到 Wi-fi 网络

1. [布隆](gestures.md#bloom)以打开**启动**菜单。
2. 查看其中前角的开始菜单中的 Wi-fi 状态。 将显示状态的 Wi-fi 和连接的网络的 SSID。

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>识别你 HoloLens 的 Wi-fi 网络上的 IP 地址

### <a name="using-the-settings-app"></a>使用设置应用

1. [布隆](gestures.md#bloom)到**启动**菜单。
2. 选择**设置**应用程序从开始或从**的所有应用**开始菜单右侧的列表。
3. **设置**应用将自动放置在您的前面。
4. 选择**网络和 Internet**。
5. 向下滚动到下可用的 Wi-fi 网络的列表，然后选择**硬件属性**。

    ![硬件属性中的 Wi-fi 设置](images/wifi-hololens-hwdetails.jpg)

将下一步所示的 IP 地址**IPv4 地址**。

### <a name="using-cortana"></a>使用 Cortana

说"*你好，小娜，我的 IP 地址是什么？*" Cortana 将显示并读取你的 IP 地址。

### <a name="using-windows-device-portal"></a>使用 Windows Device Portal

1. 打开[设备门户](using-the-windows-device-portal.md#networking)在您的 PC 上的 web 浏览器中。
2. 导航到**网络**部分。

你的 IP 地址和其他网络信息将会显示在该处。 此方法允许开发 PC 上的 IP 地址的简单复制和粘贴。
