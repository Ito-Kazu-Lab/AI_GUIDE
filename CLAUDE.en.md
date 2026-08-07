# CLAUDE.md

*[日本語版はこちら / Japanese version](CLAUDE.md)*

Claude Code refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Claude Code must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with Claude

The setup method depends on which tool you are using (claude.ai / Claude Code).

### Method A: Connect via a custom connector in claude.ai (for browser-based chat use)

GitHub is not yet listed among the "one-click official directory apps," but you can register GitHub's own officially hosted remote MCP server as a custom connector.

1. No setup is required on the GitHub side (OAuth authentication only).
2. In claude.ai, go to Settings → Connectors → Add custom connector.
3. Enter `https://api.githubcopilot.com/mcp/` as the URL.
4. Authenticate with your GitHub account and approve the scopes (grant access to the target repositories, including this one).
5. Turn this connector on in each conversation so Claude can fetch the repository contents each time.

Notes:

- Custom connectors are available only on paid plans (Pro or higher).
- The connector is turned on/off per conversation; it does not stay on automatically. You need to enable it each time you start a new conversation.

### Method B: Have Claude Code load it automatically (the most reliable option for an always-on connection)

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Place this file (`CLAUDE.md`), or a summary of it, at the root of the project you are working on.
3. Claude Code automatically loads `CLAUDE.md` every session, so it is included in context each time without any explicit action.
4. To update the contents from this repository, simply run `git pull` to get the latest version.

If an always-on connection is the goal, Method B is the most reliable. Method A is a useful complement if you also want to reference the same repository from browser-based chat.
