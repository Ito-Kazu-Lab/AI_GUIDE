# インシデント記録：claude.aiのGitHub Copilotコネクタでprivateリポジトリが404になる

*[English version](2026-08-18-github-copilot-connector-private-repo-404.en.md)*

[インシデント記録一覧](index.md)に戻る

## 概要

- **発生日**：2026-08-18
- **報告者**：YoshiyukiHatta
- **記録日**：2026-08-18
- **状態**：未解決（原因未確定、回避策あり）
- **対象**：claude.aiチャット（Web/モバイル）のGitHub連携（コネクタ）
- **対象外**：Claude Code（本リポジトリおよび`Instruction4Lab`を扱う今回のセッションを含む）は影響を受けていない

## 事象

claude.aiのチャットにおいて、`GitHub Copilot`という名前のコネクタ（ツール）経由で、privateリポジトリ `YoshiyukiHatta/Instruction4Lab`（`Ito-Kazu-Lab/Instruction4Lab`からのfork）へアクセスしようとしたところ、一貫して `404 Not Found` となり、リポジトリ内容を取得できなかった。

同じアカウントから`AI_GUIDE`リポジトリへは正常にアクセスできており、`Instruction4Lab`固有の問題であることを確認済み。

## 調査内容

以下を確認したが、いずれも問題は見当たらなかった。

1. `get_me`ツールで、GitHub連携の認証アカウントが確かに `YoshiyukiHatta`（リポジトリオーナー本人）であることを確認した。
2. GitHub側の `Settings → Applications → Installed GitHub Apps` を確認したところ、「Claude」というGitHub Appがインストール済みで、`Permissions: Read/Write`、`Repository access: All repositories` に設定されていた（＝private repoを含め、アクセス許可されているはずの設定）。
3. コネクタの切断・再接続を試みたが、リポジトリアクセスの許可を求める同意画面（Repository access / Private repositoriesへの同意）自体が表示されなかった。
4. GitHub側の `Installed GitHub Apps` には「ChatGPT Codex Connector」と「Claude」のみが存在し、実際にツールとして使われている「GitHub Copilot」という名前のAppは存在しなかった。
5. GitHub側の `Authorized OAuth Apps` も確認したが、Git Credential Manager／GitHub／GitHub Android／GitHub CLI／GitHub Desktop／Visual Studio Codeのみで、Claude/GitHub Copilotに該当するものはなかった。
6. Claudeの利用はチームやEnterpriseの管理者アカウントではなく、個人アカウントでの利用であることを確認した。

## 結論・原因

原因は確定していない。ログから確認できる事実と、そこからの推測は以下の通り区別する。

**確認できた事実**：

- GitHub側の個人アカウント設定（Installed GitHub Apps、Authorized OAuth Apps）のどこにも、実際にアクセスに使われている「GitHub Copilot」コネクタに対応する認可が見当たらない。
- GitHub Appとして表示されている「Claude」は `All repositories` 権限を持つが、それでも404が解消しない。

**推測（未確定）**：

- Claude側で実際に使われている「GitHub Copilot」ツールは、ユーザーの個人GitHub設定画面に表示される「Claude」Appとは別の認証経路（Anthropic側の組織／ワークスペース単位のカスタムコネクタなど）を使っている可能性がある。
- その場合、個人のGitHubアカウント側でどれだけ権限を確認・再設定しても解消しない可能性がある。

いずれも未検証の推測であり、Anthropic側の実装詳細に依存するため、本リポジトリの記録だけでは確定できない。

## 回避策

- リポジトリ内容をコピー＆ペーストで直接チャットに共有する。
- Claude Code（本セッションのようなリポジトリ添付型のセッション）を利用する。今回確認した範囲では、Claude Codeは同じprivateリポジトリ（`Instruction4Lab`）に問題なくアクセスできている。

## 関連

- `Instruction4Lab`リポジトリの`CLAUDE.md`更新履歴：GitHub連携方法がPAT方式（2026-08-04）→Claudeでの利用禁止（2026-08-11）→本リポジトリ（`AI_GUIDE`）への集約、と変遷している。
- 本リポジトリ`CLAUDE.md`「Claudeとの連携方法」節の方法A（claude.aiチャット向けのGitHub公式リモートMCPコネクタ）は、本インシデントの事象と矛盾する可能性があるため、利用者は鵜呑みにせず、privateリポジトリでは動作しない場合があることを踏まえること。
