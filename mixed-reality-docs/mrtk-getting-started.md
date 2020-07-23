---
title: MRTK 版本 2 入门
description: 面向有兴趣利用 MRTK 的新开发人员
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: a7fdd7b199530b38fb0921baa57d9783fa45672a
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447884"
---
# <a name="getting-started-with-mrtk-for-unity"></a>MRTK for Unity 入门
![MRTK](images/UX/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>混合现实工具包 (MRTK) 是什么？
MRTK 是一个很神奇的开源工具包，自 HoloLens 首次发布后推出。它有现在这样的地位离不开为其贡献内容的开发人员社区的辛勤工作。 在过去 3 年里，我们听取了开发人员社区的反馈，在构建 MRTK v2 时考虑到了大家最关注的一些事项。  

MRTK for Unity 是一款面向混合现实应用程序的开源跨平台开发工具包。 MRTK 为空间交互提供了跨平台的输入系统、基础组件和常用的构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

要了解详细信息，请参阅 [GitHub 上的 MRTK 相关文档](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。

## <a name="new-with-mrtk-v2"></a>MRTK v2 新增功能
我们想要强调一下我们对这些平台工具的承诺。  事实上，我们利用 MRTK 第 2 版开发了我们的内置体验，例如设置体验 (OOBE) 和混合现实学习应用程序。  另外，你还会看到首先通过 MRTK 公开的全新 HoloLens 2 功能，因为我们认为这是在我们的平台上进行开发的最佳方式。 

### <a name="modular"></a>模块化
构建它时，我们采用了模块化方式。因此，你不需要将此工具包的所有组件都放到项目中。  实际上，这样做有一些好处。  缩小你的项目，使之更易于管理。  另外，由于我们在构建它时使用了可脚本化的对象，并且它是接口驱动型的，因此你也可以将它附带的组件替换为你自己的，这样就可以支持其他服务、系统和平台。

### <a name="cross-platform"></a>跨平台
说到其他平台，必须指出的是，它提供跨平台支持。  虽然这并不意味着我们会对每个平台提供现成的支持，但我们可以保证：当你将生成目标切换到其他平台时，工具包代码的任何部分都不会崩溃。  模块化设计稳定可靠且具有可扩展性，因此能够支持多个平台，例如 ARCore、ARKit 和 OpenVR。

### <a name="performant"></a>高性能
由于要使用移动平台，因此我们在构建它时必须时时刻刻考虑到性能。  这相当重要，我们需要确保这些工具不会给你造成麻烦。

## <a name="see-also"></a>另请参阅
* [MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 文档主页](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安装工具](install-the-tools.md)
* [从 HTK/MRTK 移植到 MRTK 第 2 版](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
