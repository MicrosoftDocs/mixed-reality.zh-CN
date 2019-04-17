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
# <a name="keyboard-input-in-unity"></a>在 Unity 中的键盘输入

**命名空间：***UnityEngine*<br>
 类型：*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

尽管 HoloLens 支持许多形式的输入包括蓝牙键盘，大多数应用程序不能假定所有用户都都可用的物理键盘。 如果你的应用程序需要文本输入，则应提供某种形式的屏幕键盘上。

Unity 提供了*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类用于接受键盘输入时没有可用的物理键盘。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>在 Unity 中的 HoloLens 系统键盘行为

HoloLens 上, *TouchScreenKeyboard*利用屏幕键盘上的系统。 屏幕键盘上的系统不能覆盖容量耗尽视图顶部，因此，Unity 创建辅助的 2D 的 XAML 视图以显示键盘，然后输入提交后返回到容量耗尽视图。 用户流如下所示：
1. 用户执行的操作，从而导致应用程序代码调用*TouchScreenKeyboard*
    * 应用负责暂停应用程序状态，然后才能调用*TouchScreenKeyboard*
    * 应用程序可能会不断切换回容量耗尽视图之前终止
2. Unity 将切换到 2D 的 XAML 视图，即自动放置在世界
3. 用户输入文本使用系统键盘和提交或取消
4. Unity 切换回容量耗尽视图
    * 应用负责正在恢复应用运行时*TouchScreenKeyboard*完成
5. 已提交的文本现已推出*TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>可用的键盘视图

提供了六个不同的键盘视图：
* 单行文本框
* 带标题的单行文本框
* 多行文本框
* 带标题的多行文本框
* 单行密码框
* 带标题的单行密码框

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>如何启用在 Unity 中的系统键盘

HoloLens 系统键盘才可用于与"UWP 生成类型"设置为"XAML"一起导出的 Unity 应用程序。 有一些的缺点进行时通过"D3D"作为"UWP 生成类型"选择"XAML"。 如果您不熟悉这些权衡，您可能希望探索[替代方法输入解决方案](#alternative-keyboard-options)到系统键盘。
1. 打开**文件**菜单，然后选择**生成设置...**
2. 请确保**平台**设置为**Windows 应用商店**，则**SDK**设置为**通用 10**，并设置**UWP 生成类型**到**XAML**。
3. 在中**生成设置**对话框中，单击**播放器设置...** 按钮
4. 选择**设置适用于 Windows 应用商店**选项卡
5. 展开**其他设置**组
6. 在中**呈现**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实设备**列表
7. 请确保**Windows Holographic**虚拟现实 Sdk 的列表中显示

>[!NOTE]
>如果不将生成与 HoloLens 设备标记为受支持的虚拟现实中，项目将导出为 2D XAML 应用。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Unity 应用程序中使用系统键盘

### <a name="declare-the-keyboard"></a>声明键盘

在类中，声明一个变量来存储*TouchScreenKeyboard* ，并返回一个变量来保存键盘的字符串。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>调用键盘

请求的键盘输入事件时，调用其中一个具体的所需的输入类型取决于这些函数。 请注意，textPlaceholder 参数中指定标题。

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

### <a name="retrieve-typed-contents"></a>检索类型化的内容

在更新循环中，检查键盘是否收到新的输入，并将其存储以用于其他地方。

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

## <a name="alternative-keyboard-options"></a>备选键盘选项

我们了解到，切出到二维视图的容量耗尽视图并不理想的方式从用户获取文本输入。

利用通过 Unity 系统键盘的当前替代项包括：
* 使用语音听写输入 (<b>注意：</b>这通常是不在字典中找到的单词容易出错，不适合用于输入密码)
* 在应用程序独占视图中创建的工作原理的键盘
