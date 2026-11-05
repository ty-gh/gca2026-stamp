# gca2026-stamp — スタンプ集め（スマホ用ページ）

出張 高専ラボ with ICTパーク（GCA2026 秋・11/7・8 泉佐野オチアリーナ）のワークショップ「スイッチだけで足し算を作る」で使う、スタンプ集めのページ。

- 公開 URL: https://ty-gh.github.io/gca2026-stamp/
- `index.html` に `manifest.webmanifest` と `icon.svg` を添えた 3 ファイル。ビルド不要、サーバー不要。フォントだけ Google Fonts を読む（届かなければ端末のフォントで動く）
- 合言葉（NOT / OR / AND / XOR / 半加算器）を入れるとスタンプが押され、5 つそろうと賞状の画像を保存できる
- 名前は任意（ニックネーム）。端末の中にだけ残り、どこにも送らない

**正本は `ty-gh/ws-remote` の `gca2026-stamp/stamp-app/`。** 直すときはそちらを直して、3 ファイルをここへコピーして push する（数分で反映）。
仕様・変え方・できないことは、そちらの README にある。

## 公開のしかた

GitHub Pages。Settings → Pages → Build and deployment → Source を **Deploy from a branch**、Branch を **main / (root)** にする。
