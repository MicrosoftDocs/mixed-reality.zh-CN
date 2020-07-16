---
title: Unreal 中的 WinRT
description: Unreal 引擎的空间音频插件概述。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像, 游戏开发
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408215"
---
# <a name="winrt-in-unreal"></a>Unreal 中的 WinRT

## <a name="overview"></a>概述

在 HoloLens 开发过程中，可能需要使用 WinRT 编写功能。 例如，在 HoloLens 应用程序中打开文件对话时，需要 winrt/FileSavePicker 头文件中的。  由于 Unreal 不会以本机方式编译 WinRT 代码，因此您的工作就是生成一个单独的二进制文件，并可由 Unreal 的生成系统使用。 本教程将引导你完成此类方案。

## <a name="objectives"></a>目标
- 创建用于打开 FileSaveDialogue 的通用 Windows DLL
- 将该 DLL 链接到 Unreal 游戏项目
- 使用新 DLL 从 Unreal 蓝图将文件保存在 HoloLens 上

## <a name="getting-started"></a>入门
1. 检查是否已安装所有[必需的工具](unreal-uxt-ch1.md)
2. [创建新的 Unreal 项目](unreal-uxt-ch2.md#creating-a-new-unreal-project)并将其命名为**Consumewinrt**
3. 为 HoloLens 开发启用[所需插件](unreal-uxt-ch2.md#enabling-required-plugins)
4. 部署到设备或仿真程序[的设置](unreal-uxt-ch6.md)

## <a name="creating-a-winrt-dll"></a>创建 WinRT DLL 
1. 打开新的 Visual Studio 项目，并在 Unreal 游戏的**uproject**文件所在的目录中创建一个**DLL （通用 Windows）** 项目。 

![创建 DLL](images/unreal-winrt-img-01.png)

2. 将该项目命名为**HoloLensWinrtDLL** ，并将该位置设置为 Unreal 游戏 uproject 文件的**ThirdParty**子目录。 
    * 选择 **"将解决方案和项目放置在相同的目录中"** ，以简化以后查找路径的情况。 

![配置 DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 新项目编译完成后，您需要分别特别注意名为**HoloLensWinrtDLL**和**HoloLensWinrtDLL**的空白 cpp 和头文件。 标头是在 Unreal 中使用 DLL 的包含文件，而 cpp 包含所导出的任何函数的主体，并且包含 Unreal 不能编译的任何 WinRT 代码。 

3. 添加任何代码之前，需要更新项目属性，以确保所需的 WinRT 代码可以编译： 
    * 右键单击 "HoloLensWinrtDLL" 项目，然后选择 "**属性**"  
    * 将 "**配置**" 下拉列表中的 "**所有配置**" 和 "**平台**" 下拉列表更改为**所有平台**  
    * 在 "**配置属性" 下> C/c + +> 所有选项**：
        * 将**await**添加到**其他选项**，以确保我们可以等待异步任务  
        * 将**c + + 语言标准**更改为**ISO c + + 17 标准（/std： c + + 17）** 以包括任何 WinRT 代码

![配置 DLL](images/unreal-winrt-img-03.png)

你的项目已准备好使用 WinRT 代码更新 DLL 的源，该代码打开文件对话框，并将文件保存到 HoloLens 磁盘。  

## <a name="adding-the-dll-code"></a>添加 DLL 代码
1. 打开**HoloLensWinrtDLL** ，并添加要使用的 Unreal 的 dll 导出函数： 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. 打开**HoloLensWinrtDLL**并添加类将使用的所有标头：  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> 所有 WinRT 代码都存储在**HoloLensWinrtDLL**中，因此 Unreal 不会在引用标头时尝试包含任何 WinRT 代码。 

3. 仍在**HoloLensWinrtDLL**中，为 OpenFileDialogue （）和所有支持的代码添加函数体： 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. 将 SaveGameManager 类添加到**HoloLensWinrtDLL**以处理文件对话框并保存文件： 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. 生成用于**Release > ARM64**的解决方案，以便将 DLL 从 dll 解决方案生成到子目录 ARM64/Release/HoloLensWinrtDLL。 

## <a name="adding-the-winrt-binary-to-unreal"></a>向 Unreal 添加 WinRT 二进制文件 
在 Unreal 中链接和使用 DLL 需要一个 c + + 项目。 如果使用的是蓝图项目，可以通过添加 c + + 类轻松地将其转换为 c + + 项目：  

1. 在 Unreal 编辑器中，打开 " **> 新建 c + + 类的文件 ...** " 并在 DLL 中**创建名为** **WinrtActor**的新执行组件： 

![配置 DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> 现在，已在与 uproject 文件相同的目录中创建了一个解决方案，同时还创建了一个名为 Source/ConsumeWinRT/ConsumerWinRT 的新生成脚本。

2. 打开解决方案，浏览到**游戏/ConsumeWinRT/源/ConsumeWinRT**文件夹，然后打开**ConsumeWinRT.build.cs**：

![配置 DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>链接 DLL
1. 在**ConsumeWinRT.build.cs**中，添加一个属性以查找 DLL （包含 HoloLensWinrtDLL 的目录）的包含路径。 DLL 位于包含路径的子目录中，因此此属性将用作二进制根目录：

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. 在类构造函数中，添加以下代码以更新包含路径、链接新的 lib 并延迟加载，并将 DLL 复制到打包的 appx 位置：

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. 打开**WinrtActor** ，并添加两个函数定义，一个是蓝图可以使用的，另一个是使用 DLL 代码的函数定义： 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. 打开**WinrtActor** ，并在 BeginPlay 中加载 DLL： 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> 必须先加载 DLL，然后才能调用它的任何函数。

### <a name="building-the-game"></a>构建游戏
1. 构建游戏解决方案，启动为游戏项目打开的 Unreal 编辑器： 
    * 在 "**设置参与者**" 选项卡中，搜索新**WinrtActor**并将其拖动到场景中 
    * 打开级别蓝图，以在**WinrtActor**中执行蓝图可调用函数 

![配置 DLL](images/unreal-winrt-img-06.png)

2. 在**World Outliner**中，找到以前拖放到场景中的**WindrtActor** ，并将其拖动到级别蓝图： 

![配置 DLL](images/unreal-winrt-img-07.png)

3. 在级别蓝图中，从 WinrtActor 中拖动输出节点，搜索 "**打开文件" 对话框**，然后从任何用户输入路由节点。  在这种情况下，从语音事件调用 "打开文件" 对话框： 

![配置 DLL](images/unreal-winrt-img-08.png)

4. [为 HoloLens 打包这一游戏](unreal-uxt-ch6.md)，部署它，然后运行。  

当 Unreal 调用 OpenFileDialogue 时，将在 HoloLens 提示符下打开一个文件对话框，提示输入 .txt 文件名。  保存该文件后，请在设备门户中转到 "**文件资源管理器**" 选项卡，查看内容 "Hello WinRT"。 

## <a name="summary"></a>总结 

我们鼓励您在本教程中使用代码，作为在 Unreal 中使用 WinRT 代码的起点。  它允许用户使用与 Windows 相同的文件对话框将文件保存到 HoloLens 磁盘。  按照相同的过程从 HoloLensWinrtDLL 标头中导出任何其他函数并在 Unreal 中使用。  请注意，在后台 MTA 线程中等待任何异步 WinRT 代码的 DLL 代码，这可避免死锁 Unreal 游戏线程。 

## <a name="see-also"></a>另请参阅
* [C + +/WinRT Api](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker 类](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal 第三方库](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
