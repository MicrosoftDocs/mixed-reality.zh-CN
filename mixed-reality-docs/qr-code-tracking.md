---
title: 跟踪的 QR 代码
description: 了解如何启用跟踪您的 Windows Mixed Reality 沉浸式 (VR) 头戴式 QR 码和 VR 应用程序中实现的功能。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr lbe，基于位置娱乐、 vr 拱廊沉浸式拱廊，qr，qr 代码
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593071"
---
# <a name="qr-code-tracking"></a>跟踪的 QR 代码

在沉浸式 (VR) 耳机 Windows Mixed Reality 驱动程序中实现跟踪的 QR 代码。 通过启用耳机驱动程序中的 QR 代码跟踪器，耳机扫描 QR 码和它们报告给希望应用程序。 此功能才可用的[Windows 10 2018 年 10 月更新 (也称为 RS5)](release-notes-october-2018.md)。

>[!NOTE]
>这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。  这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> 跟踪的 QR 代码</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>启用和禁用 QR 代码跟踪您的头戴式
注意：本部分中时才有效[Windows 10 2018 年 10 月更新 (也称为 RS5)](release-notes-october-2018.md)。 从 19 h 1 及更高版本生成不需要执行此操作。
是否正在开发一个混合的现实应用，它将利用 QR 代码跟踪，或者你是其中一个应用的客户，你将需要手动开启跟踪耳机的驱动程序中的 QR 代码。

为了**开启 QR 代码跟踪**的沉浸式的 (VR) 耳机：

1. 关闭您的 PC 上的混合的现实门户应用。
2. 从您的 PC 耳机中拔出。
3. 在命令提示符处运行以下脚本：<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. 重新连接到您的 PC 将耳机。

为了**关闭跟踪的 QR 码**的沉浸式的 (VR) 耳机：

1. 关闭您的 PC 上的混合的现实门户应用。
2. 从您的 PC 耳机中拔出。
3. 在命令提示符处运行以下脚本：<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. 重新连接到您的 PC 将耳机。 这将使任何已发现的 QR 码"非定位。"

## <a name="printing-codes"></a>打印代码

