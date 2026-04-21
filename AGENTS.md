# Instructions for AI Agents Working on The Book of Sol

This file is read by any AI coding/writing agent that recognizes the `AGENTS.md` convention (Claude Code, Cursor, Aider, Copilot, Codex, and others). It records the standing conventions for contributing to this repository so that no agent has to infer them from context.

## The Project

The Book of Sol is a collection of essays on solar nourishment, Āyurvedic principles, chloride toxicology, yogic practice, and related subjects. Articles are Markdown files at the repository root. Each file is a self-contained essay.

## The Bibliography Convention

The project relies on two distinct "bibliography" locations. Agents must understand the distinction and never confuse them.

### `~/git/bibliography/` — the standalone library (where books live)

A **separate git repository** on disk at `/home/li/git/bibliography/`. This is the sema-ecosystem-wide scholarly library. It holds:

- Binary source texts (PDFs, EPUBs, DJVUs, MOBIs, ZIPs) organized into author folders under `en/`, `fr/`, `de/`, `sa/` etc. by language.
- An authoritative index in `bibliography.md` at the repo root, keyed by author with Anna's Archive MD5 hashes for each text.
- A `CLAUDE.md` file at the repo root documenting the structure; read it if you need full conventions.

**All book binaries belong in this repo.** Not in The Book of Sol. When a book is downloaded or acquired, move it to the appropriate `~/git/bibliography/en/<author-slug>/` folder and register it in `~/git/bibliography/bibliography.md` with its MD5 hash.

Binaries are gitignored in that repo (only the `bibliography.md` index is committed). This is deliberate: the index is canonical, the binaries are retrievable from Anna's Archive by MD5 hash.

VCS in the bibliography repo: **jujutsu (`jj`) is mandatory.** Always `jj commit -m` with a description, then `jj bookmark set main -r @-` and `jj git push` to publish.

### `TheBookOfSol/bibliography/` — project-local quote extractions (where notes live)

A **folder inside this repo**. It is not a place for books. It holds:

- Hand-curated quote extractions from specific source texts (`.md` files), organized into per-book subfolders (`Caraka_Samhita/`, `Damar_Tantra/`, `Hatha_Yoga_Pradipika/`, `Water_of_Life/`).
- These `.md` files feed the article drafts directly and are committed.

Book binaries must never live here. The `.gitignore` at the repo root enforces this (all `*.pdf`, `*.epub`, `*.mobi`, `*.djvu`, `*.zip` under `bibliography/` are excluded). If you need to reference a book, download it to the standalone repo and reference it from there.

### The workflow

When an article or extraction requires a book:

1. Search Anna's Archive (via the `bibliotheca` MCP server when available, or via web search) for the book and its MD5.
2. Download it to `~/git/bibliography/en/<author-slug>/<slug-name>.<ext>` using the standard kebab-case naming.
3. Register it in `~/git/bibliography/bibliography.md` with a short entry explaining why it matters for the project.
4. Extract quotes into `TheBookOfSol/bibliography/<Book_Name>/quotes.md` or similar, and cite the author / title / chapter in the article.
5. Commit and push both repos independently.

## Writing Conventions

These apply to all articles in the repository.

### No horizontal-rule separators

Never use Markdown `---` horizontal rules as section dividers. Structure articles with headings (`##`, `###`) alone. If you need a visual break, use a new heading or a blank line. This rule applies to new articles, edits to existing articles, and files under `bibliography/`.

### Primary-source quote blocks — Sanskrit, translation, citation (in that order)

Every block-quote of a primary source uses this structure: **Sanskrit (bold IAST) on top, blank blockquote line, English translation in double quotes, hard line break, em-dash attribution on the final line.** The citation always goes at the end, after the translation — never between the Sanskrit and the English, and never before the Sanskrit.

Canonical form:

```
> **Sanskrit line**\
> **continuation line if the verse has more than one pāda**
>
> "English translation, flowing across\
> multiple lines if useful."\
> — *Source Text* chapter.verse, trans. Translator (optional)
```

Rules of thumb:

