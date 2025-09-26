# 🧰 Git：一站式管理我的所有代码/项目（脱敏版）

虽然开始接触 GitHub 很早，但我真正用 Git **系统化管理所有项目和代码**，是从博士毕业后才开始的。随着我在多台服务器之间切换、开发更大型、需要定期发布的项目，Git 成了不可或缺的工具。后来就一发不可收拾，几乎所有的项目（包括这个 Blog 📝）都用 Git 来管理。

这里写一份 **Git 使用手册 SOP**，既方便自己查阅，也方便朋友们参考。

---

## 1️⃣ Install Git

我的日常电脑环境：

* 单位服务器：Ubuntu Linux
* 个人笔记本：MacBook Air

因此这里总结两种常见平台的安装方法。

### 🐧 Linux (Ubuntu)

```bash
sudo apt update
sudo apt install git -y
git --version   # 验证安装
```

> ⚠️ 建议始终 `apt update` 后再安装，避免版本过老。

### 🍎 macOS

macOS 通常自带 Git，如果没有或想升级，可以用 Homebrew 安装：

```bash
git --version   # 检查版本
brew install git
```

> 如果没有安装 Homebrew，先运行：
>
> ```bash
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
> ```

---

## 2️⃣ 创建 GitHub 账号

1. 访问 GitHub 官网
2. 点击 **Sign up** 注册账号
3. 设置用户名、邮箱、密码
4. 验证邮箱，完成注册
5. 建议在个人设置里生成一个 SSH key 或 Personal Access Token，后续推送会更方便（详见下面 token/SSH 教程）

---

## 3️⃣ 在本地 Git 上登陆个人账号

```bash
git config --global user.name "<your-github-username>"
git config --global user.email "<your-email@example.com>"
git config --global init.defaultBranch main  # 建议设置默认分支为 main
```

---

## 4️⃣ 在需托管文件夹中建立 Git Repo

```bash
git init  # 初始化 git
ls -a     # 确认 .git 文件夹已创建

git switch -c main  # 创建并切换到 main 分支 (新版推荐)

# 如果需要忽略某些文件，建立 .gitignore
nano .gitignore
# 示例 .gitignore
# DATA_DUMP/
# MRD_input/
# MRD_output/
# raw/
# temp/
# *.evp

git add .gitignore
git commit -m "Ignore data files and results folder"
git status              # 查看追踪文件状态
git status --ignored    # 查看被忽略的文件
```

---

## 5️⃣ 将本地 Repo 提交到 Remote Repo

```bash
git remote add origin https://github.com/<your-github-username>/<repo_name>.git
git remote -v   # 验证远程地址

# 如果加错了远程仓库地址，可以先移除再重新添加
git remote remove origin

# 提交并推送
git status
git add .                # 添加所有更改
git commit -m "Commit message"
git push origin main     # 推送到远程 main 分支
```

🔑 **Token 登录（HTTPS 方式）：**
GitHub > Settings > Developer settings > Personal access tokens > Tokens (classic) > Generate new token
勾选 `repo` 权限，复制生成的 token，在命令行提示输入密码时粘贴即可。

---

## 6️⃣ 从 Remote Repo 部署到新机器

当你在新的 PC/server 上工作时，可以用以下命令拉取已有项目：

```bash
git clone https://github.com/<your-github-username>/<repo_name>.git
cd <repo_name>
```

如果你使用 **SSH**，先在本地生成 key 并绑定 GitHub：

```bash
ssh-keygen -t rsa -b 4096 -C "<your-email@example.com>"
cat ~/.ssh/id_rsa.pub   # 复制到 GitHub -> Settings -> SSH and GPG keys
ssh -T git@github.com   # 测试连接（应返回成功握手信息）
# 之后可用 SSH 地址：
# git clone git@github.com:<your-github-username>/<repo_name>.git
```

---

## 7️⃣ 在本地同步 Remote Repo 更新

当你在 PC1 更新了 repo，PC2 需要同步更新：

```bash
git fetch origin         # 获取远程更新
git status               # 确认本地是否落后
git pull origin main     # 拉取最新更改并合并
```

> 💡 如果有冲突，解决冲突后 `git add . && git commit`，再继续工作。

---

## 8️⃣ Revert to Previous Version

查看提交历史：

```bash
git log --oneline
```

回退到某次提交：

```bash
git checkout <commit-hash>      # 临时切换到该提交（detached HEAD）
# 或
git reset --hard <commit-hash>  # 强制回滚到该版本（危险⚠️ 会丢弃未提交修改）
```

> ⚠️ `reset --hard` 会丢弃当前未提交的修改，慎用。

---

## 9️⃣ 文件对比 (Diff)

1. **对比不同 branch：**

```bash
git diff branchA..branchB
```

2. **对比不同提交：**

```bash
git diff <commit1> <commit2> -- path/to/file
```

3. **对比本地文件和暂存区：**

```bash
git diff path/to/file
```

---

## 🔟 Release 私有 Repo

当你想发布某个版本：

```bash
git tag -a v1.0 -m "Release v1.0"
git push origin v1.0
```

然后到 GitHub 的 **Releases** 页面，选择对应 tag，填写 release notes，点击发布即可。
