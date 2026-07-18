# Setup Instructions

## 1. Create the profile repository

- Create a new **public** repository named exactly: `Anurag-gg04`
  (must match your GitHub username exactly — this is what makes GitHub render it on your profile page)

## 2. Add the files

Copy this structure into the repository root:

```
Anurag-gg04/
├── README.md
├── SETUP.md
└── .github/
    └── workflows/
        ├── snake.yml
        └── metrics.yml
```

## 3. Enable GitHub Actions

- Go to the repo's **Settings → Actions → General**
- Under "Actions permissions," select **Allow all actions and reusable workflows**
- Under "Workflow permissions," select **Read and write permissions** (required so the workflows can push the snake SVG and metrics SVG back to the repo)

## 4. Set up the Snake Animation

- No extra secrets needed — it uses the default `GITHUB_TOKEN`.
- Go to the **Actions** tab → select **Generate Snake Animation** → **Run workflow** (manual trigger for the first run).
- After it completes, an `output` branch will be created containing the generated SVGs. The README already points to that branch, so the animation will appear automatically once it exists.

## 5. Set up Live Metrics

- The metrics workflow needs a **Personal Access Token** (the default `GITHUB_TOKEN` doesn't have enough scope for some plugins):
  1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)**
  2. Generate a new token with the `repo` and `read:user` scopes
  3. In your `Anurag-gg04` repo, go to **Settings → Secrets and variables → Actions**
  4. Add a new secret named `METRICS_TOKEN` and paste the token
- Go to the **Actions** tab → select **Update Profile Metrics** → **Run workflow** (manual trigger for the first run).
- This commits `github-metrics.svg` to the `main` branch, which the README already references.

## 6. Verify

- Visit `github.com/Anurag-gg04` and confirm:
  - Typing header, banner, and stats cards render
  - Snake animation appears (may take a few minutes after the first workflow run)
  - Metrics SVG appears (same — allow a few minutes after first run)
- Both workflows are scheduled to auto-refresh afterward (snake: daily, metrics: every 6 hours) — no further action needed.

## 7. Customize

- Replace project descriptions/links in `README.md` as your repositories evolve.
- Badge colors, theme names (`tokyonight`), and banner gradient colors in the `capsule-render` URLs can be swapped for any other supported theme if you want a different palette later.
