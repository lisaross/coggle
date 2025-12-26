# Perplexity AI Prompting Templates

Perplexity combines LLM reasoning with real-time web search and citations. Effective prompts should guide both **retrieval** (what it searches for) and **reasoning** (how it synthesizes the answer).

## Core Pattern

Structure prompts to specify search scope, recency requirements, and output format.

### Research Query Template

```text
[Topic or question]

Search parameters:
- Focus on [specific domains/sources]
- Prioritize [recency requirement: last week/month/year]
- Include [academic papers/news/official docs]

Output format:
- [Bullet summary / detailed analysis / comparison table]
- Cite sources inline
```

### Example Prompts

**Factual Research:**
```text
What are the latest developments in quantum computing error correction?

Focus on peer-reviewed research from 2024-2025.
Summarize the top 3 breakthroughs with citations.
Include practical implications for each.
```

**Competitive Analysis:**
```text
Compare the pricing and features of Vercel, Netlify, and Cloudflare Pages for hosting Next.js apps.

Use official pricing pages as primary sources.
Present as a comparison table with monthly costs for 100k page views.
Note any recent pricing changes from 2025.
```

**Current Events:**
```text
What happened with [topic] in the last 48 hours?

Prioritize breaking news from major outlets.
Separate confirmed facts from speculation.
List key sources chronologically.
```

## Key Principles

1. **Specify recency**: Perplexity searches in real-time, so indicate how fresh you need the information
2. **Name source types**: Academic, news, official documentation, forums
3. **Request citations**: Ask for inline citations or a sources list
4. **Define output structure**: Tables, bullets, prose with headers
5. **Use Pro Search mode**: For complex multi-step research, indicate you want deep research

## PRECISE Adaptations

| Element | Perplexity Approach |
| ------- | ------------------- |
| Persona | "Research assistant focused on [domain]" |
| Requirements | Specify source types, recency, depth |
| Examples | Reference types of sources to find |
| Context | Explain why you need this information |
| Instructions | Break into search phases if complex |
| Specifications | Output format, citation style |
| Evaluation | Accuracy, source quality, completeness |

## Pro Search Tips

For complex research, structure as multi-step:

```text
I need to understand [complex topic]. Please:

1. First, explain the foundational concepts
2. Then, find the latest research (2024-2025)
3. Finally, identify open questions and controversies

Use academic sources where possible. Cite everything.
```

## Anti-Patterns

- **Avoid**: Generic questions without search guidance
- **Avoid**: Asking for opinions (it will cite sources instead)
- **Avoid**: Ignoring the citation capability—always request sources
