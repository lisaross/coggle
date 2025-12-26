# /template - Get Prompt Template

Retrieve a ready-to-use prompt template for common tasks.

## Usage

```
/template [category] [type]
```

## Categories

- `analysis` - Market analysis, code review, competitive analysis
- `creation` - Content writing, email drafting, copywriting
- `technical` - API design, database schema, system architecture
- `strategy` - Decision frameworks, planning, roadmaps

## Examples

```
/template analysis market
/template creation email
/template technical api
/template strategy decision
```

## Available Templates

### Analysis
- `market` - Market research and sizing
- `code` - Code review checklist
- `competitive` - Competitor analysis
- `data` - Data analysis framework

### Creation
- `blog` - Blog post writing
- `email` - Professional email drafting
- `copy` - Marketing copywriting
- `docs` - Documentation writing

### Technical
- `api` - API endpoint design
- `schema` - Database schema design
- `architecture` - System architecture
- `debug` - Debugging framework

### Strategy
- `decision` - Decision framework
- `roadmap` - Product/project roadmap
- `okr` - OKR planning
- `retrospective` - Team retrospective

## Execution

When invoked:

1. Parse category and type from input
2. Load the prompt-templates skill
3. Find matching template
4. Present template with placeholders highlighted
5. Offer customization suggestions

## Output

```markdown
## Template: [Category] - [Type]

### Description
[What this template is for]

### The Template

---

[Full template with [PLACEHOLDERS] marked]

---

### How to Use
1. Replace [PLACEHOLDERS] with your specifics
2. Remove sections that don't apply
3. Add context specific to your situation
4. Run through /coggle for final polish

### Customization Tips
- [Tip 1]
- [Tip 2]
```

## Quick Access

Most common templates:
- `/template creation email` - Email writing
- `/template analysis code` - Code review
- `/template technical api` - API design
- `/template strategy decision` - Decision making
