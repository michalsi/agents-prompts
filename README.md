# Agents & Prompts Library (starter)

This repository is a small, opinionated scaffold to collect and reuse LLM prompts and agent definitions across projects and tools.

Focus for now
- Primary: VS Code + GitHub Copilot (including Copilot CLI workflows)
- Future: add adapters for other tools (Anthropic, Code Editor integrations, Cursor, etc.) — optional later.

Repository layout (minimal):

- `prompts/` — prompt library and templates (markdown + optional metadata)
- `agents/` — reusable agent definitions (YAML/JSON examples)
- `tools/vscode-copilot/` — examples and sample settings for VS Code + Copilot CLI
- `.github/` — repo-level Copilot instructions (existing)

Goals
- Keep structure small and extensible.
- Provide clear templates so prompts and agents are consistent.
- Allow you to paste prompts into VS Code/Copilot or load agent configs into simple tooling.

## Usage

**Browse and copy**: Find a prompt or agent definition that fits your need, copy it into your editor or CLI.

**Adapt templates**: Use the templates in `prompts/templates/` and `agents/templates/` as starting points for new prompts or agents.

**Integrate**: Reference prompts in VS Code snippets, Copilot CLI commands, or custom scripts. Agent definitions can be loaded by tooling that accepts YAML/JSON configs.
