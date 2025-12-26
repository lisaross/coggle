---
name: prompt-formatter
description: CONVERT prompts into various output formats including plain text, markdown, JSON, slides, emails, system prompts, and API requests. Use when user needs prompt in specific format for copying, sharing, or integrating. Triggers on "format as", "export as", "convert to", "make this a", "format prompt".
---

# Prompt Formatter

Convert expanded prompts into various output formats for different use cases including copy-paste, documentation, APIs, presentations, and system prompts.

## Trigger Phrases

Users invoke this skill by saying:
- "format as"
- "export as"
- "convert to"
- "make this a"
- "format prompt"

## When to Use This Skill

Use this skill when:
- User needs prompt in specific format for copying or sharing
- Prompt needs to be integrated into an application or API
- Presenting prompt in slides or documentation
- Converting prompt for email delegation
- Preparing prompt as system prompt for custom GPT/Assistant

## Available Formats

1. **Copy-Ready** - Plain text for pasting into chat interfaces
2. **Markdown** - Formatted documentation
3. **JSON** - Structured data for storage/APIs
4. **Slide Outline** - Presentation format
5. **Email Draft** - Professional delegation email
6. **System Prompt** - Persistent instructions for custom assistants
7. **API Request** - OpenAI/Anthropic API format

## Workflow

### Step 1: Identify Target Format

**Actions:**
- Determine which format the user needs
- Understand the use case (pasting, storing, presenting, etc.)
- Clarify any format-specific requirements

**Decision Points:**
- If user says "ChatGPT" or "Claude" → Copy-Ready format
- If user says "documentation" or "README" → Markdown format
- If user says "store" or "database" → JSON format
- If user says "present" or "teach" → Slide Outline format
- If user says "delegate" or "send to colleague" → Email Draft format
- If user says "custom GPT" or "assistant" → System Prompt format
- If user says "API" or mentions OpenAI/Anthropic → API Request format

### Step 2: Transform to Target Format

Apply format-specific transformations:

#### Format 1: Copy-Ready (Plain Text)

