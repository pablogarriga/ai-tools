---
name: repo-setup
description: Bootstrap a new or lightly structured repository with standard project docs and working conventions. Use when a user wants to initialize repo structure, add a root README, add AGENTS.md, add logs/session-log.md, add a repo-local skills scaffold, or apply an existing starter repo's conventions without blindly copying its auxiliary template folders.
---

# Repo Setup

## Overview

Set up a repository with a lightweight, reusable working structure. Inspect the existing repo first, then adapt the scaffold to the actual project instead of dropping in generic placeholders unchanged.

## Workflow

1. Inspect the repository before editing anything.
   Look for existing `README*`, `AGENTS.md`, `.editorconfig`, `logs/`, `skills/`, top-level source folders, analysis folders, package manifests, notebooks, and project docs.

2. Infer the repo's actual purpose from local evidence.
   Prefer the current codebase, documents, and folder names over assumptions. If the user references another repo as a model, treat that repo as a source of conventions unless they explicitly ask to copy directories verbatim.

3. Propose or apply the minimum scaffold that belongs in the current repo.
   Default scaffold:
   - root `README.md`
   - root `AGENTS.md`
   - root `.editorconfig`
   - `logs/session-log.md`
   - `skills/README.md`
   - `skills/template/SKILL.md`

4. Do not import auxiliary template repositories literally unless the user asks for that.
   In particular, if the reference repo contains a `templates/` folder, use it as source material for writing the current repo's real files. Do not copy the `templates/` folder into the target repo unless the user explicitly requests it.

5. Adapt every file to the current repo.
   Replace placeholders with repo-specific content:
   - project purpose
   - language/tooling stack
   - relevant run commands
   - workflow constraints
   - important directories
   - testing or validation expectations
   - formatting conventions when they matter for day-to-day editing

6. Preserve existing work.
   If the repo already has a `README.md`, `AGENTS.md`, `.editorconfig`, `logs/`, or `skills/`, update them carefully instead of overwriting them wholesale. Do not remove user-authored content without a clear reason.

7. Keep the scaffold lean.
   Do not add extra docs such as changelogs, installation guides, or copied template archives unless the user requested them.

8. Validate the result.
   Check that:
   - the created files match the repo's actual contents
   - no unintended directories from the starter repo were imported
   - `git status` shows only the intended additions or edits

## File Guidance

### `README.md`

Write a concise project-level README that explains:
- what the repo is for
- the main workflow or outputs
- the important directories
- how to run or work in the repo, if known
- key constraints or open questions

If commands are unclear, state that setup is partial rather than inventing a full install flow.

### `AGENTS.md`

Write agent instructions specific to the repo. Include:
- project context
- what agents should optimize for
- rules for safe edits
- how to validate changes
- repo-specific constraints

Anchor the guidance in the current codebase instead of generic software-project language when the repo is research, data, or document heavy.

### `.editorconfig`

Create a lightweight root `.editorconfig` when the repo does not already have a stronger formatter-driven setup. At minimum, prefer spaces over tabs and make the intended indentation width explicit. If the repo already documents formatting conventions, keep `.editorconfig` aligned with them.

### `logs/session-log.md`

Create one reverse-chronological session log. Prepend the newest entry first. Use `YYYY-MM-DD HH:MM` headings and concise bullets.

### `skills/`

Create a minimal repo-local skills scaffold only:
- `skills/README.md`
- `skills/template/SKILL.md`

Do not populate extra repo-local skills unless the user asks for them.

## Output Expectations

After bootstrapping, report:
- which files were added or updated
- which starter-repo conventions were adopted
- which things were intentionally not copied
- any validation performed
- any unresolved repo-specific gaps
