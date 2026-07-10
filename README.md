# PLEDGE project management

- **`vault/`**: Obsidian vault (open this folder in Obsidian)
- **`site/`**: Quartz publisher for GitHub Pages
- **Site:** https://nichollsharrisonj.github.io/PLEDGE_project_page/

## How to use in Obsidian

Open `vault/` as the vault root.

## Publish

```bash
cd site
npm ci
npx quartz build --serve --directory ../vault
```

Pushes to `main` deploy with `.github/workflows/deploy.yml`.
