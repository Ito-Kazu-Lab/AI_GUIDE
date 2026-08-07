# GitHub Copilot 向け指示

*[English version](copilot-instructions.en.md)*

GitHub Copilotは、本ファイルを案内として参照し、詳細な指示・ドキュメント構成については [AGENTS.md](../AGENTS.md) を参照してください。

GitHub Copilotは、このリポジトリ内での作業前だけでなく、いかなる作業前にも、必ず [AGENTS.md](../AGENTS.md) の内容に従ってください。

## GitHub Copilotとの連携方法

今使っているツールによって、設定方法が変わります。

### 方法A：GitHub.com上のCopilot Chatで都度参照する（ブラウザで手軽に使いたい場合）

1. GitHubアカウントでサインインし、対象リポジトリ（`Ito-Kazu-Lab/AI_GUIDE`）のページを開く
2. リポジトリページから Copilot Chat を開く
3. チャット内でリポジトリの内容について質問すると、開いているリポジトリのコンテキストが参照される
4. 別のリポジトリやセッションで使う場合は、その都度対象リポジトリを開き直す必要がある

### 方法B：IDE（VS Code等）でCopilotに「毎回自動的に」読み込ませる（すでに導入済みなので、こちらが確実）

1. リポジトリをローカルにクローンする（`git clone https://github.com/Ito-Kazu-Lab/AI_GUIDE.git`）
2. そのリポジトリ内の `.github/copilot-instructions.md`（本ファイル）に、AI_GUIDEの要点・ルールを記載しておく
3. VS Code / Visual Studio / JetBrains などでGitHub Copilotを有効にし、対象リポジトリをワークスペースとして開く
4. Copilotは `.github/copilot-instructions.md` をワークスペースのカスタム指示として自動的に読み込むため、明示的な読み込み操作なしで毎回コンテキストに入る
5. リポジトリ自体を更新したい時は `git pull` するだけで最新化できる

普段のコーディング作業でGitHub Copilotを使う場合は、方法B（`.github/copilot-instructions.md`の自動読み込み）が最も確実です。github.com上でリポジトリを開いて手軽に質問したい場合は方法Aを併用してください。
