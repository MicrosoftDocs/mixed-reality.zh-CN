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
# <a name="in-app-purchases"></a><span data-ttu-id="6b9f2-104">应用内购买</span><span class="sxs-lookup"><span data-stu-id="6b9f2-104">In-app purchases</span></span>

<span data-ttu-id="6b9f2-105">HoloLens，支持应用内购买，但可将其设置一些工作。</span><span class="sxs-lookup"><span data-stu-id="6b9f2-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="6b9f2-106">若要利用中的应用购买功能，您必须：</span><span class="sxs-lookup"><span data-stu-id="6b9f2-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="6b9f2-107">创建 XAML[二维视图](app-views.md)显示为一台平板电脑</span><span class="sxs-lookup"><span data-stu-id="6b9f2-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="6b9f2-108">切换到它，以激活放置，离开沉浸式视图</span><span class="sxs-lookup"><span data-stu-id="6b9f2-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="6b9f2-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="6b9f2-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="6b9f2-110">显示应用内购买名称、 说明和价格的股票 Windows OS 弹出窗口会显示此 API。</span><span class="sxs-lookup"><span data-stu-id="6b9f2-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="6b9f2-111">然后，用户可以选择购买选项。</span><span class="sxs-lookup"><span data-stu-id="6b9f2-111">The user can then choose purchase options.</span></span> <span data-ttu-id="6b9f2-112">完成操作后，应用将需要显示 UI，这样用户就可以切换回其[沉浸式视图](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9f2-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="6b9f2-113">对于面向桌面基于 Windows Mixed Reality 沉浸式耳机的应用程序，它不是需要手动切换到 XAML 视图，然后再调用 RequestProductPurchaseAsync API。</span><span class="sxs-lookup"><span data-stu-id="6b9f2-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
