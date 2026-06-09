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

### 更新チェックリスト

方針を変えるときは、次の順で反映漏れを防ぎます。

1. `preferences/` の該当ファイルを更新する（ここが唯一の正）。
2. 必要なら `templates/CLAUDE.md` / `templates/AGENTS.md` に反映する。
3. 必要なら `skills/*/references/` に反映する。
4. プロンプトは `preferences/` を参照する形のため、原則そのままでよい。
5. 差分を確認してコミットする。

### プロンプトの使い方

- 再利用プロンプトは `prompts/` にあります（索引は `prompts/README.md`）。
- プロンプトの書き方は `prompts/prompt-writing-guide.md` を参照してください。

## Claude Code（ウェブ版）での使い方

Claude Code は起動時に、紐づいたリポジトリ直下の `CLAUDE.md` を自動で読みます。どのリポジトリで作業しているかで入力の仕方が変わります。

### 準備（各アプリリポジトリ側で1回だけ）

`templates/CLAUDE.md` をコピーして、開発対象リポジトリの直下に `CLAUDE.md` として置き、空欄を埋めてコミットしておきます。以降、そのリポジトリのセッションでは共通方針が自動で効きます。

### ケースA：アプリ用リポジトリ（`CLAUDE.md` あり）で作業するとき

今回の依頼だけを短く書きます（方針は書かない）。

```txt
帯広市の農地区画を地図表示する社内向けプロトタイプを作りたい。
入力は data/farmland.geojson。まず技術選定と構成案の確認から。
```

### ケースB：この `llm-workflows` リポジトリで作業するとき

中のファイルを参照させます。

```txt
preferences/ の方針に従って、新しい地図アプリ用リポジトリに置く
CLAUDE.md と README のたたき台を作って。対象は帯広の農地可視化。
```

### ケースC：対象リポジトリに `CLAUDE.md` が無い／別リポジトリの方針を引きたいとき

`llm-workflows` をセッションに追加してから参照します。

```txt
shinyanakashima/llm-workflows をこのセッションに追加して、
そこの preferences/tech-stack.md と deployment-policy.md を前提に、
このリポジトリの地図アプリの技術選定を提案して。
```

| 紐づいているリポジトリ | 入力欄に書くこと |
| --- | --- |
| アプリ用（`CLAUDE.md` あり） | 今回の依頼だけ（3〜5 行）。方針は書かない |
| `llm-workflows` | 「`preferences/` に従って〜」と参照を明示 |
| `CLAUDE.md` 無し | 「`llm-workflows` を追加して `preferences/…` を前提に〜」 |

## 取り扱い上の注意

- 秘密情報、API キー、パスワード、顧客固有の機密情報、個人情報は置きません。
- 個人的な引き継ぎメモや作業中のメタ情報は、このリポジトリではなく非公開メモとして扱います。
- このリポジトリは公開を前提とした原本であり、第三者が読んでも理解できる内容に保ちます。
