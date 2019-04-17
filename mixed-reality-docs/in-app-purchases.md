---
title: 应用内购买
description: 在混合的现实应用中，支持应用内购买，但一些操作来设置它们。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 在应用内购买、 hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592561"
---
# <a name="in-app-purchases"></a>应用内购买

HoloLens，支持应用内购买，但可将其设置一些工作。

若要利用中的应用购买功能，您必须：
* 创建 XAML[二维视图](app-views.md)显示为一台平板电脑
* 切换到它，以激活放置，离开沉浸式视图
* Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

显示应用内购买名称、 说明和价格的股票 Windows OS 弹出窗口会显示此 API。 然后，用户可以选择购买选项。 完成操作后，应用将需要显示 UI，这样用户就可以切换回其[沉浸式视图](app-views.md)。

对于面向桌面基于 Windows Mixed Reality 沉浸式耳机的应用程序，它不是需要手动切换到 XAML 视图，然后再调用 RequestProductPurchaseAsync API。
