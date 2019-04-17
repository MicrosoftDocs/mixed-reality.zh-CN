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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="dc75e-103">参与撰写 Windows Mixed Reality 开发人员文档</span><span class="sxs-lookup"><span data-stu-id="dc75e-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="dc75e-104">欢迎来到[Windows Mixed Reality 开发者文档的公共存储库](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)！</span><span class="sxs-lookup"><span data-stu-id="dc75e-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="dc75e-105">创建或编辑此存储库中的所有文章**将对公共可见。**</span><span class="sxs-lookup"><span data-stu-id="dc75e-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="dc75e-106">Docs.microsoft.com 平台，其中使用 GitHub 风格的 Markdown （附有 Markdig 功能） 上现提供 Windows Mixed Reality 文档。</span><span class="sxs-lookup"><span data-stu-id="dc75e-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="dc75e-107">实质上，获取在此存储库中编辑的内容转换为在显示的格式和风格化页 https://docs.microsoft.com/windows/mixed-reality。</span><span class="sxs-lookup"><span data-stu-id="dc75e-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="dc75e-108">此页介绍了基本步骤和指导原则的参与，以及链接到 Markdown 基础知识。</span><span class="sxs-lookup"><span data-stu-id="dc75e-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="dc75e-109">感谢您参与您的发布内容 ！</span><span class="sxs-lookup"><span data-stu-id="dc75e-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="dc75e-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="dc75e-110">Before you start</span></span>

