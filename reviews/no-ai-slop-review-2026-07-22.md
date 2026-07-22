# Review: no-ai-slop

- **Source:** https://github.com/petergyang/no-ai-slop
- **Reviewed commit:** `61c21c351da4dcb40946a11fead978f2078a2c65`
- **Date:** 2026-07-22
- **License:** MIT
- **Verdict:** Safe to test, with local adaptation

## What was reviewed

The repository at the pinned commit contained five tracked text/configuration files:

- `SKILL.md`
- `eval.md`
- `agents/openai.yaml`
- `README.md`
- `LICENSE`

No scripts, executables, binaries, submodules, package manifests, hooks, or installers were present. The only URLs were documentation/source links. The native `hermes skills inspect` preview completed on the commit-pinned raw `SKILL.md` URL.

## History and integrity

Eight commits from one contributor were reviewed. The security-relevant functional change removed a prior instruction to use editor/evaluator subagents and replaced it with a self-check against `eval.md`; no persistence, external calls, credential access, or tool-permission expansion appeared. `git fsck --full` completed without integrity findings. The repository has no tags or releases, and commits are not cryptographically signed, so the exact reviewed commit SHA is the provenance anchor.

## Security findings

No material security issue found in the reviewed content. It does not instruct the agent to access secrets, credentials, browser data, private files, networks, packages, background services, or destructive system commands.

## Behavioral-fit cautions

The upstream skill is intentionally strict about certain words and patterns. Mechanical use could erase legitimate style, personal voice, culturally specific language, or deliberate rhetorical choices. The local adaptation treats those lists as signals, preserves intentional texture, and keeps the skill opt-in for personal or emotionally significant writing.

## Trial and rollback

Status is `trial` through 2026-07-29. To stop using it, set its catalog status to `archived` or delete `skills/no-ai-slop/` in a new commit; Git history preserves the reviewed copy and provenance.
