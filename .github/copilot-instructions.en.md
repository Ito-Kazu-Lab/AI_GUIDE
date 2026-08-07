# Instructions for GitHub Copilot

*[日本語版はこちら / Japanese version](copilot-instructions.md)*

GitHub Copilot refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](../AGENTS.en.md).

GitHub Copilot must always follow the contents of [AGENTS.en.md](../AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with GitHub Copilot

The setup method depends on which tool you are currently using.

### Method A: Reference it each time via Copilot Chat on GitHub.com (for casual use in the browser)

1. Sign in with your GitHub account and open the page for the target repository (`Ito-Kazu-Lab/AI_GUIDE`).
2. Open Copilot Chat from the repository page.
3. When you ask about the repository's content in the chat, the context of the repository you have open is referenced.
4. To use it with a different repository or session, you need to open the target repository again each time.

### Method B: Have Copilot load it "automatically every time" in an IDE such as VS Code (already set up, so this is the reliable option)

1. Clone the repository locally (`git clone https://github.com/Ito-Kazu-Lab/AI_GUIDE.git`).
2. Record the key points and rules from AI_GUIDE in `.github/copilot-instructions.md` (this file) within that repository.
3. Enable GitHub Copilot in VS Code / Visual Studio / JetBrains, etc., and open the target repository as your workspace.
4. Copilot automatically loads `.github/copilot-instructions.md` as custom instructions for the workspace, so it is brought into context each time without any explicit action to load it.
5. To update the repository itself, simply run `git pull` to get the latest version.

For everyday coding work with GitHub Copilot, Method B (automatic loading of `.github/copilot-instructions.md`) is the most reliable. If you also want to ask quick questions by opening the repository on github.com, use Method A alongside it.
