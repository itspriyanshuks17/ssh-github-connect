## Connect GitHub with SSH on Windows

### 1. **Install Git for Windows**

If you haven't already, install Git:
👉 [https://git-scm.com/download/win](https://git-scm.com/download/win)

Make sure you **select “Git Bash”** during installation — you'll use it for commands.

---

### 2. **Open Git Bash**

Right-click on your desktop or in a folder → choose **"Git Bash Here"**.

---

### 3. **Generate an SSH Key**

Run this in Git Bash:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

* Press **Enter** to accept the default file location (`/c/Users/YourName/.ssh/id_ed25519`)
* You can add a passphrase or leave it empty

---

### 4. **Start the SSH Agent and Add the Key**

In Git Bash, run:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

You should see something like:

```
Agent pid 5954
Identity added...
```

---

### 5. **Copy the Public Key**

Run this to copy the key:

```bash
clip < ~/.ssh/id_ed25519.pub
```

This copies the key to your clipboard.

---

### 6. **Add SSH Key to GitHub**

1. Go to: [https://github.com/settings/keys](https://github.com/settings/keys)
2. Click **New SSH key**
3. Paste the key (from clipboard) into the **Key** field
4. Give it a **title** like "My Windows PC"
5. Click **Add SSH key**

---

### 7. **Test SSH Connection**

Back in Git Bash:

```bash
ssh -T git@github.com
```

If it works, you’ll see:

```
Hi your-username! You've successfully authenticated...
```

If you see a warning about authenticity, type `yes` and press Enter.

---

### 8. **Use SSH to Clone Repos**

Now you can use SSH URLs:

```bash
git clone git@github.com:username/repo.git
```

To switch an existing project from HTTPS to SSH:

```bash
git remote set-url origin git@github.com:username/repo.git
```

---

## 💡 Optional Tips

* Make sure your key is persistent across reboots (you can use **Windows Credential Manager** or set up autoloading).
* If you use **VS Code**, it uses Git Bash/SSH automatically when configured.
