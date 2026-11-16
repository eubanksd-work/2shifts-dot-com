# 2shifts-dot-com

Rules for agents working in this repo. The owner's global rules load separately; these add to them.

## What this is

The public website for Second Shift Automation, LLC. Static pages, no build step. `README.md` describes every file and the brand rules: read it first.

## Rules

- This repo is public. Anything a stranger should not read goes in `private/`, which is ignored here and is its own private repository. Commit and push it from inside `private/`.
- Before proposing or writing any page change, read the design system in `private/design-system/`.
- Nothing in this repo touches DNS. Leave `CNAME` and `.nojekyll` alone.
- Pushing to `main` publishes the site whenever GitHub Pages is on. Check the live state in `private/memory-bank.md` before assuming either way.
- Check `git config user.email` before the first commit, here and again inside `private/`.

## Where things are kept

- Long-term facts: this file and `README.md`.
- Short-term status and the task queue: `private/memory-bank.md`. There is no `memory-bank.md` in the public repo on purpose.
- Work that can wait: `private/backlog.md`.
