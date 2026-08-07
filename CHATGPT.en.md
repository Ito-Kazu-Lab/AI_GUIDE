# CHATGPT.md

*[日本語版はこちら / Japanese version](CHATGPT.md)*

ChatGPT/Codex refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md). ChatGPT/Codex loads AGENTS.md natively, so this file is mainly used as a guide for connecting with ChatGPT.

ChatGPT/Codex must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with ChatGPT

The setup method depends on which tool you are currently using.

### Method A: Connect via a connector in ChatGPT (chatgpt.com) (for general chat use)

1. In ChatGPT, go to Settings → Connectors.
2. Add the GitHub connector and authenticate with your GitHub account.
3. Select the target repositories you want to grant access to, including `Ito-Kazu-Lab/AI_GUIDE`.
4. When you reference this connector in a conversation, ChatGPT can fetch the repository contents each time.

There are two points to note.

- The scope of the connector feature available may differ depending on your plan or contract type.
- You may need to explicitly reference the connector in each conversation (it is not necessarily referenced automatically every time).

### Method B: Have Codex CLI / Codex load it "automatically every time" (the reliable option)

1. Clone the repository locally (`git clone https://github.com/Ito-Kazu-Lab/AI_GUIDE.git`).
2. Record the key points and rules from AI_GUIDE in the `AGENTS.md` file at the root of that folder (this repository's AGENTS.md corresponds to it).
3. Codex CLI / Codex automatically loads AGENTS.md every session, so it is brought into context each time without any explicit action to load it.
4. To update the repository itself, simply run `git pull` to get the latest version.

For everyday work with Codex CLI, Method B is the most reliable. If you also want to reference the same content in ChatGPT in the browser, use Method A alongside it.
