---
title: 在 Unreal 中注视输入
description: 说明如何在 Unreal 中使用注视输入
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens，目视跟踪
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835617"
---
# <a name="gaze-input"></a>注视输入

Windows Mixed Reality 插件不为注视输入提供任何特殊功能。 一切都可通过标准 Unreal API 使用。

[打印头注视 API](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>眼动跟踪

若要使用目视跟踪 API，开发人员应在其 HoloLens 项目设置中启用 "注视输入" 功能。 当应用程序启动时，用户将看到以下同意提示

![目视输入权限](images/unreal/eye-input-permissions.png)
 
如果用户提供了其权限，则该应用程序将会获得目视的输入。 

[此处](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)介绍了 Unreal 的目视跟踪 API

[此处](eye-tracking.md)提供目视跟踪的技术详细信息

请注意，对于 Unreal，HoloLens 眼睛跟踪对于这两种眼睛都有一个注视。 HoloLens 不提供 stereoscopic 眼跟踪。
