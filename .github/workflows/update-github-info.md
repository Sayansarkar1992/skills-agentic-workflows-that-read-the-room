---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit: true
  web-fetch: {}
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    draft: false
    allowed-files:
      - site/content/github-info.md
---

Read `notes/mona-notes.md` first and follow its editorial guidance. Use web-fetch
to read:

- https://github.blog/latest/
- https://github.blog/changelog/

Select only recent, verified developments that would be useful to GitHub
developers. Update `site/content/github-info.md` with concise, practical
guidance, preserving its existing structure and avoiding repetition or
unsupported claims. Link to the GitHub Blog or Changelog source for each
development you include.

If neither source contains a development that warrants a useful update, leave
the file unchanged and use `noop` with a brief reason. When you make a change,
open a pull request targeting `main` for Mona to review using the
`create-pull-request` safe output. Keep the PR title and summary concise. Do not
write directly to `main` or use tools to make GitHub writes outside that safe
output.
