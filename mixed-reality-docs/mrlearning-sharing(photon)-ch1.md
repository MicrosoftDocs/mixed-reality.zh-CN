---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326721"
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

2. 一旦您注册了，单击 Sdk。 后该页面上，单击"服务器"，并确保它说，"自我托管。" 然后向下滚动并单击"服务器"中第二张插图所示。

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. 这将导致文本框中，以便显示标记，"读取我。" 请继续并读取它。 完成后，单击"downloadSDK"若要下载它旁边的链接。


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. 完成下载后，双击单击的文件夹。  在文件资源管理器打开后显示的 SDK 文件夹，将 SDK 文件夹复制。
   
   - 下一步是转到 windows c： 驱动器并创建新的文件夹名为 server。
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - 现在打开文件夹，并粘贴先前复制的 SDK 文件夹。
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. 完成后，打开 SDK 文件夹并转到"部署"然后"bin_Win64，"，然后双击"photon 控制"。


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> 注意：如果有任何疑问 IP 地址或任何其他类似问题，您可以在工具栏中发现你的信息的大部分，（如下图所示）。
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. 现在，设置并启动服务器，请返回到 Photon 网站并确保仍登录 （或重新登录，如果您不。）单击配置文件图标 （在下图右上角中装箱），然后选择"在应用程序"。
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. 通过单击"创建新的应用程序"按钮创建一个应用程序 ID。

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - 从"photon 类型。"下的下拉列表菜单中选择"Photon 双关语" 然后为其提供一个名称，在此示例中，我们将其命名为"HoloLensPhotonProject。" 完成后，单击"创建"按钮。

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. 完成后，返回到应用程序页，并应看到类似于下面的图片。 单击应用程序 id 并将其复制。 粘贴是可以轻松访问的某个位置。  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. 创建一个新的 unity 项目并将其命名为"HLSharingProject。" 有关如何创建一个新的 Unity 项目的说明，请参阅[基本模块的"创建 Unity 项目"一节](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 


10. 项目加载后，单击"资产存储区"选项卡上，如下图中所示。 然后，在下图中突出显示搜索框中，键入"双关语"并从搜索结果中选择"Photon 双关语 2 免费"的资产。 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. 下载并导入此资产按"下载"和"导入"按钮。
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>祝贺

已成功创建 Photon 帐户、 设置本地 Photon 服务器，并导入 Unity 俏皮话。 下一步是将设置项目，然后允许与其他用户的连接，以便多个用户可以看到您的工作。 

[下一课：第 2 课 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)

