---
title: MR 和 Azure 313-IoT 中心服务
description: 完成本课程, 了解如何在运行 Ubuntu 16.4 的虚拟机上实现 Azure IoT 中心服务, 然后使用 Microsoft HoloLens 或沉浸式 (VR) 耳机直观显示邮件数据。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, 混合现实, 学院, 边缘, iot edge, 教程, api, 通知, 函数, 表, hololens, 沉浸, vr, iot, 虚拟机, ubuntu, python
ms.openlocfilehash: ec669b799e7c46a9a4ed87674ed78e50f816c9e9
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047244"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

# <a name="mr-and-azure-313-iot-hub-service"></a>MR 和 Azure 313:IoT 中心服务

![课程结果](images/AzureLabs-Lab313-00.png)

在本课程中, 你将了解如何在运行 Ubuntu 16.4 操作系统的虚拟机上实现**Azure IoT 中心服务**。 然后, **azure Function App**将用于从 Ubuntu VM 接收消息, 并将结果存储在**Azure 表服务**中。 然后, 你将能够使用 Microsoft HoloLens 或沉浸式 (VR) 耳机上的**Power BI**查看此数据。

本课程的内容*适用*于 IoT Edge 设备, 不过, 在本课程中, 重点将位于虚拟机环境中, 因此不需要访问物理边缘设备。

完成本课程后, 你将学习:

- 将**IoT Edge 模块**部署到表示 IoT 设备的虚拟机 (UBUNTU 16 OS)。
- 将**Azure 自定义视觉 Tensorflow 模型**添加到 Edge 模块, 其中包含用于分析容器中存储的图像的代码。
- 设置模块以将分析结果消息发送回**IoT 中心服务**。
- 使用**azure Function App**将消息存储在**azure 表**中。
- 设置**Power BI**以收集存储的消息并创建报表。
- 在**Power BI**中直观显示 IoT 消息数据。

将使用的服务包括:

