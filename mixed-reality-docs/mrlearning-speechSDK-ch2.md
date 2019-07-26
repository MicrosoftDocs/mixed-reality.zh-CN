---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b13b22fcdce2e7fa1319d241302b764f457aabba
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485606"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a>2.  添加本地语音到文本转换的脱机模式

在本教程中, 我们将添加一个脱机模式, 使你能够在无法连接到 Azure 服务时执行本地语音到文本转换。 我们还将*模拟*断开连接状态。

## <a name="instructions"></a>说明

1. 选择层次结构中的 Lunarcom_Base 对象, 并在 "检查器" 面板中单击 "添加组件"。 搜索并选择 "Lunarcom 脱机识别"。

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. 单击 LunarcomOfflineRecognizer 中的下拉箭头, 然后选择 "已启用"。 这会使项目的行为类似于用户没有连接。 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. 现在, 按下 "在 Unity 编辑器中播放" 并对其进行测试。 在屏幕左下角按下麦克风, 开始说话。 

> [!NOTE]
> 由于我们处于脱机状态, 因此唤醒 word 功能已禁用。 每次希望在离线时识别语音时, 您都必须每次都单击麦克风。 

下面是场景外观的示例。

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>祝贺

脱机模式已启用。 现在, 脱机时, 仍可以使用 speech SDK 来处理项目! 


[下一教程:3.添加 Azure 认知服务语音翻译组件](mrlearning-speechSDK-ch3.md)

