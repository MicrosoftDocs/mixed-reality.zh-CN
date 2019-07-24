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
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="ba05a-104">DirectX 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="ba05a-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="ba05a-105">使用[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx)和[xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx)音频库基于 DirectX 向 Windows Mixed Reality 应用添加空间声音。</span><span class="sxs-lookup"><span data-stu-id="ba05a-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="ba05a-106">本主题使用来自 HolographicHRTFAudioSample 的示例代码。</span><span class="sxs-lookup"><span data-stu-id="ba05a-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="ba05a-107">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT, 这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="ba05a-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="ba05a-108">概念对于C++/WinRT 项目是等效的, 但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="ba05a-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="ba05a-109">标题相对空间声音概述</span><span class="sxs-lookup"><span data-stu-id="ba05a-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="ba05a-110">空间音效实现为**音频处理对象 (APO)** , 该对象使用**头相关的传输函数 (HRTF)** 筛选器*spatialize*普通的音频流。</span><span class="sxs-lookup"><span data-stu-id="ba05a-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="ba05a-111">在 pch 中包含这些标头文件, 以访问音频 Api:</span><span class="sxs-lookup"><span data-stu-id="ba05a-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="ba05a-112">XAudio2</span><span class="sxs-lookup"><span data-stu-id="ba05a-112">XAudio2.h</span></span>
* <span data-ttu-id="ba05a-113">xapo</span><span class="sxs-lookup"><span data-stu-id="ba05a-113">xapo.h</span></span>
* <span data-ttu-id="ba05a-114">hrtfapoapi</span><span class="sxs-lookup"><span data-stu-id="ba05a-114">hrtfapoapi.h</span></span>

