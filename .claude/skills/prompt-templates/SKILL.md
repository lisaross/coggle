---
name: prompt-templates
description: PROVIDE ready-to-use prompt templates for common use cases across analysis, creation, technical, and strategy domains. Use when user needs starting point, wants best-practice patterns, or asks for prompt examples. Triggers on "prompt template", "give me a template", "example prompt for", "how should I prompt for", "template for".
---

# Prompt Templates

Provide ready-to-use, production-quality prompt templates for common use cases. Templates follow best practices and include placeholders for customization.

## Trigger Phrases

Users invoke this skill by saying:
- "prompt template"
- "give me a template"
- "example prompt for"
- "how should I prompt for"
- "template for"

## When to Use This Skill

Use this skill when:
- User needs a starting point for a prompt
- Wants to follow best-practice patterns
- Asks for examples for specific use cases
- Needs inspiration for structuring a prompt

## Template Categories

### 1. Analysis Templates

Templates for evaluating, reviewing, or assessing something.

**Available Templates:**
- Market Analysis
- Code Review
- Competitive Analysis
- Risk Assessment

### 2. Creation Templates

Templates for generating new content or artifacts.

**Available Templates:**
- Content Writing (blog posts, articles)
- Email Drafting
- Social Media Posts
- Documentation

### 3. Technical Templates

Templates for software development and architecture.

**Available Templates:**
- API Design
- Database Schema
- System Architecture
- Test Plan

### 4. Strategy Templates

Templates for decision-making and planning.

**Available Templates:**
- Decision Framework
- Project Planning
- Stakeholder Analysis
- SWOT Analysis

## Workflow

### Step 1: Identify Use Case

**Actions:**
- Understand what the user wants to accomplish
- Determine which category fits best
- Select the most appropriate template

**Decision Points:**
- If user asks for multiple categories → Provide category overview first
- If use case is unclear → Ask clarifying questions
- If no exact match → Suggest closest template and note customizations needed

### Step 2: Present Template

**Format:**
```markdown
## [Template Name]

**Use Case:** [When to use this template]

**Template:**
```
[Full template with [PLACEHOLDERS]]
```

**Customization Guide:**
1. Replace [PLACEHOLDER1] with [guidance]
2. Replace [PLACEHOLDER2] with [guidance]
3. Optional: [Optional elements and when to include]

**Example Usage:**
[Concrete example with placeholders filled in]
```

### Step 3: Provide Usage Instructions

**Standard instructions for all templates:**

1. Copy the template
2. Replace [PLACEHOLDERS] with specific details
3. Remove sections not applicable to your use case
4. Add context specific to your situation
5. (Optional) Run through prompt-expander for final optimization

## Template Library

### Market Analysis Template

```
Act as a market research analyst with 10+ years of experience in [INDUSTRY].

Analyze the market opportunity for [PRODUCT/SERVICE] considering:

1. Market Size & Growth
   - Current TAM, SAM, SOM
   - Growth rate projections (3-5 years)
   - Key drivers and headwinds

2. Competitive Landscape
   - Top 5 competitors with strengths/weaknesses
   - Market share distribution
   - Differentiation opportunities

3. Customer Segments
   - Primary target personas (3)
   - Pain points and needs
   - Willingness to pay

4. Entry Strategy
   - Recommended go-to-market approach
   - Key success factors
   - Risks and mitigations

Format: Executive summary (200 words) + detailed sections with bullets
Include: Data sources and confidence levels for key claims
```

### Code Review Template

```
Act as a senior software engineer specializing in [LANGUAGE/FRAMEWORK].

Review the following code for:

1. **Bugs & Logic Errors**
   - Runtime issues
   - Edge cases not handled
   - Race conditions or memory issues

2. **Security Vulnerabilities**
   - Input validation gaps
   - Authentication/authorization issues
   - Data exposure risks

3. **Performance**
   - Algorithmic complexity concerns
   - Unnecessary operations
   - Caching opportunities

4. **Code Quality**
   - Readability and naming
   - DRY violations
   - Pattern adherence

Format each issue as:
- **Severity:** Critical/High/Medium/Low
- **Location:** File:Line
- **Issue:** Description
- **Fix:** Recommended solution
- **Code:** Corrected snippet if applicable

Code to review:
[PASTE CODE]
```

### Content Writing Template

