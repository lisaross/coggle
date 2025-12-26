# /learn-prompting - Interactive Prompt Engineering Tutorial

Learn prompt engineering concepts through interactive lessons and practice.

## Usage

```
/learn-prompting [topic]
```

## Topics

### Fundamentals
- `basics` - Core prompting principles
- `precise` - The PRECISE framework
- `antipatterns` - Common mistakes to avoid
- `format` - Controlling output format

### Intermediate
- `cot` - Chain of thought prompting
- `fewshot` - Few-shot learning with examples
- `roles` - Effective role/persona prompting
- `constraints` - Using constraints effectively

### Advanced
- `meta` - Meta-prompting techniques
- `multiturn` - Multi-turn conversation strategies
- `models` - Model-specific optimization
- `debug` - Debugging failing prompts

## Examples

```
/learn-prompting basics
/learn-prompting precise
/learn-prompting cot
/learn-prompting debug
```

## Behavior

1. Presents concept with clear explanation
2. Shows before/after examples
3. Provides key principles
4. Offers practice exercise
5. Gives feedback on attempts

## Execution

When invoked:

1. Parse topic from input
2. Invoke prompt-coach agent
3. Load appropriate teaching module
4. Present lesson content
5. Offer practice opportunity
6. Provide feedback if user attempts exercise

## Lesson Structure

```markdown
## Learn: [Topic Name]

### What Is It?
[2-3 sentence explanation]

### Why It Matters
[Impact on prompt quality]

### Before & After

**Without:**
> [Weak example]

**With:**
> [Strong example]

### Key Principles
1. [Principle]
2. [Principle]
3. [Principle]

### Try It Yourself
[Practice exercise]

### Quick Tips
- [Tip]
- [Tip]
- [Tip]

---
**Need more practice?** Share a prompt for personalized feedback.
```

## Topic Quick Reference

| Topic | Key Takeaway |
|-------|--------------|
| basics | Every prompt needs: role, task, format |
| precise | Use all 7 elements for complete prompts |
| antipatterns | Avoid vague verbs and implicit assumptions |
| cot | "Think step by step" for complex reasoning |
| fewshot | 2-3 examples set the pattern |
| roles | Specific expertise > generic roles |
| constraints | "Do not" is as important as "do" |
