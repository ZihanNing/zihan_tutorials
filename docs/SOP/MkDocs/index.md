# MkDocs 轻松写博客

这一篇来更新关于我的个人主页中，如何创建 tutorials 相关界面！

在个人主页中，我对于 tutorials 这个部分的要求是:

1. 这个部分我需要经常更新，因此我不能使用像 docusaurus 那样经常需要重新编译的工具
2. 这个博客页面最好简洁，不需要太花哨，有必要的导航栏和检索工具
3. 在 github 上面能够更新迅速
4. 轻量化，不需要太多编程，专注于文字

在寻找了好几个工具后，最终我选择了 **MkDocs**，因为其符合我上述所有的需求。接下来，就是我的 MkDocs 配置教程和使用手册！

---

## 1. 在 Mac 上配置 MkDocs

**（1）安装 Python & MkDocs**

如果系统没 Python3，先安装 [Homebrew](https://brew.sh/)：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

安装 Python3 与 pip：

```bash
brew install python3
```

安装 MkDocs：

```bash
pip install mkdocs
```

推荐使用 Material 主题（最常见且好看）：

```bash
pip install mkdocs-material
```

---

**（2）创建第一个 MkDocs 文档**

进入一个你准备写 blog 的文件夹：

```bash
mkdocs new my-blog
cd my-blog
```

此时会生成一个最基础的结构：

```
my-blog/
  mkdocs.yml      # 配置文件
  docs/
    index.md      # 首页内容
```

---

**（3）本地预览功能**

在根目录下运行：

```bash
mkdocs serve
```

打开浏览器访问 `http://127.0.0.1:8000` 即可实时预览。

---

**（4）上传到 GitHub 并启用 GitHub Pages**

初始化 Git：

```bash
git init
git add .
git commit -m "first mkdocs blog"
git branch -M main
git remote add origin git@github.com:ZihanNing/my-blog.git
```

部署到 GitHub Pages：

```bash
mkdocs gh-deploy
```

部署后，GitHub Pages 会自动生成并托管网站。你可以在仓库的 **Settings → Pages** 里确认发布地址。每次更新后，只要运行 `mkdocs gh-deploy` 就能立即上线，非常轻量。

---

## 2. 在 MkDocs 中加入检索和中/英切换按钮

**（1）检索功能**

Material 主题自带检索功能。确保 `mkdocs.yml` 中有：

```yaml
plugins:
  - search
```

这样即可在右上角生成搜索框。

---

**（2）多语言切换（i18n 插件）**

安装插件：

```bash
pip install mkdocs-static-i18n
```

配置 `mkdocs.yml`：

```yaml
plugins:
  - search
  - i18n:
      docs_structure: suffix
      reconfigure_material: true        # 启用 Material 的语言切换
      fallback_to_default: true         # 没有翻译时显示中文
      languages:
        - locale: zh
          name: 中文
          default: true
        - locale: en
          name: English
```

然后在 `docs/` 下分别创建：

```
index.zh.md
index.en.md
```

访问页面时，右上角会自动出现语言切换按钮（中文/English），可以自由切换。

---

✨ 到这里，一个支持中英文切换 + 搜索功能的 **轻量级个人博客教程系统** 就完成了。
以后要更新，只需要在 `docs/` 文件夹里写新的 markdown 文件，然后一行命令：

```bash
mkdocs gh-deploy
```

就能快速更新 GitHub Pages。

## 常用操作清单（SOP）

### A. 新增文章 SOP

1. 在 `docs/` 文件夹里新建 Markdown 文件，例如：

   ```bash
   touch docs/tutorial1.zh.md
   touch docs/tutorial1.en.md
   ```
2. 在 `mkdocs.yml` 中的导航（`nav`）添加链接：

   ```yaml
   nav:
     - Home: index.md
     - Tutorials:
         - 教程一: tutorial1.zh.md
         - Tutorial 1: tutorial1.en.md
   ```
3. 保存后即可在本地预览/发布。

---

### B. 本地调试 SOP

> ⚠️ 如果你是用虚拟环境（`.venv`）安装的 mkdocs 和插件，必须先进入虚拟环境，否则命令不可用。

1. 进入虚拟环境：

   ```bash
   source .venv/bin/activate
   ```

   成功后命令行前会出现 `(.venv)` 前缀。
2. 启动本地预览：

   ```bash
   mkdocs serve
   ```
3. 浏览器打开 `http://127.0.0.1:8000`，修改内容会自动刷新。

退出虚拟环境：

```bash
deactivate
```

---

### C. 一键发布 SOP

1. 激活虚拟环境（如果使用 `.venv`）：

   ```bash
   source .venv/bin/activate
   ```
2. 发布到 GitHub Pages：

   ```bash
   mkdocs gh-deploy
   ```

几秒后即可在 GitHub Pages 上更新。