- **Azure IoT 中心**是一种 Microsoft Azure 服务, 它允许开发人员连接、监视和管理 IoT 资产。 有关详细信息, 请访问[ **Azure IoT 中心服务**页](https://azure.microsoft.com/en-au/services/iot-hub/)。

- **Azure 容器注册表**是一种 Microsoft Azure 服务, 它允许开发人员为各种类型的容器存储容器映像。 有关详细信息, 请访问[ **Azure 容器注册表服务**页](https://azure.microsoft.com/en-au/services/container-registry/)。

- **Azure Function App**是一种 Microsoft Azure 服务, 它允许开发人员在 Azure 中运行小部分代码 "函数"。 这提供了一种方法, 可将工作委托给云, 而不是本地应用程序, 这可能有很多好处。 **Azure Functions**支持多种开发语言, 包括 C\#、F\#、node.js、Java 和 PHP。 有关详细信息, 请访问[ **Azure Functions**页](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

- **Azure 存储:表**是一种 Microsoft Azure 服务, 它允许开发人员在云中存储结构化非 SQL 数据, 使其在任何地方都可以轻松访问。 此服务的设计良好, 可根据需要进行表的发展, 因此非常灵活。 有关详细信息, 请访问[ **Azure 表**页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

本课程将介绍如何设置和使用 IoT 中心服务, 然后将设备提供的响应可视化。 您可以将这些概念应用到您可能会构建的自定义 IoT 中心服务设置。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 313:IoT 中心服务</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

有关利用混合现实进行开发的最新先决条件, 包括 Microsoft HoloLens, 请访问[安装工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文。

> [!NOTE]
> 本教程适用于具有 Python 的基本经验的开发人员。 另外, 请注意, 本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容 (2018 年7月)。 您可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的软件内容完全匹配。

需要以下硬件和软件:

- Windows 10 秋季创意者更新 (或更高版本),**开发人员模式已启用**

    > [!WARNING]
    > 你无法在 Windows 10 Home Edition 上使用 Hyper-v 运行虚拟机。

- Windows 10 SDK (最新版本)
- **已启用 HoloLens、开发人员模式**
- Visual Studio 2017.15.4 (仅用于访问 Azure Cloud Explorer)
- Azure 和 IoT 中心服务的 Internet 访问。 有关详细信息, 请访问[IoT 中心服务页面链接](https://azure.microsoft.com/en-au/services/iot-hub/)
- 机器学习模型。 如果没有现成的可用模型,[可以使用本课程提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。
- 在 Windows 10 开发计算机上启用**hyper-v**软件。
- 运行 Ubuntu (16.4 或 18.4) 的虚拟机, 可在开发计算机上运行, 也可以使用运行 Linux 的单独计算机 (Ubuntu 16.4 或 18.4)。 可以在["开始之前" 一章](#before-you-start)中找到有关如何使用 Hyper-v 在 Windows 上创建虚拟机的详细信息。(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>开始之前

1. 设置并测试你的 HoloLens。 如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。
2. 在开始开发新的 HoloLens 应用程序时, 最好执行**校准**和**传感器调整**(有时它可以帮助为每个用户执行这些任务)。

有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens-2)。

有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。

3. 使用**hyper-v**设置**Ubuntu 虚拟机**。 以下资源将帮助你执行此过程。
    1.  首先, 请单击以下链接[下载 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/)。 选择**64-BIT PC (AMD64) 桌面映像**。
    2.  请确保已在 Windows 10 计算机上启用**hyper-v** 。 你可以访问此链接以获取有关在[Windows 10 上安装和启用 hyper-v](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)的指南。
    3.  启动 Hyper-v 并创建新的 Ubuntu VM。 可以访问此链接, 了解有关[如何使用 hyper-v 创建 VM](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)的分步指导。 当请求 **"从可启动的映像文件安装操作系统"** 时, 选择之前下载的**Ubuntu ISO** 。

    > [!NOTE]
    > 不建议使用**Hyper-v 快速创建**。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第1章-检索自定义视觉模型

在本课程中, 您将有权访问[预建的自定义视觉模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip), 用于检测图像中的键盘和鼠标。 如果使用此操作, 请转到[第2章](#chapter-2---the-container-registry-service)。

但是, 如果想要使用自己的自定义视觉模型, 则可以执行以下步骤:

1. 在**自定义视觉项目**中转到 "**性能**" 选项卡。

    > [!WARNING]
    > 您的模型必须使用*精简*域来导出模型。 你可以在项目的设置中更改模型域。

    ![性能选项卡](images/AzureLabs-Lab313-01.png)

2. 选择要导出的**迭代**, 并单击 "**导出**"。 随即出现一个边栏选项卡。

    ![导出边栏选项卡](images/AzureLabs-Lab313-02.png)

3. 在边栏选项卡中, 单击 " **Docker 文件**"。

    ![选择 docker](images/AzureLabs-Lab313-03.png)

4. 在下拉菜单中单击 " **Linux** ", 然后单击 "**下载**"。

    ![单击 "下载"](images/AzureLabs-Lab313-04.png)

5. 解压缩内容。 稍后将在本课程中使用它。

## <a name="chapter-2---the-container-registry-service"></a>第2章-容器注册表服务

**容器注册表服务**是用于托管容器的存储库。

你将在本课程中构建和使用的**IoT 中心服务**是指**容器注册表服务**, 用于获取要在边缘设备中部署的容器。

1. 首先, 请[在 Azure 门户](https://portal.azure.com/)中单击此链接, 然后用你的凭据登录。

2. 请参阅**创建资源**并查找**容器注册表**。

    ![容器注册表](images/AzureLabs-Lab313-05.png)

3. 单击 "**创建**"。

    ![](images/AzureLabs-Lab313-06.png)

4. 设置服务安装参数:

    1. 插入项目的名称, 在本示例中, 它称为**IoTCRegistry**。

    2. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种方式来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。

    3. 设置服务的位置。

    4. 将 "**管理员用户**" 设置为**启用**。

    5. 将**SKU**设置为**基本**。 

    ![](images/AzureLabs-Lab313-07.png)

5. 单击 "**创建**" 并等待要创建的服务。 

6. 通知进入成功创建*容器注册表*后, 请单击 "**转到资源**", 将其重定向到 "服务" 页。

    ![](images/AzureLabs-Lab313-08.png)

7. 在 "*容器注册表*服务" 页上, 单击 "**访问密钥**"。

8. 请注意 (可以使用记事本) 以下参数:
    1. **登录服务器**
    2. **Username**
    3. **密码**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第3章-IoT 中心服务

现在, 你将开始创建和设置**IoT 中心服务**。

1. 如果尚未登录, 请登录到[Azure 门户](https://portal.azure.com)。

2.  登录后, 单击左上角的 "**创建资源**", 搜索 " **IoT 中心**", 然后单击 " **Enter**"。

 ![搜索存储帐户](images/AzureLabs-Lab313-10.png)

3.  新页将提供**存储帐户**服务的说明。 在此提示符的左下方, 单击 "**创建**" 按钮以创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab313-11.png)

4.  单击 "**创建**" 后, 将显示一个面板:

    1. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。

        > 如果希望了解有关 Azure 资源组的详细信息, 请参阅此[链接, 了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。


    2. 选择适当的**位置**(在本课程中创建的所有服务之间使用同一位置)。

    3. 为此服务实例插入所需的**名称**。    

5.  在页面底部, 单击 **"下一步":大小和缩放**。

    ![创建存储实例](images/AzureLabs-Lab313-12.png)

6.  在此页中, 选择**定价和缩放层**(如果这是你的第一个 IoT 中心服务实例, 你应该可以使用免费层)。  

7.  单击 "**查看" + "创建**"。

    ![创建存储实例](images/AzureLabs-Lab313-13.png)

8.  查看设置, 然后单击 "**创建**"。

    ![创建存储实例](images/AzureLabs-Lab313-14.png)

9. 通知进入成功创建*IoT 中心*服务的通知后, 请单击 "**转到资源**", 将其重定向到 "服务" 页。

    ![创建存储实例](images/AzureLabs-Lab313-15.png)

10. 滚动到左侧的侧面板, 直到看到 "*自动设备管理*", 然后单击 " **IoT Edge**"。

    ![创建存储实例](images/AzureLabs-Lab313-16.png)

11. 在出现在右侧的窗口中, 单击 "**添加 IoT Edge 设备**"。 边栏选项卡将显示在右侧。

12. 在边栏选项卡中, 为新设备提供**设备 ID** (所选的名称)。 然后单击 "**保存**"。 如果已**自动生成**勾选, 则*主密钥*和*辅助密钥*将自动生成。

    ![创建存储实例](images/AzureLabs-Lab313-17.png)

13. 你将导航回*IoT Edge 设备*"部分, 将在其中列出新设备。 单击新设备 (下图中以红色突出显示)。 

    ![创建存储实例](images/AzureLabs-Lab313-18.png)

14. 在出现的 "*设备详细信息*" 页上, 获取**连接字符串**(主键) 的副本。

    ![创建存储实例](images/AzureLabs-Lab313-19.png)

15. 返回到左侧的面板, 单击 "*共享访问策略*" 将其打开。 

16. 在显示的页面上, 单击 " **iothubowner**", 屏幕右侧会显示一个边栏选项卡。 

17. 请注意**连接字符串的连接字符串**(主密钥), 以便以后在将*连接字符串*设置到设备时使用。

    ![创建存储实例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>第4章-设置开发环境

若要为*IoT 中心边缘*创建和部署模块, 需要在运行 Windows 10 的开发计算机上安装以下组件:

1.  [用于 Windows 的 Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows), 它将要求你创建一个可供下载的帐户。 

    [![下载适用于 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker 需要*windows 10 专业* *版、企业版 14393*或*windows Server 2016 RTM*才能运行。 如果你运行的是其他版本的 Windows 10, 则可以尝试使用[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)安装 docker。

2.  [Python 3.6](https://www.python.org/downloads/)。

    [![下载 python 3。6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (也称为 VS Code)](https://code.visualstudio.com/download)。

    [![下载 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

安装上述软件之后, 需要重新启动计算机。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>第5章-设置 Ubuntu 环境

现在, 可以转到设置**运行 UBUNTU 操作系统**的设备。 按照以下步骤安装所需的软件, 以便在你的面板上部署容器:

> [!IMPORTANT]
> 应始终在带有**sudo**的终端命令之前, 以管理员用户身份运行。 亦
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  打开**Ubuntu 终端**, 并使用以下命令安装**pip**:

    > [!提示] 可以使用键盘快捷方式轻松地打开*终端*:**Ctrl + Alt + T**。

    ```bash
        sudo apt-get install python-pip
    ```

2.  在本章中, 系统可能会提示你:*终端*, 允许使用设备存储, 并输入**y/n** (是或否), 键入 **"y"** , 然后按**enter**键接受。

3.  完成该命令后, 请使用以下命令安装**卷**:

    ```bash
        sudo apt install curl
    ```

4.  安装**pip**和**卷曲**后, 使用以下命令安装**IoT Edge 运行时**, 这是部署和控制板上的模块所必需的:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. 此时, 系统将提示你打开*运行时配置文件*, 以便在创建**IoT 中心服务**(在第[3 章的步骤 14](#chapter-3---the-iot-hub-service)中) 时, 插入你记下的**设备连接字符串**(在记事本中)。 在终端上运行以下行, 以打开该文件:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. 此时将显示**yaml**文件, 供你编辑:

    > [!WARNING]
    > 打开此文件时, 可能会有些混乱。 你将在*终端*本身中编辑此文件的文本。 

    1.  使用键盘上的箭头键向下滚动 (您将需要向下滚动一点), 以便到达包含 ":

        **"\<将设备连接字符串添加到此处 >** "。

    2. 用前面记下的**设备连接字符串**替换线条 (**包括方括号**)。

7. 建立连接字符串后, 请在键盘上按**Ctrl + X**键保存该文件。 它将要求通过键入**Y**进行确认。然后, 按**enter**键以确认。 你将返回到常规*终端*。 

8. 成功运行这些命令后, 你将安装**IoT Edge 运行时**。 初始化后, 每次打开设备时, 运行时就会自行启动, 并将在后台等待从**IoT 中心服务**部署模块。

9.  运行以下命令行, 初始化*IoT Edge 运行时*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > 如果更改了 yaml 文件或上述设置, 则需要在*终端*内再次运行上面的重新启动行。

10. 通过运行以下命令行检查*IoT Edge 运行时*状态。 运行时应以绿色文本显示状态 "**活动 (正在运行)** "。

    ```bash
        sudo systemctl status iotedge
    ```

11. 按下**Ctrl + C**键, 退出 "状态" 页。 可以通过键入以下命令来验证*IoT Edge 运行时*是否正确拉取容器:

    ```bash
        sudo docker ps
    ```

12. 应该会出现一个包含两个 (2) 容器的列表。 这些是 IoT 中心服务 (edgeAgent 和 edgeHub) 自动创建的默认模块。 一旦您创建和部署自己的模块, 它们将显示在此列表中的默认值之下。

## <a name="chapter-6---install-the-extensions"></a>第6章-安装扩展

> [!IMPORTANT]
> 接下来的几章 (6-9) 将在你的 Windows 10 计算机上执行。

1. 打开**VS Code**。

2. 单击 VS Code 左侧栏上的 "**扩展**" (方形) 按钮, 打开 "**扩展" 面板**。

3. 搜索并安装以下扩展 (如下图所示):

    1. Azure IoT Edge
    2. Azure IoT 工具包
    3. Docker   

    ![创建容器](images/AzureLabs-Lab313-24.png)

4. 安装扩展后, 请关闭并重新打开 VS Code。

5. 再打开 VS Code, 导航到 "**查看** > " "**集成终端**"。

6. 现在, 你将安装**Cookiecutter**。 在终端中运行以下 bash 命令:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示] 如果你在使用此命令时遇到问题: 
    >1. 重新启动 VS Code 和/或您的计算机。
    >2. 可能有必要将**VS Code 终端**切换到你用来安装 Python 的计算机 (即**Powershell** ) (尤其是在计算机上已安装 python 环境时)。 打开终端后, 会在终端的右侧找到下拉菜单。
     ![创建容器](images/AzureLabs-Lab313-24b.png) 
    >3. 请确保将**Python**安装路径添加为计算机上的**环境变量**。 Cookiecutter 应属于同一位置路径。 [有关环境变量的详细信息](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), 请访问此链接 

7. **Cookiecutter**安装完成后, 应重新启动计算机, 以便在系统环境中将**Cookiecutter**识别为命令。

## <a name="chapter-7---create-your-container-solution"></a>第7章-创建容器解决方案

此时, 需要创建包含模块的容器, 将其推送到*容器注册表*中。 推送容器后, 将使用*IoT 中心边缘*服务将其部署到运行*IoT Edge 运行时*的设备。

1. 在 VS Code 中, 单击 "**查看** > " "**命令面板**"。

2. 在调色板中, 搜索并运行**Azure IoT Edge:新的 Iot Edge**解决方案。

3. 浏览到要在其中创建解决方案的位置。 按**enter**键接受该位置。

4. 为解决方案指定一个名称。 按**enter**键以确认所提供的名称。

5. 现在, 系统将提示您选择解决方案的模板框架。 单击 " **Python 模块**"。 按**enter**键确认此选择。

6. 为模块指定名称。 按**enter**键以确认模块的名称。 请确保记下模块名称的注释 (使用记事本), 因为稍后将用到它。

7. 你会注意到, 组件面板上将显示预先生成的*Docker 映像存储库*地址。 它将如下所示:

    **localhost: 5000/-模块的名称-** 。 

8. 删除**localhost:5000**，并在其位置插入 *容器注册表* **登录服务器**地址，创建时记下**容器注册表服务**([在步骤 8 的第 2 章](#chapter-2---the-container-registry-service))。 按**enter**键以确认地址。

9. 此时, 将创建包含 Python 模块模板的解决方案, 并将其结构显示在 "浏览" 选项卡的 "**浏览器" 选项卡**中, 在 "浏览器" 选项卡中, 在 "浏览器" 选项卡中, 在 "VS Code 如果 "**资源管理器" 选项卡**未打开, 则可以通过单击左侧栏中的最上面的按钮打开它。

    ![创建容器](images/AzureLabs-Lab313-25.png)

10. 本章节中，最后一步是单击，然后打开 **.env 文件**，从**浏览选项卡**，并添加你 *容器注册表* **用户名** 并 **密码**。 Git 忽略此文件, 但在构建容器时, 将设置用于访问**容器注册表服务**的凭据。

    ![创建容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>第8章-编辑容器解决方案

现在, 你将通过更新下列文件来完成容器解决方案:

- py python 脚本。 *<span></span>*
- *要求 .txt*。
- *deployment*。
- *Dockerfile amd64*

然后, 将创建用于 python 脚本的 images 文件夹, 以检查图像是否与*自定义视觉模型*匹配。 最后, 您将添加*标签 .txt*文件, 以帮助读取您的模型, 以及模型文件 。

1. 打开 VS Code, 导航到模块文件夹, 然后查找名 **<span></span>为 py**的脚本。 双击以打开它。

2. 删除文件的内容并插入以下代码:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  打开名为 "**要求 .txt**" 的文件, 并将其内容替换为以下内容:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  打开名为 " **deployment**" 的文件, 并根据以下准则替换其内容:

    1. 由于你将拥有自己的唯一 JSON 结构, 因此需要手动编辑 (而不是复制示例)。 为此, 请使用以下图像作为指导。
    2. 外观与你的区域不同, 但你**不应更改为黄色**。
    3. **您需要删除的部分将突出显示为红色。**
    4. 请注意删除正确的方括号, 同时删除逗号。

        ![创建容器](images/AzureLabs-Lab313-27.png)

    5. 已完成的 JSON 应该如下图所示 (但唯一的区别在于:*用户名/密码/模块名称/模块引用*):

        ![创建容器](images/AzureLabs-Lab313-28.png)

5.  打开名为**Dockerfile**的文件, 并将其内容替换为以下内容:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  右键单击 "**模块**" 下的文件夹 (它将具有你先前提供的名称; 在示例中, 该名称为 " *pythonmodule*"), 然后单击 "**新建文件夹**"。 将文件夹命名为**images**。

7.  在该文件夹中, 添加包含鼠标或键盘的一些图像。 这些将是 Tensorflow 模型将分析的映像。

    > [!WARNING]
    > 如果你使用自己的模型, 则需要更改此以反映你自己的模型数据。

8.  你现在需要在[第1章](#chapter-1---retrieve-the-custom-vision-model)中从你先前下载的 (或从你自己的**自定义影像服务**创建的) 模型文件夹中检索**标签 .txt**和**model。** 获得这些文件后, 请将它们放在解决方案中, 并将它们放在其他文件中。 最终结果应该如下图所示:

    ![创建容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第9章-将解决方案打包为容器

1.  现在, 你可以将文件 "打包" 为容器并将其推送到**Azure 容器注册表**。 在 VS Code 中, 打开*集成终端*("**查看** > **集成终端**" 或 " **Ctrl**+ **\`** "), 并使用以下行登录到**Docker** (将带有**Azure 容器注册表 (ACR)** 的凭据的命令:

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. 右键单击文件 " **deployment**", 然后单击 "**生成 IoT Edge 解决方案**"。 此生成过程需要很长时间 (具体取决于你的设备), 因此请准备好等待。 在生成过程完成后, 将在名为**config**的新文件夹内创建一个**deployment. json**文件。

    ![创建部署](images/AzureLabs-Lab313-30.png)

3. 再次打开**命令面板**, 搜索 **"Azure":** 登录。 按照使用 Azure 帐户凭据的提示进行操作;VS Code 将向你提供一个选项, 用于*复制和打开*, 这将会复制你即将需要的设备代码, 并打开默认 web 浏览器。 当系统询问时, 粘贴设备代码以对计算机进行身份验证。

    ![复制并打开](images/AzureLabs-Lab313-31.png)

4. 登录后, 将在 "*浏览*" 面板的底部看到一个名为 " **Azure IoT 中心设备**" 的新部分。 单击此部分以将其展开。

    ![边缘设备](images/AzureLabs-Lab313-32.png)

5. 如果你的设备不在此处, 你需要右键单击 " *Azure IoT 中心设备*", 然后单击 "**设置 IoT 中心连接字符串**"。 然后, 你将看到**命令面板**(位于 VS Code 顶部) 将提示你输入*连接字符串*。 这是你在[第3章](#chapter-3---the-iot-hub-service)末尾记下的*连接字符串*。 在中复制字符串后, 按**enter**键。    

6. 设备应加载并显示。 右键单击设备名称, 然后单击 "**创建单个设备的部署**"。

    ![创建部署](images/AzureLabs-Lab313-33b.png)

7. 你将看到一个*文件资源管理器*提示, 你可以在其中导航到**config**文件夹, 然后选择 " **deployment** " 文件。 选择该文件后, 单击 "**选择边缘部署清单**" 按钮。

    ![创建部署](images/AzureLabs-Lab313-34.png)

8. 此时, 你已为**IoT 中心服务**提供了一个清单, 用于从**Azure 容器注册表**将容器 (作为模块) 部署到你的设备, 并有效地将其部署到设备。

9. 若要查看从设备发送到 IoT 中心的消息, 请再次右键单击 " **Azure IoT 中心设备**" 部分中的设备名称, 然后在 "**资源管理器**" 面板中单击 "**开始监视 D2C 消息**"。 设备发送的消息应显示在 VS 终端中。 请耐心等待, 因为这可能需要一些时间。 请参阅下一章进行调试, 并检查部署是否成功。

此模块现在将在**images**文件夹中的图像之间进行循环访问, 并在每次迭代时进行分析。 这显然只是演示如何获取基本机器学习模型, 以便在 IoT Edge 设备环境中工作。 

若要扩展此示例的功能, 可以通过多种方式继续操作。 其中一种方法可能是在容器中包含某些代码, 这些代码从连接到设备的网络摄像机捕获照片, 并将图像保存到 images 文件夹中。 

另一种方法是将映像从 IoT 设备复制到容器中。 实现此目的的一种可行方法是在 IoT 设备终端中运行以下命令 (如果想要自动执行此过程, 可能只有小型应用才能执行此操作)。 可以通过从存储文件的文件夹位置手动运行此命令来对其进行测试:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第10章-调试 IoT Edge 运行时

下面是命令行和提示的列表, 可帮助你从**Ubuntu 设备**监视和调试*IoT Edge 运行时*的消息传递活动。 

- 通过运行以下命令行检查*IoT Edge 运行时*状态:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > 请记得按**Ctrl + C**来完成状态的查看。

- 列出当前部署的容器。 如果*IoT 中心服务*成功部署了容器, 则会通过运行以下命令行来显示它们:

    ```bash
        sudo iotedge list
    ```

    或

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 以上是检查模块是否已成功部署的好方法, 因为它将出现在列表中;否则, 你将**只**看到*edgeHub*和*edgeAgent*。

- 若要显示容器的代码日志, 请运行以下命令行:

    ```bash
        journalctl -u iotedge
    ```

**用于管理 IoT Edge 运行时的有用命令:**

-  删除主机中的所有容器:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  若要停止*IoT Edge 运行时*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>第11章-创建表服务 

导航回到 Azure 门户, 在该门户中创建存储资源。

1. 如果尚未登录, 请登录到[Azure 门户](https://portal.azure.com)。

2. 登录后, 单击左上角的 "**创建资源**", 搜索 "**存储帐户**", 然后按**enter**键开始搜索。

3. 出现后, 单击列表中的 "**存储帐户-blob、文件、表、队列**"。

    ![搜索存储帐户](images/AzureLabs-Lab313-35.png)

4. 新页将提供**存储帐户**服务的说明。 在此提示符的左下方, 单击 "**创建**" 按钮以创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab313-36.png)

5. 单击 "**创建**" 后, 将显示一个面板:

    1. 为此服务实例插入所需的**名称**(*必须全部小写*)。

    2. 对于**部署模型**, 单击 "**资源管理器**"。

    3. 对于 "**帐户类型**", 请使用下拉菜单, 单击 "**存储 (常规用途 v1)** "。

    4. 单击适当的**位置**。
    
    5. 对于 "**复制**" 下拉菜单, 单击 "**读取-访问-异地冗余存储 (GRS)** "。

    6. 对于 "**性能**", 请单击 "**标准**"。

    7. 在 "**需要安全传输**" 部分中, 单击 "**禁用**"。

    8. 从 "**订阅**" 下拉菜单中, 单击相应的订阅。

    9. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种方式来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。

        > 如果希望了解有关 Azure 资源组的详细信息, 请参阅此[链接, 了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 如果这是一个选项, 请将**虚拟网络**保留为**禁用状态**。

    11. 单击“创建”。

        ![填写存储详细信息](images/AzureLabs-Lab313-37.png)

6. 单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。

7. 创建服务实例后, 门户中将显示一个通知。 单击通知以浏览新服务实例。

    ![新存储通知](images/AzureLabs-Lab313-38.png)

8. 单击通知中的 "**转到资源**" 按钮, 会转到 "新建存储服务实例概述" 页。

    ![中转到资源](images/AzureLabs-Lab313-39.png)

9. 在 "概述" 页中, 单击右侧的 "**表**"。
    
    ![tables](images/AzureLabs-Lab313-40.png)

10. 右侧面板将更改为显示**表服务**信息, 你需要添加一个新表。 单击左上角的 " **+ 表**" 按钮即可执行此操作。

    ![打开表](images/AzureLabs-Lab313-41.png)

11. 将显示一个新页, 需要在其中输入**表名称**。 这是将用于在后面的章节中引用应用程序中的数据的名称 (创建 Function App 和 Power BI)。 插入 " **IoTMessages** " 作为名称 (可以自行选择, 只需记住它, 稍后在本文档中使用), 然后单击 **"确定"** 。 

12. 创建新表后, 可以在 "**表服务**" 页 (底部) 中查看它。

    ![已创建新表](images/AzureLabs-Lab313-42.png)  

13. 现在, 单击 "**访问密钥**", 然后复制**存储帐户名称**和**密钥**(使用记事本), 稍后在创建**Azure Function App**时, 将使用这些值。

    ![已创建新表](images/AzureLabs-Lab313-43.png) 

14. 再次使用左侧的面板, 滚动到 "*表服务*" 部分, 单击 "**表**" (或 "在新门户中**浏览表**"), 并获取**表 URL** (使用记事本) 的副本。 在本课程中, 将表链接到**Power BI**应用程序时, 将使用此值。

    ![已创建新表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第12章-完成 Azure 表

由于已设置了**表服务**存储帐户, 因此可以向其添加数据, 这将用于存储和检索信息。 可以通过**Visual Studio**来编辑表。

1. 打开**Visual Studio** (**不**Visual Studio Code)。

2. 从菜单中, 单击 "**查看** > **Cloud Explorer**"。

    ![打开 cloud explorer](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer**将作为停靠项打开 (患者, 因为加载可能需要一些时间)。

    > [!WARNING] 
    > 如果用于创建*存储帐户*的订阅不可见, 请确保: 
    > - 已登录到与 Azure 门户一起使用的帐户。
    > - 从 "帐户管理" 页中选择了你的订阅 (你可能需要从帐户设置应用筛选器):  
    >
    >   ![查找订阅](images/AzureLabs-Lab313-46.png)

4. 将显示你的 Azure 云服务。 查找**存储帐户**, 并单击其左侧的箭头以展开你的帐户。

    ![打开存储帐户](images/AzureLabs-Lab313-47.png)

5. 展开后, 新创建的**存储帐户**应该可用。 单击存储左侧的箭头, 然后在展开后, 查找 "**表**" 并单击该按钮旁边的箭头, 以显示在上一章中创建的**表**。 双击**表**。

6. 您的表将在您的 Visual Studio 窗口的中心打开。 单击与表图标 **+** （加上） 在其上。

    ![添加新表](images/AzureLabs-Lab313-48.png)

7. 将显示一个窗口, 提示你*添加实体*。 您将只创建一个实体, 但它将具有三个属性。 你会注意到已提供了*PartitionKey*和*RowKey* , 因为表使用这些方法来查找数据。 

    ![分区和行键](images/AzureLabs-Lab313-49.png)

8. 更新以下值:

    - 名称：**PartitionKey**, 值:**PK_IoTMessages** 

    - 名称：**RowKey**, 值:**RK_1_IoTMessages** 

9. 然后, 在 "*添加实体*" 窗口的左下角单击 "**添加属性**", 并添加以下属性:

    - **MessageContent**, 将值保留为空。

10. 表应与下图中的表匹配:

    ![添加正确的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > 在行键中, 实体的编号为1的原因是, 您可能需要添加更多的消息, 而您希望在本课程中进行进一步试验。

11. 完成后, 单击 **"确定"** 。 现在可以使用表了。

## <a name="chapter-13---create-an-azure-function-app"></a>第13章-创建 Azure Function App 

现在可以创建一个*Azure Function App*, *IoT 中心服务*将调用该将*IoT Edge*设备消息存储在之前章节中创建的**表**服务中。

首先, 需要创建一个文件, 该文件允许 Azure 函数加载所需的库。

1.  打开**记事本**(按*Windows 键*, 然后键入*Notepad*)。

    ![打开记事本](images/AzureLabs-Lab313-51.png)

2.  打开记事本后, 将下面的 JSON 结构插入其中。 完成此操作后, 将其以**项目 json**的形式保存在桌面上。 此文件定义函数将使用的库。 如果使用了 NuGet, 则会很熟悉。
    
    > [!WARNING]
    > 命名正确, 这一点很重要。确保它没有 **.txt**文件扩展名。 请参阅下面的参考:
    >
    > ![JSON 保存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  登录到[Azure 门户](https://portal.azure.com)。

4.  登录后, 单击左上角的 "**创建资源**", 搜索**Function App**, 然后按**enter**键进行搜索。 在结果中单击 " *Function App* " 以打开新面板。

    ![搜索函数应用](images/AzureLabs-Lab313-53.png)

5.  新面板将提供**Function App**服务的说明。 在此面板的左下方, 单击 "**创建**" 按钮以创建与此服务的关联。

    ![function app 实例](images/AzureLabs-Lab313-54.png)

6.  单击 "**创建**" 后, 请填写以下内容:

    1. 对于 "**应用名称**", 请为此服务实例插入所需的名称。

    2. 选择**订阅**。

    3. 选择适合你的定价层, 如果这是第一次创建**Function App 服务**, 则应提供免费层。

    4. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种方式来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。

        > 如果希望了解有关 Azure 资源组的详细信息, 请参阅此[链接, 了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 对于**操作系统**, 请单击 "Windows", 因为这是预期的平台。

    6. 选择**托管计划**(本教程使用**消耗计划**。

    7. 选择**位置**(选择与在上一步骤中生成的存储相同的位置)

    8. 对于 "**存储**" 部分,**你必须选择在上一步中创建的存储服务**。

    9. 在此应用中不需要*Application Insights* , 因此可随意将其**关闭**。

    10. 单击“创建”。

        ![创建新实例](images/AzureLabs-Lab313-55.png)

7.  单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。

8.  创建服务实例后, 门户中将显示一个通知。

    ![新建通知](images/AzureLabs-Lab313-56.png)

9.  完成部署后, 单击 "通知"。

10. 单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 

    ![中转到资源](images/AzureLabs-Lab313-57.png)

11. 在左侧和右侧的新面板，单击 **+** （加号） 旁边的图标*函数*，以创建新的函数。

    ![添加新函数](images/AzureLabs-Lab313-58.png)

12. 在中央面板中, 将显示 "**函数**创建" 窗口。 进一步向下滚动, 然后单击 "**自定义函数**"。

    ![自定义函数](images/AzureLabs-Lab313-59.png)

13. 在下一页上向下滚动, 直到找到**IoT 中心 (事件中心)** , 然后单击它。

    ![自定义函数](images/AzureLabs-Lab313-60.png)

14. 在 " **IoT 中心 (事件中心)** " 边栏选项卡中, **C#** 将 "语言" 设置为, 然后单击 "**新建**"。

    ![自定义函数](images/AzureLabs-Lab313-61.png)

15. 在将显示的窗口中, 确保已选中 " **Iot 中心**", 并且 " *iot 中心*" 字段的名称与你之前创建的*iot 中心服务*的名称 ([在第3章的步骤8中](#chapter-3---the-iot-hub-service)) 相对应。 然后单击 "**选择**" 按钮。

    ![自定义函数](images/AzureLabs-Lab313-62.png)

16. 返回到**IoT 中心 (事件中心)** 边栏选项卡, 并单击 "**创建**"。

    ![自定义函数](images/AzureLabs-Lab313-63.png)

17. 你将被重定向到函数编辑器。

    ![自定义函数](images/AzureLabs-Lab313-64.png)

18. 删除其中的所有代码, 并将其替换为以下代码:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 更改以下变量, 使其对应于你将在**存储帐户**中找到的相应值 (**表**和**存储**值,[分别为第11章和第11章的步骤11和 13](#chapter-11---create-table-service)):

    - **tableName**, 其中包含你的**存储帐户**中的**表**的名称。
    - **tableURL**, 其中包含你的**存储帐户**中的**表**的 URL。
    - **storageAccountName**, 其中包含与你的**存储帐户**名称的名称相对应的值的名称。
    - **storageAccountKey**, 其中包含你之前在创建的存储服务中获得的密钥。

    ![自定义函数](images/AzureLabs-Lab313-65.png)

20. 在代码准备就绪后, 单击 "**保存**"。

21. 接下来，单击 **\<** （箭头） 图标，在页面的右侧。

    ![自定义函数](images/AzureLabs-Lab313-66.png)

22. 面板会从右侧滑入。 在该面板中, 单击 "**上载**", 将显示*文件浏览器*。

23. 导航到, 然后单击 "您之前在**记事本**中创建的**项目 json**文件", 然后单击 "**打开**" 按钮。 此文件定义函数将使用的库。

    ![自定义函数](images/AzureLabs-Lab313-67.png)

24. 文件上传后, 它将显示在右侧的面板中。 单击它会在**函数**编辑器中打开它。 它必须与下一个图像**完全**相同。

    ![自定义函数](images/AzureLabs-Lab313-68.png)

25. 此时, 最好测试函数将消息存储在*表*中的功能。 在窗口的右上角, 单击 "**测试**"。

    ![自定义函数](images/AzureLabs-Lab313-69.png)

26. 在**请求正文**中插入一条消息 (如上图所示), 然后单击 "**运行**"。 

27. 该函数将运行, 并显示结果状态 (你将注意到 "*输出*" 窗口上方的 "已**接受绿色状态 202**", 这表示它是成功的调用):

    ![输出结果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第14章-查看活动消息

如果现在打开 Visual Studio (**而不**是 Visual Studio Code), 可以可视化测试消息结果, 因为它将存储在*MessageContent*字符串区域中。

![自定义函数](images/AzureLabs-Lab313-71.png)

在表服务和 Function App 就绪后, Ubuntu 设备消息将显示在*IoTMessages*表中。 如果尚未运行, 则重新启动设备, 你将能够通过使用 Visual Studio *Cloud Explorer*在表中看到来自你的设备和模块的结果消息。

![可视化数据](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第15章-Power BI 安装

若要将数据从 IOT 设备中可视化, 你需要设置**Power BI** (桌面版本), 以从你刚创建的*表*服务中收集数据。 Power BI 的*HoloLens*版本随后将使用该数据来可视化结果。

1.  在 Windows 10 上打开 Microsoft Store, 并搜索**Power BI Desktop**。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  下载应用程序。 完成下载后, 请将其打开。

3.  用**Microsoft 365 帐户**登录*Power BI* 。 你可能会被重定向到浏览器进行注册。 注册后, 返回到 Power BI 应用, 然后再次登录。

4.  单击 "**获取数据**", 然后单击 "**更多 ...** "。

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  单击 " **azure**"、" **azure 表存储**", 然后单击 "**连接**"。

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  系统将提示您插入先前收集的**表 URL** ([第11章第11章的第13步](#chapter-11---create-table-service)), 同时创建表服务。 插入 URL 后, 删除引用表 "子文件夹" (在本课程中为 IoTMessages) 的路径部分。 最终结果应如下图所示。 然后单击 **"确定"** 。

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  系统将提示你在创建表存储时, 先插入你记下的**存储密钥**([在第11章的第11章中](#chapter-11---create-table-service))。 然后单击 "**连接**"。

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. 将显示 **"导航器" 面板**, 勾选表旁边的框, 然后单击 "**加载**"。

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. 你的表现在已在 Power BI 上加载, 但它需要一个查询以显示其中的值。 为此, 请右键单击位于屏幕右侧的 "**字段" 面板**中的表名称。 然后单击 "**编辑查询**"。

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. **Power Query 编辑器**将作为新窗口打开, 并显示您的表。 单击表的 "*内容*" 列中的字词**记录**, 以可视化存储的内容。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. 单击窗口左上角的 "**到表**"。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. 单击 "**关闭" & 应用**。

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 完成加载查询后, 在屏幕右侧的 "**字段" 面板**中, 勾选与参数**名称**和**值**相对应的框, 以可视化**MessageContent**列内容。

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. 单击窗口左上角的**蓝色磁盘图标**, 将工作保存到所选的文件夹中。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. 你现在可以单击 "发布" 按钮将表上传到工作区。 出现提示时, 单击 **"我的工作区**" 并单击 "*选择*"。 等待它显示成功提交的提交结果。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 下面是特定于 HoloLens 的章节。 Power BI 当前不可用作沉浸式应用程序, 但你可以通过桌面应用在 Windows Mixed Reality 门户 (也称为 Cliff 房子) 中运行桌面版本。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>第16章-显示 Power BI HoloLens 上的数据

1. 在 HoloLens 上, 通过在应用程序列表中点击其图标来登录到**Microsoft Store**。

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. 搜索并下载**Power BI**应用程序。

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. 从应用程序列表中启动**Power BI** 。 

4. **Power BI**可能会要求你登录到**Microsoft 365 帐户**。

5. 在应用程序中, 默认情况下, 工作区应显示, 如下图所示。 如果未执行此操作, 只需单击窗口左侧的工作区图标。

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>已完成 IoT 中心应用程序

恭喜, 你已成功创建了一个包含模拟虚拟机边缘设备的 IoT 中心服务。 你的设备可以将机器学习模型的结果传达给 Azure 表服务, 该服务由 Azure Function App (读入 Power BI 并在 Microsoft HoloLens 中进行可视化) 促进。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

展开表中存储的消息结构, 并将其显示为图形。 您可能想要收集更多的数据, 并将其存储在同一个表中, 以便以后显示。

### <a name="exercise-2"></a>练习2

创建要部署在 IoT 板上的其他 "相机捕获" 模块, 使其可以通过要分析的相机捕获映像。
