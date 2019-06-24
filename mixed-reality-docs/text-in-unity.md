---
title: 在 Unity 中的文本
description: 若要显示的文本在 Unity 中，有两种类型的文本组件可以使用-UI 文本和三维文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，用于控制字体、 版式、 ui、 用户体验
ms.openlocfilehash: 45037f27f68a19478fd56a6edc940fbe45ae7671
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326302"
---
# <a name="text-in-unity"></a><span data-ttu-id="01c85-104">在 Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="01c85-104">Text in Unity</span></span>

<span data-ttu-id="01c85-105">文本是全息版应用中的最重要的组件之一。</span><span class="sxs-lookup"><span data-stu-id="01c85-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="01c85-106">若要显示的文本在 Unity 中，有两种类型的文本组件可以使用-UI 文本和三维文本网格。</span><span class="sxs-lookup"><span data-stu-id="01c85-106">To display text in Unity, there are two types of text components you can use — UI Text and 3D Text Mesh.</span></span> <span data-ttu-id="01c85-107">默认情况下，它们显示模糊并且太大。</span><span class="sxs-lookup"><span data-stu-id="01c85-107">By default they appear blurry and are too big.</span></span> <span data-ttu-id="01c85-108">您需要调整几个变量，以获得 sharp、 高质量的文本中 HoloLens 有合理的大小。</span><span class="sxs-lookup"><span data-stu-id="01c85-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="01c85-109">可以通过应用缩放因子来获取正确的尺寸，使用 UI 文本和三维文本网格组件时，获得更好地呈现质量。</span><span class="sxs-lookup"><span data-stu-id="01c85-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="01c85-110">![如何获得 sharp 和美观的文本](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="01c85-111">*在 Unity 中的模糊的默认文本*</span><span class="sxs-lookup"><span data-stu-id="01c85-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-fonts-in-unity"></a><span data-ttu-id="01c85-112">使用 Unity 中的字体</span><span class="sxs-lookup"><span data-stu-id="01c85-112">Working with fonts in Unity</span></span>

