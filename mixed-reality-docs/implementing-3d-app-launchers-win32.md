---
title: 实现的 3D 应用程序启动器 （Win32 应用）
description: 如何创建三维应用启动器和徽标 Win32 VR 应用和游戏 （流以外分发） 因此它们出现在 Windows 混合现实开始菜单和主页环境中。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、 徽标、 图标、 建模、 启动器、 3D 启动器、 磁贴、 实时的多维数据集、 win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592184"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="74d51-104">实现的 3D 应用程序启动器 （Win32 应用）</span><span class="sxs-lookup"><span data-stu-id="74d51-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="74d51-105">此功能仅适用于运行最新版本的电脑正在[Windows Insider](https://insider.windows.com)航班 (RS5)、 生成 17704 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="74d51-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="74d51-106">[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。</span><span class="sxs-lookup"><span data-stu-id="74d51-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="74d51-107">默认情况下，沉浸式 Win32 VR 应用和游戏必须从启动外部耳机，并且不会显示在 Windows 混合现实开始菜单上的"所有应用"列表。</span><span class="sxs-lookup"><span data-stu-id="74d51-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="74d51-108">但是，按照这篇文章中的说明来实现的 3D 应用程序启动器，令人着迷的 Win32 VR 体验可以从启动 Windows 混合现实开始菜单和家庭环境中。</span><span class="sxs-lookup"><span data-stu-id="74d51-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="74d51-109">这是仅适用于外部流的沉浸式 Win32 VR 体验 distributied。</span><span class="sxs-lookup"><span data-stu-id="74d51-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="74d51-110">VR 体验时会[通过流分发](updating-your-steamvr-application-for-windows-mixed-reality.md)，我们已[SteamVR beta 更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新 Windows Insider RS5 航班以便 SteamVR 标题显示了在 Windows 中混合现实开始菜单会自动使用默认启动器在"所有应用"列表中。</span><span class="sxs-lookup"><span data-stu-id="74d51-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="74d51-111">换而言之，在本文中所述的方法，没有必要 SteamVR 标题也将被重写由 Windows Mixed Reality SteamVR Beta 功能。</span><span class="sxs-lookup"><span data-stu-id="74d51-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="74d51-112">三维应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="74d51-112">3D app launcher creation process</span></span>

<span data-ttu-id="74d51-113">有 3 个步骤创建的 3D 应用程序启动器：</span><span class="sxs-lookup"><span data-stu-id="74d51-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="74d51-114">设计和 concepting</span><span class="sxs-lookup"><span data-stu-id="74d51-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="74d51-115">建模和导出</span><span class="sxs-lookup"><span data-stu-id="74d51-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="74d51-116">将其集成到你的应用程序 （详见本文）</span><span class="sxs-lookup"><span data-stu-id="74d51-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="74d51-117">三维资产，以用作应使用创作你的应用程序的启动器[创作指南 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以确保兼容性。</span><span class="sxs-lookup"><span data-stu-id="74d51-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="74d51-118">在 Windows Mixed Reality 家庭中将不会呈现不符合此创作规范的资产。</span><span class="sxs-lookup"><span data-stu-id="74d51-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="74d51-119">配置 3D 启动器</span><span class="sxs-lookup"><span data-stu-id="74d51-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="74d51-120">如果为其创建的 3D 应用程序启动器，Win32 应用程序将显示 Windows 混合现实开始菜单上的"所有应用"列表中。</span><span class="sxs-lookup"><span data-stu-id="74d51-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="74d51-121">若要执行此操作，创建[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)XML 文件引用三维应用程序启动程序，通过执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="74d51-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="74d51-122">创建**三维应用启动器资产 GLB 文件**(请参阅[建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。</span><span class="sxs-lookup"><span data-stu-id="74d51-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="74d51-123">创建 **[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 为应用程序。</span><span class="sxs-lookup"><span data-stu-id="74d51-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="74d51-124">可以使用启动[下面的示例](#sample-visual-elements-manifest)。</span><span class="sxs-lookup"><span data-stu-id="74d51-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="74d51-125">查看完整[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)文档了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="74d51-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="74d51-126">更新**Square150x150Logo**并**Square70x70Logo**使用 PNG/JPG/GIF 为你的应用。</span><span class="sxs-lookup"><span data-stu-id="74d51-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="74d51-127">将使用这些 Windows 混合现实所有应用程序列表中的应用程序的 2D 徽标以及在桌面上的开始菜单。</span><span class="sxs-lookup"><span data-stu-id="74d51-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="74d51-128">文件路径是相对于包含 Visual 元素清单的文件夹。</span><span class="sxs-lookup"><span data-stu-id="74d51-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="74d51-129">仍需要为应用提供的桌面开始菜单图标，通过标准机制。</span><span class="sxs-lookup"><span data-stu-id="74d51-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="74d51-130">这可以是直接在可执行文件或快捷方式 （例如通过 IShellLink::SetIconLocation) 创建中。</span><span class="sxs-lookup"><span data-stu-id="74d51-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="74d51-131">*可选：* 如果您要用于 MRT 为不同的分辨率缩放和高对比度主题中提供多个资产的大小，可以使用 resources.pri 文件。</span><span class="sxs-lookup"><span data-stu-id="74d51-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="74d51-132">更新**MixedRealityModel 路径**以指向 GLB 的 3D 的应用程序启动程序</span><span class="sxs-lookup"><span data-stu-id="74d51-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="74d51-133">保存该文件具有相同名称与可执行文件，扩展名为"。VisualElementsManifest.xml"并将其保存在同一目录中。</span><span class="sxs-lookup"><span data-stu-id="74d51-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="74d51-134">例如，对于可执行文件"contoso.exe"，随附的 XML 文件是名为"contoso.visualelementsmanifest.xml"。</span><span class="sxs-lookup"><span data-stu-id="74d51-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="74d51-135">**添加快捷方式**到桌面 Windows 开始菜单应用程序。</span><span class="sxs-lookup"><span data-stu-id="74d51-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="74d51-136">请参阅[下面的示例](#sample-app-launcher-shortcut-creation)例如C++实现。</span><span class="sxs-lookup"><span data-stu-id="74d51-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="74d51-137">创建在 %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs （计算机） 或 %APPDATA%\Microsoft\Windows\Start Menu\Programs （用户）</span><span class="sxs-lookup"><span data-stu-id="74d51-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="74d51-138">如果更新更改可视元素清单或它引用的资产，更新程序或安装程序应更新该快捷方式以便在清单重新解析和缓存的资产进行更新。</span><span class="sxs-lookup"><span data-stu-id="74d51-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="74d51-139">*可选：* 如果您的桌面快捷方式不会不直接指向应用程序的 EXE (例如，如果它调用的自定义协议处理程序，如"myapp: / /")，开始菜单不会自动查找应用的 VisualElementsManifest.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="74d51-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="74d51-140">若要解决此问题，快捷方式应指定可视元素清单使用 System.AppUserModel.VisualElementsManifestHintPath （） 的文件路径。</span><span class="sxs-lookup"><span data-stu-id="74d51-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="74d51-141">这可以作为 System.AppUserModel.ID 使用相同的方法的快捷方式中设置。</span><span class="sxs-lookup"><span data-stu-id="74d51-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="74d51-142">您不需要使用 System.AppUserModel.ID，但如果想要匹配的应用程序显式应用程序用户模型 ID，如果使用的快捷方式可能会这样做。</span><span class="sxs-lookup"><span data-stu-id="74d51-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="74d51-143">请参阅[示例快捷方式创建的应用启动器](#sample-app-launcher-shortcut-creation)部分获取C++示例。</span><span class="sxs-lookup"><span data-stu-id="74d51-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="74d51-144">示例可视化元素清单</span><span class="sxs-lookup"><span data-stu-id="74d51-144">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="74d51-145">创建示例应用程序启动程序快捷方式</span><span class="sxs-lookup"><span data-stu-id="74d51-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="74d51-146">下面的代码示例演示如何创建快捷方式C++，包括重写视觉元素清单 XML 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="74d51-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="74d51-147">请注意，您的快捷方式不指向直接 （例如与清单关联的 EXE 的情况下才需要重写。</span><span class="sxs-lookup"><span data-stu-id="74d51-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="74d51-148">您的快捷方式使用自定义协议处理程序，如"myapp: / /")。</span><span class="sxs-lookup"><span data-stu-id="74d51-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="74d51-149">示例。创建 LNK 快捷方式 (C++)</span><span class="sxs-lookup"><span data-stu-id="74d51-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="74d51-150">示例。URL 启动程序快捷方式</span><span class="sxs-lookup"><span data-stu-id="74d51-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="74d51-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="74d51-151">See also</span></span>

* <span data-ttu-id="74d51-152">[混合的现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含三维应用启动器。</span><span class="sxs-lookup"><span data-stu-id="74d51-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="74d51-153">三维应用程序启动程序设计指南</span><span class="sxs-lookup"><span data-stu-id="74d51-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="74d51-154">在 Windows Mixed Reality 主页中创建用于 3D 模型</span><span class="sxs-lookup"><span data-stu-id="74d51-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="74d51-155">实现的 3D 应用程序启动器 （UWP 应用）</span><span class="sxs-lookup"><span data-stu-id="74d51-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="74d51-156">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="74d51-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
