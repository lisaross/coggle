# /coggle - Quick Prompt Expansion

Instantly expand a vague prompt into a precise, actionable instruction.

## CRITICAL: Generation Only

**This command GENERATES improved prompts. It does NOT execute tasks.**

- Input: User's vague/unclear prompt
- Output: An enhanced, production-ready prompt for the user to copy and use

## Usage

```bash
/coggle [your prompt]
```

## Examples

```bash
/coggle Write me something about marketing
/coggle Help me debug this code
/coggle Create a presentation about AI
```

## Execution

**Invoke the `prompt-expander` agent via Task tool:**

```yaml
Task:
  subagent_type: "general-purpose"
  description: "Expand prompt via prompt-expander agent"
  prompt: |
    Read and follow the agent specification at:
    .claude/agents/prompt-expander.md

    Then expand this prompt:
    > $ARGUMENTS

    Use the Skill tool to invoke the prompt-expander skill for PRECISE methodology.
    Research domain context with Exa/Ref if the prompt involves specific technologies.
```

The Task tool spawns a subagent that:

1. Reads the prompt-expander agent specification
2. Invokes the prompt-expander skill for methodology
3. Researches domain context if needed
4. Returns the expanded prompt

## Output

```markdown
## Coggle!

**Original:**
> [Input prompt]

---

**Expanded:**

[Full expanded prompt ready to use]

---

**Quick Actions:** [Copy] [Markdown] [JSON]
```
