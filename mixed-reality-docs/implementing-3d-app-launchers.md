---
title: 实现三维应用启动器（UWP 应用）
description: 如何在 HoloLens 和沉浸式（VR）耳机上创建适用于 Windows Mixed Reality UWP 应用和游戏（通过 Microsoft Store 分发）的3D 应用启动器和徽标。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，徽标，图标，建模，启动器，3D 启动器，磁贴，动态立方体，深层链接，secondarytile，辅助磁贴，UWP
ms.openlocfilehash: 0a2e2177ffa7e381c461a58f373c818c9c5e72c4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549383"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>实现三维应用启动器（UWP 应用）

> [!NOTE]
> 此功能是作为沉浸式耳机的2017秋季创意者更新（RS3）的一部分添加的，使用 Windows 10 4 月2018更新时，HoloLens 支持此功能。 请确保应用程序面向的是10.0.16299 的版本，Windows SDK 该版本大于或等于沉浸式耳机上的和10.0.17125 上的。 可在[此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。

[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。 为 Windows Mixed Reality 创建 UWP 应用程序时，默认情况下，应用程序将以2D 清单启动，其应用的徽标。 当开发 Windows Mixed Reality 体验时，可以根据需要定义3D 启动程序来覆盖应用程序的默认2D 启动器。 通常情况下，建议使用三维启动器来启动将用户从 Windows Mixed Reality 主页移出的沉浸式应用程序，而在就地激活应用程序时首选默认的2D 启动器。 还可以创建一个[3d 深层链接（secondaryTile）](#3d-deep-links-secondarytiles)作为3d 启动程序，使其成为二维 UWP 应用内的内容。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 应用程序启动器创建过程

创建三维应用启动器有三个步骤：
1. [设计和 concepting](3d-app-launcher-design-guidance.md)
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到你的应用程序中（本文）

要用作应用程序启动器的3D 资产应使用[Windows Mixed Reality 创作指南](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)进行创作，以确保兼容性。 未能满足此创作规范的资产将不会在 Windows Mixed Reality 主页中呈现。

## <a name="configuring-the-3d-launcher"></a>配置3D 启动器

当在 Visual Studio 中创建新项目时，它将创建显示应用名称和徽标的简单默认磁贴。 若要将此2D 表示形式替换为自定义3D 模型，请编辑应用程序的应用程序清单，将 "MixedRealityModel" 元素作为默认磁贴定义的一部分包含在内。 若要还原为2D 启动器，只需从清单中删除 MixedRealityModel 定义。

### <a name="xml"></a>XML

首先，在当前项目中找到应用程序包清单。 默认情况下，该清单将命名为 appxmanifest.xml。 如果使用的是 Visual Studio，请右键单击解决方案查看器中的清单，然后选择 "**查看源**" 以打开要编辑的 xml。 

在清单的顶部，添加 uap5 架构，并将其包含为可忽略的命名空间：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

接下来，在应用程序的默认磁贴中指定 "MixedRealityModel"：

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

MixedRealityModel 元素接受指向存储在应用包中的3D 资产的文件路径。 目前仅支持使用 glb 文件格式交付并针对[Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)创作的3d 模型。 资产必须存储在应用包中，且当前不支持动画。 如果 "Path" 参数保留为空，则 Windows 将显示2D 盖板而不是3D 启动器。 **注意：** 生成和运行应用之前，必须在生成设置中将 glb 资产标记为 "内容"。


![在解决方案资源管理器中选择 glb，并使用 properties 节将其标记为生成设置中的 "Content"](images/buildsetting-content-300px.png)<br>
*在解决方案资源管理器中选择 glb，并使用 properties 节将其标记为生成设置中的 "Content"*

### <a name="bounding-box"></a>边界框

边界框可用于根据需要在对象周围添加其他缓冲区区域。 边界框是使用中心点和范围指定的，这些范围指示从边界框的中心到沿每个轴的边缘之间的距离。 边界框的单位可以映射到1个 unit = 1 个计量器。 如果未提供边界框，则会自动将一个边界调整到对象的网格。 如果提供的边界框小于模型，则将调整其大小以适合网格。

对范围框属性的支持将作为 MixedRealityModel 元素上的属性提供给 Windows RS4 更新。 若要首先在应用程序清单顶部定义边界框，请添加 uap6 架构，并将其包含为可忽略的命名空间：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
接下来，在 MixedRealityModel 上，将 SpatialBoundingBox 属性设置为定义边界框： 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>使用 Unity

使用 Unity 时，必须先在 Visual Studio 中生成和打开项目，然后才能编辑应用程序清单。 

>[!NOTE]
>在从 Unity 生成和部署新的 Visual Studio 解决方案时，必须在清单中重新定义3D 启动程序。

## <a name="3d-deep-links-secondarytiles"></a>3D 深层链接（secondaryTiles）

> [!NOTE]
> 此功能已作为2017秋季创意者更新（RS3）的一部分添加，适用于沉浸式（VR）耳机和年4月2018更新（RS4）的一部分。 请确保应用程序面向的是 Windows SDK 大于或等于 10.0.16299 on 沉浸式（VR）耳机和10.0.17125 的版本。 可在[此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。

>[!IMPORTANT]
>3D 深层链接（secondaryTiles）仅适用于 2D UWP 应用。 不过，你可以创建一个[3d 应用启动器](implementing-3d-app-launchers.md)，从 Windows Mixed Reality 主页启动一个独占应用。

您的2D 应用程序可以通过添加将3D 模型从应用置于[Windows Mixed reality 主页](navigating-the-windows-mixed-reality-home.md)中来增强 Windows mixed reality，就像 Windows "开始" 菜单上的[2d 辅助磁贴](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)一样。 例如，你可以创建360° photospheres，它直接链接到360°照片查看器应用，或让用户从一组资产中放置3D 内容，以便打开有关作者的详细信息页。 这只是使用三维内容展开2D 应用程序功能的几种方法。

### <a name="creating-a-3d-secondarytile"></a>创建三维 "secondaryTile"

可以通过在创建时定义混合现实模型，使用 "secondaryTiles" 从应用程序中放置3D 内容。 混合现实模型是通过引用应用包中的3D 资产创建的，还可以选择定义边界框。 

> [!NOTE]
> 当前不支持在排他视图内创建 "secondaryTiles"。

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

边界框可用于在对象周围添加其他缓冲区区域。 边界框是使用中心点和范围指定的，这些范围指示从边界框的中心到沿每个轴的边缘之间的距离。 边界框的单位可以映射到1个 unit = 1 个计量器。 如果未提供边界框，则会自动将一个边界调整到对象的网格。 如果提供的边界框小于模型，则将调整其大小以适合网格。

### <a name="activation-behavior"></a>激活行为

> [!NOTE]
> Windows RS4 更新将支持此功能。 如果计划使用此功能，请确保应用程序面向的 Windows SDK 版本大于或等于10.0.17125

您可以定义三维 secondaryTile 的激活行为，以控制用户选择它时其反应方式。 这可用于将三维对象置于纯信息性或装饰性的混合现实主页中。 支持以下激活行为类型：
1. 默认值：用户选择 3D secondaryTile 时，会激活应用
2. 无：当用户选择 3D secondaryTile 时，不会执行任何操作，也不会激活应用。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>获取和更新现有 "secondaryTile"

开发人员可以返回其现有辅助磁贴的列表，其中包括前面指定的属性。 它们还可以通过更改值，然后调用 UpdateAsync （）来更新属性。

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>正在检查用户是否处于 Windows Mixed Reality

仅当在 Windows Mixed Reality 耳机中显示视图时，才能创建3D 深层链接（secondaryTiles）。 如果未在 Windows Mixed Reality 耳机中显示你的视图，我们建议通过隐藏输入点或显示错误消息来处理此问题。 可以通过查询[IsCurrentViewPresentedOnHolographic （）](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)来检查此情况。

## <a name="tile-notifications"></a>磁贴通知

磁贴通知当前不支持使用三维资产发送更新。 这意味着开发人员不能执行以下操作：
* 推送通知
* 定期轮询
* 计划的通知

有关其他磁贴功能和属性以及它们如何用于2D 磁贴的详细信息，请参阅[UWP 应用的磁贴文档](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。

## <a name="see-also"></a>另请参阅

* 包含三维应用程序启动器的[混合现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D 应用启动器设计指南](3d-app-launcher-design-guidance.md)
* [创建用于 Windows Mixed Reality 主页的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现三维应用启动器（Win32 应用）](implementing-3d-app-launchers-win32.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
