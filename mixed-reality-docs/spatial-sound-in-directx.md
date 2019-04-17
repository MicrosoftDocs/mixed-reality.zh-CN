---
title: 在 DirectX 空间声音
description: 将空间声音添加到您通过 XAudio2 和 xAPO 音频库基于 DirectX 的 Windows Mixed Reality 应用程序。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实、 空间声音、 应用、 XAudio2，较低级别的 Windows xAPO、 音频库、 演练中，DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593076"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="74a0b-104">在 DirectX 空间声音</span><span class="sxs-lookup"><span data-stu-id="74a0b-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="74a0b-105">你通过基于 DirectX 的 Windows Mixed Reality 应用中添加空间声音[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)并[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)音频库。</span><span class="sxs-lookup"><span data-stu-id="74a0b-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="74a0b-106">本主题使用示例代码从 HolographicHRTFAudioSample。</span><span class="sxs-lookup"><span data-stu-id="74a0b-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="74a0b-107">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="74a0b-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="74a0b-108">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="74a0b-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="74a0b-109">头相对空间声音的概述</span><span class="sxs-lookup"><span data-stu-id="74a0b-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="74a0b-110">作为实现空间声音**音频处理对象 (APO)** ，它使用**head 相关传递函数 (HRTF)** 筛选出*spatialize*普通的音频流。</span><span class="sxs-lookup"><span data-stu-id="74a0b-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="74a0b-111">在 pch.h 中访问音频 Api 包括这些标头文件：</span><span class="sxs-lookup"><span data-stu-id="74a0b-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="74a0b-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="74a0b-112">XAudio2.h</span></span>
* <span data-ttu-id="74a0b-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="74a0b-113">xapo.h</span></span>
* <span data-ttu-id="74a0b-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="74a0b-114">hrtfapoapi.h</span></span>

