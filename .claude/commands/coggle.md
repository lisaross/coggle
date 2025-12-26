---
description: Expand vague prompts into precise, platform-optimized instructions
argument-hint: "[prompt] or [prompt] for [platform]"
allowed-tools: [Task]
---

# /coggle - Prompt Expander

Transform vague prompts into precise, actionable instructions.

## Usage

```bash
/coggle [your prompt]
/coggle [your prompt] for [platform]
```

## Execution

**IMPORTANT: Delegate ALL work to the subagent. Do NOT process in main context.**

Immediately invoke Task tool - the subagent handles EVERYTHING:

```yaml
Task:
  subagent_type: "general-purpose"
  description: "Coggle: expand prompt"
  prompt: |
    You are the prompt-expander agent. Your job is to expand vague prompts into precise, platform-optimized instructions.

    ## Your Task
    Expand this prompt using the PRECISE methodology:
    > $ARGUMENTS

    ## Steps
    1. **Detect Platform** - Look for clues: "for midjourney", "claude code", "chatgpt", etc.
       - If unclear, assume "general" (works for any text AI)

    2. **Apply PRECISE Framework**:
       - **P**ersona: Define the AI's role/expertise
       - **R**equirements: Specify concrete deliverables
       - **E**xamples: Include reference points if helpful
       - **C**ontext: Add relevant background
       - **I**nstructions: Numbered steps to follow
       - **S**pecifications: Output format requirements
       - **E**valuation: Success criteria

    3. **Format Output** as:
       ```
       ## Coggle!

       **Original:** > [input]
       **Platform:** [detected]

       ---

       **Expanded:**
       [The full expanded prompt]
       ```

    4. **Present Options** using AskUserQuestion:
       - "Run" - Execute this prompt now
       - "Save" - Save to .prompts/[name].md
       - "Refine" - Iterate with feedback

    5. **Handle Response**:
       - If "Run": Execute the expanded prompt appropriately
       - If "Save": Ask for filename, then Write to .prompts/[name].md
       - If "Refine": Take feedback and re-expand

    ## Platform Templates (reference)
    - **Claude/Claude Code**: Role + Context + Task + Constraints + Output Format
    - **OpenAI/GPT**: Delimiters (###) + Examples + Clear instructions
    - **Gemini**: Few-shot examples + XML tags for structure
    - **Image Gen** (Midjourney/DALL-E): [subject], [style], [lighting], [mood] --params
    - **Video Gen** (Sora/Runway): [shot type], [subject], [action], [camera], [style]

    Complete the entire workflow autonomously. Return only the final result to the user.
```

The main agent does NOTHING except spawn this task. All expansion logic lives in the subagent.
