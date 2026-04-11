---
name: reedy
description: Activated whenever the user's message contains `/reedy`. When `/reedy` appears, Claude MUST fully read the skill instructions below before doing anything — do not assume you know what to do from this description alone, the exact rules are in the skill body and must be followed precisely. Do not answer normally first, do not add preamble, do not explain what you are doing. Strips markdown and citations from Claude responses and outputs clean prose inline, ready to select and speed-read with the Reedy browser extension. Use `/reedy` to clean the last response, or `/reedy [prompt]` to get a fresh answer in clean prose.
---

When the user's message contains `/reedy`, execute these instructions immediately. Do not greet, explain, or respond normally first.

If the message is just `/reedy`, find the most recent AI response in the conversation that contains real content (skip any reedy-formatted outputs or /reedy messages). Rewrite that content as clean prose.

If the message is `/reedy [prompt]`, answer the prompt fully. Search the web silently if needed.

RULES — EVERY SINGLE ONE IS MANDATORY. VIOLATING ANY RULE IS A FAILURE.

RULE 1 — NO MARKDOWN: No bullets, dashes, headers, bold, italics, or code blocks. Plain sentences only.

RULE 2 — NO CITATIONS: No source labels, bracketed references, or link text of any kind. Write as if from memory. If you searched the web, do not let a single citation tag appear in your output.

RULE 3 — NO SHORTENING: Preserve full detail and length. Do not summarize.

RULE 4 — ONE UNBROKEN BLOB: There must be ZERO blank lines in your output. None. Every paragraph runs directly into the next separated by a single space. The entire response must be selectable in one triple-click. If there is a blank line anywhere, you have failed this rule.

RULE 5 — INLINE ONLY: Output directly in the chat. Not as an artifact. Not as a file.

RULE 6 — END WITH THIS EXACT LINE AND NOTHING AFTER IT:

— Select the text above and press Alt+S to open in [Reedy](https://chromewebstore.google.com/detail/speed-reading/ihbdojmggkmjbhfflnchljfkgdhokffj)
