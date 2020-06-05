---
title: Azure 空间定位点教程 - 4. 适用于 Android 和 iOS 的 Azure 空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: 混合现实, unity, 教程, 课程, hololens, azure, 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867619"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4.适用于 Android 和 iOS 的 Azure 空间定位点

在本教程中，你将学习如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。

## <a name="objectives"></a>目标

* 学习如何使用 Unity AR Foundation 和 ARCore XR 插件对 Android 设备生成项目。
* 学习如何使用 Unity AR Foundation 和 ARKit XR 插件对 iOS 设备生成项目。

[!NOTE] 要完成本教程，请确保你已学完 Azure 空间定位点教程的 [Azure 空间定位点入门](mrlearning-asa-ch1.md)。

## <a name="adding-inbuilt-unity-packages"></a>添加内置 Unity 包

在本部分，你将安装 Unity 内置的 AR Foundation、ARCore XR 插件和 ARKit XR 插件包，需使用这些包来支持 Android 和 iOS 设备。

请务必安装这些 Unity 包的正确版本，如下所示：

* **AR Foundation 2.1.4**
* **ARCore XR 插件 2.2.0 预览版 2**
* **ARKit XR 插件 2.1.1**

[!NOTE] 如果你要为 Android 开发此项目，则无需安装 ARKit XR 插件包。 同样，如果你要为 iOS 开发此项目，则无需安装 ARCore XR 插件。

在 Unity 菜单中，选择“窗口” > “包管理器”： 

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

所有包可能几秒后才会在列表中显示。 单击“高级”选项，再选择“显示预览包”来显示它

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

在包管理器窗口中选择 AR Foundation，你将在这里看到多个版本，你需要选择版本 2.1.4 并单击“更新到 2.1.4”按钮来更新包 ：

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

要支持 Android 设备，可按相同的过程导入 ARCore XR 插件 2.2.0 预览版 2。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

要支持 iOS 设备，则应从包管理器中导入“ARKit XR 插件 2.1.1”Unity 包。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>自定义 MRTK 来支持 AR Foundation 相机

通过在“层次结构”窗口中选择 MixedRealityToolKit，自定义 MRTK 设置来支持 AR Foundation，然后在检查器窗口的混合现实工具包中单击“克隆”按钮。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

单击“克隆”按钮时，会出现一个新的“克隆配置文件”窗口，请再次单击“克隆”按钮来克隆 DefaultMixedRealityToolkitProfile。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

同样地，在检查器窗口中克隆相机配置文件，将该配置文件重命名为“UnityARConfigurationProfile”，并单击“克隆”按钮。 在检查器窗口中，找到 MixedReality，然后选择“相机”选项卡。在检查器窗口展开相机设置提供程序，然后单击“+添加相机设置提供程序”，展开“新数据提供程序 1”，选择类型“无”，再选择“Microsoft .MixedReality.Toolkit.Experimental.UnityAR”，最后选择“UnityARCameraSettings”    。


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

在“层次结构”窗口中选择 MixedRealityToolKit 对象后，单击“添加组件”按钮在检查器窗口中附加支持脚本，然后键入“AR 引用点管理器”并选择该脚本。

如果添加“AR 引用点管理器”脚本，则将在检查器窗口中随附该脚本自动添加“AR 会话来源”。 添加支持脚本后，检查器窗口如下所示。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a>对 Android 设备生成应用程序

要对 Android 设备生成此应用程序，请单击窗口顶部的“文件”，然后选择“生成设置” 。 屏幕上将显示一个新窗口，选择“Android”，然后单击“切换平台” 。 切换平台需要几分钟时间。 切换到 Android 平台后，单击“添加打开的场景”，确保你当前的场景是“生成中的场景”列表中唯一选中的场景 。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

关闭“生成设置”窗口。 在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”，然后单击“应用”，为 Android 平台配置 Unity 项目   。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

在 Unity 菜单中选择“编辑” > “项目设置”，打开“项目设置”窗口 。 在“项目设置”窗口中，选择“播放器”选项卡，展开“其他设置”部分，然后选择“Vulkan”并单击“-”符号将它删除 。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

关闭“播放器设置”窗口，再次打开“生成设置”窗口。 然后，使用 USB 线缆将 Android 设备连接到计算机，并在“生成和运行位置”下拉列表中选择你的设备，然后单击“生成并运行” 。 系统会要求你保存一个 .apk 文件，可选择任意名称。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> 如果在 Unity 控制台窗口中收到任何与 Android SDK、NDK 和/或 JDK 模块相关的错误，则需要打开 Unity Hub，然后为 Android 生成支持模块安装关联的 SDK、NDK 和 JDK 模块。

生成过程完成后，应用程序应会在 Android 设备上自动加载。

## <a name="build-application-to-ios-device"></a>对 iOS 设备生成应用程序

要对 iOS 设备生成此应用程序，请单击窗口顶部的“文件”，然后选择“生成设置” 。 屏幕上将显示一个新窗口，选择“iOS”，然后单击“切换平台” 。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

关闭“生成设置”窗口。 在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”，然后单击“应用”，为 iOS 平台配置 Unity 项目   。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

要生成 iOS XCode 项目，请转到“生成设置”并单击“生成”。

按照[本指南](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)了解如何将此项目部署到 iOS 设备中。

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何为 Android 和 iOS 设备生成项目。 你还学习了如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件来让你的项目适用于 Android 和 iOS 设备。