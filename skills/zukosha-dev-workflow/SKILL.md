# zukosha-dev-workflow

開発・技術選定・デプロイ判断を支援する Skill 原本。後で ChatGPT Skills として `skill.zip` 化できる構成にしている。

## どのような場面で使う Skill か

- Web サイト / Web アプリ / 地図アプリの開発を始めるとき。
- 技術スタックやデプロイ先を選定するとき。
- Git 運用やコミット方針を確認するとき。
- README やドキュメントの品質、データの出典・ライセンス・限界の明記を確認するとき。

## 参照すべき references

- `references/stack-selection.md` — 技術スタック選定（Vanilla HTML / React + TypeScript / Svelte / SvelteKit、Vite、MapLibre）。
- `references/deployment-policy.md` — デプロイ先判断（GitHub Pages / ConoHa WING / Cloudflare / Railway / AWS）。
- `references/git-policy.md` — Git / コミット運用。
- `references/data-policy.md` — データの出典・ライセンス・限界の扱い。
- `references/review-checklist.md` — README・ドキュメント品質のレビュー観点。

## 回答時の判断方針

- Web を作るなら、まず構成（Vanilla HTML / React + TypeScript / Svelte / SvelteKit）を確認する。
- ビルドは `Vite` を前提とし、プロトタイプは `Vite + pnpm`。
- 地図は原則 `MapLibre`。単純な 2D 要件のみ `Leaflet`。
- デプロイ先は契約状況・運用方針・好みを優先して選ぶ。
- データを扱う場合は、出典・ライセンス・限界を必ず明記する。
- 作業は `main` ブランチを前提とし、制約があれば明示する。

## 避けるべき提案

- 不要に重いフルスタックフレームワークの導入。
- API キー必須・外部依存の大きい構成（自己完結を好む方針に反する）。
- 一般論の最適解だけを根拠にしたデプロイ先の押し付け。
- 出典やライセンスを省いたデータ利用。
- 秘匿化データの粒度を上げる処理。

## 成果物に含めるべき観点

- 第三者可読性・日英バイリンガル対応。
- README 冒頭の公開 URL・目的・対象読者。
- 地図アプリの見方・UI 操作の平易な説明。
- データの限界と数字を読むときの注意。
- 再現手順・前処理方針・デプロイ方法。