最重要的是，[规范的 QR 代码](https://www.qrcode.com/en/howto/code.html)说"QR 代码符号区域需要边距或"无人参与区域"围绕其可用。 位置，其中会输出任何内容周围符号清除区域。 QR 代码需要在所有边的符号的四个模块宽边距。" 这需要有一个宽度大小的模块-在代码中的一个黑色方块四次，每个侧。 规范的页面包含有关如何打印 QR 代码并找出进行特定大小的 QR 代码所需的区域的建议。

QR 代码检测质量目前易受不同的照明和背景。 若要应对这种情况，请注意你照明并打印将相应的代码。 特别是亮照明场景中打印黑色灰色背景的代码。 在低光场景，黑色白色的工作原理。 同样，如果特别深色背景下的代码，尝试黑色灰色代码上的，如果检测率较低。 否则，如果浅色背景下，常规代码应正常工作。

## <a name="qrtracking-api"></a>QRTracking API

QRTracking 插件公开 Api，可用于跟踪的 QR 代码。 若要使用该插件，您将需要使用以下类型从*QRCodesTrackerPlugin*命名空间。

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

## <a name="implementing-qr-code-tracking-in-unity"></a>实现跟踪在 Unity 中的 QR 代码

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>示例 MRTK （混合现实工具包） 中的 Unity 场景

您可以找到有关如何使用混合现实工具包中的 QR 跟踪 API 示例[GitHub 站点](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)。

MRTK 已实现所需的脚本，以 simpilify QR 跟踪使用情况。 所有必要资产可开发 QR 跟踪应用程序位于"QRTracker"文件夹中。 有两个场景： 第一种是一个示例，用于检测到它们，以及第二个演示如何使用坐标系统附加到的 QR 代码以显示全息只需显示的 QR 代码的详细信息。
没有预设"QRScanner"添加到在后台使用 QRCodes 的所有必要 scrips。 脚本 QRCodeManager 是实现 QRCode API 可以将其添加到您的场景的 singileton 类。 脚本"AttachToQRCode"用于将全息附加到的 QR 码 coodridnate 系统，此脚本可以添加到任何你全息。 "SpatialGraphCoordinateSystem"显示了如何使用 QRCode 坐标系统。 因为是您项目的场景中，可以使用这些脚本也可以编写您自己直接使用的插件上文所述。

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>实现跟踪而无需 MRTK Unity 中的 QR 代码

您可以不依赖于 MRTK 的情况下在 Unity 中使用 QR 跟踪 API。 若要使用 API，需要准备你的项目使用以下指令：

1. 在名为 unity 项目的 assets 文件夹中创建一个新文件夹："插件"。
2. 从所有所需的文件复制[此文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)到刚创建的本地"插件"文件夹。
3. 可以使用跟踪中的脚本 QR [MRTK scripts 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)或编写自己的。
注意：仅对有这些插件[Windows 10 2018 年 10 月更新 (也称为 RS5)](release-notes-october-2018.md)生成。 将使用下一步的 windows 版本更新插件。 当前的插件是实验性和不能用于 windows 的未来版本。 新插件将发布可从下一个 windows 版本并且它们不会向后兼容和不会使用 RS5）。

## <a name="implementing-qr-code-tracking-in-directx"></a>实现在 DirectX 中跟踪的 QR 代码

若要在 Visual Studio 中使用 QRTrackingPlugin，您需要将 QRTrackingPlugin 引用添加到.winmd。 您可以找到[受支持的平台所需的文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)。

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

我们定义了与在左上角快速检测正方形的左上角处的 QR 代码对齐右侧坐标系统。 坐标系统如下所示。 Z 轴指向到文件 （未显示），但在 Unity 中的 z 轴是缺纸和惯用左手。

定义 SpatialCoordinateSystem 对齐如下所示。 可以从使用 API 的平台中获取此坐标系*Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*。

![QR 代码坐标系统](images/Qr-coordinatesystem.png) 

从 QRCode ^ 对象代码，下面的代码演示如何创建一个矩形，并将其放入 QR 坐标系统：

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

您可以使用的物理大小创建 QR 矩形：

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

坐标系统可用于绘制的 QR 代码或将全息附加到的位置：

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

同时，你*QRCodesTrackerPlugin::QRCodeAddedHandler*可能如下所示：

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

## <a name="troubleshooting-and-faq"></a>故障排除和常见问题解答

**常规故障排除**

* 为您的 PC 运行 Windows 10 2018 年 10 月更新？
* 已设置注册表项？ 之后重新启动设备？
* QR 代码版本是受支持的版本？ 当前 API 支持最多 QR 代码版本 20 个。 我们建议用于常规用途使用版本 5。 
* 关闭足以 QR 代码？ 照相机越接近 QR 码，可以支持更高版本的 QR 代码版本 API。  

**如何关闭需要到 QR 代码来检测它？**

这将取决于 QR 代码的大小，并且也是哪个版本。 对于从 5 cm 边 25 厘米边到不同的版本 1 QR 代码，最小检测距离范围从 0.15 计量到 0.5 米。 最远掉这些可以从检测到会从较小的 QR 代码目标的大约 0.3 指标 1.4 改为适用于更大。 为了比这更大的 QR 代码，您可以评估;大小的检测距离呈线性增加。 我们跟踪程序并不适用于使用边的 QR 代码小于 5 cm。

**使用徽标工作的 QR 代码？**

使用徽标的 QR 代码尚未经过测试，当前不受支持。

**如何清除的 QR 代码从我的应用程序以便它们不会保留？**

* 在启动会话中，才会保留的 QR 代码。 后重新启动 （或重新启动该驱动程序） 时，它们将进入并为新对象下一次检测到。
* QR 代码历史记录在系统级别上保存在驱动程序会话，但您可以将应用配置为忽略早于特定的时间戳的 QR 代码，如果你想。 当前 API 支持清除 QR 代码历史记录，如多个应用程序感兴趣的数据。

**RS5 和未来版本的插件不兼容**RS5 版本的插件仅适用于 RS5，而不能用于将来的版本。 Expermental 插件将替换为实际的插件，应是一个值，我们可以使用在将来版本的 windows。
