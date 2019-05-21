---
title: 在 Unity 中定位照相机
description: 在 Unity 中 HoloLens 可定位照相机使用情况。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 照片、 视频、 hololens、 照相机、 unity、 可定位
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592339"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="cffda-104">在 Unity 中定位照相机</span><span class="sxs-lookup"><span data-stu-id="cffda-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="cffda-105">启用的照片视频摄像机的功能</span><span class="sxs-lookup"><span data-stu-id="cffda-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="cffda-106">若要使用的应用必须声明为"网络摄像机"功能[照相机](locatable-camera.md)。</span><span class="sxs-lookup"><span data-stu-id="cffda-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="cffda-107">在 Unity 编辑器中，转到播放机设置通过导航到"编辑 > 项目设置 > Player"页面</span><span class="sxs-lookup"><span data-stu-id="cffda-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="cffda-108">单击"Windows 应用商店"选项卡</span><span class="sxs-lookup"><span data-stu-id="cffda-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="cffda-109">在"发布设置 > 功能"部分中，检查**网络摄像头**并**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="cffda-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="cffda-110">只有一项操作会出现一次照相机。</span><span class="sxs-lookup"><span data-stu-id="cffda-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="cffda-111">若要确定哪种模式 （照片、 视频或无） 照相机目前在中，可以检查 UnityEngine.XR.WSA.WebCam.Mode。</span><span class="sxs-lookup"><span data-stu-id="cffda-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="cffda-112">照片拍摄</span><span class="sxs-lookup"><span data-stu-id="cffda-112">Photo Capture</span></span>

<span data-ttu-id="cffda-113">**命名空间：** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="cffda-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="cffda-114">**类型：** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="cffda-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="cffda-115">*PhotoCapture*类型使您可以充分仍照片的照片视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="cffda-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="cffda-116">常规模式，用于使用*PhotoCapture*来拍摄一张照片如下所示：</span><span class="sxs-lookup"><span data-stu-id="cffda-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="cffda-117">创建*PhotoCapture*对象</span><span class="sxs-lookup"><span data-stu-id="cffda-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="cffda-118">创建*CameraParameters*与我们想要的设置的对象</span><span class="sxs-lookup"><span data-stu-id="cffda-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="cffda-119">Start Photo Mode via *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="cffda-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="cffda-120">执行所需的照片</span><span class="sxs-lookup"><span data-stu-id="cffda-120">Take the desired photo</span></span>
    * <span data-ttu-id="cffda-121">（可选）与该图片进行交互</span><span class="sxs-lookup"><span data-stu-id="cffda-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="cffda-122">停止照片模式并清理资源</span><span class="sxs-lookup"><span data-stu-id="cffda-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="cffda-123">常见设置为 PhotoCapture</span><span class="sxs-lookup"><span data-stu-id="cffda-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="cffda-124">对于所有三种用途，我们开始前 3 个以上的步骤相同</span><span class="sxs-lookup"><span data-stu-id="cffda-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="cffda-125">我们首先创建*PhotoCapture*对象</span><span class="sxs-lookup"><span data-stu-id="cffda-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="cffda-126">接下来我们将存储我们的对象、 设置参数，并启动照片模式</span><span class="sxs-lookup"><span data-stu-id="cffda-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="cffda-127">最后，我们还将使用清除本文中介绍的代码相同</span><span class="sxs-lookup"><span data-stu-id="cffda-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="cffda-128">这些步骤之后，可以选择哪种类型的照片将其捕获。</span><span class="sxs-lookup"><span data-stu-id="cffda-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="cffda-129">捕获到文件的照片</span><span class="sxs-lookup"><span data-stu-id="cffda-129">Capture a Photo to a File</span></span>

<span data-ttu-id="cffda-130">最简单的操作是捕获照片直接到文件。</span><span class="sxs-lookup"><span data-stu-id="cffda-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="cffda-131">可以为 JPG 或 PNG 保存照片。</span><span class="sxs-lookup"><span data-stu-id="cffda-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="cffda-132">如果我们已成功启动照片模式下，我们现在将拍摄一张照片并将其存储在磁盘上</span><span class="sxs-lookup"><span data-stu-id="cffda-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="cffda-133">在捕获后到磁盘的照片，我们将退出照片模式，并清除我们的对象</span><span class="sxs-lookup"><span data-stu-id="cffda-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="cffda-134">捕获到 Texture2D 照片</span><span class="sxs-lookup"><span data-stu-id="cffda-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="cffda-135">数据捕获到 Texture2D，过程将非常类似于捕获到磁盘。</span><span class="sxs-lookup"><span data-stu-id="cffda-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="cffda-136">我们将遵循上述过程设置。</span><span class="sxs-lookup"><span data-stu-id="cffda-136">We will follow the set up process above.</span></span>

