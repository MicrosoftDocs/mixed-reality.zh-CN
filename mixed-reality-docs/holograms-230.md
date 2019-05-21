---
title: MR 空间 230-空间映射
description: 遵循此编码使用 Unity、 Visual Studio 和 HoloLens 学习空间映射概念的详细信息的演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程、 空间映射，图面上重新构造，网格
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993562"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR 空间 230:空间映射

[空间映射](spatial-mapping.md)将合并的实际和虚拟世界一起教授全息有关的环境。 在 MR 空间 230 (项目 Planetarium) 中，我们将了解如何：

* 扫描的环境和传输数据从 HoloLens 到开发计算机。
* 了解着色器并了解如何使用它们用于可视化你的空间。
* 分解到使用网格处理简单的平面空间网格。
* 我们在中学到的位置技术超越[MR 基础知识 101](holograms-101.md)，并提供有关在环境中的一张全息图可以放置位置的反馈。
* 探索封闭的效果，因此真实世界物体后面你全息图时，您仍然可以看到与 x 射线视力 ！

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 空间 230:空间映射</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。
* 一些基本C#编程功能。
* 您应当已完成[MR 基础知识 101](holograms-101.md)。
* HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
  * 如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。
  * 如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。
  * 如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。
* 取消存档到您的桌面或其他轻松地访问位置的文件。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)。

### <a name="notes"></a>说明

* Visual Studio 需要禁用中的"启用仅我的代码"(*未选中*) 在工具 > 选项 > 以命中断点在代码中的调试。

## <a name="unity-setup"></a>Unity 安装程序

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* 启动**Unity**。
* 选择**新建**创建新项目。
* 将项目命名**Planetarium**。
* 确认**3D**选择设置。
* 单击**创建项目**。
* 一旦启动 Unity 时，请转到**编辑 > 项目设置 > 播放机**。
* 在中**Inspector**面板中，找到并选择绿色**Windows 应用商店**图标。
* 展开**其他设置**。
* 在中**呈现**部分中，选择**虚拟现实支持**选项。
* 确认**Windows Holographic**出现在列表中**虚拟现实 Sdk**。 如果没有，请选择 **+** 按钮在列表的底部，然后选择**Windows Holographic**。
* 展开**发布设置**。
* 在中**功能**部分中，检查以下设置：
    * InternetClientServer
    * PrivateNetworkClientServer
    * 麦克风
    * SpatialPerception
* 转到**编辑 > 项目设置 > 质量**
* 在中**Inspector**面板，在 Windows 应用商店图标，然后选择下的默认行的黑色下拉箭头并将默认设置更改为**非常低**。
* 转到**资产 > 导入包 > 自定义包**。
* 导航到 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting**文件夹。
* 单击**Planetarium.unitypackage**。
* 单击“打开” 。
* **导入 Unity 程序包**应显示窗口，单击**导入**按钮。
* 等待导入的所有资产，我们将需要完成此项目的 Unity。
* 在中**层次结构**面板中，删除**Main Camera**。
* 在中**项目**面板中， **HoloToolkit SpatialMapping 230\Utilities\Prefabs**文件夹中，找到**Main Camera**对象。
* 拖放到**Main Camera**到 prefab**层次结构**面板。
* 在中**层次结构**面板中，删除**定向光**对象。
* 在中**项目**面板中，**全息**文件夹中，找到**游标**对象。
* 拖放**游标**到 prefab**层次结构**。
* 在中**层次结构**面板中，选择**光标**对象。
* 在中**Inspector**面板中，单击**层**下拉列表中，选择**编辑层...**.
* 名称**用户层 31**作为"**SpatialMapping**"。
* 保存新的场景：**文件 > 另存为场景...**
* 单击**新文件夹**，然后将文件夹**场景**。
* 将文件"**Planetarium**"并将其保存在**场景**文件夹。

## <a name="chapter-1---scanning"></a>第 1 章-扫描

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**目标**
* 了解有关 SurfaceObserver 和其设置影响如何体验和性能。
* 创建聊天室扫描体验，以收集你的聊天室的网格。

**说明**
* 在中**项目**面板**HoloToolkit SpatialMapping 230\SpatialMapping\Prefabs**文件夹中，找到**SpatialMapping**预设。
* 拖放**SpatialMapping**到 prefab**层次结构**面板。

