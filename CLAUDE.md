# Claude Skills Configuration

This repository contains skills for Claude Code and other AI agents.

## Skills

Skills are located in the `skills/` directory. Each skill is a folder containing a `SKILL.md` file with YAML frontmatter and instructions.

## Installation

To use these skills with Claude Code, install them according to the Claude Code documentation.

## Development

When developing new skills:
1. Create a new folder in `skills/` with your skill name
2. Create `SKILL.md` following the [Agent Skills specification](https://agentskills.io/specification)
3. Add YAML frontmatter with required fields: `name` and `description`
4. Provide clear instructions that agents can follow
5. Keep SKILL.md under 500 lines (use `references/` for detailed docs)

See [AGENTS.md](AGENTS.md) for complete development guidelines and templates.
