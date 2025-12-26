# Coggle - AI Prompt Expander

Transform vague AI prompts into precise, platform-optimized instructions using the **PRECISE** methodology.

## Features

- **Multi-Platform Support**: Optimizes prompts for Claude, GPT, Gemini, Perplexity, GitHub Copilot, Grok, Midjourney, Flux, Sora, and more
- **PRECISE Framework**: Systematic approach covering Persona, Requirements, Examples, Context, Instructions, Specifications, and Evaluation
- **Platform Detection**: Automatically detects target platform from context clues
- **Interactive Workflow**: Run, Save, or Refine expanded prompts

## Installation

### From Marketplace

```bash
claude plugins install coggle
```

### Local Development

```bash
claude --plugin-dir /path/to/coggle
```

## Usage

### Basic Expansion

```bash
/coggle help me write better emails
```

### Platform-Specific

```bash
/coggle a sunset over mountains for midjourney
/coggle write a function to parse JSON for claude code
/coggle create a product demo video for sora
```

### After Expansion

Choose from:

- **Run** - Execute the expanded prompt immediately
- **Save** - Save to `.prompts/[name].md` for reuse
- **Refine** - Iterate with feedback

## Supported Platforms

| Platform           | Triggers                        | Best For                  |
| ------------------ | ------------------------------- | ------------------------- |
| Claude/Claude Code | "claude", "system prompt"       | Complex reasoning, coding |
| OpenAI/GPT         | "gpt", "chatgpt", "openai"      | Code generation, chat     |
| Gemini             | "gemini", "google ai"           | Multimodal, reasoning     |
| Perplexity         | "perplexity", "research"        | Research with citations   |
| GitHub Copilot     | "copilot", "github"             | Code completion           |
| Grok               | "grok", "xai"                   | Conversational, real-time |
| Image Gen          | "midjourney", "dall-e", "image" | Visual content            |
| Flux               | "flux", "flux.1"                | Photorealistic images     |
| Video Gen          | "sora", "runway", "video"       | Video content             |

## The PRECISE Framework

Each prompt is enhanced with:

| Element            | Purpose                       |
| ------------------ | ----------------------------- |
| **P**ersona        | Define the AI's role or style |
| **R**equirements   | Specify deliverables          |
| **E**xamples       | Provide concrete references   |
| **C**ontext        | Add relevant background       |
| **I**nstructions   | Break down the task           |
| **S**pecifications | Define format and structure   |
| **E**valuation     | Specify success criteria      |

## Examples

### Text AI (Claude)

```text
Before: "Write something about marketing"

After: "Act as a marketing strategist with 10+ years B2B SaaS experience.
Write a 500-word blog post about email marketing best practices for
startup founders. Include 3 actionable tips with examples. Format as:
Hook -> Problem -> Solution -> Examples -> CTA.
Tone: Professional but approachable."
```

### Image AI (Midjourney)

```text
Before: "sunset over mountains"

After: "Golden hour sunset over snow-capped mountain peaks, dramatic
god rays through clouds, alpine lake reflection in foreground,
cinematic composition, in the style of Ansel Adams, photorealistic,
--ar 16:9 --v 6 --q 2"
```

## Plugin Structure

```text
coggle/
├── .claude-plugin/
│   └── plugin.json      # Plugin manifest
├── agents/
│   └── prompt-expander.md
├── commands/
│   └── coggle.md        # /coggle command
├── skills/
│   └── prompt-expander/
│       ├── SKILL.md     # PRECISE methodology
│       └── templates/   # Platform-specific patterns
└── README.md
```

## Development

See [CLAUDE.md](./CLAUDE.md) for development guidelines.

### Adding Platform Templates

1. Create `skills/prompt-expander/templates/[platform].md`
2. Define platform characteristics, style, and constraints
3. Add adaptation guidelines for PRECISE elements
4. Update platform detection in `SKILL.md`

## License

MIT

## Author

Lisa Ross ([@makably](https://github.com/makably))
