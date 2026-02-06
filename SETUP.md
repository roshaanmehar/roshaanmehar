# How to set up your GitHub profile README (beginner guide)

This guide assumes you have never set up a GitHub profile or used Actions. Follow the steps in order.

---

## What you’re doing

- **GitHub** = A website where people host code and collaborate. Your “profile” is your personal page (like `github.com/roshaanmehar`).
- **Profile README** = A special page that only you can edit. It’s the big block of text and images on your profile. It comes from a **repository** (a folder of files) that has the **same name as your username**.
- **This folder** = The contents of that repository on your computer. You will put this onto GitHub so your profile shows the new README and the two “automatic” features: the **snake** and the **space shooter game**.

---

## Part 1: Get your profile repository on GitHub

### Step 1.1 – Log in to GitHub

1. Open a web browser (Chrome, Edge, Firefox, etc.).
2. Go to: **https://github.com**
3. Log in. If you don’t have an account, click **Sign up** and create one (free).

### Step 1.2 – Create the profile repository (if it doesn’t exist yet)

Your profile README is shown from a repo that **must** be named exactly like your username. For you, that’s **roshaanmehar**.

1. On GitHub, click the **+** (plus) at the top right.
2. Click **New repository**.
3. In **Repository name**, type exactly: **roshaanmehar**  
   (no spaces, no capitals, no extra words).
4. Set **Public**.
5. **Do not** check “Add a README file” (you already have one in this folder).
6. Click **Create repository**.

If you already have a repo named **roshaanmehar**, skip to Step 1.3.

### Step 1.3 – Check the repository name

1. Open: **https://github.com/roshaanmehar**
2. You should see your profile. Under your name you should see a repo called **roshaanmehar**. Click it.
3. The address should be: **https://github.com/roshaanmehar/roshaanmehar**
4. If the repo has a different name (e.g. `roshaanmehar-main` or `my-profile`), you must rename it:
   - Open that repo → **Settings** (top menu) → under **General**, find **Repository name**.
   - Change it to **roshaanmehar** and click **Rename**.

---

## Part 2: Put your files on GitHub

You need to upload the contents of the **roshaanmehar-main** folder (README, SETUP, and the `.github` folder) into the **roshaanmehar** repo. You can do that in two ways.

### Option A – Upload without installing Git (easiest)

1. Go to **https://github.com/roshaanmehar/roshaanmehar**
2. If the repo is empty, you’ll see “uploading an existing file”. Click **uploading an existing file**.
3. Open the folder on your PC: **R:\Code\github-retro\roshaanmehar-main**
4. Drag these into the browser window (or use “choose your files”):
   - **README.md**
   - **SETUP.md**
   - The whole **.github** folder (with **workflows** inside it, and inside workflows: **main.yml** and **update-game.yml**)
5. At the bottom, in the first box, type a short message like: **Update profile README**
6. Click **Commit changes**.

If the repo already has files (e.g. an old README):

1. Open the repo → click **Add file** → **Upload files**.
2. Drag **README.md**, **SETUP.md**, and the **.github** folder.
3. Commit as above. If it asks for a branch, use **main**.

**Important:** The structure on GitHub must look like this:

```
roshaanmehar (repo)
├── README.md
├── SETUP.md
└── .github
    └── workflows
        ├── main.yml
        └── update-game.yml
```

### Option B – Using Git on your computer

Use this only if you already use Git and have this folder as a clone of your repo.

1. Open **Command Prompt** or **PowerShell**.
2. Go to the folder:
   ```bash
   cd R:\Code\github-retro\roshaanmehar-main
   ```
3. If this folder is not yet a Git repo linked to GitHub:
   ```bash
   git init
   git remote add origin https://github.com/roshaanmehar/roshaanmehar.git
   git branch -M main
   ```
4. Add, commit, and push:
   ```bash
   git add .
   git commit -m "Update profile README and workflows"
   git push -u origin main
   ```
5. If it asks for a username and password: use your GitHub username and a **Personal Access Token** (not your normal password). You can create a token at: GitHub → **Settings** → **Developer settings** → **Personal access tokens**.

---

## Part 3: Turn on GitHub Actions

**Actions** are automatic tasks that run on a schedule or when you click “Run”. Your profile uses two: one for the snake, one for the space shooter. They must be allowed to run.

