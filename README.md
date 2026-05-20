# PLEDGE project management

- **`vault/`** — Obsidian vault (open this folder in Obsidian)
- **`site/`** — Quartz publisher for GitHub Pages
- **Live site:** https://nichollsharrisonj.github.io/PLEDGE_project_page/

## Obsidian

Open `vault/` as the vault root.

## Publish

```bash
cd site
npm ci
npx quartz build --serve --directory ../vault
```

Pushes to `main` deploy via `.github/workflows/deploy.yml`.
