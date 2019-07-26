---
title: HoloLens 2 的 MR 教育共享模块
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 46c32abaf45623b7ccba90f257959e4ef4f8e1b5
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485641"
---
#  <a name="1-setting-up-photon-unity-networking"></a>1.设置 Photon Unity 网络

在本教程中, 我们将了解如何通过将 Photon Unity 联网 (双关语) 导入到 Unity 项目来创建共享体验。 Photon 是可供混合现实开发人员用来创建共享体验的多个网络选项之一。 我们将了解如何创建 Photon 帐户、导入 Photon 以及创建可选的本地服务器

## <a name="objectives"></a>目标

* 了解如何创建 Photon 帐户

* 了解如何查找和导入 Photon Unity 网络

* 设置本地 Photon 服务器

  

## <a name="setting-up-photon"></a>设置 Photon

1. 设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。 通过单击[此链接](https://dashboard.photonengine.com/en-US/Account/SignUp)导航到 "Photon 注册" 页。 按照注册页上的说明来创建帐户。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 单击 "创建新应用程序" 按钮, 创建一个应用程序 ID。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 在 Photon Type 下的下拉菜单中选择 Photon 双关语。 然后为其指定名称。 在此示例中, 我们将其命名为 HoloLensPhotonProject。 完成后, 单击 "创建" 按钮。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 完成后, 返回到应用程序页面, 你应该会看到类似于下图的内容。 单击应用程序 ID 并复制它。 将其粘贴到可以轻松访问的位置。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 创建新的 unity 项目, 并将其命名为 HLSharingProject。 有关如何创建新 Unity 项目的说明, 请参阅[基本模块的 "创建 Unity 项目" 部分](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 

6. 加载项目后, 单击 "资产存储" 选项卡, 如下图所示。 然后, 在下图中突出显示的 "搜索" 框中, 键入 "双关语", 然后从搜索结果中选择 "Photon 双关语 2-免费" 资产。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 通过按 "下载" 和 "导入" 按钮来下载和导入此资产。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. 完成导入过程后, 将显示双关语向导 Photon。 获取步骤4中的应用程序 ID (应在剪贴板中), 将其粘贴到 "AppID" 框中, 然后按 "设置项目" 按钮。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. 成功添加 AppID 后, 导航到资产中的 Photon-> PhotonUnityNetworking > 资源-> PhotonServerSettings。 选择 "使用名称服务器" 选项, 并将 "固定区域" 设置为 "US" 或 "photon" 服务区域。

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>祝贺

已成功创建 Photon 帐户, 设置本地 Photon 服务器, 并将双关语导入到 Unity。 下一步是设置项目, 并允许与其他用户建立连接, 使多个用户能够看到你的工作。 

[下一教程:2.让 Unity 为开发做好准备](mrlearning-sharing(photon)-ch2.md)