1. Go to **https://github.com/roshaanmehar/roshaanmehar**
2. Click **Settings** (top menu of the repo).
3. In the left sidebar, click **Actions** → **General**.
4. Under **Actions permissions**, select: **Allow all actions and reusable workflows**.
5. Click **Save**.

---

## Part 4: Run the workflows (first time)

### 4.1 – Snake (contribution snake)

1. In your **roshaanmehar** repo, click **Actions** (top menu).
2. In the left list, click **GitHub Snake Game**.
3. On the right, click **Run workflow** → **Run workflow**.
4. Wait 1–2 minutes. The list will show a run with a yellow dot (running) then a green tick (done).
5. When it’s green, the snake images are on a branch called **output**. Your README already points to them; refresh your profile page to see the snake.

### 4.2 – Space shooter (game GIF)

1. Still in **Actions**, click **Update Space Shooter Game** in the left list.
2. Click **Run workflow** → **Run workflow**.
3. Wait a few minutes (the game takes longer to generate).
4. When the run is green, the workflow has created **game.gif** and pushed it to your **main** branch. Refresh your profile; the space shooter section should show the GIF.

If you don’t see the GIF right away, wait a minute and refresh again. The README loads it from GitHub’s servers.

---

## Part 5: Check your profile

1. Open **https://github.com/roshaanmehar** (your profile, not the repo).
2. You should see:
   - Your new intro and “About me”
   - Projects with links
   - Tech and stats
   - The contribution snake
   - The space shooter GIF (after Part 4.2 has run successfully)
   - Contact links at the bottom

---

## What runs automatically from now on

- **Snake:** The “GitHub Snake Game” workflow runs every day at midnight (UTC) and when you push to **main**. It keeps the snake in sync with your contributions.
- **Space shooter:** The “Update Space Shooter Game” workflow runs every day at midnight (UTC). You can also run it anytime from **Actions** → **Update Space Shooter Game** → **Run workflow**.

You don’t need to do anything else unless you change the README or the workflow files.

---

## If something doesn’t work

### The snake doesn’t show

- Make sure the repo is named **roshaanmehar** (same as your username).
- In the repo, go to **Actions** and check that “GitHub Snake Game” has at least one run with a green tick.
- Click that run and make sure every step (e.g. “Generate GitHub Contributions Snake Animations”, “Deploy to Output Branch”) is green.
- On the repo’s **Code** tab, check the branch dropdown: you should see a branch called **output**. Open it and confirm files like **github-snake.svg** are there.

### The space shooter GIF doesn’t show

- In **Actions**, open **Update Space Shooter Game** and run it once manually. Wait until the run finishes (green).
- On the **Code** tab (main branch), look in the root folder for **game.gif**. If it’s there, the README should show it; try a hard refresh (Ctrl+F5) on your profile page.
- If your default branch is **master** instead of **main**, the README currently expects **main**. Either rename the branch to **main** in repo Settings, or edit README.md and replace `main` with `master` in the game.gif URL.

### “Actions” is disabled or I don’t see Run workflow

- In the repo go to **Settings** → **Actions** → **General** and set **Allow all actions and reusable workflows**, then Save.
- If your account or org has restricted Actions, you may need to change that in your account/org settings.

### I don’t see the roshaanmehar repo / I get 404

- The profile repo **must** be under your account and named **exactly** like your username (e.g. **roshaanmehar**). Check the URL: it must be **github.com/roshaanmehar/roshaanmehar**.

---

## Words used in this guide

| Word | Meaning |
|------|--------|
| **GitHub** | The website (github.com) where you store code and your profile. |
| **Repository / repo** | A project folder on GitHub. One repo = one project. |
| **Profile** | Your public GitHub page (e.g. github.com/roshaanmehar). |
| **README** | The main text file (README.md) that describes a repo. On your profile repo, this text is shown on your profile. |
| **Branch** | A version of the repo. **main** is usually the default. The snake uses a second branch called **output**. |
| **Actions** | GitHub’s way of running automated tasks (workflows) on a schedule or when you trigger them. |
| **Workflow** | One automatic task (e.g. “generate snake”, “generate game GIF”). Defined by a file in `.github/workflows/`. |
| **Run workflow** | The button you click to start a workflow by hand. |
| **Push** | Sending your local files to GitHub (when using Git). |
| **Commit** | Saving a snapshot of your changes (one step before push when using Git). |

---

You’re done. Your profile README is updated, and the snake and space shooter will keep updating automatically. For daily use, you only need to push changes to README or run a workflow manually if you want a fresh GIF right away.
