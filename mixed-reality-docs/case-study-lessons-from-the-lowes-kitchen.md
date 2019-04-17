---
title: 案例研究-从 Lowe 的厨房获得的教训
description: HoloLens 团队想要分享一些衍生 Lowe 的 HoloLens 项目的最佳实践。
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 Lowe 的、 HoloLens、 厨房、 案例研究
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591750"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>案例研究-从 Lowe 的厨房获得的教训

HoloLens 团队想要分享一些衍生 Lowe 的 HoloLens 项目的最佳实践。 下面是投影 Lowe 的 HoloLens 的视频演示了 Satya 的 2016 Ignite 主题。
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowe 的 HoloLens 最佳实践

两个视频介绍衍生自 2016 年 4 月以来一直驻留在两个 Lowe 存储 Lowe 的 HoloLens 试验的最佳实践。 关键主题包括：
* 最大限度地移动设备的性能
* 创建具有完整 holographic 帧 UX 方法 （第 2 个对话）
* 精度的对齐方式 （第 2 个对话）
* 共享 holographic 体验 （第 2 个对话）
* 与客户交互 （第 2 个对话）

## <a name="video-1"></a>视频 1

**使移动设备的性能最大化**HoloLens 是无约束的设备的设备中发生的所有处理。 这需要移动平台并且思维方式类似于创建移动应用程序。 Microsoft 建议您 HoloLens 的应用程序维护 60 FPS，若要为用户提供一种美味体验。 具有较低的每秒帧数可能会导致不稳定全息。

一些最重要的事情，若要查看在 HoloLens 上进行开发时资产优化/抽取，使用自定义着色器 (免费提供[HoloLens 工具包](https://github.com/Microsoft/HoloToolkit-Unity))。 另一个重要的考虑因素是项目的度量值从一开始您的帧速率。 具体取决于该项目，显示你的资产的顺序也可以是大参与者
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>视频 2

**创建具有完整 holographic 帧 UX 方法**务必了解全息物理世界中的位置。 使用 Lowe 的我们讨论有关帮助的用户注册体验全息关闭同时仍可以查看全息的较大环境的不同用户体验方法。

**精度对齐**为 Lowe 的方案中，它是至关重要的体验，没有到物理厨房全息精度对齐方式。 我们将讨论的技术有助于确保使其物理环境已更改的用户的体验。

**共享 holographic 体验**将紧密结合起来都使用 Lowe 的体验的主要方法。 一个人可以更改台面上，其他人将看到所做的更改。 我们调用了此"共享体验"。

**与客户交互**Lowe 的设计器不使用 HoloLens，但他们需要查看客户看到的内容。 我们演示如何捕获客户 UWP 应用程序上看到的内容。
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
