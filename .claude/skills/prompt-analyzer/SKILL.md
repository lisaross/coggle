---
name: prompt-analyzer
description: ANALYZE prompts across 7 quality dimensions to identify weaknesses and improvement opportunities. Use when user wants to understand why prompt isn't working, needs diagnostic feedback, or wants to learn prompt engineering patterns. Triggers on "analyze prompt", "diagnose prompt", "why isn't this working", "prompt audit", "prompt review".
---

# Prompt Analyzer

Evaluate prompts across 7 quality dimensions to identify weaknesses, improvement opportunities, and provide diagnostic feedback. This skill performs comprehensive prompt audits using a scoring framework.

## Trigger Phrases

Users invoke this skill by saying:
- "analyze prompt"
- "diagnose prompt"
- "why isn't this working"
- "prompt audit"
- "prompt review"

## When to Use This Skill

Use this skill when:
- User wants to understand why their prompt isn't producing good results
- Needs diagnostic feedback on prompt quality
- Wants to learn prompt engineering patterns through analysis
- Needs objective scoring before/after prompt improvements

## Core Principles

1. **Multi-Dimensional Scoring**: Evaluate across 7 independent quality dimensions
2. **Actionable Feedback**: Every issue identified includes a specific fix recommendation
3. **Prioritization**: Focus on top 3 issues for maximum impact

## Workflow

### Step 1: Read Input Prompt

**Actions:**
- Capture the complete prompt to be analyzed
- Understand the user's intent and expected outcome
- Note any context about what's not working

**What to expect:**
- May be a failing prompt or one needing optimization
- User may provide context about issues encountered

### Step 2: Score Across 7 Dimensions

Evaluate the prompt on each dimension (1-10 scale):

#### 1. Clarity Score (1-10)
- Is the intent unambiguous?
- Would two different AIs interpret this the same way?
- Are technical terms defined?

#### 2. Specificity Score (1-10)
- Are requirements concrete and measurable?
- Is the scope well-defined?
- Are constraints explicit?

#### 3. Structure Score (1-10)
- Is there logical organization?
- Are steps/sections clearly delineated?
- Is the format specified?

#### 4. Context Score (1-10)
- Is background information provided?
- Is the audience defined?
- Is the purpose clear?

#### 5. Actionability Score (1-10)
- Can the AI immediately start working?
- Are all inputs provided?
- Is the task decomposed into steps?

#### 6. Completeness Score (1-10)
- Are all necessary elements present?
- Are edge cases addressed?
- Are examples or references included?

#### 7. Efficiency Score (1-10)
- Is the prompt free of redundancy?
- Is token usage optimized?
- Could it be more concise?

### Step 3: Identify Anti-Patterns

Flag these common issues when detected:

1. **Vague Verbs** - "help", "something", "stuff"
2. **Missing Audience** - No target reader/user defined
3. **Implicit Assumptions** - Unstated requirements
4. **Wall of Text** - No structure or breaks
5. **Conflicting Instructions** - Contradictory requirements
6. **Scope Creep** - Too many tasks in one prompt
7. **Missing Format** - No output specification
8. **Role Ambiguity** - Unclear AI persona

### Step 4: Generate Analysis Report

**Output Format:**

```markdown
## Prompt Analysis Report

**Input Prompt:**
> [Original prompt]

### Dimension Scores

| Dimension | Score | Issue |
|-----------|-------|-------|
| Clarity | X/10 | [Key issue or "Good"] |
| Specificity | X/10 | [Key issue or "Good"] |
| Structure | X/10 | [Key issue or "Good"] |
| Context | X/10 | [Key issue or "Good"] |
| Actionability | X/10 | [Key issue or "Good"] |
| Completeness | X/10 | [Key issue or "Good"] |
| Efficiency | X/10 | [Key issue or "Good"] |

**Overall Score: X/70 ([Rating])**
- 60-70: Excellent - Ready for production
- 45-59: Good - Minor improvements possible
- 30-44: Fair - Significant improvements needed
- Below 30: Poor - Major rewrite recommended

### Top 3 Issues

1. **[Issue Name]**
   - Problem: [Description]
   - Impact: [How this affects output]
   - Fix: [Specific recommendation]

2. **[Issue Name]**
   - Problem: [Description]
   - Impact: [How this affects output]
   - Fix: [Specific recommendation]

3. **[Issue Name]**
   - Problem: [Description]
   - Impact: [How this affects output]
   - Fix: [Specific recommendation]

### Quick Wins
- [Easy improvement 1]
- [Easy improvement 2]
- [Easy improvement 3]

### Recommended Next Step
[Single most impactful action to take]
```

