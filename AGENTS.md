# Contributor instructions

## Purpose and structure

This repository contains Orbitali guides and tutorials in US English, Spain Spanish,
and Italian.

- Keep `toc_en.md`, `toc_es.md`, and `toc_it.md` in the repository root. The website
  parses these files: use a heading followed by a flat Markdown bullet list,
  never a table. Put each entry on one line in the format
  `- [Title](relative/path.md): Description`.
- Use one descriptive, lowercase, hyphenated folder per guide.
- Each guide folder contains `en.md`, `es.md`, `it.md`, and an `images/` directory.
- Keep links portable: use relative paths for images, locale links, and TOC links.
- Add or update the corresponding entry in all three TOCs when adding or renaming
  a guide.

## Writing and localization

- Write practical, step-by-step tutorials for the reader's task. Explain the
  purpose of settings and the expected result of each action.
- Use US English in `en.md`, Spain Spanish in `es.md`, and natural Italian in
  `it.md`. Keep the scope, facts, and steps consistent across versions.
- Link each article to its localized TOC and the other two language versions.
- Keep visible UI labels consistent with the screenshots. Explain their meaning
  in the article's language when useful.
- Distinguish the article's language from the languages supported by the product.
  A translation does not imply support for that voice language or UI locale.
- Clearly distinguish demonstrated actions from instructions for the reader.
  Do not claim that an agent was created, a setting saved, or a test completed
  unless that action was actually performed and verified.
- State meaningful prerequisites and differences between agent types. Do not
  present an existing demo agent's integrations as default product capabilities.

## Product context and screenshots

- If `LOCAL_CONTEXT.md` exists, read it for additional local context sources.
  This optional file is Git-ignored and is not required to contribute.
- Reconcile documentation with the running UI and available implementation;
  do not copy internal-only information into a public guide.
- Use the user's specified browser and running webapp for navigation and real
  screenshots. Do not fabricate UI screenshots.
- Respect the requested stopping point in a workflow. If asked to show creation
  without completing it, stop before the final creation action.
- Inspect existing agents without changing their configuration unless authorized.
  Do not start calls, enable integrations, or publish a widget just to illustrate
  the controls.
- Store screenshots in the guide's `images/` folder with descriptive filenames.
  Ensure the extension matches the actual image format.
- Reuse screenshots across translations when the UI is the same. Provide useful,
  localized alt text and place images next to the relevant explanation.
- Review screenshots for readability and unintended sensitive information,
  including credentials, private customer data, and unrelated activity.

## Verification

- Check that every local Markdown link and image reference resolves.
- Check that image files are readable and their extensions match their format.
- Review the rendered article when a preview is available. File existence alone
  does not verify rendering. Report any preview limitation honestly.
- Verify consistency across all three languages and their TOC entries.
- Run `rtk git diff --check` before committing; for staged changes, use
  `rtk git diff --cached --check`.
- Documentation-only changes do not require application builds or a new test
  framework. Use checks appropriate to the changed content.

## Shell commands

Always prefix shell commands with `rtk`. Prefer its dedicated filters when
available; use `rtk proxy <command>` when raw output or passthrough is needed.
Prefix every command in a chain separately:

```bash
rtk git add AGENTS.md && rtk git commit -m "Document contributor workflow"
```

Use `rtk rg` or `rtk rg --files` for searches. Do not run destructive Git commands
without explicit authorization.

## Git workflow

- Follow the user's explicit branch choice. Before starting a new feature or bug
  fix, ask whether to use a worktree or work on `main` unless already specified.
- Inspect repository status first. If unrelated uncommitted changes exist, ask
  the user to clean them up before continuing. Do not treat changes from the
  current authorized task as unrelated work.
- Unless otherwise specified, update from `main` before starting work when a
  remote branch exists. A new repository with no commits or remote cannot be
  pulled; state that limitation and continue within the authorized scope.
- Stage only files belonging to the task. Commit and push when requested.
- After completing work, ask whether the user wants a PR unless they have already
  chosen direct delivery to `main` or another delivery method.
- Never open draft PRs. Requested PRs must be ready for review.
