# git

## 基本設定

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

## revert コミットの(マージも含む)打消し

- [【gitコマンド】いまさらのrevert \- Qiita](https://qiita.com/chihiro/items/2fa827d0eac98109e7ee)

---

- 打消しするコミットを作る
- revertを戻したいときはrevertをrevert すればよい
- 現在のブランチにコミットされる
  - 明示的にしたい場合は、先にブランチ切り替えてから実行する

```bash
# 取り消したいコミットを確認
git log --oneline
# コミットの 詳細確認 左が1 右が2らしい
git show <commit>
# revert (取り消し, 基本 1 のはず)
git revert -m 1 <commit>
```
