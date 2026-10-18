# Free AI review bridge for EA FC 26

**Status:** Prepared, but not connected to Gemini until the owner creates a free Gemini API key and securely adds it as a GitHub Actions secret. No agent is currently running.

## What it does
When the repository owner comments `/gemini-review` on [issue #1](https://github.com/judedevilliers/jarvis-secure/issues/1), GitHub Actions sends *public issue text only* to Gemini 2.5 Flash and posts Gemini's response as a new issue comment. ChatGPT can then review the reply through its connected GitHub integration. This creates an asynchronous exchange of findings, not direct model-to-model control.

## One-time setup
1. Visit https://aistudio.google.com/apikey and create a key for an **unbilled Gemini API free-tier project**, if available for your account and country. Do not enable billing. Review Google's Free Tier usage limits.
2. In the GitHub repository visit **Settings → Secrets and variables → Actions → New repository secret**.
3. Name it exactly `GEMINI_API_KEY` and paste the key there. **Never put a key in a GitHub issue, chat, repository file, or screenshot.**
4. In [issue #1](https://github.com/judedevilliers/jarvis-secure/issues/1), add an issue comment: `/gemini-review Compare the apparently clean local saves with the separate post-drop attribute wipe evidence. Explain what we need to test next.`

## Security and limitations
- Public repository and public issue. **Never add decrypted PS4 saves, account details, keys, protected files, or any sensitive material.** The bridge only transmits existing *public issue description* and the owner command to Google.
- It does not use Cursor on the Mac, control Claude, perform local file edits, or certify fixes.
- This is a Gemini free-tier integration only. Claude's API typically requires paid credits, so Claude is deliberately not wired in.
- GitHub Actions on standard public repository runners are generally free, subject to GitHub policies. The Gemini provider can apply quotas; only use an unbilled/free-tier API project.
- The owner must trigger each review with `/gemini-review`; no recurring AI usage is scheduled.
- To stop it, remove the secret, delete this workflow, or stop invoking the command.
