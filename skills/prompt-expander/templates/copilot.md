# GitHub Copilot Prompting Templates

GitHub Copilot uses code context (current file, open tabs, chat history) to generate responses. Effective prompts combine natural language with code structure for precise results.

## Core Pattern

Start general (describe the goal), then get specific (list requirements). Copilot works best when it understands both **what** you want and **how** it should be implemented.

### Code Generation Template

```text
[High-level goal description]

Requirements:
- [Specific behavior 1]
- [Specific behavior 2]
- [Error handling approach]

Use [language/framework conventions]
```

### Inline Comment Pattern

For code completions, use descriptive comments:

```javascript
// Function that validates email addresses
// Returns true if valid, throws if input is not a string
// Uses RFC 5322 compliant regex
function validateEmail(email) {
```

## Example Prompts

**Function Generation:**

```text
Write a TypeScript function that retries an async operation with exponential backoff

Requirements:
- Accept a function, max retries (default 3), and initial delay (default 1000ms)
- Double the delay after each retry
- Return the successful result or throw after max retries
- Log each retry attempt with the attempt number
```

**Code Explanation:**

```text
Explain what this code does and identify any potential issues:

[paste code]

Focus on:
- Logic flow
- Edge cases not handled
- Performance considerations
```

**Refactoring:**

```text
Refactor this function to:
- Use early returns instead of nested if/else
- Add TypeScript types
- Handle the null case explicitly

[paste code]
```

**Test Generation:**

```text
Write unit tests for this function using Jest

Cover:
- Happy path with valid input
- Edge cases (empty string, null, undefined)
- Error conditions

[paste function]
```

## Key Principles

1. **Start general, get specific**: Describe the goal first, then requirements
2. **Provide examples**: Show input/output pairs for clarity
3. **Use context**: Reference open files with @file or keep relevant code visible
4. **Be explicit about constraints**: Error handling, types, conventions
5. **Iterate**: Ask follow-up questions to refine the output

## PRECISE Adaptations

| Element | Copilot Approach |
| ------- | ---------------- |
| Persona | Not needed—Copilot is always a coding assistant |
| Requirements | Function signature, types, behavior specs |
| Examples | Input/output pairs, sample usage |
| Context | Language, framework, existing patterns in codebase |
| Instructions | Step-by-step breakdown for complex tasks |
| Specifications | Return type, error handling, naming conventions |
| Evaluation | Test cases, edge case handling |

## Slash Commands

Use built-in commands for common tasks:

- `/explain` - Explain selected code
- `/fix` - Fix problems in selected code
- `/tests` - Generate tests for selected code
- `/doc` - Add documentation to selected code
- `/simplify` - Simplify selected code

## Agent Mode (@workspace)

For codebase-wide tasks:

```text
@workspace How do we handle authentication in this project?

@workspace Find all API endpoints that don't have rate limiting

@workspace Create a new React component following our existing patterns
```

## Anti-Patterns

- **Avoid**: Prompts without context (Copilot needs to see relevant code)
- **Avoid**: Overly long single prompts—break into steps
- **Avoid**: Asking about non-coding topics
- **Avoid**: Expecting perfect code on first try—iterate
