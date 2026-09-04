---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
    allowed-base-branches:
      - main
---

# Update GitHub Info

Keep the site's GitHub information current using official GitHub sources.

## Instructions

1. Read `notes/mona-notes.md` before making any decisions.
2. Use the GitHub repository API tools to read repository guidance and relevant reference files. Do not use terminal, CLI, or sandboxed commands for that repository guidance or reference-file reading.
3. Use web fetch to read https://github.blog/latest/.
4. Use web fetch to read https://github.blog/changelog/.
5. Review the current contents of `site/content/github-info.md`.
6. Identify only concise, practical updates that help developers learn GitHub faster. Preserve useful existing content and avoid speculative or duplicate items.
7. Update `site/content/github-info.md` with well-supported information from the fetched GitHub Blog or Changelog pages. Mention the source whenever a change comes from either source, including a direct link where appropriate.
8. Make the smallest focused edit needed. Do not modify workflow files, notes, or unrelated site files.
9. Use the `create-pull-request` safe output to create a pull request for Mona to review. Do not write directly to `main`.
10. If no worthwhile, source-backed update is available, leave the file unchanged and do not open a pull request.

When proposing a pull request, include a concise title and body that summarize the content changes and cite the official sources reviewed.
