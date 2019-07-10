---
title: MR 和 Azure 313-IoT 中心服务
description: 完成此课程以了解如何在运行 Ubuntu 16.4 的虚拟机上实现 Azure IoT 中心服务，然后使用 Microsoft HoloLens 或沉浸式的 (VR) 耳机将消息数据可视化。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 edge、 iot edge、 教程、 api、 通知、 函数中，表、 沉浸式 hololens、 vr、 iot、 虚拟机、 ubuntu、 python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694592"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

# <a name="mr-and-azure-313-iot-hub-service"></a>MR 和 Azure 313:IoT 中心服务

![课程结果](images/AzureLabs-Lab313-00.png)

在本课程中，您将学习如何实现**Azure IoT 中心服务**虚拟机上运行 Ubuntu 16.4 操作系统。 **Azure Function App**然后将使用 Ubuntu VM，从接收消息并在将结果存储**Azure 表服务**。 然后将能够查看此数据使用**Power BI** Microsoft HoloLens 或沉浸式 (VR) 耳机上。

本课程的内容*适用于*到 IoT Edge 设备，但在本课程中，他们将着重介绍在虚拟机环境中，因此就不需要访问物理边缘设备。

通过完成本课程，您将了解到：

- 部署**IoT Edge 模块**到虚拟机 (Ubuntu 16 OS)，它将表示你的 IoT 设备。
- 添加**Azure 自定义影像 Tensorflow 模型**到 Edge 模块，将分析图像存储在容器中的代码。
- 设置该模块将分析结果消息发送回您**IoT 中心服务**。
- 使用**Azure Function App**存储中的消息**Azure 表**。
- 设置**Power BI**收集存储的消息和创建报表。
- 实现 IoT 消息中的数据可视化效果**Power BI**。

将使用的服务包括：

