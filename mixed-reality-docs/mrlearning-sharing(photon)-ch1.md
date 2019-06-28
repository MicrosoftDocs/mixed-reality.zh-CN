---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416118"
---
# <a name="setting-up-photon"></a>Photon 设置

在本课中，我们将了解如何为你的 Unity 项目导入 Photon Unity 网络 （双关语） 创建的共享的体验做好准备。 Photon 是多个网络选项可供 Mixed Reality 开发人员若要创建共享的体验之一。 我们我们将了解如何创建 Photon 帐户、 导入 Photon，并创建可选的本地服务器

目标：

* 了解如何创建 Photon 帐户

* 了解如何查找和导入 Photon Unity 网络

* 设置本地 Photon server

  

### <a name="setting-up-photon"></a>Photon 设置

1. 设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。 通过单击导航到 Photon 注册页面[此链接](https://dashboard.photonengine.com/en-US/Account/SignUp)。 若要创建该帐户注册页面上按照的说明。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 通过单击"创建新的应用程序"按钮创建一个应用程序 ID。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 从"photon 类型。"下的下拉列表菜单中选择"Photon 双关语" 然后为其提供一个名称，在此示例中，我们将其命名为"HoloLensPhotonProject。" 完成后，单击"创建"按钮。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 完成后，返回到应用程序页，并应看到类似于下面的图片。 单击应用程序 id 并将其复制。 粘贴是可以轻松访问的某个位置。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 创建一个新的 unity 项目并将其命名为"HLSharingProject。" 有关如何创建一个新的 Unity 项目的说明，请参阅[基本模块的"创建 Unity 项目"一节](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 

6. 项目加载后，单击"资产存储区"选项卡上，如下图中所示。 然后，在下图中突出显示搜索框中，键入"双关语"并从搜索结果中选择"Photon 双关语 2-免费"资产。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 下载并导入此资产按"下载"和"导入"按钮。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon 完成导入进程，将出现双关语向导。 获取第 4 步中的应用程序 ID （它应位于您的剪贴板上） 并将其粘贴到 AppID 框中，并按"安装项目"按钮。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. 已成功添加后 AppID，导航到"Photon"->"PhotonUnityNetworking"->"资源"->"PhotonServerSettings"中的资产。 选择"使用名称服务器"选项，将固定的区域设置为"我们"或你 photon 服务区域。

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>祝贺

已成功创建 Photon 帐户、 设置本地 Photon 服务器，并导入 Unity 俏皮话。 下一步是将设置项目，然后允许与其他用户的连接，以便多个用户可以看到您的工作。 

[下一课：第 2 课 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)

