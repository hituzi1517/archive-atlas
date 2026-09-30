# Archive Atlas PWA — GitHub Pages用

このフォルダの中身をそのままGitHubリポジトリのルートへ置けば使えます。ビルド作業は不要です。

## 今回の更新：ランキングの期間指定・累計再生数順

「ランキング」タブで、**再生数（現在の累計）**が選択できます。「ランキング対象期間」は全期間／直近30日／90日／1年／2年／5年／年別／開始日〜終了日から選択可能です。期間の判定には、配信アーカイブは実際のライブ開始日、通常動画は公開日を使い、画面のタイムゾーン設定に従います。歌投稿・外れ値フィルターは従来どおりランキングに反映されます。**過去の期間内に発生した再生数を取得する機能ではありません**。期間内に公開・配信された動画について、API取得時点の累計再生数で順位をつけます。

以前のPWAから更新するときは**index.html と sw.js の2ファイルをGitHubで置き換え**てください。アイコン・manifest・.nojekyllは同じものをそのまま使えます。更新後はGitHub Pagesのデプロイが完了してから、iPhone/iPadのホーム画面アプリをいったん閉じて開き直してください。古い画面が残る場合はSafariで公開URLを一度開いて再読み込みしてください。

## 公開手順

1. GitHubで新しいリポジトリを作る（例: `archive-atlas`）。
2. このフォルダ内の `index.html`、`manifest.webmanifest`、`sw.js`、`icons/`、`.nojekyll` をリポジトリ直下へアップロードしてコミットする。
3. リポジトリの **Settings → Pages** を開く。
4. **Build and deployment → Source** を **Deploy from a branch** にし、Branch を **main / (root)** にして保存する。
5. 表示された `https://USERNAME.github.io/REPOSITORY/` を開く。GitHub PagesはHTTPSなのでPWAのService Workerが有効になります。

## iPhone / iPad

公開URLをSafariなどで開き、共有メニュー → **ホーム画面に追加**。ホーム画面から起動すると独立したアプリ画面になります。

## YouTube APIキー

APIキーはリポジトリには書き込まれていません。アプリ画面で入力します。「この端末にAPIキーを保存する」をONにした場合だけ、そのブラウザ/PWAのLocal Storageに保存されます。

公開用にはGoogle Cloud ConsoleでAPIキーを **YouTube Data API v3だけにAPI制限**し、Webサイト制限を使う場合はGitHub PagesのURL（例 `https://USERNAME.github.io/REPOSITORY/*`）を許可してください。

## オフライン動作

PWA本体の画面・アイコンはキャッシュされるため、通信がなくてもアプリの画面自体は起動できます。ただしYouTube Data APIからチャンネル情報を取得・更新するにはインターネット接続が必要です。APIレスポンスやYouTubeサムネイルはService Workerで保存しません。
