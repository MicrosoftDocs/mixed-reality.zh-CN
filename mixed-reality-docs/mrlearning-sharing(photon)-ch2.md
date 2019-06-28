**让 Unity 开发做好准备** 

在本课程中，我们将学习如何准备和配置 Unity 应用程序开发，包括导入混合现实工具包、 配置生成设置和准备场景。

目标：

- 配置 Unity 应用程序开发

- 导入混合现实工具包

- 准备项目场景

### <a name="instructions"></a>说明

1. 下载并保存混合现实工具包 unity 包，通过单击[此处。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. 在 Unity 中，单击资产菜单选择"导入包"，然后单击"自定义包"。

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 选择您刚从在步骤 1 中提供的链接下载 Unity 包。 导入弹出窗口出现后在 Unity 中，单击导入按钮以开始导入。 导入 MRTK 可能需要几分钟。

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> 注意：下载的包将文件保存在本地文件夹中。 上图没有描绘出将在何处找到程序包。

4. 创建新的场景 （这可以通过单击"文件"并选择"新的场景"）。 将场景另存为"HLSharedProjectMain。"

> 注意： 可能会收到一个弹出窗口，它看起来类似于下图所示。 现在，只需单击"否"。
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. 在"混合现实 Toolkit"单击"将添加到场景和配置"。

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. 完成后完成后，新的配置文件将出现，让您选择自定义配置文件。 单击"复制和自定义"。

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. 向下滚动并取消选中"启用诊断系统"是否你想要隐藏诊断窗口。 我们建议保持诊断窗口启用应用程序开发过程来监视性能，并在生产环境或应用程序演示期间禁用它。 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. 通过按 control + shift + B 或转到文件中打开生成设置 > 生成设置。 请注意，该程序当前在"电脑、 Mac 和 Linux 独立"平台设置。 HoloLens 2 开发，将平台设置为"通用 Windows 平台。" 选择它，然后单击"切换平台"。![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. 完成后，单击框，其中显示"添加打开的场景。 现在请转到检查器面板，并确保右侧的"支持的虚拟现实"复选框 （如在下图中所示） 已选中。 此外确保也选中"场景/HLSharedProjectMain"旁边的复选框，如下图中所示。![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. 在"发布设置"部分中检查器面板中向下滚动到"功能"，并确保标记下面的复选框：![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. 导入名为"SharingAssetCollection"可以下载自定义软件包[此处。](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. 现在，在项目面板中，转到"预设"文件夹，因为下一步的几个步骤中您将执行向场景的几个预设。 在"预设"文件夹中，单击并拖动预设可在层次结构"DebugWindow"。 完成后，保存项目 （单击文件，然后保存，或按 control + S）

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > 注意：您可能注意到一个弹出窗口，显示当您单击预设可，询问您 TMP Essentials。 单击"导入 TMP Essentials"，因为将需要它们。 如果此弹出窗口，您可能需要删除预设可从你的层次结构并重新将其拖到层次结构，以避免潜在与文本相关的错误。
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>祝贺

你的 Unity 项目现已准备好 Photon ！ 在接下来的课程中，我们将在此场景和我们的 Unity 项目针对完整的共享体验为基础进行构建。

[下一课：第 3 课 Sharing(Photon)](mrlearning-sharing(photon)-ch3.md)

