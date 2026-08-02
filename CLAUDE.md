# .github

The organization profile and the issue templates other repositories inherit.
Public.

```
profile/README.md          what renders at github.com/nacre-work
profile/assets/            logos the profile page loads
ISSUE_TEMPLATE/            default templates
```

## Two rules, both learned the hard way

**No links to private repositories.** This page is public; `brand`,
`nacre-web`, `nacre-infra`, and `nacre-enterprise` are not. A link to one
renders as a 404 for every visitor who is not in the organization, and the
profile is the first page anyone sees. **Link only `nacre`** — it is the only
public repository left.

`nacre-web` was public until it was not. Anything the profile needs from the
website links to `nacre.work` itself rather than to the repository behind it:
the served file is public whatever the repository is, and it is the canonical
location anyway.

**Check that a link resolves before adding it.** The Quickstart link pointed at
`nacre/docs/quickstart.md` from the initial commit; the file did not exist for
months. Anonymously, not signed in:

```bash
curl -s -o /dev/null -w '%{http_code}\n' <url>
```

`403` on `/discussions` from an automated request is normal and does not mean
the link is broken — GitHub treats unauthenticated tooling differently there.

## Why the logos are here

`raw.githubusercontent.com` serves public repositories only, so a profile
pointing at the private `brand` repository loads nothing. The two lockups in
`profile/assets/` are copies kept here for that reason.

`brand` stays the source of truth. When the mark or palette changes, change it
there first and refresh these copies — the mirror table in that repository lists
every downstream copy.

## Tone

The profile carries the nacre metaphor at length, on purpose: strength from
stacking, the layer growing around what got inside, iridescent but opaque. Each
paragraph ties to an engineering commitment rather than sitting as decoration.
Keep that pairing if you edit it — the metaphor without the commitment is
marketing, and the commitment without the metaphor is a changelog.
