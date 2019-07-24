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
# <a name="qr-code-tracking"></a>QR 代码跟踪

QR 代码跟踪在用于沉浸式 (VR) 耳机的 Windows Mixed Reality 驱动程序中实现。 通过启用耳机驱动程序中的 QR 代码跟踪程序, 耳机会扫描 QR 码, 并报告给感兴趣的应用程序。 此功能仅在[Windows 10 年10月2018更新 (也称为 RS5)](release-notes-october-2018.md)中可用。

>[!NOTE]
>本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT, 这与全息项目模板中使用的不同。  概念对于C++/WinRT 项目是等效的, 但你将需要转换代码。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>QR 代码跟踪</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>启用和禁用耳机代码跟踪
注意:本部分仅适用于[Windows 10 十月2018更新 (也称为 RS5)](release-notes-october-2018.md)。 从19h1 开始, 你无需执行此操作。
无论你是要开发将利用 QR 代码跟踪的混合现实应用, 还是你是其中一个应用的客户, 你都需要在耳机的驱动程序中手动打开 QR 代码跟踪。

若要为沉浸式 (VR) 耳机**启用 QR 码跟踪, 请**执行以下操作:

1. 在电脑上关闭混合现实门户应用。
2. 从 PC 中拔出耳机。
3. 在命令提示符下运行以下脚本:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. 将您的耳机重新连接到您的 PC。

若要为沉浸式 (VR) 耳机**关闭 QR 码跟踪, 请**执行以下操作:

1. 在电脑上关闭混合现实门户应用。
2. 从 PC 中拔出耳机。
3. 在命令提示符下运行以下脚本:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. 将您的耳机重新连接到您的 PC。 这会使发现的任何 QR 码 "不可定位"。

## <a name="printing-codes"></a>打印代码

首先, [qr 码规范](https://www.qrcode.com/en/howto/code.html)显示 "qr 码符号区需要使用边距或" 安静区 "才能使用它。 边距是符号周围的空白区域, 不会打印任何内容。 QR 代码要求符号的所有边都有四个模块宽的边距。 " 这需要在每一端有一个模块大小的四倍的宽度-代码中的单个黑色方形。 "规范" 页包含有关如何打印 QR 码的建议, 以及如何确定所需的区域来确定所需的大小的 QR 码。

当前, QR 码检测质量容易产生不同的照明和背景。 要对付这一点, 请注意您的照明, 并打印相应的代码。 在具有特别明亮的光线的场景中, 打印灰色背景上的黑色代码。 在低亮度场景下, 黑色打开。 同样, 如果代码的背景更暗, 则如果检测频率较低, 请尝试使用黑色的灰色代码。 否则, 如果背景较轻, 则常规代码应正常工作。

## <a name="qrtracking-api"></a>QRTracking API

QRTracking 插件为 QR 代码跟踪公开 Api。 若要使用插件, 你将需要使用*QRCodesTrackerPlugin*命名空间中的以下类型。

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

## <a name="implementing-qr-code-tracking-in-unity"></a>在 Unity 中实现 QR 代码跟踪

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>MRTK 中的示例 Unity 场景 (混合现实工具包)

可在混合现实工具包[GitHub 网站](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)中找到有关如何使用 QR 跟踪 API 的示例。

MRTK 已实现所需的脚本来 simpilify QR 跟踪使用情况。 开发 QR 跟踪应用程序所需的所有资产都位于 "QRTracker" 文件夹中。 有两种场景: 第一种是在检测到 QR 码的详细信息时, 只显示其详细信息, 第二个示例演示如何使用连接到 QR 代码的坐标系来显示全息影像。
有一个 prefab 的 "QRScanner", 它将所有必需的脚本添加到要使用 QRCodes 的场景中。 脚本 QRCodeManager 是实现 QRCode API 的单一实例类。 这需要添加到场景中。 脚本 "AttachToQRCode" 用于将全息影像附加到 QR 码坐标系统, 可以将此脚本添加到任何全息影像。 "SpatialGraphCoordinateSystem" 显示了如何使用 QRCode 坐标系统。 这些脚本可以在项目场景中按原样使用, 也可以直接使用插件自行编写, 如上所述。

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>在不 MRTK 的 Unity 中实现 QR 代码跟踪

你还可以在 Unity 中使用 QR 跟踪 API, 而无需依赖于 MRTK。 若要使用该 API, 你将需要使用以下指令准备你的项目:

1. 在 unity 项目的 "资产" 文件夹中创建一个名为的新文件夹:"插件"。
2. 将[此文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)中的所有所需文件复制到刚创建的本地 "插件" 文件夹中。
3. 你可以使用[MRTK scripts 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)中的 QR 跟踪脚本或编写你自己的脚本。
注意:这些插件仅适用于[Windows 10 十月2018更新 (也称为 RS5)](release-notes-october-2018.md)生成。 插件将在下一个 windows 版本中更新。 当前插件是实验性的, 不能用于将来的 windows 版本。 新插件将发布, 可从下一 windows 版本中使用, 并且不会向后兼容, 并且不会与 RS5 配合使用)。

