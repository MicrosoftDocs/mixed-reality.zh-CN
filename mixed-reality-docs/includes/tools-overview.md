# <a name="unity"></a>[<span data-ttu-id="fb631-101">Unity</span><span class="sxs-lookup"><span data-stu-id="fb631-101">Unity</span></span>](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="fb631-103">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="fb631-103">1. Download the latest version</span></span>

<span data-ttu-id="fb631-104">建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。</span><span class="sxs-lookup"><span data-stu-id="fb631-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span> 
* <span data-ttu-id="fb631-105">目前的建议是使用“Unity 2019”，这是下文的 MRTK v2 所需的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="fb631-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="fb631-106">如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。</span><span class="sxs-lookup"><span data-stu-id="fb631-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="fb631-107">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="fb631-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="fb631-109">[混合现实工具包](../mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="fb631-109">[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="fb631-110">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="fb631-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="fb631-111">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="fb631-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="fb631-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="fb631-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="fb631-113">**混合现实工具包 - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="fb631-113">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="fb631-114">如果你不想使用 Unity 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="fb631-114">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="fb631-115">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="fb631-115">Other tools [optional]</span></span>
* <span data-ttu-id="fb631-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="fb631-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="fb631-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="fb631-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="fb631-118">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="fb631-118">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="fb631-119">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="fb631-119">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="fb631-120">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="fb631-120">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="fb631-121">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="fb631-121">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="fb631-122">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="fb631-122">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="fb631-123">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="fb631-123">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="fb631-124">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="fb631-124">For HoloLens development</span></span>

