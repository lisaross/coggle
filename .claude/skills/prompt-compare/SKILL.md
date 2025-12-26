---
name: prompt-compare
description: COMPARE two prompt versions side-by-side to understand differences, improvements, and recommend best approach. Use when user has multiple prompt versions, wants to understand what changed, or needs to choose between approaches. Triggers on "compare prompts", "which prompt is better", "what's different", "diff these prompts".
---

# Prompt Compare

Compare two versions of a prompt side-by-side to understand differences, improvements, and provide data-driven recommendations on which to use or how to combine them.

## Trigger Phrases

Users invoke this skill by saying:
- "compare prompts"
- "which prompt is better"
- "what's different"
- "diff these prompts"
- "prompt comparison"

## When to Use This Skill

Use this skill when:
- User has two versions of a prompt and wants to understand differences
- Wants to know which prompt version is better
- Needs to understand what changed between iterations
- Deciding between different prompt approaches
- Learning what makes one prompt more effective

## Core Principles

1. **Multi-Dimensional Comparison**: Evaluate across structure, elements, quality, and specific differences
2. **Data-Driven Recommendations**: Base recommendations on scoring and objective analysis
3. **Combination Insights**: Identify opportunities to combine best elements from both

## Workflow

### Step 1: Capture Both Prompts

**Actions:**
- Receive Prompt A and Prompt B from user
- Label them clearly (A/B or Original/Revised or V1/V2)
- Confirm which prompt came first if relevant

**What to expect:**
- User may provide two complete prompts
- Or one prompt and ask to compare with expanded/improved version
- May want comparison to understand improvements made

### Step 2: Structural Comparison

Analyze basic metrics:

**Metrics to calculate:**
- Length (estimated token count)
- Section count (how many distinct sections)
- Instruction count (numbered steps)
- Constraint count (explicit limitations)

**Output format:**
```markdown
### Structural Comparison

| Metric | Prompt A | Prompt B |
|--------|----------|----------|
| Length | ~X tokens | ~Y tokens |
| Sections | X | Y |
| Instructions | X steps | Y steps |
| Constraints | X defined | Y defined |
```

### Step 3: Element Comparison

Check for presence of key prompt elements:

**Elements to check:**
- Persona (AI role definition)
- Context (background information)
- Instructions (step-by-step guidance)
- Format specification
- Examples
- Constraints
- Success criteria

**Output format:**
```markdown
### Element Comparison

| Element | Prompt A | Prompt B |
|---------|----------|----------|
| Persona | Present/Missing | Present/Missing |
| Context | Present/Missing | Present/Missing |
| Instructions | X steps | Y steps |
| Format spec | Present/Missing | Present/Missing |
| Examples | X included | Y included |
| Constraints | X defined | Y defined |
```

### Step 4: Quality Scoring

Score both prompts using the 7-dimension framework from the `prompt-analyzer` skill:

| Dimension | What It Measures |
|-----------|------------------|
| Clarity | Is the intent unambiguous? |
| Specificity | Are requirements concrete? |
| Structure | Is there logical organization? |
| Context | Is background provided? |
| Actionability | Can AI start immediately? |
| Completeness | Are all elements present? |
| Efficiency | Is it concise? |

→ See `.claude/skills/prompt-analyzer/SKILL.md` for detailed scoring guidelines.

**Output format:**
```markdown
### Quality Scores

| Dimension | Prompt A | Prompt B | Winner |
|-----------|----------|----------|--------|
| Clarity | X/10 | Y/10 | A/B/Tie |
| Specificity | X/10 | Y/10 | A/B/Tie |
| Structure | X/10 | Y/10 | A/B/Tie |
| Context | X/10 | Y/10 | A/B/Tie |
| Actionability | X/10 | Y/10 | A/B/Tie |
| Completeness | X/10 | Y/10 | A/B/Tie |
| Efficiency | X/10 | Y/10 | A/B/Tie |

**Total: X/70 vs Y/70**
```

### Step 5: Identify Specific Differences

**Categorize differences:**

1. **Added in B (not in A)**
   - List new elements, sections, or requirements
   - Note impact of each addition

2. **Removed from A (not in B)**
   - List elements present in A but missing in B
   - Note potential impact of removal

3. **Modified Elements**
   - Highlight elements that changed between versions
   - Explain how they changed and why it matters

