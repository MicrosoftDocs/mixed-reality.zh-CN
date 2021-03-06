---
title: 6. 打包并部署到设备或仿真器
description: 教程系列第 6 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: c49e2a69cb97a996da4bf601a105c2176ccf267f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303538"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.打包并部署到设备或仿真器

## <a name="overview"></a>概述

在上一个教程中，你添加了一个简单的按钮，来将象棋棋子重置到原始位置。 这是最后一个部分，介绍了如何将此应用准备就绪，以在 HoloLens 2 或仿真器中运行它。 如果你有 HoloLens 2，则可以从计算机进行流式传输，或者打包应用，以便直接在设备上运行。 如果没有设备，则打包应用，以便在仿真器上运行它。 本部分结束时，你将拥有一个已部署的混合现实应用，你可以通过交互和 UI 充分利用它。

## <a name="objectives"></a>目标

* [仅设备] 通过全息应用远程处理流式传输到 HoloLens 2
* 打包应用并将其部署到 HoloLens 2 设备或仿真器

## <a name="device-only-streaming"></a>[仅设备] 流式传输
在这种情况下，[全息远程处理](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)是指将数据从电脑或独立 UWP 设备流式传输到 HoloLens 2，而非切换通道。 这种方法的工作方式是，远程处理主机应用从 HoloLens 接收输入数据流，在虚拟沉浸式视图中呈现内容，并通过 Wi-Fi 将内容帧流式传输回 HoloLens。 通过流式处理，可以将远程沉浸式视图添加到现有的台式电脑软件中，并可访问更多系统资源。 

如果要将此方法用于该象棋应用，需要完成以下事项：

1.  在 HoloLens 2 上从 Microsoft Store 安装并运行“全息远程处理播放器”。 请注意应用中显示的 IP 地址。

2.  返回到 Unreal 编辑器，转到“编辑”>“项目设置”，然后选中“全息远程处理”部分中的“启用远程处理”  。

3.  重启编辑器，然后输入设备的 IP 地址（如全息远程处理播放器应用中所示），然后单击“连接”。

连接后，单击“开始”按钮右侧的下拉箭头，然后选择“VR 预览”。  此操作将在“VR 预览”窗口中运行应用，该窗口将流式传输到 HoloLens 头戴显示设备。 

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>通过设备门户打包和部署应用

>[!NOTE]
>如果这是你第一次为 HoloLens 打包 Unreal 应用，则需要从 Epic Launcher 下载支持文件。 
>- 转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。   
>- 在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。 
>![项目设置 - 描述](images/unreal-uxt/6-installationoptions.PNG)

1.  转到“编辑”>“项目设置”。 
    * 在“项目 > 描述 > 关于 > 项目名称”下，添加项目名称。 
    * 在“项目”>“描述”>“发布者”>“公司可分辨名称”下，添加“CN=YourCompanyName” 。

> [!IMPORTANT]
> 如果将这些字段中的任一字段留空，那么当你在步骤 3 中尝试生成新证书时将遇到错误。 

> [!IMPORTANT]
> 发布者的名称必须采用 [LADPv3 可分辨名称格式](https://www.ietf.org/rfc/rfc2253.txt)。 格式不正确的发布者名称会导致在打包时出现“找不到签名密钥。 无法对应用进行数字签名。” 错误。

![项目设置 - 描述](images/unreal-uxt/6-cn.PNG)

2.  在“平台 > HoloLens”下，启用“为 HoloLens 仿真生成”和/或“为 HoloLens 设备生成”。  

3.  单击“打包”部分（在“签名证书”旁）中的“生成新的”  。

> [!IMPORTANT]
> 如果使用的是已生成的证书，证书的发布者名称则必须与应用程序的发布者名称相同。 否则，会导致“找不到签名密钥。 无法对应用进行数字签名。” error。

![项目设置 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. 当系统提示你创建私钥密码时，出于测试目的，请单击“无”。

![正在生成新证书](images/unreal-uxt/6-private-key-testing.png)

5. 转到“文件”>“包项目”并选择“HoloLens”。 
    * 创建新文件夹以保存包，并单击“选择文件夹”。 

6.  打包应用后，请打开 [Windows 设备门户](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)，转到“视图 > 应用”，并找到“部署应用”部分。

7.  单击“浏览...”，转到“ChessApp.appxbundle”文件，然后单击“打开”。   

    * 如果这是你第一次在设备上安装应用，请选中“允许我选择框架包”旁的复选框。 
    * 在下一个对话框中，包含相应的 VCLibs 和 appx 文件（arm64 用于设备，x64 用于仿真器）。  在保存包的文件夹中，可以从 HoloLens 下找到这些文件。

8.  单击“安装” 
    * 现在可以转到“所有应用”，并点击新安装的应用来运行它，或者可以直接从 Windows 设备门户启动应用。  

恭喜！ 你的 HoloLens 混合现实应用程序已完成，并且可随时运行。 不过，这不是旅途的尽头。 MRTK 有许多独立功能，你可以将其添加到项目中，其中包括空间映射、凝视和语音输入甚至 QR 码。 有关这些功能的详细信息，请参阅 [Unreal 开发概述](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。
