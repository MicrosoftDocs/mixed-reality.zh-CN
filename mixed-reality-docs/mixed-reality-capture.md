---
title: 混合现实捕获
description: 使用混合的现实捕获的信息。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc，混合现实捕获、 照片、 视频、 照相机、 捕获、 使用情况、 流、 流媒体直播、 演示
ms.openlocfilehash: 18a80083bd25974905874c6c2ec0de87dc7424ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592871"
---
# <a name="mixed-reality-capture"></a><span data-ttu-id="cafe3-104">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="cafe3-104">Mixed reality capture</span></span>

<span data-ttu-id="cafe3-105">HoloLens 为用户提供了混合现实世界与数字世界的体验。</span><span class="sxs-lookup"><span data-stu-id="cafe3-105">HoloLens gives users the experience of mixing the real world with the digital world.</span></span> <span data-ttu-id="cafe3-106">混合的现实捕获 (MRC) 允许您为照片或视频捕获这种体验。</span><span class="sxs-lookup"><span data-stu-id="cafe3-106">Mixed reality capture (MRC) let you capture that experience as either a photograph or a video.</span></span> <span data-ttu-id="cafe3-107">这样可以允许用户以查看全息，正如您看到它们，从而与他人共享体验。</span><span class="sxs-lookup"><span data-stu-id="cafe3-107">This lets you share the experience with others by allowing them to see the holograms as you see them.</span></span> <span data-ttu-id="cafe3-108">此类视频和照片是从第一人称角度。</span><span class="sxs-lookup"><span data-stu-id="cafe3-108">Such videos and photos are from a first-person point of view.</span></span> <span data-ttu-id="cafe3-109">对于第三个人的角度来看，使用[spectator 视图](spectator-view.md)。</span><span class="sxs-lookup"><span data-stu-id="cafe3-109">For a third-person point of view, use [spectator view](spectator-view.md).</span></span>

<span data-ttu-id="cafe3-110">共享社交圈之间的视频超出了混合的现实捕获的用例。</span><span class="sxs-lookup"><span data-stu-id="cafe3-110">Use cases for mixed reality capture go beyond sharing videos amongst a social circle.</span></span> <span data-ttu-id="cafe3-111">可以使用视频，以指示其他人如何使用应用程序。</span><span class="sxs-lookup"><span data-stu-id="cafe3-111">Videos can be used to instruct others on how to use an app.</span></span> <span data-ttu-id="cafe3-112">开发人员可以使用视频或静止图像来改进重现步骤和调试应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="cafe3-112">Developers can use videos or stills to improve repro steps and debug app experiences.</span></span>

## <a name="live-streaming-from-hololens"></a><span data-ttu-id="cafe3-113">实时传送视频流从 HoloLens</span><span class="sxs-lookup"><span data-stu-id="cafe3-113">Live streaming from HoloLens</span></span>

<span data-ttu-id="cafe3-114">[Windows 10 2018 年 10 月更新](release-notes-october-2018.md)将 Miracast 支持添加到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="cafe3-114">The [Windows 10 October 2018 Update](release-notes-october-2018.md) adds Miracast support to HoloLens.</span></span> <span data-ttu-id="cafe3-115">选择**Connect**开始菜单以显示为已启用 Miracast 的设备和适配器的选取器底部的按钮。</span><span class="sxs-lookup"><span data-stu-id="cafe3-115">Select the **Connect** button at the bottom of the Start menu to bring up a picker for Miracast-enabled devices and adapters.</span></span> <span data-ttu-id="cafe3-116">选择你想要开始流式处理的设备。</span><span class="sxs-lookup"><span data-stu-id="cafe3-116">Select the device to which you want to begin streaming.</span></span> <span data-ttu-id="cafe3-117">完成后，选择**断开连接**底部的开始菜单的按钮。</span><span class="sxs-lookup"><span data-stu-id="cafe3-117">When done, select the **Disconnect** button at the bottom of the Start menu.</span></span>  <span data-ttu-id="cafe3-118">**连接**并**断开连接**快速操作菜单上也有提供。</span><span class="sxs-lookup"><span data-stu-id="cafe3-118">**Connect** and **Disconnect** are also available on the quick actions menu.</span></span> 

<span data-ttu-id="cafe3-119">[Windows Device Portal](using-the-windows-device-portal.md)公开实时流式处理选项的开发人员模式下的设备。</span><span class="sxs-lookup"><span data-stu-id="cafe3-119">The [Windows Device Portal](using-the-windows-device-portal.md) exposes live streaming options for devices that are in Developer mode.</span></span>

## <a name="taking-mixed-reality-captures"></a><span data-ttu-id="cafe3-120">采用混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="cafe3-120">Taking mixed reality captures</span></span>

