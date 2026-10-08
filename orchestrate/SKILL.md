---
name: orchestrate
description: Coordinate multiple agents on substantial implementation, investigation, or review tasks. Keep small or tightly coupled tasks with one agent when delegation adds unnecessary overhead.
---

# Orchestrate

## Scope and responsibility

- Use `gpt-6.1-sol` at `medium` effort for root coordination.
- Root agent: Own integration, conflict resolution, required verification, and completion.
- Root agent: Remain available to the user during delegated work.
- Preserve the user's scope, requirements, and authorization.

## Delegation

- Root and non-leaf agents: Delegate independent subtasks when time or quality gains justify coordination and usage costs.
- Keep small or tightly coupled tasks with one agent when delegation adds unnecessary overhead.
- Run independent, read-only exploration tasks in parallel.
- Avoid conflicting edits and duplicate work.

## Model and effort selection

- Before each spawn, assess the subtask's required decisions, uncertainty, affected behavior, and deliverable.
- Use `gpt-6.1-sol` for implementation and investigation subagents.
- Except for the fixed final reviewer, select the lowest effort that supports the required analysis and acceptance conditions.
- Select effort from the assigned subtask rather than the parent task.
- Do not classify work as low effort merely because it is read-only.
- Pass `model` and `reasoning_effort` explicitly when the tool permits overrides.
- Coordinator: Select effort and include one brief reason in the assignment.
- For high or above, name the unresolved decision or interaction and explain why medium effort may be insufficient.
- Do not justify high effort solely through file count, task importance, or subject matter.
- Example: "High: Recovery and reconnect can overlap, which requires analysis of competing paths that could duplicate command effects."
- Subagents: Report evidence or scope changes that could require a different effort level.
- Coordinator: Reassess effort after diagnosis and when evidence or scope changes.
- Apply revised effort to subsequent assignments when the tool permits overrides.

### Low

- Use `low` when the task is bounded, requirements are explicit, and little interpretation is necessary.
- Use it for targeted searches, factual extraction, prescribed replacements, and mechanical checks.
- Examples include locating callers, extracting toolchain versions, checking file equality, or applying an approved label change.
- Return unresolved questions rather than infer behavior from search results alone.

### Medium

- Use `medium` when clear requirements require several connected decisions or checks.
- Use it for routine implementation, bounded research, test development, and debugging with an established failure.
- Default to medium for bounded implementation and corrections once the cause, solution, and acceptance conditions are established.
- Examples include implementing a defined feature, tracing a known workflow, or planning corrections for established findings.

### High

- Use `high` when unresolved ambiguity or complex interactions require substantial analysis.
- Use it for unclear failure causes, competing hypotheses, consequential boundary changes, and difficult compatibility decisions.
- Examples include diagnosing recovery races, tracing account isolation failures, or resolving conflicting behavioral evidence.

## Assignment

- Default to `fork_turns: "none"`.
- Give each subagent clear scope, deliverables, ownership boundaries, relevant context, and acceptance conditions.
- Instruct leaf subagents not to delegate.
- Require results, supporting evidence, unresolved questions, and verification limits.
- Write readable agent messages with proper word and number spacing.

## Integration and verification

- Confirm that all contributing agents have finished relevant source, test, and configuration edits before combined verification.
- Review and integrate subagent results.
- Resolve conflicts and assess the combined changes against the user's requirements.
- Complete required checks at the smallest reliable scope.
- Repeat checks only for relevant changes, failures, missing evidence, or unresolved concerns.
- Identify blocked checks and remaining acceptance gaps.
- Keep the source stable during combined verification and final review.

## Final review

- After implementation, integration, and required checks finish, spawn one independent final reviewer for substantial delegated work.
- Use `model: "gpt-6.1-sol"`, `reasoning_effort: "xhigh"`, and `fork_turns: "none"`.
- Keep final review at xhigh without effort selection, including review of subsequent corrections.
- Provide the user's requirements, acceptance conditions, source identity, combined changes, verification evidence, and known limitations.
- Include unresolved questions and contributing agents' reports.
- Have the reviewer inspect actual changes and affected consumers rather than rely solely on agent reports.
- Have the reviewer assess requirement coverage, correctness, regressions, integration, and verification sufficiency.
- Permit focused checks where existing evidence is insufficient.
- Have the reviewer return actionable findings, supporting evidence, unresolved ambiguity, and whether the evidence supports completion.
- Keep the reviewer independent of implementation and shared-source edits.
- Instruct the reviewer not to delegate.

## Corrections

- Root agent: Resolve confirmed findings within the authorized scope.
- Select correction agents through the model and effort criteria.
- Integrate corrections and repeat affected checks.
- Have the reviewer review corrections and their effects before completion.
- Expand review only when changes or unresolved concerns justify it.

## Completion

- Confirm that final review covers the current source.
- Complete only when required acceptance conditions pass and no unresolved finding prevents completion.
- Report completed work, verification evidence, and material limitations.
- If findings or required checks remain unresolved, report the remaining work without claiming completion.
