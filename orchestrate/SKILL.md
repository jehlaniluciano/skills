---
name: orchestrate
description: Coordinate subagents for substantial work that benefits from parallel execution. Keep simple tasks with the root agent.
---

# Orchestrate

## Coordination

- Root: Keep the main chat's model and effort, remain available, and own integration, verification, and completion.
- Preserve user scope and authorization.

## Delegation

- Assess requirements, acceptance conditions, dependencies, and shared resources before splitting serial and parallel work.
- Root and non-leaf agents: Delegate early when benefits exceed coordination, usage, and integration costs.
- Keep small or tightly coupled work solo, sequence dependencies, and batch simple independent lookups.
- Assign scope, ownership, dependencies, context, deliverables, and acceptance conditions, with one owner per shared resource and no leaf delegation.
- Avoid conflicting or duplicate work and continue independent work while agents run.
- Require concise results, evidence, questions, verification limits, and artifact references.
- Reassess assignments and effort after diagnosis or reported scope/evidence changes.

## Reasoning effort

- Use `gpt-6.1-sol` for implementation and investigation agents, explicit model/effort when supported, and `fork_turns: "none"` by default.
- For non-fixed assignments, assess subtask decisions, uncertainty, interactions, and acceptance conditions before selecting the lowest sufficient effort.
- Assess low → medium → high before execution; no initial low-effort run is required.
- Use `low` for explicit, bounded, directly checkable work with little interpretation: inventories, caller locations, comparisons, or prescribed edits.
- Use `medium` for connected decisions within clear requirements: defined features, workflow tracing, behavioral tests, or established fixes.
- Use `high` for ambiguity, competing explanations, uncertain assumptions, or complex interactions: races, ownership boundaries, or conflicting behavioral/compatibility evidence.
- Select medium/high for behavioral conclusions beyond factual checks, and high when ambiguity or complex interactions determine the result.
- Select by subtask, not parent-task size, file count, importance, subject matter, or read-only status.
- Before dispatch, report each assignment in commentary and the assignment message under a separate `### Agent: <name>` heading, using the assigned agent name and three separate bullets labeled `Task:`, `Reasoning:`, and `Reason:`.
- Separate agent blocks with a blank line and explain why lower effort is insufficient for non-fixed medium/high assignments.
- Report uncertainty rather than infer behavior from search results alone.

```markdown
### Agent: deployment_review

- Task: Review deployment readiness.
- Reasoning: medium
- Reason: Readiness needs connected build and configuration checks, beyond an inventory.

### Agent: recovery_review

- Task: Review recovery and alerting.
- Reasoning: high
- Reason: Competing restart and alert paths require more than routine tracing.
```

## Verification

- Integrate results, resolve conflicts, and assess combined work against requirements.
- Finish relevant source, test, and configuration edits before combined verification, and keep source stable during verification and review.
- Run required checks at the smallest reliable scope and identify blocked checks and acceptance gaps.

## Independent review

- After implementation, integration, and checks finish, assign one independent final reviewer for substantial delegated work.
- Use `gpt-6.1-sol`, `reasoning_effort: "high"`, and `fork_turns: "none"` for all final and correction reviews.
- Supply requirements, acceptance conditions, source identity, combined changes, reports, verification evidence, questions, and limitations.
- Require inspection of actual changes and affected consumers for coverage, correctness, regressions, integration, and verification sufficiency, with focused checks where needed.
- Keep the reviewer independent of implementation and source edits, prohibit delegation, and require actionable findings, evidence, unresolved ambiguity, and a completion assessment.
- Fix confirmed findings within scope, select correction agents with the rubric, integrate corrections, rerun affected checks, and have corrections and their effects reviewed.
- Repeat checks or expand review only for relevant changes, failures, missing evidence, or unresolved concerns.

## Completion

- Complete only when review covers current source, acceptance conditions pass, and no blocking finding remains.
- Report results, verification, limitations, and remaining work without overstating completion.
