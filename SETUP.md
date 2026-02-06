# Profile README – Workflows & Actions Setup

This repo is your **GitHub profile repository** (`roshaanmehar/roshaanmehar`). The README is shown on [github.com/roshaanmehar](https://github.com/roshaanmehar). Two workflows run automatically to keep the contribution snake and the space shooter GIF up to date.

---

## 1. Make sure this is your profile repo

- The profile repo **must** be named exactly like your GitHub username: `roshaanmehar`.
- If you created it with another name, rename it: **Settings → General → Repository name** → set to `roshaanmehar` → **Rename**.
- Default branch should be `main` (or update the README image URL for the space shooter if you use `master`).

---

## 2. Enable GitHub Actions

1. Open **https://github.com/roshaanmehar/roshaanmehar**
2. Go to **Settings → Actions → General**
3. Under **Actions permissions**, choose **Allow all actions and reusable workflows**
4. Click **Save**

---

## 3. Snake workflow (contribution snake)

**File:** `.github/workflows/main.yml`

**What it does:** Uses [Platane/snk](https://github.com/Platane/snk) to generate the contribution snake SVGs and deploys them to the `output` branch. The README loads them from:

- `https://raw.githubusercontent.com/roshaanmehar/roshaanmehar/output/github-snake.svg` (light)
- `https://raw.githubusercontent.com/roshaanmehar/roshaanmehar/output/github-snake-dark.svg` (dark)

**Triggers:**

- Daily at **00:00 UTC**
- On **push to `main`**
- **Manual:** Actions → **GitHub Snake Game** → **Run workflow**

**No extra setup.** `GITHUB_TOKEN` is provided by GitHub; the workflow has permission to push to the `output` branch.

**First time / troubleshooting:**

1. Push a commit to `main` (e.g. this README) so the workflow runs.
2. After it runs, check that branch **output** exists and contains `github-snake.svg` and `github-snake-dark.svg`.
3. If the snake doesn’t show in the README, confirm the repo name is exactly `roshaanmehar` and the URLs above are correct.

---

## 4. Space shooter workflow (retro game GIF)

**File:** `.github/workflows/update-game.yml`

**What it does:** Uses [czl9707/gh-space-shooter](https://github.com/czl9707/gh-space-shooter) to turn your contribution graph into a GIF, then commits it as `game.gif` on the default branch. The README shows it in the “Space shooter” section.

**Triggers:**

- Daily at **00:00 UTC**
- **Manual:** Actions → **Update Space Shooter Game** → **Run workflow**

**No extra setup.** The action needs `contents: write` (already set in the workflow) so it can commit and push `game.gif`.

**First time:**

1. Push this repo (including `.github/workflows/update-game.yml`) to GitHub.
2. Go to **Actions** → **Update Space Shooter Game** → **Run workflow** → **Run workflow**.
3. Wait for the run to finish (a few minutes). The action will commit `game.gif` to `main`.
4. Refresh your profile; the space shooter section should show the GIF.

**If the GIF doesn’t appear:**

- Open the latest **Update Space Shooter Game** run and check that all steps are green.
- On the **Code** tab, confirm `game.gif` exists in the root of `main`.
- The README uses:  
  `https://raw.githubusercontent.com/roshaanmehar/roshaanmehar/main/game.gif`  
  If your default branch is not `main`, change that URL in the README to use your branch name.

---

## 5. Pushing this repo to GitHub

If this folder is a clone or copy of your profile repo:

```bash
cd R:\Code\github-retro\roshaanmehar-main

# If it’s not a git repo yet:
git init
git remote add origin https://github.com/roshaanmehar/roshaanmehar.git

# Add and push
git add .
git commit -m "Revamp profile README, add space shooter workflow"
git branch -M main
git push -u origin main
```

If it’s already a clone:

```bash
git add .
git commit -m "Revamp profile README, add space shooter workflow"
git push origin main
```

After the push:

1. **Snake:** The **GitHub Snake Game** workflow will run (schedule or push). Ensure the **output** branch gets created/updated.
2. **Space shooter:** Go to **Actions → Update Space Shooter Game → Run workflow**. After it finishes, `game.gif` will be on `main` and visible on your profile.

---

## 6. Summary

| Item | Where | Action needed |
|------|--------|----------------|
| Profile repo name | GitHub repo settings | Must be `roshaanmehar` |
| Actions enabled | Settings → Actions | Allow actions |
| Snake assets | Branch `output` | Auto after workflow run |
| Space shooter GIF | File `game.gif` on `main` | Auto after workflow run |
| Manual run | Actions tab | Use “Run workflow” for each workflow |

No secrets or tokens are required beyond the default `GITHUB_TOKEN` that GitHub provides to Actions.
