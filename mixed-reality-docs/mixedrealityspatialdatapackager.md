---
title: 混合的现实空间数据包装器文档
description: 有关使用混合现实空间数据包装器文档
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe，MixedRealitySpatialDataPackager.exe MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942103"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>混合的现实空间数据包装器文档

>[!NOTE]
> 此工具，其操作作为提供的是。 它可能会发生更改而无任何通知，并可能与未来的 Windows 兼容或者 Windows 混合现实 HMD 释放。

## <a name="download"></a>下载
 下载[MixedRealitySpatialDataPackager 此处](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>快速入门

混合现实空间数据包装器工具将空间数据的目标应用程序复制从一个 PC 到另一个通过两个步骤导出和导入过程。 该工具必须使用管理员特权运行，并删除上导入现有的空间数据。 导出使现有空间数据保持不变。

密钥的要求和限制：

1. 必须使用管理员特权运行工具 
2. 可能需要重新启动 PC，如果运行该工具后，混合现实门户则不稳定
3. 当遇到有关空间数据的版本不匹配或不兼容性时，将不会运行工具
4. 工具将清除上导入现有空间数据
5. 除非它已通过导出以前已备份，否则如果导入过程失败以前无法还原数据
6. 导入功能取决于空间地图数据的"只读"模式的质量
***

## <a name="mapping-best-practices"></a>映射最佳实践

1. 清除控件面板中的现有映射 (设置-> Mixed Reality-> 环境-> 清除环境数据)
2. 确保足够照明很好的跟踪，如果运行锁定的映射模式下尝试维护相同的亮度
3. 如有可能保持照明动态范围较低的通过避免高照明旁边深色、 隐藏区域
4. 最小化空白、 textureless 图面例如白色墙上放置一系列不同的海报
5. 映射不包含动态对象，例如移动用户场景中的空间
6. 锁定在地图上导入 （可通过 Insider Preview）
7. 解锁该映射，然后重新扫描环境时跟踪质量下降和/或 （照明或对象布局中的更改） 的环境中发生了更改
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>与配套脚本的正在运行的混合的现实空间数据包装器

我们提供了 MRSpatialPackagerHelperScript.ps1 运行映射包装器工具。 


脚本参数定义如下：

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Powershell 脚本示例用法和输出

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager.exe 导出
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

导出设备的映射将生成两个 mapx 文件、 het.mapx 和 sa.mapx。 在导出过程中所有空间定位点删除指定的应用程序和用户创建边界除外 （如果存在）。 源包系列名称必须匹配现有安装的应用程序或该 exe 将失败。

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager.exe 导入操作
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
导入删除现有的空间数据，并替换与指定的目录中的数据。 应用名称输入指定的目标应用喜欢空间定位点的包名称应为导入和目标用户 SID 指定有权访问的导入的空间定位点的用户。 目标包系列名称和用户 Sid 必须匹配在 PC 上的现有值或 exe 将失败。


***
## <a name="error-messages"></a>错误消息
除了下面故障的错误消息将还附带一个 HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>如果出现错误的参数无效
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>如果没有在管理员模式下运行可执行文件
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>如果出现错误启用或禁用该驱动程序
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>如果没有正在验证空间的数据库版本错误
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>如果没有验证为目标导入/导出应用程序提供的包系列名称时出错
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>如果没有验证的用户 SID 时出错
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>如果没有错误相关的目标或源空间数据文件
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>如果没有与启动和停止范围/SharedRealitySvc 相关的错误
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
