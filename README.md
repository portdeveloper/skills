# Monad Skills

A collection of AI agent skills for working with Monad blockchain projects.

## Overview

This repository contains skills that can be used with Claude Code, Cursor, and other AI agents to enhance development workflows for Monad blockchain applications.

Skills follow the [Agent Skills format specification](https://agentskills.io/specification) for compatibility across multiple AI development tools.

## Structure

```
monad/skills/
├── .claude-plugin/        # Claude Code plugin configuration
├── skills/                # All skills (flat structure)
│   └── monad-development/ # Individual skill folders
├── AGENTS.md             # Guide for AI agents working with this repo
├── CLAUDE.md             # Project-level Claude instructions
├── CONTRIBUTING.md       # Contribution guidelines
├── LICENSE               # License information
└── README.md             # This file
```

## Available Skills

### monad-development

Build dapps on Monad without friction. This skill provides:
- Smart contract deployment with Foundry and Hardhat
- Frontend setup with viem/wagmi
- Contract verification on Monad testnet/mainnet
- Safe multisig integration for secure deployments

## Installation

To use these skills with Claude Code or other compatible AI agents, install them according to the tool's documentation.

## Creating New Skills

To create a new skill:

1. Create a new directory: `mkdir skills/your-skill-name`
2. Create `skills/your-skill-name/SKILL.md` following the [Agent Skills specification](https://agentskills.io/specification)
3. Add YAML frontmatter with required fields: `name` and `description`
4. Write clear, actionable instructions for agents

Each skill must have:
- A unique name (lowercase, hyphens for spaces)
- A clear description of what it does and when to use it
- Specific instructions for agents to follow
- SKILL.md under 500 lines (move detailed content to `references/`)

For complete development guidelines, templates, and best practices, see [AGENTS.md](AGENTS.md).

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

See [LICENSE](LICENSE) for details.

## Additional Resources

- [Agent Skills Specification](https://agentskills.io/specification) - Official format specification
- [Agent Development Guide](AGENTS.md) - Guidelines for working with this repository
- [Monad Documentation](https://docs.monad.xyz) - Monad blockchain documentation