<span data-ttu-id="cafe3-121">![单击底部的开始菜单的摄像机图标](images/cameraiconinpins-300px.png)</span><span class="sxs-lookup"><span data-stu-id="cafe3-121">![Click the camera icon at the bottom of the Start menu](images/cameraiconinpins-300px.png)</span></span><br>
<span data-ttu-id="cafe3-122">*单击底部的开始菜单的摄像机图标*</span><span class="sxs-lookup"><span data-stu-id="cafe3-122">*Click the camera icon at the bottom of the Start menu*</span></span>

<span data-ttu-id="cafe3-123">有多种方法来启动混合的现实捕获：</span><span class="sxs-lookup"><span data-stu-id="cafe3-123">There are multiple ways to initiate a mixed reality capture:</span></span>
* <span data-ttu-id="cafe3-124">Cortana 可以使用在所有时间不考虑当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="cafe3-124">Cortana can be used at all times regardless of the app currently running.</span></span> <span data-ttu-id="cafe3-125">只需输入:"你好，小娜，拍摄一张照片"或"你好，小娜，开始记录。"</span><span class="sxs-lookup"><span data-stu-id="cafe3-125">Just say, "Hey Cortana, take a picture" or "Hey Cortana, start recording."</span></span> <span data-ttu-id="cafe3-126">若要停止视频，请说"你好，小娜停止录制。"</span><span class="sxs-lookup"><span data-stu-id="cafe3-126">To stop a video, say "Hey Cortana, stop recording."</span></span>
* <span data-ttu-id="cafe3-127">在开始菜单上选择任一**照相机**或**视频**。</span><span class="sxs-lookup"><span data-stu-id="cafe3-127">On the Start menu, select either **Camera** or **Video**.</span></span> <span data-ttu-id="cafe3-128">使用[敲击](gestures.md#air-tap)以打开内置 MRC 相机 UI。</span><span class="sxs-lookup"><span data-stu-id="cafe3-128">Use [air-tap](gestures.md#air-tap) to open the built-in MRC camera UI.</span></span>
* <span data-ttu-id="cafe3-129">在快速操作菜单上选择任一**照相机**或**视频**以打开内置 MRC 相机 UI。</span><span class="sxs-lookup"><span data-stu-id="cafe3-129">On the quick actions menu, select either **Camera** or **Video** to open the built-in MRC camera UI.</span></span>
* <span data-ttu-id="cafe3-130">应用程序均可公开使用自定义的混合的现实捕获，或在其自己的 UI [Windows 10 2018 年 10 月更新](release-notes-october-2018.md)，[内置 MRC 摄像头 UI](mixed-reality-capture-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="cafe3-130">Apps are able to expose their own UI for mixed reality capture using custom or, as of the [Windows 10 October 2018 Update](release-notes-october-2018.md), [built-in MRC camera UI](mixed-reality-capture-for-developers.md).</span></span>
* <span data-ttu-id="cafe3-131">唯一的 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="cafe3-131">Unique to HoloLens:</span></span> 
    * <span data-ttu-id="cafe3-132">[Windows Device Portal](using-the-windows-device-portal.md)具有一个混合的现实捕获页面，可用来拍摄照片、 视频、 实时流，并查看捕获。</span><span class="sxs-lookup"><span data-stu-id="cafe3-132">[Windows Device Portal](using-the-windows-device-portal.md) has a mixed reality capture page that can be used to take photos, videos, live stream, and view captures.</span></span>
    * <span data-ttu-id="cafe3-133">按这两**调高音量**并**调低音量**按钮同时以拍摄照片，不考虑当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="cafe3-133">Press both the **volume up** and **volume down** buttons simultaneously to take a picture, regardless of the app currently running.</span></span>
    * <span data-ttu-id="cafe3-134">保存**调高音量**并**调低音量**三秒，若要开始录制视频的按钮。</span><span class="sxs-lookup"><span data-stu-id="cafe3-134">Hold the **volume up** and **volume down** buttons for three seconds to start recording a video.</span></span> <span data-ttu-id="cafe3-135">若要停止视频，请点击两者**调高音量**并**调低音量**同时按钮。</span><span class="sxs-lookup"><span data-stu-id="cafe3-135">To stop a video, tap both **volume up** and **volume down** buttons simultaneously.</span></span>
* <span data-ttu-id="cafe3-136">唯一的沉浸式耳机：</span><span class="sxs-lookup"><span data-stu-id="cafe3-136">Unique to immersive headsets:</span></span> 
    * <span data-ttu-id="cafe3-137">使用 motion 控制器，存放**Windows**按钮，然后点击**触发器**来拍摄照片。</span><span class="sxs-lookup"><span data-stu-id="cafe3-137">Using a motion controller, hold the **Windows** button and then tap the **trigger** to take a picture.</span></span> 
    * <span data-ttu-id="cafe3-138">使用 motion 控制器，存放**Windows**按钮，然后点击**菜单**按钮开始录制视频。</span><span class="sxs-lookup"><span data-stu-id="cafe3-138">Using a motion controller, hold the **Windows** button and then tap the **menu** button to start recording video.</span></span> <span data-ttu-id="cafe3-139">保存**Windows**按钮，然后点击**触发器**到停止录制视频。</span><span class="sxs-lookup"><span data-stu-id="cafe3-139">Hold the **Windows** button and then tap the **trigger** to stop recording video.</span></span>
    
>[!NOTE]
><span data-ttu-id="cafe3-140">[Windows 10 2018 年 10 月更新](release-notes-october-2018.md)更改布隆和 Windows 按钮的行为方式。</span><span class="sxs-lookup"><span data-stu-id="cafe3-140">The [Windows 10 October 2018 Update](release-notes-october-2018.md) changes how bloom and Windows button behave.</span></span> <span data-ttu-id="cafe3-141">在更新前布隆手势或 Windows 按钮会停止记录。</span><span class="sxs-lookup"><span data-stu-id="cafe3-141">Before the update, the bloom gesture or Windows button would stop recording.</span></span> <span data-ttu-id="cafe3-142">更新后，布隆手势或 Windows 按钮打开开始菜单 （或快速操作菜单上你是否在应用中）。</span><span class="sxs-lookup"><span data-stu-id="cafe3-142">After the update, the bloom gesture or the Windows button opens the Start menu (or the quick actions menu if you are in an app).</span></span> <span data-ttu-id="cafe3-143">在菜单中，选择**停止视频**停止录制。</span><span class="sxs-lookup"><span data-stu-id="cafe3-143">In the menu, select **Stop video** to stop recording.</span></span>

### <a name="limitations-of-mixed-reality-capture"></a><span data-ttu-id="cafe3-144">混合的现实捕获的限制</span><span class="sxs-lookup"><span data-stu-id="cafe3-144">Limitations of mixed reality capture</span></span>

<span data-ttu-id="cafe3-145">上 HoloLens，系统将限制为 30 Hz 的呈现速率。</span><span class="sxs-lookup"><span data-stu-id="cafe3-145">On HoloLens, the system will throttle the render rate to 30Hz.</span></span> <span data-ttu-id="cafe3-146">这将创建一些空间用于 MRC 运行，因此应用程序不需要保留的常量预算保留，并还与帧速率每秒 30 帧 MRC 视频记录为相匹配。</span><span class="sxs-lookup"><span data-stu-id="cafe3-146">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve, and also matches the MRC video record framerate of 30fps.</span></span>

<span data-ttu-id="cafe3-147">视频的最大长度为五分钟。</span><span class="sxs-lookup"><span data-stu-id="cafe3-147">Videos have a maximum length of five minutes.</span></span>

<span data-ttu-id="cafe3-148">内置 MRC 摄像头 UI 仅支持单个 MRC 操作一次 （拍摄照片是从录制视频互相排斥）。</span><span class="sxs-lookup"><span data-stu-id="cafe3-148">The built-in MRC camera UI only supports a single MRC operation at a time (taking a picture is mutually exclusive from recording a video).</span></span>

### <a name="file-formats"></a><span data-ttu-id="cafe3-149">文件格式</span><span class="sxs-lookup"><span data-stu-id="cafe3-149">File formats</span></span>

<span data-ttu-id="cafe3-150">混合的现实捕获从 Cortana 语音命令和开始菜单工具创建的文件采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="cafe3-150">Mixed reality captures from Cortana voice commands and Start Menu tools create files in the following formats:</span></span>

|  <span data-ttu-id="cafe3-151">在任务栏的搜索框中键入</span><span class="sxs-lookup"><span data-stu-id="cafe3-151">Type</span></span>  |  <span data-ttu-id="cafe3-152">格式</span><span class="sxs-lookup"><span data-stu-id="cafe3-152">Format</span></span>  |  <span data-ttu-id="cafe3-153">扩展</span><span class="sxs-lookup"><span data-stu-id="cafe3-153">Extension</span></span>  |  <span data-ttu-id="cafe3-154">分辨率</span><span class="sxs-lookup"><span data-stu-id="cafe3-154">Resolution</span></span>  |  <span data-ttu-id="cafe3-155">Audio</span><span class="sxs-lookup"><span data-stu-id="cafe3-155">Audio</span></span> | 
|----------|----------|----------|----------|----------|
|  <span data-ttu-id="cafe3-156">Photo</span><span class="sxs-lookup"><span data-stu-id="cafe3-156">Photo</span></span>  |  [<span data-ttu-id="cafe3-157">JPEG</span><span class="sxs-lookup"><span data-stu-id="cafe3-157">JPEG</span></span>](https://en.wikipedia.org/wiki/JPEG)  |  <span data-ttu-id="cafe3-158">.jpg</span><span class="sxs-lookup"><span data-stu-id="cafe3-158">.jpg</span></span>  |  <span data-ttu-id="cafe3-159">1408x792px (HoloLens) 1920x1080px<br> （沉浸式耳机）</span><span class="sxs-lookup"><span data-stu-id="cafe3-159">1408x792px (HoloLens) 1920x1080px (Immersive headsets)</span></span> |  <span data-ttu-id="cafe3-160">不可用</span><span class="sxs-lookup"><span data-stu-id="cafe3-160">N/A</span></span> | 
|  <span data-ttu-id="cafe3-161">视频</span><span class="sxs-lookup"><span data-stu-id="cafe3-161">Video</span></span>  |  [<span data-ttu-id="cafe3-162">MPEG 4</span><span class="sxs-lookup"><span data-stu-id="cafe3-162">MPEG-4</span></span>](https://en.wikipedia.org/wiki/MPEG-4)  |  <span data-ttu-id="cafe3-163">.mp4</span><span class="sxs-lookup"><span data-stu-id="cafe3-163">.mp4</span></span>  |  <span data-ttu-id="cafe3-164">1408x792px (HoloLens) 1632x918px （沉浸式耳机）</span><span class="sxs-lookup"><span data-stu-id="cafe3-164">1408x792px (HoloLens) 1632x918px (Immersive headsets)</span></span> |  <span data-ttu-id="cafe3-165">48khz 立体声</span><span class="sxs-lookup"><span data-stu-id="cafe3-165">48kHz Stereo</span></span> | 

## <a name="viewing-mixed-reality-captures"></a><span data-ttu-id="cafe3-166">查看混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="cafe3-166">Viewing mixed reality captures</span></span>

<span data-ttu-id="cafe3-167">混合的现实捕获照片和视频保存到设备的"本机照片"文件夹中。</span><span class="sxs-lookup"><span data-stu-id="cafe3-167">Mixed reality capture photos and videos are saved to the device's "Camera roll" folder.</span></span> <span data-ttu-id="cafe3-168">可通过访问它们[照片应用](see-your-photos.md#photos-app)或文件资源管理器。</span><span class="sxs-lookup"><span data-stu-id="cafe3-168">These can be accessed via the [Photos app](see-your-photos.md#photos-app) or File Explorer.</span></span>

<span data-ttu-id="cafe3-169">连接到 HoloLens pc，您还可以使用[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)或你的电脑的文件资源管理器 ([通过 MTP](release-notes-april-2018.md#new-features-for-hololens))。</span><span class="sxs-lookup"><span data-stu-id="cafe3-169">On a PC connected to HoloLens, you can also use [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture) or your PC's File Explorer ([via MTP](release-notes-april-2018.md#new-features-for-hololens)).</span></span>

<span data-ttu-id="cafe3-170">如果您在安装[OneDrive 应用](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)，可开启**照相机上传**和 MRC 照片和视频将同步到 OneDrive 和其他设备使用 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="cafe3-170">If you install the [OneDrive app](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), you can turn on **Camera upload,** and your MRC photos and videos will sync to OneDrive and your other devices using OneDrive.</span></span>

>[!NOTE]
><span data-ttu-id="cafe3-171">截至 Windows 10 2018 年 4 月更新，照片应用将无法再上传照片和视频到 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="cafe3-171">As of the Windows 10 April 2018 Update, the Photos app will no longer upload your photos and videos to OneDrive.</span></span>

## <a name="see-also"></a><span data-ttu-id="cafe3-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="cafe3-172">See also</span></span>
* [<span data-ttu-id="cafe3-173">Spectator 视图</span><span class="sxs-lookup"><span data-stu-id="cafe3-173">Spectator view</span></span>](spectator-view.md)
* [<span data-ttu-id="cafe3-174">可定位照相机</span><span class="sxs-lookup"><span data-stu-id="cafe3-174">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="cafe3-175">面向开发人员混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="cafe3-175">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="cafe3-176">请参阅您的照片</span><span class="sxs-lookup"><span data-stu-id="cafe3-176">See your photos</span></span>](see-your-photos.md)
* [<span data-ttu-id="cafe3-177">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="cafe3-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
