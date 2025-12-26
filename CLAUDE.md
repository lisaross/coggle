# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Coggle** is a Claude Code marketplace plugin for prompt enhancement that transforms vague AI prompts into precise, actionable instructions. It provides a local, extensible toolset using Claude Code's agent/skill/command architecture.

## Architecture

```
coggle/
├── .claude-plugin/
│   └── plugin.json              # Plugin manifest
├── agents/
│   └── prompt-expander.md       # Expands prompts with platform detection
├── commands/
│   └── coggle.md                # /coggle - Main entry point
├── skills/
│   └── prompt-expander/
│       ├── SKILL.md             # PRECISE methodology + platform adaptation
│       └── templates/           # Platform-specific prompt patterns
│           ├── claude.md
│           ├── codex.md
│           ├── gemini.md
│           ├── image-gen.md
│           └── video-gen.md
├── README.md                    # Plugin documentation
└── CLAUDE.md                    # Development guidance (this file)
```

## Core Concepts

> **Single Source of Truth**: Skills contain full methodology. Agents are thin orchestrators that invoke skills. Tables below are quick reference only.

### PRECISE Framework

> **Full methodology**: See `skills/prompt-expander/SKILL.md` for complete PRECISE framework documentation.

Quick mnemonic: **P**ersona, **R**equirements, **E**xamples, **C**ontext, **I**nstructions, **S**pecifications, **E**valuation

## Quick Start

```bash
/coggle [your prompt]                    # Expand for any platform
/coggle [prompt] for [platform]          # Expand for specific platform
```

### Supported Platforms

> **Detection rules**: See `skills/prompt-expander/SKILL.md` for platform detection table.

Supports: Claude/Claude Code, OpenAI/GPT/Codex, Google Gemini, Image Gen (Midjourney, DALL-E), Video Gen (Sora, Runway, Kling)

### After Expansion
Interactive options:
- **Run** - Execute the prompt immediately
- **Save** - Save to `.prompts/[name].md`
- **Refine** - Iterate with feedback

## Development Guidelines

When extending this plugin:

### Adding Platform Templates
Add to `skills/prompt-expander/templates/[platform].md`:
1. Define platform characteristics (style, constraints, strengths)
2. Add adaptation guidelines for PRECISE elements
3. Include example prompts for that platform
4. Update platform detection in SKILL.md

### Adding New Commands
Create in `commands/` following pattern:
```markdown
---
description: Brief description
argument-hint: "[args]"
---

# /command-name - Brief Description

[What it does]

## Usage
[Syntax and examples]

## Execution
[Instructions for Claude]
```

### Extending the Agent

The prompt-expander agent should remain a thin orchestrator. When adding features:
1. Add methodology to `skills/prompt-expander/SKILL.md`
2. Add platform-specific patterns to template files
3. Keep agent logic minimal (detect platform, invoke skill, return result)

### Skill File Structure
Skills use YAML frontmatter for metadata:
```markdown
---
name: skill-name
description: VERB description with trigger phrases...
---

# Skill Name

[Full skill documentation]
```

## Anti-Patterns to Avoid

> **Full list**: See `skills/prompt-expander/SKILL.md` quality checklist.

Watch for: vague verbs, missing audience, implicit assumptions, wall of text, conflicting instructions, scope creep, missing format, role ambiguity.

## File Locations

| Type | Location | Pattern |
|------|----------|---------|
| Manifest | `.claude-plugin/` | `plugin.json` |
| Agent | `agents/` | `prompt-expander.md` |
| Command | `commands/` | `coggle.md` |
| Skill | `skills/prompt-expander/` | `SKILL.md` |
| Templates | `skills/prompt-expander/templates/` | `[platform].md` |
| Saved Prompts | `.prompts/` | `[name].md` |
| Documentation | Root | `README.md`, `CLAUDE.md` |

> **Note**: The `.prompts/` directory is auto-created when first saving a prompt via `/coggle`.

## Testing the Plugin

### Local Development
```bash
claude --plugin-dir /path/to/coggle
```

### Verify Components Load
1. Run `/coggle test prompt` - command should work
2. Check agents list - prompt-expander should appear
3. Verify skill triggers on "expand", "improve prompt", etc.
