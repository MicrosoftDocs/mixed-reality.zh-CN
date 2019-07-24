---
title: QR 代码跟踪
description: 了解如何为 Windows Mixed Reality 沉浸式 (VR) 耳机启用 QR 码跟踪, 并在你的 VR 应用中实现该功能。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr, lbe, 基于位置的娱乐, vr 拱廊类, 拱廊类, 沉浸, qr, qr 码
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829984"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="525c9-104">QR 代码跟踪</span><span class="sxs-lookup"><span data-stu-id="525c9-104">QR code tracking</span></span>

<span data-ttu-id="525c9-105">QR 代码跟踪在用于沉浸式 (VR) 耳机的 Windows Mixed Reality 驱动程序中实现。</span><span class="sxs-lookup"><span data-stu-id="525c9-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="525c9-106">通过启用耳机驱动程序中的 QR 代码跟踪程序, 耳机会扫描 QR 码, 并报告给感兴趣的应用程序。</span><span class="sxs-lookup"><span data-stu-id="525c9-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="525c9-107">此功能仅在[Windows 10 年10月2018更新 (也称为 RS5)](release-notes-october-2018.md)中可用。</span><span class="sxs-lookup"><span data-stu-id="525c9-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="525c9-108">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT, 这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="525c9-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="525c9-109">概念对于C++/WinRT 项目是等效的, 但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="525c9-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="525c9-110">设备支持</span><span class="sxs-lookup"><span data-stu-id="525c9-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="525c9-111"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="525c9-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="525c9-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="525c9-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="525c9-113"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="525c9-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="525c9-114">QR 代码跟踪</span><span class="sxs-lookup"><span data-stu-id="525c9-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="525c9-115">❌</span><span class="sxs-lookup"><span data-stu-id="525c9-115">❌</span></span></td>
        <td><span data-ttu-id="525c9-116">✔️</span><span class="sxs-lookup"><span data-stu-id="525c9-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="525c9-117">启用和禁用耳机代码跟踪</span><span class="sxs-lookup"><span data-stu-id="525c9-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="525c9-118">注意:本部分仅适用于[Windows 10 十月2018更新 (也称为 RS5)](release-notes-october-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="525c9-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="525c9-119">从19h1 开始, 你无需执行此操作。</span><span class="sxs-lookup"><span data-stu-id="525c9-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="525c9-120">无论你是要开发将利用 QR 代码跟踪的混合现实应用, 还是你是其中一个应用的客户, 你都需要在耳机的驱动程序中手动打开 QR 代码跟踪。</span><span class="sxs-lookup"><span data-stu-id="525c9-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="525c9-121">若要为沉浸式 (VR) 耳机**启用 QR 码跟踪, 请**执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="525c9-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="525c9-122">在电脑上关闭混合现实门户应用。</span><span class="sxs-lookup"><span data-stu-id="525c9-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="525c9-123">从 PC 中拔出耳机。</span><span class="sxs-lookup"><span data-stu-id="525c9-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="525c9-124">在命令提示符下运行以下脚本:</span><span class="sxs-lookup"><span data-stu-id="525c9-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="525c9-125">将您的耳机重新连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="525c9-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="525c9-126">若要为沉浸式 (VR) 耳机**关闭 QR 码跟踪, 请**执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="525c9-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="525c9-127">在电脑上关闭混合现实门户应用。</span><span class="sxs-lookup"><span data-stu-id="525c9-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="525c9-128">从 PC 中拔出耳机。</span><span class="sxs-lookup"><span data-stu-id="525c9-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="525c9-129">在命令提示符下运行以下脚本:</span><span class="sxs-lookup"><span data-stu-id="525c9-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="525c9-130">将您的耳机重新连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="525c9-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="525c9-131">这会使发现的任何 QR 码 "不可定位"。</span><span class="sxs-lookup"><span data-stu-id="525c9-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="525c9-132">打印代码</span><span class="sxs-lookup"><span data-stu-id="525c9-132">Printing codes</span></span>

<span data-ttu-id="525c9-133">首先, [qr 码规范](https://www.qrcode.com/en/howto/code.html)显示 "qr 码符号区需要使用边距或" 安静区 "才能使用它。</span><span class="sxs-lookup"><span data-stu-id="525c9-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="525c9-134">边距是符号周围的空白区域, 不会打印任何内容。</span><span class="sxs-lookup"><span data-stu-id="525c9-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="525c9-135">QR 代码要求符号的所有边都有四个模块宽的边距。 "</span><span class="sxs-lookup"><span data-stu-id="525c9-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="525c9-136">这需要在每一端有一个模块大小的四倍的宽度-代码中的单个黑色方形。</span><span class="sxs-lookup"><span data-stu-id="525c9-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="525c9-137">"规范" 页包含有关如何打印 QR 码的建议, 以及如何确定所需的区域来确定所需的大小的 QR 码。</span><span class="sxs-lookup"><span data-stu-id="525c9-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="525c9-138">当前, QR 码检测质量容易产生不同的照明和背景。</span><span class="sxs-lookup"><span data-stu-id="525c9-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="525c9-139">要对付这一点, 请注意您的照明, 并打印相应的代码。</span><span class="sxs-lookup"><span data-stu-id="525c9-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="525c9-140">在具有特别明亮的光线的场景中, 打印灰色背景上的黑色代码。</span><span class="sxs-lookup"><span data-stu-id="525c9-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="525c9-141">在低亮度场景下, 黑色打开。</span><span class="sxs-lookup"><span data-stu-id="525c9-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="525c9-142">同样, 如果代码的背景更暗, 则如果检测频率较低, 请尝试使用黑色的灰色代码。</span><span class="sxs-lookup"><span data-stu-id="525c9-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="525c9-143">否则, 如果背景较轻, 则常规代码应正常工作。</span><span class="sxs-lookup"><span data-stu-id="525c9-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="525c9-144">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="525c9-144">QRTracking API</span></span>

<span data-ttu-id="525c9-145">QRTracking 插件为 QR 代码跟踪公开 Api。</span><span class="sxs-lookup"><span data-stu-id="525c9-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="525c9-146">若要使用插件, 你将需要使用*QRCodesTrackerPlugin*命名空间中的以下类型。</span><span class="sxs-lookup"><span data-stu-id="525c9-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="525c9-147">在 Unity 中实现 QR 代码跟踪</span><span class="sxs-lookup"><span data-stu-id="525c9-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="525c9-148">MRTK 中的示例 Unity 场景 (混合现实工具包)</span><span class="sxs-lookup"><span data-stu-id="525c9-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="525c9-149">可在混合现实工具包[GitHub 网站](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)中找到有关如何使用 QR 跟踪 API 的示例。</span><span class="sxs-lookup"><span data-stu-id="525c9-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="525c9-150">MRTK 已实现所需的脚本来 simpilify QR 跟踪使用情况。</span><span class="sxs-lookup"><span data-stu-id="525c9-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="525c9-151">开发 QR 跟踪应用程序所需的所有资产都位于 "QRTracker" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="525c9-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="525c9-152">有两种场景: 第一种是在检测到 QR 码的详细信息时, 只显示其详细信息, 第二个示例演示如何使用连接到 QR 代码的坐标系来显示全息影像。</span><span class="sxs-lookup"><span data-stu-id="525c9-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="525c9-153">有一个 prefab 的 "QRScanner", 它将所有必需的脚本添加到要使用 QRCodes 的场景中。</span><span class="sxs-lookup"><span data-stu-id="525c9-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="525c9-154">脚本 QRCodeManager 是实现 QRCode API 的单一实例类。</span><span class="sxs-lookup"><span data-stu-id="525c9-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="525c9-155">这需要添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="525c9-155">This needs to be added to your scene.</span></span> <span data-ttu-id="525c9-156">脚本 "AttachToQRCode" 用于将全息影像附加到 QR 码坐标系统, 可以将此脚本添加到任何全息影像。</span><span class="sxs-lookup"><span data-stu-id="525c9-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="525c9-157">"SpatialGraphCoordinateSystem" 显示了如何使用 QRCode 坐标系统。</span><span class="sxs-lookup"><span data-stu-id="525c9-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="525c9-158">这些脚本可以在项目场景中按原样使用, 也可以直接使用插件自行编写, 如上所述。</span><span class="sxs-lookup"><span data-stu-id="525c9-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="525c9-159">在不 MRTK 的 Unity 中实现 QR 代码跟踪</span><span class="sxs-lookup"><span data-stu-id="525c9-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="525c9-160">你还可以在 Unity 中使用 QR 跟踪 API, 而无需依赖于 MRTK。</span><span class="sxs-lookup"><span data-stu-id="525c9-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="525c9-161">若要使用该 API, 你将需要使用以下指令准备你的项目:</span><span class="sxs-lookup"><span data-stu-id="525c9-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="525c9-162">在 unity 项目的 "资产" 文件夹中创建一个名为的新文件夹:"插件"。</span><span class="sxs-lookup"><span data-stu-id="525c9-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="525c9-163">将[此文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)中的所有所需文件复制到刚创建的本地 "插件" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="525c9-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="525c9-164">你可以使用[MRTK scripts 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)中的 QR 跟踪脚本或编写你自己的脚本。</span><span class="sxs-lookup"><span data-stu-id="525c9-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="525c9-165">注意:这些插件仅适用于[Windows 10 十月2018更新 (也称为 RS5)](release-notes-october-2018.md)生成。</span><span class="sxs-lookup"><span data-stu-id="525c9-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="525c9-166">插件将在下一个 windows 版本中更新。</span><span class="sxs-lookup"><span data-stu-id="525c9-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="525c9-167">当前插件是实验性的, 不能用于将来的 windows 版本。</span><span class="sxs-lookup"><span data-stu-id="525c9-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="525c9-168">新插件将发布, 可从下一 windows 版本中使用, 并且不会向后兼容, 并且不会与 RS5 配合使用)。</span><span class="sxs-lookup"><span data-stu-id="525c9-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="525c9-169">在 DirectX 中实现 QR 代码跟踪</span><span class="sxs-lookup"><span data-stu-id="525c9-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="525c9-170">若要在 Visual Studio 中使用 QRTrackingPlugin, 需要将 QRTrackingPlugin 的引用添加到 winmd。</span><span class="sxs-lookup"><span data-stu-id="525c9-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="525c9-171">可在此处找到[受支持的平台所需的文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)。</span><span class="sxs-lookup"><span data-stu-id="525c9-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="525c9-172">获取坐标系统</span><span class="sxs-lookup"><span data-stu-id="525c9-172">Getting a coordinate system</span></span>

<span data-ttu-id="525c9-173">我们定义一个右侧坐标系统, 它与左上角快速检测方块左上角的 QR 码对齐。</span><span class="sxs-lookup"><span data-stu-id="525c9-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="525c9-174">坐标系统如下所示。</span><span class="sxs-lookup"><span data-stu-id="525c9-174">The coordinate system is shown below.</span></span> <span data-ttu-id="525c9-175">Z 轴指向纸张 (未显示), 但在 Unity 中, z 轴不在纸张上并左手。</span><span class="sxs-lookup"><span data-stu-id="525c9-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="525c9-176">定义的 SpatialCoordinateSystem 如下所示。</span><span class="sxs-lookup"><span data-stu-id="525c9-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="525c9-177">可使用 API Windows 从平台获取此坐标系统: *:P erception:: 空间::P 查看:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*。</span><span class="sxs-lookup"><span data-stu-id="525c9-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR 码坐标系统](images/Qr-coordinatesystem.png) 

