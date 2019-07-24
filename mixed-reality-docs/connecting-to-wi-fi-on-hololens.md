---
title: 在 HoloLens 上连接到 Wi-fi
description: 说明如何通过 HoloLens 连接到无线 internet, 以及如何识别设备的 IP 地址。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, 无线, internet, ip, ip 地址
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670117"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>在 HoloLens 上连接到 Wi-fi

HoloLens 包含一种支持 802.11 ac 的 2x2 Wi-fi 无线电。 将 HoloLens 连接到 Wi-fi 网络类似于将 Windows 10 桌面版或移动设备连接到 Wi-fi 网络。

![HoloLens Wi-fi 设置](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>在 HoloLens 上连接到 Wi-fi 网络

1. [布隆](gestures.md#bloom)到 "**开始**" 菜单。
2. 从 "开始" 菜单右侧的 "开始" 或 "**所有应用**" 列表中选择 "**设置**" 应用。
3. "**设置**" 应用将自动置于你前面。
4. 选择 "**网络 & Internet**"。
5. 确保 WLAN 已打开。
6. 从列表中选择 "Wi-fi 网络"。
7. 键入 Wi-fi 网络密码 (如果需要)。

## <a name="disabling-wi-fi-on-hololens"></a>在 HoloLens 上禁用 Wi-fi

### <a name="using-the-settings-app-on-hololens"></a>在 HoloLens 上使用 "设置" 应用

1. [布隆](gestures.md#bloom)到 "**开始**" 菜单。
2. 从 "开始" 菜单右侧的 "开始" 或 "**所有应用**" 列表中选择 "**设置**" 应用。
3. "**设置**" 应用将自动置于你前面。
4. 选择 "**网络 & Internet**"。
5. 选择 "Wi-fi" 滑块开关, 将其移动到 "关" 位置。 这会关闭 Wi-fi 无线电的 RF 组件, 并在 HoloLens 上禁用所有 Wi-fi 功能。 

    >[!WARNING]
    >在禁用 Wi-fi 无线电时, HoloLens 将无法自动加载你的[空间](environment-considerations-for-hololens.md#WiFi fingerprint considerations)。
    
6. 将滑块切换到 "打开" 位置, 打开 Wi-fi 收音机并在 Microsoft HoloLens 上还原 Wi-fi 功能。 所选的 Wi-fi 无线电状态 ("关闭") 将在重新启动后保持。

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>如何确认已连接到 Wi-fi 网络

1. [布隆](gestures.md#bloom)打开 "**开始**" 菜单。
2. 查看 "开始" 菜单左上方的 "Wi-fi" 状态。 将显示 Wi-fi 的状态和已连接网络的 SSID。

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>在 Wi-fi 网络上确定 HoloLens 的 IP 地址

### <a name="using-the-settings-app"></a>使用 "设置" 应用

1. [布隆](gestures.md#bloom)到 "**开始**" 菜单。
2. 从 "开始" 菜单右侧的 "开始" 或 "**所有应用**" 列表中选择 "**设置**" 应用。
3. "**设置**" 应用将自动置于你前面。
4. 选择 "**网络 & Internet**"。
5. 向下滚动到可用 Wi-fi 网络列表下, 选择 "**硬件属性**"。

    ![Wi-fi 设置中的硬件属性](images/wifi-hololens-hwdetails.jpg)

IP 地址将显示在 " **IPv4 地址**" 旁边。

### <a name="using-cortana"></a>使用 Cortana

说 "*你好 Cortana, 我的 IP 地址是什么？* " Cortana 将显示并读出你的 IP 地址。

### <a name="using-windows-device-portal"></a>使用 Windows 设备门户

1. 在电脑上的 web 浏览器中打开[设备门户](using-the-windows-device-portal.md#networking)。
2. 导航到 "**网络**" 部分。

你的 IP 地址和其他网络信息将显示在此处。 此方法允许在开发电脑上轻松复制和粘贴 IP 地址。
