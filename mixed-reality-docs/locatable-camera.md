---
title: 可定位照相机
description: HoloLens 前置相机、 它的工作原理，以及配置文件的常规信息和解决方法可供开发人员。
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: 相机、 hololens，颜色照相机前端面向
ms.openlocfilehash: f661fc82fbeab9a870e8ccf7044c9bb375bed7e3
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326293"
---
# <a name="locatable-camera"></a>可定位照相机

HoloLens 包括设备这能使应用程序以查看用户看到的内容的正面上装载了世界摄像头。 开发人员有权访问和控制的照相机就像用于智能手机、 笔记本或台式机上的颜色相机。 相同的通用 windows[媒体捕获](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)，在 HoloLens 上的 windows media foundation Api 适用于移动和桌面工作。 Unity[也具有包装这些 windows Api](locatable-camera-in-unity.md)抽象 HoloLens 的任务，例如正则照片和视频 （有或没有全息） 并在查找中的照相机的位置和角度来看的照相机的简单用法场景。

## <a name="device-camera-information"></a>设备相机信息

### <a name="hololens-first-generation"></a>HoloLens （第一代）

* 固定的焦点照片/视频 (PV) 摄像机，白色自动平衡、 自动公开与完整的映像处理管道
* 面向全球的白色隐私发光二极管会只要照相机处于活动状态
* 照相机支持在 30、 24、 20、 15 和 5 帧/秒 （所有模式都都纵横比为 16:9） 的以下模式：

  |  视频  |  预览  |  仍  |  水平视野 (FOV H) |  建议的用法 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  （通过视频防抖动的默认模式） | 
  |  不可用 |  不可用 |  2048x1152 |  67deg |  最高分辨率静止图像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  视频防抖动之前自定大小 （填充） 解析 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  使用过度扫描大型 FOV 视频模式 | 
  |  896x504 |  896x504 |  896x504 |  48deg |  低功耗 / 图像的低分辨率模式处理任务 | 

### <a name="hololens-2"></a>HoloLens 2

* 自动聚焦照片/视频 (PV) 摄像机，白色自动平衡、 自动公开与完整的映像处理管道
* 面向全球的白色隐私发光二极管会只要照相机处于活动状态
* 照相机支持以下模式 （所有视频的模式是纵横比为 16:9）：

  >[!NOTE]
  >这些模式会在 HoloLens 2 正式发布之前的更改。

  |  视频  |  预览  |  仍  |  帧速率  |  水平视野 (FOV H) |  建议的用法 | 
  |----------|----------|----------|----------|----------|----------|
  |  1920x1080 |  1920x1080 |  不可用 |  30、 15 帧/秒  |  54deg  |  （通过视频防抖动的默认模式） | 
  |  不可用 |  不可用 |  3904X2196 |  不可用  |  64deg |  最高分辨率静止图像 | 
  |  2272x1278 |  2272x1278 |  不可用 |  30、 15 帧/秒  |  64deg |  视频防抖动之前自定大小 （填充） 解析 | 
  |  1952x1100 |  1952x1100 |  1952x1100  |  30、 15 帧/秒  |  64deg |  高质量的流式处理 | 
  |  1280x720 |  1280x720 |  不可用 |  30、 15、 5 帧/秒  |  64deg |  流式处理和图像处理任务的每个分辨率低电源模式 | 

## <a name="locating-the-device-camera-in-the-world"></a>在世界上定位设备相机

照片和视频 HoloLens 时，捕获的帧世界，以及照相机的镜头模型中包括的照相机的位置。 这样，应用程序的原因有关的扩充式映像方案现实生活中的照相机的位置信息。 开发人员可以创造性地回滚其自己的方案使用他们最喜爱的图像处理或自定义计算机影像库。

HoloLens 文档中的其他位置的"照相机"可能指"虚拟游戏照相机"（截锥应用程序呈现为）。 否则表示，除非在此页上的"照相机"是指实际的 RGB 颜色照相机。

有关此页覆盖中使用的详细信息[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference)类，但是也有 Api 拉取照相机内部函数和使用的位置[Media Foundation 属性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)。 请参阅[Holographic 跟踪示例的人脸](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)有关详细信息。

### <a name="images-with-coordinate-systems"></a>与坐标系统的映像

