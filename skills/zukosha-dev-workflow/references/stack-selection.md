# 技術スタック選定

## Web サイト / Web アプリの構成

- 実装の優先順位は `React + TypeScript` → `SvelteKit` → `Vanilla HTML`。迷ったら上位から検討する。
- ビルド環境は原則 `Vite`。
- フロントエンドのプロトタイプは原則 `Vite + pnpm`。

### 選定の目安

| 優先 | 候補 | 適した要件 |
| --- | --- | --- |
| 第一 | `React + TypeScript + Vite` | コンポーネント化・状態管理・再利用性。判断に迷う場合の既定。 |
| 第二 | `SvelteKit` | ルーティング・SSR・フォーム処理・サーバーサイド処理。軽量・書き味重視。 |
| 第三 | `Vanilla HTML + Vite` | シンプルな静的ページ・小規模な可視化。 |

- SSR・認証・API 統合が中心の場合は `Next.js` も比較する。

## UI / スタイリング

- UI は `shadcn/ui` または `Tailwind CSS` で実装する。
- `React + TypeScript` では `shadcn/ui`（`Tailwind CSS` + `Radix UI` ベース）を優先。
- `SvelteKit` は `shadcn-svelte`、`Vanilla HTML` は `Tailwind CSS` 単体。
- `Tailwind CSS` は v4 系を前提（`@theme`、OKLCH カラー）。
- コンポーネントはコピー＆オウン方式で同梱し、外部 UI ライブラリへの強い依存を避ける。

## 地図ライブラリ

- 原則 `MapLibre` を優先する。
- 単純な 2D 要件のみ `Leaflet` を候補にする。
- ベクトルタイル、PMTiles、MapLibre Style、地理院タイル、複数レイヤ制御、将来的な拡張性が必要なら `MapLibre`。
- 地図の背景はデフォルトで地理院地図（衛星画像＝シームレス空中写真／標準地図）を用い、切り替え可能にする。
- 衛星画像は `seamlessphoto`、標準地図は `std` の地理院タイルを基本とする。
- 広域・国際的な要件では `MapLibre` 標準スタイルなども比較対象にする。

## データ処理

- 用途に応じて `Python`、既存資産に合わせる場合は `Ruby`。

## コンテナ環境

- `Podman` / `Docker Compose` を優先する。

## フレームワーク方針

- 不要に重いフルスタックフレームワークは避ける。
- SSR・認証・API 統合が必要な場合のみ `Next.js` 等を検討する。

## 重視する性質

- API キー不要・自己完結・外部依存最小化。
- CDN 非依存・ライブラリ同梱・静的配信。
- 保守性・再現性・非専門メンバーでも扱えること。
