# CS Study Vault

A study knowledge base in a single web page. Use it on [GitHub Pages](https://chanwoo777.github.io/cs-study-vault/) with your own Anthropic API key, or as an artifact inside [claude.ai](https://claude.ai). Upload lecture slides, textbook pages, handwritten notes or code, and Claude turns them into concept documents, course roadmaps and spaced-review check questions.

The writing rules come from a `CLAUDE.md` learning spec: explain before naming, keep every formula and pair it with a plain sentence, hide answers until you try, and judge mastery by your review record rather than by feel.

## What it does

- **Inbox:** drop in PDFs, photos, Markdown or code. Claude plans the concept documents first, you check the plan, then it writes them.
- **Course roadmaps:** documents grouped by lecture and numbered in the order you can learn them, with a prerequisite graph, "ready to learn next", and open gaps or suspected source errors.
- **Concept documents:** summary, a concrete case, definition, proof, worked examples, common misconceptions, check questions and your own notes.
- **Review:** spaced repetition. Pick how sure you are, write an answer, and Claude grades it against the stored answer.
- **Marks:** flag a whole document or one section as *Complete* or *Need more understanding*, then filter by it or jump back to it.
- **Rewrite:** bring older documents up to the current rules while keeping your notes, card numbers and review history. The previous version can be restored.
- **Renaming:** rename lecture topics, document titles and courses.
- **Deleting:** remove one document from its page, or tick several on a course page with **Select to delete**. Each document goes with its check questions, review history and marks, and **Undo** in the message at the bottom brings them back for 10 seconds.
- **Export:** download any document, course or marked set as a PDF, or the whole vault as an Obsidian folder (`.zip`).
- **Backup:** one `.json` file with everything, to restore in another browser or move between claude.ai and GitHub Pages.

## Two ways to use it

The same `study-vault.html` runs in two places and picks the right storage by itself.

### On GitHub Pages: https://chanwoo777.github.io/cs-study-vault/

- **Notes and files** are saved in your browser (IndexedDB), on that device only. Clearing browser data or switching browsers starts an empty vault, so download a backup from **Settings** now and then.
- **Claude features** (arranging notes, rewrites, grading) use your own Anthropic API key, added under **Settings**. The key stays in your browser and is sent only to Anthropic; usage is billed to your Anthropic account. Requests go through the official Anthropic SDK (`@anthropic-ai/sdk`, loaded from jsDelivr) and use Claude Opus 5.5. Effort is set per task (low for grading short answers, high for heavy documents), and the server-side refusal fallback is turned on.
- **Moving a vault here:** on the claude.ai version, open **Settings → Download backup**, then on this site open **Settings → Restore from a backup**.

### As a claude.ai artifact

Published as a Claude artifact, it uses claude.ai's built-in capabilities instead:

| Capability | Used for |
|---|---|
| `db` | Storing courses, documents, review history and marks |
| `assets` | Storing uploaded files |
| `sample` | Asking Claude to plan, write, rewrite and grade |
| `downloads` | Saving PDFs, backups and the Obsidian export |

To publish your own copy, ask Claude Code to publish `study-vault.html` as an artifact with the capabilities `db`, `assets`, `sample` and `downloads`.

**No study notes are in this repository.** It holds only the page's code. `.github/workflows/pages.yml` wraps `study-vault.html` in a full HTML document and deploys it to GitHub Pages on every push to `main`.

## Design

"Calm paper & ink": warm off-white pages, a deep teal accent, soft rounded panels and a serif reading font (Literata) for long study sessions. It has a matching dark mode in warm charcoal with muted teal.

## Libraries

Loaded at runtime: marked, DOMPurify, MathJax, pdf.js, JSZip, html2canvas and jsPDF from cdnjs, and the Anthropic SDK from jsDelivr (browser mode only). Fonts come from Google Fonts (Nunito Sans, Literata, IBM Plex Mono).
