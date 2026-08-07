# GEMINI.md

*[日本語版はこちら / Japanese version](GEMINI.md)*

Gemini CLI refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Gemini CLI must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with Gemini

Achieving an "always-on" connection requires a mechanism that does not rely on manual per-conversation actions. The setup location depends on the context in which you are using Gemini (Gemini / Gemini CLI), so each is described separately.

### Method A: For Gemini (gemini.google.com)

Writing a sentence instructing Gemini to reference this repository under **Settings & help → Personal Intelligence → "Instructions for Gemini"** applies it automatically to every new conversation (this feature was previously called "Saved info," so the label may differ depending on your UI version).

Example:

> When working on laboratory-related tasks (writing papers/reports, coding, preparing materials, etc.), treat the contents of the `<your-github-username>/AI_GUIDE` repository (especially GEMINI.md and docs/rules.md) as the laboratory's instruction document.

**Important limitation: as of now, Gemini (gemini.google.com / the app) has no official connector or extension for connecting a GitHub repository.** Google's official list of connectable services (Google Photos, YouTube, various Google Workspace apps, Google Search-related services, and Contacts) does not include GitHub. This means that even with the "Instructions for Gemini" set up above, Gemini itself cannot directly fetch the latest contents of the repository.

If you want Gemini to reference the repository's content on an ad-hoc basis, pasting the content of the relevant file directly into the chat is an alternative. Note that this requires pasting the content again in every conversation.

### Method B: Have Gemini CLI load it automatically (the most reliable option for an always-on connection)

You can also place a `GEMINI.md` file in each individual project, but setting up your **global configuration file** to load this repository is more reliable, since it is then loaded automatically no matter which project you are working in.

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Add a single line to your global configuration file, `~/.gemini/GEMINI.md` (on Windows, `C:\Users\<your-username>\.gemini\GEMINI.md`), using the `@` import syntax to reference the cloned repository's `AGENTS.md`. Create the file if it does not already exist (this import syntax only supports `.md` files).

   ```
   @<absolute-path-to-the-cloned-repository>/AGENTS.md
   ```

3. Gemini CLI automatically loads the global `GEMINI.md` every session and expands the file referenced by `@` into context, so the contents of this repository are loaded every time without any explicit action, regardless of which project you are working in. You can check what was actually loaded with the `/memory show` command.
4. To update the contents from this repository, simply run `git pull`, and the latest version will be reflected starting with your next session (within an existing session, you can reload with `/memory reload`).

If an always-on connection is the goal, Method B is the most reliable. Because Gemini itself cannot directly reference the repository, Method A is only a supplementary way to convey that "there is something it should refer to."