每个图像帧 (是否照片或视频) 包括[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)捕获可使用访问时根节点的照相机[坐标系](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)属性您[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)。 此外，每个帧包含照相机镜头模型中可以找到的说明[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)属性。 在一起，这些转换定义为每个像素 ray 在 3D 空间中表示生成像素 photons 所采用的路径。 这些大气可以与通过对某些其他坐标系统从框架的坐标系统获取转换应用程序中的其他内容 (例如，从[固定参考框架](coordinate-systems.md#stationary-frame-of-reference))。 总之，每个图像帧提供以下功能：
* 像素格式的数据 （RGB/NV12/JPEG/等）
* 一个[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)从捕获的位置
* 一个[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)类包含照相机的可重用功能区模式

### <a name="camera-to-application-specified-coordinate-system"></a>照相机传送到应用程序指定坐标系统

若要从 CameraIntrinsics 和 CameraCoordinateSystem 转到应用程序/世界坐标系统，你将需要：

[在 Unity 中的定位照相机](locatable-camera-in-unity.md):CameraToWorldMatrix 会自动提供由 PhotoCaptureFrame 类 （因此，无需担心 CameraCoordinateSystem 转换）。

[在 DirectX 可定位照相机](locatable-camera-in-directx.md):演示了查询的照相机的坐标系统和你自己的应用程序 coordinate system(s) 之间的转换非常简单的方法。

### <a name="distortion-error"></a>扭曲错误

HoloLens，在视频和仍图像流是未扭曲系统的映像处理管道中之前帧都提供给应用程序 （预览流包含原始失真的帧）。 由于仅 CameraIntrinsics 都可用，应用程序必须假定图像帧表示完美 pinhole 照相机，但是变形纠正函数中的图像处理器可能仍将保留最多 10 个像素的错误上 HoloLens （第一代）在使用 CameraIntrinsics 帧元数据中。 在许多用例，此错误将不起作用，但如果要对齐全息到实际海报/标记，例如，且您注意到 < 10px 偏移量 （大致为全息定位 2 米消失的 11 毫米） 此扭曲错误可能是原因。 

## <a name="locatable-camera-usage-scenarios"></a>可定位照相机使用方案

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>在捕获时的世界中显示的照片或视频

设备相机帧附带"照相机 World"转换，用于显示准确的设备时图像捕获。 例如在 （CameraToWorld.MultiplyPoint(Vector3.zero)) 和甚至绘图小箭头方向照相机面向 (CameraToWorld.MultiplyVector(Vector3.forward)) 此位置开始位置小 holographic 图标。

### <a name="tag--pattern--poster--object-tracking"></a>标记 / 海报 / 对象跟踪

许多混合的现实应用程序使用可识别图像或 visual 模式空间中创建的可跟踪点。 这再用于呈现对象相对于的点或创建一个已知的位置。 HoloLens 的一些用途包括的查找现实世界对象标记为裂痕 （例如一个有 QR 码电视监视器）、 通过裂痕，放置全息和直观地与已设置为与通过 HoloLens 的平板电脑之类的非 HoloLens 设备配对Wi-fi。

若要识别 visual 模式，然后将该对象放在应用程序世界空间中，你将需要几件事：
1. 一个映像模式识别的工具包，如 QR 码、 AR 标记、 人脸 finder、 圆形跟踪器、 OCR 等。
2. 收集在运行时，图像帧，并将其传递给识别层
3. Unproject 回世界位置或可能世界大气其映像位置。 请参阅
4. 虚拟模型放这些世界位置

一些重要的图像处理链接：
* [OpenCV](http://opencv.org/)
* [QR 标记](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

保留交互式应用程序帧速率至关重要，尤其是在处理长时间运行图像识别算法。 因此我们通常使用以下模式：
1. 主线程： 管理相机对象
2. 主线程： 请求新帧 （异步）
3. 主线程： 将新帧传递给跟踪线索
4. 跟踪线程： 处理要收集的关键点图像
5. 主线程： 移动虚拟模式，以匹配找到关键点
6. 重复步骤 2 中的主线程：

某些图像标记系统仅提供单个像素的位置 (其他人提供完整的转换在这种情况下将不需要此部分)，其相当于一条可能的位置。 若要获取到一个单独的三维位置我们可以利用多个大气并查找其近似的交集的最终结果上。 若要执行此操作将需要：
1. 获取一个循环将收集多个照相机图像
2. 查找关联的功能点和其全球大气
3. 当具有的功能，每个都有多个世界大气，字典时可以使用下面的代码来解决这些射线相交的：

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

给定两个或多个跟踪的标记位置，您可以定位 modelled 的场景以适合用户当前应用场景。 如果您不能假定重力，您将需要三个标记位置。 在许多情况下，我们使用简单的配色方案白色球体表示实时跟踪标记位置和蓝色球体表示建模标记位置，这允许用户直观地仪表对齐质量。 在我们的所有应用程序中，我们假设以下设置：
* 两个或多个建模标记位置
* 其中一个校准的空间场景中的标记的父级
* 照相机功能标识符
* 将移动校准格对齐 （我们非常小心地将移动的父区域中，不 modelled 标记本身，因为其他 connect 是它们的相对位置） 的实时标记的 modelled 的标记的行为。

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>跟踪或标识标记的静态或移动现实世界对象/人脸使用 Led 或其他识别器库

示例：
* 使用 Led 工业机器人 （或对象的速度较慢移动 QR 码）
* 确定和识别在聊天室中的对象
* 确定和识别出空间 （例如位置 holographic 联系人卡通过人脸） 中的人员

## <a name="see-also"></a>请参阅
* [DirectX 中的可定位相机](locatable-camera-in-directx.md)
* [Unity 中的可定位相机](locatable-camera-in-unity.md)
* [混合现实捕获](mixed-reality-capture.md)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [媒体捕获简介](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [全息版的人脸跟踪示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
