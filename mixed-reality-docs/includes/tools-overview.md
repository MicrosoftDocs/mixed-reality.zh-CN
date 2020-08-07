# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1.下载最新版本

建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。 
* 目前的建议是使用“Unity 2019”，这是下文的 MRTK v2 所需的 LTS 版本。
* 如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.导入混合现实工具包 (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

[混合现实工具包](../mrtk-getting-started.md) (MRTK) 是一个用于混合现实应用程序的开源跨平台开发工具包。 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**混合现实工具包 - Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果你不想使用 Unity 的 MRTK，则需要自行编写所有交互和行为的脚本。

#### <a name="other-tools-optional"></a>其他工具 [可选]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。 

> [!NOTE]
> 你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。 如果打算使用 [HoloLens 仿真器](../using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](../using-the-hololens-emulator.md)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

#### <a name="immersive-vr-headset-requirements"></a>沉浸式 (VR) 头戴显示设备要求

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 建议</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

### <a name="whats-next"></a>下一步操作

> [!div class="nextstepaction"]
> [开始你的 Unity 之旅](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1.下载最新版本

建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2.导入混合现实工具包 (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**混合现实工具包 - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。

#### <a name="other-tools-optional"></a>其他工具 [可选]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合现实伴侣工具包 (GitHub)</a> - 代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，但可通过与它们配对生成面向 Windows Mixed Reality 的体验。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合现实工具包 - 通用 (GitHub)</a> - 共享脚本和组件的集合。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。 

> [!NOTE]
> 你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

如果要设置开发电脑来进行 HoloLens 开发，请确保满足 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。 如果打算使用 [HoloLens 仿真器](../using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

#### <a name="immersive-vr-headset-requirements"></a>沉浸式 (VR) 头戴显示设备要求

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 建议</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

### <a name="whats-next"></a>下一步操作

> [!div class="nextstepaction"]
> [开始你的 Unreal 之旅](../unreal-development-overview.md)

# <a name="native-openxr"></a>[原生 (OpenXR)](#tab/native)

 ![原生应用开发](../images/native_logo_banner.png)

原生 OpenXR 开发没有可供下载的引擎。 可在 [OpenXR 入门](../openxr-getting-started.md)文档中找到开始开发所需的全部内容。

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

如果要设置开发电脑来进行 HoloLens 开发，请确保满足 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系统要求。 如果打算使用 [HoloLens 仿真器](../using-the-hololens-emulator.md)，还需要确保电脑满足 [HoloLens 仿真器系统要求](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

> [!NOTE]
> 你可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。

#### <a name="immersive-vr-headset-requirements"></a>沉浸式 (VR) 头戴显示设备要求

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 建议</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

### <a name="whats-next"></a>下一步操作

> [!div class="nextstepaction"]
> [开始你的原生开发之旅](../directx-development-overview.md)


