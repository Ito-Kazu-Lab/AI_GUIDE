# CHATGPT.md

*[English version](CHATGPT.en.md)*

ChatGPT/Codexは、本ファイルを案内として参照し、詳細な指示・ドキュメント構成については [AGENTS.md](AGENTS.md) を参照してください。ChatGPT/CodexはAGENTS.mdをネイティブに読み込むため、本ファイルは主にChatGPTとの連携方法の案内として用いる。

ChatGPT/Codexは、このリポジトリ内での作業前だけでなく、いかなる作業前にも、必ず [AGENTS.md](AGENTS.md) の内容に従ってください。

## 利用条件

- 学習機能をオフにして利用すること。

## ChatGPTとの連携方法

「常に」連携させるには、会話ごとの手動操作に頼らない仕組みが必要である。利用している場面（Web/モバイル/クラウドでの作業：ChatGPT（chatgpt.com） / ローカルでの作業：Codex CLI / Codex）によって設定場所が異なるため、常時GitHubと連携する方法をそれぞれ説明する。

ChatGPT/Codexでは、本リポジトリを自身のGitHubアカウントにフォークせず、`Ito-Kazu-Lab/AI_GUIDE` を直接参照できる。そのため、方法A・方法Bのいずれも、カスタム指示に `Ito-Kazu-Lab/AI_GUIDE` の参照を指示する文を書いておく方法とする。

### 方法A：常時GitHubと連携する方法（Web/モバイル/クラウドでの作業向け）

ChatGPT（chatgpt.com / モバイルアプリ）を対象とする。

**設定 → パーソナライズ（Personalization） → カスタム指示（Custom Instructions）** に、本リポジトリ（`Ito-Kazu-Lab/AI_GUIDE`）の参照を指示する一文を書いておく方法が最も確実である。ここに書いた内容はすべての新しい会話に自動的に適用されるため、コネクタのように毎回オンにする手間がない。

例：

> 研究室関連の作業（論文・レポート執筆、コーディング、資料作成など）を行う際は、`Ito-Kazu-Lab/AI_GUIDE` リポジトリの内容（特にAGENTS.md、CHATGPT.md、docs/rules.md、docs/policy.md）を指示書として扱ってください。GitHubコネクタが有効な場合は直接参照し、無効な場合はその旨を伝えてください。

これだけで、会話のたびにコネクタを設定し忘れても「参照すべきものがある」という前提だけは常にChatGPTに伝わる。ただし、実際にリポジトリの最新内容を読み込むには、その会話でGitHubコネクタも別途有効にする必要がある点は変わらない。

GitHubコネクタ自体は、以下の手順で利用できる。

1. ChatGPTで 設定 → Connectors（コネクタ） を開く。
2. GitHubコネクタを追加し、GitHubアカウントで認証する。
3. アクセスを許可するリポジトリとして、自身が利用する対象リポジトリを選択する。`Ito-Kazu-Lab/AI_GUIDE` は自身のアカウントにフォークせず直接参照できるため、本リポジトリのフォークを作成・選択する必要はない。
4. 会話内でこのコネクタを参照すると、ChatGPTがリポジトリの内容をその都度取得できる。

接続後は、ChatGPTからリポジトリ内のファイルを検索、参照、分析できる。書き込み機能が提供されている環境では、ユーザーの明示的な指示と確認に基づいてファイルを作成または更新すること。非公開リポジトリを利用する場合は、対象リポジトリをアクセス許可の対象に含める。組織所有リポジトリでは、必要に応じて組織管理者の承認を受ける。GitHub上で当該ユーザーが本来持っていない権限がChatGPTに追加されることはない。

注意点：

- コネクタ機能はPlus以上の有料プラン（Plus/Pro/Team/Enterprise等）向けに提供されている（無料プランでの利用可否は未確認）。Enterprise/Eduプランでは既定で無効になっており、管理者が組織単位で有効化する必要がある。
- カスタム指示・コネクタとも、会話ごとの参照が保証されるわけではなく、明示的に参照を指示した方が確実な場合がある。

### 公式情報

- OpenAI Help Center: [Apps in ChatGPT](https://help.openai.com/en/articles/11487775-apps-in-chatgpt)
- OpenAI Help Center: [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)
- OpenAI Codex Docs: [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
- OpenAI Codex Docs: [Settings](https://learn.chatgpt.com/docs/reference/settings)
- OpenAI Codex Docs: [Plugins](https://learn.chatgpt.com/docs/plugins)

GitHub連携の提供状況、プラン条件、認証方法およびCodexの設定画面は変更される可能性があるため、実際の運用時にはOpenAIおよびGitHubの公式情報を確認する。

### 方法B：常時GitHubと連携する方法（ローカルでの作業向け）

ローカル環境でのCodex CLI / Codex（ChatGPTデスクトップアプリのCodexを含む）による作業を対象とする。

方法Aと同様に、Codexの **カスタム指示** に、本リポジトリ（`Ito-Kazu-Lab/AI_GUIDE`）の参照を指示する文を書いておく方法が最も確実である。Codexのカスタム指示はグローバル設定ファイル `~/.codex/AGENTS.md`（`$CODEX_HOME`環境変数で変更可能。既定は `~/.codex`）に保存され、セッションごとに自動的に読み込まれるため、毎回指示し直す手間がない。本リポジトリをフォーク・クローンする必要はない。

カスタム指示は、利用している環境に応じて以下のいずれかの方法で編集する。

- ChatGPTデスクトップアプリ（Codex）の場合：**設定 → パーソナライズ（Personalization）** で、個人用の指示（`AGENTS.md`）を編集する。
- Codex CLIの場合：`~/.codex/AGENTS.md` を作成（既に存在する場合は追記）する。

例：

> すべての作業前に、`Ito-Kazu-Lab/AI_GUIDE` リポジトリのAGENTS.md、CHATGPT.md、docs/rules.md、docs/policy.mdを実際に開いて最後まで読み、その内容を指示書として従ってください。いずれかの文書が存在しない、読み取れない、または最後まで確認できない場合は、作業を開始せず、その旨を伝えてください。

Codex CLI / Codexはカスタム指示（`~/.codex/AGENTS.md`）を自動的に読み込むが、そこに記載されたMarkdownリンクや別ファイルの本文を自動的に展開するわけではない。そのため、例のように、`Ito-Kazu-Lab/AI_GUIDE` の必須文書を実際に読むようカスタム指示で明示する必要がある。

Codex CLI / Codexは、セッションごとにグローバルの `~/.codex/AGENTS.md`（カスタム指示）と、作業中のプロジェクトの `AGENTS.md`（存在する場合）を読み込み、コンテキストに結合する。CodexはGitHub上の `Ito-Kazu-Lab/AI_GUIDE` をその都度参照するため、本リポジトリが更新されても、カスタム指示を修正したり `git pull` を実行したりする必要はない。

注意点：

- Codexが `Ito-Kazu-Lab/AI_GUIDE` の内容を取得できる環境（GitHub連携用のプラグインの導入やネットワークアクセスの許可など）が必要である。プラグインは、ChatGPTデスクトップアプリでは「プラグイン（Plugins）」タブ、Codex CLIでは `/plugins` から導入できる（IDE拡張機能は非対応）。
- カスタム指示は、作業ごとの参照が保証されるわけではなく、明示的に参照を指示した方が確実な場合がある。