<span data-ttu-id="cffda-137">在中*OnPhotoModeStarted*，我们将捕获的帧的内存。</span><span class="sxs-lookup"><span data-stu-id="cffda-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="cffda-138">我们然后将为纹理应用我们的结果，并使用清理上述代码的常见。</span><span class="sxs-lookup"><span data-stu-id="cffda-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="cffda-139">原始字节可捕获照片和交互</span><span class="sxs-lookup"><span data-stu-id="cffda-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="cffda-140">与内存中的原始字节进行交互框架中，我们将遵循相同的设置按照上述步骤并*OnPhotoModeStarted*如捕获 Texture2D 到照片中所示。</span><span class="sxs-lookup"><span data-stu-id="cffda-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="cffda-141">区别在于*OnCapturedPhotoToMemory*我们可以获取的原始字节，并与之交互。</span><span class="sxs-lookup"><span data-stu-id="cffda-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="cffda-142">在此示例中，我们将创建*列表<Color>* 这可能会进一步处理或应用于通过纹理*SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="cffda-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="cffda-143">视频捕获</span><span class="sxs-lookup"><span data-stu-id="cffda-143">Video Capture</span></span>

<span data-ttu-id="cffda-144">**命名空间：** *UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="cffda-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="cffda-145">**类型：** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="cffda-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="cffda-146">*VideoCapture*功能非常类似于*PhotoCapture*。</span><span class="sxs-lookup"><span data-stu-id="cffda-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="cffda-147">只有两个差异是你必须指定帧每个第二个 (FPS) 值，并且你可以仅将直接保存到磁盘为.mp4 文件。</span><span class="sxs-lookup"><span data-stu-id="cffda-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="cffda-148">若要使用的步骤*VideoCapture*如下所示：</span><span class="sxs-lookup"><span data-stu-id="cffda-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="cffda-149">创建*VideoCapture*对象</span><span class="sxs-lookup"><span data-stu-id="cffda-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="cffda-150">创建*CameraParameters*与我们想要的设置的对象</span><span class="sxs-lookup"><span data-stu-id="cffda-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="cffda-151">启动视频模式下通过*StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="cffda-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="cffda-152">开始录制视频</span><span class="sxs-lookup"><span data-stu-id="cffda-152">Start recording video</span></span>
5. <span data-ttu-id="cffda-153">停止录制视频</span><span class="sxs-lookup"><span data-stu-id="cffda-153">Stop recording video</span></span>
6. <span data-ttu-id="cffda-154">停止视频模式并清理资源</span><span class="sxs-lookup"><span data-stu-id="cffda-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="cffda-155">我们首先创建我们*VideoCapture*对象*VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="cffda-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="cffda-156">然后，我们将在设置用于录制和开始，我们想的参数。</span><span class="sxs-lookup"><span data-stu-id="cffda-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="cffda-157">启动后，我们将开始录制</span><span class="sxs-lookup"><span data-stu-id="cffda-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="cffda-158">启动录制后，无法更新你的 UI 或行为，以便停止。</span><span class="sxs-lookup"><span data-stu-id="cffda-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="cffda-159">此处我们只需记录</span><span class="sxs-lookup"><span data-stu-id="cffda-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="cffda-160">稍后，我们想要停止录制。</span><span class="sxs-lookup"><span data-stu-id="cffda-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="cffda-161">从计时器或用户输入，例如发生此情况。</span><span class="sxs-lookup"><span data-stu-id="cffda-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="cffda-162">录制停止后，我们将停止视频模式并清理资源。</span><span class="sxs-lookup"><span data-stu-id="cffda-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="cffda-163">疑难解答</span><span class="sxs-lookup"><span data-stu-id="cffda-163">Troubleshooting</span></span>
* <span data-ttu-id="cffda-164">有没有解决方法</span><span class="sxs-lookup"><span data-stu-id="cffda-164">No resolutions are available</span></span>
    * <span data-ttu-id="cffda-165">请确保**网络摄像头**项目中指定功能。</span><span class="sxs-lookup"><span data-stu-id="cffda-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="cffda-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="cffda-166">See Also</span></span>
* [<span data-ttu-id="cffda-167">可定位照相机</span><span class="sxs-lookup"><span data-stu-id="cffda-167">Locatable camera</span></span>](locatable-camera.md)
