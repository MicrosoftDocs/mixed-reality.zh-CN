---
title: 在 HoloLens 2 上学习 ASA 模块 Azure 空间锚的 MR
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327402"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (如果错误, 请更正我)

在本课中, 

目标

* 了解如何 _____________________________________________

* 了解如何 _________________________________________________

  

## <a name="instructions"></a>说明

### <a name="setting-up-photon"></a>设置 Photon

1. 设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。 执行此操作将会输入你的电子邮件并完成一些验证步骤。
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 注册后, 单击 "Sdk"。 一旦处于该页上, 请单击 "服务器", 并确保显示 "自承载"。 然后向下滚动并单击 "服务器", 如下图所示。

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. 这将导致文本框显示为 "阅读我"。 继续阅读。 完成后, 单击 "downloadSDK" 旁边的链接以下载它。


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. 下载完成后, 双击该文件夹。  文件资源管理器打开并公开 SDK 文件夹后, 请复制 SDK 文件夹。
   
   - 下一步是进入 windows C: 驱动器, 并创建名为 "server" 的新文件夹。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 现在打开文件夹, 然后粘贴前面复制的 SDK 文件夹。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. 完成后, 打开 SDK 文件夹, 然后前往 "部署", 然后单击 "bin_Win64", 然后双击 "photon 控件"。


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 注意:如果对 IP 地址或任何其他类似的问题有任何疑问, 则可以在工具栏中找到大多数信息 (如下图所示)。
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. 设置并启动服务器后, 请返回到 Photon 网站, 然后单击 "配置文件" 图标 (下图中的 "装箱"), 并选择 "应用程序"。
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. 单击 "创建新应用" 按钮, 创建一个应用程序 ID。

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - 从 "Photon 类型" 下的下拉菜单中选择 "Photon 运行"。 然后为其指定一个名称 (你要记住的内容)。 在此示例中, 我们将其命名为 "HoloLensPhotonProject"。 完成后, 单击 "创建"。

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 完成后, 返回到应用程序页面, 你应该会看到类似于下图的内容。 单击 "应用 ID" 并复制它。 可以轻松地进行访问。  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 创建新的 unity 项目。 打开 Unity 中心, 并单击 "新建"。 将其命名为 "HLSharingProject"。 然后单击 "创建"。 

   > 纪录根据计算机的速度, 最多可能需要2分钟的时间来加载。

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 注意: 通过更改 "location" 选项, 选择一个在计算机中保存项目的位置。 将其保存到你会记住并可轻松访问的位置。

10. 加载项目后, 请单击 "资产存储"。 然后, 在下图所示的搜索框中键入 "双关语", 并选择 "Photon 双关语-2 FREE" 资产。 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. 下载和导入!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**设置 Unity 项目** 

11. 单击此处, 下载在 Unity 中设置 Photon 所需的新资产[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. 在 Unity 中, 单击 "资产" 菜单并选择 "导入资产", 然后单击 "自定义资产"。

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 选择刚刚从步骤1中提供的链接下载的 Unity 包。 "导入" 按钮出现在 Unity 中后, 单击该按钮。

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 注意: 无论将包下载到何处, 都可以找到它。 上面的图像不会描绘出包的位置。

14. 创建新场景 (可以使用 control/command + N 或单击 "文件" 并选择 "新建场景" 来完成此操作。) 将场景保存为 "HLSharedProjectMain"。

> 注意: 你可能会收到类似于下面的图像的弹出窗口。 现在, 只需单击 "否"。
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. 在 "混合现实工具包" 下, 单击 "添加到场景并配置"。

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 完成后, 将出现一个新的配置文件, 允许你选择自定义配置文件。 单击 "复制并自定义"。

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 向下滚动并取消选中 "启用诊断系统"。 这可以更轻松地设置此项目。

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. 打开 "生成设置" (ctrl + shift + B)。 请注意, 该程序当前设置在 "PC、Mac 和 Linux 独立版" 平台下。 对于此项目, 请将平台设置为 "通用 windows 平台"。 选择它并单击 "切换平台"。

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 完成后, 单击显示 "添加打开的场景" 的框。 现在, 请前往检查器面板, 确保选中 "受支持的虚拟现实" (如下图所示) 右侧的复选框。 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 纪录还要确保还检查了 "场景/HLSharedProjectMain" 旁边的复选框。

20. 在 "检查器" 面板中的 "发布设置" 下, 向下滚动到 "功能" 并确保只标记以下复选框:

- internet 客户端
- internet 客户端服务器
- 专用网络客户端服务器
- 照相机/网络摄像机
- 麦克风

21. 与步骤12类似, 下一步是导入名为 "第2课" 的另一个自定义包, 可将其下载 [此处]。[第2课 link]导入该包。

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 现在, 在 "项目" 面板中, 请访问 "prototyping" 文件夹, 因为在接下来的几个步骤中, 将在场景中实施一些 prototyping。 在 "prototyping" 文件夹中, 单击 "prefab" 并将其拖到层次结构中。 完成后, 保存该项目 (依次单击 "文件"、"保存" 或 "ctrl + S")

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 纪录你可能会注意到, 当你单击 prefab 时, 会显示一个弹出窗口, 询问你有关 TMP Essentials 的信息。 如果需要, 请单击 "导入 TMP Essentials"。
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**连接多个用户**

23. 与步骤22一样, 在 "项目" 面板的 "prototyping" 文件夹中, 下一步是将 "NetworkLobby" prefab 拖放到层次结构中。 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 打开父 prefab "NetworkLobby" 时, 应会看到子 prefab "NetworkRoom"。 选择该选项后, 进入检查器面板, 然后单击 "添加组件"。 搜索 "PhotonView" 并添加组件。

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 在层次结构中创建新的空游戏对象 (在层次结构中右键单击并选择 "空")。 确保将 "位置" 设置为 x = 0、y = 0、z = 0 并将对象命名为 "PhotonUser"。

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>祝贺