<span data-ttu-id="dc75e-111">如果你还没有一个，将需要[创建一个 GitHub 帐户](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="dc75e-112">如果你是 Microsoft 员工，在链接到您的 Microsoft 别名 GitHub 帐户[Microsoft 开放源门户](https://repos.opensource.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="dc75e-113">加入 **"Microsoft"** 并 **"MicrosoftDocs"** 组织)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="dc75e-114">当设置 GitHub 帐户，我们还建议这些安全预防措施：</span><span class="sxs-lookup"><span data-stu-id="dc75e-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="dc75e-115">创建[Github 帐户的强密码](https://github.com/settings/admin)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="dc75e-116">启用[双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="dc75e-117">保存你[恢复代码](https://github.com/settings/auth/recovery-codes)在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="dc75e-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="dc75e-118">更新你[公用配置文件设置](https://github.com/settings/profile)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="dc75e-119">设置你的名称，并设置，请考虑你*公用电子邮件*到*不再显示我的电子邮件地址*。</span><span class="sxs-lookup"><span data-stu-id="dc75e-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="dc75e-120">我们建议上传个人资料图片，因为参与的 docs 页面上会显示在缩略图。</span><span class="sxs-lookup"><span data-stu-id="dc75e-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="dc75e-121">如果你打算使用命令行工作流，请考虑设置[Git 凭据管理器的 Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) ，因此无需每次都输入密码进行了贡献。</span><span class="sxs-lookup"><span data-stu-id="dc75e-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="dc75e-122">执行这些步骤非常重要，因为发布系统已绑定到 GitHub，你将列为作者或参与者使用 GitHub 别名每篇文章。</span><span class="sxs-lookup"><span data-stu-id="dc75e-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="dc75e-123">编辑现有项目</span><span class="sxs-lookup"><span data-stu-id="dc75e-123">Editing an existing article</span></span>

<span data-ttu-id="dc75e-124">使用以下工作流来更新到*现有项目*通过 web 浏览器中的 GitHub:</span><span class="sxs-lookup"><span data-stu-id="dc75e-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="dc75e-125">导航到想要编辑的"混合现实-文档"文件夹中的文章。</span><span class="sxs-lookup"><span data-stu-id="dc75e-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="dc75e-126">在右上角选择编辑按钮 （铅笔图标）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="dc75e-127">这将自动创建分支的主分支的可释放的分支。</span><span class="sxs-lookup"><span data-stu-id="dc75e-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![编辑文章。](images/editpage.png)
3. <span data-ttu-id="dc75e-129">编辑文章的内容 (请参阅["Markdown 基础知识"](#markdown-basics)下面的指南)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="dc75e-130">更新相关的每篇文章顶部的元数据：</span><span class="sxs-lookup"><span data-stu-id="dc75e-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="dc75e-131">标题：这是正在查看项目时，将显示在浏览器选项卡中的页面标题。</span><span class="sxs-lookup"><span data-stu-id="dc75e-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="dc75e-132">因为这用于 SEO 和编制索引，您不应更改标题，除非必要的 （尽管这是不太重要，文档进入公共之前）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="dc75e-133">说明：编写文章的内容的简短说明。</span><span class="sxs-lookup"><span data-stu-id="dc75e-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="dc75e-134">这有助于 SEO 和发现。</span><span class="sxs-lookup"><span data-stu-id="dc75e-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="dc75e-135">作者：如果你是主要所有者页上的，添加你的 GitHub 别名。</span><span class="sxs-lookup"><span data-stu-id="dc75e-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="dc75e-136">ms.author:如果你是主要所有者页上的，添加你的 Microsoft 别名此处 (不需要@microsoft.com，只需别名)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="dc75e-137">ms.date:如果要将主要内容添加至页上，但不是说明，格式设置、 语法，如修补程序或拼写检查，更新的日期。</span><span class="sxs-lookup"><span data-stu-id="dc75e-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="dc75e-138">关键字：SEO （搜索引擎优化） 可帮助关键字。</span><span class="sxs-lookup"><span data-stu-id="dc75e-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="dc75e-139">添加关键字，由一个逗号和空格分隔的特定于您的文章 （但没有在列表中的最后一个关键字之后的标点符号）;您不必添加适用于所有项目的全局关键字，如那些在其他地方进行管理。</span><span class="sxs-lookup"><span data-stu-id="dc75e-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="dc75e-140">完成你文章的编辑后，向下滚动并单击**建议文件更改**按钮。</span><span class="sxs-lookup"><span data-stu-id="dc75e-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="dc75e-141">在下一页上，单击**创建拉取请求**要将你自动创建的分支合并到 master。</span><span class="sxs-lookup"><span data-stu-id="dc75e-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="dc75e-142">下一步想要编辑的项目重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="dc75e-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="dc75e-143">创建新文章</span><span class="sxs-lookup"><span data-stu-id="dc75e-143">Creating a new article</span></span>

<span data-ttu-id="dc75e-144">使用以下工作流*创建新文章*通过 GitHub 文档存储库中的 web 浏览器中：</span><span class="sxs-lookup"><span data-stu-id="dc75e-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="dc75e-145">创建分叉的 MicrosoftDocs/混合现实 master 分支 (使用**分叉**在右上角的按钮)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![创建分支的主分支。](images/forkbranch.png)
2. <span data-ttu-id="dc75e-147">在"混合现实-文档"文件夹中，单击**创建新文件**在右上角的按钮。</span><span class="sxs-lookup"><span data-stu-id="dc75e-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="dc75e-148">创建项目的页名称 （而不是空格使用连字符和标点符号或撇号不使用） 和追加".md"</span><span class="sxs-lookup"><span data-stu-id="dc75e-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![命名您的新页面。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="dc75e-150">请确保创建了新的文章，可从"混合现实-文档"文件夹中。</span><span class="sxs-lookup"><span data-stu-id="dc75e-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="dc75e-151">你可以通过检查来确认这一点"混合现实 docs /"的新的文件名称行中。</span><span class="sxs-lookup"><span data-stu-id="dc75e-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="dc75e-152">在新页的顶部，添加以下元数据块：</span><span class="sxs-lookup"><span data-stu-id="dc75e-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="dc75e-153">填写相关的元数据字段中的说明每[上面部分](#editing-an-existing-article)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="dc75e-154">写文章内容使用[Markdown 基础知识](#markdown-basics)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="dc75e-155">添加`## See also`部分包含指向其他相关文章文章的底部。</span><span class="sxs-lookup"><span data-stu-id="dc75e-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="dc75e-156">完成后，单击**提交新的文件**。</span><span class="sxs-lookup"><span data-stu-id="dc75e-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="dc75e-157">单击**新的拉取请求**和分支的主分支合并到 MicrosoftDocs/混合现实 master （请确保箭头指向正确的方式）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![到 MicrosoftDocs/混合现实从分叉创建拉取请求](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="dc75e-159">Markdown 基础知识</span><span class="sxs-lookup"><span data-stu-id="dc75e-159">Markdown basics</span></span>

<span data-ttu-id="dc75e-160">以下资源将帮助您了解如何编辑使用 Markdown 语言的文档：</span><span class="sxs-lookup"><span data-stu-id="dc75e-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="dc75e-161">Markdown 基础知识</span><span class="sxs-lookup"><span data-stu-id="dc75e-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="dc75e-162">Markdown 在快速参考海报</span><span class="sxs-lookup"><span data-stu-id="dc75e-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="dc75e-163">有关编写针对 docs.microsoft.com 的 Markdown 的其他资源</span><span class="sxs-lookup"><span data-stu-id="dc75e-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="dc75e-164">添加表</span><span class="sxs-lookup"><span data-stu-id="dc75e-164">Adding tables</span></span>

<span data-ttu-id="dc75e-165">由于方式 docs.microsoft.com 样式表，它们不会有边框或自定义样式，即使尝试内联 CSS。</span><span class="sxs-lookup"><span data-stu-id="dc75e-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="dc75e-166">它看起来工作一小段时间，但该平台将最终剥离出表样式。</span><span class="sxs-lookup"><span data-stu-id="dc75e-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="dc75e-167">因此提前计划并简化你的表。</span><span class="sxs-lookup"><span data-stu-id="dc75e-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="dc75e-168">[此处是一个站点，Markdown 表可以轻松](http://www.tablesgenerator.com/markdown_tables)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="dc75e-169">[针对 Visual Studio Code 的 Docs Markdown 扩展](https://docs.microsoft.com/teamblog/docs-extension)还使表生成简单，如果您使用的[Visual Studio Code （见下文）](#using-visual-studio-code)编辑文档。</span><span class="sxs-lookup"><span data-stu-id="dc75e-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="dc75e-170">添加图像</span><span class="sxs-lookup"><span data-stu-id="dc75e-170">Adding images</span></span>

<span data-ttu-id="dc75e-171">你将需要将映像上传到该存储库中的"混合的现实的 docs/images"文件夹，然后在文章中适当地引用它们。</span><span class="sxs-lookup"><span data-stu-id="dc75e-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="dc75e-172">映像会自动显示在原尺寸，这意味着如果你的映像很大，它将填充整个项目的宽度。</span><span class="sxs-lookup"><span data-stu-id="dc75e-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="dc75e-173">因此，我们建议将其上传之前预调整你的映像。</span><span class="sxs-lookup"><span data-stu-id="dc75e-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="dc75e-174">建议的宽度是 600 和 700 像素之间，尽管它分别是密集的屏幕快照或一小部分的屏幕截图中，应大小向上或向下。</span><span class="sxs-lookup"><span data-stu-id="dc75e-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="dc75e-175">在合并之前，您可以仅将图像上载到分叉的存储库。</span><span class="sxs-lookup"><span data-stu-id="dc75e-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="dc75e-176">因此，如果您计划将映像添加到项目，您将需要[使用 Visual Studio Code](#using-visual-studio-code)首先将映像添加到分支的"images"文件夹，或确保所做的 web 浏览器中的以下：</span><span class="sxs-lookup"><span data-stu-id="dc75e-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="dc75e-177">分叉 MicrosoftDocs/混合现实存储库。</span><span class="sxs-lookup"><span data-stu-id="dc75e-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="dc75e-178">编辑在分支中的文章。</span><span class="sxs-lookup"><span data-stu-id="dc75e-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="dc75e-179">上传您的文章"混合的现实的 docs/images"文件夹中引用在分支中的映像。</span><span class="sxs-lookup"><span data-stu-id="dc75e-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="dc75e-180">创建**拉取请求**要合并到 MicrosoftDocs/混合现实 master 分支的分支。</span><span class="sxs-lookup"><span data-stu-id="dc75e-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="dc75e-181">若要了解如何设置分叉存储库，请按照的说明进行操作[创建新文章](#creating-a-new-article)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="dc75e-182">预览所做的工作</span><span class="sxs-lookup"><span data-stu-id="dc75e-182">Previewing your work</span></span>

<span data-ttu-id="dc75e-183">在 GitHub 中编辑时通过 web 浏览器，可以单击**预览版**页后，可以预览所做的工作之前提交的顶部附近的选项卡。</span><span class="sxs-lookup"><span data-stu-id="dc75e-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="dc75e-184">预览 review.docs.microsoft.com 上所做的更改是仅供 Microsoft 员工</span><span class="sxs-lookup"><span data-stu-id="dc75e-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="dc75e-185">Microsoft 员工： 一旦您的发布内容已合并为主分支，可以看到之前将它放在公共文档外观 https://review.docs.microsoft.com/windows/mixed-reality?branch=master（找到您在左侧列中使用的目录的文章）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="dc75e-186">与使用桌面客户端进行编辑浏览器中编辑</span><span class="sxs-lookup"><span data-stu-id="dc75e-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="dc75e-187">在浏览器中编辑是最简单的方法进行快速更改，但是，有几个缺点：</span><span class="sxs-lookup"><span data-stu-id="dc75e-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="dc75e-188">别让拼写检查。</span><span class="sxs-lookup"><span data-stu-id="dc75e-188">You don't get spell-check.</span></span>
- <span data-ttu-id="dc75e-189">别让任何智能-将链接到 （您需要手动键入文章的文件名） 的其他文章。</span><span class="sxs-lookup"><span data-stu-id="dc75e-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="dc75e-190">它可以是一个麻烦上, 传和引用图像。</span><span class="sxs-lookup"><span data-stu-id="dc75e-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="dc75e-191">如果您将相当不处理这些问题，您可能更愿意使用桌面客户端，如[Visual Studio Code](https://code.visualstudio.com/)需单击几次[有用的扩展](#useful-extensions)来参与编辑文档。</span><span class="sxs-lookup"><span data-stu-id="dc75e-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="dc75e-192">使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc75e-192">Using Visual Studio Code</span></span>

<span data-ttu-id="dc75e-193">由于原因列出[上面](#editing-in-the-browser-vs-editing-with-a-desktop-client)，您可能更喜欢使用桌面客户端编辑而不是 web 浏览器的文档。</span><span class="sxs-lookup"><span data-stu-id="dc75e-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="dc75e-194">我们建议使用[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="dc75e-195">安装</span><span class="sxs-lookup"><span data-stu-id="dc75e-195">Setup</span></span>

<span data-ttu-id="dc75e-196">请执行以下步骤来配置 Visual Studio 代码，以使用此存储库：</span><span class="sxs-lookup"><span data-stu-id="dc75e-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="dc75e-197">在 web 浏览器中：</span><span class="sxs-lookup"><span data-stu-id="dc75e-197">In a web browser:</span></span>
    1. <span data-ttu-id="dc75e-198">安装[适用于您的 PC 的 Git](https://git-scm.com/downloads)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="dc75e-199">安装[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="dc75e-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="dc75e-200">[创建分支 MicrosoftDocs/混合现实](#creating-a-new-article)如果尚未准备好。</span><span class="sxs-lookup"><span data-stu-id="dc75e-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="dc75e-201">中的分支，请单击**克隆或下载**并复制 URL。</span><span class="sxs-lookup"><span data-stu-id="dc75e-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="dc75e-202">在 Visual Studio Code 中创建分支的本地克隆：</span><span class="sxs-lookup"><span data-stu-id="dc75e-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="dc75e-203">从**视图**菜单中，选择**命令面板**。</span><span class="sxs-lookup"><span data-stu-id="dc75e-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="dc75e-204">类型"Git:Clone。"</span><span class="sxs-lookup"><span data-stu-id="dc75e-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="dc75e-205">粘贴刚刚复制的 URL。</span><span class="sxs-lookup"><span data-stu-id="dc75e-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="dc75e-206">选择你的 PC 上保存克隆的位置。</span><span class="sxs-lookup"><span data-stu-id="dc75e-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="dc75e-207">单击**打开存储库**在弹出窗口中。</span><span class="sxs-lookup"><span data-stu-id="dc75e-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="dc75e-208">编辑文档</span><span class="sxs-lookup"><span data-stu-id="dc75e-208">Editing documentation</span></span>

<span data-ttu-id="dc75e-209">使用以下工作流使用 Visual Studio Code 文档进行更改：</span><span class="sxs-lookup"><span data-stu-id="dc75e-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="dc75e-210">所有的指南[编辑](#editing-an-existing-article)和[创建](#creating-a-new-article)文章，并[的编辑 Markdown 基础知识](#markdown-basics)，上述适用于使用 Visual Studio Code 还时。</span><span class="sxs-lookup"><span data-stu-id="dc75e-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="dc75e-211">请确保在克隆的分支是最新的与官方存储库。</span><span class="sxs-lookup"><span data-stu-id="dc75e-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="dc75e-212">在 web 浏览器中创建同步最新更改从其他参与者都 MicrosoftDocs/混合现实 master 分支的拉取请求 （请确保箭头指向正确的方式）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![将从 MicrosoftDocs/混合现实的更改同步到分支](images/sync_repos.PNG)
   2. <span data-ttu-id="dc75e-214">在 Visual Studio Code 中，单击同步按钮以同步新更新将分支与本地克隆。</span><span class="sxs-lookup"><span data-stu-id="dc75e-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![单击同步按钮](images/sync_clone.png)
2. <span data-ttu-id="dc75e-216">创建或编辑使用 Visual Studio Code 在克隆存储库中的文章。</span><span class="sxs-lookup"><span data-stu-id="dc75e-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="dc75e-217">编辑一个或多个项目 （将映像添加到"图片"文件夹如有必要）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="dc75e-218">**保存**中的更改**资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="dc75e-218">**Save** changes in **Explorer**.</span></span>
      
      ![在资源管理器中选择"全部保存"](images/explorer_save.png)
   3. <span data-ttu-id="dc75e-220">**全部提交**中的更改**源代码管理**（写入提交消息出现提示时）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![选择"全部提交"在源代码管理中](images/source_control_commit.png)
   4. <span data-ttu-id="dc75e-222">单击**同步**同步所做的更改回源 （在 GitHub 上的分支） 按钮。</span><span class="sxs-lookup"><span data-stu-id="dc75e-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![单击同步按钮](images/sync_back.png)
3. <span data-ttu-id="dc75e-224">在 web 浏览器中创建同步回 MicrosoftDocs/混合现实 master 分支中的新更改的拉取请求 （请确保箭头指向正确的方式）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![到 MicrosoftDocs/混合现实从分叉创建拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="dc75e-226">有用的扩展</span><span class="sxs-lookup"><span data-stu-id="dc75e-226">Useful extensions</span></span>

<span data-ttu-id="dc75e-227">编辑文档时，以下 Visual Studio Code 扩展是非常有用：</span><span class="sxs-lookup"><span data-stu-id="dc75e-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="dc75e-228">[Visual Studio Code 的 docs Markdown 扩展](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)-使用**Alt + M**弹出的 docs 创作选项，如菜单：</span><span class="sxs-lookup"><span data-stu-id="dc75e-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="dc75e-229">已上载的搜索和参考映像。</span><span class="sxs-lookup"><span data-stu-id="dc75e-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="dc75e-230">添加格式设置等列表、 表和特定于文档的标注喜欢`>[!NOTE]`。</span><span class="sxs-lookup"><span data-stu-id="dc75e-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="dc75e-231">搜索并引用内部链接和书签 （在页面内的特定部分的链接）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="dc75e-232">格式错误将突出显示 （请将鼠标悬停在错误以了解详细信息）。</span><span class="sxs-lookup"><span data-stu-id="dc75e-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="dc75e-233">[拼写检查器的代码](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼错的单词将带有下划线; 右键单击拼错的单词，若要对其进行更改或将其保存到字典。</span><span class="sxs-lookup"><span data-stu-id="dc75e-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
