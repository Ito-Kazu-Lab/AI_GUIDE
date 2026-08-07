# GitHub Copilot 向け指示

*[English version](copilot-instructions.en.md)*

GitHub Copilotは、本ファイルを案内として参照し、詳細な指示・ドキュメント構成については [AGENTS.md](../AGENTS.md) を参照してください。

GitHub Copilotは、このリポジトリ内での作業前だけでなく、いかなる作業前にも、必ず [AGENTS.md](../AGENTS.md) の内容に従ってください。

## GitHub Copilotとの連携方法

利用しているツール（GitHub.com上のCopilot Chat / IDE上のCopilot）によって、設定方法が異なる。

### 方法A：GitHub.com上のCopilot Chatで都度参照する（ブラウザで手軽に使いたい場合）

1. GitHubアカウントでサインインし、対象リポジトリ（本リポジトリ）のページを開く。
2. リポジトリページから Copilot Chat を開く。
3. チャット内でリポジトリの内容について質問すると、開いているリポジトリのコンテキストが参照される。
4. 別のリポジトリやセッションで使う場合は、その都度対象リポジトリを開き直す必要がある。

### 方法B：IDE（VS Code等）でCopilotに自動的に読み込ませる（常時連携として最も確実）

1. 本リポジトリをローカルにクローンする（`git clone https://github.com/<GitHubユーザー名>/AI_GUIDE.git`）。
2. Copilotは、VS Code / Visual Studio / JetBrains などでワークスペースを開く際、そのリポジトリ内の `.github/copilot-instructions.md`（本ファイル）をカスタム指示として自動的に読み込む。
3. 本リポジトリの内容を更新したい場合は、`git pull` で最新化する。

常時連携が目的であれば方法B（`.github/copilot-instructions.md`の自動読み込み）が最も確実である。github.com上でリポジトリを開いて手軽に質問したい場合は、方法Aを補完手段として併用するとよい。
