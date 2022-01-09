---
title: "Setup_myblog_using_hugo"
date: 2022-01-09T17:53:37+08:00
draft: true
---


## 使用的工具
Github Hugo

## 参考文档
https://www.bilibili.com/video/BV1q4411i7gL/?spm_id_from=333.788.recommend_more_video.-1

## 操作步骤

### 1. 生成博客（生成一个文件夹，如：myblog）
```
[mengbao@minitana mnt]$ ls
 00_code   01_software   02_document   03_Video   06_my_blog   lost+found  'System Volume Information'
[mengbao@minitana mnt]$ hugo new site myblog
Congratulations! Your new Hugo site is created in /home/mengbao/mnt/myblog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
[mengbao@minitana mnt]$ ls
 00_code   01_software   02_document   03_Video   06_my_blog   lost+found   myblog  'System Volume Information'
```

### 2. 选择一个主题
Hugo提供了很多主题，下面连接下找到自己喜欢的主题并下载。
每个主题下面都有步骤和命令。
```
https://themes.gohugo.io/
```
```
mengbao@minitana myblog]$ pwd
/home/mengbao/mnt/myblog
[mengbao@minitana myblog]$ git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
Cloning into 'themes/m10c'...
remote: Enumerating objects: 397, done.
remote: Counting objects: 100% (17/17), done.
remote: Compressing objects: 100% (16/16), done.
remote: Total 397 (delta 2), reused 3 (delta 0), pack-reused 380
Receiving objects: 100% (397/397), 914.77 KiB | 18.00 KiB/s, done.
Resolving deltas: 100% (142/142), done.
[mengbao@minitana myblog]$ cd themes/
[mengbao@minitana themes]$ ls
m10c
[mengbao@minitana themes]$ 
```

### 3. 在本地启动个人博客
```
[mengbao@minitana myblog]$ pwd
/home/mengbao/mnt/myblog
[mengbao@minitana myblog]$ hugo server -t m10c --buildDrafts
Start building sites … 
hugo v0.89.4+extended linux/amd64 BuildDate=unknown

                   | EN  
-------------------+-----
  Pages            |  7  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  1  
  Processed images |  0  
  Aliases          |  1  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 19 ms
Watching for changes in /home/mengbao/mnt/myblog/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /home/mengbao/mnt/myblog/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
打开一个游览器可以查看你的博客：输入http://localhost:1313/

### 4. 创建一片文章
```
[mengbao@minitana myblog]$ pwd
/home/mengbao/mnt/myblog
[mengbao@minitana myblog]$ ls
archetypes  config.toml  content  data  layouts  resources  static  themes
[mengbao@minitana myblog]$ hugo new post/blog.md
Content "/home/mengbao/mnt/myblog/content/post/blog.md" created
[mengbao@minitana myblog]$ 
```

### 5. 将博客部署到远端服务器上

#### 1. 在github上创建一个仓库
仓库的名字必须跟你用户名关联。
比如：我的用户名字为mengbao815，所以我创建的仓库名字是mengbao815.github.io

#### 2. 使用md文件生成html格式的文件
首先更新完/home/mengbao/mnt/myblog/content/post/blog.md。
然后执行下面命令（生成public文件夹，里面html格式的文件）。

```
[mengbao@minitana myblog]$ pwd
/home/mengbao/mnt/myblog
[mengbao@minitana myblog]$ ls
archetypes  config.toml  content  data  layouts  resources  static  themes
[mengbao@minitana myblog]$ hugo --theme=m10c --baseUrl="https://mengbao815.github.io" --buildDrafts
Start building sites … 
hugo v0.89.4+extended linux/amd64 BuildDate=unknown

                   | EN  
-------------------+-----
  Pages            | 10  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  1  
  Processed images |  0  
  Aliases          |  2  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 26 ms
[mengbao@minitana myblog]$ ls
archetypes  config.toml  content  data  layouts  public  resources  static  themes
```

### 6. 把public文件夹上传到github
```
[mengbao@minitana public]$ pwd
/home/mengbao/mnt/myblog/public
[mengbao@minitana public]$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /home/mengbao/mnt/myblog/public/.git/
[mengbao@minitana public]$ git add .
[mengbao@minitana public]$ git commit -m "first update for my blog"
[master (root-commit) 45e2056] first update for my blog
 15 files changed, 409 insertions(+)
 create mode 100644 404.html
 create mode 100644 avatar.jpg
 create mode 100644 categories/index.html
 create mode 100644 categories/index.xml
 create mode 100644 css/main.min.4a7ec8660f9a44b08c4da97c5f2e31b1192df1d4d0322e65c0dbbc6ecb1b863f.css
 create mode 100644 index.html
 create mode 100644 index.xml
 create mode 100644 page/1/index.html
 create mode 100644 post/blog/index.html
 create mode 100644 post/index.html
 create mode 100644 post/index.xml
 create mode 100644 post/page/1/index.html
 create mode 100644 sitemap.xml
 create mode 100644 tags/index.html
 create mode 100644 tags/index.xml
[mengbao@minitana public]$ 
[mengbao@minitana public]$ git remote add origin https://github.com/mengbao815/mengbao815.github.io.git
[mengbao@minitana public]$ git push -u origin master
```