<span data-ttu-id="fb631-125">在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="fb631-125">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="fb631-126">如果打算使用 [HoloLens 仿真器](../using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="fb631-126">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="fb631-127">若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="fb631-127">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="fb631-128">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="fb631-128">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="fb631-129">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="fb631-129">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="fb631-130">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="fb631-130">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="fb631-131">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="fb631-131">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="fb631-132">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="fb631-132">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="fb631-133">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="fb631-133">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="fb631-134">最低配置</span><span class="sxs-lookup"><span data-stu-id="fb631-134">Minimum</span></span></th><th> <span data-ttu-id="fb631-135">建议</span><span class="sxs-lookup"><span data-stu-id="fb631-135">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="fb631-136">处理器</span><span class="sxs-lookup"><span data-stu-id="fb631-136">Processor</span></span></td><td> <span data-ttu-id="fb631-137"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="fb631-137"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="fb631-138"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="fb631-138"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-139">GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-139">GPU</span></span></td><td> <span data-ttu-id="fb631-140"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-140"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="fb631-141"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-141"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-142">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="fb631-142">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="fb631-143">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="fb631-143">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-144">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="fb631-144">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="fb631-145">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="fb631-145">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-146">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="fb631-146">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="fb631-147">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="fb631-147">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-148">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="fb631-148">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="fb631-149">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="fb631-149">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-150">内存</span><span class="sxs-lookup"><span data-stu-id="fb631-150">Memory</span></span></td><td> <span data-ttu-id="fb631-151">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="fb631-151">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="fb631-152">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="fb631-152">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-153">存储</span><span class="sxs-lookup"><span data-stu-id="fb631-153">Storage</span></span></td><td colspan="2"> <span data-ttu-id="fb631-154">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="fb631-154">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-155">USB 端口</span><span class="sxs-lookup"><span data-stu-id="fb631-155">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="fb631-156">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="fb631-156">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-157">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="fb631-157">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="fb631-158">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="fb631-158">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="fb631-159">下一步操作</span><span class="sxs-lookup"><span data-stu-id="fb631-159">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb631-160">开始你的 Unity 之旅</span><span class="sxs-lookup"><span data-stu-id="fb631-160">Start your Unity journey</span></span>](../unity-development-overview.md)

# <a name="unreal"></a>[<span data-ttu-id="fb631-161">Unreal</span><span class="sxs-lookup"><span data-stu-id="fb631-161">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="fb631-163">1.下载最新版本</span><span class="sxs-lookup"><span data-stu-id="fb631-163">1. Download the latest version</span></span>

<span data-ttu-id="fb631-164">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="fb631-164">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="fb631-165">2.导入混合现实工具包 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="fb631-165">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="fb631-167">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="fb631-167">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="fb631-168">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="fb631-168">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="fb631-169">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="fb631-169">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="fb631-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="fb631-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="fb631-171">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="fb631-171">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="fb631-172">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="fb631-172">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="fb631-173">其他工具 [可选]</span><span class="sxs-lookup"><span data-stu-id="fb631-173">Other tools [optional]</span></span>
* <span data-ttu-id="fb631-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。</span><span class="sxs-lookup"><span data-stu-id="fb631-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="fb631-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。</span><span class="sxs-lookup"><span data-stu-id="fb631-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="fb631-176">3.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="fb631-176">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="fb631-177">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="fb631-177">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="fb631-178">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="fb631-178">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="fb631-179">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="fb631-179">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="fb631-180">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="fb631-180">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="fb631-181">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="fb631-181">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="fb631-182">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="fb631-182">For HoloLens development</span></span>

<span data-ttu-id="fb631-183">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="fb631-183">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="fb631-184">如果打算使用 [HoloLens 仿真器](../using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="fb631-184">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="fb631-185">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="fb631-185">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="fb631-186">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="fb631-186">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="fb631-187">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="fb631-187">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="fb631-188">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="fb631-188">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="fb631-189">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="fb631-189">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="fb631-190">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="fb631-190">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="fb631-191">最低配置</span><span class="sxs-lookup"><span data-stu-id="fb631-191">Minimum</span></span></th><th> <span data-ttu-id="fb631-192">建议</span><span class="sxs-lookup"><span data-stu-id="fb631-192">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="fb631-193">处理器</span><span class="sxs-lookup"><span data-stu-id="fb631-193">Processor</span></span></td><td> <span data-ttu-id="fb631-194"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="fb631-194"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="fb631-195"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="fb631-195"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-196">GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-196">GPU</span></span></td><td> <span data-ttu-id="fb631-197"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-197"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="fb631-198"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-198"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-199">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="fb631-199">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="fb631-200">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="fb631-200">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-201">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="fb631-201">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="fb631-202">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="fb631-202">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-203">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="fb631-203">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="fb631-204">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="fb631-204">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-205">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="fb631-205">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="fb631-206">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="fb631-206">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-207">内存</span><span class="sxs-lookup"><span data-stu-id="fb631-207">Memory</span></span></td><td> <span data-ttu-id="fb631-208">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="fb631-208">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="fb631-209">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="fb631-209">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-210">存储</span><span class="sxs-lookup"><span data-stu-id="fb631-210">Storage</span></span></td><td colspan="2"> <span data-ttu-id="fb631-211">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="fb631-211">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-212">USB 端口</span><span class="sxs-lookup"><span data-stu-id="fb631-212">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="fb631-213">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="fb631-213">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-214">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="fb631-214">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="fb631-215">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="fb631-215">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="fb631-216">下一步操作</span><span class="sxs-lookup"><span data-stu-id="fb631-216">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb631-217">开始你的 Unreal 之旅</span><span class="sxs-lookup"><span data-stu-id="fb631-217">Start your Unreal journey</span></span>](../unreal-development-overview.md)

# <a name="native-openxr"></a>[<span data-ttu-id="fb631-218">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="fb631-218">Native (OpenXR)</span></span>](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

<span data-ttu-id="fb631-220">原生 OpenXR 开发没有可供下载的引擎。</span><span class="sxs-lookup"><span data-stu-id="fb631-220">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="fb631-221">可在 [OpenXR 入门](../openxr-getting-started.md)文档中找到开始开发所需的全部内容。</span><span class="sxs-lookup"><span data-stu-id="fb631-221">You can find everything you need to begin development in the [Getting started with OpenXR](../openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="fb631-222">1.设置电脑来进行混合现实开发</span><span class="sxs-lookup"><span data-stu-id="fb631-222">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="fb631-223">Windows 10 SDK 在 Windows 10 操作系统上效果最佳。</span><span class="sxs-lookup"><span data-stu-id="fb631-223">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="fb631-224">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。</span><span class="sxs-lookup"><span data-stu-id="fb631-224">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="fb631-225">请注意，并非所有工具都在较早的操作系统上受支持。</span><span class="sxs-lookup"><span data-stu-id="fb631-225">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="fb631-226">对于 HoloLens 开发</span><span class="sxs-lookup"><span data-stu-id="fb631-226">For HoloLens development</span></span>

<span data-ttu-id="fb631-227">如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。</span><span class="sxs-lookup"><span data-stu-id="fb631-227">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="fb631-228">如果打算使用 [HoloLens 仿真器](../using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="fb631-228">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="fb631-229">如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。</span><span class="sxs-lookup"><span data-stu-id="fb631-229">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="fb631-230">你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。</span><span class="sxs-lookup"><span data-stu-id="fb631-230">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="fb631-231">确保满足以下要求（具体由你的需求而定）。</span><span class="sxs-lookup"><span data-stu-id="fb631-231">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="fb631-232">沉浸式 (VR) 头戴显示设备要求</span><span class="sxs-lookup"><span data-stu-id="fb631-232">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="fb631-233">以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。</span><span class="sxs-lookup"><span data-stu-id="fb631-233">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="fb631-234">不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。</span><span class="sxs-lookup"><span data-stu-id="fb631-234">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="fb631-235">如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="fb631-235">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="fb631-236">某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。</span><span class="sxs-lookup"><span data-stu-id="fb631-236">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="fb631-237">最低配置</span><span class="sxs-lookup"><span data-stu-id="fb631-237">Minimum</span></span></th><th> <span data-ttu-id="fb631-238">建议</span><span class="sxs-lookup"><span data-stu-id="fb631-238">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="fb631-239">处理器</span><span class="sxs-lookup"><span data-stu-id="fb631-239">Processor</span></span></td><td> <span data-ttu-id="fb631-240"><b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</span><span class="sxs-lookup"><span data-stu-id="fb631-240"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="fb631-241"><b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</span><span class="sxs-lookup"><span data-stu-id="fb631-241"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-242">GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-242">GPU</span></span></td><td> <span data-ttu-id="fb631-243"><b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-243"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="fb631-244"><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</span><span class="sxs-lookup"><span data-stu-id="fb631-244"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-245">GPU 驱动程序 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="fb631-245">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="fb631-246">WDDM 2.2 驱动程序</span><span class="sxs-lookup"><span data-stu-id="fb631-246">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-247">散热设计功耗</span><span class="sxs-lookup"><span data-stu-id="fb631-247">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="fb631-248">15W 或更高</span><span class="sxs-lookup"><span data-stu-id="fb631-248">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-249">图形显示端口</span><span class="sxs-lookup"><span data-stu-id="fb631-249">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="fb631-250">1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</span><span class="sxs-lookup"><span data-stu-id="fb631-250">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-251">显示器分辨率</span><span class="sxs-lookup"><span data-stu-id="fb631-251">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="fb631-252">分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</span><span class="sxs-lookup"><span data-stu-id="fb631-252">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-253">内存</span><span class="sxs-lookup"><span data-stu-id="fb631-253">Memory</span></span></td><td> <span data-ttu-id="fb631-254">8 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="fb631-254">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="fb631-255">16 GB 或更高的 RAM</span><span class="sxs-lookup"><span data-stu-id="fb631-255">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-256">存储</span><span class="sxs-lookup"><span data-stu-id="fb631-256">Storage</span></span></td><td colspan="2"> <span data-ttu-id="fb631-257">&gt;10 GB 的额外可用空间</span><span class="sxs-lookup"><span data-stu-id="fb631-257">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-258">USB 端口</span><span class="sxs-lookup"><span data-stu-id="fb631-258">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="fb631-259">1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="fb631-259">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="fb631-260">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="fb631-260">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="fb631-261">蓝牙 4.0（用于连接配件）</span><span class="sxs-lookup"><span data-stu-id="fb631-261">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="fb631-262">下一步操作</span><span class="sxs-lookup"><span data-stu-id="fb631-262">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb631-263">开始你的原生开发之旅</span><span class="sxs-lookup"><span data-stu-id="fb631-263">Start your Native journey</span></span>](../directx-development-overview.md)


