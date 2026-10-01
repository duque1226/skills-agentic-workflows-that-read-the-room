---
name: update-github-info
description: Keep the GitHub Info page current with practical, sourced updates from GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    allowed-files:
      - site/content/github-info.md
    draft: false
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before making any changes.

Fetch both of these official sources with the web-fetch tool:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Also include Awesome Copilot workflows as a source when identifying useful updates.

Identify recent items that are useful to developers and fit the site's existing themes. Check publication dates, avoid repeating items already covered, and do not add claims that are not supported by the fetched sources. If there is nothing worthwhile to add, leave the page unchanged.

Update only `site/content/github-info.md`. Keep the additions short and practical, preserve the existing editorial direction, and link each new item directly to its source on GitHub Blog or GitHub Changelog.

Review the final diff to ensure it contains only the intended page update. When there are changes, use the configured create-pull-request safe output to open a pull request against `main` for Mona to review. Include a concise summary and source links in the pull request description. Never push changes directly to `main`.