# Grok AI Prompting Templates

Grok (by xAI) combines strong reasoning with a distinctive conversational style—witty, direct, and sometimes irreverent. It has real-time data access via DeepSearch and handles complex multi-step reasoning well.

## Core Pattern: Role-Task-Format

Structure prompts using the RTF framework for consistent results:

```text
Role: [Who Grok should be]
Task: [What you want done]
Format: [How to structure the output]
```

### Example Prompts

**Analysis with Personality:**
```text
Role: Skeptical tech analyst who's seen too many hype cycles
Task: Evaluate the claims in this startup pitch deck
Format: Bullet points with a "reality check" score (1-10) for each claim

[paste pitch content]
```

**Research with DeepSearch:**
```text
Use DeepSearch to find the latest information about [topic].

Focus on developments from the past week.
Summarize in 3 paragraphs:
1. What happened
2. Why it matters
3. What's likely next
```

**Creative with Edge:**
```text
Role: Sardonic comedy writer
Task: Write 5 tweets about the absurdity of [topic]
Format: Each tweet under 280 characters, progressively more unhinged

Keep it smart, not mean.
```

**Reasoning Task:**
```text
Think through this step by step:

[Problem description]

Show your reasoning, flag any assumptions, and give a confidence level with your final answer.
```

## Key Principles

1. **Embrace the personality**: Grok responds well to prompts that match its irreverent style
2. **Use "Think Mode"**: For complex reasoning, ask it to show its work
3. **Leverage real-time data**: Reference current events—Grok can access live information
4. **Be direct**: No need for excessive politeness; Grok appreciates clarity
5. **Request confidence levels**: Ask how sure it is about answers

## PRECISE Adaptations

| Element | Grok Approach |
| ------- | ------------- |
| Persona | Match Grok's wit or specify a contrasting style |
| Requirements | Be direct and specific—Grok handles complexity |
| Examples | Include if you want a specific format matched |
| Context | Current events context works well with DeepSearch |
| Instructions | Can handle multi-step reasoning chains |
| Specifications | Format preferences, tone (serious vs playful) |
| Evaluation | Ask for confidence levels and alternative views |

## Think Mode

For complex problems, invoke deliberate reasoning:

```text
I need you to think carefully about this:

[Complex question or problem]

Use step-by-step reasoning. Consider:
- What assumptions am I making?
- What could go wrong?
- What's my confidence level?

Then give your conclusion.
```

## Style Control

Grok has distinct modes. Specify what you want:

```text
Respond in [regular/fun] mode.
```

- **Regular mode**: More straightforward, professional
- **Fun mode**: More irreverent, witty, edgy

## DeepSearch Prompts

For research requiring current information:

```text
Search for the most recent information about [topic].

I need:
- Latest news (past 24-48 hours)
- Key facts with sources
- Any controversy or debate

Summarize what you find.
```

## Anti-Patterns

- **Avoid**: Overly formal corporate-speak (Grok works better with directness)
- **Avoid**: Expecting GPT-style responses (Grok has its own voice)
- **Avoid**: Ignoring Think Mode for complex reasoning tasks
- **Avoid**: Not specifying format for structured output
