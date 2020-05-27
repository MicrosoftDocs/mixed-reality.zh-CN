---
title: 6. 打包并部署到设备或仿真器
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 6 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519960"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.打包并部署到设备或仿真器

本部分将指导你完成在 HoloLens 2 设备或仿真器上运行应用的准备步骤。 如果你有设备，则可以从计算机流式传输到设备，或者打包应用，以便直接在设备上运行。 如果没有设备，则需要打包应用，使其在仿真器上运行。 

## <a name="objectives"></a>目标

* [仅设备] 通过全息应用远程处理将应用流式传输到 HoloLens 2
* 打包应用并将其部署到 HoloLens 2 设备或仿真器

## <a name="device-only-stream"></a>[仅设备] 流式传输

1.  在 HoloLens 2 上从 Microsoft Store 安装并运行“全息远程处理播放器”

2.  转到“编辑”>“项目设置”。 在“全息远程处理”部分中，选中复选框以启用远程处理并重新启动编辑器。

3.  输入设备的 IP 地址，并单击“连接”。

4.  连接后，在 UE4 Editor 中，单击“播放”按钮右侧的下拉箭头，然后选择“VR 预览”。

## <a name="package-and-deploy-your-app"></a>打包和部署应用 

>[!NOTE]
>如果这是你第一次为 HoloLens 打包 Unreal 应用，则需要从 Epic Launcher 下载支持文件。 为此，请在 Epic Games Launcher 中转到“库”选项卡。 选择“启动”旁边的下拉箭头，然后选择“选项”。 在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。 
>![项目设置 - 描述](images/unreal-uxt/6-installationoptions.PNG)

1.  转到“编辑”>“项目设置”。 在“项目”>“描述”>“关于”>“项目名称”下，为项目指定名称。 在“项目”>“描述”>“发布者”>“公司可分辨名称”下，输入“CN={INSERT COMPANY NAME}”。 将其中任一字段留空将导致错误。 

![项目设置 - 描述](images/unreal-uxt/6-cn.PNG)

2.  在“平台”>“HoloLens”下，根据所需的目标，选择“模拟”和/或“设备”。

3.  在“打包”部分的“签名证书”旁，单击“生成新证书”按钮生成新的签名证书。 返回到主窗口。

![项目设置 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  转到“文件”>“包项目”并选择“HoloLens”。 创建新文件夹以保存包，并单击“选择文件夹”。 

5.  成功打包应用后，请打开“Windows 设备门户”，转到“视图”>“应用”，并找到“部署应用”部分。

6.  单击“浏览...”并导航到“ChessApp.appxbundle”文件。 单击“打开” 。 

    * 如果这是你第一次在设备上安装应用，请选中“允许我选择框架包”旁的复选框。 在下一个对话框中，包含相应的 VCLibs appx 文件（arm64 用于设备，x64 用于仿真器）。 

7.  单击“安装” 

祝贺你学完本教程！  