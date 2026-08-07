# Instructions for GitHub Copilot

*[日本語版はこちら / Japanese version](copilot-instructions.md)*

GitHub Copilot refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](../AGENTS.en.md).

GitHub Copilot must always follow the contents of [AGENTS.en.md](../AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with GitHub Copilot

The setup method depends on which tool you are using (Copilot Chat on GitHub.com / Copilot in an IDE).

### Method A: Reference it each time via Copilot Chat on GitHub.com (for casual use in the browser)

1. Sign in with your GitHub account and open the page for the target repository (this repository).
2. Open Copilot Chat from the repository page.
3. When you ask about the repository's content in the chat, the context of the repository you have open is referenced.
4. To use it with a different repository or session, you need to open the target repository again each time.

### Method B: Have Copilot load it automatically in an IDE such as VS Code (the most reliable option for an always-on connection)

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. When you open the repository as a workspace in VS Code / Visual Studio / JetBrains, etc., Copilot automatically loads `.github/copilot-instructions.md` (this file) within that repository as custom instructions.
3. To update the contents from this repository, simply run `git pull` to get the latest version.

If an always-on connection is the goal, Method B (automatic loading of `.github/copilot-instructions.md`) is the most reliable. If you also want to ask quick questions by opening the repository on github.com, use Method A as a complement.
