---
name: update-github-info
description: Refresh Mona's GitHub Info content with recent official GitHub Blog and Changelog updates.
on:
  schedule: daily
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
---

# Update GitHub Info

Keep `site/content/github-info.md` current with concise, practical updates from official GitHub sources.

## Instructions

1. Read `notes/mona-notes.md` and `site/content/github-info.md` before drafting any changes.
2. Use web-fetch to read both `https://github.blog/latest/` and `https://github.blog/changelog/`. Follow links on those pages to the individual official posts when more detail is needed. Use only facts supported by those sources; do not invent dates, titles, or claims.
3. Find a small set of recent, useful updates that help developers learn GitHub faster. Prefer items published since the latest entries already recorded in `site/content/github-info.md`. Avoid duplicate titles or source URLs, and do not change the site's editorial angle or unrelated content.
4. Update only `site/content/github-info.md`. Keep summaries short and practical, preserve the existing headings and Markdown style, and attribute each item to GitHub Blog or GitHub Changelog with its publication date and source URL. Put new items under `## Latest GitHub Updates` using `### <title>`, a brief summary paragraph, and a `Source:` line. Create that section if it does not exist; otherwise add or refresh entries without duplicating them.
5. Review the diff to confirm it only changes `site/content/github-info.md`, every new item has a verifiable official source, and the Markdown follows the existing content structure.
6. If there are substantive, non-duplicate updates, use the `create-pull-request` safe output to open one pull request for Mona to review before publication. Describe the updates and link their sources in the pull request. Do not write changes directly to the default branch. If there are no substantive changes to propose, do not open an empty pull request.
