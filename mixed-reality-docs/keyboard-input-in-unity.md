---
title: 在 Unity 中的键盘输入
description: Unity 提供用于接受键盘输入时没有可用的物理键盘 TouchScreenKeyboard 类。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 键盘输入，unity touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593025"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="f2907-104">在 Unity 中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="f2907-104">Keyboard input in Unity</span></span>

<span data-ttu-id="f2907-105">\**命名空间：\*\*\*UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="f2907-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="f2907-106">类型：*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="f2907-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="f2907-107">尽管 HoloLens 支持许多形式的输入包括蓝牙键盘，大多数应用程序不能假定所有用户都都可用的物理键盘。</span><span class="sxs-lookup"><span data-stu-id="f2907-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="f2907-108">如果你的应用程序需要文本输入，则应提供某种形式的屏幕键盘上。</span><span class="sxs-lookup"><span data-stu-id="f2907-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="f2907-109">Unity 提供了*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类用于接受键盘输入时没有可用的物理键盘。</span><span class="sxs-lookup"><span data-stu-id="f2907-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="f2907-110">在 Unity 中的 HoloLens 系统键盘行为</span><span class="sxs-lookup"><span data-stu-id="f2907-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="f2907-111">HoloLens 上, *TouchScreenKeyboard*利用屏幕键盘上的系统。</span><span class="sxs-lookup"><span data-stu-id="f2907-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="f2907-112">屏幕键盘上的系统不能覆盖容量耗尽视图顶部，因此，Unity 创建辅助的 2D 的 XAML 视图以显示键盘，然后输入提交后返回到容量耗尽视图。</span><span class="sxs-lookup"><span data-stu-id="f2907-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="f2907-113">用户流如下所示：</span><span class="sxs-lookup"><span data-stu-id="f2907-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="f2907-114">用户执行的操作，从而导致应用程序代码调用*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f2907-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="f2907-115">应用负责暂停应用程序状态，然后才能调用*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f2907-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="f2907-116">应用程序可能会不断切换回容量耗尽视图之前终止</span><span class="sxs-lookup"><span data-stu-id="f2907-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="f2907-117">Unity 将切换到 2D 的 XAML 视图，即自动放置在世界</span><span class="sxs-lookup"><span data-stu-id="f2907-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="f2907-118">用户输入文本使用系统键盘和提交或取消</span><span class="sxs-lookup"><span data-stu-id="f2907-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="f2907-119">Unity 切换回容量耗尽视图</span><span class="sxs-lookup"><span data-stu-id="f2907-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="f2907-120">应用负责正在恢复应用运行时*TouchScreenKeyboard*完成</span><span class="sxs-lookup"><span data-stu-id="f2907-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="f2907-121">已提交的文本现已推出*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f2907-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="f2907-122">可用的键盘视图</span><span class="sxs-lookup"><span data-stu-id="f2907-122">Available keyboard views</span></span>

