# /analyze-prompt - Prompt Quality Diagnosis

Analyze a prompt to identify weaknesses and get actionable improvement suggestions.

## Usage

```bash
/analyze-prompt [your prompt]
```

## Examples

```bash
/analyze-prompt Write a blog post about technology trends
/analyze-prompt Help me with my code problem
/analyze-prompt Create marketing content
```

## Execution

**Invoke the `prompt-analyzer` agent via Task tool:**

```yaml
Task:
  subagent_type: "general-purpose"
  description: "Analyze prompt via prompt-analyzer agent"
  prompt: |
    Read and follow the agent specification at:
    .claude/agents/prompt-analyzer.md

    Then analyze this prompt:
    > $ARGUMENTS

    Use the Skill tool to invoke the prompt-analyzer skill for scoring methodology.
```

The Task tool spawns a subagent that:

1. Reads the prompt-analyzer agent specification
2. Invokes the prompt-analyzer skill for methodology
3. Scores across 7 dimensions
4. Returns the analysis report

## Output

```markdown
## Prompt Analysis

**Analyzing:**
> [First 100 chars of prompt...]

### Scores

| Dimension | Score |
|-----------|-------|
| Clarity | X/10 |
| Specificity | X/10 |
| Structure | X/10 |
| Context | X/10 |
| Actionability | X/10 |
| Completeness | X/10 |
| Efficiency | X/10 |

**Overall: X/70** ([Rating])

### Issues Found

1. **[Issue]** - [Fix]
2. **[Issue]** - [Fix]
3. **[Issue]** - [Fix]

---

**Fix automatically?** Run `/coggle` to expand with improvements.
```

## Rating Scale

- **60-70**: Excellent - Production ready
- **45-59**: Good - Minor tweaks helpful
- **30-44**: Fair - Significant improvements needed
- **Below 30**: Poor - Major rewrite recommended
