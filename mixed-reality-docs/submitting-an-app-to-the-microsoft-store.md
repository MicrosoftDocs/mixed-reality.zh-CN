---
title: 将应用提交到 Microsoft Store
description: 本文介绍了如何将混合现实应用程序提交到 Microsoft Store，包括如何打包和测试应用程序，以及如何在应用商店中对应用程序的可发现性进行认证和帮助。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 应用程序，uwp，提交，提交，筛选器，元数据，系统要求，关键字，wack，证书，包，appx，销售情况
ms.openlocfilehash: f2eb4093a2bea51d8c39b94d23777e426810981e
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375804"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>将应用提交到 Microsoft Store

[HoloLens](hololens-hardware-details.md)和 WINDOWS 10 PC 均支持[沉浸式耳机](immersive-headset-hardware-details.md)运行通用 Windows 平台应用。 无论是提交支持 HoloLens 的应用还是同时提交两者，都可以通过[合作伙伴中心](https://partner.microsoft.com/dashboard)将应用提交到 Microsoft Store。

如果还没有合作伙伴中心开发人员帐户，可[立即注册](https://developer.microsoft.com/store/register)。

## <a name="packaging-a-mixed-reality-app"></a>打包混合现实应用

### <a name="prepare-image-assets-included-in-the-appx"></a>准备包含在 appx 中的映像资产

Appx 构建工具需要多个映像资产，以便将应用程序构建到 appx 包以提交到存储区。 你可以在 MSDN 上详细了解[磁贴和图标资产的准则](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)。

| 所需资产 | 建议的缩放 | 图像格式 | 此显示在何处？ | 
|----------|----------|----------|------------------|
| 方块字71x71 徽标 | 任何 |  PNG | 不可用 | 
| 方块字150x150 徽标 | 150x150 （100% scale）或225x225 （150%） | PNG | 开始 pin 和所有应用（如果未提供310x310）、存储搜索建议、商店列表页、商店浏览、商店搜索 | 
|  宽310x150 徽标 |  任何  |  PNG  |  不可用 | 
|  应用商店徽标 |  75x75 （150% 刻度）  |  PNG  |  合作伙伴中心，报表应用，编写评审，我的媒体库 | 
|  初始屏幕 |  930x450 （150% 刻度）  |  PNG  |  2D 应用启动器（石板） | 

此外，还提供了 HoloLens 可以利用的一些建议资产。

| 推荐的资产 | 建议的缩放 | 此显示在何处？ | 
|----------|----------|----------|
|  方块字310x310 徽标 |  310x310 （150% 刻度） |  启动 pin 和所有应用 | 

### <a name="live-tile-requirements"></a>动态磁贴要求

HoloLens 上的 "开始" 菜单将使用最大的包含正方形磁贴图像。

你可能会发现，Microsoft 发布的某些应用程序的应用程序具有3D 启动器。 开发人员可以使用[这些说明](implementing-3d-app-launchers.md)为其应用程序添加3d 启动器。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定 Windows 的目标和最低版本

如果混合现实应用包含特定于特定 Windows 版本的功能，则必须指定通用 Windows 应用程序将支持的目标和最低平台版本。

**对于面向[Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)（要求至少需要 Windows 10 秋季创意者更新（10.0;版本16299）才能正常工作。**

当你在 Visual Studio 中创建新的通用 Windows 项目时，系统将提示你设置 Windows 的目标和最低版本。 您还可以在 "项目" 菜单中更改现有项目的此设置，然后在下拉菜单的底部 "< 应用程序名称的 > 属性"。

在 Visual Studio 2019 中 ![设置最低和目标平台版本](images/visual-studio-min-version-500px.png)<br>
在 Visual Studio 中设置最低平台版本和目标平台版本

### <a name="specifying-target-device-families"></a>指定目标设备系列

Windows Mixed Reality 应用程序（适用于[HoloLens](hololens-hardware-details.md)和[沉浸式耳机](immersive-headset-hardware-details.md)）是通用 Windows 平台的一部分，因此，[目标设备系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)为 "Windows 通用" 的任何应用包都能够使用沉浸式耳机在 HoloLens 或 Windows 10 电脑上运行。 也就是说，如果未在应用程序清单中指定目标设备系列，可能会无意中打开应用程序，使其不会出现意外的 Windows 10 设备。 按照下面的步骤指定所需的 Windows 10 设备系列，然后在["合作伙伴中心" 中上传应用程序包时，仔细检查是否选择了正确的设备系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

若要在 Visual Studio 中设置此字段，请右键单击 appxmanifest.xml，然后选择 "查看代码"，找到 "y" 名称字段。 默认情况下，它可能如下所示：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果你的应用是为**HoloLens**创建的，则可以通过指定 "Windows 全息版" 目标设备系列来确保它仅安装在 hololens 上。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果你的应用程序需要特定于使用**HoloLens 2**的功能，如目视跟踪或手动跟踪，则可以通过指定目标设备系列 "windows 版" 和 "MinVersion 10.0.18362.0" 来确保它面向 Windows 版本18362或更高版本。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

如果你的应用是为**Windows Mixed Reality 沉浸式耳机**创建的，则可以通过指定目标设备系列 "Desktop" 和 MinVersion of "10.0.16299.0"，确保它仅安装在 Windows 10 计算机上（Windows mixed reality 需要此更新）。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最后，如果你的应用程序应在**HoloLens 和 Windows Mixed Reality 沉浸式耳机**上运行，你可以确保此应用仅可用于这两个设备家族，并同时通过为每个目标设备系列包含其各自的最小值来确保每个目标为正确的最小 Windows 版本。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

若要了解有关面向设备家族的详细信息，请阅读[y UWP 文档](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)。

### <a name="associate-app-with-the-store"></a>将应用与应用商店关联

从 Visual Studio 解决方案的 "项目" 菜单中，选择 "应用商店 > 将应用与应用商店相关联"。 如果执行了此操作，则可在应用中测试购买和通知方案。 当你将应用程序与应用商店关联时，这些值将下载到本地计算机上当前项目的应用程序清单文件中：
* 包显示名称
* 包名称
* 发布者 ID
* 发布者显示名称
* 版本

如果通过创建清单的自定义 .xml 文件重写默认的 package.appxmanifest 文件，则无法将应用与应用商店关联。 如果尝试将自定义清单文件与应用商店关联，则显示一条错误消息。

### <a name="creating-an-upload-package"></a>创建上传包

按照[打包适用于 windows 10 的通用 windows 应用程序中的](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)准则。

创建上传包的最后一步是使用[Windows 应用认证](#windows-app-certification-kit)包验证包。

如果要将专用于 HoloLens 的包添加到其他 Windows 10 设备家族上提供的现有产品，还需要了解[版本编号可能会如何影响哪些包交付给特定客户](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)，以及[如何将包分发到不同的操作系统](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)。

一般原则是，适用于设备的最高版本号包将是存储区分发的包。

如果有一个 Windows 通用包和一个 Windows. 全息包，并且 Windows 通用包具有较高的版本号，则 HoloLens 用户将下载更高版本的 Windows 通用包，而不是 Windows 全息版。软件包. 有几种解决方案，此问题：
1. 确保特定于平台的包（如 Windows. 全息）的版本号比平台无关包（如 Windows 通用）的版本号更高。
2. 如果还具有特定于平台的包，请不要将应用打包为 Windows。通用包-改为将 Windows 通用包打包为要在其上提供的特定平台

>[!NOTE]
> 若要在 HoloLens （第一代）和 HoloLen 2 上支持你的应用，你将需要上传两个应用包;一个包含适用于 HoloLens 的 x86 （第一代），另一个包含用于 HoloLens 2 的 ARM 或 ARM64。 
> 
> 如果在包中同时包含 ARM 和 ARM64，则会在 HoloLens 2 上使用 ARM64 版本。 

>[!NOTE]
> 可以声明单个包，使其适用于多个目标设备系列

3. 创建跨所有平台工作的单个 Windows 通用包。 目前尚不支持此操作，因此建议使用上述解决方案。

## <a name="testing-your-app"></a>测试应用

### <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

通过 Visual Studio 创建要提交到合作伙伴中心的应用包时，"创建应用程序包" 向导会提示你针对创建的包运行 Windows 应用认证工具包。 若要对应用程序进行平滑的提交，最好先验证[Windows 应用程序认证工具包](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx)是否会在将应用程序提交到应用商店之前，在本地计算机上对其进行测试。 当前不支持在远程 HoloLens 上运行 Windows 应用程序认证包。

### <a name="run-on-all-targeted-device-families"></a>在所有目标设备系列上运行

使用 Windows 通用平台，您可以创建跨所有 Windows 10 设备系列运行的单一应用程序。 但是，它并不保证通用 Windows 应用程序将只在所有设备家族上工作。 在您选择在 HoloLens 或其他任何 Windows 10 目标设备系列上提供您的应用程序之前，请务必在每个设备家族上[测试该应用程序](testing-your-app-on-hololens.md)，以确保获得良好的体验。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>将混合现实应用提交到应用商店

如果要提交基于 Unity 项目的混合现实应用，请先观看此[视频](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)。

通常，提交在 HoloLens 和/或沉浸式耳机上运行的 Windows Mixed Reality 应用就像将任何 UWP 应用提交到 Microsoft Store。 [通过保留应用名称创建应用](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)后，应遵循[UWP 提交清单](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。

首先要做的就是为混合现实体验[选择类别和子类别](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table)。 务必**为应用选择最准确的类别**，以便可以将应用程序注册到正确的商店类别，并确保它使用相关搜索查询显示。 **将您的 VR 标题列为游戏不会使您的应用程序获得更好的曝光，** 并且可能会阻止其显示在更具可容纳性和更拥挤的类别中。

但在提交过程中，有四个重要方面需要进行特定于现实的特定选择：
1. 在 "[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)" 下的 " **[产品声明](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** " 部分。
2. 在 "[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)" 下的 " **[系统要求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** " 部分。
3. "[包](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)" 下的 " **[设备系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** " 部分。
4. 几个 **[商店列表页](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 字段。

### <a name="mixed-reality-product-declarations"></a>混合现实产品声明

在应用提交过程的 " **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** " 页上，可以在 " **[产品声明](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** " 部分中找到几个与混合现实相关的选项。

![混合现实产品声明](images/product-declarations-900px.png)<br>
混合现实产品声明

首先，需要确定应用为其提供混合现实体验的设备类型。 这可确保应用程序包含在存储区中的 Windows Mixed Reality 集合中，并可在连接沉浸式耳机后（或在 HoloLens 上浏览应用商店时）用户浏览存储。

"这一体验是针对 Windows Mixed Reality 设计的："
* 仅当沉浸式耳机连接到用户的电脑时，才应选中 " **PC** " 框。 你应该选中此框，无论你的应用程序是专为在沉浸式头戴式耳机上运行而设计的，还是当耳机连接时提供混合现实模式和/或附赠内容的标准 PC 游戏/应用程序。
* 仅当你的应用程序在 HoloLens 上运行时提供了全息体验时，才检查**hololens**框。
* 如果你的应用程序在两个设备类型上都提供混合现实体验（如版本2017中的[混合现实学院 "Project 孤岛" 应用](mixed-reality-250.md)），请选中**这两个**框。

如果选择上述 "PC"，则需要设置 "混合现实设置" （活动级别）。 这仅适用于在连接到沉浸式头设备的 Pc 上运行的混合现实体验，因为 HoloLens 上的混合现实应用是全球规模的，用户在安装过程中未定义边界。
* 如果你的应用程序的设计目的是让用户保持在一个位置（例如，你在飞机的考核中心的游戏），请选择 "**固定**"。
* 如果你的应用程序的设计目的是让用户在安装过程中定义的边界内浏览，则选择 "**所有体验**" （例如，你可能会在其中进行逐步操作并有可能会发生减减攻击的游戏）。

### <a name="mixed-reality-system-requirements"></a>混合现实系统要求

在应用提交过程的 " **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** " 页上，可以在 " **[系统要求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** " 部分中找到几个与混合现实相关的选项。

![系统要求](images/system-reqs-800px.png)<br>
系统要求

在本部分中，你将确定混合现实应用的最低（必需）硬件和推荐（可选）硬件。

**输入硬件：**

如果你的应用程序支持**麦克风**（适用于[语音输入](voice-input.md)）、 **[Xbox 控制器或游戏板](hardware-accessories.md#bluetooth-gamepads)** 和/或 **[Windows Mixed Reality 运动控制器](motion-controllers.md)** ，请使用复选框来告知潜在客户。 此信息将显示在应用商店中的应用程序的产品详细信息页上，可帮助你的应用程序包含在适当的应用/游戏集合中（例如，对于支持运动控制器的所有游戏，可能存在一个集合）。

为输入类型选择 "最低硬件" 或 "推荐的硬件" 复选框。 

例如： 
* 如果游戏需要运动控制器，但通过麦克风接受语音输入，请选择 "Windows Mixed Reality 运动控制器" 旁边的 "最小硬件" 复选框，但 "麦克风" 旁边的 "推荐的硬件" 复选框。 
* 如果可以使用 Xbox 控制器/游戏板或运动控制器播放游戏，则可以选择 "Xbox 控制器或游戏板" 旁边的 "最小硬件" 复选框，并选择 "Windows Mixed Reality 运动控制器" 旁边的 "推荐的硬件" 复选框，因为运动控制器可能会在游戏板上提供一个步骤。

**Windows Mixed Reality 沉浸式耳机：**

指示是否需要沉浸式耳机来使用你的应用，或是否可选，这对于客户满意度和教育至关重要。

如果你的应用*只能*通过沉浸式耳机使用，请选择 "Windows Mixed Reality 沉浸式耳机" 旁边的 "最小硬件" 复选框。 这会显示在应用程序中应用程序的产品详细信息页上，在 "购买" 按钮上显示为警告，因此客户不会认为他们购买的应用程序将在其电脑上运行，如传统桌面应用程序。

如果你的应用程序在桌面上运行，如传统的 PC 应用程序，但在连接沉浸式头戴式耳机时提供了 VR 体验（无论应用的完整内容是可用还是仅部分），请选中 "Windows Mixed Reality" 旁边的 "推荐的硬件" 复选框。沉浸式耳机。 " 如果你的应用程序在未连接沉浸式头戴式的情况下作为传统桌面应用程序运行，则不会出现任何警告。

**PC 规范：**

如果你希望你的应用程序尽可能多地访问 Windows Mixed reality 沉浸式耳机用户，则需要将[Windows Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的 PC 规格作为集成图形的[目标](understanding-performance-for-mixed-reality.md)。

无论混合现实应用的 Windows Mixed Reality 计算机要求最小，还是需要特定的 PC 配置（如[Windows Mixed Reality 超 pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的专用 GPU），都应在 "最低硬件" 列中指出具有相关 PC 规范。

如果混合现实应用旨在更好地执行，或在特定 PC 配置或图形卡上提供更高分辨率的图形，则应在 "推荐的硬件" 列中指出具有相关的 PC 规范。

仅当混合现实应用使用连接到电脑的沉浸式头戴式耳机时，此情况才适用。 如果混合现实应用仅在 HoloLens 上运行，则无需指示 PC 规范，因为 HoloLens 只有一个硬件配置。

### <a name="device-family-availability"></a>设备系列可用性

如果已在 Visual Studio 中[正确打包了应用](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements)，则在应用提交过程的 "包" 页上上传该应用时，应生成一个表，其中标识了你的应用将可用于哪些设备系列。

![设备家族可用性表](images/device-family-table-900px.png)<br>
设备家族可用性表

如果混合现实应用适用于沉浸式耳机，则应在表中选择至少 "Windows 10 桌面"。 如果你的混合现实应用在 HoloLens 上工作，则应至少选择 "Windows 10 全息版"。 如果你的应用程序在两个 Windows Mixed Reality 耳机类型上运行，例如[混合现实学院 "Project 孤岛" 应用](mixed-reality-250.md)，则应选择 "Windows 10 桌面" 和 "Windows 10 全息版"。

>[!TIP]
>许多开发人员在上载其应用包时出现错误，这些错误与 "合作伙伴中心" 中的包清单与你的应用/发布者帐户信息的不匹配相关。 通过使用与你的 Windows 开发人员帐户（用于登录合作伙伴中心的帐户）相关联的同一帐户登录到 Visual Studio，通常可以避免这些错误。 如果你使用相同的帐户，则在打包应用程序之前，你可以将应用与其在 Microsoft Store 中的标识相关联。

![将应用程序与 Microsoft Store 相关联](images/associate-your-app-700px.png)<br>
在 Visual Studio 中将应用与 Microsoft Store 相关联

### <a name="store-listing-page"></a>商店列表页

在应用提交过程的 "应用[商店列表](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings)" 页上，可以添加有关混合现实应用的有用信息。

>[!IMPORTANT]
>若要确保应用程序正确地分类了应用程序并将其视为 Windows Mixed Reality 客户，应将 **"Windows Mixed Reality"** 添加为应用的 "搜索词" 之一（可以通过展开 "共享字段" 部分找到搜索词）。

![将 Windows Mixed Reality 添加到搜索词](images/search-terms-800px.png)<br>
向搜索词添加 "Windows Mixed Reality"

## <a name="offering-a-free-trial-for-your-game-or-app"></a>为游戏或应用提供免费试用版

许多使用者在购买 Windows Mixed Reality 沉浸式耳机之前，不会受到虚拟现实的任何经验限制。 他们可能不知道强烈游戏中的预期，并且可能不熟悉沉浸式体验中自身的舒适阈值。 许多客户还可能会尝试在未徽章为[Windows Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的电脑上使用 Windows mixed reality 沉浸式耳机。 出于上述考虑，强烈建议您考虑为付费混合现实应用或游戏提供[免费试用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial)。

## <a name="see-also"></a>另请参阅
* [混合现实](mixed-reality.md)
* [开发概述](development.md)
* [应用视图](app-views.md)
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [Unity 性能建议](performance-recommendations-for-unity.md)
* [在 HoloLens 上测试应用](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最小电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
