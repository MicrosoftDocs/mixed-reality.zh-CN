---
title: 定位照相机
description: 有关短期正面相机相机、工作原理以及开发人员可用的配置文件和分辨率的一般信息。
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: 照相机, hololens, 彩色相机, 正面朝, hololens 2, cv, 计算机视觉, 基准, 标记, qr 码, qr, 照片, 视频
ms.openlocfilehash: 368943dd70c721a41ca7c265a19ecb7c394db312
ms.sourcegitcommit: 4ac761fed7a9570977f6d031ba4f870585d6630a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861723"
---
# <a name="locatable-camera"></a>定位照相机

HoloLens 包括在设备前面安装的面向世界的相机, 使应用能够查看用户看到的内容。 开发人员可以访问和控制照相机, 就像在 smartphone、笔记本或台式机上的彩色照相机一样。 在 mobile 和 desktop 上工作的相同通用 windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)和 windows Media foundation Api 在 HoloLens 上工作。 Unity[还包装了这些 Windows api](locatable-camera-in-unity.md) , 以便在 HoloLens 上抽象地使用照相机的简单用法, 例如拍摄定期照片和视频 (有或没有全息影像) 以及查找相机在场景中的位置和透视。

## <a name="device-camera-information"></a>设备照相机信息

### <a name="hololens-first-generation"></a>HoloLens (第一代)

* 固定的照片/视频 (PV) 摄像机, 具有自动白平衡、自动曝光和完整图像处理管道。
* 当照相机处于活动状态时, 面向世界的白色隐私 LED 将发亮
* 摄像头支持以下模式 (所有模式均为16:9 纵横比), 其状态为30、24、20、15和 5 fps:

  |  视频  |  预览  |  正常  |  视图的水平字段 (FOV) |  建议的用法 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (视频不稳定的默认模式) | 
  |  不可用 |  不可用 |  2048x1152 |  67deg |  最高分辨率静止图像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  视频抖动之前的 Overscan (填充) 分辨率 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  带有 overscan 的大型 FOV 视频模式 | 
  |  896x504 |  896x504 |  896x504 |  48deg |  图像处理任务的低功率/低分辨率模式 | 

### <a name="hololens-2"></a>HoloLens 2

* 自动将照片/视频 (PV) 摄像机与自动平衡、自动曝光和完整图像处理管道配合工作。
* 当照相机处于活动状态时, 世界上的白色隐私 LED 将会亮起。
* HoloLens 2 支持不同的相机配置文件。 了解如何[发现和选择相机功能](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)。
* 摄像头支持以下配置文件和分辨率 (所有视频模式均为16:9 纵横比):
  
  | 配置文件                                         | 视频     | 预览   | 正常     | 帧速率 | 视图的水平字段 (FOV) | 建议的用法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | 旧, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15、30       | 64.69                            | 高质量视频录制                |
  | 旧, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15、30       | 64.69                            | 用于高质量照片捕获的预览流 |
  | 旧, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64.69                            | 优质照片捕获                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15、30       | 64.69                            | 长持续时间方案                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15、30       | 64.69                            | 长持续时间方案                     |
  | 视频会议, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15、30、60    | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100                           | 1504x846  | 1504x846  |           | 5、15、30、60  | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 960x540   |           |           | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 640x360   |           |           | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |
  | 视频会议, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15、30       | 64.69                            | 视频会议, 长持续时间方案 |

>[!NOTE]
>客户可以利用[混合现实捕获](mixed-reality-capture.md)来获取应用的视频或照片, 其中包括全息影像和视频抖动。
>
>作为开发人员, 如果你希望在客户捕获内容时能够更好地显示你的应用程序, 请考虑创建应用程序时应考虑的一些事项。 你还可以直接在应用中启用 (和自定义) 混合现实捕获。 在[混合现实捕获](mixed-reality-capture-for-developers.md)中了解更多开发人员。

## <a name="locating-the-device-camera-in-the-world"></a>在世界各地查找设备照相机

当 HoloLens 拍摄照片和视频时, 捕获的帧包括世界上相机的位置以及照相机的镜头型号。 这样, 应用程序就可以在现实世界中为补充式的图像处理方案提供有关相机位置的原因。 开发人员可以使用他们最喜爱的图像处理或自定义计算机视觉库, 创造性地滚动自己的方案。

HoloLens 文档中其他地方的 "照相机" 可能指的是 "虚拟游戏相机" (应用呈现到的截锥)。 除非另有指示, 否则, 此页上的 "照相机" 指的是实际的 RGB 颜色相机。

此页上的详细信息介绍了如何使用[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference)类, 不过, 还存在使用[媒体基础特性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)请求照相机内部函数和位置的 api。 有关详细信息, 请参阅[全息面部跟踪示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)。

### <a name="images-with-coordinate-systems"></a>带有坐标系统的图像

