# Claude & Claude Code Prompting Templates

## Core Pattern
Claude responds best to direct, structured prompts with clear role definition and constraints.

### System Prompt Template
```
You are a [ROLE] with expertise in [DOMAIN].

## Context
[Background information]

## Task
[Specific request]

## Constraints
- [Constraint 1]
- [Constraint 2]

## Output Format
[Expected structure]
```

### Claude Code Specific
- Use CLAUDE.md for persistent instructions
- Leverage agents for complex multi-step tasks
- Provide file paths and code context explicitly
- Be direct: Claude prefers clear instructions over hints

### Key Principles
- Place critical constraints at the beginning
- Use markdown headers for structure
- Be explicit about output format
- Context first, task last
