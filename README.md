# Agent Skill Land

A versioned, personal-friendly library for AI-agent skills: the skills currently in use, skills being evaluated, and adapted copies of skills imported from other projects.

This repository is **public**. Do not add credentials, private URLs, personal data, or instructions that would expose a private system.

## What lives here

- `skills/` — the usable, locally adapted skills. One folder per skill, with `SKILL.md` as the entrypoint.
- `catalog/skills.yml` — the source, license, import date, upstream revision, and current local version of every skill.
- `templates/skill-source.yml` — a record template for each imported or original skill.
- `.github/` — lightweight issue and pull-request scaffolding for deliberate changes.

## Add or adopt a skill

1. Check the upstream repository's license and review the skill before copying it.
2. Create `skills/<skill-name>/SKILL.md` and adapt it for your actual workflow.
3. Add or update that skill's entry in `catalog/skills.yml`, including the upstream URL, revision/tag, license, and what you changed.
4. Validate the metadata and test the skill in a fresh agent session.
5. Commit the change with a clear message. For a significant change, use a branch and pull request so GitHub preserves the review discussion.

## Versioning policy

Git is the source of truth:

- Every intentional change is a commit.
- Use focused commit messages: `add:`, `update:`, `fix:`, `docs:`, or `chore:`.
- Tag stable library snapshots as `vYYYY.MM.DD` (for example, `v2026.07.22`).
- Keep the upstream version/ref in the catalog so an adapted skill can be compared or refreshed later.
- Never overwrite history to hide a change; corrections are new commits.

## Skill status

| Status | Meaning |
| --- | --- |
| `active` | In regular use and maintained. |
| `trial` | Being evaluated; record review date and source. |
| `paused` | Kept for reference, not currently loaded. |
| `archived` | No longer recommended; retained for history. |

## First skill checklist

- [ ] Name is lowercase and hyphenated.
- [ ] `SKILL.md` begins with valid YAML frontmatter.
- [ ] Source, license, and upstream revision are captured in `catalog/skills.yml`.
- [ ] Local adaptations are described in the catalog entry.
- [ ] No secrets or private details are included.
- [ ] The change is committed.

## License

The repository's original material is available under the [MIT License](LICENSE). Imported skills remain subject to their original licenses; record those licenses in the catalog and preserve required notices.
