## 🧭 Practical recommendation for your use-case

1. Create `.github/copilot-instructions.md` in your project root (or if you want profile-wide behaviour, use a user-instructions file as described).

2. Paste **only** your protocol (the Clarification Protocol snippet) in that file — e.g.:

   ```
   Before answering user requests, first list any clarifications/ambiguities in a numbered list.
   For each item, if multiple options exist show a), b), c). If one preferred choice, write “Proposal: …”. If no proposal available, write “(No proposal available)”.
   Do not provide reasoning or the main answer yet — only the list.
   The user will respond by index or sub-index (e.g., “1: a, 2: Accept, 3: Yes”).
   After user response, proceed with main answer according to their choices.
   ```

3. In your VS Code workspace/settings, ensure:

   ```json
   {
     "github.copilot.chat.codeGeneration.useInstructionFiles": true
   }
   ```

   and optionally, disable or ignore older `customUserInstructions` settings if present.

4. Optionally, for profile-wide or multi-repo use, you can place instruction files at user-level or define `chatMode.md` or `.instructions.md` files as per the docs. ([Visual Studio Code][2])

5. Test by starting a chat in Copilot Chat: ask a simple question, then check “References” (in the chat response UI) — you should see your `.github/copilot-instructions.md` listed as a reference. If it’s listed, you know it was attached to the prompt. ([GitHub Docs][1])

6. If you still see behaviour inconsistent with your instruction (the LLM ignoring or partially following your protocol), you may need to explicitly prepend the protocol in the chat prompt (just in case the system prompt overrides your instruction) or use a “chat mode” persona.

---

[1]: https://copilot-instructions.md/?utm_source=chatgpt.com "Adding custom instructions for GitHub Copilot - GitHub Docs"
[2]: https://code.visualstudio.com/docs/copilot/customization/custom-instructions?utm_source=chatgpt.com "Use custom instructions in VS Code"
[3]: https://github.com/dfinke/awesome-copilot-chatmodes?utm_source=chatgpt.com "GitHub - dfinke/awesome-copilot-chatmodes: Custom chatMode.md personas for GitHub Copilot — specialize your VS Code with AI assistants for testing, security, clean‑code refactoring, dashboards, prompt design, and more. Just drop in and select your mode."
[4]: https://www.reddit.com/r/github/comments/18bbk41?utm_source=chatgpt.com "Prompt hacking Github Copilot extension for Visual Studio Code"
[5]: https://www.reddit.com/r/GithubCopilot/comments/1j4yemi?utm_source=chatgpt.com "Agent option does not show up"
