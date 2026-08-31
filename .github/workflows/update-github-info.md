---
name: update-github-info
description: Draft updates for Mona's GitHub Info website using official GitHub sources and repository context.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making any updates.

Use these sources and instructions:
- Read `notes/mona-notes.md`
- Web fetch https://github.blog/latest/
- Web fetch https://github.blog/changelog/
- Web fetch https://awesome-copilot.github.com/workflows/
- Read external public guidance with web-fetch.
- Read repository guidance or reference files with GitHub repository API tools instead of terminal, CLI, or sandboxed commands.

Use the GitHub Blog, GitHub Changelog, and Awesome Copilot workflows as sources for updates, product changes, and practical examples relevant to Mona's audience.

If the repository model configuration is not available or resolves to an unsupported Copilot model, prefer a known-supported model such as `gpt-4o` for this workflow instead of relying on an invalid repository default.

Required workflow behavior:
1. Read `notes/mona-notes.md` and the selected source pages before editing.
2. Web fetch the current GitHub Blog and GitHub Changelog pages and extract at least one concrete update or product announcement that is new enough to be relevant to readers.
3. Edit `site/content/github-info.md` with an actual visible change that reflects the newly fetched source, such as adding a new bullet, a fresh subsection, or a concrete recommendation based on the source.
4. Do not leave the file unchanged. The change must be specific, useful, and based on the fetched sources rather than a generic restatement.
5. Add source attribution directly in the content near the change, using a line like `Source: GitHub Blog`, `Source: GitHub Changelog`, or `Source: Awesome Copilot workflows`, plus the source URL when helpful.
6. Use `safe-outputs` with `create-pull-request` only after the page has been updated.
7. The generated pull request must include the same source context in the PR body or title, and it must clearly mention `GitHub Blog`, `GitHub Changelog`, or `awesome-copilot.github.com`.
8. If the source material does not obviously fit the existing content, create a short new section titled something like `Recent GitHub updates` and add 2-4 bullets with source labels.

Update `site/content/github-info.md` with concise, practical website copy that reflects the latest GitHub developments and Mona's notes. Make sure the change is a real content improvement and not a no-op.

Open a pull request for Mona to review. Use `safe-outputs` with `create-pull-request` so the agent can propose changes without writing directly to `main`. The pull request should clearly say where the new information came from and should be ready for Mona to review and approve or adjust before merge.
