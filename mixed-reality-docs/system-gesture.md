---
title: 系统手势
description: 用于调用 "开始" 菜单的系统手势。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实、手势、交互、设计
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064242"
---
# <a name="system-gesture"></a><span data-ttu-id="b2290-104">系统手势</span><span class="sxs-lookup"><span data-stu-id="b2290-104">System gesture</span></span>

<span data-ttu-id="b2290-105">系统手势是用于调用 "开始" 菜单的笔势。</span><span class="sxs-lookup"><span data-stu-id="b2290-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="b2290-106">它相当于按键盘上的 Windows 键、Xbox 控制器上的 Xbox 按钮或沉浸式耳机运动控制器上的 Windows 按钮。</span><span class="sxs-lookup"><span data-stu-id="b2290-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="b2290-107">务必要了解在每个混合现实设备上为系统保留了哪些手势，以防止在设计交互时出现冲突。</span><span class="sxs-lookup"><span data-stu-id="b2290-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="b2290-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="b2290-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b2290-109"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="b2290-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b2290-110"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="b2290-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b2290-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b2290-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b2290-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="b2290-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b2290-113">布隆</span><span class="sxs-lookup"><span data-stu-id="b2290-113">Bloom</span></span></td>
        <td><span data-ttu-id="b2290-114">✔️</span><span class="sxs-lookup"><span data-stu-id="b2290-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="b2290-115">手腕按钮</span><span class="sxs-lookup"><span data-stu-id="b2290-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b2290-116">✔️</span><span class="sxs-lookup"><span data-stu-id="b2290-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="b2290-117">眼睛和掌上手掌</span><span class="sxs-lookup"><span data-stu-id="b2290-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b2290-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b2290-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="b2290-119">布隆</span><span class="sxs-lookup"><span data-stu-id="b2290-119">Bloom</span></span>
<span data-ttu-id="b2290-120">若要在 HoloLens 中显示 "开始" 菜单（第一代），我们设计了 "布隆"，这是一个模拟花朵开花的符号手势。</span><span class="sxs-lookup"><span data-stu-id="b2290-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="b2290-121">这是 surefooted 交互的独特之处，易于执行，并可快速回调。</span><span class="sxs-lookup"><span data-stu-id="b2290-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="b2290-122">若要在 HoloLens （第一代）上执行布隆手势，请将掌托在一起，并将其放在一起，然后将手指向外伸展。</span><span class="sxs-lookup"><span data-stu-id="b2290-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b2290-123">![布隆关闭](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="b2290-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="b2290-124">**步骤1：将手掌集中到一起**</span><span class="sxs-lookup"><span data-stu-id="b2290-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b2290-125">![布隆打开](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="b2290-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="b2290-126">**步骤2：掌上手掌**</span><span class="sxs-lookup"><span data-stu-id="b2290-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="b2290-127">手腕按钮</span><span class="sxs-lookup"><span data-stu-id="b2290-127">Wrist button</span></span>
<span data-ttu-id="b2290-128">在 HoloLens 2 中，我们将布隆手势替换为虚拟手腕按钮，该按钮允许更多的 instinctual 交互，无需其他教学。</span><span class="sxs-lookup"><span data-stu-id="b2290-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="b2290-129">通过向用户显示手腕上的按钮，用户可以以直观的方式进行访问，并将其与他人一起使用。</span><span class="sxs-lookup"><span data-stu-id="b2290-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b2290-130">![手腕按钮已准备好](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="b2290-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="b2290-131">**步骤1：掌上以显示 "手腕" 按钮**</span><span class="sxs-lookup"><span data-stu-id="b2290-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b2290-132">![手腕按钮按](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="b2290-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="b2290-133">**步骤2：按 "手腕" 按钮**</span><span class="sxs-lookup"><span data-stu-id="b2290-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="b2290-134">眼睛和掌上</span><span class="sxs-lookup"><span data-stu-id="b2290-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="b2290-135">我们还为 HoloLens 2 中的轻松访问设计了一个直通解决方案。</span><span class="sxs-lookup"><span data-stu-id="b2290-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="b2290-136">此手势要求用户可以注视手腕按钮，然后使用同一手来使用拇指和食指执行手掌紧。</span><span class="sxs-lookup"><span data-stu-id="b2290-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="b2290-137">![手腕按钮已准备好](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="b2290-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="b2290-138">**步骤1：掌上以显示 "手腕" 按钮**</span><span class="sxs-lookup"><span data-stu-id="b2290-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b2290-139">![手腕按钮挤压](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="b2290-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="b2290-140">**步骤2：目视看着按钮，然后捏紧**</span><span class="sxs-lookup"><span data-stu-id="b2290-140">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="b2290-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2290-141">See also</span></span>

* [<span data-ttu-id="b2290-142">本能交互</span><span class="sxs-lookup"><span data-stu-id="b2290-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b2290-143">眼部凝视</span><span class="sxs-lookup"><span data-stu-id="b2290-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="b2290-144">语音输入</span><span class="sxs-lookup"><span data-stu-id="b2290-144">Voice input</span></span>](voice-input.md)
