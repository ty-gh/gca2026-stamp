# gca2026-stamp — スタンプ集め（スマホ用ページ）

出張 高専ラボ with ICTパーク（GCA2026 秋・11/7・8 泉佐野オチアリーナ）のワークショップ「スイッチだけで足し算を作る」で使う、スタンプ集めのページ。

- 公開 URL: https://ty-gh.github.io/gca2026-stamp/
- `index.html` に `manifest.webmanifest` と `icon.svg` を添えた 3 ファイル。ビルド不要、サーバー不要。フォントだけ Google Fonts を読む（届かなければ端末のフォントで動く）
- 合言葉（NOT / OR / AND / XOR / 半加算器）を入れるとスタンプが押され、5 つそろうと賞状の画像を保存できる
- 名前は任意（ニックネーム）。端末の中にだけ残り、どこにも送らない
- 賞状の下に満足度アンケート（7 問・全部タップで 1 分・満足度だけ必須）。送信先は Google フォーム（下の「アンケートの送信先」）。名前は送らない

**正本は `ty-gh/ws-remote` の `gca2026-stamp/stamp-app/`。** 直すときはそちらを直して、3 ファイルをここへコピーして push する（数分で反映）。
仕様・変え方・できないことは、そちらの README にある。

## 公開のしかた

GitHub Pages。Settings → Pages → Build and deployment → Source を **Deploy from a branch**、Branch を **main / (root)** にする。

## アンケートの送信先

答えは Google フォームに送る。**`index.html` の `SURVEY` が空のままだと、答えは端末の中に残るだけで、どこにも届かない。** イベント前に次をやる（10 分）。

1. Google フォームを新しく作り、設問を次の順で 8 つ作る（種類はすべて「記述式」でよい。選択式にするなら選択肢の文字をページと同じにする）。
   回答の収集でメールアドレスを集めない設定にする（匿名で送るため）。

   | key | 設問 | ページの選択肢 |
   |---|---|---|
   | `sat` | 全体の満足度 | 1〜5 |
   | `grade` | お子さんの学年 | 未就学 / 小1・2 / 小3・4 / 小5・6 / 中学生以上 |
   | `level` | 内容のむずかしさ | かんたんすぎた / ちょうどよかった / むずかしかった |
   | `fav` | いちばんおもしろかったステージ | 1 NOT あべこべの回路 / 2 OR ことわれない回路 / 3 AND がんこな回路 / 4 XOR ちがいがわかる回路 / 5 半加算器 1+1=10！？ |
   | `interest` | 半導体やコンピューターのしくみへの興味 | とても増えた / 少し増えた / 変わらない |
   | `again` | また参加したいか | ぜひ参加したい / 内容によっては / あまり |
   | `comment` | 感想・ご意見 | 自由記述（300 字まで） |
   | `date` | 回答日 | `2026-11-07` のような文字（ページが自動で入れる） |

2. フォームの右上「⋮」→「事前入力した URL を取得」で、各設問に適当な文字を入れて「リンクを取得」。URL の中の `entry.123456789=...` が設問ごとの番号。
3. `index.html` の `var SURVEY = { ... }` に書き込む。`action` はフォームの URL の末尾 `/viewform` を `/formResponse` に変えたもの。

   ```js
   var SURVEY = {
     action: 'https://docs.google.com/forms/d/e/XXXXXXXX/formResponse',
     entry: { sat: 'entry.111', grade: 'entry.222', level: 'entry.333', fav: 'entry.444',
              interest: 'entry.555', again: 'entry.666', comment: 'entry.777', date: 'entry.888' }
   };
   ```

4. push して数分待ち、公開 URL で 5 つそろえて送信し、フォームの「回答」に 1 件入るのを確かめる。

送れなかったとき（電波が弱いなど）は端末に残り、次にページを開いたときに送り直す。同じ端末からは 1 回だけ（「はじめから」で消すと、また答えられる）。
設問を変えるときは `index.html` の `<section id="survey">` の文字を直す。設問を増やすときは `SURVEY.entry` と `SURVEY_KEYS` にも key を足す。
