# CLAUDE.md

*[日本語版はこちら / Japanese version](CLAUDE.md)*

Claude Code refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Claude Code must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with Claude

The setup method depends on which tool you are currently using.

### Method A: Always-on connection via a custom connector in claude.ai (for general chat use)

GitHub is not yet listed in the "one-click official directory apps," but you can register GitHub's own officially hosted remote MCP server as a custom connector.

1. No setup is required on the GitHub side (OAuth authentication only).
2. In claude.ai, go to Settings → Connectors → Add custom connector.
3. Enter `https://api.githubcopilot.com/mcp/` as the URL.
4. Authenticate with your GitHub account and approve the scope (grant access to the target repositories, including `Ito-Kazu-Lab/AI_GUIDE`).
5. Turn this connector on in each conversation so Claude can fetch the repository contents each time.

There are two points to note.

- Custom connectors are a feature limited to paid plans (Pro or higher).
- Even though it is an "always-on connection," the connector is turned on/off per conversation, so you still need to toggle it on each time you start a new conversation (it does not turn on automatically).

### Method B: Have Claude Code load it "automatically every time" (already set up, so this is the reliable option)

Since you have already set up Claude Code before, this method better fits the goal of an "always-on connection."

1. Clone the repository locally (`git clone https://github.com/Ito-Kazu-Lab/AI_GUIDE.git`).
2. Place a `CLAUDE.md` file in that folder (or the root of your working project) and record the key points and rules from AI_GUIDE in it.
3. Claude Code automatically loads CLAUDE.md every session, so it is brought into context each time without any explicit action to load it.
4. To update the repository itself, simply run `git pull` to get the latest version.

Since you mentioned wanting to use Claude Code for everyday writing in Word and organizing documents, Method B — summarizing the contents of AI_GUIDE (writing rules, naming conventions, etc.) in CLAUDE.md — lets it be referenced automatically every time. Method A is a good complement if you also want to view the same repository from chat in the browser.

If you have decided which approach to focus on, I can help further with the specific wording of CLAUDE.md or the connector authentication steps.
