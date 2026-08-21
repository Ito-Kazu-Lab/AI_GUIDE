# CLAUDE.md

*[日本語版はこちら / Japanese version](CLAUDE.md)*

Claude Code refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Claude Code must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## Usage Conditions

- Use with the learning feature turned off.

## Reading and Writing Repositories on GitHub

Using a Personal Access Token (fine-grained or classic) to read or write repositories on GitHub from Claude is prohibited.

Do not enter other credentials, such as passwords or SSH private keys, into chat. If credential exposure is suspected, revoke the credential immediately and contact a faculty member or administrator.

## How to Connect with Claude

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are working (Web/mobile/cloud work: general chat on claude.ai / local work: Claude Code), so the ways to keep an always-on GitHub connection are described separately for each.

### Method A: Always-on GitHub connection (for work on Web/mobile/cloud)

This applies to general chat on claude.ai (Web/mobile apps) and to work in the cloud.

The most reliable approach is to write a sentence instructing Claude to reference this repository under **Settings → Profile → "What personal preferences should Claude know about?"**. Content written there is automatically loaded into every new conversation, so there is no need to toggle it on each time, unlike a connector.

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), treat the contents of the `<your-github-username>/AI_GUIDE` repository (especially CLAUDE.md and docs/rules.md) as the instruction document. If the GitHub connector is enabled, refer to it directly; if not, say so.

This alone ensures that even if you forget to turn on the connector for a given conversation, Claude is always aware that "there is something it should refer to." However, to actually read the latest contents of the repository, you still need to separately turn on the GitHub connector for that conversation.

The GitHub connector itself can be set up by registering GitHub's own officially hosted remote MCP server as a custom connector.

1. No setup is required on the GitHub side (OAuth authentication only).
2. In claude.ai, go to Settings → Connectors → Add custom connector.
3. Enter `https://api.githubcopilot.com/mcp/` as the URL.
4. Authenticate with your GitHub account and approve the scopes (grant access to the target repositories, including this one).
5. Turn this connector on within a conversation so Claude can fetch the repository contents each time.

Notes:

- **Currently, Method A (the GitHub connector) works only with public repositories, even on paid plans.** Attempting to access a private repository results in `404 Not Found` and the contents cannot be retrieved (see the [incident record](docs/incidents/2026-08-18-github-copilot-connector-private-repo-404.en.md)). To reference a private repository, use Method B (local work) or paste the file contents directly into the chat.
- Custom connectors are available only on paid plans (Pro or higher).
- The connector is turned on/off per conversation; it does not stay on automatically. You need to enable it each time you start a new conversation.

### Method B: Always-on GitHub connection (for local work)

This applies to local work with Claude Code.

You can also place a `CLAUDE.md` file in each individual project, but setting up your **global configuration file** to load this repository is more reliable, since it is then loaded automatically no matter which project you are working in.

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Add one line each for the cloned repository's `AGENTS.md`, `docs/rules.md`, and `docs/policy.md` to your global configuration file — `~/.claude/CLAUDE.md` (on Windows, `C:\Users\<your-username>\.claude\CLAUDE.md`; on macOS/Linux, `/home/<your-username>/.claude/CLAUDE.md` or similar) — using the `@` import syntax. Create the file if it does not already exist.

   ```
   @<absolute-path-to-the-cloned-repository>/AGENTS.md
   @<absolute-path-to-the-cloned-repository>/docs/rules.md
   @<absolute-path-to-the-cloned-repository>/docs/policy.md
   ```

   Example (Windows):

   ```
   @C:\Users\<your-username>\path\to\AI_GUIDE\AGENTS.md
   @C:\Users\<your-username>\path\to\AI_GUIDE\docs\rules.md
   @C:\Users\<your-username>\path\to\AI_GUIDE\docs\policy.md
   ```

   > **Note**: The references to `docs/rules.md` and `docs/policy.md` inside `AGENTS.md` are ordinary Markdown links, not Claude Code's `@` import syntax. Therefore, importing only `AGENTS.md` with `@` will not automatically expand the contents of those files into context. If you want the compliance/prohibition rules (docs/rules.md) and the basic AI usage policy (docs/policy.md) to be loaded reliably every time, you need to `@`-import them individually as shown above.

3. Claude Code automatically loads the global `CLAUDE.md` every session and expands each file referenced by `@` (AGENTS.md, docs/rules.md, docs/policy.md) into context, so their contents are loaded every time without any explicit action, regardless of which project you are working in.
4. To update the contents from this repository, simply run `git pull`, and the latest version will be reflected starting with your next session.

### Summary

| Method | Context | Setup Location | Effect |
| --- | --- | --- | --- |
| Method A | Web/mobile/cloud work (general chat on claude.ai) | Settings → Profile → Personal preferences | The instruction to refer to the repository is automatically loaded in every conversation (you still need to separately turn on the connector to fetch the actual content, and it currently works only with public repositories). |
| Method B | Local work (Claude Code) | Global configuration file `~/.claude/CLAUDE.md` (`@`-import AGENTS.md, docs/rules.md, docs/policy.md) | The content is automatically loaded every session, regardless of which project you are working in. |

Setting up both gets you close to a state where laboratory-related work always takes this repository into account.