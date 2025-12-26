# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Coggle** is a Claude Code plugin for prompt enhancement that transforms vague AI prompts into precise, actionable instructions. It provides a local, extensible toolset using Claude Code's agent/skill/command architecture.

## Architecture

```
.claude/
├── agents/
│   └── prompt-expander.md    # Expands prompts with platform detection
├── commands/
│   └── coggle.md             # /coggle - Main entry point
└── skills/
    └── prompt-expander/
        ├── SKILL.md          # PRECISE methodology + platform adaptation
        └── templates/        # Platform-specific prompt patterns
            ├── README.md
            ├── claude.md
            ├── codex.md
            ├── gemini.md
            ├── image-gen.md
            └── video-gen.md
```

## Core Concepts

> **Single Source of Truth**: Skills contain full methodology. Agents are thin orchestrators that invoke skills. Tables below are quick reference only.

### PRECISE Framework

Quick reference for the expansion methodology (full details in `.claude/skills/prompt-expander/SKILL.md`):

| Element | Description | Example |
|---------|-------------|---------|
| **P**ersona | Define AI role/expertise | "Act as a senior marketing strategist..." |
| **R**equirements | Specify deliverables | "Provide 3 strategies with ROI estimates" |
| **E**xamples | Include references | "Like this example: [sample]" |
| **C**ontext | Add background | "For a B2B SaaS startup targeting..." |
| **I**nstructions | Numbered steps | "1. Analyze market 2. Identify gaps 3. Recommend approach" |
| **S**pecifications | Format requirements | "Output as markdown table with headers" |
| **E**valuation | Success criteria | "Success = actionable within 24 hours" |

## Quick Start

```bash
/coggle [your prompt]                    # Expand for any platform
/coggle [prompt] for [platform]          # Expand for specific platform
```

### Supported Platforms
| Platform | Examples |
|----------|----------|
| Claude/Claude Code | System prompts, agent instructions |
| OpenAI/GPT/Codex | ChatGPT prompts, code generation |
| Google Gemini | Multimodal prompts, reasoning tasks |
| Image Gen | Midjourney, DALL-E, Nano Banana Pro |
| Video Gen | Sora, Runway, Kling |

### After Expansion
Interactive options:
- **Run** - Execute the prompt immediately
- **Save** - Save to `.prompts/[name].md`
- **Refine** - Iterate with feedback

## Development Guidelines

When extending this plugin:

### Adding Platform Templates
Add to `.claude/skills/prompt-expander/templates/[platform].md`:
1. Define platform characteristics (style, constraints, strengths)
2. Add adaptation guidelines for PRECISE elements
3. Include example prompts for that platform
4. Update platform detection in SKILL.md

### Adding New Commands
Create in `.claude/commands/` following pattern:
```markdown
# /command-name - Brief Description

[What it does]

## Usage
[Syntax and examples]

## Behavior
[Step-by-step execution]

## Output
[Expected output format]
```

### Extending the Agent

The prompt-expander agent should remain a thin orchestrator. When adding features:
1. Add methodology to `.claude/skills/prompt-expander/SKILL.md`
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

When expanding prompts, watch for and fix:

| Anti-Pattern | Example | Fix |
|--------------|---------|-----|
| Vague verbs | "help", "something", "stuff" | Specific actions |
| Missing audience | No target reader defined | Add audience context |
| Implicit assumptions | Unstated requirements | Make explicit |
| Wall of text | No structure | Add sections/steps |
| Conflicting instructions | Contradictory asks | Resolve conflicts |
| Scope creep | Too many tasks | Split into focused prompts |
| Missing format | No output spec | Define structure |
| Role ambiguity | Unclear AI persona | Add specific role |

## File Locations

| Type | Location | Pattern |
|------|----------|---------|
| Agent | `.claude/agents/` | `prompt-expander.md` |
| Command | `.claude/commands/` | `coggle.md` |
| Skill | `.claude/skills/prompt-expander/` | `SKILL.md` |
| Templates | `.claude/skills/prompt-expander/templates/` | `[platform].md` |
| Saved Prompts | `.prompts/` | `[name].md` |
| Project docs | Root | `CLAUDE.md` |
