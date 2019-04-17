---
title: 应用程序模型
description: Windows Mixed Reality 使用通用 Windows 平台、 模型和现代 Windows 应用的环境提供的应用程序模型。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP 应用程序模型、 生命周期、 挂起、 恢复、 磁贴、 视图和协定
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592586"
---
# <a name="app-model"></a>应用程序模型

Windows Mixed Reality 使用提供的应用程序模型[通用 Windows 平台](https://docs.microsoft.com/windows/uwp/get-started/)(UWP) 模型和现代 Windows 应用的环境。 UWP 应用模型定义应用如何为已安装、 更新、 版本控制并安全地完全删除。 它控制如何应用执行、 睡眠和终止的应用程序生命周期和它们保留状态的方式。 它还介绍了集成和与操作系统、 文件和其他应用进行交互。

![2D 排列在 Windows Mixed Reality 家庭早餐区域中的应用](images/20160112-055908-hololens-500px.jpg)<br>
*使用二维视图排列在主 Windows Mixed Reality 应用*

## <a name="app-lifecycle"></a>应用生命周期

混合的现实应用的生命周期涉及标准应用程序概念，如位置、 启动、 终止和删除。

### <a name="placement-is-launch"></a>放置已启动

每个应用程序启动混合现实中放置一个应用程序磁贴 (刚[Windows 辅助磁贴](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) 中[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)。 这些应用的磁贴，在上放置功能，将启动运行该应用程序。 这些应用程序磁贴持久保存和放置位置的位置保持操作如启动器为只要您想要返回到应用。

![放置的辅助磁贴放在世界](images/slide1-600px.png)<br>
*放置的辅助磁贴放在世界*

放置完成后立即 (除非由启动放置[应用](app-model.md#protocols)启动)，启动该应用程序启动。 Windows Mixed Reality 可以一次运行有限的数量的应用程序。 在放置并启动应用程序，可能会挂起其他活动的应用，只要将其放在其应用程序磁贴上离开应用程序的最后一个状态的屏幕截图。 请参阅[Windows 10 UWP 应用程序生命周期](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle)上处理恢复和其他应用程序生命周期事件的详细信息。

![将置于磁贴之后, 应用程序开始运行](images/slide2-500px.png)![正在运行、 挂起或未运行的应用程序的状态示意图](images/ic576232-500px.png)<br>
*左： 后放置一个磁贴，启动该应用程序运行。Right： 正在运行、 已挂起，或未运行的应用程序的状态示意图。*

### <a name="remove-is-closeterminate-process"></a>删除是关闭/终止进程

当从世界上删除放置的应用磁贴时，这会关闭基本过程。 这可用于确保您的应用程序终止或重新启动存在问题的应用。

### <a name="app-suspensiontermination"></a>应用挂起/终止

在中[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)，用户便可创建的应用的多个入口点。 它们启动将应用程序从开始菜单，然后将应用程序磁贴放在世界中执行此操作。 每个应用磁贴表现为其他入口点，并在系统中有一个单独的磁贴实例。 有关查询[SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)将导致**SecondaryTile**针对每个应用实例。

后一个 UWP 应用将挂起，屏幕截图采取的当前状态。

![屏幕截图显示为挂起的应用程序](images/slide9-800px.png)<br>
*屏幕截图显示为挂起的应用程序*

从其他 Windows 10 shell 的一个主要区别是如何应用通知的应用程序实例激活通过[CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming)并[CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)事件。

|  应用场景 |  恢复中  |  已激活 | 
|----------|----------|----------|
|  启动应用程序从开始菜单的新实例  |   |  **激活**有一个新[TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  启动第二个实例的应用程序从开始菜单  |   |  **激活**有一个新**TileId** | 
|  选择的应用程序不是当前处于活动状态的实例  |   |  **激活**与**TileId**与实例相关联 | 
|  选择一个不同的应用，然后选择之前处于活动状态的实例  |  **正在恢复**引发  |  | 
|  选择一个不同的应用，然后选择之前处于非活动状态的实例  |  **正在恢复**引发  |  然后**Activated**与**TileId**与实例相关联 | 

### <a name="extended-execution"></a>扩展执行

有时您的应用程序需要继续在后台工作或播放音频。 [后台任务](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)HoloLens 上可用。

![应用可以在后台运行](images/slide10-800px.png)<br>
*应用可以在后台运行*

## <a name="app-views"></a>应用视图

当您的应用程序激活时，可以选择想要显示的视图的类型。 为应用**CoreApplication**，始终是主[应用视图](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView)和任意数量的进一步你想要创建的应用程序视图。 在桌面上，您可以将应用视图作为窗口。 我们的混合的现实应用模板创建其中的主要应用视图是一个 Unity 项目[沉浸式](app-views.md)。 

您的应用程序可以创建使用 XAML，如技术，使用 Windows 10 功能，例如应用内购买的更多的 2D 应用视图。 如果您的应用程序启动为 UWP 应用的其他 Windows 10 设备，主视图是 2D，但您无法"点燃"混合现实中通过添加为沉浸式 volumetrically 显示一种体验的更多的应用视图。 假定要构建的幻灯片放映按钮，切换到游回来照片将应用程序中跨世界和图面的沉浸式应用程序视图的 XAML 中的照片查看器应用程序。

![正在运行的应用可以有 2D 视图或沉浸式视图](images/slide3-800px.png)<br>
*正在运行的应用可以有 2D 视图或沉浸式视图*

### <a name="creating-an-immersive-view"></a>创建沉浸式视图

混合的现实应用是创建沉浸式视图，可以使用的那些[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace)类型。

即使从桌面启动，是完全沉浸式应用程序应始终创建启动时的沉浸式视图。 沉浸式视图始终显示在耳机，无论它们创建从。 激活的沉浸式视图将显示在混合现实门户，并指导用户将其耳机。

桌面监视器上的二维视图启动的应用可以创建辅助的沉浸式视图以显示耳机中的内容。 出现这种是在耳机中显示的 360 度视频显示器上一个 2D 边缘窗口。

![在沉浸式视图中运行的应用程序是唯一一个可见](images/slide4-800px.png)<br>
*在沉浸式视图中运行的应用程序是唯一一个可见*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>中的主 Windows Mixed Reality 的二维视图

沉浸式视图之外的任何内容将呈现为您的世界中的二维视图。

应用程序可能具有桌面显示器上和耳机的二维视图。 请注意新的二维视图将位于与创建它，该监视器或耳机视图相同的外壳。 不是当前可能的应用或混合现实主页和监视器之间移动的二维视图的用户。

![在二维视图中运行的应用与其他应用共享混合世界中的空间](images/slide5-800px.png)<br>
*在二维视图中运行的应用与其他应用共享空间*

### <a name="placement-of-additional-app-tiles"></a>更多的应用磁贴的位置

您可以放置许多具有 2D 应用查看您的世界中，会出现[辅助磁贴 Api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)。 这些"固定"的磁贴将显示为初始屏幕，用户必须将放置，然后稍后可用于启动应用。 Windows Mixed Reality 当前不支持作为动态磁贴呈现任何 2D 磁贴内容。

![应用可以有多个位置使用辅助磁贴](images/slide6-800px.png)<br>
*应用可以有多个位置使用辅助磁贴*

### <a name="switching-views"></a>切换视图

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>从 2D XAML 视图切换到沉浸式视图

如果应用使用 XAML，则 XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource)将控制应用程序的第一个视图。 应用程序将需要切换到令人着迷的视图，然后再激活**CoreWindow**，以确保该应用将启动直接在沉浸式体验。

使用[CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_)并[ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_)以使其活动视图。

> [!NOTE]
>* 未指定[ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)标记，用于**SwitchAsync**何时删除从 XAML 视图切换到沉浸式视图或启动应用程序的静态图像从世界。
>* **SwitchAsync**应该使用调用[调度程序](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher)与要切入到视图关联。
>* 你将需要**SwitchAsync**回 XAML 视图，如果您需要启动虚拟键盘或想要激活另一个应用程序。

![应用可以二维视图和沉浸式视图之间切换](images/slide7-600px.png)![混合的世界和其他应用时应用进入的沉浸式视图，消失](images/slide8-600px.png)<br>
*左： 应用程序可以二维视图和沉浸式视图之间切换。Right： 时应用进入的沉浸式视图时，Windows Mixed Reality 家庭和其他应用程序消失。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>从沉浸式视图切换回键盘 XAML 视图

视图之间进行切换和-往返的一个常见原因在 mixed 的 reality 应用中显示键盘。 在 shell 才可以显示系统键盘，如果是，应用显示二维视图。 如果应用需要获取文本输入，它可能与文本输入字段中提供的自定义的 XAML 视图中，切换到它，，然后切换输入完成后返回。

在上一节中，就可以使用**ApplicationViewSwitcher.SwitchAsync**在沉浸式视图从其过渡回 XAML 视图。

## <a name="app-size"></a>应用程序大小

2D 应用视图始终显示在固定的虚拟静态图像。 这使得所有显示的内容完全相同的量的二维视图。 下面是一些有关应用的二维视图的大小的更多详细信息：
* 调整大小时保留应用的纵横比。
* 应用程序[分辨率和比例因子](building-2d-apps.md#2d-app-view-resolution-and-scale-factor)未更改通过调整大小。
* 应用程序不能查询实际大小的世界中。

![2D 应用显示具有固定的窗口大小](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*具有固定的窗口大小显示二维视图的应用*

## <a name="app-tiles"></a>应用磁贴

开始菜单为 pin 使用标准的小磁贴和中等磁贴和**所有应用**混合现实中的列表。 

![Windows Mixed Reality 「 开始 」 菜单](images/start-500px.png)<br>
*Windows Mixed Reality 「 开始 」 菜单*

## <a name="app-to-app-interactions"></a>应用程序交互的应用

生成应用时，您将有权访问提供的丰富的应用通信机制，Windows 10 上。 许多协议的新 Api 和文件注册的完全处理的 HoloLens，若要启用应用程序正在启动和通信。 

请注意，对于桌面耳机，与给定的文件扩展名关联应用程序或协议可能只能出现在桌面监视器上或在桌面的静态图像中的 Win32 应用。

### <a name="protocols"></a>协议

HoloLens 支持通过启动应用[Windows.System.Launcher Api](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)。

有启动另一个应用程序时应注意一些事项：

* 在执行时非模式启动，如[LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)，用户必须与之进行交互之前将此应用程序。

* 在执行时模式启动，如通过[LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)，模式应用程序放在窗口的顶部。

* Windows Mixed Reality 不能覆盖独占视图顶层的应用程序。 为了显示启动的应用，Windows 将用户返回到世界上显示该应用程序。

### <a name="file-pickers"></a>文件选取器

同时支持 HoloLens [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker)并[FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker)协定。 但是，没有任何应用可能已预安装，可满足文件选取器协定。 可从 Microsoft Store 安装这些应用程序-例如 OneDrive。

如果有多个安装的文件选取器应用，你看不到任何消除歧义 UI 选择哪些应用程序以启动;相反，将选择第一个文件选取器。 保存文件，将生成文件名，其中包括时间戳。 这不能由用户更改。

默认情况下，本地支持以下扩展：

|  应用  |  Extensions | 
|----------|----------|
|  照片  |  bmp、 gif、 jpg、 png、 avi、 mov、 mp4、 wmv | 
|  Microsoft Edge  |  htm，html、 pdf、 svg、 xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>应用合约和扩展 Windows Mixed Reality

应用合约和扩展点，可注册应用以充分利用更深层次的操作系统功能，如处理文件扩展名或使用后台任务。 这是支持的和不受支持的协定和 HoloLens 上的扩展点的列表。

|  协定或扩展插件  |  支持？ | 
|----------|----------|
| [帐户图片提供程序 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | 不支持 | 
| [Alarm](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | 不支持 | 
| [应用服务](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | 支持，但不是完全正常运行 | 
| [约会提供程序](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | 不支持 | 
| [自动播放 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | 不支持 | 
| [后台任务 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | 部分受支持的 （不是所有触发器工作） | 
| [更新任务 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | 支持 | 
| [缓存的文件更新程序协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | 支持 | 
| [相机设置 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | 不支持 | 
| [拨号协议](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | 不支持 | 
| [文件激活 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | 支持 | 
| [文件打开选取器协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | 支持 | 
| [文件保存选取器协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | 支持 | 
| [锁定屏幕调用](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | 不支持 | 
| [媒体播放](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | 不支持 | 
| [播放到协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | 不支持 | 
| [预安装的配置任务](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | 不支持 | 
| [打印三维工作流](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | 支持 | 
| [打印任务设置 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | 不支持 | 
| [URI 激活 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | 支持 | 
| [受限的启动](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | 不支持 | 
| [搜索协定](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | 不支持 | 
| [设置合约](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | 不支持 | 
| [共享合约](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | 不支持 | 
| [SSL/证书 （扩展）](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | 支持 | 
| [Web 帐户提供程序](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | 支持 | 

## <a name="app-file-storage"></a>应用程序文件存储

所有的存储是通过[Windows.Storage 命名空间](https://docs.microsoft.com/uwp/api/Windows.Storage)。 请参阅以下文档了解详细信息。 HoloLens 不支持应用存储同步/漫游。

* [文件、文件夹和库](https://docs.microsoft.com/windows/uwp/files/index)
* [存储和检索设置和其他应用程序数据](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>已知的文件夹

请参阅[KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders)适用于 UWP 应用的完整详细信息。

<table>
<tr>
<th> 属性</th><th> 在 HoloLens 上受支持</th><th> 在沉浸式耳机上受支持</th><th> 描述</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取应用可捕获文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取的本机照片文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取文档库。 在文档库不是供常规使用。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取音乐库。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取对象三维文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取图片库。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">播放列表</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取的播放列表文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取已保存图片文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取视频库。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>获取的家庭组文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>获取媒体的文件夹服务器 (数字生活网络联盟 (DLNA)) 设备。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>获取记录的呼叫文件夹。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>获取可移动设备文件夹。</td>
</tr>
</table>

## <a name="app-package"></a>应用包

与 Windows 10 不再目标操作系统而[将应用定位到一个或多个设备系列](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)。 设备系列可标识在其中的设备上所需的 API、系统特性和行为。 它还确定的一组设备在其您的应用程序可以安装来自[Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)。

* 若要针对桌面耳机和 HoloLens，将应用定位到**Windows.Universal**设备系列。
* 若要针对仅用于桌面耳机，将应用定位到**Windows.Desktop**设备系列。
* 若要针对仅 HoloLens，将应用定位到**Windows.Holographic**设备系列。

## <a name="see-also"></a>请参阅

* [应用程序视图](app-views.md)
* [更新适用于混合现实的 2D UWP 应用](building-2d-apps.md)
* [三维应用程序启动程序设计指南](3d-app-launcher-design-guidance.md)
* [实现的 3D 应用程序启动器](implementing-3d-app-launchers.md)
