# 🧰 Git: My All-in-One Code & Project Management SOP (Sanitized)

I started using GitHub quite early, but I didn’t really manage **all my projects and code systematically** with Git until after finishing my PhD. As I began working across multiple servers and developing larger projects that needed regular releases, Git became an essential part of my workflow. Soon, I was using Git for almost everything — even this blog 📝 is managed with Git!

Here’s my personal **Git SOP** — a handy reference for myself and hopefully useful for you too.

---

## 1️⃣ Install Git

My daily environments:

* Work servers: Ubuntu Linux
* Personal laptop: MacBook Air

Here’s how to install Git on both.

### 🐧 Linux (Ubuntu)

```bash
sudo apt update
sudo apt install git -y
git --version   # verify installation
```

> ⚠️ Always run `apt update` before installing to avoid outdated versions.

### 🍎 macOS

macOS usually comes with Git preinstalled. If not, or if you want the latest version:

```bash
git --version   # check current version
brew install git
```

> If you don’t have Homebrew yet:
>
> ```bash
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
> ```

---

## 2️⃣ Create a GitHub Account

1. Go to [GitHub](https://github.com/)
2. Click **Sign up**
3. Set username, email, and password
4. Verify your email
5. (Recommended) Generate an SSH key or Personal Access Token for smoother pushes later (see token/SSH section below)

---

## 3️⃣ Configure Your Local Git Account

```bash
git config --global user.name "<your-github-username>"
git config --global user.email "<your-email@example.com>"
git config --global init.defaultBranch main  # set default branch name to main
```

---

## 4️⃣ Initialize a Local Git Repository

```bash
git init  # initialize git
ls -a     # check that the .git folder exists

git switch -c main  # create and switch to the main branch (recommended syntax)

# If you need to ignore certain files:
nano .gitignore
# Sample .gitignore
# DATA_DUMP/
# MRD_input/
# MRD_output/
# raw/
# temp/
# *.evp

git add .gitignore
git commit -m "Ignore data files and results folder"
git status              # check tracked files
git status --ignored    # see ignored files
```

---

## 5️⃣ Push Local Repo to a Remote Repo

```bash
git remote add origin https://github.com/<your-github-username>/<repo_name>.git
git remote -v   # verify remote link

# If you added the wrong remote, remove and re-add:
git remote remove origin

# Stage, commit, and push
git status
git add .                # stage all changes
git commit -m "Commit message"
git push origin main     # push to remote main branch
```

🔑 **Token Login (HTTPS):**
GitHub > Settings > Developer settings > Personal access tokens > Tokens (classic) > Generate new token
Select `repo` scope, copy the token, and paste it when prompted for a password.

---

## 6️⃣ Clone a Repo on a New Machine

When working on a new PC or server:

```bash
git clone https://github.com/<your-github-username>/<repo_name>.git
cd <repo_name>
```

If using SSH (recommended):

```bash
ssh-keygen -t rsa -b 4096 -C "<your-email@example.com>"
cat ~/.ssh/id_rsa.pub   # copy to GitHub -> Settings -> SSH and GPG keys
ssh -T git@github.com   # test connection
# Then you can use:
# git clone git@github.com:<your-github-username>/<repo_name>.git
```

---

## 7️⃣ Sync Updates from Remote Repo

When PC1 has updates and you need to sync on PC2:

```bash
git fetch origin         # fetch updates
git status               # check if your local branch is behind
git pull origin main     # pull and merge changes
```

> 💡 Resolve conflicts if necessary, then `git add . && git commit` to continue.

---

## 8️⃣ Revert to a Previous Version

View commit history:

```bash
git log --oneline
```

Switch or reset to a specific commit:

```bash
git checkout <commit-hash>      # temporarily check out (detached HEAD)
# or
git reset --hard <commit-hash>  # force rollback (⚠️ discards uncommitted changes)
```

> ⚠️ Use `reset --hard` with caution — it will permanently discard local changes.

---

## 9️⃣ Compare Files (Diff)

1. **Compare branches:**

```bash
git diff branchA..branchB
```

2. **Compare commits:**

```bash
git diff <commit1> <commit2> -- path/to/file
```

3. **Compare working directory vs staged:**

```bash
git diff path/to/file
```

---

## 🔟 Release a Private Repo Version

When you want to release a specific version:

```bash
git tag -a v1.0 -m "Release v1.0"
git push origin v1.0
```

Then go to GitHub **Releases**, select the tag, add release notes, and publish.
