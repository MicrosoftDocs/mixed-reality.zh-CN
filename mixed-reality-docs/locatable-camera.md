---
title: 可定位照相机
description: HoloLens 前置相机、 它的工作原理，以及配置文件的常规信息和解决方法可供开发人员。
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 照相机、 hololens、 颜色照相机，面向 hololens 2、 cv、 计算机视觉、 基准的前端、 标记、 qr 码、 qr、 照片、 视频
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028611"
---
# <a name="locatable-camera"></a>可定位照相机

HoloLens 包括设备这能使应用程序以查看用户看到的内容的正面上装载了世界摄像头。 开发人员有权访问和控制的照相机就像用于智能手机、 笔记本或台式机上的颜色相机。 相同的通用 windows[媒体捕获](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)，在 HoloLens 上的 windows media foundation Api 适用于移动和桌面工作。 Unity[也具有包装这些 windows Api](locatable-camera-in-unity.md)抽象 HoloLens 的任务，例如正则照片和视频 （有或没有全息） 并在查找中的照相机的位置和角度来看的照相机的简单用法场景。

## <a name="device-camera-information"></a>设备相机信息

### <a name="hololens-first-generation"></a>HoloLens （第一代）

* 固定的焦点照片/视频 (PV) 照相机，摄像机带有白色自动平衡、 自动公开和完整的映像处理管道。
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

* 自动聚焦照片/视频 (PV) 照相机，摄像机带有白色自动平衡、 自动公开和完整的映像处理管道。
* 面向全球的白色隐私发光二极管会只要照相机处于活动状态。
* HoloLens 2 支持不同的照相机配置文件。 了解如何[发现和选择照相机功能](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)。
* 照相机支持以下配置文件和 （所有视频的模式是纵横比为 16:9） 的解决方法：
  
  | 配置文件                                         | 视频     | 预览   | 仍     | 帧速率 | 水平视野 (FOV H) | 建议的用法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0  BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15,30       | 64.69                            | 高质量视频录制                |
  | Legacy,0  BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | 高质量照片拍摄                  |
  | BalancedVideoAndPhoto,120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64.69                            | 持续时间长的方案                     |
  | BalancedVideoAndPhoto,120                       | 1504x846  | 1504x846  |           | 15,30       | 64.69                            | 持续时间长的方案                     |
  | 视频会议 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议 100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 1128x635  |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 960x540   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 760x428   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 640x360   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 500x282   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |
  | 视频会议，100 BalancedVideoAndPhoto 120 | 424x240   |           |           | 15,30       | 64.69                            | 视频会议，持续时间长的方案 |

>[!NOTE]
>客户可以利用[混合现实捕获](mixed-reality-capture.md)使视频或照片应用程序，其中包括全息和视频防抖动。
>
>作为开发人员，有一些创建您的应用程序，如果您希望其客户捕获内容时的外观一样好可能时应考虑的注意事项。 此外可以启用 （并自定义） 从直接在您的应用程序中的混合的现实捕获。 了解详细信息，请[开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)。

## <a name="locating-the-device-camera-in-the-world"></a>在世界上定位设备相机

照片和视频 HoloLens 时，捕获的帧世界，以及相机的角度来看投影中包括的照相机的位置。 这样，应用程序的原因有关的扩充式映像方案现实生活中的照相机的位置信息。 开发人员可以创造性地回滚其自己的方案使用他们最喜爱的图像处理或自定义计算机影像库。

HoloLens 文档中的其他位置的"照相机"可能指"虚拟游戏照相机"（截锥应用程序呈现为）。 否则表示，除非在此页上的"照相机"是指实际的 RGB 颜色照相机。

有关此页面涵盖的详细信息[Media Foundation 特性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)，但是也有 Api 拉取照相机内部函数使用[WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)。  

### <a name="images-with-coordinate-systems"></a>与坐标系统的映像

