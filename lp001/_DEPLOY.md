# TERAPP Lift Up Patch LP（lp001）— 本番アップ手順【自己完結版】

想定公開URL（canonical/OGPで指定済み）: **https://terapp.jp/lp001/**

## 1. アップロード方法（このフォルダだけでOK）
このバンドルは **自己完結型** です。法定ページ・favicon・manifest 等をすべて `lp001/` 内に同梱し、参照を同フォルダ相対にしています。

**`lp001/` フォルダの中身を、そのまま `terapp.jp/lp001/` にアップロードするだけ**で完結して動作します。
- `index.html` → `/lp001/index.html`
- `images/` → `/lp001/images/`（画像34点）
- `videos/` → `/lp001/videos/`（ブランドフィルム）
- 法定ページ・共通ファイルも同梱済み（下記）
- `_DEPLOY.md` はアップロード不要です。

## 2. 同梱している共通ファイル（すべて `/lp001/` 配下で完結）
- `tokushoho.html`（特定商取引法に基づく表記）／`privacy.html`／`terms.html`／`contact.html`／`404.html`
- `favicon.svg`／`apple-touch-icon.png`（180×180）／`site.webmanifest`（start_url=`/lp001/`）
- `sitemap.xml`／`robots.txt`／`llms.txt`（URLはすべて `/lp001/` 配下で設定済み）

法定ページのヘッダー/フッターは同フォルダ相対でリンクしているため、`/lp001/` 単体で正しく回遊できます。

## 3. ⚠ SEO/LLMO の注意（ドメイン直下が必要なファイル）
`robots.txt` と `llms.txt` は仕様上 **ドメイン直下** でないと検索エンジン/AIクローラに読まれません。
サブディレクトリの `/lp001/robots.txt`・`/lp001/llms.txt` は**参照されません**（クローラは常に `https://terapp.jp/robots.txt`・`https://terapp.jp/llms.txt` を見ます）。

- **ドメイン全体を管理できる場合**：同梱の `robots.txt`・`llms.txt`（＋できれば `sitemap.xml`）を **`terapp.jp/` 直下にも配置**すると効果が最大化します。
- **`/lp001/` だけの運用でも**：ページ表示・法定ページ・**JSON-LD構造化データ・OGP・canonical・sitemap（手動送信）** は完全に機能します。robots/llms が効かないぶん、AI/検索クローラ制御の一部が及ばないだけです。

## 4. 収録アセット
- `index.html` … 単一ファイル完結（インラインCSS/バニラJS／背景装飾#bg-decor／使用シーン画像マーキー／FV直下ブランドフィルム）
- 画像は全て `<picture>` でWebP優先＋JPEGフォールバック（KV/各セクション/ツボ/使用シーン7枚/装飾/OGP/ポスター）
- `videos/terapp-brand-film.mp4`（1920×1080 / 40秒 / 14MB）
- 合計 約18MB（うち動画14MB）

## 5. 確定済み / 未確定（TODO）
**確定・反映済**: 価格 1セット2,200円／3セット5,500円（税込）・内容量 パッチ24枚入り・送料 全国一律250円・支払（銀行振込/代引/クレカ/キャリア）・引渡（決済確認後発送）・返品（未開封30日以内）。

**未確定（TODO）**:
- 購入/カートURL：現状「購入について問い合わせる」→お問い合わせへ誘導。確定後、価格カードの `data-checkout` にURLを設定すれば文言・遷移が自動切替。
- 「使い方」画像内の小注記「使用上の注意（仮・…）」：確定時に `images/terapp-howto.*` を差し替え。
- GA/GTM 測定ID：`dataLayer` があればイベント push する実装済み。IDは未挿入。
- 独自ドメイン：canonical/OGP/sitemap は `terapp.jp/lp001/` で確定済み。DNSを公開先へ向ければ有効化。
- 公開後：Google Search Console 登録＋sitemap送信、リッチリザルトテスト、PageSpeed/Core Web Vitals 実測（14MB自動再生動画のLCP影響）。

## 6. SEO/LLMO 実装状況（オンページ完了）
title / description / **canonical `/lp001/`** / robots(index,follow) / **専用OGP画像 terapp-ogp.jpg（1200×630）**・Twitterカード / **JSON-LD @graph（Organization・WebSite・Product・HowTo・BreadcrumbList・FAQPage14）** / favicon・apple-touch-icon・manifest / 画像内テキストの sr-only 化（クロール対応）。

## 7. コンプライアンス
本商品は **雑貨** です。医薬品・医薬部外品・化粧品・医療機器ではありません。効能効果・即効性・疾患名による訴求は掲載しない方針で、印象・習慣表現に統一しています。
※ ヒーロー2文「あなた史上、最高のフェイスラインへ／貼るだけ"瞬感"リフトケア」と、位置ガイド画像の「引き上げる/リフトケア」表現は、薬機法リスクを説明のうえユーザーの明示採用で掲載。文言変更時もこの経緯にご留意ください。お客様の声は許諾済み適合レビューが用意できるまで空状態です。
