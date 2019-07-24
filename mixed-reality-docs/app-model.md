---
title: 应用模型
description: Windows Mixed Reality 使用通用 Windows 平台所提供的应用模型, 该模型和环境适用于新式 Windows 应用。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, 应用模型, 生命周期, 暂停, 恢复, 磁贴, 视图, 协定
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517115"
---
# <a name="app-model"></a>应用模型

Windows Mixed Reality 使用[通用 Windows 平台](https://docs.microsoft.com/windows/uwp/get-started/)(UWP) 提供的应用模型, 适用于新式 Windows 应用的模型和环境。 UWP 应用模型定义了如何安全完整地安装、更新、版本控制和删除应用。 它控制应用程序的生命周期-应用程序的执行方式、睡眠和终止方式, 以及它们如何保持状态。 还介绍了与操作系统、文件和其他应用程序的集成和交互。

![在早餐区域中, 在 Windows Mixed Reality 主页中安排的2D 应用](images/20160112-055908-hololens-500px.jpg)<br>
*在 Windows Mixed Reality 主页中显示2D 视图的应用*

## <a name="app-lifecycle"></a>应用生命周期

混合现实应用程序的生命周期涉及标准应用概念, 如放置、启动、终止和删除。

### <a name="placement-is-launch"></a>启动位置

每个应用程序都通过将应用磁贴 (只是一个[windows 辅助磁贴](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) 置于[windows mixed reality 主页](navigating-the-windows-mixed-reality-home.md)中来启动混合现实。 在放置时, 这些应用磁贴会开始运行应用。 这些应用磁贴保留并停留在放置它们的位置, 在任何时候想要返回到应用程序时都是这样的。

![放置将辅助磁贴置于世界中](images/slide1-600px.png)<br>
*放置将辅助磁贴置于世界中*

放置完成后 (除非已将[应用启动到应用](app-model.md#protocols)启动), 应用就会开始启动。 Windows Mixed Reality 一次可以运行有限数量的应用。 一旦你开始使用应用程序, 其他活动的应用程序就可能会挂起, 并使应用程序在其应用磁贴上的最后状态屏幕截图保持屏幕截图。 有关处理恢复和其他应用生命周期事件的详细信息, 请参阅[Windows 10 UWP 应用生命周期](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle)。

![放置磁贴后, 应用将开始运行](images/slide2-500px.png) ![状态图, 以使应用程序运行、挂起或未运行](images/ic576232-500px.png)<br>
*Left: 放置磁贴后, 应用将开始运行。Right: 应用正在运行、已挂起或未运行的状态图。*

### <a name="remove-is-closeterminate-process"></a>删除为关闭/终止进程

在从世界中删除放置的应用磁贴时, 这会关闭基础进程。 这对于确保应用程序终止或重启有问题的应用程序很有用。

### <a name="app-suspensiontermination"></a>应用挂起/终止

在[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)中, 用户可以为应用程序创建多个入口点。 它们通过从 "开始" 菜单启动应用程序并将应用程序磁贴置于世界中来实现此目的。 每个应用磁贴表现为不同的入口点, 并且在系统中有一个单独的磁贴实例。 针对每个应用实例的[SecondaryTile](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)的查询将导致**SecondaryTile** 。

当 UWP 应用暂停时, 将获取当前状态的屏幕截图。

![显示已挂起应用程序的屏幕截图](images/slide9-800px.png)<br>
*显示已挂起应用程序的屏幕截图*

与其他 Windows 10 shell 的一个关键区别在于, 如何通过[CoreApplication](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming)和[CoreWindow](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)事件通知应用程序实例激活。

|  应用场景 |  恢复中  |  已激活 | 
|----------|----------|----------|
|  从 "开始" 菜单启动应用程序的新实例  |   |  使用新的[TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) **激活** | 
|  从 "开始" 菜单启动应用的第二个实例  |   |  使用新的**TileId** **激活** | 
|  选择当前处于非活动状态的应用的实例  |   |  已通过与实例关联的**TileId** **激活** | 
|  选择其他应用, 然后选择以前的活动实例  |  **继续**引发  |  | 
|  选择一个不同的应用, 然后选择先前处于非活动状态的实例  |  **继续**引发  |  然后通过与实例关联的**TileId** **激活** | 

### <a name="extended-execution"></a>扩展执行

有时, 您的应用程序需要在后台继续工作或播放音频。 HoloLens 上提供了[后台任务](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)。

![应用可在后台运行](images/slide10-800px.png)<br>
*应用可在后台运行*

## <a name="app-views"></a>应用视图

当应用程序激活时, 可以选择想要显示的视图类型。 对于应用的**CoreApplication**, 始终有一个主要[应用视图](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView)和你想要创建的任意数量的其他应用视图。 在桌面上, 可以将应用视图视为窗口。 混合现实应用模板会创建一个 Unity 项目, 其中主要应用视图是[沉浸式](app-views.md)的。 

您的应用程序可以使用 XAML 之类的技术创建附加的2D 应用程序视图, 以使用 Windows 10 功能, 如应用内购买。 如果你的应用程序是作为其他 Windows 10 设备的 UWP 应用启动的, 则你的主视图是2D 视图, 但你可以通过添加一个沉浸式的附加应用视图来显示 volumetrically 体验, 从而使你处于混合现实状态。 想象一下, 在 XAML 中生成照片查看器应用程序, 其中的 "幻灯片" 按钮切换到了一个沉浸式应用视图, 可在世界各地的应用程序中星城照片。

![正在运行的应用程序可以有2D 视图或沉浸式视图](images/slide3-800px.png)<br>
*正在运行的应用程序可以有2D 视图或沉浸式视图*

### <a name="creating-an-immersive-view"></a>创建沉浸式视图

混合现实应用是创建沉浸式视图的应用, 该视图是使用[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace)类型实现的。

即使是从桌面启动, 纯粹沉浸式应用程序也应始终在启动时创建一个沉浸式视图。 沉浸式视图始终显示在耳机中, 而不考虑它们的创建位置。 激活沉浸式视图将显示混合现实门户, 并指导用户将其放在耳机上。

以2D 视图在桌面监视器上启动的应用程序可能会创建辅助沉浸式视图, 以显示耳机中的内容。 这种情况的一个示例是监视器上的2D 边缘窗口, 该窗口在耳机中显示360度视频。

![在沉浸式视图中运行的应用程序是唯一可见的](images/slide4-800px.png)<br>
*在沉浸式视图中运行的应用程序是唯一可见的*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 主页中的2D 视图

沉浸式视图以外的任何内容都将呈现为世界上的2D 视图。

应用可能在桌面监视器和耳机上都有2D 视图。 请注意, 新的2D 视图将放在与创建它的视图相同的 shell 中, 无论是在监视器上还是在头戴式耳机中。 目前, 应用或用户无法在混合现实主页与监视器之间移动2D 视图。

![在2D 视图中运行的应用与其他应用共享混合世界的空间](images/slide5-800px.png)<br>
*在二维视图中运行的应用与其他应用共享空间*

### <a name="placement-of-additional-app-tiles"></a>其他应用磁贴的位置

您可以根据需要将任意数量的应用程序与[辅助磁贴 api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)放在世界。 这些 "固定" 磁贴将显示为初始屏幕, 用户必须在该屏幕中放置, 然后可以使用该屏幕来启动应用。 Windows Mixed Reality 目前不支持将任何2D 磁贴内容呈现为动态磁贴。

![应用可以有多个使用辅助磁贴的放置](images/slide6-800px.png)<br>
*应用可以有多个使用辅助磁贴的放置*

### <a name="switching-views"></a>切换视图

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>从 2D XAML 视图切换到沉浸式视图

如果应用使用 XAML, 则 XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource)将控制应用的第一个视图。 在激活**CoreWindow**之前, 应用需要切换到沉浸式视图, 以确保应用直接启动到沉浸式体验。

使用[CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_)和[ApplicationViewSwitcher](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_)将其设为活动视图 (CoreApplication)。

> [!NOTE]
>* 在从 XAML 视图切换到沉浸式视图时, 请勿指定**SwitchAsync**的[ApplicationViewSwitchingOptions ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)标志, 否则将从世界中删除启动该应用程序的盖板。
>* 应使用与要切换到的视图关联的[调度](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher)程序来调用**SwitchAsync** 。
>* 如果需要启动虚拟键盘或要激活其他应用程序, 则需要**SwitchAsync**到 XAML 视图。

![当应用进入沉浸式视图时, 应用](images/slide7-600px.png)可以在2d 视图和沉浸式视图![之间切换, 而混合世界和其他应用会消失](images/slide8-600px.png)<br>
*Left: 应用可以在2D 视图和沉浸式视图之间切换。Right: 当应用进入沉浸式视图时, Windows Mixed Reality home 和其他应用会消失。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>从沉浸式视图切换回键盘 XAML 视图

在两个视图之间来回切换的一个常见原因是在混合现实应用中显示一个键盘。 如果应用显示的是2D 视图, shell 只能显示系统键盘。 如果应用需要获取文本输入, 它可能会提供一个带有文本输入字段的自定义 XAML 视图, 切换到该视图, 然后在输入完成后切换回。

与上一节一样, 可以使用 SwitchAsync 从沉浸式视图过渡回 XAML 视图。 **ApplicationViewSwitcher**

## <a name="app-size"></a>应用大小

2D 应用视图始终显示在固定的虚拟石板中。 这会使所有2D 视图显示完全相同的内容量。 下面是有关应用程序的2D 视图大小的更多详细信息:
* 调整大小时, 会保留应用的长宽比。
* 调整大小不会更改应用[分辨率和缩放比例](building-2d-apps.md#2d-app-view-resolution-and-scale-factor)。
* 应用无法查询世界上的实际大小。

![2D 应用显示为固定的窗口大小](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*具有2D 视图的应用以固定窗口大小显示*

## <a name="app-tiles"></a>应用磁贴

"开始" 菜单将标准的小型磁贴和中型磁贴用于混合现实中的 "pin" 和 "**所有应用**" 列表。 

![Windows Mixed Reality 的 "开始" 菜单](images/start-500px.png)<br>
*Windows Mixed Reality 的 "开始" 菜单*

## <a name="app-to-app-interactions"></a>应用到应用交互

当你生成应用时, 你可以访问 Windows 10 上提供的应用程序通信机制的丰富应用程序。 许多新的协议 Api 和文件注册在 HoloLens 上完美地工作, 以实现应用程序的启动和通信。 

请注意, 对于桌面耳机, 与给定文件扩展名或协议相关联的应用程序可能是只能出现在桌面监视器或桌面石板中的 Win32 应用程序。

### <a name="protocols"></a>协议

HoloLens 支持通过[Windows](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)启动应用程序启动应用程序。

启动其他应用程序时需要考虑以下事项:

* 执行非模式启动 (如[LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)) 时, 用户必须先放置应用, 然后再与它交互。

* 当执行模式启动 (例如通过[LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)) 时, 将在窗口顶部放置模式应用。

* Windows Mixed Reality 无法在排他视图之上覆盖应用程序。 为了显示已启动的应用程序, Windows 会使用户回到世界以显示应用程序。

### <a name="file-pickers"></a>文件选取器

HoloLens 同时支持[FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker)和[FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker)约定。 但是, 没有预安装的应用可满足文件选取器协定。 例如, 可以从 Microsoft Store 中安装这些应用-OneDrive。

如果安装了多个文件选取器应用, 则不会看到任何消除歧义 UI, 因此无法选择要启动的应用程序;相反, 将选择第一个安装的文件选取器。 保存文件时, 会生成包含时间戳的文件名。 用户无法对此进行更改。

默认情况下, 本地支持以下扩展插件:

|  应用  |  Extensions | 
|----------|----------|
|  照片  |  bmp、gif、jpg、png、avi、mov、.wmv、wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>应用协定和 Windows Mixed Reality 扩展

应用协定和扩展点允许注册应用, 以利用更深入的操作系统功能, 例如处理文件扩展名或使用后台任务。 此列表列出了支持的和不支持的合同以及在 HoloLens 上的扩展点。

|  协定或扩展  |  受? | 
|----------|----------|
| [帐户图片提供程序 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | 不支持 | 
| [警报](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | 不支持 | 
| [应用服务](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | 支持但无法完全正常运行 | 
| [约会提供程序](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | 不支持 | 
| [自动播放 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | 不支持 | 
| [后台任务 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | 部分支持 (并非所有触发器都有效) | 
| [更新任务 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | 支持 | 
| [缓存的文件更新程序协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | 支持 | 
| [照相机设置 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | 不支持 | 
| [拨号协议](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | 不支持 | 
| [文件激活 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | 支持 | 
| [文件打开选取器协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | 支持 | 
| [文件保存选取器协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | 支持 | 
| [锁定屏幕调用](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | 不支持 | 
| [媒体播放](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | 不支持 | 
| [扮演合同](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | 不支持 | 
| [预安装的配置任务](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | 不支持 | 
| [打印三维工作流](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | 支持 | 
| [打印任务设置 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | 不支持 | 
| [URI 激活 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | 支持 | 
| [受限启动](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | 不支持 | 
| [搜索协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | 不支持 | 
| [设置约定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | 不支持 | 
| [共享协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | 不支持 | 
| [SSL/证书 (扩展)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | 支持 | 
| [Web 帐户提供程序](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | 支持 | 

## <a name="app-file-storage"></a>应用文件存储

所有存储都通过[Windows. 存储命名空间](https://docs.microsoft.com/uwp/api/Windows.Storage)。 有关更多详细信息, 请参阅以下文档。 HoloLens 不支持应用存储同步/漫游。

* [文件、文件夹和库](https://docs.microsoft.com/windows/uwp/files/index)
* [存储和检索设置以及其他应用数据](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>已知文件夹

有关 UWP 应用的完整详细信息, 请参阅[knownfolders.h](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) 。

<table>
<tr>
<th> 属性</th><th> 在 HoloLens 上受支持</th><th> 沉浸式耳机支持</th><th> 描述</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取应用捕获文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取照相机滚动文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取文档库。 文档库不用于常规用途。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取音乐库。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取对象的三维文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取图片库。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">音乐播放</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取播放列表文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取已保存的图片文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取视频库。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">组</a></td><td></td><td style="text-align: center;">✔️</td><td>获取家庭组文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>获取媒体服务器的文件夹 (数字生活网络联盟 (DLNA)) 设备。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>获取记录的调用文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>获取 "可移动设备" 文件夹。</td>
</tr>
</table>

## <a name="app-package"></a>应用包

对于 Windows 10, 你不再以操作系统为目标, 而是将[你的应用定位到一个或多个设备系列](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)。 设备系列可标识在其中的设备上所需的 API、系统特性和行为。 它还决定了可通过[Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)安装应用的设备集。

* 若要以台式机耳机和 HoloLens 为目标, 请将应用定位到**Windows 通用**设备系列。
* 若要仅面向台式机耳机, 请将应用定向到**Windows desktop**设备系列。
* 若要仅面向 HoloLens, 请将应用定位到**Windows 全息**设备系列。

## <a name="see-also"></a>请参阅

* [应用视图](app-views.md)
* [更新混合现实的 2D UWP 应用](building-2d-apps.md)
* [3D 应用启动器设计指南](3d-app-launcher-design-guidance.md)
* [实现三维应用启动器](implementing-3d-app-launchers.md)
