<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)"
            srcset="https://raw.githubusercontent.com/nacre-work/.github/main/profile/assets/nacre-lockup-h-dark-1024.png">
    <img src="https://raw.githubusercontent.com/nacre-work/.github/main/profile/assets/nacre-lockup-h-1024.png" width="260" alt="Nacre">
  </picture>

  <p><strong>Strength from layers</strong></p>

  <p>
    A self-hosted knowledge index with fine-grained access control.<br>
    Agents reach it over MCP, applications over an API.
  </p>

  <p>
    <a href="https://nacre.work">nacre.work</a> ·
    <a href="https://github.com/nacre-work/nacre">Core</a> ·
    <a href="https://github.com/nacre-work/nacre#quickstart">Quickstart</a> ·
    <a href="https://github.com/nacre-work/nacre/discussions">Discussions</a>
  </p>
</div>

---

## What we're building

Vector search is a solved problem. What isn't: making sure an agent querying a
company index sees exactly the documents the requesting user is cleared for —
and being able to prove it to an auditor.

Nacre is a context layer, not another company assistant. No chat, no search UI
of its own. Just the index, the permissions, and two ways to reach it: MCP for
agents, REST for applications.

## Why we're called Nacre

Nacre is the material lining the inside of a shell. Mother-of-pearl. It is also
one of the more instructive things nature has built, and it turned out to
describe this product more precisely than we expected.

### Strength comes from the stacking

Nacre is made of aragonite platelets — a brittle mineral you could crush between
two fingers. Stacked in thin layers and bonded with protein, those same
platelets produce a material orders of magnitude harder to fracture than solid
aragonite. A crack doesn't run straight through. It stalls, deflecting between
the layers, spending its energy on the journey.

The value was never in the material. It was in the arrangement.

The same holds for a knowledge base. Your documents already exist — in Drive, in
Confluence, in a hundred folders nobody has opened since 2023. Nothing we do
makes any single one of them better. What we build is the arrangement: layers,
boundaries, permissions, the relationships between them. The index is stronger
than the sum of the files it was built from, and for the same reason.

### The layer grows around whatever got inside

A shell doesn't fight the grain of sand that works its way in. It wraps it.
Layer after layer, until the intruder is no longer a defect but part of the
structure — and, eventually, the most valuable thing in the shell.

That is ingest, described exactly. A document arrives as it is: a PDF someone
scanned crooked, a URL, an ID from a system we've never heard of. It accumulates
layers — parsing, chunking, embeddings, permissions, metadata — and what comes
out the other side is no longer a file. It's part of the index.

### It shimmers, but you cannot see through it

The color in nacre isn't pigment. It's interference: light entering the stack,
bouncing between layer boundaries, coming back out changed. Move your head and
the color moves with you. Every viewing angle gets a different answer.

And for all that light, nacre is opaque. Nothing passes through.

This is the part of the metaphor we care about most, because it is the whole
product. Every agent and every user gets their own cross-section — the one their
permissions carve out. The index gives back exactly as much as the viewer is
entitled to, and not one line more. Different angle, different answer, nothing
visible straight through.

## How that shows up in the code

Each of those properties has a corresponding engineering commitment we don't
negotiate on:

**Permissions are part of the index, not a filter on top of it.** Access
filtering happens during HNSW traversal, so `top_k` returns k permitted results
rather than k minus whatever got stripped afterward. That decision goes into the
schema on day one; it cannot be retrofitted later.

**A permission evaluation failure denies access.** There is no "couldn't compute
it, let it through" path. Not in the resolver, not in the cache, not in the
degraded mode.

**"No permission" and "no such object" return identical responses.** Otherwise
enumerating identifiers tells you which documents exist, which is its own leak.

**Nothing leaves your network.** Docker Compose, your perimeter, your models, no
phone-home. After watching a well-funded RAG vendor shut down with two weeks'
notice in mid-2026, we think this one needs no further argument.

## Repositories

| | Contents |
|---|---|
| **[nacre](https://github.com/nacre-work/nacre)** | Core: API, MCP server, indexing, search, permissions. Apache 2.0 |
| **[nacre-web](https://github.com/nacre-work/nacre-web)** | Website and documentation |

Logos, palette, and tokens ship with the site, under
[`nacre-web/public/brand/`](https://github.com/nacre-work/nacre-web/tree/main/public/brand).

## Contributing

Start with [CONTRIBUTING.md](https://github.com/nacre-work/nacre/blob/main/CONTRIBUTING.md).
Changes to the permission model need two maintainer approvals — we're
conservative there on purpose.

Found an access-control problem? Don't open a public issue —
[SECURITY.md](https://github.com/nacre-work/nacre/blob/main/SECURITY.md).
