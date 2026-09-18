---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
permissions:
  contents: read
safe-outputs:
  create-pull-request:
    title-prefix: '[mona] '
    draft: true
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:

- `notes/mona-notes.md`
- GitHub Blog: <https://github.blog/latest/>
- GitHub Changelog: <https://github.blog/changelog/>

Use `web-fetch` to fetch both GitHub Blog URLs and use the current public
information to update `site/content/github-info.md` with concise, practical
updates for readers. Include source context when content comes from the GitHub
Blog or GitHub Changelog, and preserve the existing content style.

Open a pull request for Mona to review. Use a pull request title that mentions
Mona or GitHub Info. Do not write directly to `main`; rely on `safe-outputs` with
`create-pull-request`, and only propose changes to `site/content/github-info.md`.
If there are no meaningful, source-backed updates, use `noop` with a short reason
instead of opening a pull request.
