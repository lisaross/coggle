# Coggle Component Integrations

This document maps how Coggle components work together. Individual skills no longer need "Integration Points" sections - refer here instead.

## Dependency Flow

```
/coggle command
├── prompt-expander agent → prompt-expander skill
├── prompt-analyzer agent → prompt-analyzer skill
├── prompt-coach agent → prompt-coach skill
├── prompt-compare agent → prompt-compare skill
├── (direct) → prompt-templates skill
└── (direct) → prompt-formatter skill
```

## Skill Integration Matrix

| From | To | When |
|------|-----|------|
| prompt-expander | prompt-formatter | After expanding, to export in different formats |
| prompt-expander | prompt-analyzer | To validate expansion quality |
| prompt-analyzer | prompt-expander | When weak prompt needs improvement |
| prompt-compare | prompt-analyzer | Uses 7-dimension scoring for both prompts |
| prompt-templates | prompt-expander | Template as starting point for expansion |
| prompt-coach | all skills | References other skills during teaching |

## Cross-References

| Concept | Source of Truth | Referenced By |
|---------|-----------------|---------------|
| PRECISE framework | prompt-expander skill | prompt-coach |
| 7-dimension scoring | prompt-analyzer skill | prompt-compare, prompt-coach |
| Anti-patterns list | prompt-analyzer skill | prompt-coach |
| Export formats | prompt-formatter skill | prompt-expander (post-expansion options) |

## Typical Workflows

### Basic Expansion
1. `/coggle [prompt]` → prompt-expander → expanded prompt
2. Choose: Run / Save / Analyze

### Quality Improvement
1. `/coggle analyze [prompt]` → prompt-analyzer → quality report
2. If score < 45: `/coggle [prompt]` to expand

### Template-Based Expansion
1. `/coggle template [cat] [type]` → get template
2. Fill placeholders, then `/coggle [filled template]`

### Comparison & Selection
1. `/coggle compare [A] vs [B]` → side-by-side analysis
2. Winner can be saved or run
