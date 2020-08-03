---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流（深度、环境跟踪和反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens，HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507691"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="c7cae-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="c7cae-104">HoloLens Research Mode</span></span>

<span data-ttu-id="c7cae-105">第一代 HoloLens 中引入了研究模式，可用于访问设备上的关键传感器，尤其适用于不适用于部署的研究应用程序。</span><span class="sxs-lookup"><span data-stu-id="c7cae-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="c7cae-106">HoloLens 2 的研究模式保留了 HoloLens 1 的功能，并添加了对其他流的访问权限：</span><span class="sxs-lookup"><span data-stu-id="c7cae-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="c7cae-107">**可见的轻型环境跟踪相机**-系统用于 head 跟踪和地图构建的灰色缩放相机。</span><span class="sxs-lookup"><span data-stu-id="c7cae-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="c7cae-108">**深度相机**–在两种模式下运行：</span><span class="sxs-lookup"><span data-stu-id="c7cae-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="c7cae-109">AHAT，用于手动跟踪的高频感应（45 FPS）。</span><span class="sxs-lookup"><span data-stu-id="c7cae-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="c7cae-110">不同于第一个版本的短整型模式，AHAT 提供了超出1米的相位覆盖的伪深度。</span><span class="sxs-lookup"><span data-stu-id="c7cae-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="c7cae-111">长整型抛出，[空间映射](spatial-mapping.md)使用的最深层度（1-5 FPS）</span><span class="sxs-lookup"><span data-stu-id="c7cae-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="c7cae-112">**反射率的两个版本**： HoloLens 用于计算深度。</span><span class="sxs-lookup"><span data-stu-id="c7cae-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="c7cae-113">这些图像通过红外，并不受环境可见光的影响。</span><span class="sxs-lookup"><span data-stu-id="c7cae-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="c7cae-114">如果使用的是 HoloLens 2，还可以访问下面的其他输入：</span><span class="sxs-lookup"><span data-stu-id="c7cae-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="c7cae-115">**加速感应**程序–由系统用来确定沿 X、Y 和 Z 轴和重心的线性加速度。</span><span class="sxs-lookup"><span data-stu-id="c7cae-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="c7cae-116">**Gyro** –系统用来确定旋转。</span><span class="sxs-lookup"><span data-stu-id="c7cae-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="c7cae-117">**磁力仪**–系统用于估计绝对方向。</span><span class="sxs-lookup"><span data-stu-id="c7cae-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7cae-118">研究模式目前为公共预览版。</span><span class="sxs-lookup"><span data-stu-id="c7cae-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="c7cae-119">HoloLens 2 示例、教程和完整 API 文档将在[ECCV 2020](https://eccv2020.eu/
 )的 "调查模式" Git 存储库中提供。</span><span class="sxs-lookup"><span data-stu-id="c7cae-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="c7cae-120">![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7cae-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="c7cae-121">*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*</span><span class="sxs-lookup"><span data-stu-id="c7cae-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="c7cae-122">使用情况</span><span class="sxs-lookup"><span data-stu-id="c7cae-122">Usage</span></span>

<span data-ttu-id="c7cae-123">研究模式旨在使学术和工业研究人员了解计算机视觉和机器人的字段中的新想法。</span><span class="sxs-lookup"><span data-stu-id="c7cae-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="c7cae-124">它不适合企业环境中部署的应用程序，也不能通过 Microsoft Store 或其他分发渠道提供。</span><span class="sxs-lookup"><span data-stu-id="c7cae-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="c7cae-125">此外，Microsoft 不保证在未来的硬件或操作系统更新中将支持研究模式或等效的功能。</span><span class="sxs-lookup"><span data-stu-id="c7cae-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="c7cae-126">但是，这不会阻止你使用它来开发和测试新的观点！</span><span class="sxs-lookup"><span data-stu-id="c7cae-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="c7cae-127">安全性和性能</span><span class="sxs-lookup"><span data-stu-id="c7cae-127">Security and performance</span></span>

