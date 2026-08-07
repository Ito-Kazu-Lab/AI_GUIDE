# CLAUDE.md

*[日本語版はこちら / Japanese version](CLAUDE.md)*

Claude Code refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Claude Code must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with Claude

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are using Claude (general chat on claude.ai / Claude Code), so each is described separately.

### Method A: For general chat on claude.ai (Web/mobile)

The most reliable approach is to write a sentence instructing Claude to reference this repository under **Settings → Profile → "What personal preferences should Claude know about?"**. Content written there is automatically loaded into every new conversation, so there is no need to toggle it on each time, unlike a connector.

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), treat the contents of the `<your-github-username>/AI_GUIDE` repository (especially CLAUDE.md and docs/rules.md) as the laboratory's instruction document. If the GitHub connector is enabled, refer to it directly; if not, say so.

This alone ensures that even if you forget to turn on the connector for a given conversation, Claude is always aware that "there is something it should refer to." However, to actually read the latest contents of the repository, you still need to separately turn on the GitHub connector for that conversation.

The GitHub connector itself can be set up by registering GitHub's own officially hosted remote MCP server as a custom connector.

1. No setup is required on the GitHub side (OAuth authentication only).
2. In claude.ai, go to Settings → Connectors → Add custom connector.
3. Enter `https://api.githubcopilot.com/mcp/` as the URL.
4. Authenticate with your GitHub account and approve the scopes (grant access to the target repositories, including this one).
5. Turn this connector on within a conversation so Claude can fetch the repository contents each time.

Notes:

- Custom connectors are available only on paid plans (Pro or higher).
- The connector is turned on/off per conversation; it does not stay on automatically. You need to enable it each time you start a new conversation.

### Method B: For Claude Code

You can also place a `CLAUDE.md` file in each individual project, but setting up your **global configuration file** to load this repository is more reliable, since it is then loaded automatically no matter which project you are working in.

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Add a single line to your global configuration file — `~/.claude/CLAUDE.md` (on Windows, `C:\Users\<your-username>\.claude\CLAUDE.md`; on macOS/Linux, `/home/<your-username>/.claude/CLAUDE.md` or similar) — using the `@` import syntax to reference the cloned repository's `AGENTS.md`. Create the file if it does not already exist.

   ```
   @<absolute-path-to-the-cloned-repository>/AGENTS.md
   ```

   Example (Windows):

   ```
   @C:\Users\<your-username>\path\to\AI_GUIDE\AGENTS.md
   ```

3. Claude Code automatically loads the global `CLAUDE.md` every session and expands the file referenced by `@` into context, so the contents of this repository are loaded every time without any explicit action, regardless of which project you are working in.
4. To update the contents from this repository, simply run `git pull`, and the latest version will be reflected starting with your next session.

### Summary

| Context | Setup Location | Effect |
| --- | --- | --- |
| General chat on claude.ai | Settings → Profile → Personal preferences | The instruction to refer to the repository is automatically loaded in every conversation (you still need to separately turn on the connector to fetch the actual content). |
| Claude Code | Global configuration file `~/.claude/CLAUDE.md` (`@` import) | The content is automatically loaded every session, regardless of which project you are working in. |

Setting up both gets you close to a state where laboratory-related work always takes this repository into account.
