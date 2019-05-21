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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592539"
---
# <a name="tracking-loss-in-unity"></a>跟踪 Unity 中丢失

当设备找不到本身在世界中时，应用内体验"跟踪丢失"。 默认情况下，Unity 将暂停更新循环，然后向用户显示初始图像。 当跟踪重新获得时，初始图像将消失，update 循环继续。

作为替代方法，用户可以手动选择退出设置通过处理此转换。 所有内容将都似乎会变得跟踪丢失，如果不采取措施来对其进行处理过程中锁定的正文。

## <a name="default-handling"></a>默认处理

默认情况下，应用程序，以及所有消息和事件的更新循环持续时间内跟踪丢失将停止。 在该相同时，将向用户显示一个图像。 您可以通过转到编辑自定义此图像-> 设置-> 播放机中，单击初始图像并设置 Holographic 跟踪丢失图像。

## <a name="manual-handling"></a>手动处理

若要手动处理跟踪丢失，你需要转到**编辑** > **项目设置** > **播放机** >  **通用 Windows 平台设置选项卡** > **初始图像** > **Windows Holographic**并取消选中"在跟踪丢失暂停和显示图像". 然后，您需要使用下面指定的 Api 处理的更改跟踪。

**命名空间：** *UnityEngine.XR.WSA*<br>
**类型：** *WorldManager*

* 世界管理器公开的事件来检测跟踪丢失/获得 (*WorldManager.OnPositionalLocatorStateChanged*) 和要查询的当前状态的属性 (*WorldManager.state*)
* 不活动的跟踪状态时，照相机不会出现在虚拟世界中转换，即使在用户将转换。 这意味着对象将不再对应于任何物理位置和所有都将出现锁定的正文。

处理你自己的跟踪更改时需要轮询状态属性，每个帧或句柄*OnPositionalLocatorStateChanged*事件。

### <a name="polling"></a>轮询

最重要的状态是*PositionalLocatorState.Active*这意味着跟踪将完全正常运行。 任何其他状态将导致主摄影机仅旋转增量。 例如：

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>处理 OnPositionalLocatorStateChanged 事件

或者，为了方便使用，您还可以订阅*OnPositionalLocatorStateChanged*以处理转换：

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

## <a name="see-also"></a>请参阅
* [处理跟踪 DirectX 中丢失](coordinate-systems-in-directx.md#handling-tracking-loss)
