# 🖥️ tmux – Keep your terminal running even after disconnect 🚀

## When to use 🌟

Do you often need to:

* Run **long-time jobs** on a **remote server** (e.g. model training, simulations, or a Gadgetron client)?
* Worry that closing your laptop / losing SSH will kill your job?
* Want to **detach** and **re-attach** your session from different places?

Then **tmux** is your friend! It lets you run tasks in a “virtual terminal” that survives even after you disconnect.

---

## Background

I maintain our hospital’s **inline reconstruction platform**, mainly based on [Gadgetron](https://github.com/gadgetron/gadgetron). We’ve developed and ported multiple reconstruction algorithms on this platform (see [my framework here](https://github.com/ZihanNing/Practical_Inline_Recon_Framework-public.git)).

One key application is the **head motion correction algorithm**, which is regularly used in the **TwinsUK Project** (every Wednesday and Thursday, \~16 participants per week).

To keep everything stable, maintenance staff need to:

* ✅ Make sure the **Gadgetron client** is activated on the server every week
* ✅ Access the **Gadgetron server log** at any time

Since I often work from home, I need a reliable way to keep the client running even if I close my laptop or drop the SSH connection. The solution: **tmux!**

---

## Step 1. Connect to the Gadgetron server

Because the server is inside the hospital’s intranet, I can’t SSH directly — I need to go through a **bouncer (jump host)**.

First, from my Macbook Air:

```bash
ssh -L 4003:<gadgetron_server_ID>:4000 <user>@bouncer.<bouncer_address>
```

* `-L` sets up port forwarding (here mapping local port 4003 → server port 4000).

Then, from inside the bouncer, I SSH into the Gadgetron server:

```bash
ssh gadgetron@<gadgetron_server_ID>
```

---

## Step 2. Start Gadgetron client inside a tmux session

If I just run the client in the SSH session, it will stop as soon as I disconnect.
**Solution: run it inside tmux, which keeps it alive in the background.**

Create a new tmux session (name it, e.g. `gadgetron_client`):

```bash
tmux new -s <session_name>
```

Inside the session, start the client (I use my helper script):

```bash
./activate_gadgetron.sh
```

👉 This script starts the Gadgetron client on **port 9002** and keeps it running.

To detach (let it run in the background):

```
Ctrl+b then d
```

Even if you close your laptop or end SSH, the process keeps running!

---

## Step 3. Re-attach later

To get back to the session:

```bash
tmux attach -t <session_name>
```

Forgot the name? List sessions first:

```bash
tmux ls
```

---

## ⚡ Common pitfalls & tips

* **Forgot the session name?**
  Use `tmux ls` to list them.

* **Session crashed but still exists?**
  Kill it and restart:

  ```bash
  tmux kill-session -t <session_name>
  ```

* **Too many sessions?**
  Clean them up with `tmux kill-session` or by pruning unused ones.

* **Port already in use (9002)?**
  Check with:

  ```bash
  lsof -i:9002
  ```

  Then stop the blocking process.

* **Quick log check** 📜
  Instead of opening another terminal, just run:

  ```bash
  tail -f log/subcall_log_xxx.txt
  ```

  inside your tmux session.

---

## 🎉 Wrap-up

With `tmux`, I can run a **long-lived Gadgetron client** safely on the server, without worrying about SSH disconnects or laptop sleep.

This makes WFH much smoother while keeping the TwinsUK inline reconstruction pipeline **stable** 💪

