---
title: 坐标系
description: 空间坐标系统用于构建固定、办公室、房间规模和世界规模的混合现实体验。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 坐标系统，空间坐标系统，仅限方向，固定规模，大小，房间，房间，世界规模，360度，固定，房间，房间，世界，缩放，位置，方向，固定，附加，舞台，锚点，空间锚，世界锁定，世界锁定，正文锁定，正文锁定，边界，持久性，共享，跟踪丢失，云空间锚
ms.openlocfilehash: 228f46f1962c39012571234da47ccec07aa67118
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375634"
---
# <a name="coordinate-systems"></a>坐标系

就其核心而言，混合现实应用在世界上放置[全息影像](hologram.md)，看起来像真实的对象。 这涉及到在世界上准确定位和定位那些对用户有意义的全息影像，无论是世界空间还是您创建的虚拟领域。 当对全息影像的位置和方向或任何其他几何（如看光或手[的位置](gaze-and-commit.md)） [hand positions](hands-and-tools.md)的推理时，Windows 将提供各种真实的坐标系统，在这些系统中可以表示几何（称为**空间坐标系统**）。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/TneGSeqVAXQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>具有</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">固定的引用框架</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">附加引用框架</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">阶段引用框架</a></td>
        <td>尚不支持</td>
        <td>尚不支持</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#spatial-anchors">空间定位点</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="spatial-mapping.md">空间映射</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td><a href="scene-understanding.md">场景理解</a></td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>混合现实体验规模

混合现实应用可设计为范围广泛的用户体验，从仅需要耳机方向的360视频查看器到完整的全球规模应用和游戏（需要空间映射和空间锚点）：
<br>

