---
title: 提交到 Microsoft Store 应用
description: 本文提供有关提交到 Microsoft Store，包括如何打包和测试应用程序和提示，以通过认证并在您的应用程序存储区中的可发现性帮助你混合的现实应用程序的提示。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 应用程序中，uwp，提交，提交、 筛选器、 元数据、 系统要求、 关键字、 wack、 证书、 包、 appx、 促销活动
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592158"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>提交到 Microsoft Store 应用

这两[HoloLens](hololens-hardware-details.md)和 Windows 10 电脑增强你[沉浸式头戴式](immersive-headset-hardware-details.md)运行通用 Windows 平台应用。 是否要提交支持 HoloLens 或 PC （或两者） 的应用，你会将应用提交到通过 Microsoft Store[合作伙伴中心](https://partner.microsoft.com/dashboard)。

如果还没有合作伙伴中心开发人员帐户，则可以[立即注册](https://developer.microsoft.com/store/register)。

## <a name="packaging-a-mixed-reality-app"></a>打包的混合的现实应用

### <a name="prepare-image-assets-included-in-the-appx"></a>准备 appx 中包含的图像资产

有几个工具生成 appx 生成到 appx 包提交到应用商店应用程序所需的图像资产。 可以深入了解[磁贴和图标资产的指导原则](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)MSDN 上。

| 所需的资产 | 建议的规模 | 图像格式 | 这被显示位置？ | 
|----------|----------|----------|------------------|
| 正方形 71x71 徽标 | Any |  PNG | 不可用 | 
| 正方形 150x150 徽标 | 150 x 150 （100%缩放） 或 225 x 225 （150%缩放） | PNG | （如果未提供 310 x 310） 启动 pin 和所有应用、 浏览应用商店搜索建议，存储区列表页上，应用商店，应用商店搜索 | 
|  150 宽徽标 |  Any  |  PNG  |  不可用 | 
|  应用商店徽标 |  75 x 75 （150%缩放）  |  PNG  |  合作伙伴中心，报表应用，回顾一下，我的库 | 
|  初始屏幕 |  930 x 450 （150%缩放）  |  PNG  |  2D 应用启动器 （静态图像） | 

也有 HoloLens 可以利用的一些建议的资产。

| 建议的资产 | 建议的规模 | 这被显示位置？ | 
|----------|----------|----------|
|  正方形 310x310 徽标 |  310 x 310 （150%缩放） |  启动 pin 和所有应用 | 

### <a name="live-tile-requirements"></a>实时磁贴要求

HoloLens 上的开始菜单将使用的最大的包含的正方形图块图像。

您可能会看到一些由 Microsoft 发布的应用具有其应用程序的 3D 启动。 开发人员可以将其应用使用三维启动器[这些说明](implementing-3d-app-launchers.md)。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定目标和最低版本的 Windows

如果 mixed 的 reality 应用包含特定于 Windows 的某个版本的功能，则必须指定目标和通用 Windows 应用程序将支持的最低平台版本。

**这尤其适用于面向应用程序[Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)，至少需要 Windows 10 Fall Creators Update (10.0;内部版本 16299） 才能正常工作。**

系统将提示您若要在 Visual Studio 中创建新的通用 Windows 项目时设置的目标和最低版本的 Windows。 此外可以在底部的下拉列表菜单更改此设置为现有项目中的"项目"菜单，然后"< 应用名称的 > 属性"。

![设置最小并面向 Visual Studio 2017 中的平台版本](images/visual-studio-min-version-500px.png)<br>
设置最小并面向 Visual Studio 中的平台版本

### <a name="specifying-target-device-families"></a>指定目标设备系列

Windows Mixed Reality 应用程序 (同时[HoloLens](hololens-hardware-details.md)并[沉浸式耳机](immersive-headset-hardware-details.md)) 是通用 Windows 平台，因此任何应用包的一部分[目标设备系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)的"Windows.Universal"是支持的沉浸式耳机 HoloLens 或 Windows 10 电脑上运行。 不过，如果未指定目标设备系列应用程序清单中您可能会无意中打开你最多意外的 Windows 10 设备的应用。 请按照以下步骤来指定预期的 Windows 10 设备系列，然后[请仔细检查上传你在合作伙伴中心以提交到应用商店的应用程序包时选择正确的设备系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

若要在 Visual Studio 中设置此字段，右键单击 Package.appxmanifest 并选择"查看代码"，然后查找 TargetDeviceFamily 名称字段。 默认情况下，它可能类似以下形式：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的应用程序创建的**HoloLens**，则可以确保它仅上是否安装了 HoloLens 通过指定"Windows.Holographic"目标设备系列。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的应用程序创建的**Windows Mixed Reality 沉浸式耳机**，则可以确保它仅上是否安装了 Windows 10 电脑的 Windows 10 Fall Creators Update （所必需的 Windows Mixed Reality） 通过指定目标设备系列"Windows.Desktop"和"10.0.16299.0"MinVersion。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最后，如果您的应用程序旨在上同时运行**HoloLens 和 Windows Mixed Reality 沉浸式耳机**，可以确保应用仅可供这些两个设备系列，同时确保每个目标的正确通过包括其各自的 MinVersion 与每个目标设备系列的行的最低 Windows 版本。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

你可以了解有关目标设备系列通过阅读详细[TargetDeviceFamily UWP 文档](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)。

### <a name="associate-app-with-the-store"></a>将应用与应用商店关联

从 Visual Studio 解决方案中的项目菜单中，选择"应用商店 > 关联应用程序与应用商店关联"。 如果这样做，您可以在应用中测试购买和通知方案。 关联时您的应用程序与应用商店，这些值将被下载到应用清单文件的当前项目在本地计算机上：
* 包显示名称
* 包名称
* 发布者 ID
* 发布者显示名称
* Version

如果您通过创建清单的自定义.xml 文件重写默认的 package.appxmanifest 文件，不能将您的应用程序与应用商店相关联。 如果你尝试将自定义清单文件与应用商店相关联，您将看到一条错误消息。

### <a name="creating-an-upload-package"></a>创建上传包

请遵循在指导原则[打包通用 Windows 应用程序适用于 Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)。

创建上传包的最后一步就验证程序包使用[Windows 应用认证工具包](#windows-app-certification-kit)。

如果您将包专门针对 HoloLens 添加到现有产品，可在其他 Windows 10 设备系列上，您还需要了解[版本号可能会如何影响哪些包传递到特定的客户](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)，并[如何将包分发到不同的操作系统](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)。

一般原则是，适用于设备的最高版本数字包将是一个由应用商店分发。

如果没有 Windows.Universal 包和 Windows.Holographic 包并且 Windows.Universal 包具有更高版本的版本号，HoloLens 用户将下载的更高版本编号 Windows.Universal 包而不是 Windows.Holographic包。 有几种解决方案，此问题：
1. 确保在平台特定的包，例如 Windows.Holographic 始终具有更高版本的版本号高于如 Windows.Universal 中平台不可知的程序包
2. 进行不作为 Windows.Universal 包应用还具有平台特定的包-如果改为包所需上可用的特定平台的 Windows.Universal 包

>[!NOTE]
> 您可以声明一个包适用于多个目标设备系列

3. 创建可跨所有平台工作的单一 Windows.Universal 包。 此支持并不出色现在因此，建议使用更高版本的解决方案。

## <a name="testing-your-app"></a>测试您的应用程序

### <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

在创建应用程序包以提交到合作伙伴中心通过 Visual Studio 时，创建应用程序包向导将提示您创建的包对运行 Windows 应用认证工具包。 为了到应用商店获得平滑提交过程，最好是确保[Windows 应用认证工具包测试](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx)在本地计算机上将它们提交到存储之前对您的应用程序传递。 当前不支持远程 HoloLens 上运行 Windows 应用认证工具包。

### <a name="run-on-all-targeted-device-families"></a>所有目标的设备系列上运行

Windows 通用平台，可创建跨所有 Windows 10 设备系列都运行的单个应用程序。 但是，它并不能保证通用 Windows 应用程序会在所有设备系列上正常工作。 你选择以使您的应用程序可在 HoloLens 或其他任何 Windows 10 目标设备系列上之前，务必你[测试应用程序](testing-your-app-on-hololens.md)上每个这些设备系列，以确保良好的体验。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>将混合的现实应用提交到应用商店

如果您要提交基于 Unity 项目的混合的现实应用，请参阅此[视频](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)第一个。

一般情况下，提交 Windows Mixed Reality 应用，适用于 HoloLens 和/或沉浸式耳机就像任何 UWP 应用提交到 Microsoft Store。 后[通过保留其名称来创建您的应用程序](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)，应遵循[UWP 提交清单](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。

将完成的首要任务之一是[选择一个类别和子类别](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table)混合的现实体验。 非常重要，您**选择您的应用程序的最准确类别**，以便我们可以销售正确存储类别中的应用程序并确保它使用相关搜索查询会显示。 **游戏不会导致更好地展示您的应用程序，如列出 VR 标题**和可能会阻止其显示类别中具有多个调整和更低的拥挤。

但是，你将想要进行混合的现实特定选择提交过程中有四个主要领域：
1. 在中 **[产品声明](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 部分下 [属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)。
2. 在中 **[系统要求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** 部分下 [属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)。
3. 在中 **[设备系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** 部分下 [包](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)。
4. 在多个 **[应用商店一览页面](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 字段。

### <a name="mixed-reality-product-declarations"></a>混合的现实产品声明

上 **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 页上的应用程序提交过程，您会发现多个选项与混合现实中相关 **[产品声明](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** 部分。

![混合的现实产品声明](images/product-declarations-900px.png)<br>
混合的现实产品声明

首先，你将想要确定您的应用程序中提供了混合的现实体验的设备类型。 这可确保您的应用程序纳入 Windows Mixed Reality 集合在存储区，并提供给用户浏览应用商店连接沉浸式头戴式后 （或浏览 HoloLens 上的存储时）。

下一步"这种体验专为 Windows Mixed Reality 上:"
* 检查**PC**框仅在您的应用程序提供了 VR 体验，当沉浸式头戴式耳机连接到用户的 PC。 应选中此框是否您的应用程序以独占方式用于沉浸式头戴式上运行，或如果它是一个标准 PC 游戏/应用，它提供了混合的现实模式和/或附加内容，当连接了耳机。
* 检查**HoloLens**框仅在您的应用程序提供了全息版体验在 HoloLens 上运行时。
* 检查**两者**框，如果您的应用程序提供了混合的现实体验在这两种设备类型，如[混合的现实学院"项目 Island"应用](mixed-reality-250.md)从 Build 2017。

如果选择了"PC"更高版本，您将想要将"mixed 的 reality 安装设置"（活动级别）。 这仅适用于在连接到沉浸式耳机，如上 HoloLens 混合的现实应用是全球规模和用户不会在安装过程中定义的边界的 Pc 运行的混合的现实体验。
* 选择**关注 + 现有**如果您的应用程序设计与用户一直保持在一个位置 （一个示例是一个游戏您坐在飞机考核中心） 中的意图。
* 选择**所有体验**如果您的应用程序旨在与用户走围绕他或她在安装过程中定义的边界内的意图 (一个示例可能是游戏 where 可以端步骤和鸭子类型来避开攻击)。

### <a name="mixed-reality-system-requirements"></a>混合的现实系统要求

上 **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** 页上的应用程序提交过程，您会发现多个选项与混合现实中相关 **[系统要求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** 部分。

![系统要求](images/system-reqs-800px.png)<br>
系统要求

在本部分中，您会将确定最小 （必需） 的硬件和建议 （可选） 硬件 for mixed 的 reality 应用。

**输入的硬件：**

使用复选框，向潜在客户是否支持您的应用程序**麦克风**(对于[语音输入](voice-input.md))，  **[Xbox 控制器或游戏板](hardware-accessories.md#bluetooth-gamepads)**，和/或 **[Windows Mixed Reality 运动控制器](motion-controllers.md)**。 此信息会显示在存储区中的应用程序的产品详细信息页上，并将帮助您获取相应的应用程序/游戏集合中包含的应用程序 （例如，集合可能存在的所有支持运动控制器的游戏）。

是精心选择"最小硬件"或"推荐的硬件"的输入类型对应的复选框。 

例如： 
* 如果您的游戏需要运动控制器，但接受通过麦克风的语音输入，选择"Windows Mixed 的 Reality 运动控制器"旁边的"最小硬件"复选框，但"建议的硬件"复选框旁边"麦克风。 
* 如果与 Xbox 控制器/游戏板或动画控制器，可以播放您的游戏，您可能会选择"Xbox 控制器或游戏板"旁边的"最小硬件"复选框并选择"Windows Mixed 的 Reality 传输旁边的"建议的硬件"复选框控制器的"为运动控制器很可能将从游戏板提供升级许可的经验。

**Windows Mixed Reality 沉浸式头戴式：**

指示沉浸式头戴式需使用你的应用，还是是可选的对客户满意度和教育至关重要。

如果您的应用程序能够*仅*沉浸式头戴式通过使用中，选择"Windows Mixed 的 Reality 沉浸式头戴式。"旁边的"最小硬件"复选框 这不会出现在应用商店中的应用程序的产品详细信息页上为购买按钮上方警告使客户认为他们打算购买的应用程序将像传统桌面应用程序自己的 PC 上起作用。

如果你的应用等传统的 PC 应用程序，在桌面上运行，但当沉浸式头戴式连接时提供 VR 体验 （您的应用程序的完整内容是否可用，或仅有部分），选择"Windows Mixed Reality 旁边的"建议的硬件"复选框沉浸式头戴式。" 不会出现警告不会出现购买按钮上方应用程序的产品详细信息页上如果应用函数作为传统的桌面应用，而无需沉浸式头戴式连接。

**PC 规范：**

如果你希望应用来访问尽可能多的 Windows Mixed Reality 沉浸式头戴式用户，您需[目标](understanding-performance-for-mixed-reality.md)PC 规范[使用集成图形 Windows 混合现实电脑](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。

混合的现实应用面向的最低 Windows 混合现实 PC 要求，还是需要特定的 PC 配置 (如专用的 GPU [Windows Mixed Reality Ultra PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)，应指示与相关"最小硬件"列中的 PC 规范。

如果混合的现实应用旨在提高性能，或提供更高分辨率的图形，特定的 PC 的配置或图形卡上应与"建议的硬件"列中的相关 PC 规范来指示的。

这仅适用于你的混合的现实应用使用连接到电脑的沉浸式头戴式耳机。 如果你的混合的现实应用只能在 HoloLens 上运行，不会需要指示 PC 规范，如 HoloLens 具有只有一个硬件配置。

### <a name="device-family-availability"></a>设备系列可用性

如果您已经[正确打包您的应用程序](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements)在 Visual Studio 中，将其上传应用程序提交过程的包页面上应生成标识的设备系列的类别将可供您的应用程序的表。

![设备系列可用性表](images/device-family-table-900px.png)<br>
设备系列可用性表

如果混合的现实应用的工作方式在沉浸式耳机，然后在表中应选择最少"Windows 10 桌面"。 如果混合的现实应用的工作方式在 HoloLens，然后在最少"Windows 10 全息版"应选择。 如果您的应用程序在这两种 Windows Mixed Reality 耳机类型上运行，例如[混合的现实学院"项目 Island"应用](mixed-reality-250.md)，应选择"Windows 10 桌面版"和"Windows 10 全息版"。

>[!TIP]
>上传其应用程序的包与包清单中合作伙伴中心的应用/发布者帐户信息之间的不匹配时，许多开发人员将会出现错误。 使用与你的 Windows 开发人员帐户 （用于登录到合作伙伴中心的一个） 关联的同一帐户登录到 Visual Studio，通常可以避免这些错误。 如果使用相同的帐户，你将能够将您的应用程序与 Microsoft Store 中其标识相关联之前其打包。

![将您的应用程序与 Microsoft Store 相关联](images/associate-your-app-700px.png)<br>
将您的应用程序与 Visual Studio 中的 Microsoft Store 相关联

### <a name="store-listing-page"></a>应用商店列表页

上[应用商店列表](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings)应用提交页处理，有几个有关 mixed 的 reality 应用中添加有用的信息的位置。

>[!IMPORTANT]
>若要确保您的应用程序是正确存储分类，以及对 Windows Mixed Reality 客户发现，应将添加 **"Windows Mixed Reality"** 作为一个应用程序 （可以查找搜索词通过展开"搜索字词""共享字段"一节）。

![添加 Windows Mixed Reality 来搜索词](images/search-terms-800px.png)<br>
添加"Windows Mixed Reality"来搜索词

## <a name="offering-a-free-trial-for-your-game-or-app"></a>游戏或应用程序的免费试用版产品/服务

多个使用者只具有有限的没有体验到与虚拟现实之前购买 Windows Mixed Reality 沉浸式头戴式耳机。 它们可能不知道什么需要密集的游戏，并可能不熟悉沉浸式体验以自己舒适阈值。 许多客户还可以尝试不作为带有徽章的电脑上 Windows Mixed Reality 沉浸式头戴式[Windows 混合现实电脑](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。 由于上述考虑，我们强烈建议您考虑产品/服务[免费试用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial)付费混合的现实应用或游戏。

## <a name="see-also"></a>请参阅
* [混合现实](mixed-reality.md)
* [开发概述](development-overview.md)
* [应用程序视图](app-views.md)
* [混合现实的了解性能](understanding-performance-for-mixed-reality.md)
* [Unity 的性能建议](performance-recommendations-for-unity.md)
* [HoloLens 上测试应用](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最小 PC 硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
