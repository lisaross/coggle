---
name: prompt-expander
description: EXPAND vague or unclear prompts into precise, actionable instructions using PRECISE methodology. Use when user provides raw prompt needing improvement, wants to optimize AI interactions, or requests prompt enhancement. Triggers on "expand prompt", "improve prompt", "optimize prompt", "enhance prompt", "make this prompt better", "coggle".
---

# Prompt Expander

Transform vague or unclear prompts into precise, actionable instructions using proven best practices. This skill applies the PRECISE methodology to systematically improve prompt quality and effectiveness.

## Trigger Phrases

Users invoke this skill by saying:
- "expand prompt"
- "improve prompt"
- "optimize prompt"
- "enhance prompt"
- "make this prompt better"
- "coggle"

## When to Use This Skill

Use this skill when:
- User provides a raw prompt that needs improvement
- The prompt is vague, incomplete, or lacks structure
- User wants to optimize their AI interactions
- A prompt needs to be more actionable or specific

## Core Principles

1. **PRECISE Methodology**: Apply systematic framework covering Persona, Requirements, Examples, Context, Instructions, Specifications, and Evaluation
2. **Progressive Enhancement**: Transform incrementally, focusing on highest-impact improvements first
3. **Actionable Output**: Every expanded prompt should be immediately usable

## Workflow

### Step 1: Analyze Input

**Actions:**
- Read the user's original prompt
- Identify what's missing (role, context, structure, examples, etc.)
- Determine the prompt's intent and desired outcome

**What to expect:**
- Input may be a single sentence or vague request
- May lack context, structure, or specific requirements

### Step 2: Apply PRECISE Framework

Apply these transformations in order:

#### P - Persona
Define a specific role or expert identity for the AI to adopt.
- Add: "Act as a [specific expert role] with [relevant experience]..."

#### R - Requirements
Clarify the specific deliverables and constraints.
- Specify output format, length, style, and technical requirements
- Define what success looks like

#### E - Examples
Provide concrete examples or references.
- Include sample outputs, style references, or exemplars
- Show don't just tell

#### C - Context
Add relevant background information.
- Industry, audience, purpose, constraints
- Any assumptions that should be made explicit

#### I - Instructions
Break down the task into clear, numbered steps.
- Sequence the work logically
- Make each step actionable

#### S - Specifications
Define the technical format and structure.
- Output format (markdown, JSON, list, table)
- Structure requirements (sections, headings, bullets)

#### E - Evaluation Criteria
Specify how quality will be measured.
- Success metrics
- What to avoid

### Step 3: Generate Expanded Prompt

**Format the output as:**

```markdown
## Expanded Prompt

**Original Prompt:**
> [User's original prompt]

**Expanded Version:**

---

[Persona] Act as a [specific role] with expertise in [domain].

[Context] You are helping [audience] with [purpose]. The context is [background].

[Instructions] Complete the following steps:
1. [First step]
2. [Second step]
3. [Third step]

[Requirements]
- Output should be [format/length/style]
- Include [specific elements]
- Avoid [things to exclude]

[Examples] For reference:
- [Example or style guide]

[Specifications]
- Format: [markdown/JSON/list/table]
- Structure: [headings/bullets/numbered]
- Length: [approximate word count or sections]

---

**Why This Works:**
- [Brief explanation of key improvements made]
```

### Step 4: Explain Improvements

**Actions:**
- Highlight the 2-3 most impactful changes
- Explain why these improvements matter
- Show how they make the prompt more effective

## Quick Expansion Mode

For faster expansions when user needs speed over depth, focus on the top 3 transformations:

1. **Add Role** - Who should the AI be?
2. **Add Structure** - What format/steps?
3. **Add Specificity** - What exactly is needed?

## Export Options

After expansion, offer to format the result as:
- **Copy-ready** - Plain text for pasting
- **Markdown** - Formatted with headers
- **JSON** - Structured data format
- **Slide Outline** - For presentations
- **Email Draft** - Professional email format

## Success Indicators

This skill is successful when:
- [ ] Original prompt has been analyzed for gaps
- [ ] PRECISE framework elements have been applied where appropriate
- [ ] Expanded prompt is significantly more actionable than original
- [ ] Output includes both the expanded prompt and explanation of improvements
- [ ] User can immediately copy and use the expanded version

## Quality Checklist

Before marking complete, verify:
- [ ] Persona/role is specific and relevant
- [ ] Instructions are numbered and actionable
- [ ] Requirements are explicit and measurable
- [ ] Format/structure is clearly specified
- [ ] Output shows both original and expanded versions
- [ ] Explanation highlights key improvements

## Common Patterns

**Before:** "Write something about marketing"
**After:** "Act as a marketing strategist with 10+ years B2B SaaS experience. Write a 500-word blog post about email marketing best practices for startup founders. Include 3 actionable tips with examples. Format as: Hook -> Problem -> Solution -> Examples -> CTA. Tone: Professional but approachable."

**Before:** "Help me with code"
**After:** "Act as a senior Python developer. Review the following Flask API code for security vulnerabilities, performance issues, and PEP 8 compliance. For each issue found, provide: (1) Severity level, (2) Line number, (3) Description, (4) Recommended fix with code snippet. Format as markdown table."

## Integration Points

**Works with:**
- `prompt-analyzer` - Analyze before expanding to target specific weaknesses
- `prompt-formatter` - Format the expanded prompt for different use cases
- `prompt-compare` - Compare original vs expanded to show improvements

---

*Prompt Expander skill | Created: 2025-12-26*
