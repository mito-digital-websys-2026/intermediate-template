# devcontainerの起動方法（中級）

このリポジトリは3つのコンテナ（frontend / backend / db）で構成されています。
**VS Codeのウィンドウを2つ開いて**、それぞれ別のコンテナに接続する運用です。

## 起動手順

1. リポジトリをクローンし、VS Codeで開く
2. コマンドパレット（`Ctrl+Shift+P` / `Cmd+Shift+P`）→ **「Dev Containers: Reopen in Container」**
   - 複数の構成が表示されるので、まず **「intermediate (backend)」** を選ぶ
   - これで frontend・backend・db の3コンテナが起動する（backendのコンテナにこのウィンドウが接続される）
3. **もう一つ別のVS Codeウィンドウを開く**（同じフォルダを開く）
4. そちらでもコマンドパレット→「Dev Containers: Reopen in Container」→ 今度は **「intermediate (frontend)」** を選ぶ
   - 手順2で起動済みの同じコンテナ群に、今度はfrontendコンテナとして接続される

以降は次のように使い分ける。

| ウィンドウ | 用途 |
|---|---|
| backend | `python manage.py migrate` 等のDjangoコマンド、`http://localhost:8000` の確認 |
| frontend | `npm run dev` の実行、`http://localhost:3000` の確認 |

## 初回のみ

- backend側のウィンドウで、初回接続時に自動的に `pip install` が走る
- frontend側のウィンドウで、初回接続時に自動的に `npm install` が走る
- どちらも数分かかることがある。エラーが出た場合は、コマンドパレットから「Dev Containers: Rebuild Container」を試す

## 終了するとき

どちらのウィンドウも閉じるだけではコンテナは停止しない（意図的な設定）。作業を完全に終える場合は、WSLのターミナルから次を実行する。

```bash
docker compose -f .devcontainer/docker-compose.yml down
```

## うまく起動しない場合

- ローカル（WSL2＋Docker）で解決しない場合は、GitHub Codespaces に退避する（第1週の指導コマ2で案内）
- MySQLコンテナの起動に時間がかかることがある。`db`コンテナの起動を待ってから`backend`の接続を待つ設計にしてあるため、初回は数十秒待つ
- 「Reopen in Container」で新規作成の画面（構成ファイルが見つからない）が出る場合は、**VS Codeで開いているフォルダがこのリポジトリ自体になっているか**を確認する。1つ上の親フォルダを開いていると`.devcontainer`が認識されない
- `db`コンテナの起動時に `ports are not available: exposing port TCP 0.0.0.0:3306` のようなエラーが出る場合、PC上で別のMySQL（XAMPP等）がすでに3306番ポートを使用している。そちらを停止するか、`.devcontainer/docker-compose.yml` の `db` サービスの `ports` を別の空きポートに変更する
