---
name: instruction-design
description: Create, revise, or review model prompts, agent rules such as AGENTS.md, and skill instructions.
---

# Instruction Design

## Goal

- Create, revise, or review prompts, agent rules, and skill instructions that define the intended result while preserving useful freedom to choose the method.

## Context

### Scope and routing

- Use this skill for instruction authoring, including model and subagent assignments, rather than merely reading rules or using skills.
- Leave ordinary reply style to the configured hook and response instructions.
- For ordinary prompts, use this file without specialized references.
- For `AGENTS.md` rules, also read [references/rules.md](references/rules.md).
- For skills, also read [references/skills.md](references/skills.md).

### Model guidance

- Apply relevant [GPT-6 guidance](https://developers.openai.com/api/docs/guides/latest-model#prompting-best-practices) for the requested model, reusing verified guidance while applicable.
- Refresh official guidance when the model or context changes or material uncertainty remains.
- Skip guidance review for typo or formatting changes unless requested.
- Treat GPT-6 Astra observations as starting points to evaluate with the chosen model and workload.
- Calibrate verification to affected behavior and delegation to independent work when relevant.

## Requirements and constraints

### Structure by instruction type

- For task prompts and skills, define Goal (intended result), Context (relevant facts, sources, and inputs), Requirements and constraints (required behavior, limits, and authorization boundaries), Success criteria (completion evidence), and Output (deliverables and format).
- For simple task prompts, combine these elements without requiring separate headings.
- For agent rule files such as `AGENTS.md`, write individual actionable rules under useful topic headings without imposing the five-section structure on the file or each rule.
- For `SKILL.md`, use the five sections at the document level as specified in [references/skills.md](references/skills.md).

### Instruction design

- Tailor instructions to the recipient and task using the request and applicable instructions.
- Apply only the design elements relevant to the instruction type and scope.
- For prompts and skills, inherit autonomy and general workflow rules from applicable agent instructions, and include only task-specific or skill-specific additions or exceptions.
- When verification matters, specify required checks, evidence, and stopping criteria.
- Define when to assume, ask, continue, or stop when ambiguity or side effects materially affect the task.
- For delegated work, specify ownership, dependencies, and evidence needed for integration.
- Preserve existing authorization without inventing approvals or granting unavailable authority or tool access.
- Let the model choose its method unless correctness, permissions, or fragile operations require a procedure.
- Use only context, structure, and examples that help achieve the requested result.
- Separate instructions from source material and keep examples consistent with requirements.
- Do not add unsupported requirements or turn isolated examples into universal rules.
- When needed, request evidence, calculations, or concise rationale instead of private reasoning traces.

### Clear wording and preservation

- Preserve scope, conditions, exceptions, uncertainty, requirement strength, quantities, authorization boundaries, and required sequence.
- Preserve exact code, commands, identifiers, quotations, links, and controlled wording.
- Preserve behavior outside the requested scope.
- Use ASD-STE100 clarity principles: plain language, direct verbs, active voice, and short, complete sentences.
- Write direct, actionable rules with one sentence per bullet when the format permits.
- Order instructions by when they apply when sequence matters; keep independent rules grouped by topic without implying a required procedure.
- Use the fewest words that preserve the full requirement, removing repetition, filler, and unnecessary jargon.
- Use established shorthand when understood and permitted, defining unfamiliar terms once and using them consistently.
- Put conditions before actions and identify the actor.
- State each requirement once in one maintained location.
- When renaming, update affected callers, links, metadata, and maintained copies.

## Success criteria

- Compare revisions with the original requirements and check applicable instructions for conflicts, unnecessary procedures, and unintended approval pauses.
- Keep unconditional requirements outside conditional branches and verify each branch preserves its original requirements.
- For conditional prompts, obtain independent preservation review against original requirements, then resolve findings and have corrections rechecked before delivery.
- When warranted, use representative cases to check outcomes, useful autonomy, and stopping behavior.
- When authoring or reviewing a skill, verify that its instructions use the five sections required by [references/skills.md](references/skills.md).

## Output

- Deliver the requested instructions in the requested format without creating unrequested files.
- Report material verification gaps without claiming that this skill or readability checks establish formal ASD-STE100 compliance.
