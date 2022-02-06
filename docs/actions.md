# actions

pushやforkがされたときに自動で実行するワークの設定について

- [GitHub Actionsのドキュメント \- GitHub Docs](https://docs.github.com/ja/actions)
- [Quickstart for GitHub Actions \- GitHub Docs](https://docs.github.com/ja/actions/quickstart#more-starter-workflows)

**NOTE**

- .github/workflows ディレクトリ内に yml 形式のファイルを設置することで動作する
- エラー対応:
  - workflow のpushには、専用の権限が必要なため、pushでエラーが出る場合はaccess tokenの更新を
    - エラー内容: *refusing to allow a Personal Access Token to create or update workflow `.github/workflows/github-actions-demo.yml` without `workflow` scope*

## sample

- [Quickstart for GitHub Actions \- GitHub Docs](https://docs.github.com/ja/actions/quickstart)
- [GitHub Actionsのワークフロー構文 \- GitHub Docs](https://docs.github.com/ja/actions/using-workflows/workflow-syntax-for-github-actions)

```yml
name: GitHub Actions Demo
on: [push]
jobs:
  Explore-GitHub-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v2
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }} update"
```

- name: action名 (リポジトリのActionsメニューで表示される)
- on: 実行する条件. push, fork, label, issue, page_build...etc が指定できる
  - それぞれ更に細かい指定が可能(例: push => mainブランチへのpush時に)
  - [ワークフローをトリガーするイベント \- GitHub Docs](https://docs.github.com/ja/actions/using-workflows/events-that-trigger-workflows)
  - サンプルで不明だったもの
    - page_build:　[GitHub Pages](https://pages.github.com/) にpushされたときに動作
- [jobs](https://docs.github.com/ja/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_id): onが一致したときに実行する処理内容。複数指定できる
  - job_id: jobs直下の項目, 個々のjobのid
    - name: [option] job名 githubで表示される設定されていないときは job_id が表示される（っぽい）
    - runs-on: 実行するosを指定。containerが指定されている場合はそちらが優先される
      - 指定可能リスト: windows-2022, windows-latest, windows-2019, windows-2016, ubuntu-latest, ubuntu-20.04, ubuntu-18.04, macos-11, macos-latest, macos-10.15
      - [About GitHub\-hosted runners \- GitHub Docs](https://docs.github.com/ja/actions/using-github-hosted-runners/about-github-hosted-runners)
    - steps: 処理される内容
      - if
      - name
      - uses: 「ジョブでステップの一部として実行されるアクションを選択します。 アクションとは、再利用可能なコードの単位です。」 とのこと
        - [uses exsamples](https://docs.github.com/ja/actions/using-workflows/workflow-syntax-for-github-actions#example-using-a-public-action): 参考例が書いてあるのでこれでわかりやすい
        - サンプルの `actions/checkout@v2` ではこれが使われている [actions/checkout: Action for checking out a repo](https://github.com/actions/checkout)
      - run: osのshellを使用して実行
