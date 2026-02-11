# 出産内祝いギフト推薦（MVP）

忙しい新米パパ・ママが、出産内祝いの「候補探し」と「比較」を最短で終わらせるサービス。

## 特徴

- 入力30秒 → おすすめ8件（理由つき）→ 楽天で購入へ
- LLMによる属性ベース推薦（予算/相手/好み/NG条件）
- 楽天商品検索APIで実在する商品のみ提示

## セットアップ

### 1. 環境変数の設定

```bash
cd frontend
cp .env.example .env.local
```

`.env.local`に以下のAPIキーを設定：
- `RAKUTEN_APP_ID`: 楽天Developers登録後に取得
- `RAKUTEN_AFFILIATE_ID`: 楽天アフィリエイト登録後に取得
- `ANTHROPIC_API_KEY`: Anthropic Consoleで取得

### 2. 依存関係のインストール

```bash
cd frontend
npm install
```

### 3. 開発サーバー起動

```bash
npm run dev
```

ブラウザで http://localhost:3000 を開く

## 技術スタック

- **フロントエンド**: Next.js 16 (App Router), TypeScript, TailwindCSS
- **LLM**: Claude API (Anthropic)
- **外部API**: 楽天商品検索API, 楽天アフィリエイトAPI
- **ホスティング**: Vercel（予定）

## MVP開発フェーズ

- [x] **Phase 1**: 基盤構築（Next.js + 環境変数 + レイアウト）
- [x] **Phase 2**: 楽天API連携 + データ取得
- [x] **Phase 3**: タグ設計 + LLMタグ付けパイプライン
- [x] **Phase 4**: 入力フォーム + 推薦ロジック実装
- [ ] **Phase 5**: アナリティクス計測
- [ ] **Phase 6**: デプロイ準備

## プロジェクト構造

```
gift-birthday/
├── CLAUDE.MD         # プロジェクト仕様
├── README.md         # このファイル
├── frontend/         # Next.jsアプリ
│   ├── app/          # App Router
│   │   ├── api/
│   │   │   ├── recommend/        # 推薦API
│   │   │   ├── generate-catalog/ # カタログ生成API
│   │   │   └── test-rakuten/     # テストAPI
│   │   └── page.tsx              # メインページ
│   ├── components/   # Reactコンポーネント
│   │   ├── Header.tsx
│   │   ├── Footer.tsx
│   │   ├── RecommendationForm.tsx
│   │   └── RecommendationResults.tsx
│   ├── lib/          # ライブラリ
│   │   ├── rakuten/         # 楽天API連携
│   │   ├── tags/            # タグ付けシステム
│   │   └── recommendation/  # 推薦ロジック
│   └── public/       # 静的ファイル
├── backend/          # バックエンド（今後実装）
└── docs/             # ドキュメント
    ├── rakuten-api-setup.md
    ├── tagging-system.md
    └── recommendation-system.md
```

## 開発用ページ

- **メインページ**: http://localhost:3000
- **楽天APIテスト**: http://localhost:3000/test-rakuten
- **カタログ生成**: http://localhost:3000/generate-catalog

## ライセンス

Private（商用利用時は適切なライセンスを設定）