<span data-ttu-id="74a0b-115">若要设置空间声音：</span><span class="sxs-lookup"><span data-stu-id="74a0b-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="74a0b-116">调用[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)来初始化新 APO HRTF 音频。</span><span class="sxs-lookup"><span data-stu-id="74a0b-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="74a0b-117">将分配[HRTF 参数](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)并[HRTF 环境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)定义空间的声音 APO 声学特性。</span><span class="sxs-lookup"><span data-stu-id="74a0b-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="74a0b-118">设置 HRTF 处理 XAudio2 引擎。</span><span class="sxs-lookup"><span data-stu-id="74a0b-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="74a0b-119">创建[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)对象，并调用[启动](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)。</span><span class="sxs-lookup"><span data-stu-id="74a0b-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="74a0b-120">在 DirectX 应用程序中实现 HRTF 和空间声音</span><span class="sxs-lookup"><span data-stu-id="74a0b-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="74a0b-121">可以通过使用不同的参数和环境配置 HRTF APO 实现各种效果。</span><span class="sxs-lookup"><span data-stu-id="74a0b-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="74a0b-122">使用以下代码来探索的可能性。</span><span class="sxs-lookup"><span data-stu-id="74a0b-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="74a0b-123">从此处下载通用 Windows 平台的代码示例：[声音空间示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="74a0b-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="74a0b-124">在这些文件中提供了帮助程序类型：</span><span class="sxs-lookup"><span data-stu-id="74a0b-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="74a0b-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):通过使用媒体基础加载音频文件和[IMFSourceReader 接口](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)。</span><span class="sxs-lookup"><span data-stu-id="74a0b-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="74a0b-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):实现**SetupXAudio2**函数来初始化 XAudio2 HRTF 处理。</span><span class="sxs-lookup"><span data-stu-id="74a0b-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="74a0b-127">添加为全向源空间声音</span><span class="sxs-lookup"><span data-stu-id="74a0b-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="74a0b-128">在用户的环境中某些全息发出声音同样在所有方向上。</span><span class="sxs-lookup"><span data-stu-id="74a0b-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="74a0b-129">下面的代码演示如何初始化 APO 发出全向声音。</span><span class="sxs-lookup"><span data-stu-id="74a0b-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="74a0b-130">在此示例中，我们这一概念于旋转多维数据集从应用的 Windows 全息版的应用程序模板。</span><span class="sxs-lookup"><span data-stu-id="74a0b-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="74a0b-131">有关完整代码列表，请参阅[OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)。</span><span class="sxs-lookup"><span data-stu-id="74a0b-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="74a0b-132">**窗口的空间声音引擎仅支持 48 k samplerate 进行播放。大多数中间件程序，如 Unity 中，会自动将声音文件转换为所需的格式，但如果您启动进行补充，以便在较低级别中音频系统或使自己，这一点非常重要，需要记住来防止发生崩溃或意外的行为等HRTF 系统出现故障。**</span><span class="sxs-lookup"><span data-stu-id="74a0b-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="74a0b-133">首先，我们需要初始化 APO。</span><span class="sxs-lookup"><span data-stu-id="74a0b-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="74a0b-134">在全息版示例应用，我们选择要执行此操作后，我们**HolographicSpace**。</span><span class="sxs-lookup"><span data-stu-id="74a0b-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="74a0b-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="74a0b-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="74a0b-136">实现的 Initialize，从*OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="74a0b-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="74a0b-137">为 HRTF 配置 APO 后，调用[启动](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)上源语音以播放音频。</span><span class="sxs-lookup"><span data-stu-id="74a0b-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="74a0b-138">在我们的示例应用，我们选择将其放在一个循环，以便可以继续听到声音来自多维数据集。</span><span class="sxs-lookup"><span data-stu-id="74a0b-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="74a0b-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="74a0b-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="74a0b-140">从*OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="74a0b-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="74a0b-141">现在，我们将更新此框架，只要我们需要更新全息图的位置相对于设备本身。</span><span class="sxs-lookup"><span data-stu-id="74a0b-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="74a0b-142">这是因为 HRTF 位置始终表示相对于用户的头，包括头位置和方向。</span><span class="sxs-lookup"><span data-stu-id="74a0b-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="74a0b-143">若要执行此操作在 HolographicSpace 中，我们需要构建到固定到设备本身的坐标系统从我们 SpatialStationaryFrameOfReference 坐标系统转换矩阵。</span><span class="sxs-lookup"><span data-stu-id="74a0b-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="74a0b-144">从*HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="74a0b-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="74a0b-145">HRTF 位置是直接应用于声音 APO OmnidirectionalSound 帮助器类。</span><span class="sxs-lookup"><span data-stu-id="74a0b-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="74a0b-146">从*OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="74a0b-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="74a0b-147">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="74a0b-147">That's it!</span></span> <span data-ttu-id="74a0b-148">继续阅读以了解有关如何使用 HRTF 音频和 Windows 全息版的详细信息。</span><span class="sxs-lookup"><span data-stu-id="74a0b-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="74a0b-149">初始化方向源空间声音</span><span class="sxs-lookup"><span data-stu-id="74a0b-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="74a0b-150">在用户的环境中某些全息发出声音主要在一个方向。</span><span class="sxs-lookup"><span data-stu-id="74a0b-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="74a0b-151">此声音的模式名为*cardioid*因为它类似于卡通核心。</span><span class="sxs-lookup"><span data-stu-id="74a0b-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="74a0b-152">下面的代码演示如何初始化 APO 发出定向声音。</span><span class="sxs-lookup"><span data-stu-id="74a0b-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="74a0b-153">有关完整代码列表，请参阅[CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 。</span><span class="sxs-lookup"><span data-stu-id="74a0b-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="74a0b-154">为 HRTF 配置 APO 后，调用[启动](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)上源语音以播放音频。</span><span class="sxs-lookup"><span data-stu-id="74a0b-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="74a0b-155">实现自定义的衰减</span><span class="sxs-lookup"><span data-stu-id="74a0b-155">Implement custom decay</span></span>

<span data-ttu-id="74a0b-156">您可以重写的空间声音脱落与距离和/或之间的距离其切掉完全的速率。</span><span class="sxs-lookup"><span data-stu-id="74a0b-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="74a0b-157">若要实现自定义的衰减行为空间的声音，填充[HrtfDistanceDecay 结构](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx)并将其分配给**distanceDecay**字段中[HrtfApoInit 结构](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)之前将其传递给[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)函数。</span><span class="sxs-lookup"><span data-stu-id="74a0b-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="74a0b-158">将以下代码添加到**初始化**前面所示指定自定义的衰减行为的方法。</span><span class="sxs-lookup"><span data-stu-id="74a0b-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="74a0b-159">有关完整代码列表，请参阅[CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)。</span><span class="sxs-lookup"><span data-stu-id="74a0b-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
