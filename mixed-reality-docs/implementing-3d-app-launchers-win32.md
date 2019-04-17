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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592184"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>实现的 3D 应用程序启动器 （Win32 应用）

> [!NOTE]
> 此功能仅适用于运行最新版本的电脑正在[Windows Insider](https://insider.windows.com)航班 (RS5)、 生成 17704 和更高版本。

[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。 默认情况下，沉浸式 Win32 VR 应用和游戏必须从启动外部耳机，并且不会显示在 Windows 混合现实开始菜单上的"所有应用"列表。 但是，按照这篇文章中的说明来实现的 3D 应用程序启动器，令人着迷的 Win32 VR 体验可以从启动 Windows 混合现实开始菜单和家庭环境中。

这是仅适用于外部流的沉浸式 Win32 VR 体验 distributied。 VR 体验时会[通过流分发](updating-your-steamvr-application-for-windows-mixed-reality.md)，我们已[SteamVR beta 更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新 Windows Insider RS5 航班以便 SteamVR 标题显示了在 Windows 中混合现实开始菜单会自动使用默认启动器在"所有应用"列表中。 换而言之，在本文中所述的方法，没有必要 SteamVR 标题也将被重写由 Windows Mixed Reality SteamVR Beta 功能。

## <a name="3d-app-launcher-creation-process"></a>三维应用程序启动器创建过程

有 3 个步骤创建的 3D 应用程序启动器：
1. [设计和 concepting](3d-app-launcher-design-guidance.md)
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到你的应用程序 （详见本文）

三维资产，以用作应使用创作你的应用程序的启动器[创作指南 Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)以确保兼容性。 在 Windows Mixed Reality 家庭中将不会呈现不符合此创作规范的资产。

## <a name="configuring-the-3d-launcher"></a>配置 3D 启动器

如果为其创建的 3D 应用程序启动器，Win32 应用程序将显示 Windows 混合现实开始菜单上的"所有应用"列表中。 若要执行此操作，创建[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)XML 文件引用三维应用程序启动程序，通过执行以下步骤：

1. 创建**三维应用启动器资产 GLB 文件**(请参阅[建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。
2. 创建**[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 为应用程序。
    1. 可以使用启动[下面的示例](#sample-visual-elements-manifest)。  查看完整[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)文档了解详细信息。
    2. 更新**Square150x150Logo**并**Square70x70Logo**使用 PNG/JPG/GIF 为你的应用。
        * 将使用这些 Windows 混合现实所有应用程序列表中的应用程序的 2D 徽标以及在桌面上的开始菜单。
        * 文件路径是相对于包含 Visual 元素清单的文件夹。
        * 仍需要为应用提供的桌面开始菜单图标，通过标准机制。 这可以是直接在可执行文件或快捷方式 （例如通过 IShellLink::SetIconLocation) 创建中。
        * *可选：* 如果您要用于 MRT 为不同的分辨率缩放和高对比度主题中提供多个资产的大小，可以使用 resources.pri 文件。
    3. 更新**MixedRealityModel 路径**以指向 GLB 的 3D 的应用程序启动程序
    4. 保存该文件具有相同名称与可执行文件，扩展名为"。VisualElementsManifest.xml"并将其保存在同一目录中。 例如，对于可执行文件"contoso.exe"，随附的 XML 文件是名为"contoso.visualelementsmanifest.xml"。
3. **添加快捷方式**到桌面 Windows 开始菜单应用程序。 请参阅[下面的示例](#sample-app-launcher-shortcut-creation)例如C++实现。 
    * 创建在 %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs （计算机） 或 %APPDATA%\Microsoft\Windows\Start Menu\Programs （用户）
    * 如果更新更改可视元素清单或它引用的资产，更新程序或安装程序应更新该快捷方式以便在清单重新解析和缓存的资产进行更新。
4. *可选：* 如果您的桌面快捷方式不会不直接指向应用程序的 EXE (例如，如果它调用的自定义协议处理程序，如"myapp: / /")，开始菜单不会自动查找应用的 VisualElementsManifest.xml 文件。 若要解决此问题，快捷方式应指定可视元素清单使用 System.AppUserModel.VisualElementsManifestHintPath （） 的文件路径。 这可以作为 System.AppUserModel.ID 使用相同的方法的快捷方式中设置。 您不需要使用 System.AppUserModel.ID，但如果想要匹配的应用程序显式应用程序用户模型 ID，如果使用的快捷方式可能会这样做。  请参阅[示例快捷方式创建的应用启动器](#sample-app-launcher-shortcut-creation)部分获取C++示例。

### <a name="sample-visual-elements-manifest"></a>示例可视化元素清单

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

### <a name="sample-app-launcher-shortcut-creation"></a>创建示例应用程序启动程序快捷方式

下面的代码示例演示如何创建快捷方式C++，包括重写视觉元素清单 XML 文件的路径。 请注意，您的快捷方式不指向直接 （例如与清单关联的 EXE 的情况下才需要重写。 您的快捷方式使用自定义协议处理程序，如"myapp: / /")。

#### <a name="sample-lnk-shortcut-creation-c"></a>示例。创建 LNK 快捷方式 (C++)

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

#### <a name="sample-url-launcher-shortcut"></a>示例。URL 启动程序快捷方式 

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

## <a name="see-also"></a>请参阅

* [混合的现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)包含三维应用启动器。
* [三维应用程序启动程序设计指南](3d-app-launcher-design-guidance.md)
* [在 Windows Mixed Reality 主页中创建用于 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现的 3D 应用程序启动器 （UWP 应用）](implementing-3d-app-launchers.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
