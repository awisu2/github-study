# private access token

private access tokenについて

- [個人アクセストークンを使用する \- GitHub Docs](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
- personal access tokens の発行/確認ページ: [Personal Access Tokens](https://github.com/settings/tokens)
- [GitHub CLI \| Take GitHub to the command line](https://cli.github.com/)

簡易説明

- private access token(PAT)とは: githubのリポジトリにアクセスする際、一定のアクセス認証をかけ、それに対応する個人用 token の発行ができる
- 通常は、発行されたtokenをpasswordの代わりに利用する

## todo

- ghのloginコマンドを利用する

## 毎回の入力を回避する(自動入力にする)方法

以下の方法がある

- gitのurlを更新し

### gitにurlの入れ替えをさせる

- insteadOfのurlを前に設定されているものに変更し、patを自動セットする
- 複数セットしてあると前方一致してしまうので、insteadOfがかぶる場合は必要な方を残すこと

note: いつまで使えるかは不明。以前に書いたメモから抜粋している。現在も動作しているが公式documentが存在しない。httpプロトコルでもx-oauth-basicに関する情報が出てこない。

```bash
TOKEN={your access token}
git config --global url."https://${TOKEN}:x-oauth-basic@github.com/".insteadOf "https://github.com/"
````

*~/.gitconfig*

こんな感じになる

```gitconfig
[url "https://{your access token}:x-oauth-basic@github.com/"]
        insteadOf = https://github.com/
```

### ghコマンドを利用する

- [GitHub CLI \| Take GitHub to the command line](https://cli.github.com/)
- [Caching your GitHub credentials in Git \- GitHub Docs](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git)

- [] gh loginをすることで事前にtokenをセットしておくことができるとのこと
