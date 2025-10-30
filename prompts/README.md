# Prompts Library

This folder contains reusable prompts organized by category. Each prompt includes purpose, model recommendations, and examples.

## Structure

- `prompts/<category>/<name>.md` — individual prompts with examples and settings
- `prompts/templates/` — template examples showing the standard format

## Prompt format

Each prompt file includes:
1. **Title**: short descriptive name
2. **Purpose**: when and why to use this prompt
3. **Model**: recommended model and settings (temperature, max tokens)
4. **Prompt body**: the instruction with placeholders (e.g., `{{CODE}}`, `{{TASK}}`)
5. **Examples**: sample inputs and expected outputs

Prompts are designed to be copy-pasteable into editors, CLIs, or integrated via scripts.
