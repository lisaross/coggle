# OpenAI Codex & GPT Prompting Templates

## Core Pattern
Use delimiters (### or """) to separate instructions from context.

### Code Generation Template
```
### Instructions
[What you want]

### Context
"""
[Relevant code or information]
"""

### Output
[Expected format]
```

### Best Practices
- Put instructions at the beginning
- Use specific synonyms (not vague words)
- Provide examples when possible
- For code: comments act as prompts

### API Request Template
```json
{
  "model": "gpt-4",
  "messages": [
    {"role": "system", "content": "[SYSTEM PROMPT]"},
    {"role": "user", "content": "[USER REQUEST]"}
  ],
  "temperature": 0.7
}
```
