---
title: Unity 中的定位照相机
description: 在 Unity 中使用 HoloLens 定位相机。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 照片、视频、hololens、照相机、unity、定位
ms.openlocfilehash: b4a1a7e11a7606dab76b954c8d58a335d6bae0ab
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597610"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="31f4b-104">Unity 中的定位照相机</span><span class="sxs-lookup"><span data-stu-id="31f4b-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="31f4b-105">启用相片视频相机功能</span><span class="sxs-lookup"><span data-stu-id="31f4b-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="31f4b-106">必须为应用声明 "网络摄像机" 功能，才能使用[相机](locatable-camera.md)。</span><span class="sxs-lookup"><span data-stu-id="31f4b-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="31f4b-107">在 Unity 编辑器中，导航到 "编辑 > 项目设置 > Player" 页，转到 "播放机" 设置。</span><span class="sxs-lookup"><span data-stu-id="31f4b-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="31f4b-108">单击 "Windows 应用商店" 选项卡</span><span class="sxs-lookup"><span data-stu-id="31f4b-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="31f4b-109">在 "发布设置 > 功能" 部分中，检查**网络摄像机**和**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="31f4b-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="31f4b-110">照相机一次只能出现一次操作。</span><span class="sxs-lookup"><span data-stu-id="31f4b-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="31f4b-111">若要确定照相机当前在哪个模式（照片、视频或无），可以检查 UnityEngine. XR。</span><span class="sxs-lookup"><span data-stu-id="31f4b-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="31f4b-112">照片捕获</span><span class="sxs-lookup"><span data-stu-id="31f4b-112">Photo Capture</span></span>

<span data-ttu-id="31f4b-113">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="31f4b-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="31f4b-114">**类型：** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="31f4b-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="31f4b-115">*PhotoCapture*类型允许你使用照片摄像机拍摄照片。</span><span class="sxs-lookup"><span data-stu-id="31f4b-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="31f4b-116">使用*PhotoCapture*拍摄照片的一般模式如下所示：</span><span class="sxs-lookup"><span data-stu-id="31f4b-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="31f4b-117">创建*PhotoCapture*对象</span><span class="sxs-lookup"><span data-stu-id="31f4b-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="31f4b-118">使用所需的设置创建*CameraParameters*对象</span><span class="sxs-lookup"><span data-stu-id="31f4b-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="31f4b-119">通过*StartPhotoModeAsync*启动照片模式</span><span class="sxs-lookup"><span data-stu-id="31f4b-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="31f4b-120">拍摄所需照片</span><span class="sxs-lookup"><span data-stu-id="31f4b-120">Take the desired photo</span></span>
    * <span data-ttu-id="31f4b-121">可有可无与该图片交互</span><span class="sxs-lookup"><span data-stu-id="31f4b-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="31f4b-122">停止照片模式并清理资源</span><span class="sxs-lookup"><span data-stu-id="31f4b-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="31f4b-123">通用设置 PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="31f4b-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="31f4b-124">对于所有三个用途，请从上述前3个步骤开始</span><span class="sxs-lookup"><span data-stu-id="31f4b-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="31f4b-125">首先创建*PhotoCapture*对象</span><span class="sxs-lookup"><span data-stu-id="31f4b-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="31f4b-126">接下来，存储对象、设置参数和启动照片模式</span><span class="sxs-lookup"><span data-stu-id="31f4b-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="31f4b-127">最后，你还将使用此处提供的相同清理代码</span><span class="sxs-lookup"><span data-stu-id="31f4b-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="31f4b-128">完成这些步骤后，你可以选择要捕获哪种类型的照片。</span><span class="sxs-lookup"><span data-stu-id="31f4b-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="31f4b-129">将照片捕获到文件</span><span class="sxs-lookup"><span data-stu-id="31f4b-129">Capture a Photo to a File</span></span>

<span data-ttu-id="31f4b-130">最简单的操作是将照片直接捕获到文件中。</span><span class="sxs-lookup"><span data-stu-id="31f4b-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="31f4b-131">照片可以保存为 JPG 或 PNG。</span><span class="sxs-lookup"><span data-stu-id="31f4b-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="31f4b-132">如果已成功启动照片模式，拍摄照片并将其存储在磁盘上</span><span class="sxs-lookup"><span data-stu-id="31f4b-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="31f4b-133">将照片捕获到磁盘后，退出照片模式，然后清理对象</span><span class="sxs-lookup"><span data-stu-id="31f4b-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="31f4b-134">将照片捕获到 Texture2D</span><span class="sxs-lookup"><span data-stu-id="31f4b-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="31f4b-135">将数据捕获到 Texture2D 时，该过程与捕获到磁盘非常类似。</span><span class="sxs-lookup"><span data-stu-id="31f4b-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="31f4b-136">遵循上面的设置过程。</span><span class="sxs-lookup"><span data-stu-id="31f4b-136">Follow the set up process above.</span></span>

