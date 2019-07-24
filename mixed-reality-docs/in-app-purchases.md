---
title: 应用内购买
description: 混合现实应用支持应用内购买, 但有一些工作需要对它们进行设置。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 应用内购买, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515295"
---
# <a name="in-app-purchases"></a>应用内购买

HoloLens 中支持应用内购买, 但有一些工作需要进行设置。

若要利用应用购买功能, 你必须:
* 创建 XAML [2d 视图](app-views.md)以显示为一个石板
* 切换到它以激活放置, 这会使沉浸式视图
* 调用 API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

此 API 将显示 "常用 Windows 操作系统" 弹出窗口, 其中显示了应用内购买名称、说明和价格。 然后, 用户可以选择 "购买选项"。 操作完成后, 应用将需要显示允许用户切换回其[沉浸式视图](app-views.md)的 UI。

对于面向基于桌面的 Windows Mixed Reality 沉浸式耳机的应用程序, 无需在调用 RequestProductPurchaseAsync API 之前手动切换到 XAML 视图。
