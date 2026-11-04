# 手动上传到 GitHub

推荐仓库名：`vocab-to-exam`。

推荐描述：`把每日英语词表转成四级、六级和考研原创阅读与翻译练习的 Agent Skill。`

## 方法一：网页上传（首次发布推荐）

1. 登录 GitHub，打开 [新建仓库](https://github.com/new)。
2. Repository name 填 `vocab-to-exam`，Description 可使用上面的描述。
3. 想公开分享就选 **Public**。本地已有 README 和 .gitignore，新建时不再自动添加；许可证也可在发布后单独选择。
4. 点击 **Create repository**。
5. 空仓库的 Quick setup 区域点击 **uploading an existing file**；已有文件的仓库使用 **Add file → Upload files**。
6. 打开整理好的发布文件夹，将其中的 `README.md`、`.gitignore`、`.gitattributes`、`docs`、`vocab-to-exam` 一起拖入上传区。拖入文件夹可保留内部层级。Windows 如看不到点开头的文件，可在资源管理器开启隐藏项目显示。
7. 检查待上传列表：仓库根目录应直接出现 `README.md`，以及 `vocab-to-exam/SKILL.md`。不要把整个外层发布文件夹拖进去，也不要只上传 ZIP 压缩包。
8. 提交说明可填 `Initial release: vocab-to-exam skill`，按页面提示提交。若按钮为 **Propose changes**，继续创建并合并 PR；若直接提交到自己的新仓库，则完成提交即可。
9. 返回仓库首页，确认 README 展示正常，技能文件和参考文件均可打开。

**只上传干净的发布文件夹内容**，不要把项目中的 `work`、`outputs`、下载的 PDF 或本地依赖一起拖入。网页上传不会根据本地 `.gitignore` 自动替你筛选拖入的文件。

本地发布 ZIP 用于打包传递，网页上传前先解压。最终根目录结构见 [README](../README.md#仓库结构)。

## 方法二：PowerShell + Git（可选）

先安装 Git，并在 GitHub 创建一个不带 README、.gitignore 和许可证的空仓库。在本地项目根目录运行以下命令；将远端地址中的 `YOUR_USERNAME` 换成自己的 GitHub 用户名。

```powershell
Set-Location -LiteralPath 'E:\codex-project\单词skills'
git init -b main
git add README.md .gitignore .gitattributes docs vocab-to-exam
git diff --cached --stat
git commit -m "Initial release: vocab-to-exam skill"
git remote add origin https://github.com/YOUR_USERNAME/vocab-to-exam.git
git push -u origin main
```

这些命令用于尚未初始化的新本地仓库。已有 Git 仓库或 remote 时先检查 `git status`、`git remote -v`，不要重复初始化或覆盖已有远端。

如果提交时提示缺少身份，先在该仓库内运行以下命令，再重新提交。邮箱可用 GitHub 设置中的隐私邮箱。

```powershell
git config user.name "你的GitHub用户名"
git config user.email "你的提交邮箱"
```

推送时按 Git 的登录窗口完成 GitHub 认证。

## 发布后可补充

- 在仓库 About 中填简介，Topics 可用 `agent-skills`、`codex`、`english-learning`、`cet4`、`cet6`。
- 本次未代选许可证。若希望他人按开源条款使用和修改，可在确认授权方式后添加 `LICENSE`，常见选择包括 MIT。
- 后续版本更新 README 和技能文件即可；需要版本归档时再创建 tag 或 Release。

操作入口参考 GitHub 官方文档：[创建仓库](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)、[上传文件](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)。
