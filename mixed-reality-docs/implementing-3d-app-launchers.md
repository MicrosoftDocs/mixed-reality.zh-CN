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
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="a7d09-104">实现的 3D 应用程序启动器 （UWP 应用）</span><span class="sxs-lookup"><span data-stu-id="a7d09-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="a7d09-105">此功能已添加的沉浸式耳机 2017 Fall Creators Update (RS3) 的一部分，并且受 HoloLens 使用 Windows 10 2018 年 4 月更新。</span><span class="sxs-lookup"><span data-stu-id="a7d09-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="a7d09-106">请确保你的应用程序所面向的版本大于或等于在沉浸式耳机 10.0.16299 和 10.0.17125 HoloLens 上的 Windows sdk。</span><span class="sxs-lookup"><span data-stu-id="a7d09-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="a7d09-107">您可以找到最新的 Windows SDK[此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a7d09-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="a7d09-108">[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。</span><span class="sxs-lookup"><span data-stu-id="a7d09-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="a7d09-109">创建时的 UWP 应用程序 Windows Mixed Reality，默认情况下，使用其应用程序的徽标的 2D 平板电脑启动应用。</span><span class="sxs-lookup"><span data-stu-id="a7d09-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="a7d09-110">为 Windows Mixed Reality 开发体验时, 3D 启动器可以根据需要定义为重写默认 2D 启动器应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7d09-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="a7d09-111">一般情况下，建议使用 3D 启动器用于启动采用带 Windows Mixed Reality 家庭用户，而当就地激活应用程序时，默认 2D 启动器是首选的沉浸式应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7d09-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="a7d09-112">此外可以创建[3D 深层链接 (secondaryTile)](#3d-deep-links-secondarytiles)作为 3D 启动器 2D 的 UWP 应用中的内容。</span><span class="sxs-lookup"><span data-stu-id="a7d09-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="a7d09-113">三维应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="a7d09-113">3D app launcher creation process</span></span>

