# AI_CONTEXT

生成AIに質問する際は、**このファイルの内容をプロンプトの冒頭に貼り付けてから**質問すること。
バージョンや使えるライブラリを伝えずに質問すると、AIは別バージョン向けの記法や、このリポジトリに入っていないライブラリを前提にしたコードを返してくることがある。

---

## 技術スタック（プロンプト冒頭に貼り付けること）

- フロント：Next.js 15.5（App Router）/ React 19 / TypeScript 5.9 / Material UI v9
- バック：Django 5.2 LTS / Django REST Framework 3.16 / Python 3.13
- DB：MySQL 8.4 LTS
- 実行環境：Docker / Dev Containers（フォールバック：GitHub Codespaces）
- 使えるPythonパッケージ：Django / djangorestframework / mysqlclient / django-cors-headers / djangorestframework-simplejwt 5.5（JWTを選んだ場合のみ）
- 使えるnpmパッケージ：next / react / react-dom / @mui/material / @mui/icons-material / @emotion/react / @emotion/styled

回答時は上記バージョンに準拠してください。
Pages Router の記法、Django 4系以前の記法、MUI v5 以前の記法は使わないでください。
上記にないライブラリ（dj-rest-auth、django-allauth、django-filter など）は使わず、Django・DRF の標準機能で書いてください。
CSRF の保護を無効にする方法（@csrf_exempt など）と、CORS_ALLOW_ALL_ORIGINS = True は使わないでください。
該当バージョンで非推奨・削除された記法を使う場合は、その旨を明示してください。

---

## 使い方の例

質問するときは、次の3点をセットで渡す。

1. 上記の技術スタック（このファイルの中身をそのままコピー）
2. 今書いている・関係している既存コード（models.py、views.py、serializers.py、該当する画面のコードなど）
3. 出ているエラーメッセージの全文（一部だけを抜粋しない）

断片だけを渡すと、的外れな回答が返ってくることが多い。
自分のテーマの要件定義（該当する機能番号の部分）も一緒に渡すと、要件に合わない提案が減る。

## 注意事項

- `package.json` / `requirements.txt` の依存バージョンは固定してある。AIに勧められても `npm update` 等で勝手に更新しないこと（TypeScript 7.0 以上は Next.js 15.5 が拒否する）
- AIの出力は必ず自分で動作確認・検証してから採用すること
- 説明できないコードは提出しないこと（提出前に自分の言葉で説明できるか確認する）
- 投稿者・予約者などの「誰が作ったか」を、リクエストの値で受け取るコードは採用しないこと（ログインユーザーをサーバー側で入れる）
- Copilot 等のインライン補完で、数行以上がまとめて提示されそのまま採用した場合は、詰まりログの記録対象になる（詳細は `tsumari-log/README.md` を参照）