<span data-ttu-id="31f4b-137">在*OnPhotoModeStarted*中，将帧捕获到内存。</span><span class="sxs-lookup"><span data-stu-id="31f4b-137">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="31f4b-138">然后，将结果应用到纹理，并使用上面的常见清除代码。</span><span class="sxs-lookup"><span data-stu-id="31f4b-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="31f4b-139">捕获照片并与原始字节交互</span><span class="sxs-lookup"><span data-stu-id="31f4b-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="31f4b-140">若要与内存中帧的原始字节交互，请按照上述设置步骤进行操作，并在将照片捕获到 Texture2D 时*OnPhotoModeStarted* 。</span><span class="sxs-lookup"><span data-stu-id="31f4b-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="31f4b-141">不同之处在于，可在*OnCapturedPhotoToMemory*中获取原始字节并与其进行交互。</span><span class="sxs-lookup"><span data-stu-id="31f4b-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="31f4b-142">在此示例中，您将创建一个*列表，<Color>* 可以通过*SetPixels （）* 进一步处理或应用于纹理</span><span class="sxs-lookup"><span data-stu-id="31f4b-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="31f4b-143">视频捕获</span><span class="sxs-lookup"><span data-stu-id="31f4b-143">Video Capture</span></span>

<span data-ttu-id="31f4b-144">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="31f4b-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="31f4b-145">**类型：** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="31f4b-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="31f4b-146">*VideoCapture*函数与*PhotoCapture*非常类似。</span><span class="sxs-lookup"><span data-stu-id="31f4b-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="31f4b-147">唯一的两个不同之处在于，必须指定每秒帧数（FPS）值，并且只能以。</span><span class="sxs-lookup"><span data-stu-id="31f4b-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="31f4b-148">使用*VideoCapture*的步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="31f4b-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="31f4b-149">创建*VideoCapture*对象</span><span class="sxs-lookup"><span data-stu-id="31f4b-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="31f4b-150">使用所需的设置创建*CameraParameters*对象</span><span class="sxs-lookup"><span data-stu-id="31f4b-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="31f4b-151">通过*StartVideoModeAsync*启动视频模式</span><span class="sxs-lookup"><span data-stu-id="31f4b-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="31f4b-152">开始录制视频</span><span class="sxs-lookup"><span data-stu-id="31f4b-152">Start recording video</span></span>
5. <span data-ttu-id="31f4b-153">停止录制视频</span><span class="sxs-lookup"><span data-stu-id="31f4b-153">Stop recording video</span></span>
6. <span data-ttu-id="31f4b-154">停止视频模式并清理资源</span><span class="sxs-lookup"><span data-stu-id="31f4b-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="31f4b-155">首先，创建*VideoCapture*对象*VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="31f4b-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="31f4b-156">接下来，设置要用于记录和启动的参数。</span><span class="sxs-lookup"><span data-stu-id="31f4b-156">Next, set up the parameters you will want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="31f4b-157">启动后，开始记录</span><span class="sxs-lookup"><span data-stu-id="31f4b-157">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="31f4b-158">记录开始后，你可以更新你的 UI 或行为以启用停止。</span><span class="sxs-lookup"><span data-stu-id="31f4b-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="31f4b-159">在这里，你只需记录。</span><span class="sxs-lookup"><span data-stu-id="31f4b-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="31f4b-160">稍后，你将需要停止记录。</span><span class="sxs-lookup"><span data-stu-id="31f4b-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="31f4b-161">例如，这种情况可能发生在计时器或用户输入中。</span><span class="sxs-lookup"><span data-stu-id="31f4b-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="31f4b-162">录制停止后，停止视频模式并清理资源。</span><span class="sxs-lookup"><span data-stu-id="31f4b-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="31f4b-163">“疑难解答”</span><span class="sxs-lookup"><span data-stu-id="31f4b-163">Troubleshooting</span></span>
* <span data-ttu-id="31f4b-164">无可用解决方案</span><span class="sxs-lookup"><span data-stu-id="31f4b-164">No resolutions are available</span></span>
    * <span data-ttu-id="31f4b-165">确保在项目中指定了**网络摄像机**功能。</span><span class="sxs-lookup"><span data-stu-id="31f4b-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="31f4b-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31f4b-166">See Also</span></span>
* [<span data-ttu-id="31f4b-167">可定位相机</span><span class="sxs-lookup"><span data-stu-id="31f4b-167">Locatable camera</span></span>](locatable-camera.md)
