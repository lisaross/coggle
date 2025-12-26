# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Coggle** is a Claude Code plugin for prompt enhancement that transforms vague AI prompts into precise, actionable instructions. It provides a local, extensible toolset using Claude Code's agent/skill/command architecture.

## Architecture

```
.claude/
├── agents/           # Thin orchestrators (invoke skills via Skill tool)
│   ├── prompt-expander.md    # Orchestrates prompt expansion
│   ├── prompt-analyzer.md    # Orchestrates prompt analysis
│   ├── prompt-library.md     # Prompt storage and retrieval
│   └── prompt-coach.md       # Interactive prompt engineering teacher
│
├── commands/         # User-invocable slash commands
│   ├── coggle.md             # /coggle - Unified prompt enhancement (expand/analyze/template/format/compare)
│   └── learn-prompting.md    # /learn-prompting - Interactive tutorials
│
└── skills/           # Reusable knowledge modules (directory-based)
    ├── prompt-expander/      # PRECISE expansion methodology
    │   └── SKILL.md
    ├── prompt-analyzer/      # 7-dimension quality scoring
    │   └── SKILL.md
    ├── prompt-templates/     # Template library (analysis/creation/technical/strategy)
    │   └── SKILL.md
    ├── prompt-formatter/     # Export formats (copy/markdown/JSON/slides/email/API)
    │   └── SKILL.md
    └── prompt-compare/       # Side-by-side prompt comparison
        └── SKILL.md
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

### 7-Dimension Quality Scoring

Quick reference for scoring (full details in `.claude/skills/prompt-analyzer/SKILL.md`):

| Dimension | What It Measures |
|-----------|------------------|
| Clarity | Is the intent unambiguous? |
| Specificity | Are requirements concrete? |
| Structure | Is there logical organization? |
| Context | Is background provided? |
| Actionability | Can AI start immediately? |
| Completeness | Are all elements present? |
| Efficiency | Is it concise? |

**Overall: X/70** with ratings:
- **Excellent** (60-70): Production ready
- **Good** (45-59): Minor tweaks helpful
- **Fair** (30-44): Significant improvements needed
- **Poor** (<30): Major rewrite recommended

## Quick Start Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `/coggle [prompt]` | Expand a vague prompt (default) | `/coggle Write me something about marketing` |
| `/coggle analyze [prompt]` | Score prompt quality | `/coggle analyze Help me with code` |
| `/coggle template [cat] [type]` | Get ready-to-use template | `/coggle template analysis market` |
| `/coggle format [fmt] [prompt]` | Export in specific format | `/coggle format json last` |
| `/coggle compare [A] vs [B]` | Compare two prompts | `/coggle compare "v1" vs "v2"` |
| `/learn-prompting [topic]` | Interactive tutorials | `/learn-prompting basics` |

After expanding, interactive options are presented:
- **Run** - Execute the prompt immediately
- **Save** - Save to `.prompts/[name].md`
- **Analyze** - Score quality first
- **Other** - Refine with custom input

## Export Formats

Expanded prompts can be exported as:

| Format | Use Case |
|--------|----------|
| `copy` | Plain text for pasting into ChatGPT/Claude |
| `markdown` | Formatted documentation with headers |
| `json` | Structured data for storage/APIs |
| `slides` | Presentation outline for teaching |
| `email` | Delegation request format |
| `system` | System prompt for custom GPTs/assistants |
| `api` | OpenAI/Anthropic API request body |

## Template Categories

| Category | Templates | Use For |
|----------|-----------|---------|
| **analysis** | Market, Code Review, Competitive, Risk | Evaluating, reviewing, assessing |
| **creation** | Blog, Email, Copy, Docs | Generating new content |
| **technical** | API Design, Schema, Architecture, Debug | Software development |
| **strategy** | Decision, Roadmap, OKR, Retrospective | Planning and decision-making |

## Agent Triggers

| Agent | Trigger Phrases | Specialty |
|-------|-----------------|-----------|
| prompt-expander | "expand", "improve prompt", "coggle" | Transform vague prompts |
| prompt-analyzer | "analyze", "score", "audit prompt" | Diagnose prompt issues |
| prompt-compare | "compare prompts", "which is better" | Side-by-side comparison |
| prompt-coach | "teach me", "how do I prompt" | Learn prompting skills |

All agents are thin orchestrators that delegate to corresponding skills.

## Development Guidelines

When extending this plugin:

### Adding New Templates
Add to `.claude/skills/prompt-templates/SKILL.md` following existing format:
```
### [Template Name] Template

[Template content with [PLACEHOLDERS]]

**Customization Guide:**
1. Replace [PLACEHOLDER1] with [guidance]
```

### Adding New Formats
Add to `.claude/skills/prompt-formatter/SKILL.md`:
1. Define format name and structure
2. Add transformation rules
3. Include usage guidance
4. Update Format Selection Guide table

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

### Adding New Agents

Agents should be thin orchestrators that delegate to skills. Create in `.claude/agents/`:

```markdown
# Agent: agent-name

[Description with trigger phrases and PROACTIVELY/SPECIALIST keywords]

## Tools Available

- Skill (invoke the corresponding skill)
- [Other tools as needed]

## Execution

1. Use Skill tool to invoke [skill-name] for methodology
2. Apply methodology to user input
3. Return result in skill's output format

The skill contains the full methodology, output format, and quality criteria.
```

**Key principle**: Don't duplicate skill content in agents. Agents orchestrate; skills contain knowledge.

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
| Agents | `.claude/agents/` | `[name].md` |
| Commands | `.claude/commands/` | `[command-name].md` |
| Skills | `.claude/skills/` | `[skill-name]/SKILL.md` |
| Integrations | `.claude/` | `INTEGRATIONS.md` |
| Project docs | Root | `CLAUDE.md` |
