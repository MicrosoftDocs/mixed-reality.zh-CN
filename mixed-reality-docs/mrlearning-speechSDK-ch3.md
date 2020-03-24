---
title: Azure 语音服务教程 - 3. 添加 Azure 认知服务语音翻译组件
description: 本课程介绍如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028320"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3.添加 Azure 认知服务语音翻译组件

在本教程中，你将在项目中添加语音翻译，以便可以将语音翻译和听录成三种不同的语言。

## <a name="objectives"></a>目标

* 了解如何集成 Azure 语音翻译

## <a name="instructions"></a>说明

在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 翻译识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：   

* 将“目标语言”更改为所选语言，例如“德语”  

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> MRTK 中未包含“Lunarcom 翻译识别器(脚本)”组件。 本教程的资产中随附了该组件。

如果现在进入“游戏”模式，可以先按卫星按钮来测试语音翻译。 假设计算机上配备了麦克风，当你讲话时，你的语音将翻译成所选语言，并在终端面板上听录：

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> 应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。

## <a name="congratulations"></a>祝贺

项目现在可以成功地将你讲出的词语翻译成多种不同的语言。 请在设备上运行该应用程序，以确保功能正常。

[下一教程：4.设置意向和自然语言理解](mrlearning-speechSDK-ch4.md)
