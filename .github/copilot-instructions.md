# GitHub Copilot 向け指示

*[English version](copilot-instructions.en.md)*

GitHub Copilotは、本ファイルを案内として参照し、詳細な指示・ドキュメント構成については [AGENTS.md](../AGENTS.md) を参照してください。

GitHub Copilotは、このリポジトリ内での作業前だけでなく、いかなる作業前にも、必ず [AGENTS.md](../AGENTS.md) の内容に従ってください。

GitHub上のリポジトリを参照・更新する場合は、GitHub Copilotの利用を推奨する。

## 利用条件

- GitHubアカウントを大学メールアドレスにリンクして作成すること。
- GitHub Educationの申請を行うこと。GitHub Copilot Proを無料で利用できる場合があるため、対象となる学生・教職員は申請を検討する。利用資格、提供内容、適用条件および最新情報は、[GitHub Educationの公式情報](https://github.com/education)で確認する。GitHub Copilot Proが無条件で無料になることを意味するものではない。
- 学習機能をオフにして利用すること。

## GitHub Copilotとの連携方法

「常に」連携させるには、会話ごとの手動操作に頼らない仕組みが必要である。利用している場面（Web/モバイル/クラウドでの作業：GitHub.com上のCopilot Chat / ローカルでの作業：IDE上のCopilot）によって設定場所が異なるため、常時GitHubと連携する方法をそれぞれ説明する。

### 方法A：常時GitHubと連携する方法（Web/モバイル/クラウドでの作業向け）

GitHub.com上のCopilot Chat（Web/モバイルアプリ）を対象とする。

**Copilot Chat（github.com/copilot） → 左下のプロフィールアイコン → 「Personal instructions（個人用の指示）」** に、本リポジトリの参照を指示する一文を書いておくと、github.com上のすべてのCopilot Chatの会話に自動的に適用される。

例：

> 研究室関連の作業（論文・レポート執筆、コーディング、資料作成など）を行う際は、`<GitHubユーザー名>/AI_GUIDE` リポジトリの内容（特に.github/copilot-instructions.mdとdocs/rules.md）を指示書として扱ってください。

注意点：

- 個人用の指示は、github.com上のCopilot Chatにのみ適用され、IDE（VS Code等）のCopilotには自動的には適用されない。
- 指示の優先順位は「個人用の指示 ＞ リポジトリの指示（`.github/copilot-instructions.md`） ＞ 組織の指示」の順である。

実際にリポジトリの内容を参照させたい場合は、以下の手順で対象リポジトリのページを開いてチャットする。

1. GitHubアカウントでサインインし、対象リポジトリ（本リポジトリ）のページを開く。
2. リポジトリページから Copilot Chat を開く。
3. チャット内でリポジトリの内容について質問すると、開いているリポジトリのコンテキストが参照される。

### 方法B：常時GitHubと連携する方法（ローカルでの作業向け）

ローカル環境のIDE（VS Code等）上のCopilotを対象とする。Copilotに自動的に読み込ませる方法であり、常時連携として最も確実である。

1. 本リポジトリをローカルにクローンする（`git clone https://github.com/<GitHubユーザー名>/AI_GUIDE.git`）。
2. Copilotは、VS Code / Visual Studio / JetBrains などでワークスペースを開く際、そのリポジトリ内の `.github/copilot-instructions.md`（本ファイル）をカスタム指示として自動的に読み込む。
3. 本リポジトリの内容を更新したい場合は、`git pull` で最新化する。

これはリポジトリ（プロジェクト）単位での自動読み込みである。複数のプロジェクトを横断して「常に」読み込ませたい場合は、IDEごとのユーザー（グローバル）レベルの指示機能を利用する方法もある（例：VS Codeではコマンドパレットから「Chat: New Instructions File」→「User instructions」を選択する）。ただしこの機能はIDEやバージョンによって仕様が異なり変更も多いため、正確な設定方法は利用中のIDEのCopilot設定画面で確認すること。

常時連携が目的であれば方法B（`.github/copilot-instructions.md`の自動読み込み）が最も確実である。github.com上で手軽に質問したい場合は、方法Aを併用するとよい。
