# CHATGPT.md

*[日本語版はこちら / Japanese version](CHATGPT.md)*

ChatGPT/Codex refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md). ChatGPT/Codex loads AGENTS.md natively, so this file is mainly used as a guide for connecting with ChatGPT.

ChatGPT/Codex must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## Usage Conditions

- Use with the learning feature turned off.

## How to Connect with ChatGPT

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are working (Web/mobile/cloud work: ChatGPT (chatgpt.com) / local work: Codex CLI / Codex), so the ways to keep an always-on GitHub connection are described separately for each.

ChatGPT/Codex can refer to `Ito-Kazu-Lab/AI_GUIDE` directly, without forking this repository to your own GitHub account. Therefore, both Method A and Method B consist of writing an instruction to reference `Ito-Kazu-Lab/AI_GUIDE` in the custom instructions.

### Method A: Always-on GitHub connection (for work on Web/mobile/cloud)

This applies to ChatGPT (chatgpt.com / mobile apps).

The most reliable approach is to write a sentence instructing ChatGPT to reference this repository (`Ito-Kazu-Lab/AI_GUIDE`) under **Settings → Personalization → Custom Instructions**. Content written there is automatically applied to every new conversation, so there is no need to enable it each time like a connector.

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), treat the contents of the `Ito-Kazu-Lab/AI_GUIDE` repository (especially AGENTS.en.md, CHATGPT.en.md, docs/rules.en.md, and docs/policy.en.md) as the instruction document. If the GitHub connector is enabled, refer to it directly; if not, say so.

This alone ensures that even if you forget to set up the connector for a given conversation, ChatGPT is always aware that "there is something it should refer to." However, to actually read the latest contents of the repository, you still need to separately enable the GitHub connector for that conversation.

The GitHub connector itself can be set up as follows.

1. In ChatGPT, go to Settings → Connectors.
2. Add the GitHub connector and authenticate with your GitHub account.
3. Select the target repositories you use and want to grant access to. Because `Ito-Kazu-Lab/AI_GUIDE` can be referenced directly without forking it to your own account, there is no need to create or select a fork of this repository.
4. When you reference this connector in a conversation, ChatGPT can fetch the repository contents each time.

Once connected, use ChatGPT to search, view, and analyze repository files. Where write functionality is available, create or update files only with the user's explicit instruction and confirmation. When using a private repository, include that repository in the authorized repository access. Obtain organizational approval when needed for organization-owned repositories. Connecting ChatGPT does not grant permissions that the user does not already have on GitHub.

Notes:

- The connector feature is available on paid plans (Plus/Pro/Team/Enterprise, etc.); availability on the Free plan is unconfirmed. On Enterprise/Edu plans it is disabled by default and an admin must enable it organization-wide.
- Neither custom instructions nor the connector guarantee that the repository is referenced in every conversation; explicitly asking ChatGPT to reference it may be more reliable.

### Official Information

- OpenAI Help Center: [Apps in ChatGPT](https://help.openai.com/en/articles/11487775-apps-in-chatgpt)
- OpenAI Help Center: [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)
- OpenAI Codex Docs: [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
- OpenAI Codex Docs: [Settings](https://learn.chatgpt.com/docs/reference/settings)
- OpenAI Codex Docs: [Plugins](https://learn.chatgpt.com/docs/plugins)

GitHub integration availability, plan conditions, authentication methods, and the Codex settings screens may change. Check the official OpenAI and GitHub information when using them.

### Method B: Always-on GitHub connection (for local work)

This applies to local work with Codex CLI / Codex (including Codex in the ChatGPT desktop app).

As with Method A, the most reliable approach is to write an instruction to reference this repository (`Ito-Kazu-Lab/AI_GUIDE`) in Codex's **custom instructions**. Codex's custom instructions are stored in the global configuration file `~/.codex/AGENTS.md` (the base directory can be changed via the `$CODEX_HOME` environment variable; it defaults to `~/.codex`) and are loaded automatically every session, so there is no need to repeat the instruction each time. There is no need to fork or clone this repository.

Edit the custom instructions in one of the following ways, depending on your environment:

- ChatGPT desktop app (Codex): edit your personal instructions (`AGENTS.md`) under **Settings → Personalization**.
- Codex CLI: create `~/.codex/AGENTS.md` (or append to it if it already exists).

Example:

> Before any work, actually open, read in full, and follow as the instruction document AGENTS.en.md, CHATGPT.en.md, docs/rules.en.md, and docs/policy.en.md in the `Ito-Kazu-Lab/AI_GUIDE` repository. If any of these documents is missing, unreadable, or cannot be reviewed in full, do not start work, and say so.

Codex CLI / Codex automatically loads the custom instructions (`~/.codex/AGENTS.md`), but it does not automatically expand Markdown links or load the contents of other files mentioned there. Therefore, as in the example, the custom instructions must explicitly tell Codex to actually read the required documents in `Ito-Kazu-Lab/AI_GUIDE`.

Codex CLI / Codex loads both the global `~/.codex/AGENTS.md` (custom instructions) and the `AGENTS.md` in the project you are working on (if present) each session, merging them into context. Because Codex refers to `Ito-Kazu-Lab/AI_GUIDE` on GitHub each time, there is no need to edit the custom instructions or run `git pull` when this repository is updated.

Notes:

- Codex needs an environment in which it can retrieve the contents of `Ito-Kazu-Lab/AI_GUIDE` (for example, a plugin for GitHub integration installed, or network access allowed). Plugins can be installed from the **Plugins** tab in the ChatGPT desktop app or with `/plugins` in Codex CLI (the IDE extension does not support plugins).
- Custom instructions do not guarantee that the repository is referenced in every task; explicitly asking Codex to reference it may be more reliable.
