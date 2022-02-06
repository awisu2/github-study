# workflow

pushやforkがされたときに自動で実行するワークの設定について

- [GitHub Actionsのドキュメント \- GitHub Docs](https://docs.github.com/ja/actions)
- [Quickstart for GitHub Actions \- GitHub Docs](https://docs.github.com/ja/actions/quickstart#more-starter-workflows)

**NOTE**

- .github/workflows ディレクトリ内に yml 形式のファイルを設置することで動作する
- エラー対応:
  - workflow のpushには、専用の権限が必要なため、pushでエラーが出る場合はaccess tokenの更新を
    - エラー内容: *refusing to allow a Personal Access Token to create or update workflow `.github/workflows/github-actions-demo.yml` without `workflow` scope*

