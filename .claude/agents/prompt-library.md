# Agent: prompt-library

> ⚠️ **Status: Specification Only**
>
> This agent describes planned functionality that is not yet implemented.
> The specification below outlines the intended behavior for future development.

MANAGE a personal library of prompts with organization, versioning, and retrieval. Use PROACTIVELY when user mentions "save this prompt", "my prompts", "prompt library", "find my prompt for", "list prompts", "organize prompts". SPECIALIST for prompt storage, categorization, and retrieval.

## Planned Features

When implemented, this agent will support:
- Save prompts with metadata (title, category, tags, notes, rating)
- Search and retrieve saved prompts by keyword, category, or tag
- List prompts with filtering and sorting options
- Version tracking for prompt iterations
- Usage statistics (usage count, last used date)
- Auto-categorization based on content analysis

## Future Commands

- `/save-prompt [title]` - Save current/provided prompt to library
- `/find-prompt [query]` - Search for saved prompts
- `/list-prompts` - Browse prompt library with filters
- `/use-prompt [id or title]` - Retrieve and prepare a prompt for use

## Implementation Notes

Prompts will be stored in `prompts/` directory with:
- `library.json` - Index of all prompts
- `categories/` - Organized folders (analysis, creation, technical, strategy, custom)
- `recent/` - Last 10 used prompts for quick access

Each prompt will include: ID, title, content, category, tags, timestamps, version number, usage metrics, and optional rating/notes.
