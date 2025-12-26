---
name: prompt-coach
description: TEACH prompt engineering skills through interactive lessons, exercises, and personalized guidance. Use when user wants to learn prompting, asks for tips, requests coaching, or needs to understand prompt patterns.
---

# Prompt Coach

Interactive prompt engineering teacher that guides users through fundamentals to advanced techniques with hands-on exercises and personalized feedback.

## Trigger Phrases
- "teach me prompting"
- "how do I prompt for"
- "what makes a good prompt"
- "prompt engineering tips"
- "why does this work"
- "how do I write better prompts"
- "learn prompting"
- "prompt engineering tutorial"

## When to Use This Skill

Use this skill when:
- User wants to learn prompt engineering concepts
- User asks for tips or best practices
- User wants to understand why certain prompts work better
- User needs guidance on prompt patterns
- User wants to debug or improve their prompting technique
- User requests interactive coaching or exercises

## Skill Assessment

Determine user's experience level:
- **Beginner** - New to prompting, needs fundamentals
- **Intermediate** - Knows basics, needs optimization
- **Advanced** - Optimizing for edge cases

Identify learning goal:
- General improvement
- Specific use case mastery
- Debugging failing prompts
- Advanced techniques

## Teaching Modules

### Module 1: Fundamentals
Core concepts every prompter needs:

#### 1. The PRECISE Framework

The PRECISE methodology is the core prompt expansion framework. For complete details, see the `prompt-expander` skill.

**Quick Reference:**
- **P**ersona - Define AI role/expertise
- **R**equirements - Specify deliverables
- **E**xamples - Include references
- **C**ontext - Add background
- **I**nstructions - Numbered steps
- **S**pecifications - Format requirements
- **E**valuation - Success criteria

→ See `.claude/skills/prompt-expander/SKILL.md` for full methodology and examples.

#### 2. Common Anti-Patterns

| Anti-Pattern | Example | Why It Fails | Fix |
|--------------|---------|--------------|-----|
| Vague verbs | "help", "something", "stuff" | No clear action | Use specific verbs: analyze, create, compare |
| Missing audience | No target reader defined | Wrong tone/depth | "For [specific audience]" |
| Implicit assumptions | Unstated requirements | AI fills gaps incorrectly | Make all assumptions explicit |
| Wall of text | No structure | Hard to parse | Add sections, numbers, bullets |
| Conflicting instructions | Contradictory asks | AI guesses priority | Resolve conflicts, prioritize |
| Scope creep | Too many tasks | Diluted focus | Split into focused prompts |
| Missing format | No output spec | Inconsistent results | Define exact structure |
| Role ambiguity | Unclear AI persona | Generic responses | Add specific role |

#### 3. Output Format Control

**Specifying Structure:**
- Use exact format descriptions: "Format as: [template]"
- Provide structural constraints: "Use markdown headers H2 and H3"
- Define length: "In 200 words or less"

**Examples as Templates:**
- Show, don't just tell: Include a concrete example
- Annotate examples: Explain what makes them good
- Multiple examples: Show variation within acceptable range

**Constraints and Boundaries:**
- Positive constraints: "Include [X, Y, Z]"
- Negative constraints: "Do not include [A, B, C]"
- Hard limits: "Exactly 5 items" vs soft "Around 5 items"

### Module 2: Intermediate Techniques

#### 1. Chain of Thought

**When to Request Reasoning:**
- Complex problems requiring logic
- Math or analytical tasks
- Multi-step processes
- When answers might be wrong

**Step-by-Step Prompting:**
```
Bad: "What's the ROI of this campaign?"
Good: "Calculate the ROI of this campaign by:
1. Identifying total costs
2. Calculating total revenue
3. Computing ROI percentage
4. Explaining assumptions made"
```

**Verification Steps:**
- Add: "Show your work"
- Add: "Double-check your calculations"
- Add: "Verify against [criteria]"

#### 2. Few-Shot Learning

**Effective Example Selection:**
- Choose diverse examples covering edge cases
- Ensure examples match desired quality
- Include both typical and boundary cases
- Show examples that cover the range

**Example Formatting:**
```
Here are examples of good outputs:

Example 1:
Input: [sample input 1]
Output: [sample output 1]

Example 2:
Input: [sample input 2]
Output: [sample output 2]

Now apply this pattern to: [your input]
```

**Number of Examples Needed:**
- Simple tasks: 1-2 examples
- Pattern recognition: 3-5 examples
- Complex tasks: 5-10 examples
- Edge case coverage: Include at least one boundary example

#### 3. Role Prompting

**Persona Selection:**
- Match expertise to task: "Senior data scientist" not just "expert"
- Add experience level: "with 10 years in healthcare analytics"
- Include relevant context: "who has worked with HIPAA-compliant systems"

**Expertise Calibration:**
- Too generic: "Act as an expert"
- Better: "Act as a senior solutions architect"
- Best: "Act as a senior solutions architect specializing in cloud-native architectures for fintech"

**Perspective Shifting:**
- First-person: "You are a [role]" (immersive)
- Third-person: "Respond as a [role] would" (analytical)
- Multiple perspectives: "Provide both a beginner and expert view"

### Module 3: Advanced Patterns

#### 1. Meta-Prompting

**Prompts About Prompts:**
- "Before answering, analyze what this prompt is asking for"
- "What information would make this prompt better?"
- "What assumptions does this prompt make?"

**Self-Correction Patterns:**
```
After providing your answer:
1. Review it for [criteria]
2. Identify any weaknesses
3. Provide a revised version
```

**Reflection Techniques:**
- "What would make this output more useful?"
- "What edge cases might this not handle?"
- "How confident are you in this answer (1-10)? Why?"

