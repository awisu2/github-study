# pricing

github での支払いについて

- [GitHub Pluns](https://github.co.jp/pricing.html)
- [GitHub Actions の支払いについて \- GitHub Docs](https://docs.github.com/ja/billing/managing-billing-for-github-actions/about-billing-for-github-actions#about-spending-limits)
- [GitHub Actions の使用状況を表示する \- GitHub Docs](https://docs.github.com/ja/billing/managing-billing-for-github-actions/viewing-your-github-actions-usage)
- 利用状況の確認: [Billing](https://github.com/settings/billing)

**NOTE**

普通に使う分には無料だけれど、色々やっていると上限に引っかかる

- プラン: 基本のサービス形態
  - Free < Team < Enterprise
  - それぞれ Actions の利用時間、private リポジトリの時間利用サイズが大きくなる
  - Team で コードオーナー, Enterprise で SaML による SSO、高度な監査機能が追加
  - よほど使い込んで Team、大きな/管理体制が厳しい企業で Enterprise だろうか
- Github Actions: .github\workflows に yaml ファイルを記載することで自動処理してくれる機能
  - 上記のプラントは別に計算される
  - os の利用時間, ストレージに対して上限を超えると料金がかかる
    - ストレージ: いまいちわからず.github/workflows 内のファイルのこと？
      - _各リポジトリの Actions メニューで表示されるログなどのことだと思われる_
        - 期限の設定: 各リポジトリ > Settings > Actions > general > Artifact and log retention
          - default: 90 日
          - cron 実行で Actions の strage を削除する方法もある
    - os の利用時間: Linux < Windows < macOS の順で高くなる
      - Actions が書く os で実行されている時間に対して料金がかかる。
      - ビルドや複雑なテストでコストが嵩んでいくだろうか
- なんか料金かかってきたなというときに
  - Github Actions のストレージが意外と罠に思える。
    - 料金がかかってくるようであれば 90 日の制限を短くしたり、cron 設定した Actions でストレージを消していく方法もあるようなので検討
    - 大きめのビルド結果を保存しているようであれば、外部サービスを検討、aws の s3 とか、google drive など
