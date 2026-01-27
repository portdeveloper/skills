# Agent Development Guide

This document provides guidance for AI coding agents working with Monad Skills.

## Repository Structure

```
monad/skills/
├── .claude-plugin/        # Claude Code plugin configuration
├── skills/                # All skills (flat structure)
│   └── monad-development/
│       ├── SKILL.md       # Main skill instructions
│       ├── scripts/       # Helper scripts (optional)
│       ├── references/    # Detailed documentation (optional)
│       └── assets/        # Static resources (optional)
├── AGENTS.md             # This file
├── CLAUDE.md             # Project-level Claude instructions
├── CONTRIBUTING.md       # Contribution guidelines
├── LICENSE
└── README.md
```

## Skill Development Standards

### Naming Conventions

- **Skill names**: Use kebab-case (e.g., `monad-development`, `safe-deployment`)
- **File names**: Use UPPERCASE for markdown files (e.g., `SKILL.md`, `REFERENCE.md`)
- **Directory names**: Use lowercase (e.g., `scripts/`, `references/`, `assets/`)

### SKILL.md Structure

Each `SKILL.md` must follow the Agent Skills format specification:

#### Required Frontmatter

```yaml
---
name: skill-name
description: Clear description of what the skill does and when to use it (max 1024 chars)
---
```

#### Optional Frontmatter

```yaml
---
name: monad-development
description: Builds dapps on Monad blockchain...
license: MIT
compatibility: Requires foundry, node 18+, and internet access
metadata:
  author: monad-skills
  version: "1.0.0"
---
```

#### Body Content (< 500 lines recommended)

- **Use when**: Clear triggers for when agents should activate this skill
- **Quick Reference**: Common commands, defaults, and endpoints
- **Core Instructions**: Step-by-step procedures
- **Examples**: Real-world usage patterns
- **Technical Details**: Essential specifications

#### Progressive Disclosure

Follow this loading pattern:
1. **Metadata** (~100 tokens): name + description loaded at startup
2. **Instructions** (< 5000 tokens): Full SKILL.md loaded when activated
3. **Resources** (on-demand): Files in scripts/, references/, assets/

### Optional Directories

#### scripts/

Helper automation and executable code:
- Use bash scripts with proper shebangs (`#!/usr/bin/env bash`)
- Include error handling (`set -e`)
- Output JSON when appropriate for parsing
- Document dependencies clearly
- Keep scripts focused and single-purpose

Example:
```bash
#!/usr/bin/env bash
set -e

# Deploy Safe multisig to Monad
# Usage: ./deploy-safe.sh <OWNER1> <OWNER2> <OWNER3>
```

#### references/

Detailed documentation loaded on-demand:
- `REFERENCE.md` - Complete technical reference
- `SAFE_GUIDE.md` - Safe multisig detailed guide
- `API.md` - API endpoint documentation
- `TROUBLESHOOTING.md` - Common issues and solutions

Keep files under 500 lines for efficient context usage.

#### assets/

Static resources:
- `templates/` - Contract templates, config files
- `diagrams/` - Architecture diagrams
- `examples/` - Sample code and configurations

### Context Efficiency Principles

1. **Keep SKILL.md concise**: Under 500 lines when possible
2. **Move details to references**: Split lengthy documentation
3. **Prefer script execution**: Over inline code blocks
4. **Use relative paths**: Reference files from skill root
5. **Avoid deep nesting**: Keep references one level deep

### File References

Use relative paths from the skill root:

```markdown
See [the Safe guide](references/SAFE_GUIDE.md) for detailed setup.

Run the deployment script:
\`\`\`bash
./scripts/deploy-safe.sh
\`\`\`
```

### Skill Activation Triggers

Include clear triggers in the description and body:

```yaml
description: Builds dapps on Monad blockchain. Use when deploying contracts, setting up frontends with viem/wagmi, or verifying contracts on Monad testnet or mainnet.
```

In the body:
```markdown
## When to Use This Skill

- Deploying smart contracts to Monad
- Setting up Monad-compatible frontends
- Verifying contracts on Monad explorers
- Configuring Safe multisig wallets
```

## Creating New Skills

1. Create a new skill directory:
   ```bash
   mkdir -p skills/your-skill-name
   ```

2. Create `skills/your-skill-name/SKILL.md` with this structure:
   ```markdown
   ---
   name: your-skill-name
   description: Clear description of what this skill does and when to use it (max 1024 chars)
   license: MIT
   metadata:
     author: your-org
     version: "1.0.0"
   ---

   # Your Skill Name

   ## When to Use This Skill

   - Scenario 1
   - Scenario 2

   ## Quick Reference

   Key commands, defaults, and references

   ## Core Instructions

   Step-by-step procedures and guidelines

   ## Examples

   Real-world usage patterns

   ## Technical Details

   Essential specifications
   ```

   - Write clear, actionable instructions
   - Include examples and edge cases
   - Keep under 500 lines if possible

3. Add optional directories if needed:
   ```bash
   mkdir -p skills/your-skill-name/{scripts,references,assets}
   ```

4. Validate your skill:
   ```bash
   # Install skills-ref from https://github.com/agentskills/agentskills
   skills-ref validate ./skills/your-skill-name
   ```

## Testing Skills

When testing skills:
- Verify all file references work
- Test scripts with various inputs
- Check error handling and edge cases
- Ensure instructions are clear and complete
- Validate against Agent Skills specification

## Distribution

Skills can be distributed:
- As Git repositories (this approach)
- As individual skill directories
- As zip files for Claude Code/claude.ai
- Through package managers (future)

## Additional Resources

- [Agent Skills Specification](https://agentskills.io/specification)
- [Example Skills](https://github.com/anthropics/skills)
- [Vercel Agent Skills](https://github.com/vercel-labs/agent-skills)
- [Monad Documentation](https://docs.monad.xyz)
