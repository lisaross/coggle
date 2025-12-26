# /format-prompt - Export Prompt in Different Format

Convert a prompt to various output formats for different use cases.

## Usage

```
/format-prompt [format] [prompt or "last"]
```

## Formats

- `copy` - Plain text for pasting
- `markdown` - Formatted with headers
- `json` - Structured data
- `slides` - Presentation outline
- `email` - Email request format
- `system` - System prompt format
- `api` - API request body (OpenAI/Anthropic)

## Examples

```
/format-prompt json [paste prompt here]
/format-prompt slides last
/format-prompt api last --provider=anthropic
```

## Behavior

1. Takes a prompt (or uses last expanded prompt)
2. Converts to requested format
3. Outputs ready-to-use result
4. Copies to clipboard if possible

## Execution

When invoked:

1. Parse format type from input
2. Get prompt content (provided or last expanded)
3. Invoke the prompt-formatter skill
4. Apply format transformation
5. Present formatted output
6. Offer clipboard copy

## Output Examples

### Copy Format
```
[Clean plain text with no formatting marks]
```

### JSON Format
```json
{
  "prompt": {
    "persona": "...",
    "context": "...",
    "instructions": [...],
    "requirements": {...}
  }
}
```

### Slides Format
```
SLIDE 1: Title
- Purpose
- Outcome

SLIDE 2: The Setup
...
```

### API Format
```json
{
  "model": "claude-3-opus-20240229",
  "system": "...",
  "messages": [...]
}
```

## Use Case Guide

| Scenario | Format |
|----------|--------|
| Pasting into ChatGPT | `copy` |
| Saving to docs | `markdown` |
| Storing in database | `json` |
| Teaching/presenting | `slides` |
| Delegating to colleague | `email` |
| Building custom GPT | `system` |
| Calling LLM API | `api` |