<span data-ttu-id="c7cae-128">请注意，在正常情况下，启用研究模式比使用 HoloLens 2 时使用的电池电量更多。</span><span class="sxs-lookup"><span data-stu-id="c7cae-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="c7cae-129">即使使用调研模式功能的应用程序没有运行，也是如此。</span><span class="sxs-lookup"><span data-stu-id="c7cae-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="c7cae-130">启用此模式还可以降低设备的整体安全性，因为应用程序可能会滥用传感器数据。</span><span class="sxs-lookup"><span data-stu-id="c7cae-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="c7cae-131">您可以在[HoloLens 安全常见问题](https://docs.microsoft.com/hololens/hololens-faq-security)中找到有关设备安全的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c7cae-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="c7cae-132">设备支持</span><span class="sxs-lookup"><span data-stu-id="c7cae-132">Device support</span></span>
<table><span data-ttu-id="c7cae-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="c7cae-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="c7cae-134"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="c7cae-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c7cae-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 代</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7cae-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="c7cae-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="c7cae-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c7cae-137">标题跟踪相机</span><span class="sxs-lookup"><span data-stu-id="c7cae-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="c7cae-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-138">✔️</span></span></td>
        <td><span data-ttu-id="c7cae-139">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7cae-140">IR 相机 & 深度</span><span class="sxs-lookup"><span data-stu-id="c7cae-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="c7cae-141">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-141">✔️</span></span></td>
        <td><span data-ttu-id="c7cae-142">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7cae-143">加速计</span><span class="sxs-lookup"><span data-stu-id="c7cae-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c7cae-144">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7cae-145">陀螺仪</span><span class="sxs-lookup"><span data-stu-id="c7cae-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c7cae-146">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="c7cae-147">磁力计</span><span class="sxs-lookup"><span data-stu-id="c7cae-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c7cae-148">✔️</span><span class="sxs-lookup"><span data-stu-id="c7cae-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="c7cae-149">启用研究模式（HoloLens 第一代和 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="c7cae-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="c7cae-150">研究模式是开发人员模式的扩展。</span><span class="sxs-lookup"><span data-stu-id="c7cae-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="c7cae-151">在开始之前，需要启用设备的开发人员功能才能访问 "研究模式" 设置：</span><span class="sxs-lookup"><span data-stu-id="c7cae-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="c7cae-152">打开 "**开始" 菜单 > 设置**"，然后选择"**更新**"。</span><span class="sxs-lookup"><span data-stu-id="c7cae-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="c7cae-153">**为开发人员**选择并启用**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="c7cae-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="c7cae-154">**向下滚动**并启用“设备门户”。</span><span class="sxs-lookup"><span data-stu-id="c7cae-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="c7cae-155">启用开发人员功能后，[连接到设备门户](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以启用研究模式功能：</span><span class="sxs-lookup"><span data-stu-id="c7cae-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="c7cae-156">在**设备门户**中转到 "**系统 > 研究模式**"。</span><span class="sxs-lookup"><span data-stu-id="c7cae-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="c7cae-157">选择 "**允许访问传感器流**"。</span><span class="sxs-lookup"><span data-stu-id="c7cae-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="c7cae-158">从页面顶部的**Power** menu 项重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="c7cae-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="c7cae-159">重新启动设备后，通过**设备门户**加载的应用程序可以访问研究模式流。</span><span class="sxs-lookup"><span data-stu-id="c7cae-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="c7cae-160">![HoloLens 设备门户的研究模式选项卡](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="c7cae-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="c7cae-161">*HoloLens 设备门户中的研究模式窗口*</span><span class="sxs-lookup"><span data-stu-id="c7cae-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7cae-162">HoloLens 2 的研究模式从版本19041.1356 开始提供。</span><span class="sxs-lookup"><span data-stu-id="c7cae-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="c7cae-163">如果在早期版本中需要访问权限，请注册我们的预览[体验](https://docs.microsoft.com/hololens/hololens-insider)计划。</span><span class="sxs-lookup"><span data-stu-id="c7cae-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="c7cae-164">在应用中使用传感器数据</span><span class="sxs-lookup"><span data-stu-id="c7cae-164">Using sensor data in your apps</span></span>

<span data-ttu-id="c7cae-165">应用程序可以访问传感器流数据，其方式与通过[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)访问照片和视频相机流的方式相同。</span><span class="sxs-lookup"><span data-stu-id="c7cae-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="c7cae-166">适用于 HoloLens 开发的所有 Api 在研究模式下也可用。</span><span class="sxs-lookup"><span data-stu-id="c7cae-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="c7cae-167">具体而言，应用程序在每个传感器帧捕获时间确切地了解 HoloLens 在6DoF 空间的位置。</span><span class="sxs-lookup"><span data-stu-id="c7cae-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="c7cae-168">你可以找到有关如何访问各种研究模式流的示例应用程序、如何使用[内部函数和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存储库中记录流。</span><span class="sxs-lookup"><span data-stu-id="c7cae-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="c7cae-169">此时，HoloLensForCV 示例在 HoloLens 2 上不起作用。</span><span class="sxs-lookup"><span data-stu-id="c7cae-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="c7cae-170">支持</span><span class="sxs-lookup"><span data-stu-id="c7cae-170">Support</span></span>

<span data-ttu-id="c7cae-171">请使用 HoloLensForCV 存储库中的[问题跟踪](https://github.com/Microsoft/HololensForCV/issues)程序发布反馈并跟踪已知问题。</span><span class="sxs-lookup"><span data-stu-id="c7cae-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7cae-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7cae-172">See also</span></span>

* [<span data-ttu-id="c7cae-173">Microsoft 媒体基础</span><span class="sxs-lookup"><span data-stu-id="c7cae-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="c7cae-174">HoloLensForCV GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="c7cae-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="c7cae-175">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="c7cae-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
