---
title: 参与说明
description: 如何参与 Windows 混合现实文档。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 934171f26571b3219bbe390aff44349fb6908f74
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437123"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="46bfa-103">参与 Windows Mixed Reality 开发人员文档</span><span class="sxs-lookup"><span data-stu-id="46bfa-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="46bfa-104">欢迎使用[适用于 Windows Mixed Reality 开发人员文档的公共](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)存储库！</span><span class="sxs-lookup"><span data-stu-id="46bfa-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="46bfa-105">在此存储库中创建或编辑的任何项目**都将对公共可见。**</span><span class="sxs-lookup"><span data-stu-id="46bfa-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="46bfa-106">Windows Mixed Reality 文档现在位于 docs.microsoft.com 平台，该平台使用 GitHub 风格 Markdown （带有 Markdig 功能）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="46bfa-107">实质上，在此存储库中编辑的内容会转换为在 https://docs.microsoft.com/windows/mixed-reality 显示的已设置格式和样式的页面。</span><span class="sxs-lookup"><span data-stu-id="46bfa-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="46bfa-108">此页介绍了用于参与的基本步骤和准则，以及指向 Markdown 基础知识的链接。</span><span class="sxs-lookup"><span data-stu-id="46bfa-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="46bfa-109">感谢您的参与！</span><span class="sxs-lookup"><span data-stu-id="46bfa-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="46bfa-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="46bfa-110">Before you start</span></span>

