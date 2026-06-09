# skills

ChatGPT Skills としてパッケージ化する原本。

## 構成

- `zukosha-dev-workflow/` — 開発・技術選定・デプロイ判断用。
- `zukosha-innovation-workflow/` — 新規事業・地域課題解決・外部共創・企画検討用。

各 Skill は `SKILL.md`（使う場面・参照 references・判断方針・避ける提案・成果物観点）と `references/`（詳細）で構成する。

## skill.zip 化の手順

現時点では人間が読んで理解できる構成にとどめている。ChatGPT で使うときは、対象フォルダを zip に固めてアップロードする。

```sh
# 例: zukosha-dev-workflow を zip 化
cd skills
zip -r zukosha-dev-workflow.zip zukosha-dev-workflow
```

- zip のルート直下に `SKILL.md` が来るようにする。
- `references/` を同梱する。
- 秘密情報・個人情報を含めない（公開原本と同じ方針）。

## メンテナンス方針

- 方針の正は `preferences/`。Skill の内容は `preferences/` と整合させる。
- `preferences/` を更新したら、関連する `skills/.../references/` にも反映する。
