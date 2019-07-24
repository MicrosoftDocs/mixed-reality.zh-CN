---
title: Unity 中的跟踪丢失
description: 在 Unity 应用中处理跟踪丢失。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 跟踪丢失, 跟踪丢失图像
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548740"
---
# <a name="tracking-loss-in-unity"></a>Unity 中的跟踪丢失

当设备在世界上找不到自己时, 应用程序会遇到 "跟踪丢失" 的情况。 默认情况下, Unity 将暂停更新循环并向用户显示初始映像。 重新获得跟踪后, 初始映像将消失, 更新循环将继续。

作为替代方法, 用户可以通过选择退出设置来手动处理此转换。 如果未执行任何处理操作, 则所有内容似乎会在跟踪丢失时变为正文锁定状态。

## <a name="default-handling"></a>默认处理

默认情况下, 应用的更新循环以及所有消息和事件将在跟踪丢失期间停止。 同时, 系统会向用户显示一个映像。 可以通过以下方式自定义此映像: 转到 "编辑"-> "设置-> 播放器", 单击 "闪屏", 然后设置 "全息跟踪丢失" 图像。

## <a name="manual-handling"></a>手动处理

若要手动处理跟踪丢失情况, 需要执行 "**编辑** > **项目设置** > **播放器** > **通用 Windows 平台设置" 选项卡的 "**  > **启动图像**" > **Windows 全息**版, 并取消选中 "跟踪丢失时暂停并显示映像"。 此后, 需要处理跟踪更改和下面指定的 Api。

**命名空间：**  *UnityEngine.XR.WSA*<br>
**类型：** *WorldManager*

* 全局管理器公开一个事件来检测跟踪丢失/获取 (*WorldManager*) 和用于查询当前状态的属性 (*WorldManager*)
* 如果跟踪状态为非活动状态, 即使用户翻译, 照相机也不会在虚拟世界中进行转换。 这意味着对象将不再与任何物理位置相对应, 并且所有对象都将显示为正文锁定状态。

处理自己的跟踪更改时, 需要轮询每个帧的状态属性, 或处理*OnPositionalLocatorStateChanged*事件。

### <a name="polling"></a>轮询

最重要的状态为*PositionalLocatorState* , 这意味着跟踪功能完全正常。 任何其他状态将仅导致对主相机的循环增量。 例如：

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

另外, 更方便的是, 还可以订阅*OnPositionalLocatorStateChanged*来处理转换:

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
* [在 DirectX 中处理跟踪丢失](coordinate-systems-in-directx.md#handling-tracking-loss)
