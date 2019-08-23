---
title: 具有 Windows Mixed Reality 的基于位置的娱乐
description: 获取对 Unity 中的基础全息本机对象的访问权限。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: mixed reality, vr, lbe, location
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983395"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>具有 Windows Mixed Reality 的基于位置的娱乐

在过去几年中, 我们在基于地点的娱乐类别中观察到了惊人的增长和创新。 传统的会场 (如主题公园和 theatres) 已开始提供沉浸式多玩家体验, 作为现有搭乘和安装的免费体验。 新的操作员和会场为面向大众带来了独特的多 sensorial、多玩家体验。 所有这些经验都是通过推送信封来实现混合现实。

本文档是在基于位置的娱乐类别中开始使用 Windows Mixed Reality 的指南。 以下指南可能还适用于超出娱乐的位置体验, 例如培训、产品设计或其他用例。

## <a name="engineering-faq"></a>工程常见问题

### <a name="hardware"></a>硬件

**:Microsoft 及其合作伙伴提供了哪些可在我的设置中使用的硬件？**

答：Microsoft 及其 OEM 合作伙伴提供了一套诱人的设备, 可根据需要进行选择。  

如果你向客户提供的体验需要虚拟现实耳机, 则 HP、Samsung 和 Acer 的以下市场耳机都非常合适。 每个耳机都有其各自的不同属性。 以下各项的详细信息。

