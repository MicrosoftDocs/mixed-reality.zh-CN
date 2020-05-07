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
# <a name="gaze-input"></a><span data-ttu-id="c2bd2-104">注视输入</span><span class="sxs-lookup"><span data-stu-id="c2bd2-104">Gaze Input</span></span>

<span data-ttu-id="c2bd2-105">Windows Mixed Reality 插件不为注视输入提供任何特殊功能。</span><span class="sxs-lookup"><span data-stu-id="c2bd2-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="c2bd2-106">一切都可通过标准 Unreal API 使用。</span><span class="sxs-lookup"><span data-stu-id="c2bd2-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="c2bd2-107">打印头注视 API</span><span class="sxs-lookup"><span data-stu-id="c2bd2-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="c2bd2-108">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="c2bd2-108">Eye tracking</span></span>

<span data-ttu-id="c2bd2-109">若要使用目视跟踪 API，开发人员应在其 HoloLens 项目设置中启用 "注视输入" 功能。</span><span class="sxs-lookup"><span data-stu-id="c2bd2-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="c2bd2-110">当应用程序启动时，用户将看到以下同意提示</span><span class="sxs-lookup"><span data-stu-id="c2bd2-110">When the application starts, user will see the following consent prompt</span></span>

![目视输入权限](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="c2bd2-112">如果用户提供了其权限，则该应用程序将会获得目视的输入。</span><span class="sxs-lookup"><span data-stu-id="c2bd2-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="c2bd2-113">[此处](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)介绍了 Unreal 的目视跟踪 API</span><span class="sxs-lookup"><span data-stu-id="c2bd2-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="c2bd2-114">[此处](eye-tracking.md)提供目视跟踪的技术详细信息</span><span class="sxs-lookup"><span data-stu-id="c2bd2-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="c2bd2-115">请注意，对于 Unreal，HoloLens 眼睛跟踪对于这两种眼睛都有一个注视。</span><span class="sxs-lookup"><span data-stu-id="c2bd2-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="c2bd2-116">HoloLens 不提供 stereoscopic 眼跟踪。</span><span class="sxs-lookup"><span data-stu-id="c2bd2-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>
