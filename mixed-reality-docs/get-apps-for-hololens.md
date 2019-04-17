---
title: 为 HoloLens 获取应用
description: 介绍 HoloLens，同时通过 Microsoft Store 和旁加载安装应用。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 旁加载、 旁加载、 加载、 存储、 uwp、 应用程序中，安装
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590105"
---
# <a name="get-apps-for-hololens"></a>为 HoloLens 获取应用

为 Windows 10 设备，HoloLens 支持许多的现有 UWP 应用程序从应用商店，以及新应用程序是专为 HoloLens。 基于这些数据，甚至可能需要向[开发](development-overview.md)并安装你自己的应用或与您的朋友 ！

## <a name="installing-apps"></a>安装应用

有三种方法在 HoloLens 上安装新的应用程序。 主要方法是从 Windows 应用商店中安装新的应用程序。 但是，还可以安装自己的应用程序使用设备门户或通过从 Visual Studio 部署。

### <a name="from-the-microsoft-store"></a>从 Microsoft Store
1. 执行[布隆](gestures.md#bloom)手势以打开[开始菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。
2. 选择应用商店应用，然后点击要将此磁贴放入您的世界。
3. 应用商店应用程序打开后，使用搜索栏查找任何所需的应用程序。
4. 选择**获取**或**安装**上的应用程序页 （购买可能会需要）。

### <a name="installing-an-application-package-with-the-device-portal"></a>使用设备门户安装应用程序包
1. 从建立连接[设备门户](using-the-windows-device-portal.md)面向 HoloLens。
2. 导航到**应用**页左侧导航窗格中的。
3. 下**应用程序包**浏览到与你的应用程序相关联的.appx 文件。
  >[!IMPORTANT]
  >请确保引用任何关联的依赖项和证书文件。

4. 单击**转**。

![在 Microsoft HoloLens 上 Windows Device Portal 中安装的应用窗体](images/deviceportal-appmanager.jpg)<br>
使用 Windows Device Portal HoloLens 上安装应用

### <a name="deploying-from-microsoft-visual-studio-2015"></a>从 Microsoft Visual Studio 2015 进行部署
1. 打开应用的 Visual Studio 解决方案 （.sln 文件）。
2. 打开项目的**属性**。
3. 选择以下的生成配置：母版/x86/远程计算机。
4. 选择远程计算机时：
   * 请确保地址点到 HoloLens 的 WiFi IP 地址。
   * 为通用 （未加密的协议） 设置身份验证。
5. 生成解决方案。
6. 单击**远程计算机**按钮以部署到你 HoloLens 从进行开发的电脑应用。 如果你已有现有生成 HoloLens 上，选择是以重新安装此较新版本。<br>
  ![应用到在 Visual Studio 中的 Microsoft HoloLens 的远程计算机部署](images/vs2015-remotedeployment.jpg)<br>
7. 应用程序将安装和自动在 HoloLens 上的启动。
