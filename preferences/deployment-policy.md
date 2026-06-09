# デプロイ方針

## デプロイ先の選定基準

- 静的な公開フロントエンド: `GitHub Pages`
- private repository 由来の静的サイト: `ConoHa WING` を利用可
- 動的 Web アプリケーション: `Cloudflare`
- 常駐プロセス・worker・scheduler・WebSocket・コンテナ常駐が必要な場合: `Railway`
- 上記で対応できない場合のみ: `AWS`

## 判断の優先順位

- 一般論としての最適解より、契約状況・運用方針・好みを優先する。
- 例外を提案する場合は、その理由を明記する。