<span data-ttu-id="01c85-113">Unity 假定所有的新元素添加到场景中大小或可以转换为大约 1 米 HoloLens 上的 100%转换小数位数 1 Unity 单元。</span><span class="sxs-lookup"><span data-stu-id="01c85-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="01c85-114">在字体的情况下的边界框三维 TextMesh 有默认情况下在大约 1 米的高度。</span><span class="sxs-lookup"><span data-stu-id="01c85-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="01c85-115">![使用 Unity 中的字体](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="01c85-116">*默认 Unity 文本占用 1 Unity 单元即 1 米*</span><span class="sxs-lookup"><span data-stu-id="01c85-116">*Default Unity text occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="01c85-117">大多数的可视化设计器使用点来定义在现实生活中的字体大小。</span><span class="sxs-lookup"><span data-stu-id="01c85-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="01c85-118">有大约 2835 (2,834.645666399962) 中 1 米的点。</span><span class="sxs-lookup"><span data-stu-id="01c85-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="01c85-119">根据点系统转换为 1 米以及 Unity 的默认文本 Mesh 字体大小的 13，13 除以 2835年等于 0.0046 (0.004586111116 确切地) 的简单数学开始提供合适的标准扩展 （一些可能想要为 0.005 舍入）。</span><span class="sxs-lookup"><span data-stu-id="01c85-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="01c85-120">缩放文本对象或对这些值的容器将仅允许 1 对 1 转换字体的大小在设计程序中，但还提供了一个标准，因此您可以维护整个应用程序或游戏的一致性。</span><span class="sxs-lookup"><span data-stu-id="01c85-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your application or game.</span></span>

<span data-ttu-id="01c85-121">![Unity 3D 文本网格使用不同的字体大小](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-121">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="01c85-122">*Unity 3D 文本网格使用优化的值*</span><span class="sxs-lookup"><span data-stu-id="01c85-122">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="01c85-123">当将用户界面或画布的基于的文本元素添加到场景中，大小不一致会仍然为更高版本。</span><span class="sxs-lookup"><span data-stu-id="01c85-123">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="01c85-124">两种大小的差异是大约 1000年%，这会基于 UI 文本组件到 0.00046 (0.0004586111116 确切地) 显示比例系数或 0.0005 的舍入值。</span><span class="sxs-lookup"><span data-stu-id="01c85-124">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="01c85-125">![每单位值的不同动态像素与 unity UI 文本](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-125">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="01c85-126">*使用优化值的 unity UI 文本*</span><span class="sxs-lookup"><span data-stu-id="01c85-126">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="01c85-127">相应的字体的默认值可能会受到该字体或字体如何导入 Unity 的纹理大小。</span><span class="sxs-lookup"><span data-stu-id="01c85-127">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="01c85-128">这些测试已执行基于在 Unity 中，默认 Arial 字体，以及其他已导入的一种字体。</span><span class="sxs-lookup"><span data-stu-id="01c85-128">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="01c85-129">尖锐文本呈现质量与正确的维度</span><span class="sxs-lookup"><span data-stu-id="01c85-129">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="01c85-130">根据这些缩放比例系数，我们创建了[UI 文本和三维文本 Mesh 文本预设](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="01c85-130">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="01c85-131">开发人员可以利用这些预设可以清晰的文本和一致的字体大小。</span><span class="sxs-lookup"><span data-stu-id="01c85-131">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="01c85-132">![尖锐文本呈现质量与正确的维度](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-132">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="01c85-133">*尖锐文本呈现质量与正确的维度*</span><span class="sxs-lookup"><span data-stu-id="01c85-133">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="01c85-134">与封闭支持的着色器</span><span class="sxs-lookup"><span data-stu-id="01c85-134">Shader with occlusion support</span></span>

<span data-ttu-id="01c85-135">Unity 的默认字体材料不支持的阻挡物。</span><span class="sxs-lookup"><span data-stu-id="01c85-135">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="01c85-136">因此，将默认情况下看到对象后面的文本。</span><span class="sxs-lookup"><span data-stu-id="01c85-136">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="01c85-137">我们包含了一个简单[支持是封闭的着色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)。</span><span class="sxs-lookup"><span data-stu-id="01c85-137">We have included a simple [shader that supports the occlusion](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders).</span></span> <span data-ttu-id="01c85-138">下图显示了与默认字体材料 （左） 文本以及用正确的阻挡物 （右） 的文本。</span><span class="sxs-lookup"><span data-stu-id="01c85-138">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="01c85-139">![与封闭支持的着色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-139">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="01c85-140">*与封闭支持的着色器*</span><span class="sxs-lookup"><span data-stu-id="01c85-140">*Shader with occlusion support*</span></span>

## <a name="recommended-type-size"></a><span data-ttu-id="01c85-141">建议的类型大小</span><span class="sxs-lookup"><span data-stu-id="01c85-141">Recommended type size</span></span>

<span data-ttu-id="01c85-142">正如您期望的我们使用一台 PC 或平板电脑设备 （通常为 12 – 32pt) 的类型大小相当小看 2 米的距离。</span><span class="sxs-lookup"><span data-stu-id="01c85-142">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="01c85-143">这取决于每个字体的特征，但一般情况下建议的最小类型大小以提高可读性而无需笔划振动是围绕 30pt，根据上面介绍的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="01c85-143">It depends on the characteristics of each font, but in general the recommended minimum type size for legibility without stroke vibration is around 30pt, based on the scaling factor introduced above.</span></span> <span data-ttu-id="01c85-144">如果您的应用程序应使用在近距离，可以使用较小类型的大小。</span><span class="sxs-lookup"><span data-stu-id="01c85-144">If your app is supposed to be used at a closer distance, smaller type sizes could be used.</span></span> <span data-ttu-id="01c85-145">用于选择字体，Segoe UI （Windows 默认字体） 适用于大多数情况。</span><span class="sxs-lookup"><span data-stu-id="01c85-145">For the font selection, Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="01c85-146">但是，避免使用 light 或半浅色字体类型大小小于 42pt 由于精简垂直笔画将振动，它将会降低以增强可读性。</span><span class="sxs-lookup"><span data-stu-id="01c85-146">However, avoid using light or semi light fonts for type sizes under 42pt since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="01c85-147">最新版本，如果有足够笔画粗细能正常工作。</span><span class="sxs-lookup"><span data-stu-id="01c85-147">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="01c85-148">例如，Helvetica，Arial 查看丰富多彩和 HoloLens 中非常清晰的常规或加粗的权重。</span><span class="sxs-lookup"><span data-stu-id="01c85-148">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="01c85-149">![建议的类型大小](images/hug-text-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="01c85-149">![Recommended type size](images/hug-text-08-1000px.png)</span></span><br>
<span data-ttu-id="01c85-150">*类型的负载增加示例*</span><span class="sxs-lookup"><span data-stu-id="01c85-150">*Type ramp example*</span></span>

## <a name="see-also"></a><span data-ttu-id="01c85-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="01c85-151">See also</span></span>

* [<span data-ttu-id="01c85-152">在 MixedRealityToolkit 文本预设</span><span class="sxs-lookup"><span data-stu-id="01c85-152">Text Prefab in the MixedRealityToolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [<span data-ttu-id="01c85-153">示例文本布局预设和场景</span><span class="sxs-lookup"><span data-stu-id="01c85-153">Sample text layout prefab and scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [<span data-ttu-id="01c85-154">版式</span><span class="sxs-lookup"><span data-stu-id="01c85-154">Typography</span></span>](typography.md)

 
