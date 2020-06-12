---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流（深度、环境跟踪和反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens，HoloLens 2
ms.openlocfilehash: 62b82e3a36452d4b104bf04999e556ec19d2a5e3
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720393"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="af2fc-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="af2fc-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="af2fc-105">概述</span><span class="sxs-lookup"><span data-stu-id="af2fc-105">Overview</span></span>

<span data-ttu-id="af2fc-106">第一代 HoloLens 中引入了研究模式，可用于访问设备上的关键传感器，尤其适用于不适用于部署的研究应用程序。</span><span class="sxs-lookup"><span data-stu-id="af2fc-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="af2fc-107">你现在可以从以下输入收集数据：</span><span class="sxs-lookup"><span data-stu-id="af2fc-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="af2fc-108">**可见的轻型环境跟踪相机**-系统用于 head 跟踪和地图构建。</span><span class="sxs-lookup"><span data-stu-id="af2fc-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="af2fc-109">**深度相机**–在两种模式下运行：</span><span class="sxs-lookup"><span data-stu-id="af2fc-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="af2fc-110">用于[手动跟踪](interaction-fundamentals.md)的短期、高频率（30 FPS）近深度感知</span><span class="sxs-lookup"><span data-stu-id="af2fc-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="af2fc-111">长整型抛出，[空间映射](spatial-mapping.md)使用的最深层度（1-5 FPS）</span><span class="sxs-lookup"><span data-stu-id="af2fc-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="af2fc-112">**反射率的两个版本**： HoloLens 用于计算深度。</span><span class="sxs-lookup"><span data-stu-id="af2fc-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="af2fc-113">这些图像通过红外，并不受环境可见光的影响。</span><span class="sxs-lookup"><span data-stu-id="af2fc-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="af2fc-114">如果使用的是 HoloLens 2，还可以访问以下输入：</span><span class="sxs-lookup"><span data-stu-id="af2fc-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="af2fc-115">**加速感应**程序–由系统用来确定沿 X、Y 和 Z 轴和重心的线性加速度。</span><span class="sxs-lookup"><span data-stu-id="af2fc-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="af2fc-116">**Gyro** –系统用来确定旋转。</span><span class="sxs-lookup"><span data-stu-id="af2fc-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="af2fc-117">**磁力仪**–系统用于估计绝对方向。</span><span class="sxs-lookup"><span data-stu-id="af2fc-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="af2fc-118">![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="af2fc-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="af2fc-119">*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*</span><span class="sxs-lookup"><span data-stu-id="af2fc-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="af2fc-120">研究模式功能已添加为适用于 HoloLens 的[Windows 10 4 月2018更新](release-notes-april-2018.md)的一部分，在早期版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="af2fc-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="af2fc-121">使用情况</span><span class="sxs-lookup"><span data-stu-id="af2fc-121">Usage</span></span>

<span data-ttu-id="af2fc-122">研究模式旨在使学术和工业研究人员了解计算机视觉和机器人的字段中的新想法。</span><span class="sxs-lookup"><span data-stu-id="af2fc-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="af2fc-123">它不适合企业环境中部署的应用程序，也不能通过 Microsoft Store 或其他分发渠道提供。</span><span class="sxs-lookup"><span data-stu-id="af2fc-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="af2fc-124">此外，Microsoft 不保证在未来的硬件或操作系统更新中将支持研究模式或等效的功能。</span><span class="sxs-lookup"><span data-stu-id="af2fc-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="af2fc-125">但是，这不会阻止你使用它来开发和测试新的观点！</span><span class="sxs-lookup"><span data-stu-id="af2fc-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="af2fc-126">安全性和性能</span><span class="sxs-lookup"><span data-stu-id="af2fc-126">Security and performance</span></span>

<span data-ttu-id="af2fc-127">请注意，在正常情况下，启用研究模式比使用 HoloLens 2 时使用的电池电量更多。</span><span class="sxs-lookup"><span data-stu-id="af2fc-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="af2fc-128">即使使用调研模式功能的应用程序没有运行，也是如此。</span><span class="sxs-lookup"><span data-stu-id="af2fc-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="af2fc-129">启用此模式还可以降低设备的整体安全性，因为应用程序可能会滥用传感器数据。</span><span class="sxs-lookup"><span data-stu-id="af2fc-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="af2fc-130">您可以在[HoloLens 安全常见问题](https://docs.microsoft.com/hololens/hololens-faq-security)中找到有关设备安全的详细信息。</span><span class="sxs-lookup"><span data-stu-id="af2fc-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="af2fc-131">设备支持</span><span class="sxs-lookup"><span data-stu-id="af2fc-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="af2fc-132"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="af2fc-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="af2fc-133"><a href="hololens-hardware-details.md"><strong>HoloLens 第一代</strong></a></span><span class="sxs-lookup"><span data-stu-id="af2fc-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="af2fc-134">标题跟踪相机</span><span class="sxs-lookup"><span data-stu-id="af2fc-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="af2fc-135">✔️</span><span class="sxs-lookup"><span data-stu-id="af2fc-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="af2fc-136">IR 相机 & 深度</span><span class="sxs-lookup"><span data-stu-id="af2fc-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="af2fc-137">✔️</span><span class="sxs-lookup"><span data-stu-id="af2fc-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="af2fc-138">加速计</span><span class="sxs-lookup"><span data-stu-id="af2fc-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="af2fc-139">陀螺仪</span><span class="sxs-lookup"><span data-stu-id="af2fc-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="af2fc-140">磁力计</span><span class="sxs-lookup"><span data-stu-id="af2fc-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="af2fc-141">HoloLens 2 的研究模式支持预计在7月2020公开预览版中提供，并将包含上面列出的所有功能。</span><span class="sxs-lookup"><span data-stu-id="af2fc-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="af2fc-142">请返回获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="af2fc-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="af2fc-143">启用研究模式</span><span class="sxs-lookup"><span data-stu-id="af2fc-143">Enabling Research mode</span></span>

<span data-ttu-id="af2fc-144">研究模式是开发人员模式的扩展。</span><span class="sxs-lookup"><span data-stu-id="af2fc-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="af2fc-145">在开始之前，需要启用设备的开发人员功能才能访问 "研究模式" 设置：</span><span class="sxs-lookup"><span data-stu-id="af2fc-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="af2fc-146">打开 "**开始" 菜单 > 设置**"，然后选择"**更新**"。</span><span class="sxs-lookup"><span data-stu-id="af2fc-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="af2fc-147">**为开发人员**选择并启用**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="af2fc-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="af2fc-148">向下滚动并启用**设备门户**。</span><span class="sxs-lookup"><span data-stu-id="af2fc-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="af2fc-149">启用开发人员功能后，[连接到设备门户](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以启用研究模式功能。</span><span class="sxs-lookup"><span data-stu-id="af2fc-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="af2fc-150">在*HoloLens 第一代*：</span><span class="sxs-lookup"><span data-stu-id="af2fc-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="af2fc-151">在**设备门户**中转到 "**系统 > 研究模式**"。</span><span class="sxs-lookup"><span data-stu-id="af2fc-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="af2fc-152">选择 "**允许访问传感器流**"。</span><span class="sxs-lookup"><span data-stu-id="af2fc-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="af2fc-153">从页面顶部的**Power** menu 项重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="af2fc-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="af2fc-154">重新启动设备后，通过**设备门户**加载的应用程序可以访问研究模式流。</span><span class="sxs-lookup"><span data-stu-id="af2fc-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="af2fc-155">![HoloLens 设备门户的研究模式选项卡](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="af2fc-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="af2fc-156">*HoloLens 设备门户中的研究模式窗口*</span><span class="sxs-lookup"><span data-stu-id="af2fc-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="af2fc-157">在应用中使用传感器数据</span><span class="sxs-lookup"><span data-stu-id="af2fc-157">Using sensor data in your apps</span></span>

<span data-ttu-id="af2fc-158">*HoloLens 第一代*</span><span class="sxs-lookup"><span data-stu-id="af2fc-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="af2fc-159">应用程序可以访问传感器流数据，其方式与通过[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)访问照片和视频相机流的方式相同。</span><span class="sxs-lookup"><span data-stu-id="af2fc-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="af2fc-160">适用于 HoloLens 开发的所有 Api 在研究模式下也可用。</span><span class="sxs-lookup"><span data-stu-id="af2fc-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="af2fc-161">具体而言，应用程序在每个传感器帧捕获时间确切地了解 HoloLens 在6DoF 空间的位置。</span><span class="sxs-lookup"><span data-stu-id="af2fc-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="af2fc-162">你可以找到有关如何访问各种研究模式流的示例应用程序、如何使用[内部函数和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存储库中记录流。</span><span class="sxs-lookup"><span data-stu-id="af2fc-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="af2fc-163">此时，HoloLensForCV 示例在 HoloLens 2 上不起作用。</span><span class="sxs-lookup"><span data-stu-id="af2fc-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="af2fc-164">已知问题</span><span class="sxs-lookup"><span data-stu-id="af2fc-164">Known issues</span></span>

<span data-ttu-id="af2fc-165">你可以使用 HoloLensForCV 存储库中的[问题跟踪](https://github.com/Microsoft/HololensForCV/issues)程序来遵循已知问题。</span><span class="sxs-lookup"><span data-stu-id="af2fc-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="af2fc-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="af2fc-166">See also</span></span>

* [<span data-ttu-id="af2fc-167">Microsoft 媒体基础</span><span class="sxs-lookup"><span data-stu-id="af2fc-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="af2fc-168">HoloLensForCV GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="af2fc-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="af2fc-169">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="af2fc-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
