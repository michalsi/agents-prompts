<!--
Template examples for reusable prompts. Copy and adapt per prompt.
Fields: title, purpose, model, tags, prompt, examples
-->

## Prompt: Summarize for a non-technical manager

- Purpose: Produce a short (2-3 sentence) non-technical summary of a technical change or PR.
- Model: GPT-5 mini (recommended)
- Tags: [summary, non-technical, PR]

Prompt:
"""
You are a concise communicator. Given the following technical change, write a 2-3 sentence summary for a non-technical manager. Keep it high-level, focus on impact and risk, avoid implementation details.

Change:
{{CHANGE_TEXT}}

Output:
1-2 short sentences.
"""

Example
- Input: "Refactored the auth module to use JWT tokens; replaced session store; added tests"
- Output: "Updated authentication to use stateless JWT tokens which simplifies scaling and reduces session store overhead. Minor risk: ensure token rotation is configured; tests were added to cover core flows."

---

## Prompt: Extract TODOs from code comment

- Purpose: Find all TODO comments and return a JSON list with file, line, and brief description.
- Model: GPT-5 mini
- Tags: [code, TODO, extraction]

Prompt body:
"""
Scan the following code and list every TODO comment as JSON with fields: file, line_number, text.

Code:
{{CODE_SNIPPET}}

Output: a JSON array.
"""
