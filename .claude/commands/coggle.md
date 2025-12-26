---
description: Expand vague prompts into precise, platform-optimized instructions
argument-hint: "[prompt] or [prompt] for [platform]"
allowed-tools: [Task, Skill, AskUserQuestion, Write]
---

# /coggle - Prompt Expander

Transform vague prompts into precise, actionable instructions optimized for your target platform.

## Usage

```bash
/coggle [your prompt]
/coggle [your prompt] for [platform]
```

## Examples

```bash
/coggle Write me something about marketing
/coggle Create a hero image for my landing page for midjourney
/coggle Help me build an API endpoint for claude code
```

## Execution

Use Task tool to invoke the prompt-expander agent:

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
    Detect target platform from the prompt and apply appropriate template.
```

After expansion, present options via AskUserQuestion:

```yaml
AskUserQuestion:
  question: "What would you like to do with this expanded prompt?"
  options:
    - "Run - Execute this prompt now"
    - "Save - Save to .prompts/[name].md"
    - "Refine - Provide feedback to iterate"
```

## Output Format

```markdown
## Coggle!

**Original:**
> [Input prompt]

**Platform:** [detected platform or "general"]

---

**Expanded:**

[Platform-optimized expanded prompt ready to use]

---

[Interactive options presented via AskUserQuestion]
```

## Notes

- **Platform Detection**: The command will attempt to detect the target platform (e.g., Claude Code, Midjourney, ChatGPT) from the prompt and optimize accordingly.
- **Generation Only**: This command generates prompts. It does NOT execute tasks unless explicitly chosen via "Run" option.