**Transformation Rules:**
- Remove markdown headers (#, ##, ###)
- Convert bullet points to plain dashes
- Remove code fences
- Preserve paragraph breaks
- Remove bold/italic markers

**Output:**
```
[Clean plain text ready for pasting]
```

#### Format 2: Markdown (Formatted)

**Structure:**
```markdown
# [Prompt Title]

## Context
[Background information]

## Instructions
1. [Step one]
2. [Step two]
3. [Step three]

## Requirements
- [Requirement 1]
- [Requirement 2]

## Output Format
[Expected format specification]

---
*Generated with Coggle*
```

#### Format 3: JSON (Structured Data)

**Schema:**
```json
{
  "prompt": {
    "title": "string",
    "version": "1.0",
    "created": "ISO-8601 date",
    "persona": {
      "role": "string",
      "expertise": "string"
    },
    "context": {
      "background": "string",
      "audience": "string",
      "purpose": "string"
    },
    "instructions": [
      {
        "step": 1,
        "action": "string",
        "details": "string"
      }
    ],
    "requirements": {
      "format": "string",
      "length": "string",
      "style": "string",
      "constraints": ["string"]
    },
    "examples": ["string"],
    "evaluation": {
      "success_criteria": ["string"],
      "avoid": ["string"]
    }
  },
  "metadata": {
    "category": "string",
    "tags": ["string"],
    "difficulty": "beginner|intermediate|advanced",
    "estimated_tokens": "number"
  }
}
```

#### Format 4: Slide Outline

**Structure:**
```
SLIDE 1: Title
- [Prompt name/purpose]
- [One-line description]

SLIDE 2: The Task
- What we're asking the AI to do
- Why this matters
- Expected outcome

SLIDE 3: The Setup (Persona & Context)
- Role: [AI persona]
- Background: [Context provided]
- Audience: [Who it's for]

SLIDE 4: The Instructions
- Step 1: [Action]
- Step 2: [Action]
- Step 3: [Action]

SLIDE 5: Requirements & Constraints
- Format: [Expected format]
- Must include: [Requirements]
- Must avoid: [Constraints]

SLIDE 6: Example Output
- [Sample of expected result]
- [Key quality indicators]

SLIDE 7: Key Takeaways
- [Principle 1]
- [Principle 2]
- [Why this pattern works]
```

#### Format 5: Email Draft

**Structure:**
```
Subject: Request: [Task Summary]

Hi [Recipient],

I need help with [task description in plain language].

**Background:**
[Context and why this is needed]

**What I Need:**
[Clear deliverable description]

**Requirements:**
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

**Timeline:**
[When it's needed]

**Format:**
[How to deliver/format the output]

Please let me know if you need any clarification.

Thanks,
[Sender]
```

#### Format 6: System Prompt

**Structure:**
```
You are [role/persona with expertise].

Your purpose is to [primary function].

CORE BEHAVIORS:
- [Behavior 1]
- [Behavior 2]
- [Behavior 3]

CONSTRAINTS:
- Always [requirement]
- Never [restriction]
- When uncertain, [fallback behavior]

OUTPUT FORMAT:
[Default format specification]

INTERACTION STYLE:
[Tone and communication guidelines]
```

#### Format 7: API Request

**OpenAI Format:**
```json
{
  "model": "gpt-4",
  "messages": [
    {
      "role": "system",
      "content": "[System prompt portion]"
    },
    {
      "role": "user",
      "content": "[User prompt portion]"
    }
  ],
  "temperature": 0.7,
  "max_tokens": 2000
}
```

**Anthropic Format:**
```json
{
  "model": "claude-3-5-sonnet-20241022",
  "max_tokens": 2000,
  "system": "[System prompt portion]",
  "messages": [
    {
      "role": "user",
      "content": "[User prompt portion]"
    }
  ]
}
```

### Step 3: Validate Format

**Actions:**
- Verify the output matches format specifications
- Check for proper syntax (especially JSON)
- Ensure all placeholders are filled or marked clearly
- Test that format serves the intended use case

**Quality checks:**
- Copy-Ready → No markdown artifacts remain
- Markdown → Proper heading hierarchy
- JSON → Valid JSON syntax
- Slide Outline → Logical flow for presentation
- Email Draft → Professional tone, clear CTA
- System Prompt → Concise, directive language
- API Request → Valid API schema

### Step 4: Provide Usage Guidance

For each format, include brief usage instructions:

**Copy-Ready:** "Copy and paste directly into ChatGPT, Claude, or other chat interface"
**Markdown:** "Save as .md file or paste into documentation"
**JSON:** "Store in database or pass to API endpoints"
**Slide Outline:** "Import into PowerPoint/Google Slides or use as speaking notes"
**Email Draft:** "Customize recipient name and timeline, then send"
**System Prompt:** "Use in Custom GPT configuration or assistant settings"
**API Request:** "Include your API key and endpoint, then send via curl/fetch"

## Format Selection Guide

| Use Case | Recommended Format |
|----------|-------------------|
| Pasting into ChatGPT/Claude | Copy-Ready |
| Documentation/README | Markdown |
| Prompt library/database | JSON |
| Teaching/presentation | Slide Outline |
| Delegating to colleague | Email Draft |
| Custom GPT/Assistant | System Prompt |
| Programmatic usage | API Request |

## Success Indicators

This skill is successful when:
- [ ] Target format identified correctly
- [ ] Prompt transformed to match format specification exactly
- [ ] Output is valid (especially JSON, API formats)
- [ ] Usage instructions provided
- [ ] User can immediately use the formatted output

## Quality Checklist

Before marking complete, verify:
- [ ] Format matches user's stated need or use case
- [ ] All format-specific syntax is correct
- [ ] No markdown artifacts in plain text formats
- [ ] JSON formats validate (use JSON validator)
- [ ] API formats match provider specs (OpenAI vs Anthropic)
- [ ] Slide outlines have logical flow
- [ ] Email drafts are professional and complete
- [ ] System prompts are concise and directive

## Common Transformations

**Prompt → Copy-Ready:**
- Strip all `#` headers → plain text
- Convert `- bullet` → `- bullet` (keep dash)
- Remove `**bold**` → `bold`
- Remove ` ```code fences``` ` → leave content

**Prompt → JSON:**
- Extract persona → `persona.role` and `persona.expertise`
- Extract context → `context` object
- Convert numbered steps → `instructions` array
- Extract requirements → `requirements` object

**Prompt → System Prompt:**
- Extract role → "You are [role]"
- Convert instructions → "CORE BEHAVIORS"
- Convert constraints → "CONSTRAINTS"
- Extract format → "OUTPUT FORMAT"

## Integration Points

**Works with:**
- `prompt-expander` - Expand first, then format for delivery
- `prompt-analyzer` - Analyze before formatting to ensure quality
- `prompt-compare` - Compare different formatted versions

---

*Prompt Formatter skill | Created: 2025-12-26*
