---
title: 案例研究-来自 Lowe 厨房的课程
description: HoloLens 团队想要分享一些派生自 Lowe HoloLens 项目的最佳实践。
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，Lowe，HoloLens，厨房，案例研究
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278125"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>案例研究-来自 Lowe 厨房的课程

HoloLens 团队想要分享一些派生自 Lowe HoloLens 项目的最佳实践。 下面是 Lowe 的 HoloLens 计划的视频，其中演示了 Satya 的 2016 Ignite 主题。
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowe 的 HoloLens 最佳实践

这两个视频覆盖了自2016年4月起，从 Lowe 的 HoloLens 试点派生的最佳实践。 关键主题包括：
* 最大化移动设备性能
* 创建具有完整全息帧的 UX 方法（第二个讨论）
* 精度对齐（第二个讨论）
* 共享全息体验（第二个讨论）
* 与客户交互（第二次交谈）

## <a name="video-1"></a>视频1

**最大化移动设备性能**HoloLens 是在设备中进行所有处理的 untethered 设备。 这需要移动平台，并且需要类似于创建移动应用程序的思维方式。 Microsoft 建议你的 HoloLens 应用程序维护60FPS，为你的用户提供可口体验。 低 FPS 会导致不稳定的全息影像。

在 HoloLens 上进行开发时，需要注意的一些最重要的事项是使用自定义着色器（在[Hololens 工具包](https://github.com/Microsoft/HoloToolkit-Unity)中免费提供）的资产优化/decimation。 另一个重要的考虑因素是从项目的最开始度量帧速率。 根据项目的不同，显示资产的顺序也可能是一个大参与者
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>视频2

**使用完整全息帧创建 UX 方法**了解影像在物理世界中的位置非常重要。 通过 Lowe，我们讨论了不同的 UX 方法，这些方法可帮助用户在出现全息影像的更大环境时，使其保持关闭状态。

**精度对齐**对于 Lowe 的应用场景，使全息影像与物理厨房实现精确对齐非常重要。 我们讨论的技术有助于确保结论用户的物理环境更改的体验。

**共享全息体验**使用方式是 Lowe 的体验的主要方式。 一个人可以更改台面，其他人将看到所做的更改。 我们称之为 "共享体验"。

**与客户交互**Lowe 的设计器不使用 HoloLens，但需要查看客户的情况。 本文介绍如何捕获客户在 UWP 应用程序上看到的内容。
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