每个图像帧 (是否照片或视频) 包括坐标系，以及两个重要的转换。 "视图"转换到相机，提供的坐标系统中的映射和从照相机"投影"映射至图像中的像素。 在一起，这些转换定义为每个像素 ray 在 3D 空间中表示生成像素 photons 所采用的路径。 这些大气可以与通过对某些其他坐标系统从框架的坐标系统获取转换应用程序中的其他内容 (例如，从[固定参考框架](coordinate-systems.md#stationary-frame-of-reference))。 总之，每个图像帧提供以下功能：
* 像素格式的数据 （RGB/NV12/JPEG/等）
* 3 个部分的元数据 (存储为[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx))，使每个帧"定位":

|  属性名称  |  在任务栏的搜索框中键入  |  GUID  |  描述 | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  存储[坐标系](coordinate-systems-in-directx.md)的捕获的帧 | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  将照相机的外部转换存储在坐标系统 | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  将存储照相机的投影转换 | 

投影转换表示映射到扩展从-1 到 + 1 中的 X 和 Y 轴图平面上的可重用功能区的内部属性 （焦距，中心的投影，倾斜）。

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

不同的应用程序将具有不同的坐标系统。 下面是流来查找单个应用程序的照相机像素的概览：

![应用于照相机坐标系统的转换](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>照相机传送到应用程序指定坐标系统

若要从 CameraView 和 CameraCoordinateSystem 转到应用程序/世界坐标系统，你将需要：

[在 Unity 中的定位照相机](locatable-camera-in-unity.md):CameraToWorldMatrix 会自动提供由 PhotoCaptureFrame 类 （因此，无需担心 CameraCoordinateSystem 转换）。

[在 DirectX 可定位照相机](locatable-camera-in-directx.md):演示了查询的照相机的坐标系统和你自己的应用程序 coordinate system(s) 之间的转换非常简单的方法。

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>应用程序指定到像素坐标的坐标系统

让我们假设你想要查找或上的照相机图像绘制在特定的三维位置：

需要采用稍有不同的视图和投影转换时这两个 4 × 4 矩阵。 即执行投影后, 一个将规范化通过 w，在投影中的此额外步骤模拟如何将多个不同的三维位置的最终会得到为 （即任何内容沿某些射线将显示同一像素） 的屏幕上的同一个二维位置。 因此要点 （在着色器代码中）：

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>像素到应用程序指定坐标系统

个世界坐标从像素都是个小技巧：

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

定义作为 UnProject:

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

若要查找一个点的实际世界位置，将需要以下两者之一： 两个世界大气和查找它们的交集，或者有已知的点大小。

### <a name="distortion-error"></a>扭曲错误

HoloLens，在视频和仍图像流是未扭曲系统的映像处理管道中之前帧都提供给应用程序 （预览流包含原始失真的帧）。 由于仅投影矩阵将可用，应用程序必须假定图像帧表示完美 pinhole 照相机，但是变形纠正函数中的图像处理器可能仍将保留最多 10 个像素的错误时使用中的投影矩阵帧的元数据。 在许多用例，此错误将不起作用，但如果要对齐全息到实际海报/标记，例如，且您注意到 < 10px 偏移量 （大致为全息定位 2 米消失的 11 毫米） 此扭曲错误可能是原因。

## <a name="locatable-camera-usage-scenarios"></a>可定位照相机使用方案

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>在捕获时的世界中显示的照片或视频

设备相机帧附带"照相机 World"转换，用于显示准确的设备时图像捕获。 例如在 （CameraToWorld.MultiplyPoint(Vector3.zero)) 和甚至绘图小箭头方向照相机面向 (CameraToWorld.MultiplyVector(Vector3.forward)) 此位置开始位置小 holographic 图标。

### <a name="painting-the-world-using-a-camera-shader"></a>绘制世界上使用照相机着色器

在本部分中我们将创建材料着色器世界上基于在其中显示的设备照相机的视图中的颜色。 实际上我们将执行的操作是每个顶点将找出相对于照相机，其位置和每个像素然后将投影矩阵利用到图图像与相关联的纹素的扩展。 最后，和 （可选），我们将淡出的角映像使其看起来类似于操作之梦的内存的详细信息：

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

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
2. 查找[关联的功能点](#pixel-to-application-specified-coordinate-system)，并且其全球大气
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

### <a name="render-holograms-from-the-cameras-position"></a>呈现全息从照相机的位置

注意：如果你尝试创建您自己[混合现实捕获 (MRC)](mixed-reality-capture.md)，其中融合全息用照相机的流，则可以使用[MRC 效果](mixed-reality-capture-for-developers.md)或启用中的 showHolograms 属性[在 Unity 中的定位照相机](locatable-camera-in-unity.md)。

如果你想要执行特殊 RGB 照相机流上直接呈现，就可以呈现全息从照相机的位置的空间中以提供自定义全息图录制/实时预览视频源同步。

在 Skype，我们执行此操作以显示远程客户端 HoloLens 用户看到的内容，使他们可以与同一全息进行交互。 在发送前通过 Skype 服务每个视频帧内，我们将获取每个帧的相应相机数据。 我们然后包照相机的外部和内部元数据与视频帧，然后将其发送通过 Skype 服务。

在接收端，使用 Unity 中，我们已同步所有全息 HoloLens 用户空间使用相同的坐标系统中。 这使得我们可以使用照相机的外部元数据将 Unity 照相机放在 HoloLens 用户站着时捕获该视频的帧时，（相对于全息其余） 世界中的确切位置并使用的照相机内部函数信息请确保该视图相同。

一旦我们有摄像机正确设置，我们将组合照相机拖到框架上接收到来自 Skype，创建的 HoloLens 用户会看到使用 Graphics.Blit 混合的现实视图看到哪些全息。

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
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
