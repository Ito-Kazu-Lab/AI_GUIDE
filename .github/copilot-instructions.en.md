# Instructions for GitHub Copilot

*[日本語版はこちら / Japanese version](copilot-instructions.md)*

GitHub Copilot refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](../AGENTS.en.md).

GitHub Copilot must always follow the contents of [AGENTS.en.md](../AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with GitHub Copilot

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are using Copilot (Copilot Chat on GitHub.com / Copilot in an IDE), so each is described separately.

### Method A: For Copilot Chat on GitHub.com

Writing a sentence instructing Copilot to reference this repository under **Copilot Chat (github.com/copilot) → the profile icon in the bottom-left → "Personal instructions"** applies it automatically to every Copilot Chat conversation on github.com.

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), treat the contents of the `<your-github-username>/AI_GUIDE` repository (especially .github/copilot-instructions.md and docs/rules.md) as the instruction document.

Notes:

- Personal instructions apply only to Copilot Chat on github.com; they are not automatically applied to Copilot in an IDE (VS Code, etc.).
- The priority order for instructions is: personal instructions > repository instructions (`.github/copilot-instructions.md`) > organization instructions.

To have Copilot actually reference this repository's content, open the target repository's page and chat from there:

1. Sign in with your GitHub account and open the page for the target repository (this repository).
2. Open Copilot Chat from the repository page.
3. When you ask about the repository's content in the chat, the context of the repository you have open is referenced.

### Method B: Have Copilot load it automatically in an IDE such as VS Code (the most reliable option for an always-on connection)

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. When you open the repository as a workspace in VS Code / Visual Studio / JetBrains, etc., Copilot automatically loads `.github/copilot-instructions.md` (this file) within that repository as custom instructions.
3. To update the contents from this repository, simply run `git pull` to get the latest version.

This is automatic loading scoped to a single repository (project). If you want it loaded "always," across multiple projects, there is also a user-level (global) instructions feature in each IDE (for example, in VS Code, you can use the Command Palette → "Chat: New Instructions File" → "User instructions"). However, this feature varies and changes frequently depending on the IDE and version, so check your IDE's Copilot settings for the exact current setup steps.

If an always-on connection is the goal, Method B (automatic loading of `.github/copilot-instructions.md`) is the most reliable. If you also want to ask quick questions by opening the repository on github.com, use Method A alongside it.
