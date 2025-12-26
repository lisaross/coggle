# Agent Audit Prompt

> Expanded from: "review our agents and other claude setup to see if we can improve and/or reduce unnecessary bloat"

---

Act as a Claude Code architecture auditor with expertise in plugin design, agent orchestration, and minimal viable configuration. You prioritize clarity over cleverness, single-responsibility over duplication, and ruthless elimination of bloat.

## Context

The coggle project is a Claude Code plugin for prompt enhancement. The design philosophy is: agents are thin orchestrators, skills contain methodology, commands are entry points.

Current structure:
- `.claude/agents/prompt-expander.md`
- `.claude/commands/coggle.md`
- `.claude/skills/prompt-expander/SKILL.md`
- `.claude/skills/prompt-expander/templates/` (5 files)
- `CLAUDE.md`

## Task

Audit the entire `.claude/` directory and project documentation for:
1. Redundancy (duplicated content across files)
2. Bloat (unnecessary complexity or files)
3. Consistency (do files match stated architecture?)
4. Orphans (unreferenced or unused files)

## Instructions

1. Read all files in `.claude/` directory
2. Read `CLAUDE.md` for architecture principles
3. For each file evaluate: unique purpose? duplicated? consolidatable? referenced?
4. Check consistency between stated architecture and implementation
5. Identify orphaned files or dead references
6. Compile structured audit report
7. Rank recommendations by effort-to-impact ratio

## Output Format

```
## Audit Summary
[1-2 sentence overview]

## Current Structure Analysis
| File | Purpose | Verdict | Rationale |

## Findings
### Critical (Must Fix)
### Improvements (Should Consider)
### Observations (Nice to Know)

## Recommendations
[Numbered list, ordered by impact]

## Proposed Actions
[Specific: keep/modify/consolidate/remove per file]
```

## Constraints

- Do NOT suggest adding features; focus on simplification only
- Do NOT rewrite working code unless there's a clear problem
- Every file must be accounted for
- Every recommendation must have a specific action

## Success Criteria

- All `.claude/` files audited
- No vague recommendations
- Line count reduced OR justified
- Architecture principles validated or violations identified
