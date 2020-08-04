---
title: Azure 云教程 - 3. 集成 Azure 自定义视觉
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 自定义视觉。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, 实用工具, 教程, hololens, hololens 2, azure 自定义视觉, azure 认知服务
ms.localizationpriority: high
ms.openlocfilehash: 0fc3793315dd05f91a6193b68343205f53a3092a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376459"
---
# <a name="3-integrating-azure-custom-vision"></a>3.集成 Azure 自定义视觉

在本教程中，你将了解如何使用 Azure 自定义视觉。你将上传一组照片，将其与被跟踪对象关联，然后再上传到“自定义视觉”服务并开始训练过程。 然后，通过从网络摄像头源捕获照片，使用该服务来检测被跟踪对象。

## <a name="objectives"></a>目标

* 了解有关 Azure 自定义视觉的基础知识
* 了解如何设置场景以在此项目中使用自定义视觉
* 了解如何集成上传、训练和检测图像

## <a name="understanding-azure-custom-vision"></a>了解 Azure 自定义视觉

Azure 自定义视觉属于认知服务系列，可用于训练图像分类器 。 图像分类器是一种 AI 服务，它使用经过训练的模型来应用匹配标记。 应用程序将使用此分类功能来检测被跟踪对象。

详细了解 [Azure 自定义视觉](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。

## <a name="preparing-azure-custom-vision"></a>为 Azure 自定义视觉做好准备

在开始之前，请创建一个自定义视觉项目，最快的方法是使用 Web 门户。

按照以下[快速入门教程](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)中“上传和标记图像”之前的部分设置你的帐户和项目。

> [!WARNING]
> 若要训练模型，至少需要 2 个标记，每个标记 5 张图像。 若要使用此应用程序，至少应创建一个涵盖 5 张图片的标记，这样之后的训练过程才不会失败。

## <a name="preparing-the-scene"></a>准备场景

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

从此处将预制件 ObjectDetectionManager 拖到场景层次结构中。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

在“层次结构”窗口中，找到并选中 ObjectDetectionManager 对象。
ObjectDetectionManager 预制件包含“ObjectDetectionManager(脚本)”组件，你可从“检查器”窗口中看到，它取决于多项设置 。

## <a name="retrieving-azure-api-resource-credentials"></a>检索 Azure API 资源凭据

可从 Azure 门户和自定义视觉门户检索“ObjectDetectionManager(脚本)”设置所需的凭据。

### <a name="azure-portal"></a>Azure 门户

查找并找到你在本教程的“准备场景”部分中创建的“认知服务”类型的自定义视觉资源。 然后，单击“密钥和终结点”，以检索所需的凭据。

### <a name="custom-vision-dashboard"></a>自定义视觉仪表板

在[自定义视觉](https://www.customvision.ai/projects)仪表板中，打开已为本教程创建的项目，并单击页面右上角的齿轮图标以打开“设置”页。 此时，你可在“资源”部分中找到所需的凭据。

现在，通过“ObjectDetectionManager(脚本)”安装程序，找到并选中场景层次结构中的 SceneController 对象 。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

你将看到 SceneController 组件中“对象检测管理器”字段为空，将 ObjectDetectionManager 从层次结构拖到该字段中并保存场景 。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>拍摄和上传图像

运行场景并单击“设置对象”，键入在[上一课](mr-learning-azure-02.md)中创建的某一被跟踪对象的名称 。 现在，单击“计算机视觉”按钮，你可在“对象卡片”底部找到 。

此时将打开一个新窗口，请务必使用六张照片训练模型以进行图像识别。 如果想查找要跟踪的对象，请单击“相机”按钮并执行 AirTap，执行该操作六次。

> [!TIP]
> 若要改进模型训练，请尝试从不同角度和照明条件下拍摄每张图像。

获得足够的图像后，单击“训练”按钮，开始云中的模型训练过程。 启动训练后，系统将上传所有图像，然后开始训练，这一过程可能需要一分钟或更长时间。 菜单中一条消息会指示当前进度，一旦消息指示完成，你便可以停止应用程序

> [!TIP]
> “ObjectDetectionManager(脚本)”会直接将拍摄的图像上传到自定义视觉服务。 作为一种替代方法，自定义视觉 API 接受图像 URL，你可以练习修改“ObjectDetectionManager(script)”，将图像上传到 Blob 存储。

## <a name="detect-objects"></a>检测对象

现在，你可以测试训练后的模型，运行应用程序并从主菜单中单击“搜索对象”，然后键入相关的被跟踪对象的名称 。 随即将显示“对象卡片”，单击“自定义视觉”按钮 。 自此，ObjectDetectionManager 将开始在后台使用相机拍摄图像，菜单上将指示进度。 将相机指向你用于训练模型的对象，你将看到相机在一小段时间后会检测到对象。

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何使用 Azure 自定义视觉来训练图像，并使用分类服务来检测与关联的被跟踪对象匹配的图像。

在下一教程中，你将学习如何使用 Azure 空间定位点将被跟踪对象与物理世界中的某个位置关联在一起，以及如何显示一个将引导用户返回到被跟踪对象的关联位置的箭头。

[下一教程：4.集成 Azure 空间定位点](mr-learning-azure-04.md)
