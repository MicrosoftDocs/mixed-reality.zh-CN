---
title: Unity 中的键盘输入
description: Unity 提供了 TouchScreenKeyboard 类, 可用于在没有可用物理键盘时接受键盘输入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 键盘、input、unity、touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515738"
---
# <a name="keyboard-input-in-unity"></a>Unity 中的键盘输入

**命名空间：**  *UnityEngine*<br>
 类型： *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

虽然 HoloLens 支持多种形式的输入, 包括蓝牙键盘, 但大多数应用程序都无法假定所有用户都有可用的物理键盘。 如果你的应用程序需要文本输入, 则应该提供某种形式的屏幕键盘。

Unity 提供了 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类用于接受键盘输入时没有可用的物理键盘。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity 中的 HoloLens 系统键盘行为

在 HoloLens 上, *TouchScreenKeyboard*利用系统的屏幕键盘。 系统的屏幕键盘无法叠加到容量耗尽视图之上, 因此 Unity 必须创建辅助二维 XAML 视图, 以显示键盘, 然后在提交输入后返回到容量耗尽视图。 用户流如下所示:
1. 用户执行导致应用程序代码调用*TouchScreenKeyboard*的操作
    * 在调用*TouchScreenKeyboard*之前, 应用负责暂停应用状态
    * 应用可能会终止, 然后再切换回容量耗尽视图
2. Unity 切换到在世界上自动放置的 2D XAML 视图
3. 用户使用系统键盘输入文本并提交或取消
4. Unity 切换回容量耗尽视图
    * 应用负责在*TouchScreenKeyboard*完成后恢复应用程序状态
5. 提交的文本在*TouchScreenKeyboard*中提供

### <a name="available-keyboard-views"></a>可用的键盘视图

有六种不同的键盘视图可用:
* 单行文本框
* 带有标题的单行文本框
* 多行文本框
* 带有标题的多行文本框
* 单行密码框
* 带有标题的单行密码框

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>如何在 Unity 中启用系统键盘

HoloLens 系统键盘仅适用于使用 "UWP 版本类型" 设置为 "XAML" 导出的 Unity 应用程序。 选择 "XAML" 作为 "UWP 生成类型" over "D3D" 时, 会产生一些折衷。 如果你不熟悉这些折衷方案, 你可能希望浏览到系统键盘的[备用输入解决方案](#alternative-keyboard-options)。
1. 打开 "**文件**" 菜单, 然后选择 "**生成设置 ...** "
2. 确保将**平台**设置为**Windows 应用商店**, 将**SDK**设置为**通用 10**, 并将**UWP 生成类型**设置为**XAML**。
3. 在 "**生成设置**" 对话框中, 单击 "**播放机设置 ...** " 按钮
4. 选择 " **Windows 应用商店设置**" 选项卡
5. 展开 "**其他设置**" 组
6. 在 "**呈现**" 部分中, 选中 "**支持虚拟现实**" 复选框, 以添加新的**虚拟现实设备**列表
7. 确保**Windows 全息**出现在虚拟现实 sdk 列表中

>[!NOTE]
>如果你没有将生成标记为在 HoloLens 设备上受支持的虚拟现实, 则项目将导出为 2D XAML 应用。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在 Unity 应用中使用系统键盘

### <a name="declare-the-keyboard"></a>声明键盘

在类中, 声明一个用于存储*TouchScreenKeyboard*的变量, 并声明一个用于保存键盘返回的字符串的变量。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>调用键盘

当请求键盘输入时发生事件时, 请根据所需的输入类型调用其中一个函数。 请注意, 在 textPlaceholder 参数中指定标题。

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

### <a name="retrieve-typed-contents"></a>检索类型化内容

在更新循环中, 检查键盘是否收到新输入, 并将其存储起来供其他地方使用。

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

## <a name="alternative-keyboard-options"></a>备用键盘选项

我们了解, 从容量耗尽视图切换到2D 视图并不是获取用户文本输入的理想方法。

通过 Unity 使用系统键盘的当前替代方法包括:
* 使用语音听写进行输入 (<b>请注意:</b>这通常容易出错, 无法用于字典中找不到的字词, 也不适合密码输入)
* 在应用程序独占视图中创建工作键盘
