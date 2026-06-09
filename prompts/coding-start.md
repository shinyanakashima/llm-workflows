# 開発開始プロンプト

新しい開発作業を始めるときに使うプロンプト。

---

これから新しい開発作業を始めます。以下の前提で進めてください。

## 前提条件

- 共通方針は `preferences/`、技術選定は `preferences/tech-stack.md`、デプロイは `preferences/deployment-policy.md`、Git 運用は `preferences/git-policy.md` に従う。
- このプロジェクトの固有情報は `CLAUDE.md` / `AGENTS.md` を参照する。

## 着手前に確認すること

1. 何を作るか（目的・対象読者・公開範囲）。
2. Web の場合の構成（`Vanilla HTML` / `React + TypeScript` / `Svelte` / `SvelteKit` のどれが適切か）。
3. ビルドは `Vite`、プロトタイプは `Vite + pnpm` を前提とする。
4. 地図が必要なら原則 `MapLibre`（単純な 2D 要件のみ `Leaflet`）。
5. デプロイ先（GitHub Pages / ConoHa WING / Cloudflare / Railway / AWS）。
6. データを扱う場合は、出典・ライセンス・限界。

## 進め方

- 作業は `main` ブランチで行う。`main` への直接 push が制限される場合は制約を明示する。
- 変更前に差分を確認する。
- コミットメッセージは日本語で、淡々と変更内容のみを書く。
- 秘密情報・API キー・個人情報をコミットしない。
- AI 署名や宣伝文句、依頼者への助言や質問をコミット・Issue・PR に含めない。

まず、上記 1〜6 のうち不明な点を確認してから着手してください。
