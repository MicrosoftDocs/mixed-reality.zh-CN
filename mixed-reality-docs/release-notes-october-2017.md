---
title: 发行说明-2017 年10月
description: Windows 10 秋季创意者更新的 windows Mixed Reality 发行说明 (10 月 2017)。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 发行说明、版本、windows 10、build、rs3、os
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524097"
---
# <a name="release-notes---october-2017"></a>发行说明-2017 年10月

欢迎使用 Windows Mixed Reality! 发行 **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** 引入了对新支持 [Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)和[动作控制器](motion-controllers.md)，使您能够浏览新领域，玩游戏、 VR 和体验时连接到的沉浸式娱乐[Windows Mixed Reality capable PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。

Windows Mixed Reality 耳机和运动控制器的版本结果了大规模团队工作, 并为[Windows Mixed Reality 平台](mixed-reality.md)(包括[Microsoft HoloLens](hololens-hardware-details.md)) 前进了一大步。 虽然 HoloLens 在 Windows 10 秋季创意者更新版本中未收到更新, 但知道在 HoloLens 上的工作尚未停止;我们将提供很多知识和见解, 适用于整个 Windows Mixed Reality 的最新工作。 事实上, Windows Mixed Reality 沉浸式耳机和运动控制器也是为 HoloLens 开发的一个很好的入门点, 因为相同的 Api、工具和概念同样适用于这两种情况。

若要更新到每个设备的最新版本, 请打开 "**设置**" 应用, 中转到 "**更新" & 安全**", 然后选择"**检查更新**"按钮。 在 Windows 10 电脑上, 还可以使用[windows media 创建工具](https://www.microsoft.com/software-download/windows10)手动安装 Windows 10 秋季创建者更新。

 **最新版本的桌面:** Windows 10 桌面10月 2017 (**10.0.16299.15**, Windows 10 秋季创意者更新)<br>
 **最新版本的 HoloLens:** [Windows 10 全息版8月 2016](release-notes-august-2016.md)(**10.0.14393.0**, Windows 10 周年更新)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Windows Mixed Reality 简介

Windows 10 秋季创意者更新官方介绍了对 Windows Mixed Reality 耳机和运动控制器的支持, 并使 Windows 10 成为了世界上第一个空间操作系统。 要点如下:
* **[各种耳机](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** -Windows Mixed Reality 使合作伙伴能够提供各种耳机, 这些耳机从与运动控制器捆绑在一起的 $399 美元开始。
* **[运动控制器](motion-controllers.md)** -Windows Mixed Reality 运动控制器通过蓝牙与电脑进行无线配对, 并具有六个自由度跟踪、大量输入方法和 IMUs。
* **[简单的设置和可移植性](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** -设置并开始在10分钟内开始。 沉浸式耳机使用内部跟踪来跟踪移动和运动控制器, 具有六个自由度。 不需要任何外部照相机或 lighthouse 标记!
* **[支持更广泛的 pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** -Windows Mixed Reality 允许比以往更多的用户体验桌面版, 并支持从 $499 美元开始的选择集成图形卡和电脑。
* **[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)** -世界上第一个空间操作系统为多任务与2d 应用程序的多任务、启动 VR 游戏和应用程序以及放置装饰性全息影像提供熟悉的家庭环境。
* **[Microsoft Store 中的 Microsoft Store 精彩的 vr 游戏和应用](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** 程序 (如 Hulu vr 和360视频等沉浸式娱乐) 到长篇故事游戏 (如 SUPERHOT
* **[SteamVR 早期访问](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** -Windows 10 秋季创意者更新支持使用 Windows mixed reality 耳机和控制器播放 SteamVR 标题, 从而使 Windows mixed reality 用户可以使用最大的 VR 标题目录。

## <a name="known-issues"></a>已知问题

我们一直在努力提供强大的 Windows Mixed Reality 体验, 但我们仍在跟踪一些已知问题。 如果发现其他人, 请[向我们提供反馈](give-us-feedback.md)。

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 主页中的桌面应用
* 截图工具不适用于桌面应用。
* 桌面应用在重新启动时不会保留设置。
* 如果你在桌面上使用混合现实门户预览, 则在 Windows Mixed Reality 主页中打开桌面应用时, 你可能会注意到无限镜像效果。 
* 运行桌面应用可能会导致非超 Windows Mixed Reality 电脑上出现性能问题;不建议使用此方法。  
* 桌面应用可能会自动启动, 因为桌面上不可见的窗口有焦点。 
* 桌面用户帐户控制提示会使耳机显示黑色, 直到完成提示。

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 安装
* 当使用连接的耳机设置 Windows 时, 电脑监视器可能会留空。 拔出耳机, 使计算机监视器能够完成 Windows 安装程序的输出。
* 创建边界时, 跟踪可能会失败。 如果是这样, 请重试, 因为系统会随着时间的推移详细了解空间。
* 如果在 Windows Mixed Reality 安装过程中打开或关闭 Cortana, 此更改将应用到桌面 Cortana 设置。
* 如果尚未连接耳机, 则在首次访问 Windows Mixed Reality 主页时可能会错过其他提示。
* 蓝牙耳机可能会干扰运动控制器。 建议在 Windows Mixed Reality 会话期间取消配对或关闭蓝牙控制器。

### <a name="games-and-apps-from-windows-store"></a>Windows 应用商店中的游戏和应用
* 在 Windows Mixed Reality 内播放时, 某些以图形方式密集型的游戏 (如 Forza Motorsports 6) 可能会导致不太强大的 Pc 上出现性能问题。

### <a name="audio"></a>Audio
* 如上所述, 蓝牙音频外设不适用于 Windows Mixed Reality 语音和空间音效体验。 它们也可能对运动控制器体验产生负面影响。 建议不要将蓝牙音频耳机用于 Windows Mixed Reality。
* 如果设备未磨损, 则无法使用连接到耳机的音频设备 (或其一部分) 播放耳机进行音频播放。 如果只有一个音频耳机, 可能需要将音频耳机连接到主机 PC, 而不是耳机。 如果是这样, 则必须在 "**设置** > **混合现实** > **音频和语音**" 中关闭 "切换到耳机音频"。
* 某些应用程序 (包括许多通过 SteamVR 启动的应用程序) 可能会在音频设备随着你开始或停止混合现实门户而发生变化时丢失音频或挂起。 打开混合现实门户应用以更正此错误后, 请重新启动应用。
* 如果在使用 Windows Mixed Reality 耳机之前已在主机 PC 上启用 Cortana, 则可能会丢失适用于你在 Windows Mixed Reality 主页上放置的应用的空间声音模拟。 解决方法是在连接到电脑的所有音频设备上启用 "Windows Sonic, 耳机", 甚至是在手机网络上连接的音频设备:
   1. 在桌面任务栏上左键单击扬声器图标, 然后从音频设备列表中选择。
   2. 右键单击桌面任务栏上的扬声器图标, 然后在 "扬声器设置" 菜单中选择 "Windows Sonic 用于耳机"。
   3. 对所有音频设备 (终结点) 重复这些步骤。
>[!NOTE]
> - 由于连接到您的耳机的耳机/扬声器不会显示, 除非您戴在计算机上, 否则您必须在 Windows Mixed Reality home 中的桌面应用程序窗口内执行此操作, 以便将此设置应用到连接到耳机的音频设备 (或集成)。
> - 另一种方法是在启动 Windows Mixed Reality 之前, 在桌面上的 "**设置** > **cortana** " 中关闭 "让 cortana 响应你好 cortana"。

* 当另一个多媒体 USB 设备 (如 web cam) 与 Windows Mixed Reality 耳机共享同一 USB 集线器 (外围设备或 PC 内) 时, 在极少数情况下, 耳机的音频插孔/耳机可能有蜂鸣声或根本没有音频。 你可以将耳机修复为与其他设备不共享同一集线器的 USB 端口, 或者断开连接/禁用其他 USB 多媒体设备。
* 在极少数情况下, 主机 PC 的 USB 集线器无法为 Windows Mixed Reality 耳机提供足够的电量, 你可能会注意到耳机突然出现噪音激增。

### <a name="speech"></a>语音
* Cortana 可能无法播放她的音频提示, 以便聆听/思考和音频响应命令。
* 使用时, 中国和日本市场上的 cortana 不会正确地在 Cortana 圆圈下显示文本。
* 首次在混合现实门户会话中调用 Cortana 时, Cortana 可能会很慢。 可以通过在 "设置**cortana** > **与 cortana 通信**" 下的 "**设置** > cortana" 下, 确保 "允许 cortana 响应你好 cortana"。
* 在不是 Windows Mixed Reality 超 Pc 的 Pc 上, Cortana 的运行速度可能较慢。
* 如果系统键盘设置为 Windows Mixed Reality 中的 UI 语言以外的语言, 则在 Windows Mixed Reality 中使用键盘上的听写将导致错误对话框, 因为没有 Wi-fi 连接而无法正常运行。 若要解决此问题, 只需确保系统键盘语言与 Windows Mixed Reality UI 语言匹配即可。
* 不能正确地将西班牙识别为 Windows Mixed Reality 启用语音的市场。

### <a name="holograms"></a>影像
* 如果你在 Windows Mixed Reality 主页中放置了大量全息影像, 则某些影像可能会消失, 并在你查找时重新出现。 若要避免出现这种情况, 请删除 Windows Mixed Reality 主页的部分全息影像。

### <a name="motion-controllers"></a>运动控制器
* 有时, 如果单击边缘的网页, 内容将会缩放, 而不是单击。
* 有时, 单击边缘中的链接时, 所选内容将不起作用。

## <a name="prior-release-notes"></a>以前的发行说明
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>请参阅
* [沉浸式耳机支持 (外部链接)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 已知问题](hololens-known-issues.md)
* [安装工具](install-the-tools.md)
* [向我们提供反馈](give-us-feedback.md)
