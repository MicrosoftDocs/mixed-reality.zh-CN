---
title: 实现的 3D 应用程序启动器 （UWP 应用）
description: 如何创建三维应用启动器和徽标 Windows 混合现实 UWP 应用和游戏 （通过分发 Microsoft Store），同时在 HoloLens 和沉浸式 (VR) 耳机。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、 徽标、 图标、 建模、 启动器、 3D 启动器、 磁贴、 实时的多维数据集、 深层链接、 secondarytile、 辅助磁贴，UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593019"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>实现的 3D 应用程序启动器 （UWP 应用）

> [!NOTE]
> 此功能已添加的沉浸式耳机 2017 Fall Creators Update (RS3) 的一部分，并且受 HoloLens 使用 Windows 10 2018 年 4 月更新。 请确保你的应用程序所面向的版本大于或等于在沉浸式耳机 10.0.16299 和 10.0.17125 HoloLens 上的 Windows sdk。 您可以找到最新的 Windows SDK[此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。 创建时的 UWP 应用程序 Windows Mixed Reality，默认情况下，使用其应用程序的徽标的 2D 平板电脑启动应用。 为 Windows Mixed Reality 开发体验时, 3D 启动器可以根据需要定义为重写默认 2D 启动器应用程序。 一般情况下，建议使用 3D 启动器用于启动采用带 Windows Mixed Reality 家庭用户，而当就地激活应用程序时，默认 2D 启动器是首选的沉浸式应用程序。 此外可以创建[3D 深层链接 (secondaryTile)](#3d-deep-links-secondarytiles)作为 3D 启动器 2D 的 UWP 应用中的内容。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>三维应用程序启动器创建过程

有 3 个步骤创建的 3D 应用程序启动器：
1. [设计和 concepting](3d-app-launcher-design-guidance.md)
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到你的应用程序 （详见本文）

三维资产，以用作应使用创作你的应用程序的启动器[创作指南 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以确保兼容性。 在 Windows Mixed Reality 家庭中将不会呈现不符合此创作规范的资产。

## <a name="configuring-the-3d-launcher"></a>配置 3D 启动器

当在 Visual Studio 中创建新项目时，它将创建显示应用名称和徽标的简单默认磁贴。 若要替换此 2D 与自定义的三维模型的表示形式，请编辑应用程序清单的应用程序以你默认磁贴的定义的一部分包括"MixedRealityModel"元素。 若要还原到 2D 启动器只 MixedRealityModel 定义从清单中移除。

### <a name="xml"></a>XML

首先，在当前项目中找到应用程序包清单。 默认情况下，清单名称 Package.appxmanifest。 如果你使用 Visual Studio，右键单击解决方案查看器中的清单，然后选择**查看源**以打开用于编辑 xml。 

在清单的顶部，添加 uap5 架构并将其包含为可忽略的命名空间：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

接下来指定"MixedRealityModel"，在你的应用程序的默认磁贴：

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

MixedRealityModel 元素接受文件路径指向存储在你的应用程序包中的三维资产。 当前仅三维模型提供使用.glb 文件格式和根据创作[创作说明 Windows Mixed Reality 3D 资产](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)支持。 资产必须存储在应用包和当前不支持动画。 如果"Path"参数为空时 Windows 将显示而不是 3D 启动器 2D 静态图像。 **注意：** .glb 资产必须被标记为"内容"生成设置中构建和运行您的应用程序之前。


![在解决方案资源管理器中选择.glb 然后使用属性部分中的生成设置，将其标记为"内容"](images/buildsetting-content-300px.png)<br>
*在解决方案资源管理器中选择.glb 然后使用属性部分中的生成设置，将其标记为"内容"*

### <a name="bounding-box"></a>边界框

边界框可用来选择添加对象周围的附加缓冲区区域。 使用中心点和扩展盘区指示边界框的中心到每个轴沿其边缘的距离指定边界框。 边界框的单位可以映射到 1 个单位 = 1 米。 如果未提供边界框然后一个将会自动调整到的对象的网格。 如果提供的边界框小于模型然后，它将调整以适合网格。

边界框属性将提供支持与 Windows 版 RS4 更新作为属性 MixedRealityModel 元素上。 若要首先定义边界框顶部的应用程序清单添加 uap6 架构并将其包含它们称为可忽略的命名空间：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
接下来，在 MixedRealityModel 设置要定义的边界框的 SpatialBoundingBox 属性： 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>使用 Unity

使用 Unity 时必须生成项目，并将其 Visual Studio 中打开，然后才能编辑应用程序清单中。 

>[!NOTE]
>中的清单生成和部署新的 Visual Studio 解决方案从 Unity 时，必须重新定义三维启动器。

## <a name="3d-deep-links-secondarytiles"></a>3D 深度链接 (secondaryTiles)

> [!NOTE]
> 此功能已添加的沉浸式 (VR) 耳机 2017 Fall Creators Update (RS3) 的一部分而 2018 年 4 月的一部分的 HoloLens 的更新 (RS4)。 请确保你的应用程序所面向的版本大于或等于在沉浸式 (VR) 耳机 10.0.16299 和 10.0.17125 HoloLens 上的 Windows sdk。 您可以找到最新的 Windows SDK[此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

>[!IMPORTANT]
>3D 深层链接 (secondaryTiles) 仅适用于 2D UWP 应用。 但是，可以创建[三维应用启动器](implementing-3d-app-launchers.md)启动从主 Windows Mixed Reality 独占应用程序。

2D 应用程序可以通过添加将从你的应用到三维模型的功能增强有关 Windows Mixed Reality [Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)作为 2D 应用程序中的内容的深层链接，就像[2D 辅助数据库磁贴](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)Windows 开始菜单上。 例如，可以创建链接直接到 360 ° 照片查看器应用，或让用户在将打开关于作者的详细信息页的资产的集合中的三维内容的 360 ° photospheres。 它们只是几种方法可展开 3D 内容将 2D 应用程序的功能。

### <a name="creating-a-3d-secondarytile"></a>创建一个三维"secondaryTile"

您可以通过在创建时定义的混合的现实模型使用"secondaryTiles"应用程序中放置 3D 内容。 通过引用应用程序包中的三维资产并根据需要定义边界框创建混合的现实模型。 

> [!NOTE]
> 当前不支持创建从独占视图中的"secondaryTiles"。

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>边界框

边界框可用来添加对象周围的附加缓冲区区域。 使用中心点和扩展盘区指示边界框的中心到每个轴沿其边缘的距离指定边界框。 边界框的单位可以映射到 1 个单位 = 1 米。 如果未提供边界框然后一个将会自动调整到的对象的网格。 如果提供的边界框小于模型然后，它将调整以适合网格。

### <a name="activation-behavior"></a>激活行为

> [!NOTE]
> 将支持此功能起 Windows RS4 更新。 请确保应用程序的目标版本的 Windows SDK 大于或等于 10.0.17125，如果你打算使用此功能

您可以定义来控制其在用户选择它时的反应 3D secondaryTile 激活行为。 这可以用于三维对象放置在主是信息性或装饰性 purley 混合现实中。 支持以下激活行为类型：
1. Default：当用户选择 3D secondaryTile 激活应用程序
2. None:当用户选择 3D secondaryTile 会执行任何操作和应用程序是不会激活。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>获取和更新现有的"secondaryTile"

开发人员可以得到其现有的辅助磁贴的列表，其中包括他们以前指定的属性。 他们还可以通过更改的值，然后再调用 updateasync （） 更新属性。

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>检查用户在 Windows Mixed Reality

当视图显示了 Windows Mixed Reality 耳机，只能创建三维深层链接 (secondaryTiles)。 您的视图不显示了 Windows Mixed Reality 耳机时建议适当地处理此方法是隐藏的入口点或显示一条错误消息。 可以通过查询来检查这[IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)。

## <a name="tile-notifications"></a>磁贴通知

磁贴通知目前不支持发送与 3D 资产的更新。 这意味着开发人员将无法再执行以下操作
* 推送通知
* 定期轮询
* 预定的通知

有关详细信息的其他磁贴功能和属性以及如何为 2D 磁贴使用它们是指[UWP 应用文档的磁贴](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。

## <a name="see-also"></a>请参阅

* [混合的现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含三维应用启动器。
* [三维应用程序启动程序设计指南](3d-app-launcher-design-guidance.md)
* [在 Windows Mixed Reality 主页中创建用于 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现的 3D 应用程序启动器 （Win32 应用）](implementing-3d-app-launchers-win32.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
