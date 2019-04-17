---
title: 案例研究-构建 HoloSketch、 空间布局和 HoloLens 的素描应用的用户体验
description: HoloSketch 是一个设备上的空间布局和素描 HoloLens 以帮助您构建全息版体验的工具的用户体验。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch，HoloLens，Windows Mixed Reality，素描。 应用程序
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591866"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="4f1b1-104">案例研究-构建 HoloSketch、 空间布局和 HoloLens 的素描应用的用户体验</span><span class="sxs-lookup"><span data-stu-id="4f1b1-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="4f1b1-105">HoloSketch 是一个设备上的空间布局和素描 HoloLens 以帮助您构建全息版体验的工具的用户体验。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="4f1b1-106">HoloSketch 配合配对的蓝牙键盘和鼠标，以及手势和语音命令。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="4f1b1-107">HoloSketch 旨在提供简单的 UX 布局工具，用于快速可视化效果和迭代。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="4f1b1-108">![HoloSketch:空间布局和 HoloLens 的素描应用的用户体验。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="4f1b1-109">*HoloSketch： 空间布局和 HoloLens 的素描应用的用户体验*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="4f1b1-110">![以进行快速可视化和迭代一个简单的 UX 布局工具。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="4f1b1-111">*一个简单的 UX 布局工具以进行快速可视化和迭代*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="4f1b1-112">功能</span><span class="sxs-lookup"><span data-stu-id="4f1b1-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="4f1b1-113">用于快速研究和规模原型设计的基元</span><span class="sxs-lookup"><span data-stu-id="4f1b1-113">Primitives for quick studies and scale-prototyping</span></span>

![使用基元形状](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="4f1b1-115">对于快速 massing 研究和规模原型设计使用基元的形状。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="4f1b1-116">通过 OneDrive 导入对象</span><span class="sxs-lookup"><span data-stu-id="4f1b1-116">Import objects through OneDrive</span></span>

![导入对象](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="4f1b1-118">PNG/JPG 图像或三维 FBX 对象导入 （需要在 Unity 中的打包） 到通过 OneDrive 的混合的现实空间。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="4f1b1-119">操作对象</span><span class="sxs-lookup"><span data-stu-id="4f1b1-119">Manipulate objects</span></span>

![操作对象](images/manipulate-objects-640px.jpg)

<span data-ttu-id="4f1b1-121">操作使用熟悉的三维对象接口的对象 （移动/旋转/缩放）。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="4f1b1-122">蓝牙、 鼠标/键盘、 手势和语音命令</span><span class="sxs-lookup"><span data-stu-id="4f1b1-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![支持蓝牙](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="4f1b1-124">HoloSketch 支持蓝牙鼠标/键盘、 手势和语音命令。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="4f1b1-125">后台</span><span class="sxs-lookup"><span data-stu-id="4f1b1-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="4f1b1-126">遇到你的设备中的设计的重要性</span><span class="sxs-lookup"><span data-stu-id="4f1b1-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="4f1b1-127">在设计时的内容对于 HoloLens，务必体验你的设备中的设计。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="4f1b1-128">混合的现实应用程序设计的最大挑战之一是很难获得的规模、 位置和深度，尤其是通过传统的 2D 草图。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="4f1b1-129">2D 的成本的通信</span><span class="sxs-lookup"><span data-stu-id="4f1b1-129">Cost of 2D based communication</span></span>

<span data-ttu-id="4f1b1-130">若要有效地传达 UX 流和向其他人的方案，设计器可能最终会花费大量时间来创建使用传统的 2D 工具，例如 Illustrator、 Photoshop 和 PowerPoint 的资产。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="4f1b1-131">这些 2D 设计通常需要额外的工作量才能将其转换到 3D。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="4f1b1-132">一些观点在会丢失这种转换从二维到三维物体。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="4f1b1-133">复杂的部署过程</span><span class="sxs-lookup"><span data-stu-id="4f1b1-133">Complex deployment process</span></span>

<span data-ttu-id="4f1b1-134">由于混合的现实是为我们新的画布，它会按其性质涉及大量设计迭代和试用和错误。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="4f1b1-135">对于不熟悉 Unity 和 Visual Studio 等工具的设计器，并不容易 HoloLens 一起添加某项。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="4f1b1-136">通常，您需要经历以下过程以查看您的设备中的二维/三维作品。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="4f1b1-137">这是快速循环访问的想法和方案的设计器的大障碍。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="4f1b1-138">![复杂的部署过程](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="4f1b1-139">*部署过程*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="4f1b1-140">使用 HoloSketch 简化的处理</span><span class="sxs-lookup"><span data-stu-id="4f1b1-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="4f1b1-141">使用 HoloSketch，我们想要简化此过程不涉及开发工具和设备门户配对。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="4f1b1-142">使用 OneDrive，用户可以轻松地将二维/三维资产置于 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="4f1b1-143">![使用 HoloSketch 简化的处理](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="4f1b1-144">*使用 HoloSketch 简化的处理*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="4f1b1-145">鼓励三维设计思维和解决方案</span><span class="sxs-lookup"><span data-stu-id="4f1b1-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="4f1b1-146">我们认为此工具会使设计人员有机会了解真正三维空间中的解决方案并不会停滞在 2D。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="4f1b1-147">它们无需考虑为它们的 UI 创建三维背景，由于背景是在 Hololens 的情况下现实世界。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="4f1b1-148">HoloSketch 打开设计器，可轻松地在 Hololens 上浏览 3D 设计一种方法。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="4f1b1-149">入门</span><span class="sxs-lookup"><span data-stu-id="4f1b1-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="4f1b1-150">如何导入 HoloSketch 2D 图像 (JPG/PNG)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="4f1b1-151">将 JPG/PNG 图像上传到你的 OneDrive 文件夹文档/HoloSketch。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="4f1b1-152">在中 HoloSketch OneDrive 菜单中，您将能够选择并将图像放在环境中。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="4f1b1-153">![导入的 2D 图像](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="4f1b1-154">*导入图像和三维对象通过 OneDrive*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="4f1b1-155">如何导入 HoloSketch 三维对象</span><span class="sxs-lookup"><span data-stu-id="4f1b1-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="4f1b1-156">上传到 OneDrive 文件夹，请按照以下步骤来打包到 Unity 资产捆绑三维对象。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="4f1b1-157">使用此过程可以从 Maya、 影院 4d 和 Microsoft 画图 3D 等的 3D 软件导 FBX/OBJ 文件。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4f1b1-158">目前，使用 Unity 版本 5.4.5f1 支持资产捆绑包创建。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="4f1b1-159">下载并打开 Unity 项目[AssetBunlder_Unity](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="4f1b1-160">此 Unity 项目包括用于捆绑包资产生成的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="4f1b1-161">创建新的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="4f1b1-162">名称基于内容的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="4f1b1-163">在检查器窗格中，单击添加组件并添加盒状碰撞体。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![在检查器窗格中，单击添加组件，并添加盒状碰撞体](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在检查器窗格中，单击添加组件，并添加盒状碰撞体 #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="4f1b1-166">通过将其拖到项目面板中，导入三维 FBX 文件。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="4f1b1-167">将对象拖到层次结构面板**在新的 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![将对象拖到层次结构面板下新的 GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="4f1b1-169">调整碰撞体维度，如果与该对象不匹配。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="4f1b1-170">旋转对象面临着**z 轴**。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-170">Rotate the object to face **Z-axis**.</span></span>

   ![调整碰撞体维度，如果与该对象不匹配。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="4f1b1-172">将对象从层次结构面板拖到项目面板**使其预设**。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="4f1b1-173">在检查器面板的底部，单击下拉列表、 创建和分配新的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="4f1b1-174">以下示例演示如何添加并分配 brownchair AssetBundle 名称。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![在检查器面板的底部，单击下拉列表中并分配新的唯一名称。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="4f1b1-176">为模型对象准备缩略图。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="4f1b1-177">![将图像拖到项目面板并将分配的对象使用的名称。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="4f1b1-178">在 Unity 项目的资产文件夹下创建名为 Assetbundles 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="4f1b1-179">从资产菜单上，选择生成 AssetBundles 生成文件。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="4f1b1-180">![从资产菜单上，选择生成 AssetBundles 生成文件。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="4f1b1-181">**将生成的文件上传到 OneDrive 上的 /Files/Documents/HoloSketch 文件夹。**</span><span class="sxs-lookup"><span data-stu-id="4f1b1-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="4f1b1-182">上传仅 asset_unique_name 文件。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="4f1b1-183">不需要上传清单文件或 AssetBundles 文件。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="4f1b1-184">![将文件添加到文件/文档/HoloSketch/文件夹](images/holosketch-onedriveupload-1000px.png)
![您将看到 HoloSketch 的 OneDrive 菜单中添加了三维对象](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="4f1b1-185">如何操作的对象</span><span class="sxs-lookup"><span data-stu-id="4f1b1-185">How to manipulate the objects</span></span>

<span data-ttu-id="4f1b1-186">HoloSketch 支持 3D 软件中广泛使用的传统接口。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="4f1b1-187">可以使用移动、 旋转、 缩放手势和鼠标的对象。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="4f1b1-188">您可以快速使用语音或键盘的不同模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="4f1b1-189">对象操作模式</span><span class="sxs-lookup"><span data-stu-id="4f1b1-189">Object manipulation modes</span></span>

<span data-ttu-id="4f1b1-190">![如何操作的对象](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="4f1b1-191">*如何操作的对象*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="4f1b1-192">上下文和工具腰带菜单</span><span class="sxs-lookup"><span data-stu-id="4f1b1-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="4f1b1-193">**使用上下文菜单**</span><span class="sxs-lookup"><span data-stu-id="4f1b1-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="4f1b1-194">双精度敲击打开上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="4f1b1-195">菜单项：</span><span class="sxs-lookup"><span data-stu-id="4f1b1-195">Menu items:</span></span>
* <span data-ttu-id="4f1b1-196">**布局图面：** 这是一个三维网格系统布局的可能多个对象，并管理它们作为一个组。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="4f1b1-197">以无线方式-双击布局图面，将对象添加到它。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="4f1b1-198">**基元层：** 用于多维数据集、 球体、 圆柱体和圆锥 massing 研究。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="4f1b1-199">**OneDrive:** 打开 OneDrive 菜单导入的对象。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="4f1b1-200">**帮助：** 显示帮助屏幕。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="4f1b1-201">![上下文菜单](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="4f1b1-202">*上下文菜单*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-202">*Contextual menu*</span></span>

<span data-ttu-id="4f1b1-203">**使用工具腰带菜单**</span><span class="sxs-lookup"><span data-stu-id="4f1b1-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="4f1b1-204">移动、 旋转、 缩放，保存和加载场景可从工具腰带菜单。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="4f1b1-205">使用键盘、 手势和语音命令</span><span class="sxs-lookup"><span data-stu-id="4f1b1-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="4f1b1-206">![键盘、 手势和语音命令](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4f1b1-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="4f1b1-207">*键盘、 笔势和语音命令*</span><span class="sxs-lookup"><span data-stu-id="4f1b1-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="4f1b1-208">下载应用</span><span class="sxs-lookup"><span data-stu-id="4f1b1-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="4f1b1-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">下载并安装 HoloSketch 应用免费从 Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="4f1b1-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="4f1b1-210">已知问题</span><span class="sxs-lookup"><span data-stu-id="4f1b1-210">Known issues</span></span>
* <span data-ttu-id="4f1b1-211">目前资产捆绑包创建支持**Unity 版本 5.4.5f1。**</span><span class="sxs-lookup"><span data-stu-id="4f1b1-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="4f1b1-212">具体取决于你的 OneDrive 中的数据量，该应用程序可能会出现像它已停止加载 OneDrive 内容时</span><span class="sxs-lookup"><span data-stu-id="4f1b1-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="4f1b1-213">目前，保存并加载功能仅支持基元对象</span><span class="sxs-lookup"><span data-stu-id="4f1b1-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="4f1b1-214">文本、 声音、 视频和照片菜单处于禁用状态的上下文菜单上</span><span class="sxs-lookup"><span data-stu-id="4f1b1-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="4f1b1-215">工具腰带菜单上的 Play 按钮清除操作 gizmos 请</span><span class="sxs-lookup"><span data-stu-id="4f1b1-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="4f1b1-216">共享你草图</span><span class="sxs-lookup"><span data-stu-id="4f1b1-216">Sharing your sketches</span></span>

<span data-ttu-id="4f1b1-217">您可以使用视频录制中的功能 HoloLens 通过说你好，小娜启动/停止录制。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="4f1b1-218">按向上/向下键在一起以拍摄照片你草图的卷。</span><span class="sxs-lookup"><span data-stu-id="4f1b1-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="4f1b1-219">关于作者</span><span class="sxs-lookup"><span data-stu-id="4f1b1-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4f1b1-220"><b>盾 Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="4f1b1-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="4f1b1-221">UX 设计人员 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4f1b1-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4f1b1-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="4f1b1-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="4f1b1-223">开发人员 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4f1b1-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
