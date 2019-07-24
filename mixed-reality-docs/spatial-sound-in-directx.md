---
title: DirectX 中的空间音效
description: 使用 XAudio2 和 xAPO 音频库基于 DirectX 向 Windows Mixed Reality 应用添加空间声音。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality, 空间音效, 应用, XAudio2, 低级别, xAPO, 音频库, 演练, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550431"
---
# <a name="spatial-sound-in-directx"></a>DirectX 中的空间音效

使用[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)和[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)音频库基于 DirectX 向 Windows Mixed Reality 应用添加空间声音。

本主题使用来自 HolographicHRTFAudioSample 的示例代码。

>[!NOTE]
>本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT, 这与全息项目模板中使用的不同。  概念对于C++/WinRT 项目是等效的, 但你将需要转换代码。

## <a name="overview-of-head-relative-spatial-sound"></a>标题相对空间声音概述

空间音效实现为**音频处理对象 (APO)** , 该对象使用**头相关的传输函数 (HRTF)** 筛选器*spatialize*普通的音频流。

在 pch 中包含这些标头文件, 以访问音频 Api:
* XAudio2
* xapo
* hrtfapoapi

若要设置空间音效:
1. 调用[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)来初始化 HRTF 音频的新 APO。
2. 分配[HRTF 参数](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)和[HRTF 环境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)来定义空间音效 APO 的声音特征。
3. 设置用于 HRTF 处理的 XAudio2 引擎。
4. 创建[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)对象并调用[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)。

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>在 DirectX 应用中实现 HRTF 和空间音效

可以通过使用不同的参数和环境配置 HRTF APO 来实现各种效果。 使用以下代码来了解可能的情况。 从此处下载通用 Windows 平台代码示例:[空间音效示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

帮助器类型在这些文件中提供:
* [AudioFileReader](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):使用媒体基础和[IMFSourceReader 接口](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)加载音频文件。
* [XAudio2Helpers](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):实现**SetupXAudio2**函数以初始化用于 HRTF 处理的 XAudio2。

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>为全向源添加空间音效

用户周围的某些全息影像在所有方向上都是相同的。 下面的代码演示如何初始化 APO 以发出全向声音。 在此示例中, 我们将此概念应用于 Windows 全息应用模板中的旋转多维数据集。 有关完整的代码列表, 请参阅[OmnidirectionalSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)。

**窗口的空间声音引擎仅支持 48k samplerate 进行播放。大多数中间件程序 (如 Unity) 会自动将声音文件转换为所需的格式, 但如果你在音频系统中的较低级别上启动乱搞或进行自定义, 则请务必记住这一点, 以防出现崩溃或意外行为, 如HRTF 系统失败。**

首先, 我们需要初始化 APO。 在我们的全息示例应用程序中, 我们选择在**HolographicSpace**后执行此操作。

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

从*OmnidirectionalSound*执行 Initialize 的实现:

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

为 HRTF 配置 APO 后, 请在源语音上调用[开始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)播放音频。 在我们的示例应用程序中, 我们选择将其放在一个循环中, 以便你可以继续听到来自该立方体的声音。

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

从*OmnidirectionalSound*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

现在, 每当更新框架时, 都需要更新全息图相对于设备本身的位置。 这是因为, HRTF 的位置始终相对于用户的头表示, 包括头位置和方向。

若要在 HolographicSpace 中执行此操作, 我们需要构造一个转换矩阵, 从我们的 SpatialStationaryFrameOfReference 坐标系统到固定到设备本身的坐标系统。

From *HolographicHrtfAudioSampleMain:: Update ()* :

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

HRTF 位置直接应用于 OmnidirectionalSound 帮助器类的 APO 声音。

From *OmnidirectionalSound:: OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

就这么简单！ 继续阅读以了解有关如何通过 HRTF 音频和 Windows 全息执行的操作的详细信息。

### <a name="initialize-spatial-sound-for-a-directional-source"></a>初始化方向源的空间声音

用户周围的某些全息影像在同一方向上几乎发出声音。 此声音模式称为*cardioid* , 因为它看起来像卡通心。 下面的代码演示如何初始化 APO 以发出方向性声音。 有关完整的代码列表, 请参阅[CardioidSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 。

为 HRTF 配置 APO 后, 调用源语音上的 "[开始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)" 以播放音频。

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a>实现自定义衰减

您可以使用距离和/或其完全切断的距离来覆盖空间声音偏离的速率。 若要对空间声音实现自定义衰减行为, 请填充[HrtfDistanceDecay 结构](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx), 并在将其传递给[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)函数之前, 将其分配给[HrtfApoInit 结构](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)中的**distanceDecay**字段。

将以下代码添加到前面所示的**Initialize**方法, 以指定自定义的衰减行为。 有关完整的代码列表, 请参阅[CustomDecay](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)。

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
