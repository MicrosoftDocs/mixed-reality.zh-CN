---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 7fe3c96cf7b888a4a91960147270be81a0973980
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485758"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a>3.  添加 Azure 认知服务语音翻译组件

在本教程中, 我们将了解如何 aabout 项目中的 Azure 认知服务语音翻译组件, 并将其翻译为三种不同的语言。 

## <a name="instructions"></a>说明

1. 选择层次结构中的 Lunarcom_Base 对象, 并在 "检查器" 面板中单击 "添加组件"。 搜索并选择 "LunarcomTranslationRecognizer"。

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> 注意:请确保在测试 Speech SDK 转换器之前禁用了脱机模式模拟器。 若要进行转换, 必须连接到 internet。 请参阅下图中的查找此设置的位置。 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. 单击 LunarcomTranslationRecognizer 中的下拉箭头, 然后选择要转换为的语言。

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. 现在, 运行该应用程序并通过单击 "附属项" 按钮来测试转换器, 然后开始说话。 再次按卫星按钮以停止识别。 下面是场景外观的示例。 可以随时更改 "目标语言" 下拉列表下的语言 (请参阅上图), 以浏览其他语言的翻译。

> 注意:在测试之前, 请确保脱机模拟器已禁用, 如下图所示。
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

以下是场景外观的示例:

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>祝贺

现在, 您的项目可以将您所说的字词转换为多种不同的语言。 可以自由地利用语言, 并测试翻译的准确性。 

[下一教程:4.设置意向和自然语言理解](mrlearning-speechSDK-ch4.md)

