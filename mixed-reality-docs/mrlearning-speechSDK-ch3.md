---
title: Azure 语音服务教程-3。 添加 Azure 认知服务语音翻译组件
description: 在本课程中，你将了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143234"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. 添加 Azure 认知服务语音翻译组件

在本教程中，你将了解你的项目的 Azure 认知服务语音翻译组件以及如何转换为三种不同的语言。

## <a name="instructions"></a>说明

1. 选择层次结构中的 "Lunarcom_Base" 对象，然后在 "检查器" 面板中单击 "添加组件"。 搜索并选择 Lunarcom 转换识别器。

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    禁用脱机模式模拟器。

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >在继续之前，请确保在测试 Speech SDK 转换器之前禁用了脱机模式模拟器（如上图所示）。 若要进行转换，必须连接到 internet。

2. 单击 Lunarcom 转换识别器中的下拉箭头，然后选择要转换为的语言。

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. 运行应用程序并通过单击 "附属项" 按钮来测试转换器，开始说话。 再次按卫星按钮以停止识别。 下面是场景外观的示例。 可以随时更改 "目标语言" 下拉列表下的语言（请参阅上图），以浏览其他语言的翻译。

    以下是场景外观的示例：

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>祝贺

你的项目现在可以成功地将你说的字词转换为多种不同的语言。 可以自由地利用语言，并测试翻译的准确性。

[下一教程： 4. 设置意向和自然语言理解](mrlearning-speechSDK-ch4.md)
