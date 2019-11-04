---
title: MRTK 版本2入门
description: 对于对利用 MRTK 感兴趣的新开发人员
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality，测试，混合现实工具包，MRTK 版本2，MRTK，工具，SDK，HoloLens，HoloLens 2
ms.openlocfilehash: 46a06b951ae9aa60259f70be3fa1e558e7ab8ab6
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438343"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 入门

## <a name="mrtk-getting-started-guide"></a>MRTK 入门指南
有关 MRTK V2 入门的详细信息，请参阅[MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>什么是混合现实工具包（MRTK）？
MRTK 是一种令人惊叹的开源工具包，它是自2015首次发布后开始的，并不是我们的开发人员社区的硬性工作，而是目前为止。 过去3年来，我们已听取开发人员社区的反馈，并构建了 MRTK v2，以考虑最大的问题。  

适用于 Unity 的 MRTK v2 是一个面向混合现实应用程序的开源跨平台开发工具包。  MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。 

有关详细信息，请参阅[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。

## <a name="new-with-mrtk-v2"></a>新的 MRTK v2
我们想要对这些平台工具的承诺施加压力。  事实上，我们利用 MRTK 版本2来开发收件箱体验，例如安装体验（OOBE）和混合现实学习应用程序。  你还可以看到新的 HoloLens 2 功能首次通过 MRTK 公开，因为我们认为这是在我们的平台上进行开发的最佳方式。 

### <a name="modular"></a>模块化
我们采用模块化方式构建了它，因此您无需将该工具包的每个套件都引入到您的项目中。  这样做实际上只有几个优点。  它可以使项目大小保持较小，并使其更易于管理。  基于这一点，因为它是用可编写脚本的对象构建的，并且是接口驱动的，所以还可以替换您自己的组件，以支持其他服务、系统和平台。

### <a name="cross-platform"></a>跨平台
说到其他平台，它具有跨平台支持。  虽然这并不意味着每个平台都受支持，但我们确保在将生成目标切换到其他平台时，不会中断任何工具包代码。  模块化设计的可靠性和扩展性使你能够支持多个平台，如 ARCore、ARKit 和 OpenVR。

### <a name="performant"></a>高性能
使用移动平台时，我们构建了性能方面的考虑因素。  这非常重要，我们想要确保这些工具不会与你一起工作。

## <a name="see-also"></a>另请参阅
* [MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 文档主页](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安装工具](install-the-tools.md)
* [从 HTK/MRTK 迁移到 MRTK 版本2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
