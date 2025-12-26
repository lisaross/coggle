# Claude Code Plugin Audit: Optimization & Bloat Reduction

> **Original prompt:** "review our agents and other claude setup to see if we can improve and/or reduce unnecessary bloat"

---

## Persona

You are a **Claude Code Architecture Specialist** with expertise in:

- Agent/skill/command design patterns for Claude Code plugins
- DRY principles and minimal configuration architecture
- Performance optimization for AI assistant tooling
- Documentation clarity and maintainability

## Requirements

Deliver these specific outputs:

1. **Inventory Report** - Complete catalog of all Claude Code components:
   - Agents: List with purpose, dependencies, usage frequency
   - Skills: List with methodology coverage, file sizes
   - Commands: List with trigger patterns, delegation targets
   - Cross-references: What invokes what

2. **Bloat Analysis** - Identify redundancies:
   - Duplicate functionality across components
   - Overly verbose documentation that could be condensed
   - Unused or rarely-triggered components
   - Circular or unnecessary dependencies

3. **Optimization Recommendations** - Prioritized list:
   - Components to merge (with rationale)
   - Components to remove (with impact assessment)
   - Documentation to condense (with before/after token estimates)
   - Structure improvements (with implementation steps)

4. **Implementation Plan** - If changes approved:
   - Ordered list of changes with git commit strategy
   - Rollback plan if issues arise
   - Testing approach to verify no functionality lost

## Examples

**Good Pattern (minimal orchestrator):**

```markdown
# Agent
Invoke skill → Get result → Return to user
```

**Bloat Pattern (duplicated logic):**

```markdown
# Agent
[Repeats entire methodology that exists in skill]
[Adds platform-specific logic that belongs in templates]
```

**Good Pattern (single source of truth):**

- Skill contains full methodology
- Templates contain platform specifics
- Agent is thin wrapper

**Bloat Pattern (scattered truth):**

- Same instructions in agent, skill, AND command
- Inconsistent versions across files

## Context

**Project:** Coggle - Claude Code plugin for prompt enhancement

**Current Structure:**

```yaml
.claude/
├── agents/
│   └── prompt-expander.md    # Main agent
├── commands/
│   └── coggle.md             # /coggle entry point
└── skills/
    └── prompt-expander/
        ├── SKILL.md          # PRECISE methodology
        └── templates/        # Platform patterns (6 files)
```

**Guiding Principles:**

- Skills = single source of truth for methodology
- Agents = thin orchestrators (invoke skill, handle interaction)
- Commands = entry points that delegate to agents
- Templates = platform-specific adaptations

**Known Concerns:**

- Is the agent truly thin or does it duplicate skill content?
- Are all 6 platform templates necessary or used?
- Is the command properly delegating or over-specifying?
- Is documentation appropriately sized for token efficiency?

## Instructions

Execute in this order:

1. **Read all Claude Code configuration files:**
   - `.claude/agents/prompt-expander.md`
   - `.claude/commands/coggle.md`
   - `.claude/skills/prompt-expander/SKILL.md`
   - All files in `.claude/skills/prompt-expander/templates/`
   - `CLAUDE.md` (project instructions)

2. **Analyze each component:**
   - What is its stated purpose?
   - What does it actually do?
   - How many tokens/lines is it?
   - What does it depend on?
   - What depends on it?

3. **Identify redundancies:**
   - Text repeated across multiple files
   - Logic that exists in multiple places
   - Documentation that restates upstream docs
   - Examples that duplicate rather than extend

4. **Assess necessity:**
   - Is each platform template actually used/needed?
   - Could templates be consolidated?
   - Is the agent adding value beyond skill invocation?
   - Is the command adding value beyond agent delegation?

5. **Propose changes:**
   - For each identified issue, propose specific fix
   - Estimate token savings where applicable
   - Note any functionality that might be lost
   - Prioritize by impact/effort ratio

6. **Create implementation checklist:**
   - Ordered steps to apply changes
   - Commit strategy (one commit per logical change)
   - Verification steps after each change

## Specifications

**Output Format:**

```markdown
## Audit Summary
[2-3 sentence executive summary]

## Component Inventory
| Component | Type | Lines | Tokens (est) | Dependencies | Status |
|-----------|------|-------|--------------|--------------|--------|
| ... | ... | ... | ... | ... | ✅ Keep / ⚠️ Review / ❌ Remove |

## Redundancy Findings
### Finding 1: [Title]
- **Location:** [files affected]
- **Issue:** [description]
- **Evidence:** [quotes/diffs]
- **Recommendation:** [action]
- **Token Savings:** [estimate]

## Optimization Recommendations
### Priority 1 (High Impact, Low Effort)
1. [Recommendation with rationale]

### Priority 2 (Medium Impact)
1. [Recommendation with rationale]

### Priority 3 (Low Priority)
1. [Recommendation with rationale]

## Implementation Plan
- [ ] Step 1: [action] → commit: "type(scope): message"
- [ ] Step 2: [action] → commit: "type(scope): message"
...

## Verification Checklist
- [ ] /coggle still works for basic prompt expansion
- [ ] Platform detection still functions
- [ ] Save/Run/Refine options still work
- [ ] No orphaned files or broken references
```

## Evaluation

**Success Criteria:**

- [ ] All components catalogued with accurate metrics
- [ ] At least 3 actionable redundancy findings identified (if they exist)
- [ ] Recommendations are specific (not vague suggestions)
- [ ] Token/line count savings estimated where applicable
- [ ] No false positives (flagging necessary content as bloat)
- [ ] Implementation plan is executable without ambiguity
- [ ] Core functionality preserved after any changes

**Quality Gates:**

- Audit identifies actual issues OR confirms setup is already optimal
- Recommendations have clear rationale, not just "could be shorter"
- Trade-offs acknowledged (e.g., "removes X but loses Y capability")
