# Instructions for AI Agents Working on The Book of Sol

This file is read by any AI coding/writing agent that recognizes the `AGENTS.md` convention (Claude Code, Cursor, Aider, Copilot, Codex, and others). It records the standing conventions for contributing to this repository so that no agent has to infer them from context.

## The Project

The Book of Sol is a collection of essays on solar nourishment, Āyurvedic principles, chloride toxicology, yogic practice, and related subjects. Articles are Markdown files organized into category subdirectories at the repo root: `sol-luna/`, `chloride/` (with `chloride/witnesses/` nested for the per-tradition Ancient-Witnesses-Against-Salt compilations), `ayurveda/`, `ghee/`, `diet/`, `water/`, `yoga-tantra/`, `political/`, and `personal/`. Each file is a self-contained essay. The canonical category index lives in `_index.md` at the repo root (`readme.md` is a symlink to it). When writing a new article, place it in the appropriate category directory and add a link to it in `_index.md`.

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

### `TheBookOfSol/source-extracts/` — project-local quote extractions (where notes live)

A **folder inside this repo**. It is not a place for books. It holds:

- Hand-curated quote extractions from specific source texts (`.md` files), organized into per-book subfolders (`Damar_Tantra/`, `Hatha_Yoga_Pradipika/`, `Water_of_Life/`, etc.).
- These `.md` files feed the article drafts directly and are committed.