**生成和部署 （第 1 部分）**
* 在 Unity 中，选择**文件 > 生成设置**。
* 单击**添加打开场景**以添加**Planetarium**到生成的场景。
* 选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。
* 设置**SDK**到**通用 10**并**UWP 生成类型**到**D3D**。
* 检查**UnityC#项目**。
* 单击“生成” 。
* 创建**新文件夹**名为"应用"。
* 单击一下**应用**文件夹。
* 按**选择文件夹**按钮。
* 当完成 Unity 构建，将出现一个文件资源管理器窗口。
* 双击**应用**文件夹将其打开。
* 双击**Planetarium.sln**加载 Visual Studio 中的项目。
* 在 Visual Studio 中，使用顶部的工具栏更改为配置**版本**。
* 更改到平台**x86**。
* 单击本地计算机，右侧的下拉箭头，然后选择**远程计算机**。
* 输入[设备的 IP 地址](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network)字段中的地址和身份验证模式更改为**通用 （未加密的协议）**。
* 单击**调试-> 启动不调试**或按**Ctrl + F5**。
* 观看**输出**面板在 Visual Studio 中生成和部署状态。
* 您的应用程序已部署后，聊天室中四处走动。 你将看到由黑色或白色透明框架网格覆盖的周围图面。
* 扫描周围的环境。 请务必查看墙面、 的上限和地面。

**生成和部署 （第 2 部分）**

现在我们来探讨一下如何空间映射可能会影响性能。
* 在 Unity 中，选择**窗口 > Profiler**。
* 单击**添加 Profiler > GPU**。
* 单击**Active Profiler > <Enter IP>** 。
* 输入**IP 地址**你 HoloLens。
* 单击“连接”。
* 观察到 GPU 呈现一个帧所需的毫秒的数。
* 停止从设备上运行应用程序。
* 返回到 Visual Studio 并打开**SpatialMappingObserver.cs**。 将程序集 c# (通用 Windows) 项目的 HoloToolkit\SpatialMapping 文件夹中找到它。
* 查找**Awake()** 函数，并添加以下代码行：**TrianglesPerCubicMeter = 1200;**
* 重新部署到设备，在该项目，然后**重新连接探查器**。 观察中要呈现一个帧的毫秒数的更改。
* 停止从设备上运行应用程序。

**在 Unity 中加载和保存**

最后，让我们保存我们的空间网格，并将其加载到 Unity。
* 返回到 Visual Studio 并删除**TrianglesPerCubicMeter**中添加行**Awake()** 函数在上一节。
* 重新部署到设备项目。 我们现在应该运行带有**500**每三次方计量的三角形。
* 打开浏览器并导航到你 HoloLens IPAddress 中输入**Windows Device Portal**。
* 选择**三维视图**左侧面板中的选项。
* 下**图面重建**选择**更新**按钮。
* 观看显示窗口中显示已在 HoloLens 扫描的区域。
* 若要保存房间扫描，请按**保存**按钮。
* 打开你**下载**文件夹，以便找到保存的房间模型**SRMesh.obj**。
* 复制**SRMesh.obj**到**资产**Unity 项目的文件夹。
* 在 Unity 中，选择**SpatialMapping**对象中**层次结构**面板。
* 找到**对象图面观察者 （脚本）** 组件。
* 单击右侧的圆形**聊天室模型**属性。
* 找到并选择**SRMesh**对象，然后关闭窗口。
* 确认**聊天室模型**属性中的**Inspector**面板现在设置为**SRMesh**。
* 按**播放**按钮以输入 Unity 的预览模式。
* SpatialMapping 组件将从已保存的房间模型加载网格，因此可以在 Unity 中使用它们。
* 切换到**场景**视图，以查看所有聊天室模型显示与线框着色器。
* 按**播放**按钮再次退出预览模式。

**注意：** 下次在 Unity 中，输入预览模式下它将按默认加载已保存的空间网格。

## <a name="chapter-2---visualization"></a>第 2 章-可视化效果

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**目标**
* 了解着色器的基础知识。
* 可视化周围的环境。

**说明**
* 在 Unity 中的**层次结构**面板中，选择**SpatialMapping**对象。
* 在中**Inspector**面板中，找到**空间映射管理器 （脚本）** 组件。
* 单击右侧的圆形**面材料**属性。
* 找到并选择**BlueLinesOnWalls**材料并关闭窗口。
* 在中**项目**面板**着色器**文件夹中，双击**BlueLinesOnWalls**在 Visual Studio 中打开着色器。
* 这是一个简单的像素 （顶点片段） 着色器，完成以下任务：
    1. 将顶点位置转换为世界空间中。
    2. 检查顶点的普通以确定是否垂直像素。
    3. 设置用于呈现像素的颜色。

