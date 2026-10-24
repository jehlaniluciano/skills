---
name: orchestrate
description: Coordinate subagents for substantial work that benefits from parallel execution. Keep simple tasks with the root agent.
---

# Orchestrate

## Coordination

- Root: Keep the main chat's model and effort, remain available, and own integration, verification, and completion.
- Preserve user scope and authorization.

## Delegation

- Assess the outcome, requirements, acceptance checks, dependencies, and shared resources.
- Identify serial dependencies and independent work that can run in parallel.
- Root and non-leaf agents: Delegate when benefits exceed coordination, usage, and integration costs.
- Keep small or tightly coupled work solo, sequence dependencies, and batch simple independent lookups.
- When practical, isolate uncertain work from bounded work so each receives appropriate effort.
- Assign scope, ownership, dependencies, context, deliverables, and acceptance checks.
- Use one owner per shared resource and prohibit leaf delegation.
- Assign each agent a unique, task-relevant name of 1–3 words.
- Use spaces in output headings and underscores only in tool identifiers.
- Avoid conflicting or duplicate work and continue independent work while agents run.
- Require concise results, evidence, questions, verification limits, and artifact references.

## Reasoning effort

- Keep the root agent's model and effort unchanged.
- Use `gpt-6.1-sol` for implementation and investigation agents, explicit model/effort when supported, and `fork_turns: "none"` by default.

### Selection

For each non-fixed assignment, assess low → medium → high before dispatch. No trial run at lower effort is required.

1. Use `low` when work is explicit, bounded, and directly checkable with little interpretation: inventories, caller locations, comparisons, or prescribed edits.
2. Use `medium` when low is insufficient but requirements and acceptance checks are clear: defined features, workflow tracing, behavioral tests, verification scripts, or established fixes.
3. Use `high` when material uncertainty requires resolving competing explanations, conflicting requirements, or interacting failure paths beyond routine tracing.

- Medium can handle connected decisions across multiple files and configuration.
- Select by the subtask's decisions and uncertainty, not parent-task size, file count, importance, subject matter, or read-only status.
- Multiple steps or unfamiliar code do not alone require high.
- For non-fixed high assignments, identify the unresolved question or interaction that makes medium insufficient.
- Report uncertainty rather than infer behavior from search results alone.

### Reporting

- Before dispatch, report each assignment in commentary and the assignment message.
- Use a separate `### Agent: <name>` heading with the assigned name and spaces.
- Use three separate bullets labeled `Task:`, `Reasoning:`, and `Reason:`.
- Separate agent blocks with a blank line.
- Explain why lower effort is insufficient for non-fixed medium/high assignments.

```markdown
### Agent: package verification

- Task: Verify the saved image against release requirements.
- Reasoning: medium
- Reason: Requires a verifier that combines file, package, and configuration checks against clear expectations.

### Agent: recovery investigation

- Task: Determine whether crash recovery can repeat acknowledged work.
- Reasoning: high
- Reason: Conflicting persistence and retry contracts leave duplicate execution unresolved.
```

### Reassessment

- Reassess assignments and effort when diagnosis or new evidence changes scope, uncertainty, or interactions.
- A failed command or test alone does not require higher effort.

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
