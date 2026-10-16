---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

engine: codex

tools:
  edit:
  web-fetch:

network:
  allowed:
    - defaults
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before making any changes. Use Mona's notes as the editorial guide.

Use the `web-fetch` tool to fetch both of these official sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Select only recent, useful updates that help developers learn GitHub faster. Confirm every detail against the fetched source, keep summaries short and practical, and include a direct link to the relevant GitHub Blog or Changelog item for every update. Do not add speculation or duplicate items already covered in `site/content/github-info.md`.

Update `site/content/github-info.md` while preserving its existing purpose and structure. Add or refresh a clearly titled section for recent GitHub updates, using concise bullets with the update title, practical summary, and source link. Leave unrelated content unchanged.

If there are no useful new updates, make no changes and do not open a pull request. Otherwise, review the diff to ensure it contains only the intended update to `site/content/github-info.md`, then use the `create-pull-request` safe output exactly once to open a focused pull request for Mona to review. Include the official source links and a concise summary in the pull request description. Do not write directly to the default branch or use any other mechanism to publish changes.