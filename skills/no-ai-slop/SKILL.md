---
name: no-ai-slop
description: Use when revising a draft to sound clearer and more human, while keeping the writer's voice and meaning intact, or when auditing specific AI-writing patterns without rewriting.
version: 0.1.0
author: Peter Yang, adapted by awsm-vanessa
license: MIT
metadata:
  hermes:
    tags: [writing, editing, voice, anti-ai-slop]
    related_skills: [humanizer]
---

# No AI slop

Edit writing into sharper, more natural prose without sanding away the writer's personality. This is a targeted editing skill, not a detector of who or what wrote a draft.

## When to use

- The user asks for a draft to be clearer, less generic, or less AI-sounding.
- The user wants a pattern audit without a rewrite.
- The user wants a minimal, voice-preserving polish before publishing.

Do not apply it automatically to intimate, emotional, or deliberately stylized writing. Ask first when the writer's intent or audience is unclear.

## Two modes

**Edit (default).** Make the minimum effective changes. Return the complete edited draft, then a short **What changed** section.

**Detect.** When asked to audit, scan, or flag a draft without rewriting, name each pattern found, quote the relevant line, and suggest a brief fix. Do not score the writing, claim that AI wrote it, or rewrite it unless asked.

## Guardrails

1. Preserve the user's meaning. Do not invent facts, examples, statistics, sources, quotations, or opinions.
2. Preserve voice: notice vocabulary, cadence, bluntness, humor, uncertainty, digressions, punctuation, and level of polish. A rough but distinctive draft should still sound like its writer.
3. Treat the word and pattern lists below as **signals, not automatic deletions**. An intentional word, fragment, metaphor, or aside may belong.
4. Ask one focused question if the goal, audience, format, or a factual claim is genuinely unclear.
5. Keep culturally specific language, technical terms, direct quotations, and required house style unless the user asks to change them.

## Editing principles

- Lead with the point when the setup adds nothing. Keep setup that provides context, tension, or character.
- Prefer concrete facts, named actors, direct verbs, and plain claims when the draft supports them.
- Use active voice where it makes the actor clearer. Do not force it where passive voice is intentional or more accurate.
- Untangle genuinely hard-to-follow sentences, but keep clear spoken cadence, fragments, and varied pacing.
- Keep useful edge: opinions, humor, profanity, honest admissions, and self-interruptions can be part of a human voice.
- Preserve structure unless it is confusing or redundant. Explain any material reorganization in **What changed**.

## Patterns to examine

Check the draft in context for these common patterns:

- **Throat-clearing or rhetorical setup:** “Here’s the thing,” “What nobody tells you,” “Think about it,” or a self-answered question before the real point.
- **Binary contrast or negative listing:** “It’s not X. It’s Y.” or “Not X. Not Y. Z.” when a direct statement would be stronger.
- **Importance puffery:** claims that something “marks a pivotal moment,” “underscores its significance,” or “stands as a testament,” without concrete evidence.
- **Vague authority:** “experts agree,” “studies show,” or “many argue” without a named, supplied source.
- **Fake-strength language:** inflated verbs and abstractions such as “serves as a centralized hub,” where a simple description is clearer.
- **Synonym cycling:** changing a clear term merely to avoid repeating it.
- **Superficial explanation:** trailing “highlighting,” “underscoring,” or “reflecting” clauses that add no mechanism or fact.
- **Decorative formatting:** emoji headings, excessive bold, bullets used where short prose is clearer, or headings over tiny sections.
- **Performative rhythm:** stacked fragments, repeated sentence shapes, decorative em dashes, or a forced mic-drop ending.
- **Generic filler:** phrases such as “at its core,” “in today’s world,” “it’s worth noting,” or “let’s dive in” when they delay the point.
- **Inflated vocabulary:** words such as “delve,” “leverage,” “robust,” “transformative,” or “ever-evolving” when a plainer word says the same thing.

## Workflow

1. Read the entire draft before changing anything.
2. Identify the core point and three to five voice signals to preserve. Keep this note internal.
3. In detect mode, report only the specific patterns found, quoted evidence, and a short possible fix. Stop there.
4. In edit mode, make the minimum effective edit.
5. Check the result against [the evaluation checklist](references/eval.md). If a check fails, revise before responding.
6. Return the full edited draft and a short **What changed** section.

## Source and local adaptation

Adapted from Peter Yang’s MIT-licensed `no-ai-slop` skill at commit `61c21c351da4dcb40946a11fead978f2078a2c65`. This local version removes platform-specific configuration, makes the pattern list advisory rather than absolute, and adds explicit guardrails for voice, cultural language, and emotionally personal writing. See `catalog/skills.yml`, `reviews/no-ai-slop-review-2026-07-22.md`, and this folder’s `LICENSE`.

## Verification checklist

- [ ] Meaning and facts were preserved.
- [ ] Voice and intentional texture remain recognizable.
- [ ] Every change addresses a specific clarity, accuracy, or pattern issue.
- [ ] No source, claim, or certainty was invented.
- [ ] Detect mode did not speculate about authorship.
- [ ] The final output contains the complete draft and a concise change summary.