<span data-ttu-id="525c9-179">从 QRCode ^ Code 对象开始, 下面的代码演示如何创建一个矩形, 并将其放入 QR 坐标系统:</span><span class="sxs-lookup"><span data-stu-id="525c9-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="525c9-180">可以使用物理尺寸来创建 QR 矩形:</span><span class="sxs-lookup"><span data-stu-id="525c9-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="525c9-181">坐标系统可用于绘制 QR 码, 或将全息影像附加到该位置:</span><span class="sxs-lookup"><span data-stu-id="525c9-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="525c9-182">完全一样, *QRCodesTrackerPlugin:: QRCodeAddedHandler*的外观可能如下所示:</span><span class="sxs-lookup"><span data-stu-id="525c9-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="525c9-183">故障排除和常见问题</span><span class="sxs-lookup"><span data-stu-id="525c9-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="525c9-184">**常规故障排除**</span><span class="sxs-lookup"><span data-stu-id="525c9-184">**General troubleshooting**</span></span>

* <span data-ttu-id="525c9-185">你的电脑是否在运行 Windows 10 十月2018更新？</span><span class="sxs-lookup"><span data-stu-id="525c9-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="525c9-186">是否设置了注册表项？</span><span class="sxs-lookup"><span data-stu-id="525c9-186">Have you set the reg key?</span></span> <span data-ttu-id="525c9-187">之后重新启动了设备？</span><span class="sxs-lookup"><span data-stu-id="525c9-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="525c9-188">QR 代码版本是否是受支持的版本？</span><span class="sxs-lookup"><span data-stu-id="525c9-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="525c9-189">当前 API 最多支持 QR 代码版本20。</span><span class="sxs-lookup"><span data-stu-id="525c9-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="525c9-190">建议使用版本5进行一般使用。</span><span class="sxs-lookup"><span data-stu-id="525c9-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="525c9-191">您是否接近 QR 码？</span><span class="sxs-lookup"><span data-stu-id="525c9-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="525c9-192">照相机的位置越接近于 QR 码, API 可以支持的 QR 码版本就越高。</span><span class="sxs-lookup"><span data-stu-id="525c9-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="525c9-193">**我需要关闭 QR 码才能对其进行检测？**</span><span class="sxs-lookup"><span data-stu-id="525c9-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="525c9-194">这将取决于 QR 码的大小以及它的版本。</span><span class="sxs-lookup"><span data-stu-id="525c9-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="525c9-195">对于版本 1 QR 码, 从 5 cm 端到 25 cm 方, 最小检测距离范围为0.15 米到0.5 米。</span><span class="sxs-lookup"><span data-stu-id="525c9-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="525c9-196">从大约0.3 米开始, 可以检测到的最远的 QR 码目标为更大的 QR 码1.4 目标。</span><span class="sxs-lookup"><span data-stu-id="525c9-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="525c9-197">对于大于此值的 QR 码, 可以估算;大小的检测距离线性增加。</span><span class="sxs-lookup"><span data-stu-id="525c9-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="525c9-198">跟踪器不能使用边缘小于 5 cm 的 QR 码。</span><span class="sxs-lookup"><span data-stu-id="525c9-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="525c9-199">**带有徽标的 QR 码是否起作用？**</span><span class="sxs-lookup"><span data-stu-id="525c9-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="525c9-200">带有徽标的 QR 码尚未经过测试, 当前不受支持。</span><span class="sxs-lookup"><span data-stu-id="525c9-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="525c9-201">**如何实现清除应用程序中的 QR 码, 因此它们不会保留？**</span><span class="sxs-lookup"><span data-stu-id="525c9-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="525c9-202">QR 码仅保留在启动会话中。</span><span class="sxs-lookup"><span data-stu-id="525c9-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="525c9-203">重新启动 (或重新启动驱动程序) 后, 它们将不再被检测为新对象。</span><span class="sxs-lookup"><span data-stu-id="525c9-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="525c9-204">QR 代码历史记录保存在驱动程序会话的系统级别, 但您可以将应用程序配置为忽略特定时间戳之前的 QR 码 (如果需要)。</span><span class="sxs-lookup"><span data-stu-id="525c9-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="525c9-205">目前, API 支持清除 QR 码历史记录, 因为多个应用可能对数据感兴趣。</span><span class="sxs-lookup"><span data-stu-id="525c9-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="525c9-206">**RS5 和未来版本的插件不兼容**RS5 版本的插件仅适用于 RS5, 不适用于将来的版本。</span><span class="sxs-lookup"><span data-stu-id="525c9-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="525c9-207">Expermental 插件将替换为实际插件, 并且应该是我们可以在未来版本的 windows 中使用的插件。</span><span class="sxs-lookup"><span data-stu-id="525c9-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