#### 2. Multi-Turn Strategies

**Building Context:**
- Turn 1: Establish framework
- Turn 2: Refine with feedback
- Turn 3: Polish and finalize

**Refinement Loops:**
```
Initial prompt: [broad request]
Follow-up: "Make it more [specific quality]"
Final: "Adjust [specific element]"
```

**Error Recovery:**
- If output is wrong: Point out specific issue, don't restart
- If format is wrong: Provide example of desired format
- If tone is off: Give specific tone guidance

#### 3. Model-Specific Optimization

**Claude vs GPT Differences:**
- Claude: Better at following complex instructions, prefers structured prompts
- GPT: Better at creative tasks, handles conversational prompts well
- Both: Respond to clear examples and constraints

**Token Efficiency:**
- Front-load important instructions
- Use concise examples
- Avoid redundancy
- Reference earlier context: "As mentioned above"

**Temperature/Parameter Guidance:**
- Creative tasks: Higher temperature (0.7-1.0)
- Analytical tasks: Lower temperature (0.0-0.3)
- Balanced tasks: Medium temperature (0.3-0.7)

## Quick Tips Database

| Technique | When to Use | Example |
|-----------|-------------|---------|
| Add persona | Generic outputs | "Act as a senior marketing strategist..." |
| Add constraints | Over-explanation | "In under 200 words..." |
| Add structure | Disorganized output | "Format as: 1. 2. 3." |
| Add examples | Wrong style | "Like this example:..." |
| Add negative | Unwanted content | "Do not include..." |
| Add reasoning | Logic errors | "Explain your reasoning..." |
| Add verification | Accuracy critical | "Double-check that..." |
| Add context | Missing background | "For a B2B SaaS startup..." |
| Add format | Inconsistent structure | "Output as markdown table" |
| Add evaluation | Quality uncertain | "Success criteria: actionable within 24h" |
| Add steps | Process unclear | "1. Analyze 2. Synthesize 3. Recommend" |
| Add audience | Wrong tone/depth | "For technical audience familiar with..." |

## Interactive Exercises

### Exercise 1: Fix the Vague Prompt
```
Original: "Help me with my resume"

Your task: Rewrite this prompt to be specific and actionable.

Hints:
- What role are you applying for?
- What's your experience level?
- What format do you want?
- What's the main problem to solve?

Example fix:
"Act as a senior recruiter specializing in tech roles. Review my software
engineer resume for a senior position at a FAANG company. I have 8 years
experience. Provide specific feedback on: 1) Impact quantification 2)
Technical skills presentation 3) Achievement framing. Format as a bulleted
list with before/after examples."
```

### Exercise 2: Add Missing Context
```
Original: "Write a blog post about AI"

Your task: Add context that would improve output.

Consider:
- Who's the audience? (Beginners? Experts? Business leaders?)
- What's the tone? (Educational? Persuasive? Technical?)
- What's the goal? (Inform? Convert? Educate?)
- What's the angle? (Ethics? Applications? Future trends?)

Example fix:
"Write a 1000-word blog post about practical AI applications for small
business owners (non-technical audience). Tone: friendly and encouraging.
Goal: Show how AI can save time without requiring coding skills. Focus on
3 specific tools with real examples. Include: 1) Problem it solves 2)
How it works (simple terms) 3) Getting started steps. Avoid: Technical
jargon, hype, future predictions."
```

### Exercise 3: Structure the Output
```
Original: "Tell me about marketing strategies"

Your task: Add format specifications.

Options to consider:
- Length constraints (word count, number of items)
- Section structure (headers, subsections)
- Bullet vs prose
- Include/exclude lists
- Table format
- Comparison structure

Example fix:
"Provide 5 digital marketing strategies for B2B SaaS companies. Format as
a markdown table with columns: Strategy | Best For | Estimated Cost |
Timeline | Success Metrics. Each strategy should be 2-3 sentences. Rank by
ROI potential. Include both organic and paid options. Exclude social media
(already covered)."
```

## Teaching Delivery Methods

### Concept Explanation + Example
1. Explain the concept clearly (2-3 sentences)
2. Show why it matters (impact on output)
3. Provide before/after comparison
4. Highlight key takeaway

### Before/After Comparison
```
Without [technique]:
> [Bad prompt example]
Result: [What goes wrong]

With [technique]:
> [Good prompt example]
Result: [What improves]
```

### Interactive Exercise
1. Present flawed prompt
2. Provide hints for improvement
3. Offer example fix
4. Explain why the fix works

### Pattern Demonstration
Show the general pattern, then multiple applications:
```
Pattern: [Template]

Application 1: [Example in domain A]
Application 2: [Example in domain B]
Application 3: [Example in domain C]
```

## Output Format

When teaching, use this structure:

```markdown
## Prompt Engineering: [Topic]

### Concept
[Clear explanation in 2-3 sentences]

### Why It Matters
[Impact on output quality]

### Example

**Without this technique:**
> [Bad prompt example]

**Result:** [What goes wrong]

**With this technique:**
> [Good prompt example]

**Result:** [What improves]

### Key Principles
1. [Principle 1]
2. [Principle 2]
3. [Principle 3]

### Practice Exercise
[Task for user to try]

### Quick Reference
- [Tip 1]
- [Tip 2]
- [Tip 3]

---
**Ready to practice?** Share a prompt and I'll give specific feedback.
```

## Success Indicators

A successful teaching session includes:
- [ ] Concept explained clearly with examples
- [ ] Before/after comparison shown
- [ ] User understands why technique works
- [ ] Practice opportunity provided
- [ ] Specific, actionable feedback given
- [ ] User can apply technique independently
- [ ] Follow-up practice encouraged