<span data-ttu-id="f2907-123">提供了六个不同的键盘视图：</span><span class="sxs-lookup"><span data-stu-id="f2907-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="f2907-124">单行文本框</span><span class="sxs-lookup"><span data-stu-id="f2907-124">Single-line textbox</span></span>
* <span data-ttu-id="f2907-125">带标题的单行文本框</span><span class="sxs-lookup"><span data-stu-id="f2907-125">Single-line textbox with title</span></span>
* <span data-ttu-id="f2907-126">多行文本框</span><span class="sxs-lookup"><span data-stu-id="f2907-126">Multi-line textbox</span></span>
* <span data-ttu-id="f2907-127">带标题的多行文本框</span><span class="sxs-lookup"><span data-stu-id="f2907-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="f2907-128">单行密码框</span><span class="sxs-lookup"><span data-stu-id="f2907-128">Single-line password box</span></span>
* <span data-ttu-id="f2907-129">带标题的单行密码框</span><span class="sxs-lookup"><span data-stu-id="f2907-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="f2907-130">如何启用在 Unity 中的系统键盘</span><span class="sxs-lookup"><span data-stu-id="f2907-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="f2907-131">HoloLens 系统键盘才可用于与"UWP 生成类型"设置为"XAML"一起导出的 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f2907-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="f2907-132">有一些的缺点进行时通过"D3D"作为"UWP 生成类型"选择"XAML"。</span><span class="sxs-lookup"><span data-stu-id="f2907-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="f2907-133">如果您不熟悉这些权衡，您可能希望探索[替代方法输入解决方案](#alternative-keyboard-options)到系统键盘。</span><span class="sxs-lookup"><span data-stu-id="f2907-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="f2907-134">打开**文件**菜单，然后选择**生成设置...**</span><span class="sxs-lookup"><span data-stu-id="f2907-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="f2907-135">请确保**平台**设置为**Windows 应用商店**，则**SDK**设置为**通用 10**，并设置**UWP 生成类型**到**XAML**。</span><span class="sxs-lookup"><span data-stu-id="f2907-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="f2907-136">在中**生成设置**对话框中，单击**播放器设置...** 按钮</span><span class="sxs-lookup"><span data-stu-id="f2907-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="f2907-137">选择**设置适用于 Windows 应用商店**选项卡</span><span class="sxs-lookup"><span data-stu-id="f2907-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="f2907-138">展开**其他设置**组</span><span class="sxs-lookup"><span data-stu-id="f2907-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="f2907-139">在中**呈现**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实设备**列表</span><span class="sxs-lookup"><span data-stu-id="f2907-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="f2907-140">请确保**Windows Holographic**虚拟现实 Sdk 的列表中显示</span><span class="sxs-lookup"><span data-stu-id="f2907-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="f2907-141">如果不将生成与 HoloLens 设备标记为受支持的虚拟现实中，项目将导出为 2D XAML 应用。</span><span class="sxs-lookup"><span data-stu-id="f2907-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="f2907-142">Unity 应用程序中使用系统键盘</span><span class="sxs-lookup"><span data-stu-id="f2907-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="f2907-143">声明键盘</span><span class="sxs-lookup"><span data-stu-id="f2907-143">Declare the keyboard</span></span>

<span data-ttu-id="f2907-144">在类中，声明一个变量来存储*TouchScreenKeyboard* ，并返回一个变量来保存键盘的字符串。</span><span class="sxs-lookup"><span data-stu-id="f2907-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="f2907-145">调用键盘</span><span class="sxs-lookup"><span data-stu-id="f2907-145">Invoke the keyboard</span></span>

<span data-ttu-id="f2907-146">请求的键盘输入事件时，调用其中一个具体的所需的输入类型取决于这些函数。</span><span class="sxs-lookup"><span data-stu-id="f2907-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="f2907-147">请注意，textPlaceholder 参数中指定标题。</span><span class="sxs-lookup"><span data-stu-id="f2907-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="f2907-148">检索类型化的内容</span><span class="sxs-lookup"><span data-stu-id="f2907-148">Retrieve typed contents</span></span>

<span data-ttu-id="f2907-149">在更新循环中，检查键盘是否收到新的输入，并将其存储以用于其他地方。</span><span class="sxs-lookup"><span data-stu-id="f2907-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="f2907-150">备选键盘选项</span><span class="sxs-lookup"><span data-stu-id="f2907-150">Alternative keyboard options</span></span>

<span data-ttu-id="f2907-151">我们了解到，切出到二维视图的容量耗尽视图并不理想的方式从用户获取文本输入。</span><span class="sxs-lookup"><span data-stu-id="f2907-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="f2907-152">利用通过 Unity 系统键盘的当前替代项包括：</span><span class="sxs-lookup"><span data-stu-id="f2907-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="f2907-153">使用语音听写输入 (<b>注意：</b>这通常是不在字典中找到的单词容易出错，不适合用于输入密码)</span><span class="sxs-lookup"><span data-stu-id="f2907-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="f2907-154">在应用程序独占视图中创建的工作原理的键盘</span><span class="sxs-lookup"><span data-stu-id="f2907-154">Create a keyboard that works in your applications exclusive view</span></span>
