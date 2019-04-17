---
title: 添加自定义主环境
description: 除了 Windows Mixed Reality 家庭环境中，我们提供，您可以尝试创建和使用你自己。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、 混合现实中，虚拟现实、 VR、 MR、 主页、 自定义环境、 地点、 cliff 房子、 skyloft、 用户，创建
ms.openlocfilehash: ef140efd88aa0d3329ae2aa7e5b202c3bfe77c0a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590098"
---
# <a name="add-custom-home-environments"></a><span data-ttu-id="a444e-104">添加自定义主环境</span><span class="sxs-lookup"><span data-stu-id="a444e-104">Add custom home environments</span></span>

>[!NOTE]
><span data-ttu-id="a444e-105">这是实验性功能。</span><span class="sxs-lookup"><span data-stu-id="a444e-105">This is an experimental feature.</span></span> <span data-ttu-id="a444e-106">请试一试和乐趣，但不会感到惊讶，如果一切按预期方式不太有效。</span><span class="sxs-lookup"><span data-stu-id="a444e-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="a444e-107">我们将评估此功能和使用它，因此感兴趣的可行性请告诉我们有关你的体验 （和任何已发现的 bug） 中[开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)。</span><span class="sxs-lookup"><span data-stu-id="a444e-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="a444e-108">从开始[Windows 10 2018 年 4 月更新](#release-notes-april-2018.md)，我们启用了实验性功能，您可以将自定义环境添加到该位置选取器 （在开始菜单中） 要用作[Windows Mixed Reality 家庭](#navigating-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="a444e-108">Starting with the [Windows 10 April 2018 update](#release-notes-april-2018.md), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="a444e-109">Windows Mixed Reality 具有两个默认环境，Cliff 房屋和 Skyloft，可以选择为你的主页。</span><span class="sxs-lookup"><span data-stu-id="a444e-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="a444e-110">创建自定义环境，可展开该列表与您自己的作品。</span><span class="sxs-lookup"><span data-stu-id="a444e-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="a444e-111">我们会提供此早期状态评估从创建者和开发人员感兴趣，请参阅什么样的世界上创建，并了解如何使用不同的创作工具。</span><span class="sxs-lookup"><span data-stu-id="a444e-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="a444e-112">在使用自定义环境，您会注意到该 teleporting 时, 与应用程序，交互并将放入全息适用就像 Cliff 房屋和 Skyloft 中。</span><span class="sxs-lookup"><span data-stu-id="a444e-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="a444e-113">您可以浏览幻想布局中的 web 或具有前瞻性的市/县填充全息-一切皆有可能 ！</span><span class="sxs-lookup"><span data-stu-id="a444e-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="a444e-114">设备支持</span><span class="sxs-lookup"><span data-stu-id="a444e-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a444e-115">功能</span><span class="sxs-lookup"><span data-stu-id="a444e-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="a444e-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a444e-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a444e-117"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="a444e-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a444e-118">自定义主环境</span><span class="sxs-lookup"><span data-stu-id="a444e-118">Custom home environments</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="a444e-119">✔️</span><span class="sxs-lookup"><span data-stu-id="a444e-119">✔️</span></span></td>
</tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="a444e-120">尝试示例环境</span><span class="sxs-lookup"><span data-stu-id="a444e-120">Trying a sample environment</span></span>

<span data-ttu-id="a444e-121">我们创建了一个示例环境，它展示了一些自定义主环境创意目标。</span><span class="sxs-lookup"><span data-stu-id="a444e-121">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="a444e-122">请按照下列步骤以尝试操作：</span><span class="sxs-lookup"><span data-stu-id="a444e-122">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="a444e-123">[下载我们的示例幻想岛环境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)（链接到自解压缩可执行文件所指向）。</span><span class="sxs-lookup"><span data-stu-id="a444e-123">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="a444e-124">![幻想岛示例环境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="a444e-124">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="a444e-125">*幻想岛示例环境*</span><span class="sxs-lookup"><span data-stu-id="a444e-125">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="a444e-126">运行**Fantasy_Island.exe**刚下载的文件。</span><span class="sxs-lookup"><span data-stu-id="a444e-126">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a444e-127">尝试运行.exe 文件从 （与此类似） web 下载，可能会遇到"Windows 保护您的电脑"弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="a444e-127">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="a444e-128">若要运行此弹出窗口 Fantasy_Island.exe，选择**的详细信息**，然后**仍要运行**。</span><span class="sxs-lookup"><span data-stu-id="a444e-128">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="a444e-129">此安全设置是为了防止因你下载的文件，你可能不想要信任，因此请在你信任的文件的源时才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="a444e-129">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="a444e-130">打开**文件资源管理器**并导航到环境文件夹中，通过在地址栏中粘贴以下： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`。</span><span class="sxs-lookup"><span data-stu-id="a444e-130">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="a444e-131">将下载的示例环境复制到此文件夹。</span><span class="sxs-lookup"><span data-stu-id="a444e-131">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="a444e-132">重新启动**混合现实门户**。</span><span class="sxs-lookup"><span data-stu-id="a444e-132">Restart **Mixed Reality Portal**.</span></span> <span data-ttu-id="a444e-133">这将刷新位置选取器中的环境的列表。</span><span class="sxs-lookup"><span data-stu-id="a444e-133">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="a444e-134">将在您的头戴式上。</span><span class="sxs-lookup"><span data-stu-id="a444e-134">Put on your headset.</span></span> <span data-ttu-id="a444e-135">在您在主页中，打开**开始菜单**使用 Windows 按钮你的控制器。</span><span class="sxs-lookup"><span data-stu-id="a444e-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="a444e-136">选择**位数**固定应用程序以选择主环境列表上方的图标。</span><span class="sxs-lookup"><span data-stu-id="a444e-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="a444e-137">您会发现你在位置列表中下载的幻想岛环境。</span><span class="sxs-lookup"><span data-stu-id="a444e-137">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="a444e-138">选择**幻想岛**输入新的自定义主环境 ！</span><span class="sxs-lookup"><span data-stu-id="a444e-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="a444e-139">创建自定义环境</span><span class="sxs-lookup"><span data-stu-id="a444e-139">Creating your own custom environment</span></span>

<span data-ttu-id="a444e-140">除了使用我们的示例环境，您可以导出自定义环境使用你最喜欢的 3D 编辑软件。</span><span class="sxs-lookup"><span data-stu-id="a444e-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="a444e-141">建模指南</span><span class="sxs-lookup"><span data-stu-id="a444e-141">Modeling guidelines</span></span>

<span data-ttu-id="a444e-142">在建模时您的环境，请记住以下建议。</span><span class="sxs-lookup"><span data-stu-id="a444e-142">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="a444e-143">这将有助于确保 believably 调整大小的世界中的正确方向中用户会生成：</span><span class="sxs-lookup"><span data-stu-id="a444e-143">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="a444e-144">围绕原点你所需的生成的位置，用户将生成 0,0,0 这样的中心。</span><span class="sxs-lookup"><span data-stu-id="a444e-144">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="a444e-145">应改为标准设置工作单位，以便可以在世界上规模较大创作资产。</span><span class="sxs-lookup"><span data-stu-id="a444e-145">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="a444e-146">最多轴应设置为"Y"。</span><span class="sxs-lookup"><span data-stu-id="a444e-146">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="a444e-147">资产应"forward"正 Z 轴向人脸。</span><span class="sxs-lookup"><span data-stu-id="a444e-147">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="a444e-148">不需要的所有网格结合使用，但建议如果您面向的资源受限的设备。</span><span class="sxs-lookup"><span data-stu-id="a444e-148">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="a444e-149">导出你的环境</span><span class="sxs-lookup"><span data-stu-id="a444e-149">Exporting your environment</span></span>

<span data-ttu-id="a444e-150">Windows Mixed Reality 依赖于二进制 glTF (.glb) 环境的资产传递格式。</span><span class="sxs-lookup"><span data-stu-id="a444e-150">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="a444e-151">glTF 是特许 3D 资产传递由 Khronos 组维护的免费开放标准。</span><span class="sxs-lookup"><span data-stu-id="a444e-151">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="a444e-152">随着 glTF 发展的行业标准的可互操作三维内容，因此将对格式的 Microsoft 的支持在 Windows 应用和体验。</span><span class="sxs-lookup"><span data-stu-id="a444e-152">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="a444e-153">导出的资产，以用作自定义主环境的第一步生成 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="a444e-153">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="a444e-154">GlTF 工作组将保留[列表中的受支持的导出程序和转换器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)创建 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="a444e-154">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="a444e-155">若要开始，使用此页上列出的程序之一来创建和导出 glTF 2.0 模型，或转换使用其中一个受支持的转换器的现有模型。</span><span class="sxs-lookup"><span data-stu-id="a444e-155">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="a444e-156">此外，请查看[本文有帮助](https://www.khronos.org/blog/art-pipeline-for-gltf)画面流概述提供用于导出 glTF 模型从 Blender 和 3DS Max 直接。</span><span class="sxs-lookup"><span data-stu-id="a444e-156">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="a444e-157">环境限制</span><span class="sxs-lookup"><span data-stu-id="a444e-157">Environment limits</span></span>

<span data-ttu-id="a444e-158">所有环境必须都是 < 256 mb。</span><span class="sxs-lookup"><span data-stu-id="a444e-158">All environments must be < 256 mbs.</span></span> <span data-ttu-id="a444e-159">大于 256 mb 的环境将无法加载和故障回复到空世界与只是默认 skybox 围绕用户。</span><span class="sxs-lookup"><span data-stu-id="a444e-159">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="a444e-160">请记住此文件大小限制时创建您的模型。</span><span class="sxs-lookup"><span data-stu-id="a444e-160">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="a444e-161">此外，如果您计划用于优化环境使用 WindowsMRAssetConverter，如下所述，为 cognizant 纹理大小将增加，因为优化器将创建具有更大的文件大小，但加载速度更快的纹理。</span><span class="sxs-lookup"><span data-stu-id="a444e-161">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="a444e-162">优化您的环境</span><span class="sxs-lookup"><span data-stu-id="a444e-162">Optimizing your environment</span></span>

<span data-ttu-id="a444e-163">Windows Mixed Reality 支持多种将显著减少您的环境的加载时间的可选优化。</span><span class="sxs-lookup"><span data-stu-id="a444e-163">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="a444e-164">这可能是适合环境的很多纹理而言尤其重要，因为它们有时会在加载时超时。</span><span class="sxs-lookup"><span data-stu-id="a444e-164">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="a444e-165">一般情况下，我们建议将此步骤中的所有资产，但是，使用几个或较低分辨率纹理较小的环境不会始终需要。</span><span class="sxs-lookup"><span data-stu-id="a444e-165">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="a444e-166">为了简化此过程，我们创建了[Windows 混合现实资产转换器 （GitHub 上提供）](https://github.com/Microsoft/glTF-Toolkit/releases)执行你优化。</span><span class="sxs-lookup"><span data-stu-id="a444e-166">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="a444e-167">此工具使用一组 Microsoft glTF 工具包中提供的实用程序来优化任何标准 2.0 glTF 或.glb 通过执行其他纹理打包、 压缩和分辨率向下缩放。</span><span class="sxs-lookup"><span data-stu-id="a444e-167">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="a444e-168">转换器目前支持数进行调整优化的具体行为的标志。</span><span class="sxs-lookup"><span data-stu-id="a444e-168">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="a444e-169">我们建议运行与以下标志为获得最佳结果：</span><span class="sxs-lookup"><span data-stu-id="a444e-169">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="a444e-170">Flag</span><span class="sxs-lookup"><span data-stu-id="a444e-170">Flag</span></span>|<span data-ttu-id="a444e-171">建议的值</span><span class="sxs-lookup"><span data-stu-id="a444e-171">Recommended Value(s)</span></span>|<span data-ttu-id="a444e-172">描述</span><span class="sxs-lookup"><span data-stu-id="a444e-172">Description</span></span>
---|---|---
<span data-ttu-id="a444e-173">-max-texture-size</span><span class="sxs-lookup"><span data-stu-id="a444e-173">-max-texture-size</span></span>|<span data-ttu-id="a444e-174">1024 或 2048</span><span class="sxs-lookup"><span data-stu-id="a444e-174">1024 or 2048</span></span>| <span data-ttu-id="a444e-175">对此改进纹理的质量进行调整，默认值为 512 x 512。</span><span class="sxs-lookup"><span data-stu-id="a444e-175">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="a444e-176">请注意更大的值将会显著影响环境的文件大小因此请记住，256 mb 的限制</span><span class="sxs-lookup"><span data-stu-id="a444e-176">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="a444e-177">-min-version</span><span class="sxs-lookup"><span data-stu-id="a444e-177">-min-version</span></span>|<span data-ttu-id="a444e-178">1803</span><span class="sxs-lookup"><span data-stu-id="a444e-178">1803</span></span>|<span data-ttu-id="a444e-179">自定义环境仅支持版本的 windows 上 > = 1803年。</span><span class="sxs-lookup"><span data-stu-id="a444e-179">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="a444e-180">此标志将删除较旧版本的纹理，并减小文件大小的最终的资产</span><span class="sxs-lookup"><span data-stu-id="a444e-180">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="a444e-181">例如：</span><span class="sxs-lookup"><span data-stu-id="a444e-181">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="a444e-182">测试您的环境</span><span class="sxs-lookup"><span data-stu-id="a444e-182">Testing your environment</span></span>

<span data-ttu-id="a444e-183">最终.glb 环境后就可以对它进行测试耳机。</span><span class="sxs-lookup"><span data-stu-id="a444e-183">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="a444e-184">在步骤 2 开始["尝试的示例环境"](#trying-a-sample-environment)部分作为主混合现实中使用自定义环境。</span><span class="sxs-lookup"><span data-stu-id="a444e-184">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="a444e-185">反馈</span><span class="sxs-lookup"><span data-stu-id="a444e-185">Feedback</span></span>

<span data-ttu-id="a444e-186">虽然我们将评估此实验性功能，我们感兴趣学习如何使用自定义环境，可能会遇到任何 bug，您喜欢此功能。</span><span class="sxs-lookup"><span data-stu-id="a444e-186">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="a444e-187">请在共享用于创建和使用自定义主环境中的所有反馈[开发人员论坛](https://forums.hololens.com/categories/custom-home-environments)。</span><span class="sxs-lookup"><span data-stu-id="a444e-187">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="a444e-188">故障排除和提示</span><span class="sxs-lookup"><span data-stu-id="a444e-188">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="a444e-189">如何更改环境的名称？</span><span class="sxs-lookup"><span data-stu-id="a444e-189">How do I change the name of the environment?</span></span>

<span data-ttu-id="a444e-190">将位置选取器中使用环境文件夹中的文件名称。</span><span class="sxs-lookup"><span data-stu-id="a444e-190">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="a444e-191">若要更改您的环境名称只是重命名环境文件名称，重启混合现实门户。</span><span class="sxs-lookup"><span data-stu-id="a444e-191">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="a444e-192">如何从我的位置选取器中删除自定义环境？</span><span class="sxs-lookup"><span data-stu-id="a444e-192">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="a444e-193">若要删除自定义环境，请打开您的 PC 上的环境文件夹 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 和删除环境。</span><span class="sxs-lookup"><span data-stu-id="a444e-193">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="a444e-194">后重新启动混合现实门户时，此环境将不会再出现的位置选取器中。</span><span class="sxs-lookup"><span data-stu-id="a444e-194">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="a444e-195">如何默认我最喜欢的自定义环境？</span><span class="sxs-lookup"><span data-stu-id="a444e-195">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="a444e-196">目前不能更改默认环境。</span><span class="sxs-lookup"><span data-stu-id="a444e-196">You can't currently change the default environment.</span></span> <span data-ttu-id="a444e-197">每次重新启动混合现实门户中，您将返回到 Cliff 房屋环境。</span><span class="sxs-lookup"><span data-stu-id="a444e-197">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="a444e-198">我生成到的空白区域</span><span class="sxs-lookup"><span data-stu-id="a444e-198">I spawn into a blank space</span></span>

<span data-ttu-id="a444e-199">Windows Mixed Reality[不支持超过 256 mb 的环境](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="a444e-199">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="a444e-200">当环境超出此限制时，用户将位于空天空包装盒没有模型。</span><span class="sxs-lookup"><span data-stu-id="a444e-200">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="a444e-201">花费很长时间才能加载我的环境</span><span class="sxs-lookup"><span data-stu-id="a444e-201">It takes a long time to load my environment</span></span>

<span data-ttu-id="a444e-202">可以将可选的优化添加到您的环境以使其更快加载。</span><span class="sxs-lookup"><span data-stu-id="a444e-202">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="a444e-203">请参阅["优化您的环境"](#optimizing-your-environment)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="a444e-203">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="a444e-204">我的环境中的小数位数不正确</span><span class="sxs-lookup"><span data-stu-id="a444e-204">The scale of my environment is incorrect</span></span>

<span data-ttu-id="a444e-205">加载环境时，Windows Mixed Reality 将转换为 1 米 glTF 单位。</span><span class="sxs-lookup"><span data-stu-id="a444e-205">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="a444e-206">如果你的环境加载时出现意外的规模，仔细检查您导出程序，以确保要建模 1 米的规模。</span><span class="sxs-lookup"><span data-stu-id="a444e-206">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="a444e-207">我的环境中的生成位置不正确</span><span class="sxs-lookup"><span data-stu-id="a444e-207">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="a444e-208">默认生成位置位于 0,0,0 在环境中。</span><span class="sxs-lookup"><span data-stu-id="a444e-208">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="a444e-209">其不目前可以自定义此位置中，因此您必须通过将你的环境导出与原点定位在所需的衍生点处修改的衍生点。</span><span class="sxs-lookup"><span data-stu-id="a444e-209">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="a444e-210">音频听起来不正确的环境中</span><span class="sxs-lookup"><span data-stu-id="a444e-210">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="a444e-211">当创建自定义环境时，它将使用与已创建的物理空间不匹配噪声呈现模拟。</span><span class="sxs-lookup"><span data-stu-id="a444e-211">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="a444e-212">声音可能来自错误的方向和听起来可能 muffled。</span><span class="sxs-lookup"><span data-stu-id="a444e-212">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="a444e-213">请参阅</span><span class="sxs-lookup"><span data-stu-id="a444e-213">See also</span></span>
* [<span data-ttu-id="a444e-214">导航 Windows 混合现实主页</span><span class="sxs-lookup"><span data-stu-id="a444e-214">Navigating the Windows Mixed Reality Home</span></span>](#navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="a444e-215">混合现实资产转换器 （GitHub 上） 的 Windows</span><span class="sxs-lookup"><span data-stu-id="a444e-215">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

