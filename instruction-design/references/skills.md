# Skill Instructions

- Use `skill-creator` for packaging, metadata, resources, and validation.
- Inspect the existing skill, callers, and maintained copies before changing its scope or identity.
- Define precise capabilities and activation conditions that exclude unrelated tasks.
- Use the five sections defined in the main instruction-design skill, in that order, while preserving required YAML frontmatter.
- Apply the five sections to the skill document as a whole rather than to each rule or supporting reference.
- Include the skill's activation scope in Context and necessary procedures in Requirements and constraints.
- Keep shared guidance and ordinary workflows in `SKILL.md` and specialized procedures in linked references when appropriate.
- State when to read each reference without duplicating its content across sections.
- Include non-obvious operational requirements and failure boundaries.
- Keep project-specific terminology, examples, and resources in their owning project.
- Complete required validation and verify reference links and routing.
- When behavioral checks are warranted, assess outcomes for a representative request and a nearby request that should not activate the skill.
