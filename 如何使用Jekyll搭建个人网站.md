---
create date: 2024-09-11
modification date: 
tags:
  - "#fleeting"
type: NomalNotes
---
## 步骤 1：安装 Jekyll 环境
### **1. 安装必要的依赖工具**
在 Windows 上安装 Jekyll 需要以下工具：
1. **Ruby**
    - 访问 [RubyInstaller 下载页面](https://rubyinstaller.org/) 下载最新版的 **Ruby+Devkit** 安装包。
    - 安装过程中选择添加 Ruby 到系统路径。
    - 安装完成后，打开命令提示符 (CMD) 并输入以下命令，确认安装成功：
        `ruby -v gem -v`
2. **安装 Jekyll 和 Bundler**  
    安装完成 Ruby 后，运行以下命令安装 Jekyll 和 Bundler：
    `gem install jekyll bundler`
3. **验证安装**  
    运行以下命令确认 Jekyll 安装成功：
    `jekyll -v`
## 步骤 2：创建一个 Jekyll 网站

1. **新建 Jekyll 项目**  
    在命令提示符 (CMD) 中，导航到你想要创建网站的文件夹，然后运行：
    `jekyll new my-website`
    这将生成一个名为 `my-website` 的新项目文件夹。
2. **进入项目目录**
    `cd my-website`
3. **启动本地服务器**  
    在项目目录中运行：
    `bundle exec jekyll serve`
4. **预览网站**  
    打开浏览器，访问 `http://localhost:4000`，你将看到默认的 Jekyll 网站！
## 步骤 3：自定义 Jekyll 网站

1. **编辑内容**
    - 在 `my-website` 文件夹中，你会看到几个重要的文件和文件夹：
        - `_posts/`：存放博客文章的文件夹。每篇文章以 Markdown 格式存储。
        - `_config.yml`：网站的配置文件，可修改站点标题、描述等信息。
        - `index.markdown` 或 `index.html`：网站首页。
2. **创建新文章**  
    在 `_posts` 文件夹中，创建一个新的 Markdown 文件，命名格式为 `YYYY-MM-DD-文章标题.md`，例如：
    `2024-09-05-welcome-to-jekyll.md`
    内容示例：
```markdown
---
layout: post
title: "欢迎来到我的 Jekyll 博客"
date: 2024-09-05
categories: jekyll
---
这是我的第一篇 Jekyll 博客文章！
```
3. **重新启动服务器**  
    保存修改后，重新启动服务器查看更新：
    `bundle exec jekyll serve`
## 步骤 4：部署到 GitHub Pages

1. **创建 GitHub 仓库**
    - 在 GitHub 上创建一个新仓库，命名格式为 `username.github.io`（将 `username` 替换为你的 GitHub 用户名）。
2. **上传 Jekyll 项目到 GitHub**  
    在项目目录中运行以下命令：
```
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/username.github.io.git
git push -u origin master
```
1. **启用 GitHub Pages**
    - 在 GitHub 仓库的设置（Settings）中，找到 **GitHub Pages** 部分。
    - 将 **Source** 设置为 `master` 分支。
    - 稍等片刻，你的网站就可以通过 `https://username.github.io` 访问了！
## 接下来可以做的事情
1. **主题自定义**：  
    可以使用现成的 Jekyll 主题，或自行定制样式。推荐资源：[Jekyll Themes](https://jekyllthemes.io/)
2. **添加功能**：  
    如评论系统（Disqus）、社交分享按钮、SEO 优化等。
3. **了解 Liquid 模板引擎**：  
    学习如何使用 Jekyll 的模板语言来自定义页面布局。