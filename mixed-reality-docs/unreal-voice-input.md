---
title: 语音输入
description: 介绍如何使用语音输入
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835299"
---
# <a name="voice-input"></a>语音输入

若要在 HoloLens 上启用语音识别，开发人员需要在 "项目设置" 下的 Unreal 编辑器中启用 "麦克风" > 平台 > HoloLens > 功能。 设备还必须在设置中启用语音识别 > 隐私 > 语音并使用英语。

![Windows 语音识别设置](images/unreal/speech-recognition-settings.png)

建议同时启用在线语音识别，以获得最佳的服务质量。 可在[此处](voice-input.md)找到针对 HoloLens 的语音识别的技术详细信息

然后，用户将看到一个对话框，其中显示了在应用程序首次启动时启用麦克风。 如果用户选择 "是"，应用程序将开始获取语音输入。

语音输入不需要特殊的 Windows Mixed Reality API，而是基于现有的 Unreal Engine 4 输入映射 API 构建的。 [此处](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)提供了有关如何使用输入 API 的详细信息

已将语音映射添加到引擎的绑定部分–输入以下操作和轴映射。 

![UE4 引擎输入的输入](images/unreal/engine-input.png)
 
下面是添加了针对全球 "跳转" 的监视的示例。 可以使用任何英语单词或短句子。 

通过项目设置添加语音映射后，开发人员可以使用标准 Unreal 逻辑来处理输入，如以下示例中所示： 
 
![简单的语音操作](images/unreal/input-action-bp.png)
