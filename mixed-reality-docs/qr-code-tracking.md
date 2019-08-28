---
title: QR 代码跟踪
description: 了解如何在 HoloLens 2 上检测 QR 码。
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr, lbe, 基于位置的娱乐, vr 拱廊类, 拱廊类, 沉浸, qr, qr 码, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047159"
---
# <a name="qr-code-tracking"></a>QR 代码跟踪

HoloLens 2 可以检测头戴显示在环境中的 QR 码, 在每个代码的实际位置建立一个坐标系统。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens（第一代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> QR 码检测</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">请参阅说明</td>
</tr>
</table>

>[!NOTE]
>以下 NuGet 包目前不支持在台式计算机上支持沉浸式 Windows Mixed Reality 耳机。  请继续关注桌面支持的更多更新。

## <a name="getting-the-qr-package"></a>获取 QR 包
可在[此处](https://github.com/dorreneb/mixed-reality/releases)下载用于 QR 码检测的 NuGet 包。

此包的未来版本将通过公共 NuGet 包存储库提供。

## <a name="detecting-qr-codes"></a>检测 QR 码

### <a name="adding-the-webcam-capability"></a>添加网络摄像机功能
需要将功能`webcam`添加到清单以检测 QR 码。 此功能是必需的, 因为用户环境中检测到的代码中的数据可能包含敏感信息。

可以通过调用`QRCodeWatcher.RequestAccessAsync()`来请求权限:

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

构造 QRCodeWatcher 对象之前应请求权限。

尽管 QR 码检测需要`webcam`功能, 但使用设备的跟踪相机进行检测。 与设备的照片/视频 (PV) 摄像机相比, 此功能可提供更广泛的检测 FOV 和更好的电池寿命。

### <a name="detecting-qr-codes-in-unity"></a>检测 Unity 中的 QR 码

你可以使用 Unity 中的 QR 代码检测 API, 而无需依赖于 MRTK。 为此, 必须执行以下操作:

1. 使用名称*插件*在 unity 项目的 "资产" 文件夹中创建一个新文件夹。
2. 将此文件夹中的所有所需文件复制到刚创建的本地 "插件" 文件夹中。

这里有一个示例 Unity 应用, 其中显示了一个全息的 "QR 码" 代码, 以及关联的数据, 如 GUID、物理大小、时间戳和解码的数据。 此应用可以位于 https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes 。

### <a name="detecting-qr-codes-in-c"></a>检测 QR 码C++

>[!NOTE]
>本文C++中的代码片段当前演示了如何使用C++/cx 而不是 C + 17 兼容C++/WinRT, 这与[ C++全息项目模板](creating-a-holographic-directx-project.md)中使用的不同。 概念对于C++/WinRT 项目是等效的, 但你需要转换代码。

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>获取 QR 码的坐标系统

每个检测到的 QR 码都公开一个[空间坐标系统](coordinate-systems.md), 该系统与左上角快速检测方块左上角的 QR 码对齐, 如下所示。  当直接使用 QR SDK 时, Z 轴指向纸张 (未显示)-转换为 Unity 坐标时, Z 轴指向纸张, 并按左手。

QR 码的 SpatialCoordinateSystem 会对齐。 可以通过调用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a>并传入代码的 SpatialGraphNodeId, 从平台中获取此坐标系统。

![QR 码坐标系统](images/Qr-coordinatesystem.png) 

对于 QRCode 对象, 以下C++/cx 代码演示了如何创建矩形并使用 QR 码的坐标系统放置它:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

可以使用物理尺寸来创建 QR 矩形:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

坐标系统可用于绘制 QR 码, 或将全息影像附加到该位置:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

完全一样, *QRCodeWatcher:: QRCodeAddedHandler*的外观可能如下所示:

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
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

## <a name="best-practices-for-qr-code-detection"></a>QR 码检测的最佳实践

### <a name="quiet-zones-around-qr-codes"></a>关于 QR 码的安静区

若要正确读取, QR 码需要代码两侧的边距。 此边距不能包含任何打印内容, 并且应为四个模块 (代码中的单个黑色方块) 宽度。 

[QR 规范](https://www.qrcode.com/en/howto/code.html)包含有关 quiet 区域的详细信息。

### <a name="lighting-and-backdrop"></a>照明和背景
QR 码检测质量容易产生不同的照明和背景。 

在具有特别明亮的光线的场景中, 打印灰色背景上的黑色代码。 否则, 在白色背景上打印黑色 QR 码。

如果代码的背景非常暗, 请尝试使用黑色的灰色代码 (如果检测频率较低)。 如果背景相对较轻, 则常规代码应正常工作。

### <a name="size-of-qr-codes"></a>QR 码的大小
Windows Mixed Reality 设备不适用于每个边小于 5 cm 的 QR 码。

对于5到 10 cm 长度之间的 QR 码, 必须非常接近检测代码。 它还需要更长的时间来检测此大小的代码。 

检测代码的确切时间不仅取决于 QR 码的大小, 还取决于代码的距离。 接近代码会有助于偏移大小问题。

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR 代码的距离和角度位置
跟踪相机只能检测到特定级别的详细信息。 对于真正的小 < 代码, 10cm, 您必须非常接近。 对于版本 1 QR 码, 从10到 25 cm 的范围内, 最小检测距离范围为0.15 米到0.5 米。 

大小的检测距离线性增加。 

QR 检测适用于一系列角度 + = 45deg。 这是为了确保我们有合适的分辨率来检测代码。

### <a name="qr-codes-with-logos"></a>带有徽标的 QR 码
带有徽标的 QR 码尚未经过测试, 当前不受支持。

### <a name="managing-qr-code-data"></a>管理 QR 码数据
Windows Mixed Reality 设备检测驱动程序的系统级别的 QR 码。 设备重新启动后, 检测到的 QR 码已消失, 并将在下次重新检测为新对象。

建议将应用程序配置为忽略特定时间戳之前的 QR 码。 目前, API 不支持清除 QR 码历史记录。

### <a name="qr-code-placement-in-a-space"></a>空格中的 QR 码位置
有关在何处以及如何放置 QR 码的建议, 请参阅[HoloLens 环境注意事项](environment-considerations-for-hololens.md)。

## <a name="qr-api-reference"></a>QR API 参考

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>请参阅
* [坐标系统](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>