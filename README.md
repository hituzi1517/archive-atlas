# Archive Atlas PWA — GitHub Pages用

このフォルダの中身をそのままGitHubリポジトリのルートへ置けば使えます。ビルド作業は不要です。

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
