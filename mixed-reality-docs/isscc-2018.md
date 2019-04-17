---
title: 深度照相机白皮书-ISSCC 2018
description: 讨论深度照相机以适用于 Azure 和 HoloLens 的下一个版本，在项目 Kinect 中利用的技术白皮书。
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: 事件、 iscc、 计算机视觉、 研究、 kinect、 hololens、 深度、 图表目录
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592202"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="dbf49-104">深度照相机白皮书-ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="dbf49-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="dbf49-105">**标题：** 1Mpixel 65 纳米 BSI 320 MHz 解调的图表目录映像传感器与 3.5μm 全局快门像素和模拟装箱</span><span class="sxs-lookup"><span data-stu-id="dbf49-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="dbf49-106">**供稿人：** Cyrus S Bamji、 Swati Mehta、 Barry Thompson、 演讲 Elkhatib、 Stefan Wurster、 Onur Akkaya、 Andrew Payne、 John Godbaz、 Mike Fenton、 Vijay Rajasekaran、 Larry Prather、 Satya Nagaraja、 Vishali Mogallapu，窗格会 Snow、 丰富 McCauley、 Mustansir Mukadam，Iskender AgiShaun McCarthy、 Zhanping Xu、 Travis Perry、 William Qian、 Vei Han Chan、 Prabhu Adepu、 Gazi Ali、 Muneeb Ahmed、 Aditya Mukherjee、 Sheethal Nayak、 Dave Gampell、 Sunil Acharya，Lou Kordus Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="dbf49-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="dbf49-107">**在 ISSCC 2018 和 ISSCC 度中发布。技术。文章中，于 2018 年 2 月。**</span><span class="sxs-lookup"><span data-stu-id="dbf49-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="dbf49-108">C.</span><span class="sxs-lookup"><span data-stu-id="dbf49-108">C.</span></span> <span data-ttu-id="dbf49-109">Bamji et 都"1Mpixel 65 纳米 BSI 320 MHz 解调的图表目录映像传感器与 3.5μm 全局快门像素和模拟装箱"ISSCC 度。</span><span class="sxs-lookup"><span data-stu-id="dbf49-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="dbf49-110">技术。</span><span class="sxs-lookup"><span data-stu-id="dbf49-110">Tech.</span></span> <span data-ttu-id="dbf49-111">提供有关探讨第 94 95 中，于 2018 年 2 月。</span><span class="sxs-lookup"><span data-stu-id="dbf49-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="dbf49-112">IEEE 浏览链接： https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="dbf49-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="dbf49-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="dbf49-113">© 2018 IEEE.</span></span> <span data-ttu-id="dbf49-114">只允许在此材料的个人使用。</span><span class="sxs-lookup"><span data-stu-id="dbf49-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="dbf49-115">从 IEEE 权限必须获取有关所有其他用法，在任何当前或将来的媒体，包括重新打印/重新发布此材料的广告或宣传目的，创建新集合的工作原理，限制转售或重新分发到服务器或组列表，或这项工作中其他作品的任何受版权保护组件的重复使用。</span><span class="sxs-lookup"><span data-stu-id="dbf49-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="dbf49-116">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="dbf49-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="dbf49-117">![预览版的白皮书](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="dbf49-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="dbf49-118">下载深度照相机白皮书</span><span class="sxs-lookup"><span data-stu-id="dbf49-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
