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
# <a name="winrt-in-unreal"></a><span data-ttu-id="7682e-104">Unreal 中的 WinRT</span><span class="sxs-lookup"><span data-stu-id="7682e-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="7682e-105">概述</span><span class="sxs-lookup"><span data-stu-id="7682e-105">Overview</span></span>

<span data-ttu-id="7682e-106">在 HoloLens 开发过程中，可能需要使用 WinRT 编写功能。</span><span class="sxs-lookup"><span data-stu-id="7682e-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="7682e-107">例如，在 HoloLens 应用程序中打开文件对话时，需要 winrt/FileSavePicker 头文件中的。</span><span class="sxs-lookup"><span data-stu-id="7682e-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="7682e-108">由于 Unreal 不会以本机方式编译 WinRT 代码，因此您的工作就是生成一个单独的二进制文件，并可由 Unreal 的生成系统使用。</span><span class="sxs-lookup"><span data-stu-id="7682e-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="7682e-109">本教程将引导你完成此类方案。</span><span class="sxs-lookup"><span data-stu-id="7682e-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="7682e-110">目标</span><span class="sxs-lookup"><span data-stu-id="7682e-110">Objectives</span></span>
- <span data-ttu-id="7682e-111">创建用于打开 FileSaveDialogue 的通用 Windows DLL</span><span class="sxs-lookup"><span data-stu-id="7682e-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="7682e-112">将该 DLL 链接到 Unreal 游戏项目</span><span class="sxs-lookup"><span data-stu-id="7682e-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="7682e-113">使用新 DLL 从 Unreal 蓝图将文件保存在 HoloLens 上</span><span class="sxs-lookup"><span data-stu-id="7682e-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="7682e-114">入门</span><span class="sxs-lookup"><span data-stu-id="7682e-114">Getting started</span></span>
1. <span data-ttu-id="7682e-115">检查是否已安装所有[必需的工具](unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="7682e-115">Check that you have all [required tools](unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="7682e-116">[创建新的 Unreal 项目](unreal-uxt-ch2.md#creating-a-new-unreal-project)并将其命名为**Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="7682e-116">[Create a new Unreal project](unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="7682e-117">为 HoloLens 开发启用[所需插件](unreal-uxt-ch2.md#enabling-required-plugins)</span><span class="sxs-lookup"><span data-stu-id="7682e-117">Enable the [required plugins](unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="7682e-118">部署到设备或仿真程序[的设置](unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="7682e-118">[Setup for deployment](unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="7682e-119">创建 WinRT DLL</span><span class="sxs-lookup"><span data-stu-id="7682e-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="7682e-120">打开新的 Visual Studio 项目，并在 Unreal 游戏的**uproject**文件所在的目录中创建一个**DLL （通用 Windows）** 项目。</span><span class="sxs-lookup"><span data-stu-id="7682e-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![创建 DLL](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="7682e-122">将该项目命名为**HoloLensWinrtDLL** ，并将该位置设置为 Unreal 游戏 uproject 文件的**ThirdParty**子目录。</span><span class="sxs-lookup"><span data-stu-id="7682e-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="7682e-123">选择 **"将解决方案和项目放置在相同的目录中"** ，以简化以后查找路径的情况。</span><span class="sxs-lookup"><span data-stu-id="7682e-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![配置 DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="7682e-125">新项目编译完成后，您需要分别特别注意名为**HoloLensWinrtDLL**和**HoloLensWinrtDLL**的空白 cpp 和头文件。</span><span class="sxs-lookup"><span data-stu-id="7682e-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="7682e-126">标头是在 Unreal 中使用 DLL 的包含文件，而 cpp 包含所导出的任何函数的主体，并且包含 Unreal 不能编译的任何 WinRT 代码。</span><span class="sxs-lookup"><span data-stu-id="7682e-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="7682e-127">添加任何代码之前，需要更新项目属性，以确保所需的 WinRT 代码可以编译：</span><span class="sxs-lookup"><span data-stu-id="7682e-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="7682e-128">右键单击 "HoloLensWinrtDLL" 项目，然后选择 "**属性**"</span><span class="sxs-lookup"><span data-stu-id="7682e-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="7682e-129">将 "**配置**" 下拉列表中的 "**所有配置**" 和 "**平台**" 下拉列表更改为**所有平台**</span><span class="sxs-lookup"><span data-stu-id="7682e-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="7682e-130">在 "**配置属性" 下> C/c + +> 所有选项**：</span><span class="sxs-lookup"><span data-stu-id="7682e-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="7682e-131">将**await**添加到**其他选项**，以确保我们可以等待异步任务</span><span class="sxs-lookup"><span data-stu-id="7682e-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="7682e-132">将**c + + 语言标准**更改为**ISO c + + 17 标准（/std： c + + 17）** 以包括任何 WinRT 代码</span><span class="sxs-lookup"><span data-stu-id="7682e-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![配置 DLL](images/unreal-winrt-img-03.png)

<span data-ttu-id="7682e-134">你的项目已准备好使用 WinRT 代码更新 DLL 的源，该代码打开文件对话框，并将文件保存到 HoloLens 磁盘。</span><span class="sxs-lookup"><span data-stu-id="7682e-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="7682e-135">添加 DLL 代码</span><span class="sxs-lookup"><span data-stu-id="7682e-135">Adding the DLL code</span></span>
1. <span data-ttu-id="7682e-136">打开**HoloLensWinrtDLL** ，并添加要使用的 Unreal 的 dll 导出函数：</span><span class="sxs-lookup"><span data-stu-id="7682e-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="7682e-137">打开**HoloLensWinrtDLL**并添加类将使用的所有标头：</span><span class="sxs-lookup"><span data-stu-id="7682e-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="7682e-138">所有 WinRT 代码都存储在**HoloLensWinrtDLL**中，因此 Unreal 不会在引用标头时尝试包含任何 WinRT 代码。</span><span class="sxs-lookup"><span data-stu-id="7682e-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="7682e-139">仍在**HoloLensWinrtDLL**中，为 OpenFileDialogue （）和所有支持的代码添加函数体：</span><span class="sxs-lookup"><span data-stu-id="7682e-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="7682e-140">将 SaveGameManager 类添加到**HoloLensWinrtDLL**以处理文件对话框并保存文件：</span><span class="sxs-lookup"><span data-stu-id="7682e-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="7682e-141">生成用于**Release > ARM64**的解决方案，以便将 DLL 从 dll 解决方案生成到子目录 ARM64/Release/HoloLensWinrtDLL。</span><span class="sxs-lookup"><span data-stu-id="7682e-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="7682e-142">向 Unreal 添加 WinRT 二进制文件</span><span class="sxs-lookup"><span data-stu-id="7682e-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="7682e-143">在 Unreal 中链接和使用 DLL 需要一个 c + + 项目。</span><span class="sxs-lookup"><span data-stu-id="7682e-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="7682e-144">如果使用的是蓝图项目，可以通过添加 c + + 类轻松地将其转换为 c + + 项目：</span><span class="sxs-lookup"><span data-stu-id="7682e-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="7682e-145">在 Unreal 编辑器中，打开 " **> 新建 c + + 类的文件 ...** "</span><span class="sxs-lookup"><span data-stu-id="7682e-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="7682e-146">并在 DLL 中**创建名为** **WinrtActor**的新执行组件：</span><span class="sxs-lookup"><span data-stu-id="7682e-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![配置 DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="7682e-148">现在，已在与 uproject 文件相同的目录中创建了一个解决方案，同时还创建了一个名为 Source/ConsumeWinRT/ConsumerWinRT 的新生成脚本。</span><span class="sxs-lookup"><span data-stu-id="7682e-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumerWinRT.Build.cs.</span></span>

2. <span data-ttu-id="7682e-149">打开解决方案，浏览到**游戏/ConsumeWinRT/源/ConsumeWinRT**文件夹，然后打开**ConsumeWinRT.build.cs**：</span><span class="sxs-lookup"><span data-stu-id="7682e-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![配置 DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="7682e-151">链接 DLL</span><span class="sxs-lookup"><span data-stu-id="7682e-151">Linking the DLL</span></span>
1. <span data-ttu-id="7682e-152">在**ConsumeWinRT.build.cs**中，添加一个属性以查找 DLL （包含 HoloLensWinrtDLL 的目录）的包含路径。</span><span class="sxs-lookup"><span data-stu-id="7682e-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="7682e-153">DLL 位于包含路径的子目录中，因此此属性将用作二进制根目录：</span><span class="sxs-lookup"><span data-stu-id="7682e-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="7682e-154">在类构造函数中，添加以下代码以更新包含路径、链接新的 lib 并延迟加载，并将 DLL 复制到打包的 appx 位置：</span><span class="sxs-lookup"><span data-stu-id="7682e-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="7682e-155">打开**WinrtActor** ，并添加两个函数定义，一个是蓝图可以使用的，另一个是使用 DLL 代码的函数定义：</span><span class="sxs-lookup"><span data-stu-id="7682e-155">Open **WinrtActor.h** and add two function definitions, one that a blueprint can use and another that uses the DLL code:</span></span> 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. <span data-ttu-id="7682e-156">打开**WinrtActor** ，并在 BeginPlay 中加载 DLL：</span><span class="sxs-lookup"><span data-stu-id="7682e-156">Open **WinrtActor.cpp** and load the DLL in BeginPlay:</span></span> 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="7682e-157">必须先加载 DLL，然后才能调用它的任何函数。</span><span class="sxs-lookup"><span data-stu-id="7682e-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="7682e-158">构建游戏</span><span class="sxs-lookup"><span data-stu-id="7682e-158">Building the game</span></span>
1. <span data-ttu-id="7682e-159">构建游戏解决方案，启动为游戏项目打开的 Unreal 编辑器：</span><span class="sxs-lookup"><span data-stu-id="7682e-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="7682e-160">在 "**设置参与者**" 选项卡中，搜索新**WinrtActor**并将其拖动到场景中</span><span class="sxs-lookup"><span data-stu-id="7682e-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="7682e-161">打开级别蓝图，以在**WinrtActor**中执行蓝图可调用函数</span><span class="sxs-lookup"><span data-stu-id="7682e-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![配置 DLL](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="7682e-163">在**World Outliner**中，找到以前拖放到场景中的**WindrtActor** ，并将其拖动到级别蓝图：</span><span class="sxs-lookup"><span data-stu-id="7682e-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![配置 DLL](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="7682e-165">在级别蓝图中，从 WinrtActor 中拖动输出节点，搜索 "**打开文件" 对话框**，然后从任何用户输入路由节点。</span><span class="sxs-lookup"><span data-stu-id="7682e-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="7682e-166">在这种情况下，从语音事件调用 "打开文件" 对话框：</span><span class="sxs-lookup"><span data-stu-id="7682e-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![配置 DLL](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="7682e-168">[为 HoloLens 打包这一游戏](unreal-uxt-ch6.md)，部署它，然后运行。</span><span class="sxs-lookup"><span data-stu-id="7682e-168">[Package this game for HoloLens](unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="7682e-169">当 Unreal 调用 OpenFileDialogue 时，将在 HoloLens 提示符下打开一个文件对话框，提示输入 .txt 文件名。</span><span class="sxs-lookup"><span data-stu-id="7682e-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="7682e-170">保存该文件后，请在设备门户中转到 "**文件资源管理器**" 选项卡，查看内容 "Hello WinRT"。</span><span class="sxs-lookup"><span data-stu-id="7682e-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="7682e-171">总结</span><span class="sxs-lookup"><span data-stu-id="7682e-171">Summary</span></span> 

<span data-ttu-id="7682e-172">我们鼓励您在本教程中使用代码，作为在 Unreal 中使用 WinRT 代码的起点。</span><span class="sxs-lookup"><span data-stu-id="7682e-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="7682e-173">它允许用户使用与 Windows 相同的文件对话框将文件保存到 HoloLens 磁盘。</span><span class="sxs-lookup"><span data-stu-id="7682e-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="7682e-174">按照相同的过程从 HoloLensWinrtDLL 标头中导出任何其他函数并在 Unreal 中使用。</span><span class="sxs-lookup"><span data-stu-id="7682e-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="7682e-175">请注意，在后台 MTA 线程中等待任何异步 WinRT 代码的 DLL 代码，这可避免死锁 Unreal 游戏线程。</span><span class="sxs-lookup"><span data-stu-id="7682e-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="see-also"></a><span data-ttu-id="7682e-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7682e-176">See also</span></span>
* [<span data-ttu-id="7682e-177">C + +/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="7682e-177">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="7682e-178">FileSavePicker 类</span><span class="sxs-lookup"><span data-stu-id="7682e-178">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="7682e-179">Unreal 第三方库</span><span class="sxs-lookup"><span data-stu-id="7682e-179">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
