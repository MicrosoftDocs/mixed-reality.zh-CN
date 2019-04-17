---
title: 发行说明-2018 年 4 月
description: HoloLens 和 Windows Mixed Reality 发行说明适用于 Windows 10 2018 年 4 月更新 (也称为 RS4)。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: 发行说明、 版本、 windows 10、 生成、 rs4、 os
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592166"
---
# <a name="release-notes---april-2018"></a>发行说明-2018 年 4 月

 **[Windows 10 2018 年 4 月更新](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (也称为 RS4) 包括 HoloLens 和 Windows Mixed Reality 沉浸式耳机连接到 Pc 的新功能。 

若要更新到任一设备类型的最新版本，请打开**设置**应用程序中，转到**更新和安全**，然后选择**检查更新**按钮。 在 Windows 10 PC 上，您还可以手动安装 Windows 10 2018 年 4 月更新使用[Windows 媒体创建工具](https://www.microsoft.com/software-download/windows10)。

**面向桌面的最新版本：** Windows 10 2018 年 4 月更新 (**10.0.17134.1**)<br>
**HoloLens 的最新版本：** Windows 10 2018 年 4 月更新 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*一条消息从 Alex Kipman 和新混合的现实中的功能概述 Windows 10 2018 年 4 月更新*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>用于 Windows Mixed Reality 沉浸式耳机的新功能

Windows 10 2018 年 4 月更新包括许多与桌面 PC，如使用 Windows Mixed Reality 沉浸式 (VR) 耳机改进： 

* **新环境家庭混合现实**-现在可以通过选择选择 Cliff 房屋与新的 Skyloft 环境之间**位置**开始菜单上。 我们还添加了[实验性功能](add-custom-home-environments.md)这会让你可以使用已创建的自定义环境。
* **快速访问混合的现实捕获**-现在可以使用 motion 控制器的混合的现实照片。 保存 Windows 按钮，然后点击该触发器。 这可在环境和应用程序，但将不会捕获受 DRM 保护的内容。
* **启动和重设大小的内容的新选项**-只有当从开始菜单启动，在您面前现在会自动添加这些应用。 现在还可以通过拖动边缘和角窗口来调整 2D 应用程序。
* **轻松地跳转到"teleport"语音命令与内容**-你可以现在快速 teleport 为 Windows Mixed Reality 家庭中的内容之前，内容在观望和说"teleport。"
* **[经过动画处理的 3D 应用启动器](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines)并[装饰性三维对象](enable-placement-of-3d-models-in-the-home.md)家庭混合现实的**-现在可以将动画添加到的 3D 应用程序启动器，并允许用户将放置到的网页或 2D 应用装饰性三维模型Windows Mixed Reality 家庭。
* **[对 Windows Mixed Reality for SteamVR 改进](updating-your-steamvr-application-for-windows-mixed-reality.md)** -Windows Mixed Reality 的 SteamVR 不足"早期 access"的新的升级，包括： haptic 反馈时使用 motion 控制器、 改进的性能和可靠性，并改进的外观，SteamVR 中的动作控制器。
* **其他改进**-自动性能设置已更新，以提供更优化的体验 (您可以[手动重写](#visual-quality)此设置)。 安装程序现在提供了有关更多详情常见兼容性问题使用 USB 3.0 控制器和图形卡。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 年 4 月更新已到达的所有 HoloLens 客户 ！ 此更新打包，因为 HoloLens 软件中的最后一个主要版本引入了改进[2016 年 8 月](release-notes-august-2016.md)。

### <a name="for-everyone"></a>为每个人

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>自动布局上启动的 2D 和 3D 内容</td><td>2D 应用启动器或 2D UWP 应用自动的位置处的最佳大小和距离，而不是要求用户将其置于启动时的环境。 如果<a href="app-views.md">沉浸式应用程序</a>使用 2D 应用启动程序而不是<a href="3d-app-launcher-design-guidance.md">三维应用启动器</a>，沉浸式应用程序将自动启动从 2D 应用启动器相同如 RS1 中所示。<br><br>从开始菜单的 3D 应用程序启动器还自动-位置世界中。 而不是自动启动该应用程序，用户然后可以单击启动器启动沉浸式应用程序。 打开从全息应用和边缘的三维内容还自动-位置世界中。</td><td>当从开始菜单中打开应用，你将不再需要将其放在世界上。<br><br>如果 2D 应用 /<a href="3d-app-launcher-design-guidance.md">三维应用启动器</a>放置并非最佳选择，您可以轻松地将它们使用新的流畅应用操作，如下所述。 您还可以重新定位 2D 应用启动器/三维内容通过"移动此"，然后使用视线移动以重新定位内容。</td>
  </tr>
  <tr>
    <td>流畅的应用程序操作</td><td>移动、 调整大小，和无需输入"调整"模式下旋转 2D 和 3D 内容。</td><td>若要移动的 2D UWP 应用或 2D 应用程序启动程序，只需注视其应用程序栏，然后使用点击 + 保存 + 拖动手势。 可以通过在对象上任意位置观望移动三维内容，然后使用点击 + 按住 + 拖动。<br><br>若要调整大小 2D 内容，注视其角。 视线移动光标将转变为调整大小的光标，，然后点击 + 按住 + 拖动以调整大小。 此外可以通过查看它的边缘并拖动 2D 内容高度或宽度。<br><br>若要调整大小 3D 内容，提起注册这两个手到手势帧，手指在准备好的位置。 你将看到光标将变为 2 个小手的状态。 不要点击并按住用这两个手的手势。 将移近或远手会更改对象的大小。 移动您手中向前和向后相对于彼此将旋转对象。 您还可以调整大小/旋转 2D 内容这种方式。</td>
  </tr>
  <tr>
    <td>使用重排的 2D 应用水平调整大小</td><td>若要查看更多应用程序内容的纵横比中进行更广泛的 2D UWP 应用。 例如，使邮件应用程序足够宽，以显示预览窗格。</td><td>只需注视 2D 的 UWP 应用，请参阅大小调整光标，则使用点击 + 保存 + 拖动手势来调整大小的左或向右边缘。</td>
  </tr>
  <tr>
    <td>扩展的语音命令支持</td><td>您可以执行更多只需使用您的声音。</td><td>请尝试这些语音命令：<ul><li>"转到开始"-将显示开始菜单或退出<a href="app-views.md">沉浸式应用程序</a>。</li><li>"移动此"-允许您移动的对象。</li></ul></td>
  </tr>
  <tr>
    <td>更新的全息和照片应用程序</td><td>具有新全息更新的全息应用。 更新后的照片应用。</td><td>您会注意到全息和照片应用更新后的外观。 全息应用包括几个新全息和更轻松地创建文本标签创建者。</td>
  </tr>
  <tr>
    <td>改进了混合的现实捕获</td><td>硬件快捷方式开始和结束 MRC 视频。</td><td>保留提高音量 + 向下的键为 3 秒开始录制 MRC 视频。 再次点击两者，或使用布隆手势结束。</td>
  </tr>
  <tr>
    <td>合并的空格</td><td>简化全息到单个空格的空间的管理。</td><td>HoloLens 会自动，找到你的空间，且不再需要管理或选择空间。 如果有全息围绕你的问题，则可以转到<b>设置 > 系统 > 全息 > 删除附近全息</b>。 如果需要还可以选择<b>删除所有全息</b>。</td>
  </tr>
  <tr>
    <td>改进了音频浸入式</td><td>现在可以在嘈杂的环境中更好地了解 HoloLens 和体验更逼真的声音，从应用程序，如它们的声音将会被检测到的设备的实际墙的遮盖。</td><td>您无需执行任何操作即可享受的改进空间声音。</td>
  </tr>
  <tr>
    <td>文件资源管理器</td><td>移动和删除文件和 HoloLens。</td><td>可以使用<b>文件资源管理器</b>应用移动和删除文件和 HoloLens。<br><br><b>更改暂存文件夹路径</b>如果看不到任何文件，则"最近"筛选器可能处于活动状态 （时钟图标在左窗格中将突出显示）。 若要解决问题，请选择<b>此设备</b>文档 （时钟图标），下方的左窗格中的图标或打开的菜单并选择<b>此设备</b>。
</td>
  </tr>
  <tr>
    <td>MTP （媒体传输协议） 的支持</td><td>轻松传送在 HoloLens 上启用桌面 PC 来访问您的库 （照片、 视频、 文档）。</td><td>类似于其他移动设备连接到您的 PC 以显示你 HoloLens<b>文件资源管理器</b>若要访问您的 HoloLens 库 （照片、 视频、 文档） 的轻松传送。<br><br><b>提示：</b><ul><li>如果看不到任何文件，请确保在登录到你 HoloLens 要启用对你的数据访问。</li><li>从<b>文件资源管理器</b>您可以选择在您的 PC<b>设备属性</b>若要查看 Windows Holographic OS 版本号 （固件版本） 和设备序列号。</li></ul><b>已知的问题：</b>重命名通过 HoloLens<b>文件资源管理器</b>未启用您的 PC 上。</td>
  </tr>
  <tr>
    <td>在安装过程中强制网络门户网络支持</td><td>现在可以设置在 HoloLens 上的来宾网络的酒店、 会议中心、 零售商店或使用强制网络门户的企业。</td><td>安装过程中，选择的网络，检查自动连接，是否需要，并按照系统提示您输入网络信息。</td>
  </tr>
  <tr>
    <td>通过 OneDrive 应用的照片和视频同步</td><td>你的照片和视频从 HoloLens 现在将通过而不是直接通过照片应用的 Microsoft Store 中的 OneDrive 应用程序同步。</td><td>若要设置此功能，请下载并启动从存储区的 OneDrive 应用。 在首次运行系统应该会提示以自动将您的照片上传到 OneDrive，或可以应用设置中找到该选项。</td>
  </tr>
</table>

### <a name="for-developers"></a>对于开发人员

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>空间映射的改进</td><td>质量、 简化和性能改进。</td><td>空间映射网格将显示更简洁 – 表示相同级别的详细信息所需较少的三角形。 场景中的三角形密度，可能会注意到更改。</td>
  </tr>
  <tr>
    <td>自动选择的基于深度缓冲区的焦点位置</td><td>提交到 Windows 的深度缓冲区使 HoloLens 选择焦点自动以优化全息图稳定性。</td><td>在 Unity 中，转到<b>编辑 > 项目设置 > Player > 通用 Windows 平台选项卡 > XR 设置</b>，展开<b>Windows 混合现实 SDK</b>项，并确保<b>启用深度缓冲区共享</b>检查。 这将为新项目自动选中。<br><br>对于 DirectX 应用程序，请确保您调用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>方法<b>HolographicRenderingParameters</b>每个帧来提供到 Windows 的深度缓冲区。
</td>
  </tr>
  <tr>
    <td>Holographic reprojection 模式</td><td>现在，您可以禁用位置 reprojection 上 HoloLens 以提高严格锁定正文的内容，例如 360 度视频全息图稳定性。</td><td>在 Unity 中，设置<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a>到<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a>时所有内容视图中都是严格正文锁定。<br><br>对于 DirectX 应用程序设置<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">HolographicCameraRenderingParameters.ReprojectionMode</a>到<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a>时所有内容视图中都是严格正文锁定。</td>
  </tr>
  <tr>
    <td>应用程序定制 Api</td><td>Windows Api，了解有关您的应用程序的运行位置，例如设备的显示是透明 (HoloLens) 或不透明 （沉浸式头戴式） 和是否 UWP 应用的二维视图显示在全息版的 shell。</td><td>以前必须手动公开 unity <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a>即使在此版本之前的工作的方式。<br><br>对于 DirectX 应用程序，您现在可以访问现有的 Api，如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault()。IsOpaque</a>并<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a>上也 HoloLens。
</td>
  </tr>
  <tr>
      <td>信息检索模式</td><td>允许开发人员构建学术和行业应用程序的计算机视觉和机器人，字段中测试新的想法时访问密钥 HoloLens 传感器包括：<ul><li>四个跟踪照相机的环境</li><li>两个版本的深度映射相机数据</li><li>IR 反射率流的两个版本</li></ul></td><td><a href="research-mode.md">研究模式文档</a><br><a href="https://github.com/Microsoft/HoloLensForCV">研究模式示例应用</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>对于商业客户

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>在单个设备上使用多个 Azure Active Directory 用户帐户</td><td>与多个 Azure AD 用户，每个都有其自己的用户设置和设备上的用户数据共享 HoloLens。</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro 中心：使用多个用户共享 HoloLens</a></td>
  </tr>
  <tr>
    <td>更改的 Wi-fi 网络上单一登录</td><td>更改的 Wi-fi 网络，然后登录以启用另一个用户首次使用其 Azure AD 用户帐户登录允许用户共享多个位置的设备和作业的站点。</td><td>在登录屏幕上，您可以使用的网络图标密码字段的下方以连接到网络。 这是首次登录到设备时，这非常有用。</td>
  </tr>
  <tr>
    <td>统一的注册</td><td>现在很容易设置使用个人 Microsoft 帐户添加工作帐户 (Azure AD)，并将设备加入到他们的 MDM 服务器设备的 HoloLens 用户。</td><td>使用 Azure AD 帐户，只需登录并注册自动发生。</td>
  </tr>
  <tr>
    <td>无需 MDM 注册进行邮件同步</td><td>支持 Exchange Active Sync (EAS) 进行邮件同步，而无需 MDM 注册。</td><td>现在可以同步电子邮件，而无需注册 mdm。 可以将设备与 Microsoft 帐户设置、 下载和安装邮件应用程序，并直接添加工作电子邮件帐户。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>适用于 IT 专业人员

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>新的"Windows Holographic for Business"OS 名称</td><td>清除版本命名以在 HoloLens 上启用商业套件功能时减少版本升级许可证应用程序上的混淆。</td><td>您可以看到在设备上是哪个版本的 Windows Holographic<b>设置 > 系统 > 关于</b>。 如果应用版本更新启用商业套件功能，将出现"Windows Holographic for Business"。 了解如何<a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">解锁 Windows Holographic for Business 功能</a>。</td>
  </tr>
  <tr>
  <td>Windows 配置设计器 (WCD)</td><td>创建和编辑通过更新 WCD 应用配置 HoloLens 的预配包。 版本更新、 可配置 OOBE、 区域/时区、 大容量 Azure AD 令牌、 网络和开发人员 CSP 的简单 HoloLens 向导。 筛选到 HoloLens 的高级的编辑器支持选项，包括分配的访问权限和帐户管理 Csp。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro 中心：配置 HoloLens 使用预配包</a></td>
  </tr>
  <tr>
    <td>可配置安装程序 (OOBE)</td><td>在安装过程中隐藏校准、 培训、 手势/视线移动和 Wi-fi 配置屏幕。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro 中心：配置 HoloLens 使用预配包</a></td>
  </tr>
  <tr>
    <td>大容量支持 Azure AD 令牌</td><td>预先注册到 Azure AD 目录租户的设备进行更快的用户设置流程。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro 中心：配置 HoloLens 使用预配包</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup 云解决方案提供商</td><td>部署配置文件以在开发人员模式下设置 HoloLens。 对于开发和演示设备很有用。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro 中心：配置 HoloLens 使用预配包</a></td>
  </tr>
  <tr>
  <td>AccountManagement 云解决方案提供商</td><td>共享 HoloLens 设备并删除用户数据后的注销或处于非活动状态/存储临时使用的阈值。 支持 Azure AD 帐户。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro 中心：配置 HoloLens 使用预配包</a></td>
  </tr>
  <tr>
  <td>已分配的访问</td><td>Windows 分配一线工作人员或演示的访问权限。 一个或多应用锁定。 开发人员无需解锁。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro 中心：在展台模式下设置了 HoloLens</a></td>
  </tr>
  <tr>
  <td>展台设备的来宾访问</td><td>Windows 分配演示使用无密码的来宾帐户的访问权限。 一个或多应用锁定。 开发人员无需解锁。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro 中心：在展台模式下设置了 HoloLens</a></td>
  </tr>
  <tr>
    <td>设置 (OOBE) 诊断</td><td>获取诊断日志从 HoloLens，因此可以排查 Azure AD 单一登录失败的问题 （之前的反馈中心是可供用户使用其登录失败）。</td><td>当安装程序或登录失败时，选择新<b>收集信息</b>选项来获取诊断日志进行故障排除。</td>
  </tr>
  <tr>
    <td>本地帐户，在无限期的密码过期</td><td>删除设备重置本地帐户的密码过期时的中断。</td><td>预配的本地帐户，当不再需要在每个 42 天更改密码<b>设置</b>，如帐户密码不再会过期。</td>
  </tr>
  <tr>
    <td>MDM 同步状态和详细信息</td><td>标准 Windows 功能，以了解 MDM 同步状态和从中 HoloLens 的详细信息。</td><td>您可以检查中的设备的 MDM 同步状态<b>设置 > 帐户 > 访问工作或学校 > 信息</b>。 在中<b>设备同步状态<b>部分中，可以启动同步，查看区域通过 MDM，和创建和导出的高级的诊断报告。</td>
  </tr>
</table>

## <a name="known-issues"></a>已知问题

我们努力工作以提供最佳 Windows Mixed Reality 体验，但我们仍跟踪一些已知的问题。 如果其他人发现，请[向我们提供反馈](give-us-feedback.md)。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新后

从 RS1 更新到 RS4 在 HoloLens 上后，可能会注意到以下问题：
* **Pin 重置**-3 x 3 个应用固定到开始菜单将更新后置为默认值。 
* **应用和放置的全息重置**-放置在您的世界中应用更新后将被删除，将需要重新放置在你的空间。 
* **反馈中心可能不会立即启动**-立即更新后，将需要几分钟后才能启动反馈中心，如某些收件箱应用时它们更新本身之前。 
* **公司的 Wi-fi 证书需要重新同步**-我们正在调查问题，需要 HoloLens，若要连接到公司的证书之前无法重新连接到要重新同步到设备的不同网络使用证书的公司网络。 
* **H.265 HEVC 视频播放不起作用**-尝试播放 H.265 视频应用程序将收到一条错误消息。 解决方法是对[访问 Windows Device Portal](using-the-windows-device-portal.md)，选择**应用**在左侧的导航栏中，并**删除**HEVC 应用程序。 然后，安装最新[HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)从 Microsoft Store。 我们正在调查此问题。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>面向开发人员： 更新 HoloLens 应用适用于设备运行 Windows 10 2018 年 4 月更新

以及出色的列表[的新功能](#new-features-for-hololens)，Windows 10 年 4 月的 HoloLens 2018 更新 (RS4) 会强制执行上一版本没有某些代码行为：
* **若要使用敏感资源 （照相机、 麦克风等） 的权限请求** -RS4 HoloLens 上的将强制执行应用程序想要访问敏感资源，例如照相机或麦克风的权限请求。 HoloLens 上的 RS1 未强制这些提示，因此，如果您的应用程序有即时访问这些资源，它可能会崩溃 RS4 中 （即使用户授予对所请求资源的权限）。 请阅读相关[UWP 应用功能声明文章](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations)有关详细信息。
* **对超出你自己的应用程序的调用**-在 HoloLens 上的 RS4 将强制执行的正确使用[ *Windows.System.Launcher*类](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)启动从你自己的另一个应用程序。 例如，我们已了解问题与应用程序调用*Windows.System.Launcher.LaunchUriForResultsAsync*从非 ASTA UI 线程。 这会在 RS1 上 HoloLens，成功但 RS4 需要在 UI 线程上执行的调用。

### <a name="windows-mixed-reality-on-desktop"></a>在桌面上的 Windows 混合的现实

#### <a name="visual-quality"></a>视觉质量

* 如果您注意到 Windows 10 2018 年 4 月更新图形是比之前更模糊或视图的字段查找在您的头戴式较小之后，自动性能设置可能已更改为了保持在较不强大足够帧速率图形卡 （如 Nvidia 1050)。 您可以手动重写此 （如果你选择） 通过导航到**设置 > 混合现实 > 耳机显示 > 体验选项 > 更改**并将"自动"更改为"90 Hz。" 此外可以尝试更改**视觉质量**（在相同的设置页上） 为"High"。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 安装程序

* 当使用耳机连接的设置 Windows，PC 监视器可能会变黑。 若要启用到 PC 监视器以完成 Windows 安装程序的输出将耳机中拔出。
* 如果还没有头戴式耳机连接，当你首次访问的主 Windows Mixed Reality 可能丢失的其他提示。
* 其他蓝牙设备可能会导致动画控制器的干扰。 如果 motion 控制器有连接/配对/跟踪问题，请确保蓝牙无线 （如果外部的硬件保护装置） 插入到无障碍的位置和不会立即旁边另一个蓝牙硬件保护装置。 也可以尝试关闭其他蓝牙外围设备，以查看是否最好的 Windows Mixed Reality 会话期间。

#### <a name="games-and-apps-from-the-microsoft-store"></a>游戏和应用程序从 Microsoft Store

* 某些图形密集型游戏，Forza Motorsport 7 等可能播放内部 Windows Mixed Reality 时性能较差的 Pc 上导致性能问题。

#### <a name="audio"></a>Audio

* 如果必须在使用 Windows Mixed Reality 耳机之前主机 PC 上启用 Cortana，可能会丢失应用到应用放置在主 Windows Mixed Reality 周围的空间声音模拟。 
   * 解决办法是在所有连接到您的 PC，即使您耳机连接的音频设备的音频设备上启用"Windows Sonic 的耳机":
      1. 左键单击桌面任务栏上的扬声器图标并从音频设备列表中选择。
      2. 右键单击桌面任务栏上的扬声器图标，然后在"扬声器设置"菜单中选择"Windows Sonic 的耳机"。
      3. 有关所有音频设备 （终结点） 重复这些步骤。
   * 另一个选项中关闭"你好，小娜让 Cortana 响应"**设置** > **Cortana**在启动 Windows Mixed Reality 之前在桌面上。
* 如果另一个多媒体的 USB 设备 （如网络摄像头） 与 Windows Mixed Reality 耳机共享相同的 USB 集线器 （外部或在您的 PC），在极少数情况下耳机的音频插孔/耳机可能包含蜂鸣声音或不包括音频根本。 您可以解决此问题由你耳机，不会共享相同的中心为其他设备，或断开/禁用其他 USB 多媒体设备的 USB 端口。
* 在极少数情况下，主机的电脑的 USB 集线器不能提供足够的电源至 Windows Mixed Reality 耳机并可能会注意到连接到头戴式耳机的干扰的突然增加。

#### <a name="holograms"></a>全息

* 如果已在你的主 Windows 混合现实中放置大量全息，一些可能会消失，重新显示当你考虑。 若要避免此问题，删除一些全息 Windows Mixed Reality 家庭的此区域。

#### <a name="motion-controllers"></a>运动控制器

* 如果输入不路由到耳机，motion 控制器将简要消失时持有旁边聊天室边界。 按 Win + Y 以确保跨桌面监视器没有一个蓝色横幅会解决此问题。 
* 有时，当单击 Microsoft Edge 中的网页上时，内容将缩放而不是单击。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>中的主 Windows Mixed Reality 桌面应用程序

* 截图工具不适用于桌面应用程序。
* 桌面应用程序不会保留上重新启动设置。
* 如果你使用混合现实门户预览在您的桌面上，在 Windows Mixed Reality 主页中打开桌面应用程序时，可能会注意到无限镜像效果。 
* 运行桌面应用程序可能导致性能问题上非-超高 Windows 混合现实电脑;不建议。  
* 桌面应用程序可能会自动启动因为在桌面上不可见的窗口具有焦点。 
* 桌面的用户帐户控制提示将显示黑色，直到完成提示的耳机。

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows 为 SteamVR 的混合的现实

* 可能需要启动混合现实门户更新后以确保必要的软件更新适用于 Windows 10 2018 年 4 月更新完成后才会启动 SteamVR。 
* 您必须是在最新版本的 Windows Mixed Reality SteamVR 保持与 Windows 兼容的 10 2018 年 4 月更新。 请确保自动更新启用的 Windows Mixed Reality SteamVR，位于你在流中的库的"软件"部分。  

#### <a name="other-issues"></a>其他问题

>[!IMPORTANT]
>早期版本的 Windows 10 2018 年 4 月更新推送到预览体验成员 （版本 17134.5） 缺少的组成部分软件必须运行 Windows Mixed Reality。 我们建议避免此版本，如果使用 Windows Mixed Reality。 

在此我们正在努力修复中即将推出更新修补程序的更新 (10.0.17134.1) 的初始版本上使用 Surface Book 2 时，我们已识别性能回归。 等待，直到此问题已修复在手动更新或正在等待更新通常推出之前，我们建议。

## <a name="provide-feedback-and-report-issues"></a>提供反馈和报告问题

请使用[HoloLens 或 Windows 10 电脑上的反馈中心应用](give-us-feedback.md)提供反馈和报告问题。 使用反馈中心可确保所有必要的诊断信息均包括在内，以帮助我们的工程师快速调试和解决问题。

>[!NOTE]
>请务必接受提示，询问你是否希望反馈中心，以访问您的 Documents 文件夹 (选择**是**出现提示时)。

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明-2017 年 10 月](release-notes-october-2017.md)
* [发行说明-2016 年 8 月](release-notes-august-2016.md)
* [发行说明-2016 年 5 月](release-notes-may-2016.md)
* [发行说明-2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>请参阅
* [沉浸式头戴式支持 （外部链接）](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支持 （外部链接）](https://support.microsoft.com/products/hololens)
* [安装工具](install-the-tools.md)
* [向我们提供反馈](give-us-feedback.md)

