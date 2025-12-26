# /format-prompt - Export Prompt in Different Format

Convert a prompt to various output formats for different use cases.

## Usage

```
/format-prompt [format] [prompt or "last"]
```

## Available Formats

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
/format-prompt markdown last
/format-prompt system last
```

## Behavior

1. Takes a prompt (or uses last expanded prompt)
2. Converts to requested format via prompt-formatter skill
3. Outputs ready-to-use result
4. Provides usage instructions for the format

## Execution

When invoked:

1. Parse format type from user input
2. Get prompt content (provided or "last" expanded)
3. Invoke prompt-formatter skill with format specification
4. Present formatted output with usage guidance

**Note:** For detailed format specifications, transformation rules, and use case guidance, the agent invokes the prompt-formatter skill which contains the complete formatting methodology.
