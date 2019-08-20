---
title: 实现三维应用启动器 (Win32 应用)
description: 如何创建适用于 Win32 VR 应用和游戏 (在流外分布) 的3D 应用启动器和徽标, 使其显示在 Windows Mixed Reality 的 "开始" 菜单和 "家庭环境" 中。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 徽标, 图标, 建模, 启动器, 3D 启动器, 磁贴, 活动立方体, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515601"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>实现三维应用启动器 (Win32 应用)

> [!NOTE]
> 此功能仅适用于运行最新[Windows 有问必答](https://insider.windows.com)航班 (RS5) 的电脑、版本17704和更高版本。

[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。 默认情况下, 沉浸式 Win32 VR 应用和游戏必须从耳机外启动, 而不会出现在 Windows Mixed Reality 开始菜单上的 "所有应用" 列表中。 但是, 按照本文中的说明实现3D 应用启动器, 可以从 Windows Mixed Reality 开始菜单和 home 环境中启动沉浸式 Win32 VR 体验。

这仅适用于在流外 distributied 的沉浸式 Win32 VR 体验。 对于[通过流发布](updating-your-steamvr-application-for-windows-mixed-reality.md)的 VR 体验, 我们已[更新了适用于 SteamVR Beta 的 windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的 windows 有问必答 RS5 航班, 以便 SteamVR 标题显示在 "所有应用" 列表的 "Windows Mixed reality 开始" 菜单中自动使用默认启动程序。 换句话说, 本文中所述的方法对于 SteamVR 标题是不必要的, 将被 Windows Mixed Reality 替换为 SteamVR Beta 功能。

## <a name="3d-app-launcher-creation-process"></a>3D 应用程序启动器创建过程

创建三维应用启动器有三个步骤:
1. [设计和 concepting](3d-app-launcher-design-guidance.md)
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到你的应用程序中 (本文)

要用作应用程序启动器的3D 资产应使用[Windows Mixed Reality 创作指南](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)进行创作, 以确保兼容性。 未能满足此创作规范的资产将不会在 Windows Mixed Reality 主页中呈现。

## <a name="configuring-the-3d-launcher"></a>配置3D 启动器

如果为 Windows Mixed Reality 开始菜单创建了一个3D 应用启动器, Win32 应用程序将显示在 "所有应用程序" 列表中。 为此, 请按照以下步骤创建一个引用3D 应用程序启动器的[视觉元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)XML 文件:

1. 创建**三维应用启动器资产 GLB 文件**(请参阅[建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。
2. 创建 **[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 为应用程序。
    1. 您可以从下面的[示例](#sample-visual-elements-manifest)开始。  有关更多详细信息, 请参阅完整的[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)文档。
    2. 使用适用于应用的 PNG/JPG/GIF 更新**Square150x150Logo**和**Square70x70Logo** 。
        * 这些项将用于 Windows Mixed Reality 的 "所有应用" 列表中的应用的2D 徽标和桌面上的 "开始" 菜单。
        * 文件路径是相对于包含可视元素清单的文件夹的路径。
        * 仍需通过标准机制为应用提供桌面开始菜单图标。 这可以直接在可执行文件中, 也可以在创建的快捷方式中 (例如通过 IShellLink:: SetIconLocation)。
        * *可选：* 如果希望使用 MRT.LOG 为不同分辨率缩放和高对比度主题提供多种资产大小, 则可以使用资源 pri 文件。
    3. 更新**MixedRealityModel 路径**, 使其指向3D 应用程序启动器的 GLB
    4. 将该文件保存为与可执行文件相同的名称, 扩展名为 ""。VisualElementsManifest "并将其保存在同一目录中。 例如, 对于可执行文件 "contoso", 附带的 XML 文件名为 "visualelementsmanifest"。
3. 将应用程序的**快捷方式添加**到桌面 Windows "开始" 菜单。 有关示例 C++实现, 请参阅[下面的示例](#sample-app-launcher-shortcut-creation)。 
    * 在%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 或%APPDATA%\Microsoft\Windows\Start Menu\Programs (user) 中创建
    * 如果更新更改了你的可视元素清单或它所引用的资产, 则更新程序或安装程序应更新该快捷方式, 以使清单被重新分析并更新缓存资产。
4. *可选：* 如果桌面快捷方式不直接指向应用程序的 EXE (例如, 如果它调用了 "myapp://" 等自定义协议处理程序), 则 "开始" 菜单将不会自动找到应用程序的 VisualElementsManifest 文件。 若要解决此问题, 快捷方式应使用 VisualElementsManifestHintPath () 来指定视觉元素清单的文件路径。 这可以使用与 System.AppUserModel.ID 相同的技术在快捷方式中进行设置。 不需要使用 System.AppUserModel.ID, 但如果想要将快捷方式与应用程序的显式应用程序用户模型 ID 相匹配, 则可能需要使用。  有关C++示例, 请参阅下面的[示例应用程序启动器快捷方式创建](#sample-app-launcher-shortcut-creation)部分。

### <a name="sample-visual-elements-manifest"></a>示例视觉元素清单

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

### <a name="sample-app-launcher-shortcut-creation"></a>示例应用启动器快捷方式创建

下面的示例代码演示了如何在中C++创建快捷方式, 包括重写可视元素清单 XML 文件的路径。 请注意, 仅当快捷方式不直接指向与清单关联的 EXE 时, 才需要重写 (例如 快捷方式使用自定义协议处理程序, 如 "myapp://"。

#### <a name="sample-lnk-shortcut-creation-c"></a>范例..LNK 快捷方式创建C++()

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

#### <a name="sample-url-launcher-shortcut"></a>范例.URL 启动器快捷方式 

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

* 包含三维应用程序启动器的[混合现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D 应用启动器设计指南](3d-app-launcher-design-guidance.md)
* [创建用于 Windows Mixed Reality 主页的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现三维应用启动器 (UWP 应用)](implementing-3d-app-launchers.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