**Output format:**
```markdown
### Key Differences

#### Added in B (not in A)
- [Element 1] - [Why this matters]
- [Element 2] - [Why this matters]

#### Removed from A (not in B)
- [Element 1] - [Potential impact]

#### Modified Between A and B
- [Element]: Changed from [X] to [Y] - [Impact]
```

### Step 6: Generate Recommendation

**Decision Logic:**
- If B scores significantly higher (10+ points) → Recommend B
- If A scores higher → Recommend A with caution (understand why they're comparing)
- If scores are close (< 5 point difference) → Recommend combination approach

**Recommendation Types:**

**Type 1: Clear Winner**
```markdown
### Recommendation

**Use Prompt B**

Reasoning: Prompt B scores 58/70 vs Prompt A's 42/70. Key improvements:
- Added clear persona and role definition
- Structured instructions into 5 logical steps
- Included explicit format requirements
- Added success criteria

Prompt B is production-ready while A needs significant enhancement.
```

**Type 2: Combination Approach**
```markdown
### Recommendation

**Combine Both Prompts**

Take these elements:
- From A: [Specific element and why it's better]
- From B: [Specific element and why it's better]

Combined approach will score approximately X/70 by merging:
1. [Element from A]
2. [Element from B]
3. [Element from A or B]

[Provide combined version or outline]
```

**Type 3: Conditional Recommendation**
```markdown
### Recommendation

**Depends on Use Case**

- Use A if: [Specific conditions]
- Use B if: [Specific conditions]

For example:
- A is better for quick, informal requests
- B is better for complex, production use cases
```

### Step 7: Provide Complete Report

**Final output format:**

```markdown
## Prompt Comparison

### Prompt A
> [First 100 chars...]
**Length:** ~X tokens | **Score:** Y/70

### Prompt B
> [First 100 chars...]
**Length:** ~X tokens | **Score:** Y/70

---

[Structural Comparison Table]

[Element Comparison Table]

[Quality Scores Table]

### Key Differences

[Added/Removed/Modified sections]

### Recommendation
[Clear recommendation with reasoning]

### Next Steps
[Actionable next step for user]
```

## Use Cases

### Use Case 1: Version Evolution
**Scenario:** User improved their prompt and wants to see what changed
**Focus:** Highlight improvements, validate changes were positive

### Use Case 2: A/B Testing
**Scenario:** User has two different approaches and needs to pick one
**Focus:** Objective scoring to determine which is more effective

### Use Case 3: Learning
**Scenario:** User wants to understand what makes one prompt better
**Focus:** Educational comparison explaining principles behind differences

### Use Case 4: Optimization
**Scenario:** User wants to find the best combination of both prompts
**Focus:** Identify best elements from each and merge them

## Success Indicators

This skill is successful when:
- [ ] Both prompts captured and labeled clearly
- [ ] Structural comparison completed with metrics
- [ ] Element comparison shows what's present/missing
- [ ] Quality scores calculated for both (7 dimensions)
- [ ] Specific differences identified and categorized
- [ ] Clear recommendation provided with reasoning
- [ ] User understands which prompt to use or how to combine them

## Quality Checklist

Before marking complete, verify:
- [ ] Both prompts displayed with preview (first 100 chars)
- [ ] All comparison tables included (structural, element, quality)
- [ ] Differences categorized as Added/Removed/Modified
- [ ] Recommendation is clear and actionable
- [ ] Reasoning explains WHY one is better (not just that it scores higher)
- [ ] Next step provided for user

## Common Comparison Patterns

**Pattern 1: Expanded vs Original**
- Original is usually shorter, vaguer
- Expanded adds persona, structure, requirements
- Recommendation: Use expanded (higher scores across all dimensions)

**Pattern 2: Concise vs Detailed**
- Concise optimizes for efficiency
- Detailed optimizes for completeness
- Recommendation: Depends on use case (quick task vs complex project)

**Pattern 3: Different Approaches**
- Both prompts valid but take different angles
- May score similarly overall
- Recommendation: Combination or conditional (depends on context)

## Integration Points

**Works with:**
- `prompt-analyzer` - Use to generate quality scores for comparison
- `prompt-expander` - After comparison, expand the weaker prompt to match the stronger
- `prompt-formatter` - Format the recommended prompt for delivery

**Typical workflow:**
1. User provides two prompts
2. Use `prompt-compare` (this skill) to analyze differences
3. Use `prompt-analyzer` to score each dimension
4. If one needs improvement, use `prompt-expander`
5. Use `prompt-formatter` to deliver final result

---

*Prompt Compare skill | Created: 2025-12-26*
