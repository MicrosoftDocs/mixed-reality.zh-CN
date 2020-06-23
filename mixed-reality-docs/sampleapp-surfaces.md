---
title: 图面
description: 表面是 Microsoft 混合现实设计实验室的开源示例应用。 本文探讨了如何使用视觉、音频和完全清晰的手写跟踪来创建 tactile 成名。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，mrtk，设计，示例应用，控件
ms.openlocfilehash: fb6948ceda2a059323d23d72d6d3245a3a9896ee
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240450"
---
# <a name="surfaces"></a><span data-ttu-id="109e4-105">图面</span><span class="sxs-lookup"><span data-stu-id="109e4-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="109e4-106">本文讨论了我们在[混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例，这是我们与混合现实应用开发的知识和建议。</span><span class="sxs-lookup"><span data-stu-id="109e4-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="109e4-107">我们设计相关的文章和代码将随着我们的新发现而发展。</span><span class="sxs-lookup"><span data-stu-id="109e4-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="109e4-108">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)是 Microsoft 混合现实设计实验室的开源示例应用。</span><span class="sxs-lookup"><span data-stu-id="109e4-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="109e4-109">本文探讨了如何使用视觉、音频和完全清晰的手写跟踪来创建 tactile 成名。</span><span class="sxs-lookup"><span data-stu-id="109e4-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![图面](images/MRDL_Surfaces_1.jpg)

## <a name="about-the-app"></a><span data-ttu-id="109e4-111">关于应用</span><span class="sxs-lookup"><span data-stu-id="109e4-111">About the app</span></span>
<span data-ttu-id="109e4-112">图面演示了如何使用混合现实工具包（MRTK）的输入系统和构建基块创建适用于 HoloLens 2 的应用体验。</span><span class="sxs-lookup"><span data-stu-id="109e4-112">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="109e4-113">在此项目中，可以找到以下示例：</span><span class="sxs-lookup"><span data-stu-id="109e4-113">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="109e4-114">使用 MRTK 的[输入系统](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)，尤其是手动/联合跟踪。</span><span class="sxs-lookup"><span data-stu-id="109e4-114">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="109e4-115">使用 MRTK 的[标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)来实现高性能图形。</span><span class="sxs-lookup"><span data-stu-id="109e4-115">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="109e4-116">可以使用此项目的组件来创建自己的混合现实应用体验。</span><span class="sxs-lookup"><span data-stu-id="109e4-116">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="109e4-117">MR 开发人员 2020-知识</span><span class="sxs-lookup"><span data-stu-id="109e4-117">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="109e4-118">从 MR 表面应用知识</span><span class="sxs-lookup"><span data-stu-id="109e4-118">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="109e4-119">Lars Simkins，MRDL surface 应用后的高级设计人员将讨论应用的设计故事和技术要点。</span><span class="sxs-lookup"><span data-stu-id="109e4-119">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="109e4-120">GitHub 上的项目存储库</span><span class="sxs-lookup"><span data-stu-id="109e4-120">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="109e4-121">从 HoloLens 2 Microsoft Store 下载应用</span><span class="sxs-lookup"><span data-stu-id="109e4-121">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="109e4-122">（应用仅在 HoloLens 2 上可用）</span><span class="sxs-lookup"><span data-stu-id="109e4-122">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="109e4-123">关于作者</span><span class="sxs-lookup"><span data-stu-id="109e4-123">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="109e4-124"><b>盾 Yoon 停车场</b></span><span class="sxs-lookup"><span data-stu-id="109e4-124"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="109e4-125">UX 设计器@Microsoft</span><span class="sxs-lookup"><span data-stu-id="109e4-125">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="109e4-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="109e4-126">See also</span></span>

* [<span data-ttu-id="109e4-127">可交互对象</span><span class="sxs-lookup"><span data-stu-id="109e4-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="109e4-128">对象集合</span><span class="sxs-lookup"><span data-stu-id="109e4-128">Object collection</span></span>](object-collection.md)
