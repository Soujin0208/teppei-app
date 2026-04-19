# 👨‍👩‍👦‍👦 家族セットアップ ガイド

このドキュメントは **パパ（管理者）** が 妻・子どもたちを このリポジトリに 追加するための手順です。

---

## 1️⃣ 家族メンバーを Collaborator として招待

### 妻・長男・次男・三男の GitHub アカウントを用意

まず全員が GitHub アカウントを持っている必要があります。未登録のメンバーは [github.com/signup](https://github.com/signup) で作成（年齢制限：GitHub は13歳以上）。

> 💡 13歳未満の場合は、パパのアカウントで作業するか、専用アカウントを「家族管理下」で作成してください。

### GitHub ユーザー名を確認

各メンバーの GitHub username をメモ：
- 妻：`____________`
- 長男：`____________`
- 次男：`____________`
- 三男：`____________`

### Collaborator 招待（コマンドで）

以下をパパのターミナルで実行（`USERNAME` を置き換え）：

```bash
gh api -X PUT repos/Soujin0208/teppei-app/collaborators/USERNAME -f permission=push
```

例：
```bash
gh api -X PUT repos/Soujin0208/teppei-app/collaborators/wife-github-name -f permission=push
gh api -X PUT repos/Soujin0208/teppei-app/collaborators/son1-github-name -f permission=push
gh api -X PUT repos/Soujin0208/teppei-app/collaborators/son2-github-name -f permission=push
gh api -X PUT repos/Soujin0208/teppei-app/collaborators/son3-github-name -f permission=push
```

各メンバーには招待メールが届きます。メール内のリンクから承諾してもらう。

> 🔒 `push` 権限 = 書き込みOK。main ブランチ直 push できる設定です。シンプルさ優先。混乱が出たら保護ブランチに変更。

---

## 2️⃣ 各メンバーの端末セットアップ

妻・子どもたちの Mac で 1回だけ：

### a) Homebrew（未インストールなら）
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### b) git, gh, Claude Code
```bash
brew install git gh
# Claude Code インストール：https://docs.anthropic.com/claude/docs/claude-code
```

### c) GitHub 認証（本人のアカウントで）
```bash
gh auth login
# → GitHub.com → HTTPS → Yes → Login with a web browser
```

### d) リポジトリ clone
```bash
cd ~
git clone https://github.com/Soujin0208/teppei-app.git 鉄平アプリ
cd 鉄平アプリ
```

完了！`gakushuu-portal.html` を ブラウザで ひらけば あそべます。

---

## 3️⃣ 子どもたちの ふだんの つかいかた

[`KIDS_GUIDE.md`](KIDS_GUIDE.md) を ひらいてください。子ども向けの やさしい ことばで かいてあります。

---

## 4️⃣ トラブル時

- **招待メールが届かない** → [https://github.com/Soujin0208/teppei-app/invitations](https://github.com/Soujin0208/teppei-app/invitations) を確認
- **push で怒られる** → `git pull` してから `git push`
- **conflict** → Claude に「コンフリクト解消して」と頼む
- **変なこと消えた** → `git log` で履歴確認、`git revert <commit>` で戻せる

---

## 🔐 プライバシー

このリポジトリは **Private**。Collaborator（家族）しか見られません。公開したい場合は GitHub の Settings → Visibility で変更可。
