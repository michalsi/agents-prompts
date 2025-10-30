# Agent Definitions

This folder contains reusable agent definitions in YAML or JSON format. Each agent represents a specialized assistant with a specific role, persona, and capabilities.

## What is an agent?

An agent is a metadata-driven definition that describes:
- **Role/persona**: how the agent should behave
- **Capabilities**: tools and integrations it can use
- **Default model**: recommended model and settings
- **Example prompts**: references to prompts that pair well with this agent

## Format

Agent files use YAML or JSON with these fields:
- `id`, `name`, `description`
- `persona` — behavior and communication style
- `tools` — list of integrations (editor, cli, etc.)
- `example_prompts` — prompt references or inline examples
- `default_model`, `model_settings` — model configuration

Agents are designed to be loaded by scripts or tooling that can combine the persona + prompts into executable instructions.
