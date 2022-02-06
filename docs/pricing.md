# pricing

githubでの支払いについて

- [GitHub Pluns](https://github.co.jp/pricing.html)
- [GitHub Actionsの支払いについて \- GitHub Docs](https://docs.github.com/ja/billing/managing-billing-for-github-actions/about-billing-for-github-actions#about-spending-limits)
- [GitHub Actions の使用状況を表示する \- GitHub Docs](https://docs.github.com/ja/billing/managing-billing-for-github-actions/viewing-your-github-actions-usage)
- 利用状況の確認: [Billing](https://github.com/settings/billing)

**NOTE**

普通に使う分には無料だけれど、色々やっていると上限に引っかかる

- プラン: 基本のサービス形態
  - Free < Team < Enterprise
  - それぞれ Actionsの利用時間、privateリポジトリの時間利用サイズが大きくなる
  - Teamで コードオーナー, EnterpriseでSaMLによるSSO、高度な監査機能が追加
  - よほど使い込んでTeam、大きな/管理体制が厳しい企業でEnterpriseだろうか
- Github Actions: .github\workflowsにyamlファイルを記載することで自動処理してくれる機能
  - 上記のプラントは別に計算される
  - osの利用時間, ストレージに対して上限を超えると料金がかかる
    - ストレージ: いまいちわからず.github/workflows内のファイルのこと？
      - *各リポジトリの Actions メニューで表示されるログなどのことだと思われる*
        - 期限の設定: 各リポジトリ > Settings > Actions > general > Artifact and log retention
          - default: 90日
          - cron実行でActionsのstrageを削除する方法もある
    - osの利用時間: Linux < Windows < macOSの順で高くなる
      - Actionsが書くosで実行されている時間に対して料金がかかる。
      - ビルドや複雑なテストでコストが嵩んでいくだろうか
- なんか料金かかってきたなというときに
  - Github Actions のストレージが意外と罠に思える。
    - 料金がかかってくるようであれば 90日の制限を短くしたり、cron 設定した Actionsでストレージを消していく方法もあるようなので検討
    - 大きめのビルド結果を保存しているようであれば、外部サービスを検討、aws のs3とか、google driveなど