- Use `\` (backslash) at the end of every line that should break but stay inside the quote — including the final line of the Sanskrit and the final line of the English before the attribution.
- Put a blank `>` line (a blockquote with nothing after the marker) between the Sanskrit and the English. This is the only blank line inside the quote.
- The em-dash attribution line sits immediately after the closing quotation mark of the English, joined by a `\` hard break so it renders on its own line but inside the same blockquote.
- Italicize the source text title (`*Caraka Saṃhitā*`, `*Haṭha Yoga Pradīpikā*`, `*Bṛhadāraṇyaka Upaniṣad*`).
- If the Sanskrit text is a paraphrase or a proverbial formulation rather than an exact verse, say so in the attribution: `— proverbial formulation, after *Aṣṭāṅga Hṛdaya* Sūtrasthāna 12`.
- If you have no Sanskrit, you may use a plain block-quote of the English with the attribution underneath on its own `\\`-broken line.

Worked example — see [Cooking_and_Spices.md](Cooking_and_Spices.md) for the current reference implementation. Do **not** imitate the older pattern used in `Āyurveda.md`, `True_Ayurveda.md`, and the `Witnesses_Against_Salt_*.md` files, which places the citation between the Sanskrit and the English — that pattern is wrong and is being retired as those files are edited.

### "Chloride of sodium," not "sodium chloride"

The only permissible way to name NaCl is **"chloride of sodium"** (following the Romance-language order: *chlorure de sodium*, *cloruro di sodio*, *cloruro de sodio*). Never write "sodium chloride" (the misleading English order), and never use standalone "sodium" as shorthand for the compound. Use "chloride" alone for the active ion or principle.

Specific replacements to apply if you encounter them:
- "sodium chloride" → "chloride of sodium"
- "sodium content" → "chloride content" / "chloride load"
- "sodium intake" → "chloride intake"
- "sodium-restriction" → "chloride-restriction"
- standalone "sodium" referring to the compound → "chloride"

Why: the English construction "sodium chloride" foregrounds the stable cation and hides the reactive anion that drives the physiological injury. The project's entire linguistic argument rests on centering the anion.

Exceptions where "sodium" may remain:
1. The linguistic-argument sections of `Chloridism.md` and Section II of `The_Chloride_Indictment.md` that explicitly contrast the two ions — the argument requires both words as distinct referents.
2. Verbatim academic citation titles (journal articles, study names like "DASH-Sodium," book titles) — citations are preserved as-published.
3. Scare-quoted critiques of the sloppy modern term (e.g., *"modern dietetics collapses all of these into 'sodium'"*) — discussing the word as a word.

### No micronutrition vocabulary

Do not write in terms of "vitamins," "minerals," "protein," "micronutrients," or similar reductionist nutritional categories. Use Āyurvedic terms: *rasa, vīrya, vipāka, prabhāva, ojas, prāṇa, tejas, agni, doṣa* (*vāta, pitta, kapha*), *guṇa* (*sattva, rajas, tamas*). Explain in those terms what the modern language flattens.

### Earth is not a planet

Do not refer to Earth as a "planet" in astronomical or astrological contexts. Use "universal," "worldwide," "terrestrial," or simply "Earth." Earth has a different structural role in the solar framework this project works within than the five visible planets do.

### Gemini CLI, not direct Gemini API calls

If a workflow needs Google Gemini, use the `gemini` CLI locally. Do not construct direct Gemini API calls via `curl`.

## Version Control

### TheBookOfSol

This repo uses **jujutsu (`jj`)**. Typical flow:

```
jj status
jj commit -m "(action, scope, detail) (further-action, scope, detail)" <files>
jj bookmark set main -r @-
jj git push
```

Commit messages follow a comma-grouped parenthetical style; look at recent `jj log` entries for examples.

Do not use `git commit` / `git push` directly. The repo is set up for `jj`, and the underlying git integration is handled by `jj git push`.

### bibliography repo

Also `jj`. Same flow. Remember that the standalone bibliography repo is a separate working copy; operate in it with `jj -R /home/li/git/bibliography <cmd>` or by changing directory.

## Reading Existing Articles

Before writing a new article, read the index or related articles to understand the project's voice. Key anchor texts:

- `Chloridism.md` — the linguistic primary; establishes "chloride of sodium" vocabulary.
- `The_Chloride_Indictment.md` — the summary indictment of dietary chloride.
- `Ancient_Witnesses_Against_Salt.md` — index to the nine per-tradition witness files (Ayurveda, Yoga, Tantra, Dharma, Greek, Hebrew, Chinese, Hygienists, Political).
- `Ambrosian_Diet.md` — the positive diet of the project.
- `The_Two_Pillars_of_Nourishment.md` — the solar/lunar framework.

Match the voice and pacing of these when writing new material.

## When In Doubt

If a convention or constraint is not explicit here, look at recent commits (`jj log --limit 20`) for the current practices, and prefer to preserve existing structure rather than introduce novelty without reason. If the choice is between a small change and a refactor, default to the small change and ask.
