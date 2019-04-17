---
title: 跟踪 Unity 中丢失
description: 跟踪 Unity 应用中的丢失的处理。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 中，跟踪丢失、 跟踪丢失映像
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592539"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="371e9-104">跟踪 Unity 中丢失</span><span class="sxs-lookup"><span data-stu-id="371e9-104">Tracking loss in Unity</span></span>

<span data-ttu-id="371e9-105">当设备找不到本身在世界中时，应用内体验"跟踪丢失"。</span><span class="sxs-lookup"><span data-stu-id="371e9-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="371e9-106">默认情况下，Unity 将暂停更新循环，然后向用户显示初始图像。</span><span class="sxs-lookup"><span data-stu-id="371e9-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="371e9-107">当跟踪重新获得时，初始图像将消失，update 循环继续。</span><span class="sxs-lookup"><span data-stu-id="371e9-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="371e9-108">作为替代方法，用户可以手动选择退出设置通过处理此转换。</span><span class="sxs-lookup"><span data-stu-id="371e9-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="371e9-109">所有内容将都似乎会变得跟踪丢失，如果不采取措施来对其进行处理过程中锁定的正文。</span><span class="sxs-lookup"><span data-stu-id="371e9-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="371e9-110">默认处理</span><span class="sxs-lookup"><span data-stu-id="371e9-110">Default Handling</span></span>

<span data-ttu-id="371e9-111">默认情况下，应用程序，以及所有消息和事件的更新循环持续时间内跟踪丢失将停止。</span><span class="sxs-lookup"><span data-stu-id="371e9-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="371e9-112">在该相同时，将向用户显示一个图像。</span><span class="sxs-lookup"><span data-stu-id="371e9-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="371e9-113">您可以通过转到编辑自定义此图像-> 设置-> 播放机中，单击初始图像并设置 Holographic 跟踪丢失图像。</span><span class="sxs-lookup"><span data-stu-id="371e9-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="371e9-114">手动处理</span><span class="sxs-lookup"><span data-stu-id="371e9-114">Manual Handling</span></span>

<span data-ttu-id="371e9-115">若要手动处理跟踪丢失，你需要转到**编辑** > **项目设置** > **播放机** >  **通用 Windows 平台设置选项卡** > **初始图像** > **Windows Holographic**并取消选中"在跟踪丢失暂停和显示图像".</span><span class="sxs-lookup"><span data-stu-id="371e9-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="371e9-116">然后，您需要使用下面指定的 Api 处理的更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="371e9-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="371e9-117">\**命名空间：\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="371e9-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="371e9-118">\**类型：\*\*\*WorldManager*</span><span class="sxs-lookup"><span data-stu-id="371e9-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="371e9-119">世界管理器公开的事件来检测跟踪丢失/获得 (*WorldManager.OnPositionalLocatorStateChanged*) 和要查询的当前状态的属性 (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="371e9-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="371e9-120">不活动的跟踪状态时，照相机不会出现在虚拟世界中转换，即使在用户将转换。</span><span class="sxs-lookup"><span data-stu-id="371e9-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="371e9-121">这意味着对象将不再对应于任何物理位置和所有都将出现锁定的正文。</span><span class="sxs-lookup"><span data-stu-id="371e9-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="371e9-122">处理你自己的跟踪更改时需要轮询状态属性，每个帧或句柄*OnPositionalLocatorStateChanged*事件。</span><span class="sxs-lookup"><span data-stu-id="371e9-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="371e9-123">轮询</span><span class="sxs-lookup"><span data-stu-id="371e9-123">Polling</span></span>

<span data-ttu-id="371e9-124">最重要的状态是*PositionalLocatorState.Active*这意味着跟踪将完全正常运行。</span><span class="sxs-lookup"><span data-stu-id="371e9-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="371e9-125">任何其他状态将导致主摄影机仅旋转增量。</span><span class="sxs-lookup"><span data-stu-id="371e9-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="371e9-126">例如：</span><span class="sxs-lookup"><span data-stu-id="371e9-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="371e9-127">处理 OnPositionalLocatorStateChanged 事件</span><span class="sxs-lookup"><span data-stu-id="371e9-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="371e9-128">或者，为了方便使用，您还可以订阅*OnPositionalLocatorStateChanged*以处理转换：</span><span class="sxs-lookup"><span data-stu-id="371e9-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="371e9-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="371e9-129">See also</span></span>
* [<span data-ttu-id="371e9-130">处理跟踪 DirectX 中丢失</span><span class="sxs-lookup"><span data-stu-id="371e9-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
