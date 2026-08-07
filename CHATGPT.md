# CHATGPT.md

*[English version](CHATGPT.en.md)*

ChatGPT/Codexは、本ファイルを案内として参照し、詳細な指示・ドキュメント構成については [AGENTS.md](AGENTS.md) を参照してください。ChatGPT/CodexはAGENTS.mdをネイティブに読み込むため、本ファイルは主にChatGPTとの連携方法の案内として用います。

ChatGPT/Codexは、このリポジトリ内での作業前だけでなく、いかなる作業前にも、必ず [AGENTS.md](AGENTS.md) の内容に従ってください。

## ChatGPTとの連携方法

今使っているツールによって、設定方法が変わります。

### 方法A：ChatGPT（chatgpt.com）でコネクタとして連携する（チャット全般で使いたい場合）

1. ChatGPTで 設定 → Connectors（コネクタ） を開く
2. GitHubコネクタを追加し、GitHubアカウントで認証する
3. アクセスを許可するリポジトリとして `Ito-Kazu-Lab/AI_GUIDE` を含む対象リポジトリを選択する
4. 会話内でこのコネクタを参照すると、ChatGPTがリポジトリの中身をその都度取得できる

注意点が2つあります。

- コネクタ機能は利用しているプラン・契約形態によって使える範囲が異なる場合がある
- 会話ごとにコネクタの参照を指示する必要がある場合がある（自動で毎回参照されるとは限らない）

### 方法B：Codex CLI / Codexで「毎回自動的に」読み込ませる（確実な方法）

1. リポジトリをローカルにクローンする（`git clone https://github.com/Ito-Kazu-Lab/AI_GUIDE.git`）
2. そのフォルダのルートに置かれた `AGENTS.md`（本リポジトリのAGENTS.mdが該当）に、AI_GUIDEの要点・ルールを記載しておく
3. Codex CLI / CodexはセッションごとにAGENTS.mdを自動で読み込むため、明示的に読み込ませる操作なしで毎回コンテキストに入る
4. リポジトリ自体を更新したい時は `git pull` するだけで最新化できる

普段の作業でCodex CLIを使う場合は、方法Bが最も確実です。ブラウザ上のChatGPTでも同じ内容を参照したい場合は、方法Aを併用してください。
