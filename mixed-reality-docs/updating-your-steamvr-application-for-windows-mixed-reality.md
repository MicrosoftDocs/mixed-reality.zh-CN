---
title: 更新 Windows Mixed Reality 应用 SteamVR 程序
description: 有关更新 SteamVR 应用程序，以最大程度地使用 Windows Mixed Reality 耳机的兼容性最佳实践。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，兼容性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590165"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>更新 Windows Mixed Reality 应用 SteamVR 程序

我们建议开发人员测试并优化其 SteamVR 的体验，以在 Windows Mixed Reality 耳机上运行。 本文档介绍了常见开发人员可以进行以确保 Windows Mixed Reality 上出色运行他们的体验的改进。

## <a name="initial-setup-instructions"></a>初始安装说明

若要开始测试出游戏或应用上 Windows Mixed Reality 请确保到第一个按照我们[入门指南。](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>控制器模型
1. 如果您的应用程序呈现控制器模型：
    * 使用[Windows Mixed Reality 运动控制器模型](motion-controllers.md#rendering-the-motion-controller-model)
    * 若要获取本地的使用 IVRRenderModel::GetComponentState 将转换成组件部分 （例如。 指针姿势）
2. 具有表示法的左右手使用习惯的体验应从输入 Api 来区分控制器获取提示[（Unity 示例）](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controls

当设计或调整控件布局记住以下保留命令集：
1. 单击向下**左侧和右侧模拟摇杆**留待**Steam 仪表板**。
2. **Windows 按钮**将始终返回到 Windows Mixed Reality 家庭用户。

如果可能，默认缩略记忆棒基于 teleportation 以匹配[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)teleportation 行为

## <a name="tooltips-and-ui"></a>工具提示和 UI

许多 VR 游戏利用运动控制器工具提示和覆盖层，教用户为他们的游戏或应用程序最重要的命令。 优化 Windows 混合现实应用程序时我们建议查看您的体验，以确保将映射到 Windows 控制器模型的工具提示的这一部分。

另外如果有您的体验，其中显示图像的控制器中的任何点请确保提供更新后的映像使用 Windows Mixed Reality 运动控制器。

## <a name="haptics"></a>Haptics

开头[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)，现在支持 haptics SteamVR 体验 Windows Mixed reality。 如果在 SteamVR 应用或游戏已包含对 haptics 的支持，它应现在使用 （与任何额外工作） [Windows Mixed Reality 运动控制器](motion-controllers.md)。

Windows Mixed Reality 运动控制器使用标准 haptics 马达，而不是在某些其他 SteamVR 运动控制器，这可能会导致略有不同超出预期的用户体验中找到线性传动装置。 因此，我们建议测试和优化 Windows Mixed Reality 运动控制器 haptics 的设计。 例如，有时短 haptic 脉冲 （5-10 毫秒） 是 Windows Mixed Reality 运动控制器上不太明显。 若要生成更明显 pulse，尝试发送较长"单击"(40-70) 能够在汽车的更多时间来启动告知电源再次之前。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>从 Windows 混合现实开始菜单启动 SteamVR 应用

通过流分发 VR 体验，我们已经[SteamVR beta 更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新[Windows Insider](https://insider.windows.com) RS5 航班以便 SteamVR 标题现在显示在自动列出 Windows 混合现实开始菜单中"所有应用"。 与安装下列软件版本，你的客户现在可以不删除其耳机启动 Windows Mixed Reality 家庭内的直接从 SteamVR 标题。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 徽标

若要显示在标题上的 Windows Mixed Reality 支持，请转到"编辑应用商店页"链接应用登陆页面上，单击"基本信息"选项卡上，并向下滚动到"虚拟现实。" 取消选中"隐藏 Windows Mixed Reality"，然后将其发布到应用商店。

## <a name="bugs-and-feedback"></a>错误和反馈

改进 Windows 混合现实 SteamVR 体验时，你的反馈是非常有用。 请提交的所有反馈和通过的 bug [Windows 反馈中心](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)。 下面是一些[有关如何使 SteamVR 反馈尽可能为有用的提示](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)。

如果你有疑问或要共享的注释，也可以访问我们在我们[Steam 论坛](http://steamcommunity.com/app/719950/discussions/)。

## <a name="faqs-and-troubleshooting"></a>常见问题和疑难解答

如果运行的常规问题设置还是播放你的体验，[查看最新故障排除步骤](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。

## <a name="see-also"></a>请参阅
* [安装工具](install-the-tools.md)
* [耳机和动作控制器驱动程序历史记录](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 最小 PC 硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
