# Project Rules

各アプリリポジトリへコピーして使う雛形です。リポジトリ固有の値を書き換えて利用してください。

## Repository

- Default branch: main
- Package manager:
- Build command:
- Development command:
- Deploy target:
- Output directory:

## Development Policy

- Work on `main` by default and do not create working branches unless unavoidable.
- If the environment restricts direct push to `main`, state the limitation and proposed workaround.
- Do not include AI signatures or promotional wording in commits, issues, PRs, or generated documents.
- Do not commit secrets.
- Check diffs before committing.
- Write commit messages in Japanese, stating only what changed.

## Deployment

Follow the standard deployment preference:

- Static public frontend: GitHub Pages
- Static private-repository site: ConoHa WING
- Dynamic web application: Cloudflare
- Persistent process / worker / scheduler: Railway
- AWS only when the above options are insufficient.

## Tech Stack

- Prefer `Vite` for build tooling, `pnpm` for prototypes.
- Choose among Vanilla HTML / React + TypeScript / Svelte / SvelteKit per requirements.
- Prefer `MapLibre` for maps; use `Leaflet` only for simple 2D needs.
- Prefer self-contained, API-key-free, statically servable setups.

## Data

- Always cite sources and respect licenses.
- Do not increase the granularity of anonymized data.
- Document data limitations in both UI and docs.
