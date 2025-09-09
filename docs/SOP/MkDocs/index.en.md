# Writing a Blog with MkDocs

This post is about how I created the **tutorials** section on my personal homepage!

For this part of my homepage, my requirements are:

1. I need to update it frequently, so I can’t use a tool like Docusaurus that requires frequent recompilation.
2. The blog page should be simple, with only the necessary navigation and search tools.
3. It should update quickly on GitHub.
4. It should be lightweight, requiring little programming, and allowing me to focus on writing.

After trying several tools, I finally chose **MkDocs**, because it meets all the above needs. Next comes my MkDocs configuration guide and usage notes!

---

## 1. Setting Up MkDocs on macOS

**(1) Install Python & MkDocs**

If Python3 is not installed, first install [Homebrew](https://brew.sh/):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install Python3 and pip:

```bash
brew install python3
```

Install MkDocs:

```bash
pip install mkdocs
```

Recommended: install the popular and elegant Material theme:

```bash
pip install mkdocs-material
```

---

**(2) Create Your First MkDocs Project**

Go to the folder where you want to write your blog:

```bash
mkdocs new my-blog
cd my-blog
```

This generates a basic structure:

```
my-blog/
  mkdocs.yml      # configuration file
  docs/
    index.md      # homepage content
```

---

**(3) Local Preview**

Run the following in the project root:

```bash
mkdocs serve
```

Then open `http://127.0.0.1:8000` in your browser to preview in real time.

---

**(4) Upload to GitHub and Enable GitHub Pages**

Initialize Git:

```bash
git init
git add .
git commit -m "first mkdocs blog"
git branch -M main
git remote add origin git@github.com:ZihanNing/my-blog.git
```

Deploy to GitHub Pages:

```bash
mkdocs gh-deploy
```

After deployment, GitHub Pages will automatically build and host your site. You can confirm the published address under **Settings → Pages** in your repository. For future updates, just run `mkdocs gh-deploy` and your site will be online in seconds.

---

## 2. Adding Search and Language Switch in MkDocs

**(1) Search Function**

The Material theme comes with search functionality. Ensure your `mkdocs.yml` includes:

```yaml
plugins:
  - search
```

This will add a search box in the top right corner.

---

**(2) Multilingual Support (i18n Plugin)**

Install the plugin:

```bash
pip install mkdocs-static-i18n
```

Configure `mkdocs.yml`:

```yaml
plugins:
  - search
  - i18n:
      docs_structure: suffix
      reconfigure_material: true        # enable Material’s language switcher
      fallback_to_default: true         # show Chinese if English is missing
      languages:
        - locale: zh
          name: 中文
          default: true
        - locale: en
          name: English
```

Then create two files in the `docs/` directory:

```
index.zh.md
index.en.md
```

When visiting the page, a language switcher (中文/English) will automatically appear in the top-right corner.

---

✨ Now you have a lightweight blogging system that supports both English/Chinese switching and search.
To update, simply add new markdown files under `docs/` and run:

```bash
mkdocs gh-deploy
```

Your GitHub Pages site will be updated instantly.

---

## Common SOP (Standard Operating Procedures)

### A. Add a New Article

1. Create new Markdown files under `docs/`:

   ```bash
   touch docs/tutorial1.zh.md
   touch docs/tutorial1.en.md
   ```
2. Add links to `nav` in `mkdocs.yml`:

   ```yaml
   nav:
     - Home: index.md
     - Tutorials:
         - 教程一: tutorial1.zh.md
         - Tutorial 1: tutorial1.en.md
   ```
3. Save, then preview or publish as needed.

---

### B. Local Debugging

> ⚠️ If you installed MkDocs and its plugins inside a virtual environment (`.venv`), you must activate it first.

1. Activate the virtual environment:

   ```bash
   source .venv/bin/activate
   ```

   (You’ll see `(.venv)` at the start of the command line once activated.)
2. Start local preview:

   ```bash
   mkdocs serve
   ```
3. Open `http://127.0.0.1:8000` in your browser. Edits will auto-refresh.

Exit the virtual environment:

```bash
deactivate
```

---

### C. One-Click Deployment

1. Activate the virtual environment (if using `.venv`):

   ```bash
   source .venv/bin/activate
   ```
2. Deploy to GitHub Pages:

   ```bash
   mkdocs gh-deploy
   ```

Your site will update on GitHub Pages within seconds.

