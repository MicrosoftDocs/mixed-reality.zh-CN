---
title: 添加自定义主环境
description: 除了 Windows Mixed Reality 家庭环境中，我们提供，您可以尝试创建和使用你自己。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、 混合现实中，虚拟现实、 VR、 MR、 主页、 自定义环境、 地点、 cliff 房子、 skyloft、 用户，创建
ms.openlocfilehash: 8f5a3a1bdf5728260b0b7717c74a50f3356ca04a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829637"
---
# <a name="add-custom-home-environments"></a>添加自定义主环境

>[!NOTE]
>这是实验性功能。 请试一试和乐趣，但不会感到惊讶，如果一切按预期方式不太有效。 我们将评估此功能和使用它，因此感兴趣的可行性请告诉我们有关你的体验 （和任何已发现的 bug） 中[开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)。

从开始[Windows 10 2018 年 4 月更新](#release-notes-april-2018.md)，我们启用了实验性功能，您可以将自定义环境添加到该位置选取器 （在开始菜单中） 要用作[Windows Mixed Reality 家庭](#navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality 具有两个默认环境，Cliff 房屋和 Skyloft，可以选择为你的主页。 创建自定义环境，可展开该列表与您自己的作品。 我们会提供此早期状态评估从创建者和开发人员感兴趣，请参阅什么样的世界上创建，并了解如何使用不同的创作工具。

在使用自定义环境，您会注意到该 teleporting 时, 与应用程序，交互并将放入全息适用就像 Cliff 房屋和 Skyloft 中。 您可以浏览幻想布局中的 web 或具有前瞻性的市/县填充全息-一切皆有可能 ！

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>自定义主环境</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>尝试示例环境

我们创建了一个示例环境，它展示了一些自定义主环境创意目标。 请按照下列步骤以尝试操作：
1. [下载我们的示例幻想岛环境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)（链接到自解压缩可执行文件所指向）。

    ![幻想岛示例环境](images/FantasyLand.jpg)<br>
    *幻想岛示例环境*<br>

2. 运行**Fantasy_Island.exe**刚下载的文件。

    > [!NOTE]
    > 尝试运行.exe 文件从 （与此类似） web 下载，可能会遇到"Windows 保护您的电脑"弹出窗口。 若要运行此弹出窗口 Fantasy_Island.exe，选择**的详细信息**，然后**仍要运行**。 此安全设置是为了防止因你下载的文件，你可能不想要信任，因此请在你信任的文件的源时才选择此选项。

3. 打开**文件资源管理器**并导航到环境文件夹中，通过在地址栏中粘贴以下： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`。
4. 将下载的示例环境复制到此文件夹。
5. 重新启动**混合现实门户**。 这将刷新位置选取器中的环境的列表。
6. 将在您的头戴式上。 在您在主页中，打开**开始菜单**使用 Windows 按钮你的控制器。
7. 选择**位数**固定应用程序以选择主环境列表上方的图标。
8. 您会发现你在位置列表中下载的幻想岛环境。 选择**幻想岛**输入新的自定义主环境 ！

## <a name="creating-your-own-custom-environment"></a>创建自定义环境

除了使用我们的示例环境，您可以导出自定义环境使用你最喜欢的 3D 编辑软件。 

### <a name="modeling-guidelines"></a>建模指南

在建模时您的环境，请记住以下建议。 这将有助于确保 believably 调整大小的世界中的正确方向中用户会生成：

1. 围绕原点你所需的生成的位置，用户将生成 0,0,0 这样的中心。
2. 应改为标准设置工作单位，以便可以在世界上规模较大创作资产。
3. 最多轴应设置为"Y"。
4. 资产应"forward"正 Z 轴向人脸。
5. 不需要的所有网格结合使用，但建议如果您面向的资源受限的设备。

### <a name="exporting-your-environment"></a>导出你的环境

Windows Mixed Reality 依赖于二进制 glTF (.glb) 环境的资产传递格式。 glTF 是特许 3D 资产传递由 Khronos 组维护的免费开放标准。 随着 glTF 发展的行业标准的可互操作三维内容，因此将对格式的 Microsoft 的支持在 Windows 应用和体验。

导出的资产，以用作自定义主环境的第一步生成 glTF 2.0 模型。 GlTF 工作组将保留[列表中的受支持的导出程序和转换器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)创建 glTF 2.0 模型。 若要开始，使用此页上列出的程序之一来创建和导出 glTF 2.0 模型，或转换使用其中一个受支持的转换器的现有模型。

此外，请查看[本文有帮助](https://www.khronos.org/blog/art-pipeline-for-gltf)画面流概述提供用于导出 glTF 模型从 Blender 和 3DS Max 直接。 

### <a name="environment-limits"></a>环境限制

所有环境必须都是 < 256 mb。 大于 256 mb 的环境将无法加载和故障回复到空世界与只是默认 skybox 围绕用户。 请记住此文件大小限制时创建您的模型。 此外，如果您计划用于优化环境使用 WindowsMRAssetConverter，如下所述，为 cognizant 纹理大小将增加，因为优化器将创建具有更大的文件大小，但加载速度更快的纹理。 

### <a name="optimizing-your-environment"></a>优化您的环境

Windows Mixed Reality 支持多种将显著减少您的环境的加载时间的可选优化。 这可能是适合环境的很多纹理而言尤其重要，因为它们有时会在加载时超时。 一般情况下，我们建议将此步骤中的所有资产，但是，使用几个或较低分辨率纹理较小的环境不会始终需要。 

为了简化此过程，我们创建了[Windows 混合现实资产转换器 （GitHub 上提供）](https://github.com/Microsoft/glTF-Toolkit/releases)执行你优化。 此工具使用一组 Microsoft glTF 工具包中提供的实用程序来优化任何标准 2.0 glTF 或.glb 通过执行其他纹理打包、 压缩和分辨率向下缩放。 

转换器目前支持数进行调整优化的具体行为的标志。 我们建议运行与以下标志为获得最佳结果：

Flag|建议的值|描述
---|---|---
-max-texture-size|1024 或 2048| 对此改进纹理的质量进行调整，默认值为 512 x 512。 请注意更大的值将会显著影响环境的文件大小因此请记住，256 mb 的限制
-min-version|1803|自定义环境仅支持版本的 windows 上 > = 1803年。 此标志将删除较旧版本的纹理，并减小文件大小的最终的资产

例如：

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>测试您的环境

最终.glb 环境后就可以对它进行测试耳机。 在步骤 2 开始["尝试的示例环境"](#trying-a-sample-environment)部分作为主混合现实中使用自定义环境。 

## <a name="feedback"></a>反馈

虽然我们将评估此实验性功能，我们感兴趣学习如何使用自定义环境，可能会遇到任何 bug，您喜欢此功能。 请在共享用于创建和使用自定义主环境中的所有反馈[开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)。

## <a name="troubleshooting-and-tips"></a>故障排除和提示

### <a name="how-do-i-change-the-name-of-the-environment"></a>如何更改环境的名称？

将位置选取器中使用环境文件夹中的文件名称。 若要更改您的环境名称只是重命名环境文件名称，重启混合现实门户。

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>如何从我的位置选取器中删除自定义环境？

若要删除自定义环境，请打开您的 PC 上的环境文件夹 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 和删除环境。 后重新启动混合现实门户时，此环境将不会再出现的位置选取器中。 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>如何默认我最喜欢的自定义环境？

目前不能更改默认环境。 每次重新启动混合现实门户中，您将返回到 Cliff 房屋环境。 

### <a name="i-spawn-into-a-blank-space"></a>我生成到的空白区域

Windows Mixed Reality[不支持超过 256 mb 的环境](#environment-limits)。 当环境超出此限制时，用户将位于空天空包装盒没有模型。

### <a name="it-takes-a-long-time-to-load-my-environment"></a>花费很长时间才能加载我的环境

可以将可选的优化添加到您的环境以使其更快加载。 请参阅["优化您的环境"](#optimizing-your-environment)有关详细信息。

### <a name="the-scale-of-my-environment-is-incorrect"></a>我的环境中的小数位数不正确

加载环境时，Windows Mixed Reality 将转换为 1 米 glTF 单位。 如果你的环境加载时出现意外的规模，仔细检查您导出程序，以确保要建模 1 米的规模。 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>我的环境中的生成位置不正确

默认生成位置位于 0,0,0 在环境中。 其不目前可以自定义此位置中，因此您必须通过将你的环境导出与原点定位在所需的衍生点处修改的衍生点。

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>音频听起来不正确的环境中

当创建自定义环境时，它将使用与已创建的物理空间不匹配噪声呈现模拟。 声音可能来自错误的方向和听起来可能 muffled。 

## <a name="see-also"></a>请参阅
* [导航 Windows 混合现实主页](#navigating-the-windows-mixed-reality-home.md)
* [混合现实资产转换器 （GitHub 上） 的 Windows](https://github.com/Microsoft/glTF-Toolkit/releases)

