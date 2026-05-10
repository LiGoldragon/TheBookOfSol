# Skill — The Book of Sol

*How to work in The Book of Sol as a prose, source, and publishing
surface.*

---

## What this skill is for

Use this skill when editing The Book of Sol: article prose, source
extracts, publication metadata, generated banner images, and Substack
publishing preparation. It sits under this repo's `AGENTS.md`, which
remains the full convention document for voice, source handling,
bibliography boundaries, and version control.

The repository contains more than articles. Articles are publishable
essays in the category directories at the repo root. Source extracts
and research notes support those essays but are not themselves
articles unless their front matter says so.

---

## Article front matter

New publishable articles carry YAML front matter:

```yaml
---
title: In Praise of Agni
subtitle: On Cooking, Tapas, and the Fear of Friction
kind: article
publish: true
banner_image: generated-images/in-praise-of-agni-banner.png
---

# In Praise of Agni

![A Vedic hearth fire burning beside cooked grain, ghee, and a solar form of Agni.](../generated-images/in-praise-of-agni-banner.png)
```

Use `true` and `false` for booleans. Do not use a question mark; YAML
question marks introduce explicit mapping keys and are not the
boolean convention here. Do not use `yes` / `no`; those are ambiguous
across YAML versions.

`kind: article` distinguishes articles from `source-extracts/` and
research directories. `publish: true` means the article is intended
for Substack publication. `publish: false` means the file is still an
article-shaped draft but not ready to ship.

The Substack CLI currently reads `title` and `subtitle` from front
matter. Agent workflows read `kind`, `publish`, and `banner_image`.
Keep the article's H1 matching `title`; the CLI strips the leading H1
when it matches the chosen title.

For published articles, keep the banner image in the article body as a
standalone Markdown image block immediately below the H1 and before the
subtitle/body. This is separate from the cover image metadata. The
front matter and manifest use repo-relative paths
(`generated-images/name-banner.png`); the Markdown image uses the path
relative to the article file (`../generated-images/name-banner.png`
for root category directories).

---

## Substack CLI

Publishing uses the `substack` CLI. The durable usage reference lives
in lore's `substack/basic-usage.md`; read it before publishing or
debugging publication behavior. The CLI also exposes help through
`substack --help` and subcommand help, but the lore page is faster
and records the project-specific behavior.

Daily commands:

```sh
substack post create --file-path diet/In_Praise_of_Agni.md
substack post create --file-path diet/In_Praise_of_Agni.md --draft
substack post update <post-id> --file-path diet/In_Praise_of_Agni.md
substack post list --limit 20
```

The CLI discovers `.substack-posts.json` at the repository root. That
manifest maps local Markdown links to published Substack URLs and can
also attach `banner_image` to a source file. If an article has
`publish: true`, ensure the manifest contains its `source_path` and
`banner_image` before publishing unless the publish command passes an
explicit `--cover-image`.

Do not use `--publish-linked-files` unless every local `.md` link in
the article should itself become a published post. Otherwise ensure
local links either resolve through `.substack-posts.json` or are
written as plain prose references before publishing.

---

## Banner images

Publishable articles need a corresponding banner image before they
ship. The convention is:

- location: `generated-images/<article-slug>-banner.png`;
- aspect: very wide, roughly 2.5:1 to 3:1;
- width: at least 1900 pixels when possible;
- content: embodies the article's spirit rather than illustrating a
  literal scene mechanically;
- watermark: `ligoldragon.com` in a corner, small enough not to
  dominate the image.

When an article has `publish: true`, check whether its
`banner_image` path exists. If it does not, create the image before
publishing. Add or update the `.substack-posts.json` manifest entry
so the CLI can use the banner as the cover image. Also embed the same
image in the article body as a standalone Markdown image block. The
manifest cover makes the Substack cover; the in-body Markdown image is
what appears inside the article after a reader opens it.

Codex agents with image generation access use this workspace's
`imagegen` skill for new raster banners. Generate first, then move
the chosen output into `generated-images/`, resize or crop it to the
wide banner aspect, and add the watermark locally so the text is
exact. Claude Code agents that do not have image generation capacity
record the missing banner as a task for a Codex poet-shaped role
instead of inventing a placeholder.

---

## Source extracts and research notes

`source-extracts/` holds quote extractions that feed articles. The
`research_*` directories hold research scaffolding. They do not get
`publish: true` unless a human explicitly turns a specific file into
a publishable article. Keep extracted sources, article prose, and
publication metadata separate.

---

## See also

- this repo's `AGENTS.md` — full writing conventions and
  bibliography discipline.
- this workspace's `skills/poet.md` — poet role discipline.
- this workspace's `skills/poet-assistant.md` — second poet-shaped
  lane.
- this workspace's `skills/prose.md` — prose craft.
- lore's `substack/basic-usage.md` — Substack CLI behavior.
