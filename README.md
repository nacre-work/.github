# .github

Organization profile and templates shared across repositories.

```
profile/README.md          what shows on github.com/nacre-work
profile/assets/            logos the profile page loads
ISSUE_TEMPLATE/config.yml  shared issue-creation config, no forms
```

A repository named `.github` is special: GitHub renders `profile/README.md`
as the organization's front page, and repositories without their own
`ISSUE_TEMPLATE/` inherit `config.yml` from here.

`config.yml` carries no issue forms — only `blank_issues_enabled: false` and the
two contact links (report a vulnerability privately, ask in Discussions). A
repository that wants a bug form ships its own, as `nacre` does; a repository
that inherits only this and adds no form of its own routes every would-be issue
to those links, which is the intended default for a repository that is not
`nacre`.

## Why the logos live here

The profile page loads its images over `raw.githubusercontent.com`, which
serves public repositories only. `brand` is private, so a profile pointing at
it renders a broken image for every visitor. The two lockups in
`profile/assets/` are copies kept here for that reason.

`brand` remains the source of truth. When the mark or the palette changes,
change it there first, then refresh these copies — see the mirror table in
that repository's README.
