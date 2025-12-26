# Google Gemini Prompting Templates

## Core Pattern
Gemini excels with few-shot examples and multimodal inputs. Keep temperature at 1.0 default.

### Few-Shot Template
```
Task: [Description]

Example 1:
Input: [example input]
Output: [example output]

Example 2:
Input: [example input]
Output: [example output]

Now complete:
Input: [actual input]
Output:
```

### Multimodal Template
```
<image>[image description or reference]</image>

Analyze this image and:
1. [Task 1]
2. [Task 2]

Output format: [structure]
```

### Key Principles
- Always include 2-3 examples (few-shot > zero-shot)
- Use XML tags or markdown for structure
- Treat text, images, audio, video as equal inputs
- Direct instructions work better than hints
