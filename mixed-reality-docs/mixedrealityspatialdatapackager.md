---
title: 混合现实空间数据包装程序文档
description: 有关使用混合现实空间数据包装程序的文档
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager、MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942103"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="b20aa-104">混合现实空间数据包装程序文档</span><span class="sxs-lookup"><span data-stu-id="b20aa-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="b20aa-105">此工具及其操作按原样提供。</span><span class="sxs-lookup"><span data-stu-id="b20aa-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="b20aa-106">如果没有任何通知, 它可能会更改, 并且可能不会与未来的 Windows 或 Windows Mixed Reality HMD 版本兼容。</span><span class="sxs-lookup"><span data-stu-id="b20aa-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="b20aa-107">下载</span><span class="sxs-lookup"><span data-stu-id="b20aa-107">Download</span></span>
 <span data-ttu-id="b20aa-108">[在此处下载 MixedRealitySpatialDataPackager](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="b20aa-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="b20aa-109">起步</span><span class="sxs-lookup"><span data-stu-id="b20aa-109">Quickstart</span></span>

<span data-ttu-id="b20aa-110">混合现实空间数据包装器工具通过两步导出和导入过程将目标应用的空间数据从一台 PC 复制到另一台 PC。</span><span class="sxs-lookup"><span data-stu-id="b20aa-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="b20aa-111">此工具必须以管理员权限运行, 并在导入时删除现有空间数据。</span><span class="sxs-lookup"><span data-stu-id="b20aa-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="b20aa-112">导出会使现有的空间数据保持不变。</span><span class="sxs-lookup"><span data-stu-id="b20aa-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="b20aa-113">关键要求和限制:</span><span class="sxs-lookup"><span data-stu-id="b20aa-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="b20aa-114">必须具有管理员权限才能运行工具</span><span class="sxs-lookup"><span data-stu-id="b20aa-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="b20aa-115">运行该工具后, 如果混合现实门户不稳定, 可能需要重启电脑</span><span class="sxs-lookup"><span data-stu-id="b20aa-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="b20aa-116">当遇到空间数据版本不匹配或不兼容时, 工具不会运行</span><span class="sxs-lookup"><span data-stu-id="b20aa-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="b20aa-117">工具将在导入时删除现有空间数据</span><span class="sxs-lookup"><span data-stu-id="b20aa-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="b20aa-118">如果导入进程失败, 则无法还原以前的数据, 除非已通过导出以前的数据进行了备份</span><span class="sxs-lookup"><span data-stu-id="b20aa-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="b20aa-119">针对空间映射数据的 "只读" 模式的导入功能的质量</span><span class="sxs-lookup"><span data-stu-id="b20aa-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="b20aa-120">映射最佳实践</span><span class="sxs-lookup"><span data-stu-id="b20aa-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="b20aa-121">清除控制面板中的现有映射 (设置-> 混合现实-> 环境-> 明文环境数据)</span><span class="sxs-lookup"><span data-stu-id="b20aa-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="b20aa-122">确保光线足以进行良好跟踪, 如果正在运行锁定的映射模式, 则尝试维持相同的照明</span><span class="sxs-lookup"><span data-stu-id="b20aa-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="b20aa-123">如果可能, 请避免深色、阴影区域旁的高照明区域, 使光照动态范围较低</span><span class="sxs-lookup"><span data-stu-id="b20aa-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="b20aa-124">最大程度地减少空白、textureless 的图面, 例如, 将一系列不同海报置于白名单上</span><span class="sxs-lookup"><span data-stu-id="b20aa-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="b20aa-125">在场景中映射不包含动态对象的空间, 例如移动人员</span><span class="sxs-lookup"><span data-stu-id="b20aa-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="b20aa-126">导入时锁定地图 (可通过预览体验预览)</span><span class="sxs-lookup"><span data-stu-id="b20aa-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="b20aa-127">当跟踪质量下降并且/或环境发生变化时 (对象布局中的照明或变化), 解锁地图并重新扫描环境</span><span class="sxs-lookup"><span data-stu-id="b20aa-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="b20aa-128">运行带辅助脚本的混合现实空间数据包装器</span><span class="sxs-lookup"><span data-stu-id="b20aa-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="b20aa-129">我们提供了 MRSpatialPackagerHelperScript, 它运行地图包装器工具。</span><span class="sxs-lookup"><span data-stu-id="b20aa-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="b20aa-130">脚本参数定义如下:</span><span class="sxs-lookup"><span data-stu-id="b20aa-130">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="b20aa-131">Powershell 脚本示例用法和输出</span><span class="sxs-lookup"><span data-stu-id="b20aa-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="b20aa-132">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="b20aa-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="b20aa-133">如何使用 MixedRealityPackager 导出</span><span class="sxs-lookup"><span data-stu-id="b20aa-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="b20aa-134">从设备导出映射会生成两个 mapx 文件: 获取 mapx 和 mapx。</span><span class="sxs-lookup"><span data-stu-id="b20aa-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="b20aa-135">在导出过程中, 除了指定的应用和用户创建的边界 (如果存在) 之外, 还将删除所有空间锚。</span><span class="sxs-lookup"><span data-stu-id="b20aa-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="b20aa-136">源包系列名称必须与现有的已安装应用匹配, 否则 exe 将会失败。</span><span class="sxs-lookup"><span data-stu-id="b20aa-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="b20aa-137">如何使用 MixedRealityPackager 导入</span><span class="sxs-lookup"><span data-stu-id="b20aa-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="b20aa-138">导入删除现有空间数据, 并将其替换为指定目录中的数据。</span><span class="sxs-lookup"><span data-stu-id="b20aa-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="b20aa-139">应用名称输入指定要为其导入空间锚点的目标应用的包名称, 而目标用户 SID 指定应该有权访问已导入的空间锚的用户。</span><span class="sxs-lookup"><span data-stu-id="b20aa-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="b20aa-140">目标包系列名称和用户 Sid 必须与电脑上的现有值匹配, 否则 exe 将会失败。</span><span class="sxs-lookup"><span data-stu-id="b20aa-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="b20aa-141">错误消息</span><span class="sxs-lookup"><span data-stu-id="b20aa-141">Error Messages</span></span>
<span data-ttu-id="b20aa-142">此外, 以下错误消息还将附带 HRESULT</span><span class="sxs-lookup"><span data-stu-id="b20aa-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="b20aa-143">如果有错误的参数无效</span><span class="sxs-lookup"><span data-stu-id="b20aa-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="b20aa-144">如果可执行文件未在管理员模式下运行</span><span class="sxs-lookup"><span data-stu-id="b20aa-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="b20aa-145">如果启用或禁用驱动程序时出错</span><span class="sxs-lookup"><span data-stu-id="b20aa-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="b20aa-146">如果验证空间数据库版本时出错</span><span class="sxs-lookup"><span data-stu-id="b20aa-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="b20aa-147">验证为目标导入/导出应用提供的包系列名称时出错</span><span class="sxs-lookup"><span data-stu-id="b20aa-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="b20aa-148">验证用户 SID 时出错</span><span class="sxs-lookup"><span data-stu-id="b20aa-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="b20aa-149">如果存在与目标或源空间数据文件相关的错误</span><span class="sxs-lookup"><span data-stu-id="b20aa-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="b20aa-150">如果存在与启动和正在停止频谱/SharedRealitySvc 相关的错误</span><span class="sxs-lookup"><span data-stu-id="b20aa-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
