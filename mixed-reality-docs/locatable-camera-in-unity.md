---
title: Unity 中的定位照相机
description: 在 Unity 中使用 HoloLens 定位相机。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 照片、视频、hololens、照相机、unity、定位
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515431"
---
# <a name="locatable-camera-in-unity"></a>Unity 中的定位照相机

## <a name="enabling-the-capability-for-photo-video-camera"></a>启用相片视频相机功能

必须为应用声明 "网络摄像机" 功能, 才能使用[相机](locatable-camera.md)。
1. 在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player" 页, 转到 "播放机" 设置
2. 单击 "Windows 应用商店" 选项卡
3. 在 "发布设置 > 功能" 部分中, 检查**网络摄像机**和**麦克风**功能

照相机一次只能出现一次操作。 若要确定照相机当前在哪个模式 (照片、视频或无), 可以检查 UnityEngine. XR。

## <a name="photo-capture"></a>照片捕获

**命名空间：** *UnityEngine. XR*<br>
**类型：** *PhotoCapture*

*PhotoCapture*类型允许你使用照片摄像机拍摄照片。 使用*PhotoCapture*拍摄照片的一般模式如下所示:
1. 创建*PhotoCapture*对象
2. 使用所需的设置创建*CameraParameters*对象
3. 通过*StartPhotoModeAsync*启动照片模式
4. 拍摄所需照片
    * 可有可无与该图片交互
5. 停止照片模式并清理资源

### <a name="common-set-up-for-photocapture"></a>通用设置 PhotoCapture

对于所有这三个用途, 我们首先执行上述前3个步骤

首先创建一个*PhotoCapture*对象

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

接下来, 我们将存储对象、设置参数和启动照片模式

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

最后, 我们还将使用此处提供的相同清理代码

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

完成这些步骤后, 你可以选择要捕获哪种类型的照片。

### <a name="capture-a-photo-to-a-file"></a>将照片捕获到文件

最简单的操作是将照片直接捕获到文件中。 照片可以保存为 JPG 或 PNG。

如果已成功启动照片模式, 我们现在会拍摄照片, 并将其存储在磁盘上

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

将照片捕获到磁盘后, 将退出照片模式, 然后清理我们的对象

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

### <a name="capture-a-photo-to-a-texture2d"></a>将照片捕获到 Texture2D

将数据捕获到 Texture2D 时, 该过程与捕获到磁盘非常类似。

我们将按照上面的设置过程进行操作。

在*OnPhotoModeStarted*中, 我们会将一个帧捕获到内存。

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

然后, 将结果应用到纹理, 并使用上面的常见清除代码。

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>捕获照片并与原始字节交互

若要与内存中帧的原始字节交互, 我们将按照上述设置步骤进行操作, 就像在 Texture2D 中捕获照片一样*OnPhotoModeStarted* 。 不同之处在于, 可在*OnCapturedPhotoToMemory*中获取原始字节并与其进行交互。

在此示例中, 我们将创建*一个<Color>列表*, 该列表可以通过*SetPixels ()* 进一步处理或应用于纹理

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

**命名空间：** *UnityEngine. XR*<br>
**类型：** *VideoCapture*

*VideoCapture*函数与*PhotoCapture*非常类似。 唯一的两个不同之处在于, 必须指定每秒帧数 (FPS) 值, 并且只能以。 使用*VideoCapture*的步骤如下所示:
1. 创建*VideoCapture*对象
2. 使用所需的设置创建*CameraParameters*对象
3. 通过*StartVideoModeAsync*启动视频模式
4. 开始录制视频
5. 停止录制视频
6. 停止视频模式并清理资源

首先创建*VideoCapture*对象*VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

接下来, 我们将设置要用于记录和启动的参数。

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

启动后, 我们将开始记录

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

记录开始后, 你可以更新你的 UI 或行为以启用停止。 这里我们只记录

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

稍后, 我们需要停止记录。 例如, 这种情况可能发生在计时器或用户输入中。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

录制停止后, 将停止视频模式并清理资源。

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
* 无可用解决方案
    * 确保在项目中指定了**网络摄像机**功能。

## <a name="see-also"></a>请参阅
* [可定位相机](locatable-camera.md)