## <a name="implementing-qr-code-tracking-in-directx"></a>在 DirectX 中实现 QR 代码跟踪

若要在 Visual Studio 中使用 QRTrackingPlugin, 需要将 QRTrackingPlugin 的引用添加到 winmd。 可在此处找到[受支持的平台所需的文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)。

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

## <a name="getting-a-coordinate-system"></a>获取坐标系统

我们定义一个右侧坐标系统, 它与左上角快速检测方块左上角的 QR 码对齐。 坐标系统如下所示。 Z 轴指向纸张 (未显示), 但在 Unity 中, z 轴不在纸张上并左手。

定义的 SpatialCoordinateSystem 如下所示。 可使用 API Windows 从平台获取此坐标系统: *:P erception:: 空间::P 查看:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*。

![QR 码坐标系统](images/Qr-coordinatesystem.png) 

从 QRCode ^ Code 对象开始, 下面的代码演示如何创建一个矩形, 并将其放入 QR 坐标系统:

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

可以使用物理尺寸来创建 QR 矩形:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

坐标系统可用于绘制 QR 码, 或将全息影像附加到该位置:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

完全一样, *QRCodesTrackerPlugin:: QRCodeAddedHandler*的外观可能如下所示:

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

## <a name="troubleshooting-and-faq"></a>故障排除和常见问题

**常规故障排除**

* 你的电脑是否在运行 Windows 10 十月2018更新？
* 是否设置了注册表项？ 之后重新启动了设备？
* QR 代码版本是否是受支持的版本？ 当前 API 最多支持 QR 代码版本20。 建议使用版本5进行一般使用。 
* 您是否接近 QR 码？ 照相机的位置越接近于 QR 码, API 可以支持的 QR 码版本就越高。  

**我需要关闭 QR 码才能对其进行检测？**

这将取决于 QR 码的大小以及它的版本。 对于版本 1 QR 码, 从 5 cm 端到 25 cm 方, 最小检测距离范围为0.15 米到0.5 米。 从大约0.3 米开始, 可以检测到的最远的 QR 码目标为更大的 QR 码1.4 目标。 对于大于此值的 QR 码, 可以估算;大小的检测距离线性增加。 跟踪器不能使用边缘小于 5 cm 的 QR 码。

**带有徽标的 QR 码是否起作用？**

带有徽标的 QR 码尚未经过测试, 当前不受支持。

**如何实现清除应用程序中的 QR 码, 因此它们不会保留？**

* QR 码仅保留在启动会话中。 重新启动 (或重新启动驱动程序) 后, 它们将不再被检测为新对象。
* QR 代码历史记录保存在驱动程序会话的系统级别, 但您可以将应用程序配置为忽略特定时间戳之前的 QR 码 (如果需要)。 目前, API 支持清除 QR 码历史记录, 因为多个应用可能对数据感兴趣。

**RS5 和未来版本的插件不兼容**RS5 版本的插件仅适用于 RS5, 不适用于将来的版本。 Expermental 插件将替换为实际插件, 并且应该是我们可以在未来版本的 windows 中使用的插件。
