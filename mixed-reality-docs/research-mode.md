---
title: HoloLens 研究模式
description: 在 HoloLens 上使用研究模式下，应用程序可以访问关键的设备传感器数据流 （深度、 跟踪、 环境和 IR 反射率）。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式、 cv、 rs4、 计算机视觉、 研究、 HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590096"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="2d6ba-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="2d6ba-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="2d6ba-105">此功能已添加的一部分[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)HoloLens，为和早期版本上不可用。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="2d6ba-106">研究模式是提供的设备应用程序访问密钥的传感器的 HoloLens 的新功能。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="2d6ba-107">这些问题包括：</span><span class="sxs-lookup"><span data-stu-id="2d6ba-107">These include:</span></span>
- <span data-ttu-id="2d6ba-108">四个跟踪系统的映射生成和头跟踪使用的照相机的环境。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="2d6ba-109">两个版本的深度相机数据 – 一个用于高频率 （每秒 30 帧） 附近深度检测通常用于在手动跟踪，，另一个用于较低频率 (表示 1 FPS) 远端的深度检测当前使用的空间映射</span><span class="sxs-lookup"><span data-stu-id="2d6ba-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="2d6ba-110">HoloLens 用于计算深度，但自己权限内的有价值，因为这些映像是从 HoloLens 照明和合理的环境光线不会影响 IR 反射率流的两个版本。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="2d6ba-111">![研究模式应用程序屏幕截图](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="2d6ba-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="2d6ba-112">*显示在研究模式下提供八个传感器数据流的测试应用程序的混合的现实捕获*</span><span class="sxs-lookup"><span data-stu-id="2d6ba-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="2d6ba-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="2d6ba-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2d6ba-114">功能</span><span class="sxs-lookup"><span data-stu-id="2d6ba-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="2d6ba-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2d6ba-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2d6ba-116"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="2d6ba-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2d6ba-117">信息检索模式</span><span class="sxs-lookup"><span data-stu-id="2d6ba-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="2d6ba-118">✔️</span><span class="sxs-lookup"><span data-stu-id="2d6ba-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="2d6ba-119">使用研究模式之前</span><span class="sxs-lookup"><span data-stu-id="2d6ba-119">Before using Research mode</span></span>

<span data-ttu-id="2d6ba-120">研究模式也名为： 适用于学术和工业研究人员尝试使用计算机视觉和机器人的字段中的新创意。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="2d6ba-121">研究模式不适合将整个企业内部署或可在 Microsoft Store 中的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="2d6ba-122">这样做的原因是设备的研究模式降低了你的安全性，并使用比正常操作的更多电量。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="2d6ba-123">Microsoft 不提交到任何将来使用的设备上支持此模式。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="2d6ba-124">因此，我们建议使用它来开发和测试新的想法;但是，您将不能广泛部署的应用程序使用研究模式或具有任何保证，它将继续在将来的硬件上工作。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="2d6ba-125">启用研究模式</span><span class="sxs-lookup"><span data-stu-id="2d6ba-125">Enabling Research mode</span></span>

<span data-ttu-id="2d6ba-126">研究模式是开发人员模式下的子模式。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="2d6ba-127">首先需要启用开发人员模式下设置应用中的 (**设置 > 更新和安全 > 面向开发人员**):</span><span class="sxs-lookup"><span data-stu-id="2d6ba-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="2d6ba-128">将设置为"使用开发人员功能"**上**</span><span class="sxs-lookup"><span data-stu-id="2d6ba-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="2d6ba-129">将"启用设备门户"设置为**上**</span><span class="sxs-lookup"><span data-stu-id="2d6ba-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="2d6ba-130">然后使用连接到你 HoloLens，相同的 Wi-fi 网络的 web 浏览器导航到你 HoloLens 的 IP 地址 (通过获得**设置 > 网络和 Internet > Wi-fi > 硬件属性**)。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="2d6ba-131">这是[设备门户](using-the-windows-device-portal.md)，并将在门户的"系统"部分中找到"研究模式"页：</span><span class="sxs-lookup"><span data-stu-id="2d6ba-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="2d6ba-132">![HoloLens 设备门户研究模式选项卡](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="2d6ba-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="2d6ba-133">*HoloLens 设备门户中的信息检索模式*</span><span class="sxs-lookup"><span data-stu-id="2d6ba-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="2d6ba-134">选择后**允许访问传感器数据流**，则将需要重新启动 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="2d6ba-135">可以从位于页面顶部的"Power"菜单项下的设备门户来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="2d6ba-136">后重新启动你的设备，通过设备门户已加载的应用程序应能够访问研究模式流。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="2d6ba-137">应用程序中使用传感器数据</span><span class="sxs-lookup"><span data-stu-id="2d6ba-137">Using sensor data in your apps</span></span>

<span data-ttu-id="2d6ba-138">应用程序可以通过打开访问传感器数据流式传输[Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)中完全相同的方式访问照片/视频照相机流的流。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="2d6ba-139">适用于 HoloLens 开发的所有 Api 都都可在研究模式时。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="2d6ba-140">具体而言，应用程序可以知道准确地说，HoloLens 是 6DoF 空间中每个传感器帧捕获时间点。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="2d6ba-141">显示访问各种研究模式流的方式、 如何使用内部函数和 extrinsics，以及如何记录流的示例应用程序均位于[HoloLensForCV GitHub 存储库](https://github.com/Microsoft/HoloLensForCV)。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="2d6ba-142">已知问题</span><span class="sxs-lookup"><span data-stu-id="2d6ba-142">Known issues</span></span>

<span data-ttu-id="2d6ba-143">请参阅[问题跟踪程序](https://github.com/Microsoft/HololensForCV/issues)HoloLensForCV 存储库中。</span><span class="sxs-lookup"><span data-stu-id="2d6ba-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d6ba-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="2d6ba-144">See also</span></span>

* [<span data-ttu-id="2d6ba-145">Microsoft 媒体基础</span><span class="sxs-lookup"><span data-stu-id="2d6ba-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="2d6ba-146">HoloLensForCV GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="2d6ba-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="2d6ba-147">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="2d6ba-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
