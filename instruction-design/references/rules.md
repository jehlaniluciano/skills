# Persistent Agent Rules

- Inspect applicable instruction files, terminology, existing rules, and their callers before editing.
- Keep durable policy separate from temporary assignments and place rules at the narrowest applicable scope.
- Write actionable rules stating the trigger, required action, and material exceptions.
- Include only the context, constraints, and completion conditions relevant to each rule, and do not turn each rule into a full task prompt.
- Consolidate equivalent rules without merging distinct scopes.
- Reference documentation where needed without requiring unrelated reading.
- Keep shared policy in agent rules and substantial reusable workflows in skills.
- Fix skill descriptions and activation conditions instead of adding invocation rules to `AGENTS.md`.
- Check interactions with existing rules, including precedence and approval boundaries.
- Check an ordinary case, a material exception, and a scope boundary.