**生成和部署**
* 返回到 Unity 并按**播放**输入预览模式。
* 蓝线将空间网格 （它会自动加载已保存扫描数据） 的所有垂直图面上呈现。
* 切换到**场景**选项卡上调整聊天室的视图并查看整个空间网格在 Unity 中的显示方式。
* 在中**项目**面板中，找到**材料**文件夹，然后选择**BlueLinesOnWalls**材料。
* 修改某些属性，并查看所做的更改在 Unity 编辑器中的显示方式。
    * 在中**Inspector**面板中，调整**LineScale**值，使各行显示较粗或变小。
    * 在中**Inspector**面板中，调整**LinesPerMeter**值可以更改每面墙上显示的行数。
* 单击**播放**再次以退出预览模式。
* 生成和部署到 HoloLens 并观察着色器呈现实际的图面上的显示方式。

Unity 能够很好的预览材料，但始终签出呈现设备中的一个好主意。

## <a name="chapter-3---processing"></a>第 3 章 — 处理

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**目标**
* 了解技术来处理应用程序中使用的空间映射数据。
* 分析空间映射的数据，查找平面并删除三角形。
* 使用平面全息图放置虚拟机。

**说明**
* 在 Unity 中的**项目**面板中，**全息**文件夹中，找到**SpatialProcessing**对象。
* 拖放**SpatialProcessing**对象插入**层次结构**面板。

SpatialProcessing 预设可包括用于处理空间映射数据的组件。 **SurfaceMeshesToPlanes.cs**将查找并生成基于空间映射数据平面。 我们将在我们的应用程序中使用平面来表示墙、 楼层和上限。 此预设还包括**RemoveSurfaceVertices.cs**这可以从空间映射网格中删除顶点。 这可以用于在网格中创建的孔或删除过多 （因为可改为使用平面） 不再需要的三角形。
* 在 Unity 中的**项目**面板中，**全息**文件夹中，找到**SpaceCollection**对象。
* 拖放到**SpaceCollection**对象插入**层次结构**面板。
* 在中**层次结构**面板中，选择**SpatialProcessing**对象。
* 在中**Inspector**面板中，找到**播放空间管理器 （脚本）** 组件。
* 双击**PlaySpaceManager.cs**若要在 Visual Studio 中打开它。

PlaySpaceManager.cs 包含特定于应用程序的代码。 我们将功能添加到此脚本以启用以下行为：
1. 停止收集数据空间映射后超过扫描时间限制 （10 秒）。
2. 处理空间映射数据：
    1. 使用 SurfaceMeshesToPlanes 创建更简单的表示形式世界平面 （墙壁、 楼层、 的上限，等等）。
    2. 使用 RemoveSurfaceVertices 删除平面边界之内的图面上的三角形。
3. 在世界中生成的全息集合并将其放置在靠近用户的墙上插座和 floor 平面上。

完成编码练习中 PlaySpaceManager.cs，标记为或将该脚本完成的解决方案替换为从下面：

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**生成和部署**
* 部署到 HoloLens 之前，按**播放**Unity 进入播放模式中的按钮。
* 从文件加载的空间网格后，等待 10 秒之前空间映射网格上开始进行处理。
* 处理完成后，将显示平面表示 floor、 墙、 ceiling、 等等。
* 毕竟平面的发现，你应看到太阳系 floor 附近照相机的表上显示。
* 两个海报应该过显示附近照相机墙上。 切换到**场景**选项卡上，如果你不能看到它们在**游戏**模式。
* 按**播放**按钮再次退出 play 模式。
* 生成并部署到 HoloLens，像往常一样。
* 等待扫描和要完成的空间映射数据的处理。
* 一旦您看到平面的尝试在您的世界中查找太阳系和海报。

## <a name="chapter-4---placement"></a>第 4 章-放置

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**目标**
* 确定是否一张全息图将显示在图面。
* 当一张全息图可以/无法放入图面上时向用户提供反馈。

**说明**
* 在 Unity 中的**层次结构**面板中，选择**SpatialProcessing**对象。
* 在中**Inspector**面板中，找到**平面到图面网格 （脚本）** 组件。
* 更改**绘制平面**属性设置为**Nothing**以清除选定内容。
* 更改**绘制平面**属性设置为**墙**，以便将呈现仅墙平面。
* 在中**项目**面板中，**脚本**文件夹中，双击**Placeable.cs**若要在 Visual Studio 中打开它。

