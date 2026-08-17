# CHATGPT.md

*[日本語版はこちら / Japanese version](CHATGPT.md)*

ChatGPT/Codex refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md). ChatGPT/Codex loads AGENTS.md natively, so this file is mainly used as a guide for connecting with ChatGPT.

Before any work—not only work within this repository—ChatGPT/Codex must actually read and follow all four of the following documents:

- [AGENTS.en.md](AGENTS.en.md)
- [CHATGPT.en.md](CHATGPT.en.md)
- [docs/rules.en.md](docs/rules.en.md)
- [docs/policy.en.md](docs/policy.en.md)

Even in environments where `AGENTS.md` is loaded automatically, the contents of the other three documents may not be loaded automatically. ChatGPT/Codex must review each document individually. If any document is missing, unreadable, or cannot be reviewed in full, it must not start the work and must inform the user.

## Usage Conditions

- Use with the learning feature turned off.

## How to Connect with ChatGPT

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are using ChatGPT (ChatGPT / Codex CLI), so each is described separately.

### Method A: For ChatGPT (chatgpt.com)

The most reliable approach is to write a sentence instructing ChatGPT to reference this repository under **Settings → Personalization → Custom Instructions**. Content written there is automatically applied to every new conversation, so there is no need to enable it each time like a connector.

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), read AGENTS.en.md, CHATGPT.en.md, docs/rules.en.md, and docs/policy.en.md in the `<your-github-username>/AI_GUIDE` repository and treat all four as instruction documents. If the GitHub connector is enabled, refer to it directly; if not, say so.

This alone ensures that even if you forget to set up the connector for a given conversation, ChatGPT is always aware that "there is something it should refer to." However, to actually read the latest contents of the repository, you still need to separately enable the GitHub connector for that conversation.

The GitHub connector itself can be set up as follows.

1. In ChatGPT, go to Settings → Connectors.
2. Add the GitHub connector and authenticate with your GitHub account.
3. Select the target repositories you want to grant access to, including this one.
4. When you reference this connector in a conversation, ChatGPT can fetch the repository contents each time.

Once connected, use ChatGPT to search, view, and analyze repository files. Where write functionality is available, create or update files only with the user's explicit instruction and confirmation. When using a private repository, include that repository in the authorized repository access. Obtain organizational approval when needed for organization-owned repositories. Connecting ChatGPT does not grant permissions that the user does not already have on GitHub.

Notes:

- The connector feature is available on paid plans (Plus/Pro/Team/Enterprise, etc.); availability on the Free plan is unconfirmed. On Enterprise/Edu plans it is disabled by default and an admin must enable it organization-wide.
- Neither custom instructions nor the connector guarantee that the repository is referenced in every conversation; explicitly asking ChatGPT to reference it may be more reliable.

### Official Information

- OpenAI Help Center: [Apps in ChatGPT](https://help.openai.com/en/articles/11487775-apps-in-chatgpt)
- OpenAI Help Center: [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)

GitHub integration availability, plan conditions, and authentication methods may change. Check the official OpenAI and GitHub information when using them.

### Method B: Have Codex CLI / Codex load it automatically (the most reliable option for an always-on connection)

Unlike Claude Code or Gemini CLI, Codex CLI does not support an `@file-path` import syntax. This means the global configuration file must contain the actual content itself, not a reference to it.

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Copy the contents of the cloned repository's `AGENTS.md` into your global configuration file, `~/.codex/AGENTS.md` (the base directory can be changed via the `$CODEX_HOME` environment variable; it defaults to `~/.codex`). Create the file if it does not already exist.
3. Codex CLI / Codex automatically loads both the global `~/.codex/AGENTS.md` and the `AGENTS.md` in the project you are working on (if present) every session, merging them into context.
4. When you update this repository, run `git pull` and then manually replace the contents of `~/.codex/AGENTS.md` with the latest version — this is not synced automatically.

If an always-on connection is the goal, Method B is the most reliable, but note that updates to the repository are not reflected automatically. Method A is a useful complement if you also want to reference the same content in ChatGPT from the browser.
