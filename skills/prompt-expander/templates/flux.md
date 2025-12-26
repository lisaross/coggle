# Flux Image Generation Templates

FLUX.1 (by Black Forest Labs) excels at photorealistic images and complex scenes. Unlike Midjourney, Flux prefers **natural language descriptions** over keyword stacking.

## Core Pattern

Write prompts as clear, descriptive sentences. Flux understands nuance and context.

### Basic Structure

```text
[Subject description], [action/pose], [environment/setting], [lighting], [style/mood]
```

### Example Prompts

**Photorealistic Portrait:**
```text
A weathered fisherman in his 60s mending nets on a wooden dock at dawn.
Soft golden light catches the silver in his beard. He wears a faded blue
sweater with frayed sleeves. Background shows calm harbor water with
fishing boats. Photorealistic, shallow depth of field, intimate portrait.
```

**Product Photography:**
```text
Luxury perfume bottle on a marble surface with soft morning light from
the left. Crystal-clear glass with amber liquid inside. Subtle reflections
and caustics. Minimalist composition with negative space. Commercial
photography style, 4K, sharp focus on the bottle.
```

**Concept Art:**
```text
Ancient library floating among clouds, massive stone columns covered in
glowing runes. Scholars in flowing robes walk between towering bookshelves.
Warm candlelight contrasts with cool blue sky visible through arched
windows. Epic fantasy concept art, detailed architecture, atmospheric
perspective.
```

**Abstract/Artistic:**
```text
Abstract representation of consciousness—flowing ribbons of light in
deep blue and gold, forming loose neural network patterns. Particles of
light scatter at connection points. Dark background, ethereal glow,
contemporary digital art style.
```

## Key Principles

1. **Use natural language**: Write like you're describing to an artist, not a search engine
2. **Be specific about lighting**: Golden hour, studio lighting, dramatic shadows, etc.
3. **Describe mood and atmosphere**: Not just objects, but how they feel
4. **Specify camera/composition**: Wide shot, close-up, rule of thirds, etc.
5. **Include style references**: Photorealistic, oil painting, anime, concept art

## PRECISE Adaptations

| Element | Flux Approach |
| ------- | ------------- |
| Persona | Style reference (artist, genre, era) |
| Requirements | Core visual elements that must appear |
| Examples | Reference images via image-to-image |
| Context | Scene setting, time of day, weather |
| Instructions | Composition, camera angle, focus |
| Specifications | Aspect ratio, style, quality level |
| Evaluation | Coherence, realism, mood accuracy |

## FLUX.1 Variants

- **schnell**: Fast generation, good for iteration
- **dev**: Higher quality, better for final outputs
- **pro**: Best quality, most expensive

## Technical Parameters

Unlike Midjourney, Flux uses standard image gen parameters:

- **Guidance scale**: 3.5-7.5 typical (higher = more prompt adherence)
- **Steps**: 20-50 (more = more detail, slower)
- **Aspect ratio**: Specify in words ("landscape 16:9", "square", "portrait 9:16")

## Prompt Structure Tips

**Layered Description:**
```text
Subject: [main focus]
Setting: [environment details]
Lighting: [light source, quality, direction]
Atmosphere: [mood, weather, time]
Style: [artistic style, medium]
Technical: [camera, composition, quality]
```

**Example using structure:**
```text
Subject: Young woman with short silver hair reading a leather-bound book
Setting: Cozy window seat in a Victorian library, rain on the windows
Lighting: Soft diffused daylight mixed with warm lamp glow
Atmosphere: Contemplative, quiet, rainy afternoon mood
Style: Realistic digital painting with soft edges
Technical: Medium shot, shallow depth of field, warm color palette
```

## Anti-Patterns

- **Avoid**: Keyword stacking like Midjourney ("8k, hyper detailed, trending")
- **Avoid**: Conflicting style descriptions in same prompt
- **Avoid**: Vague descriptions ("a nice scene")
- **Avoid**: Forgetting to specify aspect ratio when it matters
