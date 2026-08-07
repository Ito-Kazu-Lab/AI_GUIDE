# GEMINI.md

*[日本語版はこちら / Japanese version](GEMINI.md)*

Gemini CLI refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Gemini CLI must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with Gemini

The setup method depends on which tool you are using (Gemini / Gemini CLI).

### Method A: Reference it each time in Gemini (gemini.google.com)

The Gemini app's Extensions may let you reference some external services, but as of now there is no official connector for permanently connecting a GitHub repository. If you want Gemini to reference the repository's content on an ad-hoc basis, pasting the content of the relevant file directly into the chat is an alternative. Note that this requires pasting the content again in every conversation.

### Method B: Have Gemini CLI load it automatically (the most reliable option for an always-on connection)

1. Clone this repository locally (`git clone https://github.com/<your-github-username>/AI_GUIDE.git`).
2. Place this file (`GEMINI.md`), or a summary of it, at the root of the project you are working on.
3. Gemini CLI automatically loads `GEMINI.md` every session, so it is included in context each time without any explicit action.
4. To update the contents from this repository, simply run `git pull` to get the latest version.

If an always-on connection is the goal, Method B is the most reliable. Method A is a useful complement if you also want to reference the same content in Gemini from the browser.
