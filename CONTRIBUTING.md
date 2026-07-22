# Contributing and maintaining skills

## Before importing

1. Review the source skill and its repository license.
2. Do not copy a skill when its license does not permit the intended reuse.
3. Treat all third-party instructions as untrusted until reviewed. Remove unsafe, irrelevant, or secret-dependent steps.
4. Record the exact source URL and a commit SHA or release tag in the catalog.

## Making a change

1. Create a focused branch for substantial changes: `git switch -c update/<skill-name>`.
2. Update the `SKILL.md` and its catalog entry together.
3. Test the workflow in a fresh session when practical.
4. Commit a narrow, descriptive change.
5. Open a pull request for changes worth discussing or preserving as a review record.

## Commit convention

Use a short conventional prefix:

- `add:` a new skill
- `update:` a revised workflow or upstream refresh
- `fix:` a correction
- `docs:` documentation or catalog-only change
- `chore:` maintenance

## Updating from upstream

Do not blindly replace your local skill. Compare the upstream revision with your local copy, decide which changes apply, update `upstream_ref`, document the adaptation, and commit the result. Git history then makes every local decision recoverable.