### Step 5: Prioritize Recommendations

**Actions:**
- Identify the top 3 most impactful issues
- Provide specific fix for each
- Suggest 3 quick wins (easy improvements)
- Recommend single best next step

**Decision Points:**
- If score < 30 → Recommend complete rewrite using prompt-expander
- If score 30-44 → Focus on top 3 issues
- If score 45-59 → Apply quick wins
- If score 60+ → Provide minor polish suggestions

## Scoring Guidelines

**Clarity (Is it unambiguous?)**
- 9-10: Crystal clear, no room for misinterpretation
- 7-8: Mostly clear with minor ambiguities
- 5-6: Some vague areas that could confuse
- 3-4: Multiple unclear elements
- 1-2: Very vague or confusing

**Specificity (Is it concrete?)**
- 9-10: All requirements are measurable and explicit
- 7-8: Most requirements specific, few generalities
- 5-6: Mix of specific and vague requirements
- 3-4: Mostly general or abstract
- 1-2: No concrete requirements

**Structure (Is it organized?)**
- 9-10: Logical flow, clear sections, easy to scan
- 7-8: Good organization with minor issues
- 5-6: Some structure but could be clearer
- 3-4: Poorly organized or hard to follow
- 1-2: No structure, wall of text

**Context (Is background provided?)**
- 9-10: Complete context with audience, purpose, constraints
- 7-8: Good context, minor gaps
- 5-6: Some context but missing key elements
- 3-4: Minimal context provided
- 1-2: No context given

**Actionability (Can AI start immediately?)**
- 9-10: All inputs provided, task ready to execute
- 7-8: Mostly actionable, minor clarifications needed
- 5-6: Some steps unclear or inputs missing
- 3-4: Significant blockers to starting
- 1-2: Cannot begin without more information

**Completeness (Are all elements present?)**
- 9-10: Comprehensive with examples, edge cases, constraints
- 7-8: Most elements present
- 5-6: Missing several important elements
- 3-4: Many gaps in requirements
- 1-2: Bare minimum information

**Efficiency (Is it optimized?)**
- 9-10: Concise with no redundancy
- 7-8: Efficient with minor wordiness
- 5-6: Some unnecessary repetition
- 3-4: Significant redundancy
- 1-2: Very verbose or bloated

## Success Indicators

This skill is successful when:
- [ ] All 7 dimensions have been scored with justification
- [ ] Overall score calculated (out of 70)
- [ ] Top 3 issues identified with specific fixes
- [ ] Quick wins provided for easy improvements
- [ ] Clear next step recommendation given

## Quality Checklist

Before marking complete, verify:
- [ ] Each dimension score has a justification in the "Issue" column
- [ ] Overall rating (Excellent/Good/Fair/Poor) matches score range
- [ ] Top 3 issues are prioritized by impact
- [ ] Each issue includes Problem, Impact, and Fix
- [ ] Quick wins are actually quick (< 5 minutes each)
- [ ] Recommended next step is specific and actionable

## Integration Points

**Works with:**
- `prompt-expander` - After analysis, use to fix identified issues
- `prompt-compare` - Compare before/after versions to validate improvements
- `prompt-templates` - Suggest relevant templates based on gaps found

---

*Prompt Analyzer skill | Created: 2025-12-26*