```
Act as a professional content writer specializing in [NICHE].

Write a [CONTENT TYPE] about [TOPIC] for [AUDIENCE].

Requirements:
- Tone: [professional/casual/authoritative/friendly]
- Length: [word count] words
- Purpose: [inform/persuade/entertain/educate]
- CTA: [desired action]

Structure:
1. Hook - Grab attention in first sentence
2. Problem - Establish the pain point
3. Solution - Present the value
4. Proof - Include evidence/examples
5. CTA - Clear next step

Include:
- [Number] subheadings using H2 format
- [Number] bullet points for key takeaways
- [Number] statistics or data points (cite sources)

Avoid:
- Jargon unless defined
- Passive voice where possible
- Claims without support

SEO Keywords to include naturally: [KEYWORDS]
```

### Email Drafting Template

```
Act as a professional communication specialist.

Write an email for: [PURPOSE]

Context:
- Sender: [Role/Name]
- Recipient: [Role/Name, relationship]
- Situation: [Background]
- Goal: [Desired outcome]
- Tone: [formal/semi-formal/friendly]

Structure:
1. Subject line (under 50 chars, compelling)
2. Greeting (appropriate formality)
3. Opening (context in 1-2 sentences)
4. Body (key message, 2-3 paragraphs max)
5. CTA (specific and actionable)
6. Closing (professional sign-off)

Constraints:
- Total length: Under [X] words
- No jargon or buzzwords
- Easy to skim (use bullets if >3 points)
```

### API Design Template

```
Act as a senior API architect with REST/GraphQL expertise.

Design an API for: [FEATURE/SERVICE]

Requirements:
- Protocol: [REST/GraphQL/gRPC]
- Authentication: [method]
- Rate limiting: [requirements]
- Versioning: [strategy]

For each endpoint, provide:
1. Method & Path (REST) or Query/Mutation (GraphQL)
2. Request payload with types
3. Response payload with types
4. Error responses (4xx, 5xx)
5. Example curl command

Consider:
- Pagination for list endpoints
- Filtering and sorting options
- Partial updates (PATCH semantics)
- Idempotency keys where needed

Output: OpenAPI 3.0 spec in YAML format
```

### Database Schema Template

```
Act as a database architect specializing in [SQL/NoSQL].

Design a schema for: [SYSTEM/FEATURE]

Requirements:
- Database: [PostgreSQL/MySQL/MongoDB/etc]
- Expected scale: [rows/documents, growth rate]
- Query patterns: [list main access patterns]
- Consistency requirements: [strong/eventual]

For each table/collection:
1. Name and purpose
2. Fields with types and constraints
3. Primary key strategy
4. Indexes with justification
5. Foreign key relationships

Include:
- Normalization decisions with rationale
- Denormalization for performance where needed
- Partitioning/sharding strategy if applicable
- Migration scripts (CREATE statements)
```

### Decision Framework Template

```
Act as a strategic advisor with expertise in [DOMAIN].

Help decide: [DECISION TO MAKE]

Context:
- Current situation: [background]
- Constraints: [time/budget/resources]
- Stakeholders: [who's affected]
- Success criteria: [what good looks like]

Analyze options using:

1. **Option Identification**
   - List all viable options (min 3)
   - Include status quo if applicable

2. **Evaluation Criteria**
   - Define 5-7 weighted criteria
   - Score each option (1-5)

3. **Risk Assessment**
   - Key risks per option
   - Likelihood and impact
   - Mitigations available

4. **Recommendation**
   - Recommended choice with rationale
   - Implementation steps
   - Success metrics to track

Format: Decision matrix table + narrative analysis
```

## Template Selection Guide

**By Goal:**
- Understand something → Analysis templates
- Create something → Creation templates
- Build something → Technical templates
- Decide something → Strategy templates

**By Domain:**
- Business → Market Analysis, Decision Framework
- Writing → Content Writing, Email Drafting
- Development → Code Review, API Design, Database Schema
- Product → Competitive Analysis, User Research

## Success Indicators

This skill is successful when:
- [ ] User's need has been matched to appropriate template
- [ ] Template provided with all placeholders clearly marked
- [ ] Customization instructions included
- [ ] Usage example shown (if helpful)
- [ ] User can immediately start customizing the template

## Quality Checklist

Before marking complete, verify:
- [ ] Template category matches user's use case
- [ ] All placeholders use [BRACKET] format
- [ ] Customization guide explains each placeholder
- [ ] Template follows PRECISE methodology (Persona, Requirements, etc.)
- [ ] Example usage provided for complex templates
- [ ] Template is production-ready (not just an outline)

## Integration Points

**Works with:**
- `prompt-expander` - Use template as starting point, then expand further
- `prompt-analyzer` - Analyze customized template for quality
- `prompt-formatter` - Format template for specific export needs

---

*Prompt Templates skill | Created: 2025-12-26*
