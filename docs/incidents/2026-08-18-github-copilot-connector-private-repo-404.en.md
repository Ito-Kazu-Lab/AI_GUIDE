# Incident Record: GitHub Copilot connector on claude.ai returns 404 for a private repository

*[日本語版](2026-08-18-github-copilot-connector-private-repo-404.md)*

Back to [incident index](index.en.md)

## Summary

- **Date occurred**: 2026-08-18
- **Reported by**: YoshiyukiHatta
- **Date recorded**: 2026-08-18
- **Status**: Unresolved (root cause undetermined; a workaround exists)
- **Scope**: GitHub integration (connector) in the claude.ai chat interface (Web/mobile)
- **Out of scope**: Claude Code (including the session that authored this record and the one working on `Instruction4Lab`) was not affected

## Symptom

In a claude.ai chat, attempting to access the private repository `YoshiyukiHatta/Instruction4Lab` (a fork of `Ito-Kazu-Lab/Instruction4Lab`) through the `GitHub Copilot` connector/tool consistently returned `404 Not Found`, and the repository contents could not be retrieved.

The same account could access the `AI_GUIDE` repository normally, confirming the problem was specific to `Instruction4Lab`.

## Investigation

The following were checked, and none revealed an obvious misconfiguration:

1. The `get_me` tool confirmed the authenticated GitHub connector account was indeed `YoshiyukiHatta` (the repository owner).
2. On the GitHub side, under `Settings → Applications → Installed GitHub Apps`, a "Claude" GitHub App was installed with `Permissions: Read/Write` and `Repository access: All repositories` (i.e., access to private repos should have been granted).
3. Disconnecting and reconnecting the connector did not surface a consent screen asking for repository access / private repository permission at all.
4. `Installed GitHub Apps` only listed "ChatGPT Codex Connector" and "Claude" — no app named "GitHub Copilot" (the name of the tool actually being used) was present.
5. `Authorized OAuth Apps` was also checked: only Git Credential Manager, GitHub, GitHub Android, GitHub CLI, GitHub Desktop, and Visual Studio Code were listed — nothing corresponding to Claude/GitHub Copilot.
6. Confirmed the Claude usage was under a personal account, not a Team/Enterprise administered account.

## Conclusion / Cause

The root cause has not been determined. Confirmed facts and inferences drawn from them are kept separate below.

**Confirmed facts**:

- Nothing in the user's personal GitHub account settings (Installed GitHub Apps, Authorized OAuth Apps) corresponds to the "GitHub Copilot" connector actually used for access.
- The "Claude" GitHub App shown in settings has `All repositories` permission, yet the 404 persists regardless.

**Inference (unverified)**:

- The "GitHub Copilot" tool actually used by Claude may go through a different authorization path than the "Claude" App visible in the user's personal GitHub settings — possibly an Anthropic-side organization/workspace-level custom connector.
- If so, no amount of reviewing or reconfiguring permissions on the personal GitHub account side may resolve it.

Both points above are unverified inferences that depend on Anthropic's internal implementation, and cannot be confirmed from this repository's records alone.

## Workaround

- Share the repository content directly in the chat via copy-and-paste.
- Use Claude Code (a repository-attached session like this one). Within what was verified here, Claude Code accessed the same private repository (`Instruction4Lab`) without issue.

## Related

- The `CLAUDE.md` change history in `Instruction4Lab` shows the GitHub integration method evolving from a PAT-based approach (2026-08-04) → PAT prohibited for Claude (2026-08-11) → consolidated into this repository (`AI_GUIDE`).
- Method A in this repository's `CLAUDE.md` ("Claude's integration method" section — the official GitHub remote MCP connector for claude.ai chat) may conflict with what this incident observed. Readers should not take it at face value and should keep in mind it may not work for private repositories.
