---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流（深度、环境跟踪和反射率）。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens
ms.openlocfilehash: 307df0c226221422f13af09d8f4944c22ead3865
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438306"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="15603-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="15603-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="15603-105">此功能添加为适用于 HoloLens 的[Windows 10 4 月2018更新](release-notes-april-2018.md)的一部分，在早期版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="15603-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="15603-106">研究模式是一项新功能，它提供对设备上的关键传感器的应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="15603-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="15603-107">这些地方包括：</span><span class="sxs-lookup"><span data-stu-id="15603-107">These include:</span></span>
- <span data-ttu-id="15603-108">系统用于地图生成和头跟踪的四个环境跟踪相机。</span><span class="sxs-lookup"><span data-stu-id="15603-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="15603-109">深度相机数据的两个版本–一种用于极接近深度的感应，通常用于跟踪，而另一种用于低频率（1-5 FPS）的深度感应，后者当前用于空间映射，</span><span class="sxs-lookup"><span data-stu-id="15603-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1-5 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="15603-110">由 HoloLens 使用的两个版本的反射率流来计算深度，但其自身的价值是，因为这些映像是从</span><span class="sxs-lookup"><span data-stu-id="15603-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="15603-111">![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="15603-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="15603-112">*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*</span><span class="sxs-lookup"><span data-stu-id="15603-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="15603-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="15603-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="15603-114"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="15603-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="15603-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="15603-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="15603-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="15603-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="15603-117">研究模式</span><span class="sxs-lookup"><span data-stu-id="15603-117">Research mode</span></span></td>
        <td><span data-ttu-id="15603-118">✔️</span><span class="sxs-lookup"><span data-stu-id="15603-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="15603-119">使用研究模式之前</span><span class="sxs-lookup"><span data-stu-id="15603-119">Before using Research mode</span></span>

<span data-ttu-id="15603-120">研究模式具有良好的名称：它旨在让学术和工业研究人员在计算机视觉和机器人的字段中试用新的观点。</span><span class="sxs-lookup"><span data-stu-id="15603-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="15603-121">研究模式不适用于将跨企业部署或在 Microsoft Store 中提供的应用程序。</span><span class="sxs-lookup"><span data-stu-id="15603-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="15603-122">这样做的原因是，研究模式降低了设备的安全性，消耗的电池电量比正常操作要大得多。</span><span class="sxs-lookup"><span data-stu-id="15603-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="15603-123">在将来的任何设备上，Microsoft 不会承诺支持此模式。</span><span class="sxs-lookup"><span data-stu-id="15603-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="15603-124">因此，我们建议你使用它来开发和测试新创意;但是，你将不能广泛地部署使用研究模式的应用程序，也不能保证它将继续在将来的硬件上工作。</span><span class="sxs-lookup"><span data-stu-id="15603-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="15603-125">启用研究模式</span><span class="sxs-lookup"><span data-stu-id="15603-125">Enabling Research mode</span></span>

<span data-ttu-id="15603-126">研究模式是开发人员模式的子模式。</span><span class="sxs-lookup"><span data-stu-id="15603-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="15603-127">首先需要在 "设置" 应用中启用 "开发人员模式" （"**设置" > 为开发人员 & 安全 >** ）：</span><span class="sxs-lookup"><span data-stu-id="15603-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="15603-128">将 "使用开发人员功能" 设置为 "**开**"</span><span class="sxs-lookup"><span data-stu-id="15603-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="15603-129">将 "启用设备门户" 设置为**打开**</span><span class="sxs-lookup"><span data-stu-id="15603-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="15603-130">然后，使用连接到与你的 HoloLens 相同的 Wi-fi 网络的 web 浏览器，导航到你的 HoloLens 的 IP 地址（通过 "**设置" > 网络 & Internet > "wi-fi > 硬件" 属性**）。</span><span class="sxs-lookup"><span data-stu-id="15603-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="15603-131">这是[设备门户](using-the-windows-device-portal.md)，你会在门户的 "系统" 部分中找到 "调研模式" 页：</span><span class="sxs-lookup"><span data-stu-id="15603-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="15603-132">HoloLens 设备门户的 ![研究模式选项卡](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="15603-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="15603-133">*HoloLens 设备门户中的研究模式*</span><span class="sxs-lookup"><span data-stu-id="15603-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="15603-134">选择 "**允许访问传感器流**" 后，将需要重新启动 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="15603-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="15603-135">可以从设备门户的页面顶部的 "电源" 菜单项下执行此操作。</span><span class="sxs-lookup"><span data-stu-id="15603-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="15603-136">重新启动设备后，通过设备门户加载的应用程序应能够访问研究模式流。</span><span class="sxs-lookup"><span data-stu-id="15603-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="15603-137">在应用中使用传感器数据</span><span class="sxs-lookup"><span data-stu-id="15603-137">Using sensor data in your apps</span></span>

<span data-ttu-id="15603-138">应用程序可以通过打开[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)流来访问传感器流数据，其方式与访问照片/视频摄像机流的方式完全相同。</span><span class="sxs-lookup"><span data-stu-id="15603-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="15603-139">在研究模式下，也可以使用适用于 HoloLens 开发的所有 Api。</span><span class="sxs-lookup"><span data-stu-id="15603-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="15603-140">具体而言，应用程序可以在每个传感器帧捕获时间精确地知道 HoloLens 在6DoF 空间的位置。</span><span class="sxs-lookup"><span data-stu-id="15603-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="15603-141">演示如何访问各种研究模式流的示例应用程序、如何使用内部函数和 extrinsics 以及如何记录流在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存储库中可用。</span><span class="sxs-lookup"><span data-stu-id="15603-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="15603-142">已知问题</span><span class="sxs-lookup"><span data-stu-id="15603-142">Known issues</span></span>

<span data-ttu-id="15603-143">请参阅 HoloLensForCV 存储库中的[问题跟踪](https://github.com/Microsoft/HololensForCV/issues)程序。</span><span class="sxs-lookup"><span data-stu-id="15603-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="15603-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15603-144">See also</span></span>

* [<span data-ttu-id="15603-145">Microsoft 媒体基础</span><span class="sxs-lookup"><span data-stu-id="15603-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="15603-146">HoloLensForCV GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="15603-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="15603-147">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="15603-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
