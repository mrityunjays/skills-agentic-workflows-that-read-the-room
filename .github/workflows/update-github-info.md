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

Update `site/content/github-info.md` with concise, practical website copy that reflects the latest GitHub developments and Mona's notes.

Open a pull request for Mona to review. Use `safe-outputs` with `create-pull-request` so the agent can propose changes without writing directly to `main`. The pull request should be ready for Mona to review and approve or adjust before merge.
