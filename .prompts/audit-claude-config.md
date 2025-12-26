# Audit Claude Config

**Platform:** Claude Code
**Created:** 2025-12-26

---

**Persona:** Act as a Claude Code plugin architect and configuration auditor with expertise in agent/skill/command design patterns, DRY principles, and lean software architecture.

**Context:** You are auditing the Coggle project - a Claude Code plugin for prompt enhancement located at `/Users/focus/Developer/Projects/coggle`. The project follows a specific architecture pattern:
- **Agents** (`.claude/agents/`) - Thin orchestrators that delegate to skills
- **Skills** (`.claude/skills/`) - Reusable knowledge modules with full methodology
- **Commands** (`.claude/commands/`) - User-invocable slash commands

The project also inherits configuration from:
- Global user CLAUDE.md at `~/.claude/CLAUDE.md`
- Parent project CLAUDE.md at `/Users/focus/Developer/Projects/.claude/CLAUDE.md`

**Instructions:** Complete the following audit steps:

1. **Inventory all configuration files:**
   - List all agents in `.claude/agents/`
   - List all skills in `.claude/skills/`
   - List all commands in `.claude/commands/`
   - Note the root `CLAUDE.md` project documentation

2. **Analyze for redundancy:**
   - Check if any agent duplicates logic that exists in a skill
   - Check if any command duplicates logic from another command or skill
   - Identify any copy-pasted content across files
   - Look for similar functionality that could be consolidated

3. **Evaluate agent architecture:**
   - Verify each agent follows the "thin orchestrator" pattern
   - Confirm agents delegate to skills rather than containing methodology
   - Check if any agents could be merged or eliminated

4. **Assess skill coverage:**
   - Identify any skills that are never referenced
   - Check for overlapping skill responsibilities
   - Evaluate if skill boundaries are clear and logical

5. **Review command mappings:**
   - Verify each command maps to appropriate agent/skill
   - Check for orphaned commands (no corresponding agent)
   - Identify redundant commands that could be consolidated

6. **Measure documentation bloat:**
   - Check if CLAUDE.md duplicates skill content unnecessarily
   - Evaluate if documentation is DRY (single source of truth)
   - Identify any verbose sections that could be condensed

**Requirements:**
- Provide a structured audit report with findings organized by category
- For each issue found, specify: Location, Issue Type, Severity (High/Medium/Low), Recommendation
- Include specific file paths for all references
- Estimate token savings for recommended consolidations
- Prioritize recommendations by impact (most valuable changes first)

**Specifications:**
- Format: Markdown with clear section headers
- Structure:
  1. Executive Summary (3-5 bullet findings)
  2. Detailed Findings Table
  3. Prioritized Recommendations
  4. Proposed File Changes (what to consolidate/remove)
- Include before/after examples for major changes

**Evaluation Criteria:**
- Success = Actionable consolidation plan that reduces file count and/or total token count by 15%+
- Preserve all functionality - no features removed
- Maintain clear architecture boundaries (agent vs skill vs command)
- Recommendations should be specific enough to implement immediately
