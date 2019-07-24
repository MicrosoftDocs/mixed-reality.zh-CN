---
title: 获取 HoloLens 应用
description: 介绍如何通过 Microsoft Store 和边载安装 HoloLens 的应用。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 旁加载, 端负载, 边负载, 存储, uwp, 应用, 安装
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522568"
---
# <a name="get-apps-for-hololens"></a>获取 HoloLens 应用

作为 Windows 10 设备, HoloLens 支持应用商店中的许多现有 UWP 应用程序以及专为 HoloLens 构建的新应用程序。 基于这些应用程序, 您甚至可以[开发](development-overview.md)和安装自己的应用程序或您的朋友的应用程序!

## <a name="installing-apps"></a>正在安装应用

可以通过三种方式在 HoloLens 上安装新的应用。 主要方法是从 Windows 应用商店安装新的应用程序。 不过, 也可以使用设备门户或从 Visual Studio 部署应用程序来安装自己的应用程序。

### <a name="from-the-microsoft-store"></a>从 Microsoft Store
1. 执行[布隆](gestures.md#bloom)笔势以打开 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 选择应用商店应用, 然后点击将此磁贴置于世界中。
3. 应用商店应用打开后, 使用搜索栏查找任何所需的应用程序。
4. 在应用程序页上选择 "**获取**" 或 "**安装**" (可能需要购买)。

### <a name="installing-an-application-package-with-the-device-portal"></a>使用设备门户安装应用程序包
1. 建立从[设备门户](using-the-windows-device-portal.md)到目标 HoloLens 的连接。
2. 导航到左侧导航栏中的 "**应用**" 页。
3. 在 "**应用包**" 下, 浏览到与应用程序关联的 .appx 文件。
  >[!IMPORTANT]
  >请确保引用任何关联的依赖项和证书文件。

4. 单击 "**开始**"。

![在 Microsoft HoloLens 上的 Windows 设备门户中安装应用表单](images/deviceportal-appmanager.jpg)<br>
使用 Windows 设备门户在 HoloLens 上安装应用

### <a name="deploying-from-microsoft-visual-studio-2015"></a>从 Microsoft Visual Studio 2015 进行部署
1. 打开应用的 Visual Studio 解决方案 (.sln 文件)。
2. 打开项目的 "**属性**"。
3. 选择以下生成配置:Master/x86/远程计算机。
4. 选择 "远程计算机" 时:
   * 请确保该地址指向 HoloLens 的 WiFi IP 地址。
   * 将身份验证设置为通用 (未加密的协议)。
5. 构建解决方案。
6. 单击 "**远程计算机**" 按钮, 将开发 PC 中的应用部署到 HoloLens。 如果已有一个 HoloLens 现有版本, 请选择 "是" 以重新安装此更新版本。<br>
  ![Visual Studio 中适用于应用的远程计算机部署到 Microsoft HoloLens](images/vs2015-remotedeployment.jpg)<br>
7. 应用程序将在你的 HoloLens 上安装和自动启动。