<span data-ttu-id="46bfa-111">如果还没有，则需要[创建一个 GitHub 帐户](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="46bfa-112">如果你是 Microsoft 员工，请将你的 GitHub 帐户链接到[Microsoft 开源门户](https://repos.opensource.microsoft.com/)上的 microsoft 别名。</span><span class="sxs-lookup"><span data-stu-id="46bfa-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="46bfa-113">加入 **"Microsoft"** 和 **"MicrosoftDocs"** 组织。</span><span class="sxs-lookup"><span data-stu-id="46bfa-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="46bfa-114">设置 GitHub 帐户时，我们还建议采用以下安全预防措施：</span><span class="sxs-lookup"><span data-stu-id="46bfa-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="46bfa-115">[为 Github 帐户创建强密码](https://github.com/settings/admin)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="46bfa-116">启用[双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="46bfa-117">将[恢复代码](https://github.com/settings/auth/recovery-codes)保存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="46bfa-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="46bfa-118">更新[公用配置文件设置](https://github.com/settings/profile)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="46bfa-119">设置你的名称，并考虑将你的*公用电子邮件*设置为*不显示我的电子邮件地址*。</span><span class="sxs-lookup"><span data-stu-id="46bfa-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="46bfa-120">建议你上载个人资料图片，因为缩略图会显示在你所参与的文档页面上。</span><span class="sxs-lookup"><span data-stu-id="46bfa-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="46bfa-121">如果计划使用命令行工作流，请考虑设置[适用于 Windows 的 Git 凭据管理器](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)，这样，每次发布时都无需输入密码。</span><span class="sxs-lookup"><span data-stu-id="46bfa-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="46bfa-122">执行这些步骤非常重要，因为发布系统与 GitHub 相关，你将使用 GitHub 别名作为每篇文章的作者或参与者列出。</span><span class="sxs-lookup"><span data-stu-id="46bfa-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="46bfa-123">编辑现有项目</span><span class="sxs-lookup"><span data-stu-id="46bfa-123">Editing an existing article</span></span>

<span data-ttu-id="46bfa-124">使用以下工作流，在 web 浏览器中通过 GitHub 对*现有文章*进行更新：</span><span class="sxs-lookup"><span data-stu-id="46bfa-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="46bfa-125">导航到要在 "混合现实-文档" 文件夹中编辑的项目。</span><span class="sxs-lookup"><span data-stu-id="46bfa-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="46bfa-126">选择右上方的 "编辑" 按钮（铅笔图标）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="46bfa-127">这会自动从 "master" 分支中派生出可释放分支。</span><span class="sxs-lookup"><span data-stu-id="46bfa-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![编辑项目。](images/editpage.png)
3. <span data-ttu-id="46bfa-129">编辑项目的内容（有关指导，请参阅下面的["Markdown 基本信息"](#markdown-basics) ）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="46bfa-130">更新每个项目顶部相关的元数据：</span><span class="sxs-lookup"><span data-stu-id="46bfa-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="46bfa-131">title：这是查看项目时浏览器选项卡中显示的页面标题。</span><span class="sxs-lookup"><span data-stu-id="46bfa-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="46bfa-132">由于此用于 SEO 和编制索引，因此除非有必要，否则不应更改标题（不过，在文档公开之前这并不重要）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="46bfa-133">说明：编写文章内容的简短说明。</span><span class="sxs-lookup"><span data-stu-id="46bfa-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="46bfa-134">这项辅助功能和发现。</span><span class="sxs-lookup"><span data-stu-id="46bfa-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="46bfa-135">作者：如果你是页面的主要所有者，请在此处添加你的 GitHub 别名。</span><span class="sxs-lookup"><span data-stu-id="46bfa-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="46bfa-136">女士：如果你是页面的主要所有者，请在此处添加你的 Microsoft 别名（你不需要 @microsoft.com，只需别名）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="46bfa-137">"ms"：如果向页面中添加主要内容，则更新日期，但不将其用于修补，如说明、格式、语法或拼写。</span><span class="sxs-lookup"><span data-stu-id="46bfa-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="46bfa-138">关键字： SEO 中的关键字帮助（搜索引擎优化）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="46bfa-139">添加特定于您的项目的关键字（以逗号和空格分隔），而不是列表中最后一个关键字后面的任何标点）;无需添加适用于所有项目的全局关键字，因为在其他位置托管这些项目。</span><span class="sxs-lookup"><span data-stu-id="46bfa-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="46bfa-140">完成文章编辑后，向下滚动并单击 "**建议文件更改**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="46bfa-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="46bfa-141">在下一页上，单击 "**创建拉取请求**" 将自动创建的分支合并到 "master"。</span><span class="sxs-lookup"><span data-stu-id="46bfa-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="46bfa-142">对于要编辑的下一篇文章，请重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="46bfa-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="46bfa-143">重命名或删除现有项目</span><span class="sxs-lookup"><span data-stu-id="46bfa-143">Renaming or deleting an existing article</span></span>

<span data-ttu-id="46bfa-144">如果更改将重命名或删除现有项目，请确保添加一个重定向。</span><span class="sxs-lookup"><span data-stu-id="46bfa-144">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="46bfa-145">这样一来，具有现有文章的链接的任何人仍将在正确的位置结束。</span><span class="sxs-lookup"><span data-stu-id="46bfa-145">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="46bfa-146">重定向由存储库根目录中的 .openpublishing.publish.config.json 文件进行管理。</span><span class="sxs-lookup"><span data-stu-id="46bfa-146">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="46bfa-147">若要将重定向添加到 .openpublishing.publish.config.json，请将条目添加到 `redirections` 数组：</span><span class="sxs-lookup"><span data-stu-id="46bfa-147">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="46bfa-148">`source_path` 是要删除的旧文章的相对存储库路径。</span><span class="sxs-lookup"><span data-stu-id="46bfa-148">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="46bfa-149">请确保路径以 `mixed-reality-docs` 开头，并以 `.md`结束。</span><span class="sxs-lookup"><span data-stu-id="46bfa-149">Be sure the path starts with `mixed-reality-docs` and ends with `.md`.</span></span>
- <span data-ttu-id="46bfa-150">`redirect_url` 是从旧文章到新文章的相对公共 URL。</span><span class="sxs-lookup"><span data-stu-id="46bfa-150">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="46bfa-151">请确保此 URL**不**包含 `mixed-reality-docs` 或 `.md`，因为它引用的是公共 URL，而不是存储库路径。</span><span class="sxs-lookup"><span data-stu-id="46bfa-151">Be sure that this URL **does not** contain `mixed-reality-docs` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="46bfa-152">允许使用 `#section` 链接到新项目中的某个部分。</span><span class="sxs-lookup"><span data-stu-id="46bfa-152">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="46bfa-153">如果需要，还可以在此处使用其他站点的绝对路径。</span><span class="sxs-lookup"><span data-stu-id="46bfa-153">You may also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="46bfa-154">`redirect_document_id` 指示是否要保留以前文件中的文档 ID。</span><span class="sxs-lookup"><span data-stu-id="46bfa-154">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="46bfa-155">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="46bfa-155">The default is `false`.</span></span> <span data-ttu-id="46bfa-156">如果要保留重定向的项目中的 `ms.documentid` 属性值，请使用 `true`。</span><span class="sxs-lookup"><span data-stu-id="46bfa-156">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="46bfa-157">如果保留文档 ID，数据（如页面视图和分级）将传输到目标文章。</span><span class="sxs-lookup"><span data-stu-id="46bfa-157">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="46bfa-158">如果重定向主要用于重命名，而不是指向仅涵盖一些相同内容的不同项目的指针，则执行此操作。</span><span class="sxs-lookup"><span data-stu-id="46bfa-158">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="46bfa-159">如果添加重定向，请确保同时删除旧文件。</span><span class="sxs-lookup"><span data-stu-id="46bfa-159">If you add a redirect, be sure to delete the old file as well.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="46bfa-160">创建新项目</span><span class="sxs-lookup"><span data-stu-id="46bfa-160">Creating a new article</span></span>

<span data-ttu-id="46bfa-161">使用以下工作流在 web 浏览器中通过 GitHub 在文档存储库中*创建新项目*：</span><span class="sxs-lookup"><span data-stu-id="46bfa-161">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="46bfa-162">使用右上方的 "**分叉**" 按钮，创建 MicrosoftDocs/mixed reality "master" 分支的分叉。</span><span class="sxs-lookup"><span data-stu-id="46bfa-162">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![将主分支分叉。](images/forkbranch.png)
2. <span data-ttu-id="46bfa-164">在 "混合现实文档" 文件夹中，单击右上方的 "**创建新文件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="46bfa-164">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="46bfa-165">为项目创建页名称（使用连字符而不是空格，不要使用标点符号或撇号）并追加 "md"</span><span class="sxs-lookup"><span data-stu-id="46bfa-165">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![命名新页。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="46bfa-167">请确保在 "mixed reality-文档" 文件夹中创建新项目。</span><span class="sxs-lookup"><span data-stu-id="46bfa-167">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="46bfa-168">可以通过在 "新文件名" 行中检查 "/mixed-reality-docs/" 来确认这一点。</span><span class="sxs-lookup"><span data-stu-id="46bfa-168">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="46bfa-169">在新页的顶部，添加以下元数据块：</span><span class="sxs-lookup"><span data-stu-id="46bfa-169">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="46bfa-170">按照[以上部分](#editing-an-existing-article)中的说明填写相关的元数据字段。</span><span class="sxs-lookup"><span data-stu-id="46bfa-170">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="46bfa-171">使用[Markdown 基础知识](#markdown-basics)编写文章内容。</span><span class="sxs-lookup"><span data-stu-id="46bfa-171">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="46bfa-172">在文章底部添加一个 `## See also` 节，其中包含指向其他相关文章的链接。</span><span class="sxs-lookup"><span data-stu-id="46bfa-172">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="46bfa-173">完成后，单击 "**提交新文件**"。</span><span class="sxs-lookup"><span data-stu-id="46bfa-173">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="46bfa-174">单击 "**新建拉取请求**"，并将分叉的 "master" 分支合并到 MicrosoftDocs/mixed reality "master" 中（确保箭头的方向正确）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-174">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="46bfa-176">Markdown 基础知识</span><span class="sxs-lookup"><span data-stu-id="46bfa-176">Markdown basics</span></span>

<span data-ttu-id="46bfa-177">以下资源将帮助你了解如何使用 Markdown 语言编辑文档：</span><span class="sxs-lookup"><span data-stu-id="46bfa-177">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="46bfa-178">Markdown 基础知识</span><span class="sxs-lookup"><span data-stu-id="46bfa-178">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="46bfa-179">一览式参考海报 Markdown</span><span class="sxs-lookup"><span data-stu-id="46bfa-179">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="46bfa-180">用于编写 docs.microsoft.com 的 Markdown 的其他资源</span><span class="sxs-lookup"><span data-stu-id="46bfa-180">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="46bfa-181">添加表</span><span class="sxs-lookup"><span data-stu-id="46bfa-181">Adding tables</span></span>

<span data-ttu-id="46bfa-182">由于 docs.microsoft.com 样式表的方式，它们没有边框或自定义样式，即使您尝试使用内联 CSS 也是如此。</span><span class="sxs-lookup"><span data-stu-id="46bfa-182">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="46bfa-183">它看起来可以正常工作，但最终平台会去除表的样式。</span><span class="sxs-lookup"><span data-stu-id="46bfa-183">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="46bfa-184">因此请提前规划并使表保持简单。</span><span class="sxs-lookup"><span data-stu-id="46bfa-184">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="46bfa-185">[下面是使 Markdown 表变得简单的站点](https://www.tablesgenerator.com/markdown_tables)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-185">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="46bfa-186">如果你使用[Visual Studio Code （见下文）](#using-visual-studio-code)来编辑文档，则[用于 Visual Studio Code 的文档 Markdown 扩展](https://docs.microsoft.com/teamblog/docs-extension)还可以简化表的生成。</span><span class="sxs-lookup"><span data-stu-id="46bfa-186">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="46bfa-187">添加图像</span><span class="sxs-lookup"><span data-stu-id="46bfa-187">Adding images</span></span>

<span data-ttu-id="46bfa-188">需要将映像上传到存储库中的 "混合现实文档/映像" 文件夹，并在文章中对它们进行相应的引用。</span><span class="sxs-lookup"><span data-stu-id="46bfa-188">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="46bfa-189">图像将自动以全尺寸显示，这意味着，如果图像很大，则会填充整个文章的宽度。</span><span class="sxs-lookup"><span data-stu-id="46bfa-189">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="46bfa-190">因此，建议在上传映像之前对其进行预先调整大小。</span><span class="sxs-lookup"><span data-stu-id="46bfa-190">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="46bfa-191">建议宽度介于600到700像素之间，不过，如果它是密集屏幕截图或屏幕截图的小部分，则应调整大小。</span><span class="sxs-lookup"><span data-stu-id="46bfa-191">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="46bfa-192">在合并前，只能将图像上传到分叉存储库。</span><span class="sxs-lookup"><span data-stu-id="46bfa-192">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="46bfa-193">因此，如果你计划将图像添加到项目中，则需要先[使用 Visual Studio Code](#using-visual-studio-code)将图像添加到分叉的 "images" 文件夹，或者确保已在 web 浏览器中完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="46bfa-193">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="46bfa-194">分叉 MicrosoftDocs/mixed reality 存储库。</span><span class="sxs-lookup"><span data-stu-id="46bfa-194">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="46bfa-195">已编辑分叉中的项目。</span><span class="sxs-lookup"><span data-stu-id="46bfa-195">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="46bfa-196">将你在项目中引用的映像上传到你的分支中的 "混合现实文档/映像" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="46bfa-196">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="46bfa-197">创建了用于将分叉合并到 MicrosoftDocs/mixed reality "master" 分支的**拉取请求**。</span><span class="sxs-lookup"><span data-stu-id="46bfa-197">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="46bfa-198">若要了解如何设置自己的分叉存储库，请按照[创建新文章](#creating-a-new-article)的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="46bfa-198">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="46bfa-199">预览工作</span><span class="sxs-lookup"><span data-stu-id="46bfa-199">Previewing your work</span></span>

<span data-ttu-id="46bfa-200">通过 web 浏览器在 GitHub 中进行编辑时，可以单击页面顶部附近的 "**预览**" 选项卡来预览你的工作，然后再提交。</span><span class="sxs-lookup"><span data-stu-id="46bfa-200">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="46bfa-201">在 review.docs.microsoft.com 上预览所做的更改仅适用于 Microsoft 员工</span><span class="sxs-lookup"><span data-stu-id="46bfa-201">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="46bfa-202">Microsoft 员工：将你的贡献合并到 "master" 分支后，你可以在 https://review.docs.microsoft.com/windows/mixed-reality?branch=master （使用左栏中的目录查找文章）中查看文档的外观。</span><span class="sxs-lookup"><span data-stu-id="46bfa-202">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="46bfa-203">在浏览器中编辑与使用桌面客户端进行编辑</span><span class="sxs-lookup"><span data-stu-id="46bfa-203">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="46bfa-204">在浏览器中进行编辑是进行快速更改的最简单方法，但有几个缺点：</span><span class="sxs-lookup"><span data-stu-id="46bfa-204">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="46bfa-205">不会进行拼写检查。</span><span class="sxs-lookup"><span data-stu-id="46bfa-205">You don't get spell-check.</span></span>
- <span data-ttu-id="46bfa-206">您不会获得任何智能链接到其他文章（您必须手动键入项目的文件名）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-206">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="46bfa-207">这可能是上传和引用图像的麻烦。</span><span class="sxs-lookup"><span data-stu-id="46bfa-207">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="46bfa-208">如果你不想处理这些问题，你可能更愿意使用桌面客户端（如[Visual Studio Code](https://code.visualstudio.com/) ），其中包含一些[有用的扩展](#useful-extensions)，可用于文档。</span><span class="sxs-lookup"><span data-stu-id="46bfa-208">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="46bfa-209">使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="46bfa-209">Using Visual Studio Code</span></span>

<span data-ttu-id="46bfa-210">出于[上面](#editing-in-the-browser-vs-editing-with-a-desktop-client)列出的原因，您可能更倾向于使用桌面客户端编辑文档而不是 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="46bfa-210">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="46bfa-211">建议使用[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-211">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="46bfa-212">“安装程序”</span><span class="sxs-lookup"><span data-stu-id="46bfa-212">Setup</span></span>

<span data-ttu-id="46bfa-213">请按照以下步骤配置 Visual Studio Code 以使用此存储库：</span><span class="sxs-lookup"><span data-stu-id="46bfa-213">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="46bfa-214">在 web 浏览器中：</span><span class="sxs-lookup"><span data-stu-id="46bfa-214">In a web browser:</span></span>
    1. <span data-ttu-id="46bfa-215">安装[适用于你的电脑的 Git](https://git-scm.com/downloads)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-215">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="46bfa-216">安装[Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="46bfa-216">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="46bfa-217">[分叉 MicrosoftDocs/混合现实（](#creating-a-new-article)如果尚未这样做）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-217">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="46bfa-218">在你的分支中，单击 "**克隆" 或下载**并复制 URL。</span><span class="sxs-lookup"><span data-stu-id="46bfa-218">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="46bfa-219">在 Visual Studio Code 中创建分叉的本地复本：</span><span class="sxs-lookup"><span data-stu-id="46bfa-219">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="46bfa-220">从 "**视图**" 菜单中选择 "**命令面板**"。</span><span class="sxs-lookup"><span data-stu-id="46bfa-220">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="46bfa-221">键入 "Git： Clone"。</span><span class="sxs-lookup"><span data-stu-id="46bfa-221">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="46bfa-222">粘贴刚才复制的 URL。</span><span class="sxs-lookup"><span data-stu-id="46bfa-222">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="46bfa-223">选择要在电脑上保存克隆的位置。</span><span class="sxs-lookup"><span data-stu-id="46bfa-223">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="46bfa-224">在弹出窗口中单击 "**打开**存储库"。</span><span class="sxs-lookup"><span data-stu-id="46bfa-224">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="46bfa-225">编辑文档</span><span class="sxs-lookup"><span data-stu-id="46bfa-225">Editing documentation</span></span>

<span data-ttu-id="46bfa-226">使用以下工作流，通过 Visual Studio Code 对文档进行更改：</span><span class="sxs-lookup"><span data-stu-id="46bfa-226">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="46bfa-227">在使用 Visual Studio Code 时，所有有关[编辑](#editing-an-existing-article)和[创建](#creating-a-new-article)文章的指南以及[编辑 Markdown 的基础知识](#markdown-basics)也适用。</span><span class="sxs-lookup"><span data-stu-id="46bfa-227">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="46bfa-228">请确保你的克隆分叉与官方存储库保持最新。</span><span class="sxs-lookup"><span data-stu-id="46bfa-228">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="46bfa-229">在 web 浏览器中，创建一个拉取请求，将最近的更改从 MicrosoftDocs/mixed reality "master" 中的其他参与者同步到分叉（确保箭头指向正确的方式）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-229">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![将更改从 MicrosoftDocs/混合事实同步到你的分支](images/sync_repos.PNG)
   2. <span data-ttu-id="46bfa-231">在 Visual Studio Code 中，单击 "同步" 按钮，将最新更新的分支同步到本地克隆。</span><span class="sxs-lookup"><span data-stu-id="46bfa-231">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![单击 "同步" 按钮](images/sync_clone.png)
2. <span data-ttu-id="46bfa-233">使用 Visual Studio Code 在克隆的存储库中创建或编辑项目。</span><span class="sxs-lookup"><span data-stu-id="46bfa-233">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="46bfa-234">编辑一个或多个项目（如有必要，将图像添加到 "images" 文件夹）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-234">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="46bfa-235">在**资源管理器**中**保存**更改。</span><span class="sxs-lookup"><span data-stu-id="46bfa-235">**Save** changes in **Explorer**.</span></span>
      
      ![在资源管理器中选择 "全部保存"](images/explorer_save.png)
   3. <span data-ttu-id="46bfa-237">**提交** **源代码管理**中的所有更改（在出现提示时写入提交消息）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-237">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![在源代码管理中选择 "全部提交"](images/source_control_commit.png)
   4. <span data-ttu-id="46bfa-239">单击 "**同步**" 按钮，将所做的更改同步回源（GitHub 上的分支）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-239">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![单击 "同步" 按钮](images/sync_back.png)
3. <span data-ttu-id="46bfa-241">在 web 浏览器中，创建一个拉取请求，以将分支中的新更改同步到 MicrosoftDocs/mixed reality "master" （确保箭头指向正确的方式）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-241">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="46bfa-243">有用的扩展</span><span class="sxs-lookup"><span data-stu-id="46bfa-243">Useful extensions</span></span>

<span data-ttu-id="46bfa-244">编辑文档时，以下 Visual Studio Code 扩展非常有用：</span><span class="sxs-lookup"><span data-stu-id="46bfa-244">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="46bfa-245">[用于 Visual Studio Code 的文档 Markdown 扩展](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)-使用**Alt + M**显示文档创作选项的菜单，如下所示：</span><span class="sxs-lookup"><span data-stu-id="46bfa-245">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="46bfa-246">搜索和引用已上传的映像。</span><span class="sxs-lookup"><span data-stu-id="46bfa-246">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="46bfa-247">添加格式设置，如列表、表和文档特定的调用 `>[!NOTE]`。</span><span class="sxs-lookup"><span data-stu-id="46bfa-247">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="46bfa-248">搜索和引用内部链接和书签（指向页面内特定部分的链接）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-248">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="46bfa-249">突出显示格式错误（将鼠标悬停在错误上以了解详细信息）。</span><span class="sxs-lookup"><span data-stu-id="46bfa-249">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="46bfa-250">[代码拼写检查器](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-将为拼写错误的单词加下划线。右键单击拼写错误的单词以对其进行更改或将其保存到字典中。</span><span class="sxs-lookup"><span data-stu-id="46bfa-250">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