HP 回音:[详细信息](https://hp.com/go/Reverbpro)

Samsung 太空 +:[详细信息](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer:[详细信息](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

如果你的位置专门从事需要使用 "查看-通过" 耳机的混合或增加的现实体验, 则可以购买 Microsoft HoloLens 2 (现已打开, 用于提前订购)。  

HoloLens 2:[预处理利息](https://www.microsoft.com/en-us/hololens/buy)

如果你正在试验需要高级计算机视觉、语音和正文跟踪的体验, 你可能会发现, Azure Kinect 深色适用于你的需求。  

Azure Kinect:[详细信息](https://azure.microsoft.com/en-us/services/kinect-dk/)

**:我可以使用哪些背包电脑组合来运行我的电脑-受限 VR 体验？**

对于电脑受限 VR 体验, 我们的 Oem 提供了令人难以置信地选择的背包 Pc。

HP 刚刚启动了其 HP VR 背包 G2, 这是世界上最强大的可穿戴 PC –为自由漫游体验进行了优化, 现在, 在内部使用 RTX 2080 GPU 可提高 30% 的电量。 [详细信息](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>安装

**:如何更轻松地配置安装并为 LBE 自定义混合现实门户？**

>[!NOTE]
>此功能需要2000.19061.1011.0 或更高版本。  

你可能会发现, 你需要对混合现实门户进行更多的自定义, 而不是通常通过用于将应用部署到展台或自定义体验的应用使用。 混合现实门户的最新7月更新支持多个高级设置, 这些高级设置可以通过配置文件执行以下操作:  

允许故障系统检查–在完成安装程序之前, 安装过程通常会检查 PC 与 Windows Mixed Reality 的兼容性。 如果出现兼容性问题, 则在尝试运行 Windows Mixed Reality 时, 绕过这种情况可能会导致问题。  

跳过设备辅助应用– DCA 提供制造商提供的耳机特定的设置步骤, 并允许更新耳机固件。  

跳过房间安装-不会提示创建房间边界, 你可以直接转到处于固定/放置模式的耳机。  

跳过从应用商店安装应用-普通安装程序将安装多个应用商店应用, 包括3D 查看器和 Edge 360 查看器加载项。 这会跳过这些应用的安装, 但可能缺少设备功能。  

全屏显示预览–混合现实门户将默认为在使用耳机时在台式计算机上全屏显示耳机预览。  

隐藏你的面板的新用户-这会阻止在启动混合现实门户时展开 "新建" 面板。  

#### <a name="how-to-configure"></a>如何配置:  

若要设置这些配置中的任何一种, 需要在此目录下创建一个名为_userconfig.psm1_的文件: _\\ $env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_

对于大多数用户, 这将类似_于\<C:\Users username >\\ \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_

对于您想要启用的任意设置, JSON 文件的内容应为 "true":  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**:是否有关于配置 playspace 的指导？**

答：应按照使用者安装体验来配置 playspace。 房间设置过程还将允许您定义房间边界。 有关配置空间边界的详细信息, 请参阅[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)。

如以上文档中所述, 最大合理的单个坐标 playspace 是围绕5mx5m 的。 如果要获得更大的区域, 可以使用 Windows 全息 API 堆栈中的空间锚功能。 使用此 API 需要在生成的体验中进行自定义工程。  

可在[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems)阅读有关如何针对不同的空间大小优化内容的更多详细信息。
 

**:我的空间太大了, 在尝试使用边界建立持续的体验时, 我遇到了错误。设置大的免费漫游体验应该怎么办？**

答：若要设置比 ~ 18x18ft 更大的空间, 你将无法使用系统提供的边界体验。  边界系统依赖于单个固定坐标 "锚点", 当用户离中心舞台锚点太远时, 这会变得不稳定。 

相反, 您可以设置 "固定" 模式, 这种模式不会显示边界, 也不会配置阶段边界或 playspace。  然后, 需要在应用内配置多个空间锚点以引用物理边界区域。 

应用程序开发人员负责显示必要的安全措施, 使用户不会与物理环境发生冲突。  这可能是经验或自定义游戏边界视觉对象中的数字背景。 

可在[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到有关通过 WMR 设置空间边界的指南。

**:Playspace 的来源是什么？**

答：Playspace 的来源取决于房间安装体验, 更具体地说是在安装过程中按下中心按钮时的 HMD 位置。 

### <a name="multi-player-setup"></a>多玩家安装

**:我将在我的场所部署多玩家体验。Windows Mixed Reality 是否支持？**

答：混合现实空间数据包装器工具是一项 beta 功能, 可通过启用将空间数据从一台电脑移植到另一台电脑, 使多个播放器在同一空间中进行本地化。 可以访问该工具, 并在[此处](mixedrealityspatialdatapackager.md)了解更多相关信息。

### <a name="tracking"></a>字距

问:Windows Mixed Reality 耳机中的跟踪技术是如何工作的？  

混合现实与 HoloLens 共享相同的跟踪技术。 若要详细了解内部输出跟踪系统, 请查看[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system)的文档。

有关更高级的空间映射系统的工作原理的说明, 请参阅[此处](spatial-mapping-design.md)的说明。

**:获取可靠跟踪卷是否有任何最佳实践？**

为了最好地配置用于跟踪成功的环境, 您可以阅读此[文章](environment-considerations-for-hololens.md)中的最佳实践。

**:对于仓库规模空间或要考虑的优化, 是否存在任何特定的细微差别？**

答：以下做法可帮助获取更可靠的跟踪卷:  

在房间中提供不同于多个位置的功能将有助于跟踪系统获得稳定的锁定。 请考虑随机绘制 splatters 和阴影, 而不是使用纯色等高线样式线条。 

尽可能最大程度地减小区域中的光线的动态范围。 混合现实 HMDs 上的跟踪相机不是 HDR, 具有 AGC (自动增益) 和 AEC (自动曝光), 以便处理不同的照明。 根据表面光、模式和对比度的分布情况, AGC 或 AEC 可能会假设您的所有白色或黑色房间都能冲蚀您的功能, 这种情况可能会与 "颜色" 相反。 如果你正在尝试在具有鲜日光的外部窗口的前方拍摄内部图片, 并调整了曝光以便查看外的详细信息, 则内部的所有内容都是 underexposed 和黑色。 或者, 如果在内部设置, 则所有外部的内容现在都是 overexposed, 所有白色。  

如果跟踪相机有时原因, 则在房间 (甚至是开销) 中进行聚光灯, 这会混淆跟踪相机的 AEC/AGC。 平面/散射照明可帮助。  

### <a name="mixed-reality-cloud-services-and-azure"></a>混合现实云服务和 AZURE 

**:Microsoft Azure 如何帮助我的业务规模？**

答：基于 Azure 的现场和远程管理可帮助你的业务进行数据驱动, 降低运营成本并在现有和新位置扩展部署。 Azure 云服务 (例如 Azure 存储、Azure Functions、应用服务、Azure 网络和 IOT 中心) 可帮助解决以下用例:  

远程设备部署 & 管理 

实时现场分析 

智能适应性 LBE 游戏 

LBE 内容流式处理和部署 

LBE Player 首选项热度地图 

LBE 预订系统和预订系统 

**:我要开发一个空间 MMOG, 以通过大量的空间来进行部署。有助于管理内容和对象持久性的任何服务？**

答：Azure 空间锚点是一项新的混合现实服务, 可在 HoloLens、iOS 和 Android 设备上实现多用户、空间丰富的混合现实体验。 可在[此处](https://azure.microsoft.com/en-us/services/spatial-anchors/)了解有关 Azure 空间定位点的详细信息。

**:.我们的场地专用于多玩家体验, 我想将开发时间集中在内容和前端开发上。是否有可帮助我启动或卸载后端开发的产品？**

答：Azure PlayFab 是适用于现场游戏的完整后端平台。 可在[此处](https://playfab.com/)了解详细信息。

### <a name="misc"></a>Misc

**:我使用 SteamVR 部署我的体验。Windows Mixed Reality 是否适用于 SteamVR？**

答：适用于 SteamVR 的 windows Mixed Reality 允许用户在 Windows Mixed Reality 沉浸式耳机上运行 SteamVR 体验。 [在此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)了解有关 SteamVR 的详细信息。

### <a name="support-and-community"></a>支持和社区  

下面是一些有用的资源, 这些资源可与我们团队的行业专家进行交流、获取故障排除支持, 并为更广泛的混合现实开发社区提供支持。  

如果遇到任何公开发布功能的问题, 请使用反馈中心提交 bug。有关指南, 请参阅此[页](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback)。

有关 WMR 的其他故障排除帮助, 请通过填写[支持请求](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)与我们的客户支持团队联系。

加入我们的 HoloDevelopers 时差通道, 与团队的混合现实和主题专家合作开发人员: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter关注混合现实开发人员关系团队, 以获取新闻、活动和更新@MxdRealityDev 

如果你的工作发生在旧金山或周围, 则 Microsoft 反应器中始终会出现一些问题。 [此处](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco)可以看到我们的事件日历。