# DDS iPS-X ブリッジ LP

再生美容株式会社「DDS iPS-X」の遷移元LP（ブリッジLP）です。  
最終遷移先: https://saiseibiyou.com/product/skin-care/ipsx/?id=A002377

---

## ファイル構成

```
ips-x/
├── index.html              # LP 本体（単一ファイル）
├── assets/
│   ├── css/
│   │   └── custom.css      # Tailwind で吸収できないスタイル
│   └── img/
│       ├── README.md       # 必要画像リスト（差し替え手順）
│       ├── placeholder-hero.jpg     ← 要配置
│       ├── placeholder-icon-01.jpg  ← 要配置
│       ├── placeholder-icon-02.jpg  ← 要配置
│       ├── placeholder-icon-03.jpg  ← 要配置
│       ├── placeholder-product.jpg  ← 要配置
│       └── placeholder-cta-bg.jpg   ← 要配置
└── README.md               # このファイル
```

---

## 画像の差し替え手順

1. `assets/img/README.md` の画像一覧を参照し、必要な画像を作成
2. 指定ファイル名で `assets/img/` ディレクトリに保存
3. ブラウザで `index.html` を開いて表示を確認
4. OGP・ファビコン画像も配置後、`index.html` 内のコメントアウトを解除

---

## デプロイ方法

### 静的ホスティング（推奨）

このLPは静的ファイルのみ（HTML + CSS）で構成されています。  
以下のいずれかにアップロードするだけで公開できます。

**FTP/SFTPの場合:**
```
ips-x/ ディレクトリの中身を、サーバーの公開ディレクトリにそのままアップロード
```

**GitHub Pages の場合:**
```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/your-org/ips-x.git
git push -u origin main
# GitHub リポジトリの Settings > Pages で main ブランチを指定
```

**Netlify の場合:**
- Netlify にログイン → "Add new site" → "Deploy manually"
- `ips-x/` フォルダをドラッグ＆ドロップ

---

## フッターリンクのURL確認

フッター内の以下リンクは仮URLです。実際のURLに差し替えてください。

| 項目 | 現在の仮URL | index.html 内の検索文字列 |
|---|---|---|
| 特定商取引法に基づく表記 | `https://saiseibiyou.com/tokusho/` | `tokusho` |
| プライバシーポリシー | `https://saiseibiyou.com/privacy/` | `privacy` |
| お問い合わせ | `https://saiseibiyou.com/contact/` | `contact` |

---

## 構造化データ

`index.html` の `<head>` 内に Product スキーマ（JSON-LD）を埋め込んでいます。  
価格変更・公開期間延長の際は `"priceValidUntil"` の日付を更新してください。

---

## パフォーマンス目標

| 指標 | 目標値 |
|---|---|
| Lighthouse Performance | 90以上 |
| Lighthouse Accessibility | 95以上 |
| ファーストビュー画像 | `loading="eager"` で優先読み込み |
| それ以外の画像 | `loading="lazy"` で遅延読み込み |

> **Note:** Tailwind CDN を使用しているため、本番公開後に Lighthouse スコアが低い場合は  
> Tailwind CLI でビルドした単一CSSファイルへの移行を検討してください。

---

## 禁止事項（デザイン維持のため）

- 色・フォント・余白感の変更
- GSAP、AOS 等の外部アニメーションライブラリの追加
- セクション順序の変更
