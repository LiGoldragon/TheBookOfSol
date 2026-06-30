# Architecture — The Book of Sol

## Role

The Book of Sol is the publishable prose surface for essays on solar
nourishment, Āyurveda, chloride toxicology, yogic practice, cosmology,
and older scientific witnesses. It is a public-facing body of doctrine,
argument, and image prepared for readers, not a private notebook.

## Boundaries

Article Markdown lives in the category directories at the repository
root. Source extracts and research notes live under `source-extracts/`
and `research_*`. Generated article images live under
`generated-images/`. Substack publication state lives in
`.substack-posts.json`.

The standalone library repository owns downloaded book binaries and its
bibliography index. Caraka extraction work lives in the dedicated
`caraka-samhita` repository; Book of Sol articles cite from that surface
or from curated public editions.

## Invariants

Articles are self-contained prose surfaces. They use YAML front matter,
category placement, and the project quote convention in `AGENTS.md`.
The voice is declarative and textually grounded: classical witnesses,
especially Sanskrit and Āyurvedic sources, carry the argument wherever
possible, and the prose avoids modern reductionist nutrition vocabulary
when the older categories name the thing more accurately. The repo index
`_index.md` is the canonical table of contents.

Generated banners embody the spirit of an article rather than
mechanically illustrate a scene.

## Status

The repository is active and publishes from local Markdown through the
Substack CLI. New article-shaped drafts may use `publish: false` until
the prose, source trail, and banner are ready.
