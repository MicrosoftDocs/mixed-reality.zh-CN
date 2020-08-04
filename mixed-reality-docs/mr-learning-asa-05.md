---
title: Azure 空间定位点教程 - 5. 适用于 Android 和 iOS 的 Azure 空间定位点
description: 完成本课程可以了解如何将使用混合现实工具包和 Azure 空间定位点的 Unity 项目部署到 Android 和 iOS 上。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376539"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5.适用于 Android 和 iOS 的 Azure 空间定位点

在本教程中，你将学习如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。

## <a name="objectives"></a>目标

* 学习如何使用 Unity 的 AR Foundation 和 ARCore XR 插件对 Android 设备生成项目
* 学习如何使用 Unity 的 AR Foundation 和 ARKit XR 插件对 iOS 设备生成项目

## <a name="installing-inbuilt-unity-packages"></a>安装内置 Unity 包

在本部分中，你将升级并安装以下内置包：

* AR Foundation 3.1.3
* 旧版 Input Helpers 2.1.4
* 适用于 Android 的 ARCore XR 插件 3.1.3 支持
* 适用于 iOS 的 ARKit XR 插件 3.1.3 支持

> [!CAUTION]
> 并非所有版本都与 MRTK 兼容，只有某些版本可协同工作，因此请确保安装的是上述版本。

在 Unity 菜单中，选择“窗口” > “包管理器”来打开“包管理器”窗口，然后选择“AR Foundation” > “3.1.3”，再单击“更新到 3.1.3”按钮来更新包    ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

根据需要按照相同的过程导入其余的包。

> [!NOTE]
> 如果你要为 Android 开发此项目，则无需安装 ARKit XR 插件包。 同样，如果你要为 iOS 开发此项目，则无需安装 ARCore XR 插件。

## <a name="configure-mrtk-for-ar-foundation-camera"></a>为 AR Foundation 摄像头配置 MRTK

在本部分，你将学习如何配置 MRTK 以部署到移动设备。

在“层次结构”窗口中，选择 MixedRealityToolkit 对象。 然后，在检查器窗口中，选择“摄像头”选项卡，克隆摄像头配置文件，并为其指定一个适当的名称，例如 AzureSpatialAnchors_ARCameraProfile ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> 要通过提示了解如何克隆 MRTK 配置文件的提示，可参阅[配置混合现实工具包配置文件](mr-learning-base-03.md)中的说明。

在检查器窗口中仍选中“摄像头”选项卡的情况下，展开“摄像头设置提供程序”，单击“+添加摄像头设置提供程序”按钮，然后展开新添加的“新数据提供程序 1”   ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

使用“类型”下拉列表将类型更改为“Microsoft.MixedReality.Toolkit.Experimental.UnityAR” > “UnityARCameraSettings”  ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

在“层次结构”窗口中仍选中 MixedRealityToolkit 对象的情况下，使用检查器窗口中的“添加组件”按钮添加以下组件 ：

* AR 空间点管理器(脚本)
* DisableDiagnosticsSystem (脚本)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> 添加“AR 引用点管理器(脚本)”组件时，会自动添加“AR 会话来源(脚本)”组件，因为它是“AR 引用点管理器(脚本)”组件所必需的。

## <a name="building-your-application-to-your-android-device"></a>将应用程序生成到 Android 设备

在本部分，你将学习如何配置项目来生成它并将其部署到 Android 设备。

在 Unity 菜单中，选择“文件” > “生成设置...”，打开“生成设置”窗口，然后将平台切换到 Android ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> 有关如何切换生成平台的提示，可参阅[切换生成平台](mr-learning-base-02.md#switching-the-build-platform)中的说明。

关闭“生成设置”窗口。

在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”来打开“MRTK 项目配置器”窗口，确保所有选项都已选中，然后单击“应用”按钮来应用设置    ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

在 Unity 菜单中，选择“编辑” > “项目设置…”来打开播放器设置窗口，然后找到“播放器” >  “其他设置”部分，选择“Vulkan”，然后单击“-”符号将其删除：     

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

关闭“播放器设置”窗口，再次打开“生成设置”窗口。

在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中 。 然后，使用 USB 线缆将 Android 设备连接到计算机，再从“运行设备”下拉列表中将它选中：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> 如果“运行设备”下拉列表中未显示你的设备，则可能需要按下拉列表旁边的“刷新”按钮。

在“生成设置”窗口中，单击“生成并运行”按钮打开“生成 Android”窗口。

选择一个合适的位置来存储生成（例如 D:\MixedRealityLearning\Builds），然后为 apk 提供一个合适的名称（例如 MRTKTutorials-AzureSpatialAnchors），再单击“保存”按钮，开始生成过程 ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
如果在 Unity 控制台窗口中收到任何与 Android SDK、NDK 或 JDK 模块相关的错误，则需要打开 Unity Hub 并安装相关的 Android 生成支持模块。

生成过程完成后，应用应会在 Android 设备上自动加载。

## <a name="building-your-application-to-your-ios-device"></a>将应用程序生成到 iOS 设备

在本部分，你将学习如何配置项目来生成它并将其部署到 iOS 设备。

在 Unity 菜单中，选择“文件” > “生成设置...”，打开“生成设置”窗口，并将平台切换到 iOS ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> 有关如何切换生成平台的提示，可参阅[切换生成平台](mr-learning-base-02.md#switching-the-build-platform)中的说明。

关闭“生成设置”窗口。

在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”来打开“MRTK 项目配置器”窗口，确保所有选项都已选中，然后单击“应用”按钮来应用设置    ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

在 Unity 菜单中，选择“编辑” > “项目设置…”来打开播放器设置窗口，然后找到“播放器” >  “其他设置”部分，取消选中“剪裁引擎代码”复选框来禁用它    ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

关闭“播放器设置”窗口，再次打开“生成设置”窗口。

在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中 ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

在“生成设置”窗口中，单击“生成”按钮打开“生成 iOS”窗口。

选择一个合适的位置来存储 Xcode 项目（例如 D:\MixedRealityLearning\Builds），创建一个新文件夹并为其指定适当的名称（例如 MRTKTutorials-AzureSpatialAnchors），然后单击“选择文件夹”按钮，启动生成过程 ：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

生成过程完成后，按照[导出 Xcode 项目](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)中的说明了解如何将 Xcode 项目部署到 iOS 设备。

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。
