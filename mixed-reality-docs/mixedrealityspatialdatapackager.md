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
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="5e82a-104">混合的现实空间数据包装器文档</span><span class="sxs-lookup"><span data-stu-id="5e82a-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="5e82a-105">此工具，其操作作为提供的是。</span><span class="sxs-lookup"><span data-stu-id="5e82a-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="5e82a-106">它可能会发生更改而无任何通知，并可能与未来的 Windows 兼容或者 Windows 混合现实 HMD 释放。</span><span class="sxs-lookup"><span data-stu-id="5e82a-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="5e82a-107">下载</span><span class="sxs-lookup"><span data-stu-id="5e82a-107">Download</span></span>
 <span data-ttu-id="5e82a-108">下载[MixedRealitySpatialDataPackager 此处](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="5e82a-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="5e82a-109">快速入门</span><span class="sxs-lookup"><span data-stu-id="5e82a-109">Quickstart</span></span>

<span data-ttu-id="5e82a-110">混合现实空间数据包装器工具将空间数据的目标应用程序复制从一个 PC 到另一个通过两个步骤导出和导入过程。</span><span class="sxs-lookup"><span data-stu-id="5e82a-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="5e82a-111">该工具必须使用管理员特权运行，并删除上导入现有的空间数据。</span><span class="sxs-lookup"><span data-stu-id="5e82a-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="5e82a-112">导出使现有空间数据保持不变。</span><span class="sxs-lookup"><span data-stu-id="5e82a-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="5e82a-113">密钥的要求和限制：</span><span class="sxs-lookup"><span data-stu-id="5e82a-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="5e82a-114">必须使用管理员特权运行工具</span><span class="sxs-lookup"><span data-stu-id="5e82a-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="5e82a-115">可能需要重新启动 PC，如果运行该工具后，混合现实门户则不稳定</span><span class="sxs-lookup"><span data-stu-id="5e82a-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="5e82a-116">当遇到有关空间数据的版本不匹配或不兼容性时，将不会运行工具</span><span class="sxs-lookup"><span data-stu-id="5e82a-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="5e82a-117">工具将清除上导入现有空间数据</span><span class="sxs-lookup"><span data-stu-id="5e82a-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="5e82a-118">除非它已通过导出以前已备份，否则如果导入过程失败以前无法还原数据</span><span class="sxs-lookup"><span data-stu-id="5e82a-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="5e82a-119">导入功能取决于空间地图数据的"只读"模式的质量</span><span class="sxs-lookup"><span data-stu-id="5e82a-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="5e82a-120">映射最佳实践</span><span class="sxs-lookup"><span data-stu-id="5e82a-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="5e82a-121">清除控件面板中的现有映射 (设置-> Mixed Reality-> 环境-> 清除环境数据)</span><span class="sxs-lookup"><span data-stu-id="5e82a-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="5e82a-122">确保足够照明很好的跟踪，如果运行锁定的映射模式下尝试维护相同的亮度</span><span class="sxs-lookup"><span data-stu-id="5e82a-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="5e82a-123">如有可能保持照明动态范围较低的通过避免高照明旁边深色、 隐藏区域</span><span class="sxs-lookup"><span data-stu-id="5e82a-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="5e82a-124">最小化空白、 textureless 图面例如白色墙上放置一系列不同的海报</span><span class="sxs-lookup"><span data-stu-id="5e82a-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="5e82a-125">映射不包含动态对象，例如移动用户场景中的空间</span><span class="sxs-lookup"><span data-stu-id="5e82a-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="5e82a-126">锁定在地图上导入 （可通过 Insider Preview）</span><span class="sxs-lookup"><span data-stu-id="5e82a-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="5e82a-127">解锁该映射，然后重新扫描环境时跟踪质量下降和/或 （照明或对象布局中的更改） 的环境中发生了更改</span><span class="sxs-lookup"><span data-stu-id="5e82a-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="5e82a-128">与配套脚本的正在运行的混合的现实空间数据包装器</span><span class="sxs-lookup"><span data-stu-id="5e82a-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="5e82a-129">我们提供了 MRSpatialPackagerHelperScript.ps1 运行映射包装器工具。</span><span class="sxs-lookup"><span data-stu-id="5e82a-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="5e82a-130">脚本参数定义如下：</span><span class="sxs-lookup"><span data-stu-id="5e82a-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="5e82a-131">Powershell 脚本示例用法和输出</span><span class="sxs-lookup"><span data-stu-id="5e82a-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="5e82a-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span><span class="sxs-lookup"><span data-stu-id="5e82a-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="5e82a-133">如何使用 MixedRealityPackager.exe 导出</span><span class="sxs-lookup"><span data-stu-id="5e82a-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="5e82a-134">导出设备的映射将生成两个 mapx 文件、 het.mapx 和 sa.mapx。</span><span class="sxs-lookup"><span data-stu-id="5e82a-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="5e82a-135">在导出过程中所有空间定位点删除指定的应用程序和用户创建边界除外 （如果存在）。</span><span class="sxs-lookup"><span data-stu-id="5e82a-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="5e82a-136">源包系列名称必须匹配现有安装的应用程序或该 exe 将失败。</span><span class="sxs-lookup"><span data-stu-id="5e82a-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="5e82a-137">如何使用 MixedRealityPackager.exe 导入操作</span><span class="sxs-lookup"><span data-stu-id="5e82a-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="5e82a-138">导入删除现有的空间数据，并替换与指定的目录中的数据。</span><span class="sxs-lookup"><span data-stu-id="5e82a-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="5e82a-139">应用名称输入指定的目标应用喜欢空间定位点的包名称应为导入和目标用户 SID 指定有权访问的导入的空间定位点的用户。</span><span class="sxs-lookup"><span data-stu-id="5e82a-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="5e82a-140">目标包系列名称和用户 Sid 必须匹配在 PC 上的现有值或 exe 将失败。</span><span class="sxs-lookup"><span data-stu-id="5e82a-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="5e82a-141">错误消息</span><span class="sxs-lookup"><span data-stu-id="5e82a-141">Error Messages</span></span>
<span data-ttu-id="5e82a-142">除了下面故障的错误消息将还附带一个 HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e82a-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="5e82a-143">如果出现错误的参数无效</span><span class="sxs-lookup"><span data-stu-id="5e82a-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="5e82a-144">如果没有在管理员模式下运行可执行文件</span><span class="sxs-lookup"><span data-stu-id="5e82a-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="5e82a-145">如果出现错误启用或禁用该驱动程序</span><span class="sxs-lookup"><span data-stu-id="5e82a-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="5e82a-146">如果没有正在验证空间的数据库版本错误</span><span class="sxs-lookup"><span data-stu-id="5e82a-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="5e82a-147">如果没有验证为目标导入/导出应用程序提供的包系列名称时出错</span><span class="sxs-lookup"><span data-stu-id="5e82a-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="5e82a-148">如果没有验证的用户 SID 时出错</span><span class="sxs-lookup"><span data-stu-id="5e82a-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="5e82a-149">如果没有错误相关的目标或源空间数据文件</span><span class="sxs-lookup"><span data-stu-id="5e82a-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="5e82a-150">如果没有与启动和停止范围/SharedRealitySvc 相关的错误</span><span class="sxs-lookup"><span data-stu-id="5e82a-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
