---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
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
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- awesome-copilot workflows: https://awesome-copilot.github.com/workflows/

Tell the agent to:
- read `notes/mona-notes.md`
- web fetch `https://github.blog/latest/`
- web fetch `https://github.blog/changelog/`
- web fetch `https://awesome-copilot.github.com/workflows/`
- update `site/content/github-info.md` with concise, practical updates for readers
- include concise source context when content comes from the GitHub Blog, GitHub Changelog, or awesome-copilot workflows
- open a pull request for Mona to review
- do not write directly to `main`; rely on `safe-outputs` with `create-pull-request`

Do not compile this workflow file.