**The *Caraka Saṃhitā* lives in its own dedicated repository** at `~/git/caraka-samhita/` ([github.com/LiGoldragon/caraka-samhita](https://github.com/LiGoldragon/caraka-samhita)). All per-page OCR, per-*sthāna* digests, thematic extractions (fruit/vegetable warnings, etc.), and philological notes on Caraka belong there. When a downstream article here cites Caraka, the citation should reference an entry in the caraka-samhita repo (either a verified-Sanskrit note under `notes/philology/` or a curated digest), not an ad-hoc local copy.

Book binaries must never live here. The `.gitignore` at the repo root enforces this (all `*.pdf`, `*.epub`, `*.mobi`, `*.djvu`, `*.zip` under `source-extracts/` are excluded). If you need to reference a book, download it to the standalone repo and reference it from there.

### The workflow

When an article or extraction requires a book:

1. Search Anna's Archive via the `annas` CLI (on `PATH` through the mentci-tools bundle). Full usage lives at `~/git/lore/annas/basic-usage.md` ([github.com/LiGoldragon/lore](https://github.com/LiGoldragon/lore/blob/main/annas/basic-usage.md)) — the short form is `annas book-search "<query>"` to find MD5 hashes and `annas book-download <md5> <filename.ext>` to fetch. Downloads land in `$PWD`, so `cd` to the target folder first.
2. Download it to `~/git/bibliography/en/<author-slug>/<slug-name>.<ext>` using the standard kebab-case naming.
3. Register it in `~/git/bibliography/bibliography.md` with a short entry explaining why it matters for the project.
4. Extract quotes into `TheBookOfSol/source-extracts/<Book_Name>/quotes.md` or similar, and cite the author / title / chapter in the article.
5. Commit and push both repos independently.

## Writing Conventions

These apply to all articles in the repository.

### No horizontal-rule separators

Never use Markdown `---` horizontal rules as section dividers. Structure articles with headings (`##`, `###`) alone. If you need a visual break, use a new heading or a blank line. This rule applies to new articles, edits to existing articles, and files under `source-extracts/`.

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

Worked example — see [Cooking and Spices](./ayurveda/Cooking_and_Spices.md) for the current reference implementation. Do **not** imitate the older pattern used in `ayurveda/Āyurveda.md`, `ayurveda/True_Ayurveda.md`, and the `chloride/witnesses/Witnesses_Against_Salt_*.md` files, which places the citation between the Sanskrit and the English — that pattern is wrong and is being retired as those files are edited.

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
1. The linguistic-argument sections of `chloride/Chloridism.md` and Section II of `chloride/The_Chloride_Indictment.md` that explicitly contrast the two ions — the argument requires both words as distinct referents.
2. Verbatim academic citation titles (journal articles, study names like "DASH-Sodium," book titles) — citations are preserved as-published.
3. Scare-quoted critiques of the sloppy modern term (e.g., *"modern dietetics collapses all of these into 'sodium'"*) — discussing the word as a word.

### No micronutrition vocabulary

Do not write in terms of "vitamins," "minerals," "protein," "micronutrients," or similar reductionist nutritional categories. Use Āyurvedic terms: *rasa, vīrya, vipāka, prabhāva, ojas, prāṇa, tejas, agni, doṣa* (*vāta, pitta, kapha*), *guṇa* (*sattva, rajas, tamas*). Explain in those terms what the modern language flattens.

### Earth is not a planet

Do not refer to Earth as a "planet" in astronomical or astrological contexts. Use "universal," "worldwide," "terrestrial," or simply "Earth." Earth has a different structural role in the solar framework this project works within than the five visible planets do.

### Gemini CLI, not direct Gemini API calls

If a workflow needs Google Gemini, use the `gemini` CLI locally. Do not construct direct Gemini API calls via `curl`.

### Prose style — avoid ChatGPT tics

The project's voice is declarative, confident, and textually grounded. It states positions directly, lets primary sources do the heavy lifting, and does not construct arguments through rhetorical antithesis. Several patterns common to LLM-drafted prose must be actively eliminated.

**Negative-contrast (the "X is not Y. It is Z." pattern) is the single most important thing to avoid.** This is the signature ChatGPT rhetorical move — building a point by first denying an alternative and then asserting the real claim. It is mechanical, tedious in repetition, and adds no information. Variants include:

- "X is not Y. It is Z." (two-sentence form)
- "X is not Y; it is Z." / "X is not Y — it is Z." (one-sentence forms)
- "X is not Y, but Z." / "Not merely X, but Y." / "Not just X, but Y."
- "Not A. Not B. Not C. But D." (triple-fragment hammer)
- "This is not [thing]. It is [other thing]." (as a standalone paragraph or section opener)

State the positive directly. If the dismissed alternative carries information (e.g., naming a common misreading to correct it), integrate it as a trailing concession: *"X is Z, not Y"* — but use this form sparingly, not as default. Most occurrences of the pattern can be eliminated entirely by cutting the "X is not Y" setup and keeping only the positive claim. A rule of thumb: if an article uses the pattern more than ~3 times, it has become the article's default rhythm and needs a full pass.

**No meta-prose about the essay itself.** Do not open with "This essay does two things...", "The argument below...", "In what follows we will see...", "A few concepts appear throughout the essay — they are worth introducing at the outset...". Do not announce the structure. Begin with the substance.

**Gloss technical terms on first use.** Articles are read by non-experts. Sanskrit terms, classical text names, and physiological concepts must carry parenthetical or inline English glosses on first appearance in each article. Subsequent uses can drop the gloss. Never assume the reader has encountered *agni*, *ojas*, *snigdha*, *mitāhāra*, *Caraka Saṃhitā*, *Haṭha Yoga Pradīpikā*, etc. before.

**Let primary sources do the heavy lifting.** The pattern that works: short orientation (one or two paragraphs of plain English), then primary-source quote block, then minimal commentary, then the next quote. Do not speak over the rishis; bring them forward and frame them. If you use an opening quote, keep it short — a long extended compound as the first thing the reader sees buries the essay's own argument.

**Example illustrates, never dominates.** When an article uses a concrete example (a modern recipe, a specific product, a named practice) to illustrate a classical doctrine, the example is one illustration, not the subject of the essay. Do not frame articles as "audits," "line-by-line analyses," or "detailed critiques of X." Frame as: "the classical doctrine says X; here is one example of a contemporary practice that violates it." The doctrine is primary; the example is secondary.

**No structural mirroring between articles.** Each subject has its own form. Do not imitate the section skeleton, paragraph count, or rhetorical pattern of another article when writing a new one. Borrow voice and register; invent structure anew each time.

**Banned filler phrases.** Remove on sight:

- "it is worth noting," "it is important to note," "it should be remembered"
- "notably," "crucially," "indeed," "moreover," "furthermore" (as paragraph openers)
- "truly," "fundamentally," "literally" (in non-literal contexts)
- "delves into," "unpacks," "navigates the complexities of," "in the realm of," "rich tapestry," "at the intersection of"
- "the fact that..." (almost always compressible)
- Stage-setting openers: "Notice that...", "Observe how...", "Note that..."

**Em-dashes used with discipline.** Em-dashes are a powerful tool for parenthetical asides and rhythmic breaks. They become a tic when used as the default emphasis device. A paragraph with three or more em-dashes is almost always restructurable into cleaner syntax. Keep density below roughly five em-dashes per 500 words of prose.

**Straight quotes, not curly.** Use `"` and `'` in all article prose. Curly quotes (`"` `"` `'` `'`) are a ChatGPT/Word-export artifact and are inconsistent with the rest of the repository.

**Aphoristic closings are welcome.** The project's best closings are brief declaratives, sometimes one-line. "Soon is a schedule." "It asked to be seen." "This is what the tradition calls food." Do not trail off with restatement or summary.

### Reference implementations for the target voice

When in doubt about voice, match these articles (which represent the clean target):

- [Cooking and Spices](./ayurveda/Cooking_and_Spices.md) — grounded textual argument, primary-source dense.
- [Apathya](./ayurveda/Apathya.md) — accessible exposition for non-experts, two-error framing.
- [The Chloride Indictment](./chloride/The_Chloride_Indictment.md) — clinical summary voice.
- [Witnesses Against Salt — Āyurveda](./chloride/witnesses/Witnesses_Against_Salt_Ayurveda.md) — primary-source compilation form.

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

- `chloride/Chloridism.md` — the linguistic primary; establishes "chloride of sodium" vocabulary.
- `chloride/The_Chloride_Indictment.md` — the summary indictment of dietary chloride.
- `chloride/witnesses/Ancient_Witnesses_Against_Salt.md` — index to the nine per-tradition witness files (Ayurveda, Yoga, Tantra, Dharma, Greek, Hebrew, Chinese, Hygienists, Political).
- `diet/Ambrosian_Diet.md` — the positive diet of the project.
- `ayurveda/The_Two_Pillars_of_Nourishment.md` — the solar/lunar framework.

Match the voice and pacing of these when writing new material.

## When In Doubt

If a convention or constraint is not explicit here, look at recent commits (`jj log --limit 20`) for the current practices, and prefer to preserve existing structure rather than introduce novelty without reason. If the choice is between a small change and a refactor, default to the small change and ask.
