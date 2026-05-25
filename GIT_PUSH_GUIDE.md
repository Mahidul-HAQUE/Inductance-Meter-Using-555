# How to Push This Repo to GitHub

Follow these steps exactly on your local machine.

---

## Step 1 — Install Git (if not already installed)

**Windows:** Download from https://git-scm.com/download/win and install.  
**Linux:** `sudo apt install git`  
**macOS:** `brew install git` or it may already be installed.

Verify: `git --version`

---

## Step 2 — Configure Git (first time only)

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## Step 3 — Create the GitHub Repository

1. Go to https://github.com and log in.
2. Click the **+** icon → **New repository**.
3. Name it: `inductance-meter-555`
4. Set it to **Public** or **Private** as you prefer.
5. **Do NOT** check "Add README" or any other initialization option.
6. Click **Create repository**.
7. Copy the repository URL — it will look like:  
   `https://github.com/YOUR_USERNAME/inductance-meter-555.git`

---

## Step 4 — Set Up the Local Repo

Download or unzip the repo folder on your machine, then open a terminal inside it:

```bash
cd inductance-meter-555
git init
git add .
git commit -m "Initial commit: Inductance meter using 555 timer IC"
```

---

## Step 5 — Add the Proteus File

Copy your Proteus file into the `simulation/` folder. The filename should be:

```
inductor meter.pdsprj
```

Then stage and commit it:

```bash
git add "simulation/inductor meter.pdsprj"
git commit -m "Add Proteus simulation file"
```

---

## Step 6 — Connect to GitHub and Push

```bash
git remote add origin https://github.com/YOUR_USERNAME/inductance-meter-555.git
git branch -M main
git push -u origin main
```

You will be prompted for your GitHub username and password.  
> ⚠️ If you have 2FA enabled, GitHub no longer accepts your password directly.  
> Use a **Personal Access Token** instead of your password.  
> Generate one at: GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token (check `repo` scope).

---

## Step 7 — Verify

Go to `https://github.com/YOUR_USERNAME/inductance-meter-555` in your browser.  
You should see the full repo with the README rendered.

---

## Quick Reference (all commands together)

```bash
cd inductance-meter-555
git init
git add .
git commit -m "Initial commit: Inductance meter using 555 timer IC"
git remote add origin https://github.com/YOUR_USERNAME/inductance-meter-555.git
git branch -M main
git push -u origin main
```

---

## Future Updates

After the initial push, every time you make changes:

```bash
git add .
git commit -m "Describe what you changed"
git push
```
