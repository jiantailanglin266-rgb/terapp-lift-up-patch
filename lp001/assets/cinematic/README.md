# TERAPP LP001 — Cinematic Video Assets（差し替え用）

このフォルダに下記ファイル名で動画を置くと、該当セクションが自動でシネマティック動画に切り替わります。
**動画が無い間は poster 画像（下記）が表示され、レイアウトは一切崩れません。**

## 仕様（共通）
- 形式: MP4（H.264 / AAC）を必須。可能なら WebM(VP9/AV1) も併置し `<source>` 先頭に追加すると軽量。
- Desktop: 1920×1080 以上（推奨 3840×2160）／ Mobile 縦持ち向けに 1080×1920 も用意可
- 長さ: 6〜12秒 / 24fps / **muted・seamless loop** / controls非表示（背景用）
- ルック: 4K commercial beauty film・35〜85mm・浅い被写界深度・warm ivory lighting・soft champagne highlights・スローモーション
- 効果効能を想起させる医療的表現・矢印・赤み表現は入れない（雑貨・美容ブランド表現に限定）

## 必要な6本

| filename | セクション | 尺 | 比率 | Desktop/Mobile | 内容コンセプト（プロンプト用） |
|---|---|---|---|---|---|
| `01-hero.mp4` | Hero（FV背景） | 8-10s | 16:9 / 9:16 | 両方 | 暗い空間、暖色の柔らかな光。女性の首筋・肩・肌の極端なクローズアップ。手がTERAPPをゆっくり扱い、肌へ静かに貼る。髪がわずかに揺れ、光が肌の輪郭を横切る。浅い被写界深度。 |
| `02-product.mp4` | Product Reveal | 6-8s | 4:5 | Desktop | TERAPP商品/パッケージの85-100mmマクロ。素材表面の超接写、シャンパンの反射、微細な埃、石/ガラス/アイボリー面の上。高級香水・ジュエリーのように。 |
| `03-ritual.mp4` | How to Use | 6-8s | 16:9 | 両方 | 清潔な肌に指で剥離紙を剥がし、気になる部分へゆっくり貼る一連。超接写・スロー。 |
| `04-areas.mp4` | Application（任意） | 6-8s | 4:5 | 両方 | フェイスライン・頬・首元へパッチが触れる肌のクローズアップ。※身体（背中/脚等）は使わない=フェイス周りのみ。 |
| `05-lifestyle.mp4` | Lifestyle（任意） | 8-12s | 16:9 | 両方 | 朝の自宅、メイク前、在宅ワーク、リラックス、外出前、特別な日——断片的な日常のつなぎ。 |
| `06-final.mp4` | Final CTA（背景） | 8-10s | 16:9 / 9:16 | 両方 | 夜、静かな部屋、窓、柔らかな照明、人物の背中。落ち着いたトーン。 |

## 現状の poster フォールバック（動画未配置時に表示）
- Hero: `images/terapp-brand-film-poster.jpg`
- Final: `images/terapp-scene-6.jpg`
- Brand Film（09）は既存の `videos/terapp-brand-film.mp4` を使用（配置済み・稼働中）

## 差し替え手順（Hero / Final の背景動画）
1. 上表のファイル名で mp4 をこのフォルダに保存（例: `assets/cinematic/01-hero.mp4`）してFTPでアップ
2. `index.html` 内の次の1行に、配置したパスを追記して有効化（既定は空＝リクエストを出さずコンソールもクリーン）:
   ```js
   var CINEMATIC_READY = ['assets/cinematic/01-hero.mp4','assets/cinematic/06-final.mp4'];
   ```
3. 再読み込みで背景動画が有効化（未配置のうちは濃色グラデ背景のまま崩れない）

※ 09 ブランドフィルム（`videos/terapp-brand-film.mp4`）は配置済みで、このマニフェストとは無関係に常時稼働します。
※ 02-product / 03-ritual / 04-areas / 05-lifestyle は現状ライブ・タイポ＋静止画で成立しています。将来これらの枠に動画を追加する場合は該当セクションに `<video>` を追加してください（設計コメント参照）。
