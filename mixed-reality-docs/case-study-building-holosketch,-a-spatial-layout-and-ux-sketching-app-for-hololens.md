---
title: 案例研究-为 HoloLens 构建 HoloSketch、空间布局和 UX 草绘应用
description: HoloSketch 是一种设备上的空间布局和适用于 HoloLens 的 UX 草图工具, 用于帮助构建全息体验。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, 草绘, 应用
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524547"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="4b549-104">案例研究-为 HoloLens 构建 HoloSketch、空间布局和 UX 草绘应用</span><span class="sxs-lookup"><span data-stu-id="4b549-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="4b549-105">HoloSketch 是一种设备上的空间布局和适用于 HoloLens 的 UX 草图工具, 用于帮助构建全息体验。</span><span class="sxs-lookup"><span data-stu-id="4b549-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="4b549-106">HoloSketch 适用于配对的蓝牙键盘和鼠标以及笔势和语音命令。</span><span class="sxs-lookup"><span data-stu-id="4b549-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="4b549-107">HoloSketch 的目的是提供一个简单的 UX 布局工具, 用于快速可视化和迭代。</span><span class="sxs-lookup"><span data-stu-id="4b549-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="4b549-108">![HoloSketch:用于 HoloLens 的空间布局和 UX 草绘应用。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="4b549-109">*HoloSketch: 用于 HoloLens 的空间布局和 UX 草绘应用*</span><span class="sxs-lookup"><span data-stu-id="4b549-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="4b549-110">![用于快速可视化和迭代的简单 UX 布局工具。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="4b549-111">*简单的 UX 布局工具, 用于快速可视化和迭代*</span><span class="sxs-lookup"><span data-stu-id="4b549-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="4b549-112">功能</span><span class="sxs-lookup"><span data-stu-id="4b549-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="4b549-113">用于快速研究和规模原型构建的基元</span><span class="sxs-lookup"><span data-stu-id="4b549-113">Primitives for quick studies and scale-prototyping</span></span>

![使用基元形状](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="4b549-115">将基元形状用于快速 massing 研究和规模原型设计。</span><span class="sxs-lookup"><span data-stu-id="4b549-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="4b549-116">通过 OneDrive 导入对象</span><span class="sxs-lookup"><span data-stu-id="4b549-116">Import objects through OneDrive</span></span>

![导入对象](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="4b549-118">通过 OneDrive 将 PNG/JPG 图像或 3D FBX 对象 (需要在 Unity 中打包) 导入到混合现实空间。</span><span class="sxs-lookup"><span data-stu-id="4b549-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="4b549-119">操作对象</span><span class="sxs-lookup"><span data-stu-id="4b549-119">Manipulate objects</span></span>

![操作对象](images/manipulate-objects-640px.jpg)

<span data-ttu-id="4b549-121">使用熟悉的3D 对象接口操作对象 (移动/旋转/缩放)。</span><span class="sxs-lookup"><span data-stu-id="4b549-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="4b549-122">蓝牙、鼠标/键盘、笔势和语音命令</span><span class="sxs-lookup"><span data-stu-id="4b549-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![支持蓝牙](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="4b549-124">HoloSketch 支持蓝牙鼠标/键盘、笔势和语音命令。</span><span class="sxs-lookup"><span data-stu-id="4b549-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="4b549-125">后台</span><span class="sxs-lookup"><span data-stu-id="4b549-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="4b549-126">在设备中体验设计的重要性</span><span class="sxs-lookup"><span data-stu-id="4b549-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="4b549-127">为 HoloLens 设计内容时, 在设备中体验设计很重要。</span><span class="sxs-lookup"><span data-stu-id="4b549-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="4b549-128">混合现实应用程序设计面临的最大挑战之一是很难理解规模、位置和深度, 尤其是通过传统的2D 草图。</span><span class="sxs-lookup"><span data-stu-id="4b549-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="4b549-129">基于2D 的通信的成本</span><span class="sxs-lookup"><span data-stu-id="4b549-129">Cost of 2D based communication</span></span>

<span data-ttu-id="4b549-130">为了有效地向他人传达 UX 流和方案, 设计人员可能会花费大量时间, 使用传统的2D 工具 (例如 Illustrator、Photoshop 和 PowerPoint) 来创建资产。</span><span class="sxs-lookup"><span data-stu-id="4b549-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="4b549-131">这些2D 设计通常需要额外的精力才能将其转换为三维。</span><span class="sxs-lookup"><span data-stu-id="4b549-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="4b549-132">从2D 到3D 的转换中, 一些想法会丢失。</span><span class="sxs-lookup"><span data-stu-id="4b549-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="4b549-133">复杂的部署过程</span><span class="sxs-lookup"><span data-stu-id="4b549-133">Complex deployment process</span></span>

<span data-ttu-id="4b549-134">由于混合现实是我们的新画布, 因此它的本质涉及到许多设计迭代和试用和错误。</span><span class="sxs-lookup"><span data-stu-id="4b549-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="4b549-135">对于不熟悉 Unity 和 Visual Studio 等工具的设计人员, 在 HoloLens 中将某些内容组合在一起并不容易。</span><span class="sxs-lookup"><span data-stu-id="4b549-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="4b549-136">通常, 您必须完成以下过程才能在设备中查看您的 2D/3D 插图。</span><span class="sxs-lookup"><span data-stu-id="4b549-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="4b549-137">这是一种非常大的障碍, 设计人员能够快速循环访问创意和方案。</span><span class="sxs-lookup"><span data-stu-id="4b549-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="4b549-138">![复杂的部署过程](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="4b549-139">*部署过程*</span><span class="sxs-lookup"><span data-stu-id="4b549-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="4b549-140">简化了 HoloSketch 的过程</span><span class="sxs-lookup"><span data-stu-id="4b549-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="4b549-141">通过 HoloSketch, 我们想要简化此过程, 而不涉及开发工具和设备门户配对。</span><span class="sxs-lookup"><span data-stu-id="4b549-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="4b549-142">使用 OneDrive, 用户可以轻松地将 2D/3D 资产置于 HoloLens 中。</span><span class="sxs-lookup"><span data-stu-id="4b549-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="4b549-143">![简化了 HoloSketch 的过程](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="4b549-144">*简化了 HoloSketch 的过程*</span><span class="sxs-lookup"><span data-stu-id="4b549-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="4b549-145">鼓励三维设计思想和解决方案</span><span class="sxs-lookup"><span data-stu-id="4b549-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="4b549-146">我们认为, 此工具可让设计人员在真正的三维空间中探索解决方案, 而不是在2D 中。</span><span class="sxs-lookup"><span data-stu-id="4b549-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="4b549-147">他们无需考虑为 UI 创建三维背景, 因为在这种情况下, 在 Hololens 情况下, 背景是真实世界。</span><span class="sxs-lookup"><span data-stu-id="4b549-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="4b549-148">HoloSketch 打开了一种方法, 使设计人员能够轻松地在 Hololens 上浏览3D 设计。</span><span class="sxs-lookup"><span data-stu-id="4b549-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="4b549-149">入门</span><span class="sxs-lookup"><span data-stu-id="4b549-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="4b549-150">如何将二维图像 (JPG/PNG) 导入 HoloSketch</span><span class="sxs-lookup"><span data-stu-id="4b549-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="4b549-151">将 JPG/PNG 图像上传到 OneDrive 文件夹的文档/HoloSketch。</span><span class="sxs-lookup"><span data-stu-id="4b549-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="4b549-152">在 HoloSketch 的 OneDrive 菜单中, 可以选择映像并将其放置在环境中。</span><span class="sxs-lookup"><span data-stu-id="4b549-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="4b549-153">![导入2D 图像](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4b549-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="4b549-154">*通过 OneDrive 导入图像和3D 对象*</span><span class="sxs-lookup"><span data-stu-id="4b549-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="4b549-155">如何将3D 对象导入 HoloSketch</span><span class="sxs-lookup"><span data-stu-id="4b549-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="4b549-156">在上传到 OneDrive 文件夹之前, 请按照下面的步骤将3D 对象打包到 Unity 资产包。</span><span class="sxs-lookup"><span data-stu-id="4b549-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="4b549-157">使用此过程可以从3D 软件 (如 Maya、电影院4D 和 Microsoft 画图 3D) 导入 FBX/OBJ 文件。</span><span class="sxs-lookup"><span data-stu-id="4b549-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4b549-158">目前, Unity 版本第5.4.5 节 f1 支持创建资产包。</span><span class="sxs-lookup"><span data-stu-id="4b549-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="4b549-159">下载并打开 Unity 项目["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。</span><span class="sxs-lookup"><span data-stu-id="4b549-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="4b549-160">此 Unity 项目包含捆绑资产生成的脚本。</span><span class="sxs-lookup"><span data-stu-id="4b549-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="4b549-161">创建新的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="4b549-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="4b549-162">基于内容命名 GameObject。</span><span class="sxs-lookup"><span data-stu-id="4b549-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="4b549-163">在检查器面板中, 单击 "添加组件" 并添加 "Box 碰撞器"。</span><span class="sxs-lookup"><span data-stu-id="4b549-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![在检查器面板中, 单击 "添加组件" 并添加 "Box 碰撞器"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在检查器面板中, 单击 "添加组件" 并添加 "Box 碰撞器" #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="4b549-166">通过将 3D FBX 文件拖到 "项目" 面板中, 将其导入。</span><span class="sxs-lookup"><span data-stu-id="4b549-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="4b549-167">将对象拖到**新 GameObject 下**的 "层次结构" 面板中。</span><span class="sxs-lookup"><span data-stu-id="4b549-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![将对象拖到新 GameObject 下的 "层次结构" 面板中。](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="4b549-169">如果碰撞器维度与对象不匹配, 则调整它。</span><span class="sxs-lookup"><span data-stu-id="4b549-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="4b549-170">将对象旋转为面朝**Z 轴**。</span><span class="sxs-lookup"><span data-stu-id="4b549-170">Rotate the object to face **Z-axis**.</span></span>

   ![如果它与对象不匹配, 则调整碰撞器维度。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="4b549-172">将对象从 "层次结构" 面板拖到 "项目" 面板,**使其 prefab**。</span><span class="sxs-lookup"><span data-stu-id="4b549-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="4b549-173">在检查器面板的底部, 单击下拉列表, 创建并分配一个新的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="4b549-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="4b549-174">下面的示例演示如何添加 "brownchair" 并将其分配给 AssetBundle 名称。</span><span class="sxs-lookup"><span data-stu-id="4b549-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![在检查器面板的底部, 单击下拉列表并分配一个新的唯一名称。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="4b549-176">为模型对象准备缩略图。</span><span class="sxs-lookup"><span data-stu-id="4b549-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="4b549-177">![将一个图像拖到 "项目" 面板中, 并分配用于该对象的名称。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="4b549-178">在 Unity 项目的 "资产" 文件夹下创建一个名为 "Assetbundles" 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4b549-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="4b549-179">从 "资产" 菜单中选择 "生成 AssetBundles" 以生成文件。</span><span class="sxs-lookup"><span data-stu-id="4b549-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="4b549-180">![从 "资产" 菜单中选择 "生成 AssetBundles" 以生成文件。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="4b549-181">**将生成的文件上传到 OneDrive 上的/Files/Documents/HoloSketch 文件夹。**</span><span class="sxs-lookup"><span data-stu-id="4b549-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="4b549-182">仅上传 asset_unique_name 文件。</span><span class="sxs-lookup"><span data-stu-id="4b549-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="4b549-183">不需要上传清单文件或 AssetBundles 文件。</span><span class="sxs-lookup"><span data-stu-id="4b549-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="4b549-184">![将文件添加到文件/文档/HoloSketch/](images/holosketch-onedriveupload-1000px.png)
文件夹![在 HoloSketch 的 OneDrive 菜单中可以看到添加的3d 对象](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4b549-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="4b549-185">如何操作对象</span><span class="sxs-lookup"><span data-stu-id="4b549-185">How to manipulate the objects</span></span>

<span data-ttu-id="4b549-186">HoloSketch 支持3D 软件广泛使用的传统接口。</span><span class="sxs-lookup"><span data-stu-id="4b549-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="4b549-187">您可以使用 "移动"、"旋转"、"用手势和鼠标缩放对象"。</span><span class="sxs-lookup"><span data-stu-id="4b549-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="4b549-188">您可以通过语音或键盘在不同模式之间快速切换。</span><span class="sxs-lookup"><span data-stu-id="4b549-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="4b549-189">对象操作模式</span><span class="sxs-lookup"><span data-stu-id="4b549-189">Object manipulation modes</span></span>

<span data-ttu-id="4b549-190">![如何操作对象](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="4b549-191">*如何操作对象*</span><span class="sxs-lookup"><span data-stu-id="4b549-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="4b549-192">上下文和工具皮带菜单</span><span class="sxs-lookup"><span data-stu-id="4b549-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="4b549-193">**使用上下文菜单**</span><span class="sxs-lookup"><span data-stu-id="4b549-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="4b549-194">双击以打开上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="4b549-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="4b549-195">菜单项:</span><span class="sxs-lookup"><span data-stu-id="4b549-195">Menu items:</span></span>
* <span data-ttu-id="4b549-196">**布局图面:** 这是一个三维网格系统, 你可以在其中布局多个对象并将其作为一个组进行管理。</span><span class="sxs-lookup"><span data-stu-id="4b549-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="4b549-197">双击布局面以向其中添加对象。</span><span class="sxs-lookup"><span data-stu-id="4b549-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="4b549-198">**上述**使用多维数据集、球体、圆柱和圆锥进行 massing 研究。</span><span class="sxs-lookup"><span data-stu-id="4b549-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="4b549-199">**Business**打开 OneDrive 菜单以导入对象。</span><span class="sxs-lookup"><span data-stu-id="4b549-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="4b549-200">**帮助：** 显示帮助屏幕。</span><span class="sxs-lookup"><span data-stu-id="4b549-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="4b549-201">![上下文菜单](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="4b549-202">*上下文菜单*</span><span class="sxs-lookup"><span data-stu-id="4b549-202">*Contextual menu*</span></span>

<span data-ttu-id="4b549-203">**使用工具皮带菜单**</span><span class="sxs-lookup"><span data-stu-id="4b549-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="4b549-204">可从 "工具" 菜单使用 "移动"、"旋转"、"缩放"、"保存" 和 "加载" 场景。</span><span class="sxs-lookup"><span data-stu-id="4b549-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="4b549-205">使用键盘、笔势和语音命令</span><span class="sxs-lookup"><span data-stu-id="4b549-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="4b549-206">![键盘、手势和语音命令](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b549-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="4b549-207">*键盘、笔势和语音命令*</span><span class="sxs-lookup"><span data-stu-id="4b549-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="4b549-208">下载应用</span><span class="sxs-lookup"><span data-stu-id="4b549-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="4b549-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">从 Microsoft Store 免费下载并安装 HoloSketch 应用</a>
</span><span class="sxs-lookup"><span data-stu-id="4b549-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="4b549-210">已知问题</span><span class="sxs-lookup"><span data-stu-id="4b549-210">Known issues</span></span>
* <span data-ttu-id="4b549-211">**Unity 版本第5.4.5 节 f1**支持当前创建的资产包。</span><span class="sxs-lookup"><span data-stu-id="4b549-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="4b549-212">根据 OneDrive 中的数据量, 应用可能看起来就像在加载 OneDrive 内容时已停止</span><span class="sxs-lookup"><span data-stu-id="4b549-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="4b549-213">目前, 保存和加载功能仅支持基元对象</span><span class="sxs-lookup"><span data-stu-id="4b549-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="4b549-214">在上下文菜单上禁用文本、声音、视频和照片菜单</span><span class="sxs-lookup"><span data-stu-id="4b549-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="4b549-215">工具皮带菜单上的 "播放" 按钮将清除操作 gizmos</span><span class="sxs-lookup"><span data-stu-id="4b549-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="4b549-216">共享草图</span><span class="sxs-lookup"><span data-stu-id="4b549-216">Sharing your sketches</span></span>

<span data-ttu-id="4b549-217">可以通过说 "你好 Cortana, 开始/停止记录" 来使用 HoloLens 中的视频录制功能。</span><span class="sxs-lookup"><span data-stu-id="4b549-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="4b549-218">同时按向上键和向下键, 拍摄草图的图片。</span><span class="sxs-lookup"><span data-stu-id="4b549-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="4b549-219">关于作者</span><span class="sxs-lookup"><span data-stu-id="4b549-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4b549-220"><b>盾 Yoon 停车场</b></span><span class="sxs-lookup"><span data-stu-id="4b549-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="4b549-221">UX 设计器@Microsoft</span><span class="sxs-lookup"><span data-stu-id="4b549-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4b549-222"><b>Sebring</b></span><span class="sxs-lookup"><span data-stu-id="4b549-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="4b549-223">开发@Microsoft</span><span class="sxs-lookup"><span data-stu-id="4b549-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
