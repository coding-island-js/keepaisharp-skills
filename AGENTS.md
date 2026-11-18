# Notes for agents editing this repo

- Each skill lives in `skills/<name>/SKILL.md`. The `name:` field must equal the folder name.
- Frontmatter uses only the standard fields from https://agentskills.io/specification: `name` and `description` (required), plus optional `license` and `metadata`.
- The `description` says what the skill does AND when to use it, in the words a user would type. Agents read only this line before deciding to load the skill.
- Keep each `SKILL.md` under 500 lines. Put long material in `skills/<name>/references/` and link it one level deep.
- Write for a stranger: no personal paths, names, private tools or links to files outside the skill folder.
- When you add a skill, add it to the table in `README.md` and to the `skills` list in `.claude-plugin/marketplace.json`.
