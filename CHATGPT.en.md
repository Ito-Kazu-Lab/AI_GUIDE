# CHATGPT.md

*[日本語版はこちら / Japanese version](CHATGPT.md)*

ChatGPT/Codex refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md). ChatGPT/Codex loads AGENTS.md natively, so this file is mainly used as a guide for connecting with ChatGPT.

ChatGPT/Codex must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with ChatGPT

The setup method depends on which tool you are using (ChatGPT / Codex CLI).

### Method A: Connect via a connector in ChatGPT (chatgpt.com) (for browser-based chat use)

1. In ChatGPT, go to Settings → Connectors.
2. Add the GitHub connector and authenticate with your GitHub account.
3. Select the target repositories you want to grant access to, including this one.
4. When you reference this connector in a conversation, ChatGPT can fetch the repository contents each time.

Notes:

- The scope of the connector feature available may differ depending on your plan or contract type.
- You may need to explicitly reference the connector in each conversation (it is not necessarily referenced automatically every time).

### Method B: Have Codex CLI / Codex load it automatically (the most reliable option for an always-on connection)

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Codex CLI / Codex automatically loads the `AGENTS.md` file at the root of the repository (this repository's AGENTS.md) every session, so it is included in context each time without any explicit action.
3. To update the contents from this repository, simply run `git pull` to get the latest version.

If an always-on connection is the goal, Method B is the most reliable. Method A is a useful complement if you also want to reference the same content in ChatGPT from the browser.
