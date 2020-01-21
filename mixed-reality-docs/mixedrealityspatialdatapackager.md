---
title: 混合现实空间数据包装程序文档
description: 有关使用混合现实空间数据包装程序的文档
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager、MixedRealitySpatialDataPackager
ms.openlocfilehash: 3beb8f9168bfb6fd921d6d5c1eb6d250c70a714d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539679"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>混合现实空间数据包装程序文档

>[!NOTE]
> 此工具及其操作按原样提供。 如果没有任何通知，它可能会更改，并且可能不会与未来的 Windows 或 Windows Mixed Reality HMD 版本兼容。

## <a name="download"></a>“下载”
 [在此处下载 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>具有</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>混合现实空间数据包装器</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>起步

混合现实空间数据包装器工具通过两步导出和导入过程将目标应用的空间数据从一台 PC 复制到另一台 PC。 此工具必须以管理员权限运行，并在导入时删除现有空间数据。 导出会使现有的空间数据保持不变。

关键要求和限制：

1. 必须具有管理员权限才能运行工具 
2. 运行该工具后，如果混合现实门户不稳定，可能需要重启电脑
3. 当遇到空间数据版本不匹配或不兼容时，工具不会运行
4. 工具将在导入时删除现有空间数据
5. 如果导入进程失败，则无法还原以前的数据，除非已通过导出以前的数据进行了备份
6. 针对空间映射数据的 "只读" 模式的导入功能的质量
***

## <a name="mapping-best-practices"></a>映射最佳实践

1. 清除控制面板中的现有映射（设置-> 混合现实-> 环境-> 明文环境数据）
2. 确保光线足以进行良好跟踪，如果正在运行锁定的映射模式，则尝试维持相同的照明
3. 如果可能，请避免深色、阴影区域旁的高照明区域，使光照动态范围较低
4. 最大程度地减少空白、textureless 的图面，例如，将一系列不同海报置于允许列表上
5. 在场景中映射不包含动态对象的空间，例如移动人员
6. 导入时锁定地图（可通过预览体验预览）
7. 当跟踪质量下降并且/或环境发生变化时（对象布局中的照明或变化），解锁地图并重新扫描环境
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>运行带辅助脚本的混合现实空间数据包装器

我们提供了 MRSpatialPackagerHelperScript，它运行地图包装器工具。 


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

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Powershell 脚本示例用法和输出

.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName MapxPath D:\temp\-LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager 导出
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

从设备导出映射会生成两个 mapx 文件：获取 mapx 和 mapx。 在导出过程中，除了指定的应用和用户创建的边界（如果存在）之外，还将删除所有空间锚。 源包系列名称必须与现有的已安装应用匹配，否则 exe 将会失败。

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>如何使用 MixedRealityPackager 导入
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
导入删除现有空间数据，并将其替换为指定目录中的数据。 应用名称输入指定要为其导入空间锚点的目标应用的包名称，而目标用户 SID 指定应该有权访问已导入的空间锚的用户。 目标包系列名称和用户 Sid 必须与电脑上的现有值匹配，否则 exe 将会失败。


***
## <a name="error-messages"></a>错误消息
此外，以下错误消息还将附带 HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>如果有错误的参数无效
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>如果可执行文件未在管理员模式下运行
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>如果启用或禁用驱动程序时出错
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>如果验证空间数据库版本时出错
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>验证为目标导入/导出应用提供的包系列名称时出错
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>验证用户 SID 时出错
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>如果存在与目标或源空间数据文件相关的错误
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>如果存在与启动和停止频谱/SharedRealitySvc 相关的错误
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
