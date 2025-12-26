# /compare-prompts - Side-by-Side Prompt Comparison

Compare two prompt versions to understand differences and identify improvements.

## CRITICAL: Comparison Only

**This command COMPARES prompts. It does NOT execute them.**

- Input: Two prompts to compare
- Output: Detailed comparison report with recommendations

## Usage

```bash
/compare-prompts [prompt A] vs [prompt B]
/compare-prompts before: [original] after: [improved]
```

## Examples

```bash
/compare-prompts "Write about marketing" vs "Act as a marketing strategist and write a 500-word blog post about email best practices for startups"
/compare-prompts before: "Help me with code" after: "Review this Python function for security vulnerabilities and PEP 8 compliance"
```

## Execution

**Invoke the `prompt-compare` agent via Task tool:**

```yaml
Task:
  subagent_type: "general-purpose"
  description: "Compare prompts via prompt-compare agent"
  prompt: |
    Read and follow the agent specification at:
    .claude/agents/prompt-compare.md

    Then compare these prompts:
    $ARGUMENTS

    Use the Skill tool to invoke the prompt-compare skill for methodology.
```

The Task tool spawns a subagent that:

1. Reads the prompt-compare agent specification
2. Invokes the prompt-compare skill for methodology
3. Scores both prompts across 7 dimensions
4. Returns the comparison report

## Output

```markdown
## Prompt Comparison Report

### Prompt A
> [First 100 chars...]
**Length:** ~X tokens | **Score:** Y/70

### Prompt B
> [First 100 chars...]
**Length:** ~X tokens | **Score:** Y/70

---

### Structural Comparison

| Metric | Prompt A | Prompt B |
|--------|----------|----------|
| Length | ~X tokens | ~Y tokens |
| Sections | X | Y |
| Instructions | X steps | Y steps |
| Constraints | X defined | Y defined |

### Element Comparison

| Element | Prompt A | Prompt B |
|---------|----------|----------|
| Persona | Present/Missing | Present/Missing |
| Context | Present/Missing | Present/Missing |
| Instructions | X steps | Y steps |
| Format spec | Present/Missing | Present/Missing |

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

### Key Differences

#### Added in B (not in A)
- [Element 1] - [Why this matters]
- [Element 2] - [Why this matters]

#### Removed from A (not in B)
- [Element 1] - [Potential impact]

#### Modified Between A and B
- [Element]: Changed from [X] to [Y] - [Impact]

### Recommendation
[Clear recommendation with reasoning]

### Next Steps
[Actionable next step for user]
```

## When to Use

- You have two versions of a prompt and want to understand differences
- Need to decide which prompt version is better
- Want to understand what changed between iterations
- Deciding between different prompt approaches
- Learning what makes one prompt more effective than another

## Related Commands

- `/coggle` - Expand a prompt to improve it
- `/analyze-prompt` - Analyze a single prompt for quality
- `/format-prompt` - Export a prompt in different formats
