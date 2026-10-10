---
name: update-github-info

on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Refresh Mona's GitHub information page with useful, current guidance from official GitHub sources.

## Instructions

1. Read `notes/mona-notes.md` and follow Mona's editorial guidance.
2. Use the `web-fetch` tool to read external public guidance from:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. When repository guidance or reference files are needed, read them with GitHub repository API tools. Do not use terminal, CLI, bash, or other sandboxed commands to retrieve repository guidance.
4. Update only `site/content/github-info.md`. Keep summaries short, practical, useful to developers, and attribute each Blog or Changelog item to its source.
5. If the sources do not support a meaningful update, leave the file unchanged and do not create a pull request.
6. Otherwise, use the `create-pull-request` safe output to open one pull request containing the update for Mona to review. Do not write directly to the default branch.
7. Do not compile agentic workflow files or generate `.lock.yml` files.