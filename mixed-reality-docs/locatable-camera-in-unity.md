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
# <a name="locatable-camera-in-unity"></a>在 Unity 中定位照相机

## <a name="enabling-the-capability-for-photo-video-camera"></a>启用的照片视频摄像机的功能

若要使用的应用必须声明为"网络摄像机"功能[照相机](locatable-camera.md)。
1. 在 Unity 编辑器中，转到播放机设置通过导航到"编辑 > 项目设置 > Player"页面
2. 单击"Windows 应用商店"选项卡
3. 在"发布设置 > 功能"部分中，检查**网络摄像头**并**麦克风**功能

只有一项操作会出现一次照相机。 若要确定哪种模式 （照片、 视频或无） 照相机目前在中，可以检查 UnityEngine.XR.WSA.WebCam.Mode。

## <a name="photo-capture"></a>照片拍摄

**命名空间：** *UnityEngine.XR.WSA.WebCam*<br>
**类型：** *PhotoCapture*

*PhotoCapture*类型使您可以充分仍照片的照片视频摄像机。 常规模式，用于使用*PhotoCapture*来拍摄一张照片如下所示：
1. 创建*PhotoCapture*对象
2. 创建*CameraParameters*与我们想要的设置的对象
3. Start Photo Mode via *StartPhotoModeAsync*
4. 执行所需的照片
    * （可选）与该图片进行交互
5. 停止照片模式并清理资源

### <a name="common-set-up-for-photocapture"></a>常见设置为 PhotoCapture

对于所有三种用途，我们开始前 3 个以上的步骤相同

我们首先创建*PhotoCapture*对象

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

接下来我们将存储我们的对象、 设置参数，并启动照片模式

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

最后，我们还将使用清除本文中介绍的代码相同

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

这些步骤之后，可以选择哪种类型的照片将其捕获。

### <a name="capture-a-photo-to-a-file"></a>捕获到文件的照片

最简单的操作是捕获照片直接到文件。 可以为 JPG 或 PNG 保存照片。

如果我们已成功启动照片模式下，我们现在将拍摄一张照片并将其存储在磁盘上

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

在捕获后到磁盘的照片，我们将退出照片模式，并清除我们的对象

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

### <a name="capture-a-photo-to-a-texture2d"></a>捕获到 Texture2D 照片

数据捕获到 Texture2D，过程将非常类似于捕获到磁盘。

我们将遵循上述过程设置。

在中*OnPhotoModeStarted*，我们将捕获的帧的内存。

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

我们然后将为纹理应用我们的结果，并使用清理上述代码的常见。

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>原始字节可捕获照片和交互

与内存中的原始字节进行交互框架中，我们将遵循相同的设置按照上述步骤并*OnPhotoModeStarted*如捕获 Texture2D 到照片中所示。 区别在于*OnCapturedPhotoToMemory*我们可以获取的原始字节，并与之交互。

在此示例中，我们将创建*列表<Color>* 这可能会进一步处理或应用于通过纹理*SetPixels()*

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

## <a name="video-capture"></a>视频捕获

**命名空间：** *UnityEngine.XR.WSA.WebCam*<br>
**类型：** *VideoCapture*

*VideoCapture*功能非常类似于*PhotoCapture*。 只有两个差异是你必须指定帧每个第二个 (FPS) 值，并且你可以仅将直接保存到磁盘为.mp4 文件。 若要使用的步骤*VideoCapture*如下所示：
1. 创建*VideoCapture*对象
2. 创建*CameraParameters*与我们想要的设置的对象
3. 启动视频模式下通过*StartVideoModeAsync*
4. 开始录制视频
5. 停止录制视频
6. 停止视频模式并清理资源

我们首先创建我们*VideoCapture*对象*VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

然后，我们将在设置用于录制和开始，我们想的参数。

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

启动后，我们将开始录制

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

启动录制后，无法更新你的 UI 或行为，以便停止。 此处我们只需记录

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

稍后，我们想要停止录制。 从计时器或用户输入，例如发生此情况。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

录制停止后，我们将停止视频模式并清理资源。

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

## <a name="troubleshooting"></a>疑难解答
* 有没有解决方法
    * 请确保**网络摄像头**项目中指定功能。

## <a name="see-also"></a>请参阅
* [可定位照相机](locatable-camera.md)