**Placeable**脚本已经连接到平面查找完成后创建的海报和投影框。 我们需要做的就是取消注释一些代码，以及此脚本将实现以下目标：
1. 确定是否一张全息图将显示在面来从中心和边界的多维数据集的四个角光线投射的细节。
2. 检查曲面法线以确定它是平滑的 hologram 设有刷新。
3. 呈现边界的多维数据集，围绕全息图放置时显示其实际大小。
4. 转换卷影下/隐藏全息图以显示其中它将要被放置在基底/墙上插座上。
5. 如果不能放置在图面上或绿色全息图，如果它能够为红色，呈现阴影。
6. 重定向的全息图，它具有与关联的图面上的类型 （垂直或水平） 与对齐。
7. 顺利地将全息图放在选定的面，以避免跳转或对齐行为。

取消注释下面，编码的演练中的所有代码或使用此已完成的解决方案中**Placeable.cs**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**生成和部署**
* 与前面一样，生成项目，并将部署到 HoloLens。
* 等待扫描和要完成的空间映射数据的处理。
* 当您看到的 solar system 时，注视在下面的投影文本框中，并执行选择手势以将其四处移动。 投影框处于选中状态，边界的多维数据集将是围绕投影框可见。
* 移动头看在聊天室中的其他位置。 投影框应遵循你的视线移动。 当投影框下方的阴影变为红色时，不能在该图面上放置全息图。 当投影框下方的阴影将变为绿色时，您可以通过执行另一个选择手势放置全息图。
* 查找并选择一个 wall，以将其移到新位置上的 holographic 海报。 请注意，不能将此海报放上下限或上限，并且它保持正确定向到每面墙因为四处移动。

## <a name="chapter-5---occlusion"></a>第 5 章-封闭

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**目标**
* 确定一张全息图封闭空间映射网格的像素。
* 应用不同的阻挡物技术来实现一个有趣的效果。

**说明**

首先，我们将允许其他全息遮蔽而无需 occluding 现实世界空间映射网格：
* 在中**层次结构**面板中，选择**SpatialProcessing**对象。
* 在中**Inspector**面板中，找到**播放空间管理器 （脚本）** 组件。
* 单击右侧的圆形**辅助材料**属性。
* 找到并选择**封闭**材料并关闭窗口。

接下来，我们要将特殊行为添加到地球，以使其具有蓝色突出显示时它将成为封闭的 （如周日），另一个全息图或空间映射网格：
* 在中**项目**面板**全息**文件夹中，展开**SolarSystem**对象。
* 单击**地球**。
* 在中**Inspector**面板中，查找地球的材料 （底部组件）。
* 在中**着色器下拉列表**，更改到着色器**自定义 > OcclusionRim**。 只要它封闭的像素由另一个对象，这将致使地球周围的蓝色突出显示。

最后，我们将启用我们太阳系中行星 x 射线视觉效果。 我们将需要编辑**PlanetOcclusion.cs** （Scripts\SolarSystem 文件夹中找到） 以实现以下：
1. 确定地球封闭 SpatialMapping 层 （空间网格和平面） 的像素。
2. 只要它封闭的像素由 SpatialMapping 层显示全球线框表示形式。
3. 它不阻止由 SpatialMapping 层时隐藏全球线框表示形式。

请遵循 PlanetOcclusion.cs 中的编码练习，或使用以下解决方案：

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**生成和部署**
* 生成和部署应用程序到 HoloLens，像往常一样。
* 等待扫描和完整的空间映射数据的处理 （应能看到显示在墙上的蓝线）。
* 查找和选择太阳系的投影框，然后设置框旁边墙或落后一个计数器。
* 通过隐藏图面，使其在海报或投影框对等后，可以查看基本的阻挡物。
* 查找地球，只要去往另一个全息图或面后面应为蓝色突出显示效果。
* 观看行星移动墙上或其他表面的空间中的后面。 现在已创建 x 射线视力，并可以看到其线框主干 ！

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**MR 空间 230:空间映射**。
* 您知道如何扫描到 Unity 环境和负载空间映射数据。
* 了解着色器和如何材料可用于重新实现世界可视化效果基础的知识。
* 你已了解的新处理技术，用于查找平面和从网格中删除三角形。
* 您就能够移动并将全息放是很有意义的图面上。
* 您遇到不同的阻挡物技术，利用 x 射线视力的强大功能 ！