| 体验规模 | 要求 | 示例体验 | 
|----------|----------|----------|
|  **仅限方向** |  **耳机方向**（重力对齐） |  360°视频查看器 | 
|  **固定规模** |  以上，加上**耳机位置**相对于零的位置 |  赛车游戏或空间模拟器 | 
|  **大规模** |  以上，以及**阶段楼层原点** |  在其中施加并减淡的动作游戏  | 
|  **会议室-规模** |  上方和**阶段边界多边形** |  拼图游戏，其中演练了测验题 | 
|  **全球规模** |  **空间锚点**（通常为[空间映射](spatial-mapping.md)） |  具有敌人的游戏，如[RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

这种体验可扩展后跟 "嵌套娃娃" 模型。 此处适用于 Windows Mixed Reality 的关键设计原则是：给定耳机支持为目标体验规模和所有较低刻度构建的应用：
<br>

| 6DOF 跟踪 | 已定义楼层 | 360°跟踪 | 定义的边界 | 空间定位点 | 最大体验 | 
|----------|----------|----------|----------|----------|----------|
|  是 |  - |  - |  - |  - |  **仅限方向** | 
|  **是** |  是 |  - |  - |  - |  **固定** | 
|  **是** |  **是** |  是 |  - |  - |  **继续** | 
|  **是** |  **是** |  **是** |  是 |  - |  **360°** | 
|  **是** |  **是** |  **是** |  **是** |  是 |  **留下** | 
|  **是** |  **是** |  **是** |  **是** |  **是** |  **World** | 

请注意，在 HoloLens 上尚不支持参考阶段。 在 HoloLens 上，会议室规模的应用目前需要使用[空间映射](spatial-mapping.md)或[场景了解](scene-understanding.md)来查找用户的地面和墙。

## <a name="spatial-coordinate-systems"></a>空间坐标系统

所有3D 图形应用程序都使用[笛卡尔坐标系统](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems)来表示它们所呈现的虚拟世界中的对象的位置和方向。 此类坐标系统建立了三个垂直轴，沿该轴放置对象： X、Y 和 Z 轴。

在[混合现实](mixed-reality.md)中，你的应用程序将考虑虚拟和物理坐标系的原因。 Windows 调用在物理环境中具有实际意义的坐标系统，即**空间坐标系统**。

空间坐标系统以米为单位表示坐标值。 这意味着，当对象在混合现实中呈现时，X、Y 或 Z 轴上相隔2个单位的每个对象将彼此分开显示2米。 这使你可以轻松地在真实规模上呈现对象和环境。

通常，笛卡尔坐标系统可以是右手或左手。 Windows 上的空间坐标系统始终是右手的，这意味着正 X 轴向右，Y 轴上点向上（与重力对齐），正 Z 轴指向你。

在这两种坐标系统中，正 X 轴向右，Y 轴向上点向右。 不同之处在于 Z 轴正向你或向外的方向。 您可以通过在正 X 方向上向左或向右箭头，然后将其运行到 Y Y 方向，来记住 Z 轴的正方向。 你的拇指点向下或远离你的方向是该坐标系统的正 Z 轴指向的方向。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>构建仅限方向或固定规模的体验

全息[呈现](rendering.md)的关键是在用户四处移动时更改应用程序的全息影像的视图，以匹配其预测的头运动。 您可以使用**固定的参考框架**，构建与用户头位置和打印头方向发生变化的**固定规模体验**。

某些内容必须忽略头位置更新，始终固定在选择的标题上，并在任何时间与用户之间保持固定。 主要示例是360度的视频：由于视频是从单个固定透视中捕获的，因此它会破坏视图位置相对于内容的移动效果，即使视图方向必须随着用户的视觉位置而更改。 您可以使用**附加的参考框架**构建这种**仅限方向的体验**。

### <a name="stationary-frame-of-reference"></a>固定的引用框架

固定框架提供的坐标系统的工作方式是使对象附近的对象位置尽可能稳定，同时遵从用户头位置中的更改。

对于在游戏引擎（如[Unity](https://unity3d.com/)）中大规模体验，固定框架是指定义引擎的 "世界原点"。 位于特定世界坐标位置的对象使用固定的引用框架来定义它们在实际中使用相同坐标的位置。 即使是在用户浏览时保留在世界各地的内容也称为**全球锁定**的内容。

通常，应用程序会在启动时创建一个固定的固定框架，并在应用程序的整个生存期内使用其坐标系统。 作为 Unity 中的应用开发人员，你可以直接相对于原点放置内容，这将是用户的初始头位置和方向。 如果用户移到了一个新位置并想要继续进行其大规模体验，则可以在该位置 recenter 世界原点。

随着时间的推移，随着系统更详细地了解用户的环境，它可能会确定现实世界不同点之间的距离是否比以前认为的系统更短或更长。 如果在应用程序上的应用程序的固定框架中呈现全息影像，而用户在游离的范围内超过5米，则您的应用程序可能会观察到这些全息影像的观察位置。 如果你的体验的用户 wandering 超过5米，则会生成[全球规模的体验](#building-a-world-scale-experience)，这将需要更多的技术来保持全息稳定，如下所述。

### <a name="attached-frame-of-reference"></a>附加引用框架

当应用程序首次创建框架时，附加的引用框架将随用户一起四处移动。 这样，用户就可以轻松地浏览位于该引用框架中的内容。 以该用户相关的方式呈现的内容称为**正文锁定**内容。

当耳机无法确定它在世界中的位置时，附加的参考框架提供了可用于呈现全息影像的唯一坐标系统。 这使得它非常适合用于显示回退 UI，告诉用户其设备无法在世界中找到它们。 已固定或更高的应用程序应包括仅限方向的回退，以帮助用户再次工作，UI 与[混合现实主页](navigating-the-windows-mixed-reality-home.md)中显示的 UI 类似。

## <a name="building-a-standing-scale-or-room-scale-experience"></a>构建大规模或会议室规模的体验

若要超越沉浸式耳机，并构建**大规模体验**，可以使用**参考阶段框架**。

为了提供**房间规模的体验**，让用户在预先定义的5米边界内浏览，你还可以检查**阶段边界**。

### <a name="stage-frame-of-reference"></a>阶段引用框架

第一次设置沉浸式耳机时，用户定义了一个阶段，该**阶段**表示他们将遇到混合现实的场所。 舞台最小程度地定义了一个**舞台原点**、一个空间坐标系统，该系统位于用户所选楼层位置，并在其打算使用设备的位置前进方向。 通过将内容放在 Y = 0 地面平面上的 "舞台坐标系统" 中，可以确保在用户发生时，您的全息影像非常熟悉，为用户提供**大规模的体验**。

### <a name="stage-bounds"></a>阶段边界

用户还可以选择定义**舞台边界**，即在房间内已清除了其在混合现实中要四处移动的区域。 如果是这样，则该应用程序可以使用这些界限来构建**会议室规模的体验**，以确保在用户可以访问的位置始终放置全息影像。

由于参考的阶段框架提供了一个固定坐标系统，在该系统中放置了楼层相关的内容，因此，它是迁移为虚拟现实耳机开发的大规模和房间规模应用程序的最简单途径。 但是，与这些 VR 平台一样，单个坐标系统仅可在大约5米（16英尺）直径的情况下稳定内容，在杆上，拉杆从中心到最远的内容在系统调整后就会显著影响。 若要超过5米，则需要空间锚。

## <a name="building-a-world-scale-experience"></a>构建全球范围的体验

HoloLens 允许用户游离5米以上的真正**世界规模体验**。 若要构建全球规模的应用程序，你将需要超出用于会议室规模体验的新技术。

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>为什么不能在5米以上使用单个刚性坐标系统

目前，编写游戏、数据可视化应用程序或虚拟现实应用时，典型的方法是建立一个绝对世界坐标系统，所有其他坐标都可以可靠地映射回。 在该环境中，始终可以找到一个稳定的转换，用于定义该世界中任意两个对象之间的关系。 如果未移动这些对象，则其相对转换始终保持不变。 当渲染纯粹的虚拟世界时，这种全局坐标系统可以正常工作。 如今，房间内的 VR 应用通常建立此类绝对房间级坐标系统，并将其原点置于地面上。

与此相反，untethered mixed reality 设备（如 HoloLens）对世界有动态的传感器驱动理解，随着用户的周围时间的推移而不断调整其知识，因为他们在一座建筑的整个楼层走出了很多时间。 在全球范围内，如果你将所有全息影像置于单个硬坐标系中，则这些全息影像一定会随着时间的推移而发生变化，不管是在世界之间还是彼此之间。

例如，耳机当前可能相信世界上的两个位置相隔4米，然后在以后优化此理解，了解位置实际上是3.9 米。 如果这些全息影像最初在一个硬坐标系中相隔4米，则其中一个将始终从真实世界向下显示0.1 米。

### <a name="spatial-anchors"></a>空间定位点

Windows Mixed Reality 通过使你能够创建[空间锚](spatial-anchors.md)点来标记用户已放置全息影像的重要点，可以解决上一部分中所述的问题。 空间定位点表示系统应随时间跟踪的世界上的重要点。

当设备了解到世界时，这些空间定位点可以根据需要调整它们之间的位置，以确保每个定位点相对于真实世界的位置保持准确。 通过在用户放置全息影像的位置放置一个空间锚点，然后相对于其空间锚点定位该全息图，可以确保全息影像保持最佳稳定性，即使用户在数米内漫游也是如此。

空间锚点之间的这种持续调整相对于另一种情况是：坐标系统与空间锚定和固定的参考框架之间的主要区别：

* 放置在 "固定" 引用框架中的全息影像会彼此保持彼此的严格关系。 但是，当用户进行长距离工作时，框架的坐标系统可能会相对于世界的偏移，以确保用户旁边的全息影像显得稳定。

* 放置在参考阶段的全息影像还会保留彼此之间的严格关系。 与固定框架不同，阶段框架始终相对于其定义的物理原点保持固定位置。 但是，当舞台坐标系统中呈现的内容超出其5计量边界时，它将仅在用户处于该边界内时才显示为稳定。

* 使用一个空间锚点放置的全息影像可能会相对于使用另一个空间锚点放置的全息影像而偏移。 这使 Windows 能够提高其对每个空间锚点的位置的理解，即使在这种情况下，一个定位点需要自行调整，另一个定位点需要进行调整。

与固定框架（始终优化用户附近的稳定性）相比，引用和空间锚的阶段框架可确保其起源附近的稳定性。 这有助于在一段时间内使这些全息影像保持准确的位置，但这也意味着，从离坐标系统源太远的位置渲染离线会遇到越来越严重的杠杆的影响。 这是因为，舞台或锚点的位置和方向的小调整会按与该锚点的距离成比例放大。 

合理的经验法则是确保基于远处空间锚定系统呈现的所有内容都在其原点约3米以内。 对于附近的阶段，呈现远距离内容是正常的，因为任何增加的定位错误都将只影响不会在用户的视图中发生很多移动的小全息影像。

### <a name="spatial-anchor-persistence"></a>空间锚点持久性

空间锚还可以让你的应用程序记住重要的位置，即使在应用程序挂起或设备关闭后也是如此。

你可以将应用创建的空间锚点保存到磁盘，以后再通过将其保存到应用的**空间锚存储**来重新加载它们。 保存或加载定位点时，需要提供对应用有意义的字符串键，以便以后标识定位点。 请将此密钥视为定位点的文件名。 如果要将其他数据与该锚点相关联（例如用户放置在该位置的3D 模型），请将其保存到应用的本地存储，并将其与所选的密钥相关联。

通过将定位点保存到应用商店，你的用户可以放置单独的全息影像，或放置一个工作区，应用将在该工作区中放置其各种全息影像，然后在其预期的位置找到这些全息影像，这超出了应用的多种用途。

还可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>在 HoloLens、iOS 和 Android 设备上实现异步全息影像持久性。  通过共享持久的云空间定位点，多个设备可以随着时间推移观察相同的持久全息影像，即使这些设备没有同时出现，也是如此。

### <a name="spatial-anchor-sharing"></a>空间锚点共享

您的应用程序也可以与其他设备实时共享空间锚，从而实现实时共享体验。

使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>，你的应用可以跨多个 HoloLens、IOS 和 Android 设备共享空间锚。 通过使每个设备使用相同的空间定位点呈现全息影像，所有用户将看到全息影像显示在现实世界中的相同位置。

## <a name="avoid-head-locked-content"></a>避免 head 锁定的内容

我们强烈建议您不要渲染 head 锁定的内容，这会停留在显示的固定位置（如 HUD）。 通常情况下，对用户而言，打印头锁定的内容不舒服，并不像世界各地。

通常情况下，应将 Head 锁定的内容替换为附加到用户或放置在世界上的全息影像。 例如，通常应将[游标](cursors.md)推入世界，并自然地进行缩放，以反映该对象在用户注视下的位置和距离。

## <a name="handling-tracking-errors"></a>处理跟踪错误

在某些环境（例如深色走廊）中，耳机可能不能使用内置式跟踪在世界上正确定位。 如果不正确地处理，这可能导致全息影像不会显示或显示在错误的位置。 现在，我们讨论了这种情况的发生情况、其对用户体验的影响以及最好地处理这种情况的技巧。

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>由于没有足够的传感器数据，耳机无法跟踪

有时，耳机传感器无法确定耳机的位置。 如果房间太暗，或者传感器被头发或双手覆盖，或者周围没有足够的纹理，就会发生这种情况。

出现这种情况时，头戴式耳机将无法跟踪其位置，以呈现全球锁定的全息影像。 您将无法确定空间锚，固定框架或舞台帧相对于设备的位置，但仍可在附加的参考框架中呈现正文锁定的内容。

您的应用程序应告诉用户如何获取位置跟踪，并呈现一些用于描述一些提示的回退正文锁定内容，例如，发现传感器并打开更多的灯光。

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>由于环境中的动态更改，耳机跟踪不正确

有时，如果环境中存在大量动态更改，则设备无法正常进行跟踪，例如许多人在房间内浏览。 在这种情况下，当设备尝试在此动态环境中对自身进行跟踪时，全息影像可能看起来像是跳转或偏移。 如果按此方案，建议在不太动态的环境中使用该设备。

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>耳机跟踪不正确，因为随着时间的推移，环境发生了重大变化

有时，当你开始在发生大量更改（例如，家具、墙壁 hangings 等的重大变动）的环境中使用耳机时，某些全息影像可能会从其原始位置移动。 当用户在此新空间中四处移动时，早期的全息影像还可能会跳过。 这是因为系统对你的空间的了解不再保留，并且在尝试协调空间的功能时，它会尝试重新映射该环境。 在这种情况下，建议鼓励用户在不显示所需位置的情况下将其固定在世界上的全息影像。

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>由于环境中的空间相同，耳机跟踪出现错误

有时，家庭或其他空间可能有两个相同的区域。 例如，两个相同的会议室，两个相同的角区，两个相同的海报涵盖了设备的视图。 在这种情况下，设备有时可能会混淆相同的部分，并在内部表示形式中将它们标记为相同。 这可能会导致某些区域中的全息影像出现在其他位置。 设备可能会开始丢失跟踪，因为它的内部表示形式已损坏。 在这种情况下，建议重置系统的环境理解。 请注意，重置地图将导致丢失所有空间定位。 这将导致耳机在环境的唯一区域中顺利地进行跟踪。 但是，如果设备再次在相同的区域之间发生混乱，则可能会发生此问题。

## <a name="see-also"></a>另请参阅
* [GDC 2017 演示了空间坐标系统和全息渲染](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Unity 中的坐标系统](coordinate-systems-in-unity.md)
* [DirectX 中的坐标系统](coordinate-systems-in-directx.md)
* [空间定位点](spatial-anchors.md)
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* [案例研究 - 看透现实中的洞](case-study-looking-through-holes-in-your-reality.md)