<span data-ttu-id="a7d09-114">有 3 个步骤创建的 3D 应用程序启动器：</span><span class="sxs-lookup"><span data-stu-id="a7d09-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="a7d09-115">设计和 concepting</span><span class="sxs-lookup"><span data-stu-id="a7d09-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="a7d09-116">建模和导出</span><span class="sxs-lookup"><span data-stu-id="a7d09-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="a7d09-117">将其集成到你的应用程序 （详见本文）</span><span class="sxs-lookup"><span data-stu-id="a7d09-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="a7d09-118">三维资产，以用作应使用创作你的应用程序的启动器[创作指南 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以确保兼容性。</span><span class="sxs-lookup"><span data-stu-id="a7d09-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="a7d09-119">在 Windows Mixed Reality 家庭中将不会呈现不符合此创作规范的资产。</span><span class="sxs-lookup"><span data-stu-id="a7d09-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="a7d09-120">配置 3D 启动器</span><span class="sxs-lookup"><span data-stu-id="a7d09-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="a7d09-121">当在 Visual Studio 中创建新项目时，它将创建显示应用名称和徽标的简单默认磁贴。</span><span class="sxs-lookup"><span data-stu-id="a7d09-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="a7d09-122">若要替换此 2D 与自定义的三维模型的表示形式，请编辑应用程序清单的应用程序以你默认磁贴的定义的一部分包括"MixedRealityModel"元素。</span><span class="sxs-lookup"><span data-stu-id="a7d09-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="a7d09-123">若要还原到 2D 启动器只 MixedRealityModel 定义从清单中移除。</span><span class="sxs-lookup"><span data-stu-id="a7d09-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="a7d09-124">XML</span><span class="sxs-lookup"><span data-stu-id="a7d09-124">XML</span></span>

<span data-ttu-id="a7d09-125">首先，在当前项目中找到应用程序包清单。</span><span class="sxs-lookup"><span data-stu-id="a7d09-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="a7d09-126">默认情况下，清单名称 Package.appxmanifest。</span><span class="sxs-lookup"><span data-stu-id="a7d09-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="a7d09-127">如果你使用 Visual Studio，右键单击解决方案查看器中的清单，然后选择**查看源**以打开用于编辑 xml。</span><span class="sxs-lookup"><span data-stu-id="a7d09-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="a7d09-128">在清单的顶部，添加 uap5 架构并将其包含为可忽略的命名空间：</span><span class="sxs-lookup"><span data-stu-id="a7d09-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="a7d09-129">接下来指定"MixedRealityModel"，在你的应用程序的默认磁贴：</span><span class="sxs-lookup"><span data-stu-id="a7d09-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="a7d09-130">MixedRealityModel 元素接受文件路径指向存储在你的应用程序包中的三维资产。</span><span class="sxs-lookup"><span data-stu-id="a7d09-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="a7d09-131">当前仅三维模型提供使用.glb 文件格式和根据创作[创作说明 Windows Mixed Reality 3D 资产](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)支持。</span><span class="sxs-lookup"><span data-stu-id="a7d09-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="a7d09-132">资产必须存储在应用包和当前不支持动画。</span><span class="sxs-lookup"><span data-stu-id="a7d09-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="a7d09-133">如果"Path"参数为空时 Windows 将显示而不是 3D 启动器 2D 静态图像。</span><span class="sxs-lookup"><span data-stu-id="a7d09-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="a7d09-134">**注意：** .glb 资产必须被标记为"内容"生成设置中构建和运行您的应用程序之前。</span><span class="sxs-lookup"><span data-stu-id="a7d09-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="a7d09-135">![在解决方案资源管理器中选择.glb 然后使用属性部分中的生成设置，将其标记为"内容"](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="a7d09-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="a7d09-136">*在解决方案资源管理器中选择.glb 然后使用属性部分中的生成设置，将其标记为"内容"*</span><span class="sxs-lookup"><span data-stu-id="a7d09-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="a7d09-137">边界框</span><span class="sxs-lookup"><span data-stu-id="a7d09-137">Bounding box</span></span>

<span data-ttu-id="a7d09-138">边界框可用来选择添加对象周围的附加缓冲区区域。</span><span class="sxs-lookup"><span data-stu-id="a7d09-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="a7d09-139">使用中心点和扩展盘区指示边界框的中心到每个轴沿其边缘的距离指定边界框。</span><span class="sxs-lookup"><span data-stu-id="a7d09-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="a7d09-140">边界框的单位可以映射到 1 个单位 = 1 米。</span><span class="sxs-lookup"><span data-stu-id="a7d09-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="a7d09-141">如果未提供边界框然后一个将会自动调整到的对象的网格。</span><span class="sxs-lookup"><span data-stu-id="a7d09-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="a7d09-142">如果提供的边界框小于模型然后，它将调整以适合网格。</span><span class="sxs-lookup"><span data-stu-id="a7d09-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="a7d09-143">边界框属性将提供支持与 Windows 版 RS4 更新作为属性 MixedRealityModel 元素上。</span><span class="sxs-lookup"><span data-stu-id="a7d09-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="a7d09-144">若要首先定义边界框顶部的应用程序清单添加 uap6 架构并将其包含它们称为可忽略的命名空间：</span><span class="sxs-lookup"><span data-stu-id="a7d09-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="a7d09-145">接下来，在 MixedRealityModel 设置要定义的边界框的 SpatialBoundingBox 属性：</span><span class="sxs-lookup"><span data-stu-id="a7d09-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="a7d09-146">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="a7d09-146">Using Unity</span></span>

<span data-ttu-id="a7d09-147">使用 Unity 时必须生成项目，并将其 Visual Studio 中打开，然后才能编辑应用程序清单中。</span><span class="sxs-lookup"><span data-stu-id="a7d09-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="a7d09-148">中的清单生成和部署新的 Visual Studio 解决方案从 Unity 时，必须重新定义三维启动器。</span><span class="sxs-lookup"><span data-stu-id="a7d09-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="a7d09-149">3D 深度链接 (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="a7d09-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="a7d09-150">此功能已添加的沉浸式 (VR) 耳机 2017 Fall Creators Update (RS3) 的一部分而 2018 年 4 月的一部分的 HoloLens 的更新 (RS4)。</span><span class="sxs-lookup"><span data-stu-id="a7d09-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="a7d09-151">请确保你的应用程序所面向的版本大于或等于在沉浸式 (VR) 耳机 10.0.16299 和 10.0.17125 HoloLens 上的 Windows sdk。</span><span class="sxs-lookup"><span data-stu-id="a7d09-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="a7d09-152">您可以找到最新的 Windows SDK[此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a7d09-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="a7d09-153">3D 深层链接 (secondaryTiles) 仅适用于 2D UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="a7d09-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="a7d09-154">但是，可以创建[三维应用启动器](implementing-3d-app-launchers.md)启动从主 Windows Mixed Reality 独占应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7d09-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="a7d09-155">2D 应用程序可以通过添加将从你的应用到三维模型的功能增强有关 Windows Mixed Reality [Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)作为 2D 应用程序中的内容的深层链接，就像[2D 辅助数据库磁贴](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)Windows 开始菜单上。</span><span class="sxs-lookup"><span data-stu-id="a7d09-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="a7d09-156">例如，可以创建链接直接到 360 ° 照片查看器应用，或让用户在将打开关于作者的详细信息页的资产的集合中的三维内容的 360 ° photospheres。</span><span class="sxs-lookup"><span data-stu-id="a7d09-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="a7d09-157">它们只是几种方法可展开 3D 内容将 2D 应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="a7d09-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="a7d09-158">创建一个三维"secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="a7d09-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="a7d09-159">您可以通过在创建时定义的混合的现实模型使用"secondaryTiles"应用程序中放置 3D 内容。</span><span class="sxs-lookup"><span data-stu-id="a7d09-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="a7d09-160">通过引用应用程序包中的三维资产并根据需要定义边界框创建混合的现实模型。</span><span class="sxs-lookup"><span data-stu-id="a7d09-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="a7d09-161">当前不支持创建从独占视图中的"secondaryTiles"。</span><span class="sxs-lookup"><span data-stu-id="a7d09-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="a7d09-162">边界框</span><span class="sxs-lookup"><span data-stu-id="a7d09-162">Bounding box</span></span>

<span data-ttu-id="a7d09-163">边界框可用来添加对象周围的附加缓冲区区域。</span><span class="sxs-lookup"><span data-stu-id="a7d09-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="a7d09-164">使用中心点和扩展盘区指示边界框的中心到每个轴沿其边缘的距离指定边界框。</span><span class="sxs-lookup"><span data-stu-id="a7d09-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="a7d09-165">边界框的单位可以映射到 1 个单位 = 1 米。</span><span class="sxs-lookup"><span data-stu-id="a7d09-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="a7d09-166">如果未提供边界框然后一个将会自动调整到的对象的网格。</span><span class="sxs-lookup"><span data-stu-id="a7d09-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="a7d09-167">如果提供的边界框小于模型然后，它将调整以适合网格。</span><span class="sxs-lookup"><span data-stu-id="a7d09-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="a7d09-168">激活行为</span><span class="sxs-lookup"><span data-stu-id="a7d09-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="a7d09-169">将支持此功能起 Windows RS4 更新。</span><span class="sxs-lookup"><span data-stu-id="a7d09-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="a7d09-170">请确保应用程序的目标版本的 Windows SDK 大于或等于 10.0.17125，如果你打算使用此功能</span><span class="sxs-lookup"><span data-stu-id="a7d09-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="a7d09-171">您可以定义来控制其在用户选择它时的反应 3D secondaryTile 激活行为。</span><span class="sxs-lookup"><span data-stu-id="a7d09-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="a7d09-172">这可以用于三维对象放置在主是信息性或装饰性 purley 混合现实中。</span><span class="sxs-lookup"><span data-stu-id="a7d09-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="a7d09-173">支持以下激活行为类型：</span><span class="sxs-lookup"><span data-stu-id="a7d09-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="a7d09-174">Default：当用户选择 3D secondaryTile 激活应用程序</span><span class="sxs-lookup"><span data-stu-id="a7d09-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="a7d09-175">None:当用户选择 3D secondaryTile 会执行任何操作和应用程序是不会激活。</span><span class="sxs-lookup"><span data-stu-id="a7d09-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="a7d09-176">获取和更新现有的"secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="a7d09-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="a7d09-177">开发人员可以得到其现有的辅助磁贴的列表，其中包括他们以前指定的属性。</span><span class="sxs-lookup"><span data-stu-id="a7d09-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="a7d09-178">他们还可以通过更改的值，然后再调用 updateasync （） 更新属性。</span><span class="sxs-lookup"><span data-stu-id="a7d09-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="a7d09-179">检查用户在 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a7d09-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="a7d09-180">当视图显示了 Windows Mixed Reality 耳机，只能创建三维深层链接 (secondaryTiles)。</span><span class="sxs-lookup"><span data-stu-id="a7d09-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="a7d09-181">您的视图不显示了 Windows Mixed Reality 耳机时建议适当地处理此方法是隐藏的入口点或显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="a7d09-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="a7d09-182">可以通过查询来检查这[IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)。</span><span class="sxs-lookup"><span data-stu-id="a7d09-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="a7d09-183">磁贴通知</span><span class="sxs-lookup"><span data-stu-id="a7d09-183">Tile notifications</span></span>

<span data-ttu-id="a7d09-184">磁贴通知目前不支持发送与 3D 资产的更新。</span><span class="sxs-lookup"><span data-stu-id="a7d09-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="a7d09-185">这意味着开发人员将无法再执行以下操作</span><span class="sxs-lookup"><span data-stu-id="a7d09-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="a7d09-186">推送通知</span><span class="sxs-lookup"><span data-stu-id="a7d09-186">Push Notifications</span></span>
* <span data-ttu-id="a7d09-187">定期轮询</span><span class="sxs-lookup"><span data-stu-id="a7d09-187">Periodic Polling</span></span>
* <span data-ttu-id="a7d09-188">预定的通知</span><span class="sxs-lookup"><span data-stu-id="a7d09-188">Scheduled Notifications</span></span>

<span data-ttu-id="a7d09-189">有关详细信息的其他磁贴功能和属性以及如何为 2D 磁贴使用它们是指[UWP 应用文档的磁贴](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。</span><span class="sxs-lookup"><span data-stu-id="a7d09-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d09-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7d09-190">See also</span></span>

* <span data-ttu-id="a7d09-191">[混合的现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含三维应用启动器。</span><span class="sxs-lookup"><span data-stu-id="a7d09-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="a7d09-192">三维应用程序启动程序设计指南</span><span class="sxs-lookup"><span data-stu-id="a7d09-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="a7d09-193">在 Windows Mixed Reality 主页中创建用于 3D 模型</span><span class="sxs-lookup"><span data-stu-id="a7d09-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="a7d09-194">实现的 3D 应用程序启动器 （Win32 应用）</span><span class="sxs-lookup"><span data-stu-id="a7d09-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="a7d09-195">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="a7d09-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
