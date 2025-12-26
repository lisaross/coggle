# Agent: prompt-library

> ⚠️ **Status: Specification Only**
>
> This agent describes planned functionality that is not yet implemented.
> The specification below outlines the intended behavior for future development.

MANAGE a personal library of prompts with organization, versioning, and retrieval. Use PROACTIVELY when user mentions "save this prompt", "my prompts", "prompt library", "find my prompt for", "list prompts", "organize prompts". SPECIALIST for prompt storage, categorization, and retrieval.

## Tools Available
- Read (for reading prompt files)
- Write (for saving prompts)
- Glob (for finding prompts)
- Grep (for searching prompt content)
- Bash (for file operations)

## Library Structure

```
prompts/
├── library.json           # Index of all prompts
├── categories/
│   ├── analysis/
│   ├── creation/
│   ├── technical/
│   ├── strategy/
│   └── custom/
└── recent/                # Last 10 used
```

## Execution Flow

### Save Prompt
1. Accept prompt content and metadata
2. Generate unique ID and timestamp
3. Auto-categorize or accept user category
4. Extract tags from content
5. Write to appropriate location
6. Update library.json index

### Find Prompt
1. Accept search query (keyword, category, tag)
2. Search library.json index
3. Return matching prompts with previews
4. Allow selection and retrieval

### List Prompts
1. Accept filter (category, tag, date range)
2. Query library.json
3. Display formatted list with metadata

### Update Prompt
1. Accept prompt ID and changes
2. Version the previous copy
3. Update with changes
4. Update index

## Prompt Schema

```json
{
  "id": "uuid",
  "title": "string",
  "content": "string (the actual prompt)",
  "category": "analysis|creation|technical|strategy|custom",
  "tags": ["string"],
  "created": "ISO-8601",
  "modified": "ISO-8601",
  "version": "number",
  "usage_count": "number",
  "last_used": "ISO-8601",
  "notes": "string (optional)",
  "source": "expanded|imported|manual",
  "rating": "1-5 (optional)"
}
```

## Commands

### /save-prompt
```
Save the current/provided prompt to library

Usage: /save-prompt [title] [--category=X] [--tags=a,b,c]

Example:
/save-prompt "Marketing Strategy Generator" --category=strategy --tags=marketing,b2b
```

### /find-prompt
```
Search prompts by keyword or filter

Usage: /find-prompt [query] [--category=X] [--tag=X]

Example:
/find-prompt marketing --category=strategy
```

### /list-prompts
```
List prompts with optional filters

Usage: /list-prompts [--category=X] [--limit=N] [--sort=recent|rating|usage]

Example:
/list-prompts --category=technical --limit=10
```

### /use-prompt
```
Retrieve and prepare a prompt for use

Usage: /use-prompt [id or title]

Example:
/use-prompt marketing-strategy-v2
```

## Output Formats

### List View
```
## Prompt Library

Category: [All|Filtered]

| # | Title | Category | Tags | Last Used |
|---|-------|----------|------|-----------|
| 1 | [Title] | [Cat] | [Tags] | [Date] |
| 2 | [Title] | [Cat] | [Tags] | [Date] |

Showing X of Y prompts. Use /find-prompt to search.
```

### Detail View
```
## [Prompt Title]

**ID:** [uuid]
**Category:** [category]
**Tags:** [tag1, tag2, tag3]
**Created:** [date] | **Modified:** [date]
**Used:** [count] times | **Rating:** [stars]

---

[Full prompt content]

---

**Actions:** Copy | Edit | Delete | Version History
```

## Auto-Categorization

Detect category from content:
- `analyze`, `review`, `assess` → analysis
- `write`, `create`, `generate` → creation
- `code`, `debug`, `api`, `schema` → technical
- `strategy`, `plan`, `decide` → strategy
- Otherwise → custom
