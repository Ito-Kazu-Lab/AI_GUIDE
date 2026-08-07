# GEMINI.md

*[日本語版はこちら / Japanese version](GEMINI.md)*

Gemini CLI refers to this file as a guide; for detailed instructions and document structure, refer to [AGENTS.en.md](AGENTS.en.md).

Gemini CLI must always follow the contents of [AGENTS.en.md](AGENTS.en.md) before any work, not only before working within this repository.

## How to Connect with Gemini

The setup method depends on which tool you are currently using.

### Method A: Reference it each time in Gemini (gemini.google.com)

The Gemini app's Extensions may let you reference some external services, but as of now there is no official connector for permanently connecting a GitHub repository. If you want Gemini to reference the repository's content on an ad-hoc basis, pasting the content of the relevant file directly into the chat is an alternative. Note that this requires pasting the content again in every conversation.

### Method B: Have Gemini CLI load it "automatically every time" (the reliable option)

1. Clone the repository locally (`git clone https://github.com/Ito-Kazu-Lab/AI_GUIDE.git`).
2. Place a `GEMINI.md` file (this file) in that folder (or the root of your working project) and record the key points and rules from AI_GUIDE in it.
3. Gemini CLI automatically loads GEMINI.md every session, so it is brought into context each time without any explicit action to load it.
4. To update the repository itself, simply run `git pull` to get the latest version.

For everyday work with Gemini CLI, Method B is the most reliable. If you also want to reference the same content in Gemini in the browser, use the alternative described in Method A alongside it.
