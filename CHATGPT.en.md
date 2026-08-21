# CHATGPT.md

*[日本語版はこちら / Japanese version](CHATGPT.md)*

ChatGPT/Codex refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md). ChatGPT/Codex loads AGENTS.md natively, so this file is mainly used as a guide for connecting with ChatGPT.

ChatGPT/Codex must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## Usage Conditions

- Use with the learning feature turned off.

## How to Connect with ChatGPT

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are working (Web/mobile/cloud work: ChatGPT (chatgpt.com) / local work: Codex CLI / Codex), so the ways to keep an always-on GitHub connection are described separately for each.

### Method A: Always-on GitHub connection (for work on Web/mobile/cloud)

This applies to ChatGPT (chatgpt.com / mobile apps).

The most reliable approach is to write a sentence instructing ChatGPT to reference this repository under **Settings → Personalization → Custom Instructions**. Content written there is automatically applied to every new conversation, so there is no need to enable it each time like a connector.

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), treat the contents of the `<your-github-username>/AI_GUIDE` repository (especially CHATGPT.md and docs/rules.md) as the instruction document. If the GitHub connector is enabled, refer to it directly; if not, say so.

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

### Method B: Always-on GitHub connection (for local work)

This applies to local work with Codex CLI / Codex. It has the global configuration load the documents automatically and is the most reliable option for an always-on connection.

Codex CLI / Codex automatically loads the global configuration file `~/.codex/AGENTS.md`, but it does not automatically expand Markdown links or load the contents of other files mentioned there. Therefore, the global configuration must explicitly instruct Codex to read the required documents from a local clone of this repository.

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Create the global configuration file `~/.codex/AGENTS.md` (the base directory can be changed via the `$CODEX_HOME` environment variable; it defaults to `~/.codex`).
3. Using the absolute path to the clone, instruct Codex in `~/.codex/AGENTS.md` to actually open, read in full, and follow all four of the following documents before any work:
   - `AGENTS.en.md`
   - `CHATGPT.en.md`
   - `docs/rules.en.md`
   - `docs/policy.en.md`
4. Instruct Codex not to start work and to notify the user if any document is missing, unreadable, or cannot be reviewed in full.
5. Codex CLI / Codex loads both the global `~/.codex/AGENTS.md` and the `AGENTS.md` in the project you are working on (if present) each session, merging them into context.
6. When this repository is updated, run `git pull` in the local clone. If the global configuration refers to the local documents by absolute path, there is no need to copy their contents into `~/.codex/AGENTS.md` again.

Method B is the most reliable option for an always-on connection, but Codex must have local permission to read all four documents.