<span data-ttu-id="ba05a-115">若要设置空间音效:</span><span class="sxs-lookup"><span data-stu-id="ba05a-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="ba05a-116">调用[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)来初始化 HRTF 音频的新 APO。</span><span class="sxs-lookup"><span data-stu-id="ba05a-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="ba05a-117">分配[HRTF 参数](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx)和[HRTF 环境](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx)来定义空间音效 APO 的声音特征。</span><span class="sxs-lookup"><span data-stu-id="ba05a-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="ba05a-118">设置用于 HRTF 处理的 XAudio2 引擎。</span><span class="sxs-lookup"><span data-stu-id="ba05a-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="ba05a-119">创建[IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx)对象并调用[Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ba05a-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="ba05a-120">在 DirectX 应用中实现 HRTF 和空间音效</span><span class="sxs-lookup"><span data-stu-id="ba05a-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="ba05a-121">可以通过使用不同的参数和环境配置 HRTF APO 来实现各种效果。</span><span class="sxs-lookup"><span data-stu-id="ba05a-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="ba05a-122">使用以下代码来了解可能的情况。</span><span class="sxs-lookup"><span data-stu-id="ba05a-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="ba05a-123">从此处下载通用 Windows 平台代码示例:[空间音效示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="ba05a-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="ba05a-124">帮助器类型在这些文件中提供:</span><span class="sxs-lookup"><span data-stu-id="ba05a-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="ba05a-125">[AudioFileReader](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp):使用媒体基础和[IMFSourceReader 接口](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)加载音频文件。</span><span class="sxs-lookup"><span data-stu-id="ba05a-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="ba05a-126">[XAudio2Helpers](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h):实现**SetupXAudio2**函数以初始化用于 HRTF 处理的 XAudio2。</span><span class="sxs-lookup"><span data-stu-id="ba05a-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="ba05a-127">为全向源添加空间音效</span><span class="sxs-lookup"><span data-stu-id="ba05a-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="ba05a-128">用户周围的某些全息影像在所有方向上都是相同的。</span><span class="sxs-lookup"><span data-stu-id="ba05a-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="ba05a-129">下面的代码演示如何初始化 APO 以发出全向声音。</span><span class="sxs-lookup"><span data-stu-id="ba05a-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="ba05a-130">在此示例中, 我们将此概念应用于 Windows 全息应用模板中的旋转多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ba05a-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="ba05a-131">有关完整的代码列表, 请参阅[OmnidirectionalSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)。</span><span class="sxs-lookup"><span data-stu-id="ba05a-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="ba05a-132">**窗口的空间声音引擎仅支持 48k samplerate 进行播放。大多数中间件程序 (如 Unity) 会自动将声音文件转换为所需的格式, 但如果你在音频系统中的较低级别上启动乱搞或进行自定义, 则请务必记住这一点, 以防出现崩溃或意外行为, 如HRTF 系统失败。**</span><span class="sxs-lookup"><span data-stu-id="ba05a-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="ba05a-133">首先, 我们需要初始化 APO。</span><span class="sxs-lookup"><span data-stu-id="ba05a-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="ba05a-134">在我们的全息示例应用程序中, 我们选择在**HolographicSpace**后执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ba05a-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="ba05a-135">From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="ba05a-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="ba05a-136">从*OmnidirectionalSound*执行 Initialize 的实现:</span><span class="sxs-lookup"><span data-stu-id="ba05a-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="ba05a-137">为 HRTF 配置 APO 后, 请在源语音上调用[开始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)播放音频。</span><span class="sxs-lookup"><span data-stu-id="ba05a-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="ba05a-138">在我们的示例应用程序中, 我们选择将其放在一个循环中, 以便你可以继续听到来自该立方体的声音。</span><span class="sxs-lookup"><span data-stu-id="ba05a-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="ba05a-139">From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="ba05a-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="ba05a-140">从*OmnidirectionalSound*:</span><span class="sxs-lookup"><span data-stu-id="ba05a-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="ba05a-141">现在, 每当更新框架时, 都需要更新全息图相对于设备本身的位置。</span><span class="sxs-lookup"><span data-stu-id="ba05a-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="ba05a-142">这是因为, HRTF 的位置始终相对于用户的头表示, 包括头位置和方向。</span><span class="sxs-lookup"><span data-stu-id="ba05a-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="ba05a-143">若要在 HolographicSpace 中执行此操作, 我们需要构造一个转换矩阵, 从我们的 SpatialStationaryFrameOfReference 坐标系统到固定到设备本身的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="ba05a-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="ba05a-144">From *HolographicHrtfAudioSampleMain:: Update ()* :</span><span class="sxs-lookup"><span data-stu-id="ba05a-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="ba05a-145">HRTF 位置直接应用于 OmnidirectionalSound 帮助器类的 APO 声音。</span><span class="sxs-lookup"><span data-stu-id="ba05a-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="ba05a-146">From *OmnidirectionalSound:: OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="ba05a-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="ba05a-147">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="ba05a-147">That's it!</span></span> <span data-ttu-id="ba05a-148">继续阅读以了解有关如何通过 HRTF 音频和 Windows 全息执行的操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ba05a-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="ba05a-149">初始化方向源的空间声音</span><span class="sxs-lookup"><span data-stu-id="ba05a-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="ba05a-150">用户周围的某些全息影像在同一方向上几乎发出声音。</span><span class="sxs-lookup"><span data-stu-id="ba05a-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="ba05a-151">此声音模式称为*cardioid* , 因为它看起来像卡通心。</span><span class="sxs-lookup"><span data-stu-id="ba05a-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="ba05a-152">下面的代码演示如何初始化 APO 以发出方向性声音。</span><span class="sxs-lookup"><span data-stu-id="ba05a-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="ba05a-153">有关完整的代码列表, 请参阅[CardioidSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 。</span><span class="sxs-lookup"><span data-stu-id="ba05a-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="ba05a-154">为 HRTF 配置 APO 后, 调用源语音上的 "[开始](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)" 以播放音频。</span><span class="sxs-lookup"><span data-stu-id="ba05a-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="ba05a-155">实现自定义衰减</span><span class="sxs-lookup"><span data-stu-id="ba05a-155">Implement custom decay</span></span>

<span data-ttu-id="ba05a-156">您可以使用距离和/或其完全切断的距离来覆盖空间声音偏离的速率。</span><span class="sxs-lookup"><span data-stu-id="ba05a-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="ba05a-157">若要对空间声音实现自定义衰减行为, 请填充[HrtfDistanceDecay 结构](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx), 并在将其传递给[CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx)函数之前, 将其分配给[HrtfApoInit 结构](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx)中的**distanceDecay**字段。</span><span class="sxs-lookup"><span data-stu-id="ba05a-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="ba05a-158">将以下代码添加到前面所示的**Initialize**方法, 以指定自定义的衰减行为。</span><span class="sxs-lookup"><span data-stu-id="ba05a-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="ba05a-159">有关完整的代码列表, 请参阅[CustomDecay](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)。</span><span class="sxs-lookup"><span data-stu-id="ba05a-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
