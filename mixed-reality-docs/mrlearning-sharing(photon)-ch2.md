# <a name="getting-unity-ready-for-development"></a>让 Unity 开发做好准备 

在本教程中，我们将了解如何准备和配置 Unity 应用程序开发，包括导入混合现实工具包、 配置生成设置和准备场景。

目标：

- 配置 Unity 应用程序开发

- 导入混合现实工具包

- 准备项目场景

### <a name="instructions"></a>说明

1. 下载并保存混合现实工具包 unity 包，通过单击[此处。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. 在 Unity 中，单击资产菜单，选择导入包，然后单击自定义包。

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 选择您刚从在步骤 1 中提供的链接下载 Unity 包。 导入弹出窗口出现后在 Unity 中，单击导入按钮以开始导入。 导入 MRTK 可能需要几分钟。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注意：下载的包是在你保存文件的本地文件夹中。 上图没有描绘出将在何处找到程序包。

4. 创建新的场景。 此可通过单击文件，并选择新的场景"）。 将场景另存为 HLSharedProjectMain。

> 注意： 可能会收到一个弹出窗口，它看起来类似于下图所示。 现在，请单击不可以。
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 在混合现实工具包，单击添加到场景和配置。

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成后完成后，新的配置文件会出现，让您自定义配置文件的选择。 单击复制和自定义。

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 向下滚动并取消选中启用 Siagnostics 系统，如果你想要隐藏诊断窗口。 我们建议保持诊断窗口启用应用程序开发期间来监视性能，并在生产环境或应用程序演示期间禁用它。 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. 打开通过按 control + shift + B 或转到文件的生成设置-> 生成设置。 请注意，该程序当前设置在 PC、 Mac 和 Linux 独立平台。 对于 HoloLens 2 开发，设置要为通用 Windows 平台的平台。 选择它，然后单击切换平台。![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完成后，单击添加打开场景框。 现在转到检查器面板中，并确保选中该复选框右侧的虚拟现实支持 （如下图所示）。 此外确保场景/HLSharedProjectMain 旁边的复选框还选中下图中所示。![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 在检查器面板中的发布设置部分中，向下滚动到功能，并确保标记下面的复选框：![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 导入自定义包调用可以在下载 SharingAssetCollection[此处。](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 在项目面板中，转到置入 Prefabs 文件夹。 在下一步的几个步骤中，您将实现向场景的几个预设。 中置入 Prefabs 文件夹中，单击并拖动预设可 DebugWindow 到层次结构。 完成后，将项目保存由 clckin 文件，然后保存或按控件 + S。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注意：您可能注意到一个弹出窗口，显示当您单击预设可，询问您 TMP Essentials。 单击导入 TMP Essentials，因为需要它们。 如果此弹出窗口，您可能需要删除预设可从你的层次结构并重新将其拖到层次结构，以避免潜在与文本相关的错误。
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>祝贺

你的 Unity 项目现已准备好 Photon。 在接下来的教程中，我们将在此场景和我们的 Unity 项目针对完整的共享体验为基础进行构建。

[下一教程：将多个用户连接](mrlearning-sharing(photon)-ch3.md)

