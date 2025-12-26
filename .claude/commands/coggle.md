---
description: Expand, analyze, and manage prompts with the PRECISE methodology
argument-hint: "[prompt] or [subcommand] [args]"
allowed-tools: [Task, Skill, AskUserQuestion, Write]
---

# /coggle - Prompt Enhancement Toolkit

Unified command for expanding, analyzing, formatting, and comparing prompts.

## Usage

```bash
/coggle [prompt]                    # Expand a vague prompt (default)
/coggle analyze [prompt]            # Score prompt quality
/coggle template [category] [type]  # Get ready-to-use template
/coggle format [format] [prompt]    # Export in specific format
/coggle compare [A] vs [B]          # Compare two prompts
```

## Examples

```bash
/coggle Write me something about marketing
/coggle analyze Help me debug this code
/coggle template analysis market
/coggle format json last
/coggle compare "Be concise" vs "Be detailed"
```

## Execution

### Mode 1: Default Expansion (No Subcommand)

When invoked with just a prompt:

#### Step 1: Expand the Prompt

Use Task tool to invoke prompt-expander agent:

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

#### Step 2: Present Interactive Options

After expansion, use AskUserQuestion to offer:

```yaml
AskUserQuestion:
  question: "What would you like to do with this expanded prompt?"
  options:
    - "Run - Execute this prompt now"
    - "Save - Save to .prompts/[name].md"
    - "Analyze - Score quality first"
    - "Other - [free-text for refinement]"
```

#### Step 3: Handle User Choice

- **If "Run"**: Use Task tool to spawn appropriate agent to execute the expanded prompt
- **If "Save"**: Ask for filename, then Write to `.prompts/[name].md`
- **If "Analyze"**: Invoke prompt-analyzer agent (Mode 2 workflow)
- **If "Other"**: Use refinement input to iterate on the expansion

### Mode 2: Analyze Subcommand

Parse: `/coggle analyze [prompt]`

Use Task tool to invoke prompt-analyzer agent:

```yaml
Task:
  subagent_type: "general-purpose"
  description: "Analyze prompt quality via prompt-analyzer agent"
  prompt: |
    Read and follow the agent specification at:
    .claude/agents/prompt-analyzer.md

    Then analyze this prompt:
    > [extracted prompt]

    Use the Skill tool to invoke the prompt-analyzer skill for 7-dimension scoring.
```

### Mode 3: Template Subcommand

Parse: `/coggle template [category] [type]`

Use Skill tool to invoke prompt-templates skill:

```yaml
Skill:
  name: "prompt-templates"
  description: "Get [category]/[type] template"
```

Pass category and type to the skill for template selection.

### Mode 4: Format Subcommand

Parse: `/coggle format [format] [prompt|last]`

Use Skill tool to invoke prompt-formatter skill:

```yaml
Skill:
  name: "prompt-formatter"
  description: "Format prompt as [format]"
```

- If "last": Use the most recently expanded prompt from context
- Otherwise: Use the provided prompt text

### Mode 5: Compare Subcommand

Parse: `/coggle compare [A] vs [B]`

Use Task tool to invoke prompt-compare agent:

```yaml
Task:
  subagent_type: "general-purpose"
  description: "Compare two prompts via prompt-compare agent"
  prompt: |
    Read and follow the agent specification at:
    .claude/agents/prompt-compare.md

    Then compare these prompts:

    Prompt A:
    > [extracted A]

    Prompt B:
    > [extracted B]

    Use the Skill tool to invoke the prompt-compare skill for comparison methodology.
```

## Output Format

### Default Expansion Output

```markdown
## Coggle!

**Original:**
> [Input prompt]

---

**Expanded:**

[Full expanded prompt ready to use]

---

[Interactive options presented via AskUserQuestion]
```

### Analyze Output

Per prompt-analyzer agent specification (7-dimension scoring report).

### Template Output

Per prompt-templates skill specification (template with placeholders).

### Format Output

Per prompt-formatter skill specification (format-specific output).

### Compare Output

Per prompt-compare agent specification (side-by-side comparison report).

## Notes

- **Generation Only**: This command generates/transforms prompts. It does NOT execute tasks unless explicitly chosen via "Run" option.
- **Context Awareness**: The "last" keyword in format mode refers to the most recently expanded prompt in the current session.
- **Agent Delegation**: All complex logic delegated to specialized agents/skills. This command is a thin router.
