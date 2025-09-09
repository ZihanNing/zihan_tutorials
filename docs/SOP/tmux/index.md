# 🖥️ tmux – 让 terminal 脱离笔电也能继续跑 🚀

## 适用场景 🌟

如果你经常需要：

* 在 **远程服务器** 上跑一些 **长期任务**（比如训练模型、跑仿真、跑 Gadgetron client）；
* 担心 **笔记本断网/休眠/关掉 SSH** 就导致程序被杀掉；
* 想随时 **detach** 和 **re-attach**，在不同地方继续工作；

那你就一定要试试 **tmux**！它能帮你把任务挂在后台，像开了个“虚拟屏幕”一样随时进入/退出。

---

## 背景

我平时负责医院里 **inline reconstruction 平台**的维护工作，目前主要基于 [Gadgetron](https://github.com/gadgetron/gadgetron) 搭建。我们在这个平台上开发和移植了不少重建算法（详见 [我的框架介绍](https://github.com/ZihanNing/Practical_Inline_Recon_Framework-public.git)）。其中，**head motion correction 重建算法**会在 **TwinsUK Project** 的扫描中定期使用（基本上每周三、四，大约 16 人次）。

为了保证平台稳定运行，维护人员需要做到两点：

* ✅ 确保 **Gadgetron client** 每周在 server 上被正确激活
* ✅ 能随时远程读取 **Gadgetron server log**

问题是：我经常需要远程办公。所以，怎么保证 **client 持续运行** 且 **我断开 SSH 后不受影响**？答案就是：**tmux！**

---

## Step 1. 从本地电脑登录 Gadgetron server

由于 server 在医院内网，不能直接 SSH，需要先通过 **bouncer** 作为跳板机。

先在本地（Macbook Air）打开 terminal，输入：

```bash
ssh -L 4003:<gadgetron_server_ID>:4000 <user>@bouncer.<bouncer_address>
```

* `-L` 用于端口转发，这里是把本地的 4003 端口映射到内网 Gadgetron server 的 4000 端口。

进入 bouncer 后，再跳转到 Gadgetron server：

```bash
ssh gadgetron@<gadgetron_server_ID>
```

---

## Step 2. 在 server 上用 tmux 开启 gadgetron client

如果直接在 SSH session 里跑 client，一旦关闭笔电终端，程序就会中断。
**解决办法：用 tmux 开启一个独立的“持久化终端”。**

新建一个 tmux 会话（`-s` 后面是给会话起的名字，比如 `gadgetron_client`）：

```bash
tmux new -s <the_name_of_terminal>
```

进入会话后，就可以启动 Gadgetron client（这里用的是我写的脚本）：

```bash
./activate_gadgetron.sh
```

👉 这个脚本会在 **9002 端口**上启动 Gadgetron client，保持运行状态。

如果想让 tmux 会话在后台继续跑，只需 **detach**：

```
Ctrl+b 然后按 d
```

这样即使你关掉 Macbook 的 SSH 终端，client 也不会被杀掉。

---

## Step 3. 重新进入 tmux 会话

当你下次想查看 log 或确认 client 状态时，可以重新 attach 回去：

```bash
tmux attach -t <the_name_of_terminal>
```

如果忘了会话名，可以先列出所有 tmux 会话：

```bash
tmux ls
```

---

## ⚡ 常见坑 & 小贴士

* **会话忘记名字？**
  用 `tmux ls` 查一下。

* **会话挂掉了？**
  有时候脚本跑挂了，会话还在。可以先退出：

  ```bash
  tmux kill-session -t <the_name_of_terminal>
  ```

  然后重新开一个。

* **开太多会话？**
  注意 `tmux ls` 会列出来所有会话，保持干净有序比较好维护。

* **端口冲突？**
  如果 Gadgetron client 启动时 9002 已经被占用，可以用 `lsof -i:9002` 查看占用进程并结束它。

* **日志快速查看** 📜
  想实时盯日志，可以直接在 tmux 里跑：

  ```bash
  tail -f log/subcall_log_xxx.txt
  ```

  这样就不用每次新开窗口了。

---

## 🎉 总结

利用 `tmux`，我就能在远程 server 上挂一个 **长期运行的 gadgetron client**，而不用担心关掉 SSH 或笔记本休眠后进程被中断。

这样一来，我就可以安心 WFH，同时保持 TwinsUK Project 的 inline reconstruction 平台 **稳定运行**！💪

