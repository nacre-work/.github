# .github

Organization profile and templates shared across repositories.

```
profile/README.md          what shows on github.com/nacre-work
profile/assets/            logos the profile page loads
ISSUE_TEMPLATE/            default templates
```

A repository named `.github` is special: GitHub renders `profile/README.md`
as the organization's front page, and repositories without their own copies
inherit the templates from here.

## Why the logos live here

The profile page loads its images over `raw.githubusercontent.com`, which
serves public repositories only. `brand` is private, so a profile pointing at
it renders a broken image for every visitor. The two lockups in
`profile/assets/` are copies kept here for that reason.

`brand` remains the source of truth. When the mark or the palette changes,
change it there first, then refresh these copies — see the mirror table in
that repository's README.