每个图像帧 (无论是照片还是视频) 在捕获时都包含一个[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , 可使用[MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[坐标系](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)属性进行访问。 此外, 每个帧都包含了相机镜头模型的说明, 该模型可在[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)属性中找到。 这些转换一起为每个像素定义了三维空间中的射线, 表示生成像素的 photons 所采用的路径。 通过获取从帧的坐标系统到某个其他坐标系统的转换 (例如从[固定的参考框架](coordinate-systems.md#stationary-frame-of-reference)中), 可以将这些光线与应用程序中的其他内容相关。 总而言之, 每个图像框架提供以下内容:
* 像素数据 (以 RGB/NV12/JPEG/etc 格式)
* 捕获位置的[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* 包含照相机镜头模式的[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)类

### <a name="camera-to-application-specified-coordinate-system"></a>照相机到应用程序指定的坐标系统

若要从 "CameraIntrinsics" 和 "CameraCoordinateSystem" 中转到应用程序/全球坐标系统, 需要以下各项:

[Unity 中的定位照相机](locatable-camera-in-unity.md):CameraToWorldMatrix 由 PhotoCaptureFrame 类自动提供 (因此你无需担心 CameraCoordinateSystem 转换)。

[DirectX 中的定位照相机](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking):全息面部跟踪示例显示了查询照相机坐标系统和自己的应用程序坐标系统之间转换的相当直接的方法。

### <a name="distortion-error"></a>失真错误

在 HoloLens 上, 视频和静态图像流在系统的图像处理管道中 undistorted, 然后才能将帧提供给应用程序 (预览流包含原始扭曲帧)。 由于只有 CameraIntrinsics 可用, 因此应用程序必须假定图像帧表示完美的 pinhole 相机。

在 HoloLens (第一代) 上, 在帧元数据中使用 CameraIntrinsics 时, 图像处理器中的 undistortion 函数可能仍会导致最大为10像素的错误。 在许多用例中, 此错误并不重要, 但如果将全息影像与真实的海报/标记对齐, 则会注意到 < 10px 的偏移量 (大约 11mm, 对于离 

## <a name="locatable-camera-usage-scenarios"></a>定位照相机使用方案

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>在捕获照片或视频的世界中显示照片或视频

设备照相机帧附带了 "相机到世界" 转换, 可用于显示在拍摄映像时设备的确切位置。 例如, 你可以在此位置 (CameraToWorld. MultiplyPoint (System.numerics.vector2)) 放置一个小全息图标, 甚至可以在相机面对的方向 (CameraToWorld. MultiplyVector (System.numerics.vector2)) 中绘制一个小箭头。

### <a name="tag--pattern--poster--object-tracking"></a>标记/模式/海报/对象跟踪

许多混合现实应用程序使用可识别的图像或视觉模式在空间中创建以可跟踪点。 然后, 使用该对象相对于该点呈现对象, 或创建一个已知位置。 某些使用 HoloLens 包括查找用 fiducials 标记的现实世界对象 (例如, 带有 QR 码的电视显示器)、将全息影像置于 fiducials 上, 并与已设置为通过Wi-fi。

若要识别可视模式, 然后将该对象放在应用程序的世界空间中, 需要执行以下操作:
1. 图像模式识别工具包, 如 QR 码、AR 标记、面部查找器、圆形跟踪器、OCR 等。
2. 在运行时收集图像帧, 并将其传递到识别层
3. 将其图像位置 Unproject 为世界位置, 或可能是世界光线。 请参阅
4. 将虚拟模型放置在这些世界位置

一些重要的图像处理链接:
* [OpenCV](http://opencv.org/)
* [QR 标记](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft 在线翻译](https://www.microsoft.com/translator/business)

保持交互应用程序帧速率非常重要, 尤其是在处理长时间运行的图像识别算法时。 出于此原因, 我们通常使用以下模式:
1. 主线程: 管理照相机对象
2. 主线程: 请求新帧 (异步)
3. 主线程: 将新帧传递到跟踪线程
4. 跟踪线程: 处理收集关键点的图像
5. 主线程: 移动虚拟模型以匹配找到的关键点
6. 主线程: 从步骤2重复

某些图像标记系统仅提供单个像素位置 (其他在这种情况下将不需要此部分), 这相当于可能的位置。 若要访问单个3d 位置, 我们可以利用多个射线, 并按近似交点查找最终结果。 为此, 您需要:
1. 获取正在收集多个照相机图像的循环
2. 查找关联的功能点及其世界光线
3. 如果有一个功能字典, 每个功能都有多个世界光线, 则可以使用以下代码来解决这些光线的交集:

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

如果有两个或多个跟踪标记位置, 则可以将建模场景定位到适合用户当前方案。 如果无法假定重心, 则需要三个标记位置。 在许多情况下, 我们使用简单的配色方案, 其中白色球体表示实时跟踪标记位置, 蓝色球体表示建模标记位置, 这使用户能够以可视方式衡量对齐质量。 我们假定在所有应用程序中都进行以下设置:
* 两个或多个建模标记位置
* 场景中的一个 "校准空间" 是标记的父项
* 相机功能标识符
* 移动校准空间以便使建模标记与实时标记对齐的行为 (我们小心地移动父空间, 而不是建模标记本身, 因为其他连接是相对于它们的位置)。

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>使用 Led 或其他识别器库跟踪或确定标记为静止或移动现实世界对象/面部

示例：
* 带有 Led 的工业机器人 (或用于缓慢移动对象的 QR 码)
* 标识并识别房间中的对象
* 确定并识别房间中的人员 (例如, 在人脸上放置全息的联系人卡片)

## <a name="see-also"></a>请参阅
* [定位相机示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Unity 中的可定位相机](locatable-camera-in-unity.md)
* [混合现实捕获](mixed-reality-capture.md)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [媒体捕获简介](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [全息面部跟踪示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
