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
# <a name="voice-input"></a><span data-ttu-id="74490-104">语音输入</span><span class="sxs-lookup"><span data-stu-id="74490-104">Voice Input</span></span>

<span data-ttu-id="74490-105">若要在 HoloLens 上启用语音识别，开发人员需要在 "项目设置" 下的 Unreal 编辑器中启用 "麦克风" > 平台 > HoloLens > 功能。</span><span class="sxs-lookup"><span data-stu-id="74490-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="74490-106">设备还必须在设置中启用语音识别 > 隐私 > 语音并使用英语。</span><span class="sxs-lookup"><span data-stu-id="74490-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Windows 语音识别设置](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="74490-108">建议同时启用在线语音识别，以获得最佳的服务质量。</span><span class="sxs-lookup"><span data-stu-id="74490-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="74490-109">可在[此处](voice-input.md)找到针对 HoloLens 的语音识别的技术详细信息</span><span class="sxs-lookup"><span data-stu-id="74490-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="74490-110">然后，用户将看到一个对话框，其中显示了在应用程序首次启动时启用麦克风。</span><span class="sxs-lookup"><span data-stu-id="74490-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="74490-111">如果用户选择 "是"，应用程序将开始获取语音输入。</span><span class="sxs-lookup"><span data-stu-id="74490-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="74490-112">语音输入不需要特殊的 Windows Mixed Reality API，而是基于现有的 Unreal Engine 4 输入映射 API 构建的。</span><span class="sxs-lookup"><span data-stu-id="74490-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="74490-113">[此处](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)提供了有关如何使用输入 API 的详细信息</span><span class="sxs-lookup"><span data-stu-id="74490-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="74490-114">已将语音映射添加到引擎的绑定部分–输入以下操作和轴映射。</span><span class="sxs-lookup"><span data-stu-id="74490-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![UE4 引擎输入的输入](images/unreal/engine-input.png)
 
<span data-ttu-id="74490-116">下面是添加了针对全球 "跳转" 的监视的示例。</span><span class="sxs-lookup"><span data-stu-id="74490-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="74490-117">可以使用任何英语单词或短句子。</span><span class="sxs-lookup"><span data-stu-id="74490-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="74490-118">通过项目设置添加语音映射后，开发人员可以使用标准 Unreal 逻辑来处理输入，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="74490-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![简单的语音操作](images/unreal/input-action-bp.png)
