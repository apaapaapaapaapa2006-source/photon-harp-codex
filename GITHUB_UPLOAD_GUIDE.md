# GitHub公開・動作確認ガイド

このメモは、今後カメラを使うHTML作品をGitHubへ上げて、Webでプレイできる状態にするための確認手順です。

## 目的

- GitHubにアップしたあと、すぐ遊べるURLを作る
- カメラ、音、外部ライブラリの読み込みで詰まらないようにする
- どこで問題が起きているかを切り分けられるようにする

## 現在の公開先

- リポジトリ: https://github.com/apaapaapaapaapa2006-source/photon-harp-codex
- GitHub Pages: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/
- PHOTON HARP 直接プレイ: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/photon_harp_codex.html
- FINGER MAZE RACE 直接プレイ: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/finger_maze_race.html

## アップ前に必ず見るファイル

- `photon_harp_codex.html`
  - メインの演奏ページ
  - カメラ、MediaPipe Hands、音、エフェクトが入っている
- `finger_maze_race.html`
  - 2人対戦の指迷路ゲーム
  - カメラ、MediaPipe Hands、音、アイテム演出が入っている
- `README.md`
  - GitHub上で見える説明文
- `camera_test.html`
  - カメラだけを確認する診断ページ
  - GitHub側には追加済み。ローカルに無い場合は、必要に応じて再取得または作り直す

## アップロード前チェック

1. HTMLをブラウザで開く
2. `START`を押す
3. カメラ許可が出るか確認する
4. 自分の映像、グレー映像、光の演出が出るか確認する
5. 指を近づけて音が鳴るか確認する
6. 右側の丸ボタンで音のエフェクトが変わるか確認する
7. エラー表示が出たら、表示された英語のエラー名を控える

## GitHub Pagesで重要なこと

カメラは基本的に安全なページでしか動きません。

- OK: `https://...`
- OK: `localhost`
- OKの場合がある: ローカルの `file://...`
- NGになりやすい: `http://...`

GitHub Pagesは `https://` なので、公開後の本番確認に向いています。

## GitHub Pages設定

GitHubのリポジトリ画面で次を確認します。

1. `Settings` を開く
2. `Pages` を開く
3. `Build and deployment` を見る
4. `Source` は `Deploy from a branch`
5. `Branch` は `main`
6. フォルダは `/root`
7. 保存後、反映まで1分から数分待つ

## 公開後の確認順

1. トップページを開く
   - https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/
2. PHOTON HARPを直接開く
   - https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/photon_harp_codex.html
3. FINGER MAZE RACEを直接開く
   - https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/finger_maze_race.html
4. うまく更新されない時はURLの最後に確認用の文字を付ける
   - 例: `?v=20260709-1`
5. カメラが動かない時は診断ページを開く
   - https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/camera_test.html

## カメラが動かない時の切り分け

### 診断ページでカメラが映る

ブラウザと権限は問題ありません。

原因候補:

- メインHTML側の手認識処理で止まっている
- MediaPipe Handsの読み込みに失敗している
- CDNの外部ファイルが読み込めていない
- Safariとの相性問題

対応:

- Chromeで確認する
- メインHTMLのデバッグ表示を見る
- `CAMERA: PLAYING` になっているか見る
- `VIDEO: 1280x720` のように0以外になっているか見る
- `HAND: TRACKING` または `NO HAND` が出るか見る

### 診断ページでもカメラが映らない

作品ではなく、ブラウザまたはOS側の問題です。

対応:

- URLが `https://` か確認する
- ブラウザのカメラ権限を許可する
- macOSの `システム設定 > プライバシーとセキュリティ > カメラ` を確認する
- ChromeまたはSafariを完全終了して開き直す
- 別のカメラアプリがカメラを使っていないか確認する

## 音が鳴らない時

Webブラウザは、ユーザーがボタンを押すまで音を鳴らせないことがあります。

確認:

- 必ず `START` を押してから演奏する
- ミュートになっていないか確認する
- Bluetoothイヤホンなど出力先を確認する
- 右側のエフェクトボタンを押しても、元の音が出ていない場合は音量またはAudioContextの問題を疑う

## 外部ライブラリの注意

`photon_harp_codex.html` と `finger_maze_race.html` はMediaPipeをCDNから読み込みます。

そのため、以下の場合は動かないことがあります。

- インターネット接続がない
- CDNが一時的に落ちている
- ブラウザが外部スクリプトを止めている
- SafariでMediaPipeとの相性が出ている

安定性を上げるなら、次の改善候補があります。

- MediaPipeが失敗した時の簡易カメラ演奏モードを追加する
- 外部ライブラリをローカルに同梱する
- カメラなしでもマウスやタッチで音を鳴らせる予備モードを入れる

## 次に作品を増やす時のファイル名ルール

GitHub Pagesで見やすくするため、英数字とアンダースコア中心にします。

良い例:

- `photon_harp_codex.html`
- `finger_maze_race.html`
- `camera_test.html`
- `new_instrument_01.html`

避けたい例:

- 空白が多い名前
- 日本語だけのHTML名
- 記号が多い名前

## 次回アップ時にCodexへ頼む文章

次のように頼むと、アップロードから確認まで進めやすいです。

```text
このHTML作品をGitHub Pagesで遊べるようにアップしてください。
アップ後に、公開URL、直接URL、カメラ診断URL、確認チェックリストも教えてください。
カメラと音が動くかを想定して、READMEも必要なら更新してください。
```

## 公開前チェックリスト

- [ ] メインHTMLをローカルで開ける
- [ ] `START`ボタンで開始できる
- [ ] カメラ許可が出る
- [ ] 映像が表示される
- [ ] 音が鳴る
- [ ] 右側エフェクトが反応する
- [ ] GitHubに最新HTMLが上がっている
- [ ] GitHub Pagesの設定が `main` / `/root`
- [ ] PagesのURLが開ける
- [ ] `?v=日付番号` を付けてキャッシュを避けて確認した
- [ ] Chromeで確認した
- [ ] 必要ならSafariでも確認した

## 重要メモ

今回の問題では、カメラ診断ページが動いたので、ブラウザのカメラ権限自体は通っている可能性が高いです。
その場合、メイン作品側では「カメラ取得」よりも「手認識ライブラリの起動」や「映像フレームの受け渡し」を疑うのが近道です。
