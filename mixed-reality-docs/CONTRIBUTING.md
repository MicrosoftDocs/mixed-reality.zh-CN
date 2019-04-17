---
title: 相关说明
description: 如何参与编辑 Windows Mixed Reality 文档。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592978"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>参与撰写 Windows Mixed Reality 开发人员文档

欢迎来到[Windows Mixed Reality 开发者文档的公共存储库](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)！ 创建或编辑此存储库中的所有文章**将对公共可见。** 

Docs.microsoft.com 平台，其中使用 GitHub 风格的 Markdown （附有 Markdig 功能） 上现提供 Windows Mixed Reality 文档。 实质上，获取在此存储库中编辑的内容转换为在显示的格式和风格化页 https://docs.microsoft.com/windows/mixed-reality。 

此页介绍了基本步骤和指导原则的参与，以及链接到 Markdown 基础知识。 感谢您参与您的发布内容 ！

## <a name="before-you-start"></a>开始之前

如果你还没有一个，将需要[创建一个 GitHub 帐户](https://github.com/join)。

>[!NOTE]
>如果你是 Microsoft 员工，在链接到您的 Microsoft 别名 GitHub 帐户[Microsoft 开放源门户](https://repos.opensource.microsoft.com/)。 加入 **"Microsoft"** 并 **"MicrosoftDocs"** 组织)。

当设置 GitHub 帐户，我们还建议这些安全预防措施：
- 创建[Github 帐户的强密码](https://github.com/settings/admin)。
- 启用[双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。
- 保存你[恢复代码](https://github.com/settings/auth/recovery-codes)在安全的位置。
- 更新你[公用配置文件设置](https://github.com/settings/profile)。
   - 设置你的名称，并设置，请考虑你*公用电子邮件*到*不再显示我的电子邮件地址*。
   - 我们建议上传个人资料图片，因为参与的 docs 页面上会显示在缩略图。
- 如果你打算使用命令行工作流，请考虑设置[Git 凭据管理器的 Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) ，因此无需每次都输入密码进行了贡献。

执行这些步骤非常重要，因为发布系统已绑定到 GitHub，你将列为作者或参与者使用 GitHub 别名每篇文章。

## <a name="editing-an-existing-article"></a>编辑现有项目

使用以下工作流来更新到*现有项目*通过 web 浏览器中的 GitHub:

1. 导航到想要编辑的"混合现实-文档"文件夹中的文章。
2. 在右上角选择编辑按钮 （铅笔图标）。 这将自动创建分支的主分支的可释放的分支。

   ![编辑文章。](images/editpage.png)
3. 编辑文章的内容 (请参阅["Markdown 基础知识"](#markdown-basics)下面的指南)。
4. 更新相关的每篇文章顶部的元数据：
   * 标题：这是正在查看项目时，将显示在浏览器选项卡中的页面标题。 因为这用于 SEO 和编制索引，您不应更改标题，除非必要的 （尽管这是不太重要，文档进入公共之前）。
   * 说明：编写文章的内容的简短说明。 这有助于 SEO 和发现。
   * 作者：如果你是主要所有者页上的，添加你的 GitHub 别名。
   * ms.author:如果你是主要所有者页上的，添加你的 Microsoft 别名此处 (不需要@microsoft.com，只需别名)。
   * ms.date:如果要将主要内容添加至页上，但不是说明，格式设置、 语法，如修补程序或拼写检查，更新的日期。
   * 关键字：SEO （搜索引擎优化） 可帮助关键字。 添加关键字，由一个逗号和空格分隔的特定于您的文章 （但没有在列表中的最后一个关键字之后的标点符号）;您不必添加适用于所有项目的全局关键字，如那些在其他地方进行管理。 
5. 完成你文章的编辑后，向下滚动并单击**建议文件更改**按钮。
6. 在下一页上，单击**创建拉取请求**要将你自动创建的分支合并到 master。
7. 下一步想要编辑的项目重复上述步骤。

## <a name="creating-a-new-article"></a>创建新文章

使用以下工作流*创建新文章*通过 GitHub 文档存储库中的 web 浏览器中：

1. 创建分叉的 MicrosoftDocs/混合现实 master 分支 (使用**分叉**在右上角的按钮)。

   ![创建分支的主分支。](images/forkbranch.png)
2. 在"混合现实-文档"文件夹中，单击**创建新文件**在右上角的按钮。
3. 创建项目的页名称 （而不是空格使用连字符和标点符号或撇号不使用） 和追加".md"

   ![命名您的新页面。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >请确保创建了新的文章，可从"混合现实-文档"文件夹中。 你可以通过检查来确认这一点"混合现实 docs /"的新的文件名称行中。

4. 在新页的顶部，添加以下元数据块：

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. 填写相关的元数据字段中的说明每[上面部分](#editing-an-existing-article)。
6. 写文章内容使用[Markdown 基础知识](#markdown-basics)。
7. 添加`## See also`部分包含指向其他相关文章文章的底部。
8. 完成后，单击**提交新的文件**。
9. 单击**新的拉取请求**和分支的主分支合并到 MicrosoftDocs/混合现实 master （请确保箭头指向正确的方式）。

   ![到 MicrosoftDocs/混合现实从分叉创建拉取请求](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown 基础知识

以下资源将帮助您了解如何编辑使用 Markdown 语言的文档：

- [Markdown 基础知识](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown 在快速参考海报](images/MarkdownPoster.pdf)
- [有关编写针对 docs.microsoft.com 的 Markdown 的其他资源](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>添加表

由于方式 docs.microsoft.com 样式表，它们不会有边框或自定义样式，即使尝试内联 CSS。 它看起来工作一小段时间，但该平台将最终剥离出表样式。 因此提前计划并简化你的表。 [此处是一个站点，Markdown 表可以轻松](http://www.tablesgenerator.com/markdown_tables)。

[针对 Visual Studio Code 的 Docs Markdown 扩展](https://docs.microsoft.com/teamblog/docs-extension)还使表生成简单，如果您使用的[Visual Studio Code （见下文）](#using-visual-studio-code)编辑文档。

### <a name="adding-images"></a>添加图像

你将需要将映像上传到该存储库中的"混合的现实的 docs/images"文件夹，然后在文章中适当地引用它们。 映像会自动显示在原尺寸，这意味着如果你的映像很大，它将填充整个项目的宽度。 因此，我们建议将其上传之前预调整你的映像。 建议的宽度是 600 和 700 像素之间，尽管它分别是密集的屏幕快照或一小部分的屏幕截图中，应大小向上或向下。

>[!IMPORTANT]
>在合并之前，您可以仅将图像上载到分叉的存储库。 因此，如果您计划将映像添加到项目，您将需要[使用 Visual Studio Code](#using-visual-studio-code)首先将映像添加到分支的"images"文件夹，或确保所做的 web 浏览器中的以下：
>
>1. 分叉 MicrosoftDocs/混合现实存储库。
>2. 编辑在分支中的文章。
>3. 上传您的文章"混合的现实的 docs/images"文件夹中引用在分支中的映像。
>4. 创建**拉取请求**要合并到 MicrosoftDocs/混合现实 master 分支的分支。
>
>若要了解如何设置分叉存储库，请按照的说明进行操作[创建新文章](#creating-a-new-article)。

## <a name="previewing-your-work"></a>预览所做的工作

在 GitHub 中编辑时通过 web 浏览器，可以单击**预览版**页后，可以预览所做的工作之前提交的顶部附近的选项卡。 

>[!NOTE]
>预览 review.docs.microsoft.com 上所做的更改是仅供 Microsoft 员工

Microsoft 员工： 一旦您的发布内容已合并为主分支，可以看到之前将它放在公共文档外观 https://review.docs.microsoft.com/windows/mixed-reality?branch=master（找到您在左侧列中使用的目录的文章）。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>与使用桌面客户端进行编辑浏览器中编辑

在浏览器中编辑是最简单的方法进行快速更改，但是，有几个缺点：

- 别让拼写检查。
- 别让任何智能-将链接到 （您需要手动键入文章的文件名） 的其他文章。
- 它可以是一个麻烦上, 传和引用图像。

如果您将相当不处理这些问题，您可能更愿意使用桌面客户端，如[Visual Studio Code](https://code.visualstudio.com/)需单击几次[有用的扩展](#useful-extensions)来参与编辑文档。

## <a name="using-visual-studio-code"></a>使用 Visual Studio Code

由于原因列出[上面](#editing-in-the-browser-vs-editing-with-a-desktop-client)，您可能更喜欢使用桌面客户端编辑而不是 web 浏览器的文档。 我们建议使用[Visual Studio Code](https://code.visualstudio.com/)。

### <a name="setup"></a>安装

请执行以下步骤来配置 Visual Studio 代码，以使用此存储库：

1. 在 web 浏览器中：
    1. 安装[适用于您的 PC 的 Git](https://git-scm.com/downloads)。
    2. 安装[Visual Studio Code](https://code.visualstudio.com/)。
    3. [创建分支 MicrosoftDocs/混合现实](#creating-a-new-article)如果尚未准备好。
    4. 中的分支，请单击**克隆或下载**并复制 URL。
2. 在 Visual Studio Code 中创建分支的本地克隆：
    1. 从**视图**菜单中，选择**命令面板**。
    2. 类型"Git:Clone。"
    3. 粘贴刚刚复制的 URL。
    4. 选择你的 PC 上保存克隆的位置。
    5. 单击**打开存储库**在弹出窗口中。

### <a name="editing-documentation"></a>编辑文档

使用以下工作流使用 Visual Studio Code 文档进行更改：

>[!NOTE]
>所有的指南[编辑](#editing-an-existing-article)和[创建](#creating-a-new-article)文章，并[的编辑 Markdown 基础知识](#markdown-basics)，上述适用于使用 Visual Studio Code 还时。

1. 请确保在克隆的分支是最新的与官方存储库。
   1. 在 web 浏览器中创建同步最新更改从其他参与者都 MicrosoftDocs/混合现实 master 分支的拉取请求 （请确保箭头指向正确的方式）。
      
      ![将从 MicrosoftDocs/混合现实的更改同步到分支](images/sync_repos.PNG)
   2. 在 Visual Studio Code 中，单击同步按钮以同步新更新将分支与本地克隆。
      
      ![单击同步按钮](images/sync_clone.png)
2. 创建或编辑使用 Visual Studio Code 在克隆存储库中的文章。
   1. 编辑一个或多个项目 （将映像添加到"图片"文件夹如有必要）。
   2. **保存**中的更改**资源管理器**。
      
      ![在资源管理器中选择"全部保存"](images/explorer_save.png)
   3. **全部提交**中的更改**源代码管理**（写入提交消息出现提示时）。
      
      ![选择"全部提交"在源代码管理中](images/source_control_commit.png)
   4. 单击**同步**同步所做的更改回源 （在 GitHub 上的分支） 按钮。
      
      ![单击同步按钮](images/sync_back.png)
3. 在 web 浏览器中创建同步回 MicrosoftDocs/混合现实 master 分支中的新更改的拉取请求 （请确保箭头指向正确的方式）。

   ![到 MicrosoftDocs/混合现实从分叉创建拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>有用的扩展

编辑文档时，以下 Visual Studio Code 扩展是非常有用：

- [Visual Studio Code 的 docs Markdown 扩展](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)-使用**Alt + M**弹出的 docs 创作选项，如菜单：
   - 已上载的搜索和参考映像。
   - 添加格式设置等列表、 表和特定于文档的标注喜欢`>[!NOTE]`。
   - 搜索并引用内部链接和书签 （在页面内的特定部分的链接）。
   - 格式错误将突出显示 （请将鼠标悬停在错误以了解详细信息）。
- [拼写检查器的代码](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼错的单词将带有下划线; 右键单击拼错的单词，若要对其进行更改或将其保存到字典。
