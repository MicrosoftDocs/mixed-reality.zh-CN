---
title: 参与说明
description: 如何参与 Windows 混合现实文档。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516239"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>参与 Windows Mixed Reality 开发人员文档

欢迎使用[适用于 Windows Mixed Reality 开发人员文档的公共](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)存储库! 在此存储库中创建或编辑的任何项目**都将对公共可见。** 

Windows Mixed Reality 文档现在位于 docs.microsoft.com 平台, 该平台使用 GitHub 风格 Markdown (带有 Markdig 功能)。 实质上, 在此存储库中编辑的内容会转换为显示在 https://docs.microsoft.com/windows/mixed-reality 中的已设置格式和样式的页面。 

此页介绍了用于参与的基本步骤和准则, 以及指向 Markdown 基础知识的链接。 感谢您的参与!

## <a name="before-you-start"></a>开始之前

如果还没有, 则需要[创建一个 GitHub 帐户](https://github.com/join)。

>[!NOTE]
>如果你是 Microsoft 员工, 请将你的 GitHub 帐户链接到[Microsoft 开源门户](https://repos.opensource.microsoft.com/)上的 microsoft 别名。 加入 **"Microsoft"** 和 **"MicrosoftDocs"** 组织。

设置 GitHub 帐户时, 我们还建议采用以下安全预防措施:
- [为 Github 帐户创建强密码](https://github.com/settings/admin)。
- 启用[双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。
- 将[恢复代码](https://github.com/settings/auth/recovery-codes)保存在安全的位置。
- 更新[公用配置文件设置](https://github.com/settings/profile)。
   - 设置你的名称, 并考虑将你的*公用电子邮件*设置为*不显示我的电子邮件地址*。
   - 建议你上载个人资料图片, 因为缩略图会显示在你所参与的文档页面上。
- 如果计划使用命令行工作流, 请考虑设置[适用于 Windows 的 Git 凭据管理器](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest), 这样, 每次发布时都无需输入密码。

执行这些步骤非常重要, 因为发布系统与 GitHub 相关, 你将使用 GitHub 别名作为每篇文章的作者或参与者列出。

## <a name="editing-an-existing-article"></a>编辑现有项目

使用以下工作流, 在 web 浏览器中通过 GitHub 对*现有文章*进行更新:

1. 导航到要在 "混合现实-文档" 文件夹中编辑的项目。
2. 选择右上方的 "编辑" 按钮 (铅笔图标)。 这会自动从 "master" 分支中派生出可释放分支。

   ![编辑项目。](images/editpage.png)
3. 编辑项目的内容 (有关指导, 请参阅下面的["Markdown 基本信息"](#markdown-basics) )。
4. 更新每个项目顶部相关的元数据:
   * 词首这是查看项目时浏览器选项卡中显示的页面标题。 由于此用于 SEO 和编制索引, 因此除非有必要, 否则不应更改标题 (不过, 在文档公开之前这并不重要)。
   * 2008编写文章内容的简短说明。 这项辅助功能和发现。
   * 主持如果你是页面的主所有者, 请在此处添加你的 GitHub 别名。
   * 女士:如果你是页面的主所有者, 请在此处添加你的 Microsoft 别名 (你不@microsoft.com需要, 只需别名)。
   * ms. 日期:如果要向页面中添加主要内容, 而不是对修补程序 (如说明、格式、语法或拼写) 添加主要内容, 请更新日期。
   * 字SEO 中的关键字帮助 (搜索引擎优化)。 添加特定于您的项目的关键字 (以逗号和空格分隔), 而不是列表中最后一个关键字后面的任何标点);无需添加适用于所有项目的全局关键字, 因为在其他位置托管这些项目。 
5. 完成文章编辑后, 向下滚动并单击 "**建议文件更改**" 按钮。
6. 在下一页上, 单击 "**创建拉取请求**" 将自动创建的分支合并到 "master"。
7. 对于要编辑的下一篇文章, 请重复上述步骤。

## <a name="creating-a-new-article"></a>创建新项目

使用以下工作流在 web 浏览器中通过 GitHub 在文档存储库中*创建新项目*:

1. 使用右上方的 "**分叉**" 按钮, 创建 MicrosoftDocs/mixed reality "master" 分支的分叉。

   ![将主分支分叉。](images/forkbranch.png)
2. 在 "混合现实文档" 文件夹中, 单击右上方的 "**创建新文件**" 按钮。
3. 为项目创建页名称 (使用连字符而不是空格, 不要使用标点符号或撇号) 并追加 "md"

   ![命名新页。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >请确保在 "mixed reality-文档" 文件夹中创建新项目。 可以通过在 "新文件名" 行中检查 "/mixed-reality-docs/" 来确认这一点。

4. 在新页的顶部, 添加以下元数据块:

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

5. 按照[以上部分](#editing-an-existing-article)中的说明填写相关的元数据字段。
6. 使用[Markdown 基础知识](#markdown-basics)编写文章内容。
7. 在文章`## See also`底部添加一个部分, 其中包含指向其他相关文章的链接。
8. 完成后, 单击 "**提交新文件**"。
9. 单击 "**新建拉取请求**", 并将分叉的 "master" 分支合并到 MicrosoftDocs/mixed reality "master" 中 (确保箭头的方向正确)。

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown 基础知识

以下资源将帮助你了解如何使用 Markdown 语言编辑文档:

- [Markdown 基础知识](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [一览式参考海报 Markdown](images/MarkdownPoster.pdf)
- [用于编写 docs.microsoft.com 的 Markdown 的其他资源](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>添加表

由于 docs.microsoft.com 样式表的方式, 它们没有边框或自定义样式, 即使您尝试使用内联 CSS 也是如此。 它看起来可以正常工作, 但最终平台会去除表的样式。 因此请提前规划并使表保持简单。 [下面是使 Markdown 表变得简单的站点](http://www.tablesgenerator.com/markdown_tables)。

如果你使用[Visual Studio Code (见下文)](#using-visual-studio-code)来编辑文档, 则[用于 Visual Studio Code 的文档 Markdown 扩展](https://docs.microsoft.com/teamblog/docs-extension)还可以简化表的生成。

### <a name="adding-images"></a>添加图像

需要将映像上传到存储库中的 "混合现实文档/映像" 文件夹, 并在文章中对它们进行相应的引用。 图像将自动以全尺寸显示, 这意味着, 如果图像很大, 则会填充整个文章的宽度。 因此, 建议在上传映像之前对其进行预先调整大小。 建议宽度介于600到700像素之间, 不过, 如果它是密集屏幕截图或屏幕截图的小部分, 则应调整大小。

>[!IMPORTANT]
>在合并前, 只能将图像上传到分叉存储库。 因此, 如果你计划将图像添加到项目中, 则需要先[使用 Visual Studio Code](#using-visual-studio-code)将图像添加到分叉的 "images" 文件夹, 或者确保已在 web 浏览器中完成以下操作:
>
>1. 分叉 MicrosoftDocs/mixed reality 存储库。
>2. 已编辑分叉中的项目。
>3. 将你在项目中引用的映像上传到你的分支中的 "混合现实文档/映像" 文件夹。
>4. 创建了用于将分叉合并到 MicrosoftDocs/mixed reality "master" 分支的**拉取请求**。
>
>若要了解如何设置自己的分叉存储库, 请按照[创建新文章](#creating-a-new-article)的说明进行操作。

## <a name="previewing-your-work"></a>预览工作

通过 web 浏览器在 GitHub 中进行编辑时, 可以单击页面顶部附近的 "**预览**" 选项卡来预览你的工作, 然后再提交。 

>[!NOTE]
>在 review.docs.microsoft.com 上预览所做的更改仅适用于 Microsoft 员工

Microsoft 员工: 一旦你的贡献合并到 "master" 分支中, 你就可以在 https://review.docs.microsoft.com/windows/mixed-reality?branch=master 公开之前查看文档的外观 (使用左栏中的目录查找文章)。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>在浏览器中编辑与使用桌面客户端进行编辑

在浏览器中进行编辑是进行快速更改的最简单方法, 但有几个缺点:

- 不会进行拼写检查。
- 您不会获得任何智能链接到其他文章 (您必须手动键入项目的文件名)。
- 这可能是上传和引用图像的麻烦。

如果你不想处理这些问题, 你可能更愿意使用桌面客户端 (如[Visual Studio Code](https://code.visualstudio.com/) ), 其中包含一些[有用的扩展](#useful-extensions), 可用于文档。

## <a name="using-visual-studio-code"></a>使用 Visual Studio Code

出于[上面](#editing-in-the-browser-vs-editing-with-a-desktop-client)列出的原因, 您可能更倾向于使用桌面客户端编辑文档而不是 web 浏览器。 建议使用[Visual Studio Code](https://code.visualstudio.com/)。

### <a name="setup"></a>安装

请按照以下步骤配置 Visual Studio Code 以使用此存储库:

1. 在 web 浏览器中:
    1. 安装[适用于你的电脑的 Git](https://git-scm.com/downloads)。
    2. 安装[Visual Studio Code](https://code.visualstudio.com/)。
    3. [分叉 MicrosoftDocs/混合现实 (](#creating-a-new-article)如果尚未这样做)。
    4. 在你的分支中, 单击 "**克隆" 或下载**并复制 URL。
2. 在 Visual Studio Code 中创建分叉的本地复本:
    1. 从 "**视图**" 菜单中选择 "**命令面板**"。
    2. 键入 "Git: Clone"。
    3. 粘贴刚才复制的 URL。
    4. 选择要在电脑上保存克隆的位置。
    5. 在弹出窗口中单击 "**打开**存储库"。

### <a name="editing-documentation"></a>编辑文档

使用以下工作流, 通过 Visual Studio Code 对文档进行更改:

>[!NOTE]
>在使用 Visual Studio Code 时, 所有有关[编辑](#editing-an-existing-article)和[创建](#creating-a-new-article)文章的指南以及[编辑 Markdown 的基础知识](#markdown-basics)也适用。

1. 请确保你的克隆分叉与官方存储库保持最新。
   1. 在 web 浏览器中, 创建一个拉取请求, 将最近的更改从 MicrosoftDocs/mixed reality "master" 中的其他参与者同步到分叉 (确保箭头指向正确的方式)。
      
      ![将更改从 MicrosoftDocs/混合事实同步到你的分支](images/sync_repos.PNG)
   2. 在 Visual Studio Code 中, 单击 "同步" 按钮, 将最新更新的分支同步到本地克隆。
      
      ![单击 "同步" 按钮](images/sync_clone.png)
2. 使用 Visual Studio Code 在克隆的存储库中创建或编辑项目。
   1. 编辑一个或多个项目 (如有必要, 将图像添加到 "images" 文件夹)。
   2. 在**资源管理器**中**保存**更改。
      
      ![在资源管理器中选择 "全部保存"](images/explorer_save.png)
   3. **提交** **源代码管理**中的所有更改 (在出现提示时写入提交消息)。
      
      ![在源代码管理中选择 "全部提交"](images/source_control_commit.png)
   4. 单击 "**同步**" 按钮, 将所做的更改同步回源 (GitHub 上的分支)。
      
      ![单击 "同步" 按钮](images/sync_back.png)
3. 在 web 浏览器中, 创建一个拉取请求, 以将分支中的新更改同步到 MicrosoftDocs/mixed reality "master" (确保箭头指向正确的方式)。

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>有用的扩展

编辑文档时, 以下 Visual Studio Code 扩展非常有用:

- [用于 Visual Studio Code 的文档 Markdown 扩展](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)-使用**Alt + M**显示文档创作选项的菜单, 如下所示:
   - 搜索和引用已上传的映像。
   - 添加格式 (如列表、表和文档`>[!NOTE]`)。
   - 搜索和引用内部链接和书签 (指向页面内特定部分的链接)。
   - 突出显示格式错误 (将鼠标悬停在错误上以了解详细信息)。
- [代码拼写检查器](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-将为拼写错误的单词加下划线。右键单击拼写错误的单词以对其进行更改或将其保存到字典中。
