# private access token

private access token について

- [個人アクセストークンを使用する \- GitHub Docs](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
- personal access tokens の発行/確認ページ: [Personal Access Tokens](https://github.com/settings/tokens)
- [GitHub CLI \| Take GitHub to the command line](https://cli.github.com/)

簡易説明

- private access token(PAT)とは: github のリポジトリにアクセスする際、一定のアクセス認証をかけ、それに対応する個人用 token の発行ができる
- 通常は、発行された token を password の代わりに利用する

## todo

- gh の login コマンドを利用する

## 毎回の入力を回避する(自動入力にする)方法

以下の方法がある

- git の url を更新し

### git に url の入れ替えをさせる

- insteadOf の url を前に設定されているものに変更し、pat を自動セットする
- 複数セットしてあると前方一致してしまうので、insteadOf がかぶる場合は必要な方を残すこと

note: いつまで使えるかは不明。以前に書いたメモから抜粋している。現在も動作しているが公式 document が存在しない。http プロトコルでも x-oauth-basic に関する情報が出てこない。

```bash
TOKEN={your access token}
git config --global url."https://${TOKEN}:x-oauth-basic@github.com/".insteadOf "https://github.com/"
```

_~/.gitconfig_

こんな感じになる

```gitconfig
[url "https://{your access token}:x-oauth-basic@github.com/"]
        insteadOf = https://github.com/
```

### gh コマンドを利用する

- [GitHub CLI \| Take GitHub to the command line](https://cli.github.com/)
- [Caching your GitHub credentials in Git \- GitHub Docs](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git)

- [] gh login をすることで事前に token をセットしておくことができるとのこと