- **Azure IoT 中心**是一种 Microsoft Azure 服务，使开发人员可以连接、 监视和管理 IoT 资产。 有关详细信息，请访问[ **Azure IoT 中心服务**页面](https://azure.microsoft.com/en-au/services/iot-hub/)。

- **Azure 容器注册表**是一种 Microsoft Azure 服务，使开发人员可以将容器映像，为各种类型的容器。 有关详细信息，请访问[ **Azure 容器注册表服务**页面](https://azure.microsoft.com/en-au/services/container-registry/)。

- **Azure Function App**是一个 Microsoft Azure 服务，它允许开发人员运行小段代码，函数，在 Azure 中。 这使您能够将工作委托给云，而不是本地应用程序，它可以有许多好处。 **Azure Functions**支持多种开发语言，包括 C\#，F\#，Node.js、 Java 和 PHP。 有关详细信息，请访问[ **Azure Functions**页面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

- **Azure 存储：表**是一个 Microsoft Azure 服务，它使开发人员可以存储结构化，非 SQL、 数据在云中，使其在任意位置时可以轻松进行访问。 该服务实现了一种无架构设计，根据需要允许为表的演变，因此非常灵活。 有关详细信息，请访问[ **Azure 表**页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

本课程将介绍如何设置并使用 IoT 中心服务，然后直观显示由设备提供的响应。 它将取决于您要应用于自定义的 IoT 中心服务安装，您可能要构建的这些概念。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 313:IoT 中心服务</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

有关使用混合现实，包括与 Microsoft HoloLens，进行开发的最新的必备组件，请访问[安装的工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文。

> [!NOTE]
> 本教程专为开发人员没有使用 Python 的基本经验。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配将比下面列出的较新的软件中找到的内容。

以下硬件和软件是必需的：

- Windows 10 Fall Creators Update （或更高版本），**启用开发人员模式**

    > [!WARNING]
    > 不能运行在 Windows 10 家庭版上使用 HYPER-V 的虚拟机。

- Windows 10 SDK （最新版本）
- 一个 HoloLens，**启用开发人员模式**
- Visual Studio 2017.15.4 （仅用于访问 Azure 云资源管理器）
- Internet 访问 Azure，以及 IoT 中心服务。 有关详细信息，请遵循此[链接到 IoT 中心服务页](https://azure.microsoft.com/en-au/services/iot-hub/)
- 机器学习模型。 如果不具有自己的已准备好使用模型中，[可以使用与此课程中提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。
- **Hyper V** Windows 10 的开发计算机上启用软件。
- 在开发计算机或者运行运行 Ubuntu （16.4 或 18.4） 的虚拟机可以使用运行 Linux (Ubuntu 16.4 或 18.4) 的单独计算机。 可以找到有关如何在 Windows 上创建的 VM 详细信息使用中的 HYPER-V ["开始之前"一章](#before-you-start)。 (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>开始之前

1. 设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。
2. 它是执行一个好办法**校准**并**传感器优化**开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时。

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

3. 设置你**Ubuntu 虚拟机**使用**HYPER-V**。 以下资源将帮助你与该进程。
    1.  首先，按照此链接[下载 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/)。 选择**64 位电脑 (AMD64) 桌面映像**。
    2.  请确保**HYPER-V**在 Windows 10 计算机上启用。 您可以在跟踪指导此链接[安装和启用 Windows 10 上的 HYPER-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)。
    3.  启动 HYPER-V 并创建一个新的 Ubuntu 虚拟机。 可以按照此链接[有关如何使用 HYPER-V 创建虚拟机的分步指南](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)。 请求时 **"从可启动映像文件安装操作系统"** ，选择**Ubuntu ISO**先前已下载。

    > [!NOTE]
    > 使用**HYPER-V 快速创建**不建议使用。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第 1 章-检索自定义影像模型

本课程将有权[预建的自定义影像模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)，用于检测键盘和鼠标从映像。 如果使用此操作，请转到[第 2 章](#chapter-2---the-container-registry-service)。

但是，如果你想要使用你自己的自定义影像模型可以执行以下步骤：

1. 在你**自定义视觉项目**转到**性能**选项卡。

    > [!WARNING]
    > 您的模型必须使用*compact*域，以导出该模型。 你可以为你的项目中设置模型的域。

    ![性能选项卡](images/AzureLabs-Lab313-01.png)

2. 选择**迭代**你想要导出，然后单击**导出**。 将显示一个边栏选项卡。

    ![导出边栏选项卡](images/AzureLabs-Lab313-02.png)

3. 在边栏选项卡中单击**Docker 文件**。

    ![选择 docker](images/AzureLabs-Lab313-03.png)

4. 单击**Linux**在下拉列表菜单，然后单击**下载**。

    ![单击下载](images/AzureLabs-Lab313-04.png)

5. 将其中内容解压缩。 稍后在本课程中，将使用它。

## <a name="chapter-2---the-container-registry-service"></a>第 2 章-容器注册表服务

**容器注册表服务**是用来承载你的容器的存储库。

**IoT 中心服务**你将构建和使用在本课程中，指**容器注册表服务**以获取要部署在边缘设备中的容器。

1. 首先，按照这[到 Azure 门户的链接](https://portal.azure.com/)，并使用你的凭据登录。

2. 转到**创建资源**并查找**容器注册表**。

    ![容器注册表](images/AzureLabs-Lab313-05.png)

3. 单击**创建**。

    ![](images/AzureLabs-Lab313-06.png)

4. 设置服务安装程序参数：

    1. 在此示例中插入一个名称为你的项目，它称**IoTCRegistry**。

    2. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配，以及管理 Azure 资产的集合计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

    3. 设置服务的位置。

    4. 设置**管理员用户**到**启用**。

    5. 设置**SKU**到**基本**。 

    ![](images/AzureLabs-Lab313-07.png)

5. 单击**创建**并等待要创建的服务。 

6. 后通知您成功创建弹出通知*容器注册表*，单击**转到资源**重定向到你的服务页面。

    ![](images/AzureLabs-Lab313-08.png)

7. 在中*容器注册表*服务页上，单击**访问密钥**。

8. 请注意 （可以使用在记事本） 的以下参数：
    1. **Login Server**
    2. **Username**
    3. **密码**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第 3 章-IoT 中心服务

现在，你将开始创建和安装你**IoT 中心服务**。

1. 如果尚未登录，登录到[Azure 门户](https://portal.azure.com)。

2.  登录后，单击**创建资源**在左上角，并搜索**IoT 中心**，然后单击**Enter**。

 ![搜索存储帐户](images/AzureLabs-Lab313-10.png)

3.  该新页面将提供的说明**存储帐户**服务。 在左下角此提示，请单击**创建**按钮，以创建服务的此实例。

    ![创建存储实例](images/AzureLabs-Lab313-11.png)

4.  一旦你单击**创建**，将显示一个面板：

    1. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

        > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。


    2. 选择相应**位置**（在本课程中创建的所有服务之间使用相同的位置）。

    3. 插入所需**名称**此服务实例。    

5.  在页面底部单击**下一步：大小和小数位数**。

    ![创建存储实例](images/AzureLabs-Lab313-12.png)

6.  在此页上，选择你**定价和缩放层**（如果这是你第一个 IoT 中心服务实例，免费级别应为可供你）。  

7.  单击**查看 + 创建**。

    ![创建存储实例](images/AzureLabs-Lab313-13.png)

8.  查看你的设置并单击**创建**。

    ![创建存储实例](images/AzureLabs-Lab313-14.png)

9. 后通知您成功创建弹出通知*IoT 中心*服务，单击**转到资源**重定向到你的服务页面。

    ![创建存储实例](images/AzureLabs-Lab313-15.png)

10. 滚动左侧侧面板，直到看到*自动设备管理*，单击**IoT Edge**。

    ![创建存储实例](images/AzureLabs-Lab313-16.png)

11. 在右侧显示窗口中，单击**添加 IoT Edge 设备**。 右侧将显示一个边栏选项卡。

12. 在边栏选项卡，提供新设备**设备 ID** （所选的名称）。 然后，单击**保存**。 *主*并*辅助密钥*将自动生成，如果你有**自动生成**勾选了。

    ![创建存储实例](images/AzureLabs-Lab313-17.png)

13. 将导航回*IoT Edge 设备*部分中，其中显示在新设备。 单击新设备上 (在红色框下图)。 

    ![创建存储实例](images/AzureLabs-Lab313-18.png)

14. 上*设备详细信息*页上显示，需要一份**连接字符串**（主键）。

    ![创建存储实例](images/AzureLabs-Lab313-19.png)

15. 返回到面板在左侧，并单击*共享访问策略*，若要打开它。 

16. 在显示的页面，单击**iothubowner**，和一个边栏选项卡将显示在屏幕的右侧。 

17. 请注意 （在你记事本) 上的**连接字符串**（主键），以供以后使用时设置*连接字符串*向你的设备。

    ![创建存储实例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>第 4 章-设置开发环境

若要创建和部署用于模块*IoT 中心 Edge*，将需要在运行 Windows 10 的开发计算机上安装以下组件：

1.  [适用于 Windows 的 docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，它会要求您创建的帐户，以便能够下载。 

    [![下载适用于 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker 需要*Windows 10 PRO*，*企业 14393*，或*Windows Server 2016 RTM*来运行。 如果正在运行其他版本的 Windows 10，则可以尝试使用 Docker 安装[Docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)。

2.  [Python 3.6](https://www.python.org/downloads/)。

    [![下载 python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (也称为 VS Code)](https://code.visualstudio.com/download)。

    [![下载 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

在安装前面所述的软件之后, 将需要重新启动你的计算机。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>第 5 章-设置 Ubuntu 环境

现在，可以设置你的设备转**运行 Ubuntu OS**。 请按照下面，安装必要的软件，将在板上的将容器部署的步骤操作：

> [!IMPORTANT]
> 应总是置于前面使用的终端命令**sudo**以管理用户身份运行。 即：
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  打开**Ubuntu 终端**，然后使用以下命令安装**pip**:

    > [!提示] 可打开*终端*非常轻松地通过使用键盘快捷方式：**Ctrl + Alt + T**。

    ```bash
        sudo apt-get install python-pip
    ```

2.  在本章中，您可能会提示您，由*终端*、 权限以使用你的设备存储，以及为你输入**y/n** （是或否）、 类型**y**，然后按**Enter**键，接受。

3.  完成该命令后，使用以下命令安装**curl**:

    ```bash
        sudo apt install curl
    ```

4.  一次**pip**并**curl**是安装，请使用以下命令安装**IoT Edge 运行时**，这是需要部署并控制在板上的模块：

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

5. 此时系统会提示打开*运行时配置文件*，以插入**设备连接字符串**，（你在记事本中），记下创建时**IoT 中心服务** ([处的章节 3 步骤 14，](#chapter-3---the-iot-hub-service))。 在终端来打开该文件上运行以下行：

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. **Config.yaml**文件将显示，以便您进行编辑：

    > [!WARNING]
    > 打开此文件后，它可能有些不易理解。 可以编辑此文件中的文本*终端*本身。 

    1.  使用键盘上的箭头键可滚动的列表中 （您将需要向下一个小的方式滚动），到达行包含":

        " **\<添加设备连接字符串 >** "。

    2. 替换为行中，**包括括号**，使用**设备连接字符串**，如上文所述。

7. 连接字符串后，在键盘上按**CTRL-X**键保存该文件。 它将请求您确认通过键入**Y**。然后，按**Enter**密钥进行确认。 将返回到常规*终端*。 

8. 这些命令具有所有运行成功后，便会安装**IoT Edge 运行时**。 初始化后，运行时将从其自身，打开设备的每次，并将一直等待模块从部署在后台**IoT 中心服务**。

9.  运行以下命令行来初始化*IoT Edge 运行时*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > 如果你的.yaml 文件或更高版本的安装程序进行更改，将需要再次运行上述的重新启动行内*终端*。

10. 检查*IoT Edge 运行时*通过运行以下命令行的状态。 在运行时应显示为状态**处于活动状态 （正在运行）** 绿色文本中。

    ```bash
        sudo systemctl status iotedge
    ```

11. 按**Ctrl + C**键，若要退出该状态页。 你可以验证*IoT Edge 运行时*拉取容器正确通过键入以下命令：

    ```bash
        sudo docker ps
    ```

12. 应显示两个 （2） 容器的列表。 这些是由 IoT 中心服务 （edgeAgent 和 edgeHub） 自动创建的默认模块。 一旦您创建和部署你自己的模块，它们将显示在此列表中，默认的下方。

## <a name="chapter-6---install-the-extensions"></a>第 6-章安装扩展

> [!IMPORTANT]
> 下一步的几个章节 (6-9) 是要在 Windows 10 计算机上执行。

1. 打开**VS 代码**。

2. 单击**扩展**（方形） 按钮在左侧栏的 VS Code 中，以打开**扩展面板**。

3. 搜索并安装，以下扩展 （如下图所示）：

    1. Azure IoT Edge
    2. Azure IoT 工具包
    3. Docker   

    ![创建容器](images/AzureLabs-Lab313-24.png)

4. 一旦安装了扩展，关闭并重新打开 VS Code。

5. 使用 VS Code 一次打开，导航到**视图** > **集成的终端**。

6. 现在，您将安装**Cookiecutter**。 在终端运行以下 bash 命令：

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示] 如果你遇到问题，使用以下命令： 
    >1. 重新启动 VS Code 中，和/或您的计算机。
    >2. 它可能需要切换**VS Code 终端**到你已在用于安装 Python，即**Powershell** （尤其是如果您的计算机上已安装的 Python 环境）。 终端打开后，您会发现终端右侧的下拉菜单。
     ![创建容器](images/AzureLabs-Lab313-24b.png) 
    >3. 请确保**Python**安装路径添加为**环境变量**在计算机上。 Cookiecutter 应该是相同的位置路径的一部分。 请遵循此[环境变量的详细信息的链接](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)， 

7. 一次**Cookiecutter**已完成安装，应重新启动你的计算机，以便**Cookiecutter**被识别为您的系统的环境中的命令。

## <a name="chapter-7---create-your-container-solution"></a>章 7-创建容器解决方案

此时，您需要创建具有该模块，若要推送到容器中，*容器注册表*。 已推送到容器，将使用*IoT 中心 Edge*服务，以将其部署到你的设备，这运行*IoT Edge 运行时*。

1. 从 VS Code 中，单击**视图** > **命令面板**。

2. 在面板中，搜索并运行**Azure IoT Edge:新的 Iot Edge 解决方案**。

3. 浏览到想要创建你的解决方案的位置。 按**Enter**键，若要接受的位置。

4. 为你的解决方案名称。 按**Enter**密钥，以确认你提供的名称。

5. 现在系统将提示选择你的解决方案模板 framework。 单击**Python 模块**。 按**Enter**密钥，以确认选择此选项。

6. 为你的模块名称。 按**Enter**密钥，以确认你的模块名称。 请务必记下 （与在记事本) 的模块名称，因为更高版本使用它。

7. 你会注意到预建*Docker 映像存储库*地址将显示在面板上。 它将如下所示：

    **localhost:5000 /-NAME 的模块-** 。 

8. 删除**localhost:5000**，并在其位置插入*容器注册表***登录服务器**地址，创建时记下**容器注册表服务**([在步骤 8 的第 2 章](#chapter-2---the-container-registry-service))。 按**Enter**密钥，以确认该地址。

9. 此时，将创建包含 Python 模块的模板的解决方案，其结构将显示在**浏览选项卡**，VS Code 中，在屏幕左侧。 如果**浏览选项卡**是未打开，您可以打开它通过单击最顶部的按钮，在左侧栏中。

    ![创建容器](images/AzureLabs-Lab313-25.png)

10. 本章节中，最后一步是单击，然后打开 **.env 文件**，从**浏览选项卡**，并添加你*容器注册表***用户名**并**密码**。 通过 git，忽略此文件，但有关生成容器，将设置用于访问的凭据**容器注册表服务**。

    ![创建容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>第 8 章-编辑容器解决方案

现在，您将完成的容器解决方案，通过更新以下文件：

- *主要<span></span>.py* python 脚本。
- *requirements.txt*。
- *deployment.template.json*。
- *Dockerfile.amd64*

然后您将创建*映像*文件夹中，python 脚本用于检查的映像以匹配你*自定义影像模型*。 最后，您将添加*labels.txt*文件中，以帮助读取您的模型，并*model.pb*文件，它是您的模型。

1. 使用 VS Code 打开，导航到模块文件夹，然后查找名为脚本**主要<span></span>.py**。 双击将其打开。

2. 删除文件的内容并插入以下代码：

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

3.  打开的文件称为**requirements.txt**，并将其与以下内容：

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  打开的文件称为**deployment.template.json**，并将其替换其内容的以下准则如下：

    1. 由于你将有自己唯一的 JSON 结构，您需要对其进行手动编辑 （而不是复制示例）。 若要让轻松，请使用下图作为指南。
    2. 看起来会对由你掌控，不同的区域，但在**不应更改会突出显示的黄色**。
    3. **需删除，请使用此部分介绍了突出显示为红色。**
    4. 请注意，若要删除正确方括号，并且还可以删除逗号。

        ![创建容器](images/AzureLabs-Lab313-27.png)

    5. 已完成的 JSON 应如图所示 (不过，与你唯一的区别：*用户名/密码/模块名称/模块引用*):

        ![创建容器](images/AzureLabs-Lab313-28.png)

5.  打开的文件称为**Dockerfile.amd64**，并将其与以下内容：

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

6.  右键单击下方的文件夹**模块**(它将具有以前; 提供的名称在示例中进一步向下，它调用*pythonmodule*)，并单击**新文件夹**. 将文件夹命名为**映像**。

7.  在文件夹中，添加包含鼠标或键盘的一些图像。 这些将 Tensorflow 模型要分析的映像。

    > [!WARNING]
    > 如果使用自己的模型，您需要更改此设置以反映你自己的模型数据。

8.  您现在需要检索**labels.txt**并**model.pb**模型文件夹，你以前下载的文件 (或从你自己创建**自定义影像服务**)，在[第 1 章](#chapter-1---retrieve-the-custom-vision-model)。 这些文件后，将它们放在你的解决方案，以及其他文件。 最终结果应类似于下图所示：

    ![创建容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第 9 章 — 包的容器解决方案

1.  你现已准备好你的文件"包"作为容器并将其推送到您**Azure 容器注册表**。 在 VS Code 中打开*集成终端*(**视图** > **集成终端**或**Ctrl** + **\`** )，并使用登录到下面的代码行**Docker** (的凭据的命令的值替换你**Azure 容器注册表 (ACR)** ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. 右键单击该文件**deployment.template.json**，然后单击**生成 IoT Edge 解决方案**。 此生成过程需要花费很长时间 （具体取决于你的设备），因此请准备好等待。 生成过程完成后， **deployment.json**文件将创建一个名为的新文件夹内**config**。

    ![创建部署](images/AzureLabs-Lab313-30.png)

3. 打开**命令面板**同样，并搜索**Azure:登录**。 按照提示使用 Azure 帐户凭据;VS Code 将为您提供的选项*复制并打开*，这会将复制你很快将需要并打开默认 web 浏览器的设备代码。 当要求时，将粘贴的设备代码进行身份验证你的计算机。

    ![复制并打开](images/AzureLabs-Lab313-31.png)

4. 一旦登录后，在您将注意到，在底部的一端*浏览*面板中，一个名为的新部分**Azure IoT 中心设备**。 单击此部分，以将其展开。

    ![边缘设备](images/AzureLabs-Lab313-32.png)

5. 如果你的设备不是此处，您将需要右键单击*Azure IoT 中心设备*，然后单击**Set IoT Hub Connection String**。 然后会看到**命令面板**（在 VS Code 的顶部），将提示你输入你*连接字符串*。 这是*连接字符串*结束时记下[第 3 章](#chapter-3---the-iot-hub-service)。 按**Enter**键，一旦复制中的字符串。    

6. 你的设备应加载和显示。 右键单击设备名称，然后依次，**的单个设备创建部署**。

    ![创建部署](images/AzureLabs-Lab313-33b.png)

7. 你将获得*文件资源管理器*提示符下，您可以导航到**config**文件夹，，然后选择**deployment.json**文件。 该文件处于选定状态，单击**选择边缘部署清单**按钮。

    ![创建部署](images/AzureLabs-Lab313-34.png)

8. 此时您已提供你**IoT 中心服务**与清单即可部署你的容器，为模块，从你**Azure 容器注册表**，从而有效地将其部署到你的设备。

9. 若要查看从你的设备发送到 IoT 中心的消息，再次右键单击设备名称在**Azure IoT 中心设备**部分中，在**资源管理器**面板，并单击**启动监视D2C 消息**。 从你的设备发送的消息应显示在 VS 终端。 耐心等待，因为这可能需要一些时间。 请参阅下一章中的进行调试和检查部署是否成功。

现在，此模块将循环访问中的映像之间**映像**文件夹和分析，每次迭代。 这是很明显只是演示如何获取要在 IoT Edge 设备环境中工作的基本机器学习模型。 

若要扩展此示例中的功能，可以继续以下几种方式。 一种方法可能包括一些代码中的容器，用于捕获从网络摄像头，连接到设备，然后将映像保存在 images 文件夹中的照片。 

另一种方法可以将复制映像 IoT 设备到容器。 一个实用方法可执行此操作是在 IoT 设备 （可能是一个小型应用无法执行该作业，如果想要自动执行此过程） 的终端中运行以下命令。 可以通过从存储文件的文件夹位置手动运行它来测试此命令：

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第 10 章 — 调试 IoT Edge 运行时

以下是命令行和技巧，以帮助您监视和调试的消息传递活动的列表*IoT Edge 运行时*，从你**Ubuntu 设备**。 

- 检查*IoT Edge 运行时*通过运行以下命令行的状态：

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > 请记住，按**Ctrl + C**以完成查看状态。

- 列出当前已部署的容器。 如果*IoT 中心服务*是否容器成功部署，它们将显示通过运行以下命令行：

    ```bash
        sudo iotedge list
    ```

    或

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 以上是一种检查是否在模块是否已成功部署，因为它将出现在列表中; 很好方法否则将**仅**请参阅*edgeHub*并*edgeAgent*。

- 若要显示容器的代码日志，请运行以下命令行：

    ```bash
        journalctl -u iotedge
    ```

**用于管理 IoT Edge 运行时的有用命令：**

-  若要删除所有容器主机中：

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  若要停止*IoT Edge 运行时*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>章 11-创建表服务 

导航回到你的 Azure 门户，其中将创建 Azure 表服务，通过创建存储资源。

1. 如果尚未登录，登录到[Azure 门户](https://portal.azure.com)。

2. 登录后，单击**创建资源**，在左上角，并搜索**存储帐户**，然后按**Enter**键，若要开始搜索。

3. 一旦它已出现，请单击**存储帐户-blob、 文件、 表、 队列**从列表中。

    ![搜索存储帐户](images/AzureLabs-Lab313-35.png)

4. 该新页面将提供的说明**存储帐户**服务。 在左下角此提示，请单击**创建**按钮，以创建服务的此实例。

    ![创建存储实例](images/AzureLabs-Lab313-36.png)

5. 一旦你单击**创建**，将显示一个面板：

    1. 插入所需**名称**此服务实例 (*必须全部小写*)。

    2. 有关**部署模型**，单击**资源管理器**。

    3. 有关**帐户类型**，使用下拉列表菜单，单击**存储 (常规用途 v1)** 。

    4. 单击相应**位置**。
    
    5. 有关**复制**下拉菜单中，单击**读取-访问-异地冗余存储 (RA-GRS)** 。

    6. 有关**性能**，单击**标准**。

    7. 内**需要安全传输**部分中，单击**禁用**。

    8. 从**订阅**下拉菜单中，单击相应的订阅。

    9. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配，以及管理 Azure 资产的集合计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

        > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 将保留**虚拟网络**作为**禁用**，如果这是为你的选项。

    11. 单击“创建”  。

        ![填写存储详细信息](images/AzureLabs-Lab313-37.png)

6. 一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。

7. 创建服务实例后，在门户中将显示一条通知。 单击通知以了解新的服务实例。

    ![新的存储通知](images/AzureLabs-Lab313-38.png)

8. 单击**转到资源**按钮中的通知，和你将转到新的存储服务实例概述页。

    ![转到资源](images/AzureLabs-Lab313-39.png)

9. 从概述页上，到右侧，单击**表**。
    
    ![表](images/AzureLabs-Lab313-40.png)

10. 在右侧面板将更改为显示**表服务**其中所需添加一个新表的信息。 执行此操作通过单击 **+ 表**左上角的按钮。

    ![打开表](images/AzureLabs-Lab313-41.png)

11. 将显示一个新页面，其中你需要输入**表名称**。 这是将用于引用应用程序中后面的章节 （创建函数应用和 Power BI） 的数据的名称。 插入**IoTMessages**作为名称 （可以选择你自己，只需记住它稍后在本文档中使用时），单击**确定**。 

12. 一旦创建新表后，你将能够看到它在**表服务**页 （底部）。

    ![创建新表](images/AzureLabs-Lab313-42.png)  

13. 现在，单击**访问密钥**，并采取一份**存储帐户名称**并**密钥**（使用在记事本），您将使用这些值更高版本中此课程中，创建时**Azure 函数应用**。

    ![创建新表](images/AzureLabs-Lab313-43.png) 

14. 同样，在左侧使用面板滚动到*表服务*部分，然后单击**表**(或**浏览表**，较新的门户网站中)，并采取一份**表 URL** （使用在记事本）。 链接到您的表时，将稍后在本课程中，使用此值您**Power BI**应用程序。

    ![创建新表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第 12 章-完成 Azure 表

现在，你**表服务**存储帐户已被安装程序，即可将数据添加到它，将用于存储和检索信息。 编辑你的表，可通过完成**Visual Studio**。

1. 打开**Visual Studio** (**不**Visual Studio Code)。

2. 从菜单中，单击**视图** > **云资源管理器**。

    ![打开 cloud explorer](images/AzureLabs-Lab313-45.png)

3. **云资源管理器**以停靠项 （如加载可能需要时间，则请耐心等待，） 将打开。

    > [!WARNING] 
    > 如果用于创建订阅你*存储帐户*不可见，请确保您具有： 
    > - 登录到 Azure 门户使用的同一个帐户。
    > - （您可能需要从你的帐户设置应用筛选器） 在帐户管理页上选择你的订阅：  
    >
    >   ![查找订阅](images/AzureLabs-Lab313-46.png)

4. 将显示在 Azure 云服务。 查找**存储帐户**，然后单击箭头以展开你的帐户的左侧。

    ![打开存储帐户](images/AzureLabs-Lab313-47.png)

5. 展开后，新创建**存储帐户**应可用。 单击你的存储，左侧的箭头，然后后，已展开，找到**表**，然后单击箭头旁边的以显示**表**在最后一章中创建。 双击您**表**。

6. 将在 Visual Studio 窗口的中心中打开您的表。 单击与表图标 **+** （加上） 在其上。

    ![添加新表](images/AzureLabs-Lab313-48.png)

7. 你能够将出现一个窗口提示*添加实体*。 您将创建一个实体，它将具有三个属性也是如此。 您会注意*PartitionKey*并*RowKey*已提供了，因为需要使用这些表以查找你的数据。 

    ![分区键和行键](images/AzureLabs-Lab313-49.png)

8. 更新以下值：

    - 名称：**PartitionKey**，值：**PK_IoTMessages** 

    - 名称：**RowKey**，值：**RK_1_IoTMessages** 

9. 然后，单击**将属性添加**(到左下角*添加实体*窗口)，并添加以下属性：

    - **MessageContent**，作为*字符串*，将值保留为空。

10. 您的表应与下图中的一个匹配：

    ![添加正确的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > 实体具有行键中的数字 1 的原因是因为你可能想要添加更多消息，你希望试验进一步与此课程。

11. 单击**确定**完成之后。 您的表现可供使用。

## <a name="chapter-13---create-an-azure-function-app"></a>章 13-创建 Azure Function App 

现在即可创建*Azure Function App*，这将调用*IoT 中心服务*存储*IoT Edge*设备中的消息**表**服务，在上一章中创建。

首先，需要创建一个文件，将允许您的 Azure 函数以加载所需的库。

1.  打开**记事本**(按*Windows 键*，然后键入*记事本*)。

    ![打开记事本](images/AzureLabs-Lab313-51.png)

2.  使用记事本打开，将插入到其中的以下 JSON 结构。 完成后，将其保存为您的桌面上**project.json**。 此文件定义函数将使用的库。 如果已使用 NuGet，它会很熟悉。
    
    > [!WARNING]
    > 很重要的命名正确。请确保它**不具有.txt**文件扩展名。 有关参考，请参阅以下内容：
    >
    > ![保存的 JSON](images/AzureLabs-Lab313-52.png)

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

4.  后记录，单击**创建资源**在左上角，并搜索**Function App**，然后按**Enter**键，搜索。 单击*Function App*从结果中，打开一个新的面板。

    ![搜索函数应用](images/AzureLabs-Lab313-53.png)

5.  新的面板将提供的说明**Function App**服务。 在左下角此面板中，单击**创建**按钮，以创建与此关联服务。

    ![function app 实例](images/AzureLabs-Lab313-54.png)

6.  一旦你单击**创建**，填写以下：

    1. 有关**应用名称**，插入此服务实例所需的名称。

    2. 选择**订阅**。

    3. 选择定价层适合你，如果这是首次创建**Function App 服务**，应可供你免费层。

    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配，以及管理 Azure 资产的集合计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

        > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 有关**OS**，单击 Windows，因为这是预期的平台。

    6. 选择**托管计划**(使用本教程**消耗计划**。

    7. 选择**位置**（上一步中选择与已生成的存储相同的位置）

    8. 有关**存储**部分中，**必须选择在上一步中创建的存储服务**。

    9. 您不需要*Application Insights*在此应用中，所以请随意将其留**关闭**。

    10. 单击“创建”  。

        ![创建新的实例](images/AzureLabs-Lab313-55.png)

7.  一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。

8.  创建服务实例后，在门户中将显示一条通知。

    ![新的通知](images/AzureLabs-Lab313-56.png)

9.  部署成功后单击该通知 （已完成）。

10. 单击**转到资源**通知探索新的服务实例中的按钮。 

    ![转到资源](images/AzureLabs-Lab313-57.png)

11. 在左侧和右侧的新面板，单击 **+** （加号） 旁边的图标*函数*，以创建新的函数。

    ![添加新函数](images/AzureLabs-Lab313-58.png)

12. 在中间面板**函数**创建窗口将显示。 此外，向下滚动并单击**自定义函数**。

    ![自定义函数](images/AzureLabs-Lab313-59.png)

13. 下一个页面，直到找到中向下的滚动**IoT 中心 （事件中心）** ，然后单击它。

    ![自定义函数](images/AzureLabs-Lab313-60.png)

14. 在中**IoT 中心 （事件中心）** 边栏选项卡，将**语言**到**C#** ，然后单击**新**。

    ![自定义函数](images/AzureLabs-Lab313-61.png)

15. 在窗口中将出现，请确保**IoT 中心**处于选中状态和名称*IoT 中心*字段对应的名称与你*IoT 中心服务*必须以前创建 ([在步骤 8 的第 3 章](#chapter-3---the-iot-hub-service))。 然后单击**选择**按钮。

    ![自定义函数](images/AzureLabs-Lab313-62.png)

16. 重新**IoT 中心 （事件中心）** 边栏选项卡上，单击**创建**。

    ![自定义函数](images/AzureLabs-Lab313-63.png)

17. 你将重定向到在函数编辑器。

    ![自定义函数](images/AzureLabs-Lab313-64.png)

18. 删除在其中的所有代码并使用以下代码替换它：

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

19. 更改以下变量，以便它们对应于相应的值 (**表**并**存储**值，从[步骤 11 到 13，分别，第 11 章](#chapter-11---create-table-service))，将在中找到你**存储帐户**:

    - **tableName**，名称为你**表**位于你**存储帐户**。
    - **tableURL**，url 为你**表**位于你**存储帐户**。
    - **storageAccountName**，具有的名称相对应的值的名称与你**存储帐户**名称。
    - **storageAccountKey**，已在具有以前创建的存储服务中获取的密钥。

    ![自定义函数](images/AzureLabs-Lab313-65.png)

20. 使用的代码中的位置，单击**保存**。

21. 接下来，单击 **\<** （箭头） 图标，在页面的右侧。

    ![自定义函数](images/AzureLabs-Lab313-66.png)

22. 一个面板，将从右侧滑中。 在该面板中，单击**上传**，和一个*文件浏览器*将出现。

23. 导航到，然后单击， **project.json**中创建的文件**记事本**以前，然后单击**打开**按钮。 此文件定义函数将使用的库。

    ![自定义函数](images/AzureLabs-Lab313-67.png)

24. 当完成上传文件时，它会在右侧面板中显示。 单击它即可打开它内**函数**编辑器。 它必须看起来**完全**的下一步的映像相同。

    ![自定义函数](images/AzureLabs-Lab313-68.png)

25. 现在那会很不错，若要测试你的函数的功能，若要将该消息存储在你*表*。 在窗口右上角，单击**测试**。

    ![自定义函数](images/AzureLabs-Lab313-69.png)

26. 插入一条消息上**请求正文**，在上图中的，然后单击中所示**运行**。 

27. 该函数将运行，并显示结果状态 (您将注意到绿色**状态 202 已接受**上面*输出*窗口中，这意味着它已成功调用):

    ![输出结果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第 14 章 — 查看活动消息

如果现在打开 Visual Studio (**不**Visual Studio Code)，可以可视化您测试的消息结果，因为它将存储在*MessageContent*区域的字符串。

![自定义函数](images/AzureLabs-Lab313-71.png)

使用表服务和 Function App 中的位置，在 Ubuntu 设备的消息将出现在你*IoTMessages*表。 如果尚未运行，再次启动你的设备，您将能够看到的结果消息从设备和模块，在表中，使用 Visual Studio*云资源管理器*。

![实现数据可视化效果](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第 15 章-Power BI 安装程序

若要从 IOT 设备将在安装程序将数据可视化**Power BI** （桌面版），以收集数据的*表*刚创建的服务。 *HoloLens*版本的 Power BI 然后会使用该数据的结果可视化。

1.  打开 Windows 10 上的 Microsoft Store 并搜索**Power BI Desktop**。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  下载应用程序。 完成下载后，请将其打开。

3.  登录到*Power BI*与你**Microsoft 365 帐户**。 你可能会重定向到浏览器中，若要注册。 一旦您注册了，请返回到 Power BI 应用，并再次登录。

4.  单击**获取数据**，然后单击**更多...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  单击**Azure**， **Azure 表存储**，然后单击**Connect**。

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  系统会提示要插入**表 URL**先前收集的 ([在步骤 13 第 11 章](#chapter-11---create-table-service))，创建表服务时。 插入 URL 后, 删除引用表"子文件夹"（这是 IoTMessages，本课程中） 的路径的一部分。 最终结果应如下图中所示。 然后单击**确定**。

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  系统会提示要插入**存储密钥**记下 ([在第 11 章第 11 步](#chapter-11---create-table-service)) 早期创建在表存储时。 然后单击**Connect**。

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. 一个**导航器面板**将显示，选中你的表旁边的框，然后单击**负载**。

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. 现在在 Power BI 上加载您的表，但它需要一个查询来显示中它的值。 为此，请右键单击表名称中位于**字段面板**在屏幕的右侧。 然后单击**编辑查询**。

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. 一个**Power Query 编辑器**以显示您的表的新窗口将打开。 单击单词**记录**内*内容*表，可视化存储的内容的列。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. 单击**Into 表**，在窗口的左上方。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. 单击**关闭并应用**。

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 在加载查询，完成**字段面板**，在屏幕的右侧，勾选对应参数的框**名称**并**值**到可视化**MessageContent**列的内容。

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. 单击**蓝色磁盘图标**在左上角的窗口在所选的文件夹中保存工作。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. 现在可以单击发布按钮以将您的表上传到你的工作区。 出现提示时，单击**我的工作区**然后单击*选择*。 等待显示成功提交的结果。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 以下章节都是特定的 HoloLens。 Power BI 当前不提供为沉浸式应用程序，但可以在 Windows 混合现实门户 （也称为 Cliff 房屋） 中运行的桌面版本通过桌面应用程序。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>第 16 章 — 在 HoloLens 上显示 Power BI 数据

1. 在你 HoloLens 登录**Microsoft Store**，通过点击应用程序列表中对应的图标。

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. 搜索，然后下载**Power BI**应用程序。

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. 启动**Power BI**从您的应用程序的列表。 

4. **Power BI**可能会要求你登录到你**Microsoft 365 帐户**。

5. 一次在应用程序，在工作区应显示默认情况下下, 图中所示。 如果不会发生，只需单击窗口左侧的工作区图标。

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>在完成 IoT 中心应用程序

祝贺您，您已成功创建 IoT 中心服务，使用模拟的虚拟机 Edge 设备。 你的设备可以进行通信机器学习模型到 Azure 表服务，利用 Azure Function App，这是读取到 Power BI，Microsoft HoloLens 中可视化的结果。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

展开表中存储的消息传递结构并将其显示为图形。 你可能想要收集更多数据并将其存储在同一个表，以更高版本显示。

### <a name="exercise-2"></a>练习 2

创建一个附加"相机捕捉"模块来部署 IoT 板上，以便它可以捕获映像通过摄像机来对其进行分析。
