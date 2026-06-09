# llm-workflows

LLM / AI エージェントに毎回伝えている共通方針・技術選定・デプロイ方針・Git 運用ルール・再利用プロンプト・Skills 原本を一元管理するためのリポジトリです。

各アプリ開発プロジェクトで、毎回長い前提条件をプロンプトへ貼り付けなくても済むように、再利用可能な AI ワークフローの「原本」を Git 管理することを目的としています。

## このリポジトリの位置づけ

- LLM / AI エージェントに渡す **共通前提の原本** です。
- 各プロジェクト固有の実装ルールは、ここではなく **個別リポジトリ側**（`CLAUDE.md` / `AGENTS.md` など）で管理します。
- 共通方針を更新したら、各プロジェクトへ反映する起点として使います。

## ディレクトリ構成

```txt
llm-workflows/
├── README.md
├── preferences/        共通方針（再利用する前提条件の原本）
│   ├── profile.md
│   ├── business-context.md
│   ├── tech-stack.md
│   ├── deployment-policy.md
│   ├── git-policy.md
│   ├── data-policy.md
│   └── product-policy.md
├── templates/          各プロジェクトへコピーする雛形
│   ├── CLAUDE.md
│   ├── AGENTS.md
│   └── README-template.md
├── prompts/            再利用プロンプト
│   ├── coding-start.md
│   ├── proposal-review.md
│   ├── research-summary.md
│   └── project-handoff.md
└── skills/             ChatGPT Skills としてパッケージ化する原本
    ├── zukosha-dev-workflow/
    │   ├── SKILL.md
    │   └── references/
    └── zukosha-innovation-workflow/
        ├── SKILL.md
        └── references/
```

## 各ディレクトリの役割

### `preferences/`

共通方針の原本です。技術選定・デプロイ・Git 運用・データの扱い・プロダクト面の好みなど、プロジェクトをまたいで共通して伝えたい前提条件をまとめます。

### `templates/`

各アプリリポジトリへコピーして使う雛形です。`CLAUDE.md` / `AGENTS.md` をプロジェクト直下に置き、リポジトリ固有情報を書き換えて使います。

### `prompts/`

繰り返し使うプロンプトの原本です。開発開始時、企画レビュー、調査要約、プロジェクト引き継ぎなどの場面で利用します。

### `skills/`

ChatGPT Skills としてパッケージ化する原本です。複数プロジェクト横断の判断基準や業務文脈を記載します。現時点では完全なパッケージ化までは行わず、人間が読んで理解でき、後で `skill.zip` 化できる構成にしています。

## 運用方法

- 各アプリリポジトリには `CLAUDE.md` や `AGENTS.md` を置き、プロジェクト固有情報を書きます。
- Skills には、複数プロジェクト横断の判断基準や業務文脈を書きます。
- 共通方針を変更したいときは、まず `preferences/` を更新し、必要に応じて `templates/` と `skills/` に反映します。

## 取り扱い上の注意

- 秘密情報、API キー、パスワード、顧客固有の機密情報、個人情報は置きません。
- 個人的な引き継ぎメモや作業中のメタ情報は、このリポジトリではなく非公開メモとして扱います。
- このリポジトリは公開を前提とした原本であり、第三者が読んでも理解できる内容に保ちます。
