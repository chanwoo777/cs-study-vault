# CS Study Vault

A study knowledge base that runs as a single web page inside [claude.ai](https://claude.ai). Upload lecture slides, textbook pages, handwritten notes or code, and Claude turns them into concept documents, course roadmaps and spaced-review check questions.

The writing rules come from a `CLAUDE.md` learning spec: explain before naming, keep every formula and pair it with a plain sentence, hide answers until you try, and judge mastery by your review record rather than by feel.

## What it does

- **Inbox:** drop in PDFs, photos, Markdown or code. Claude plans the concept documents first, you check the plan, then it writes them.
- **Course roadmaps:** documents grouped by lecture and numbered in the order you can learn them, with a prerequisite graph, "ready to learn next", and open gaps or suspected source errors.
- **Concept documents:** summary, a concrete case, definition, proof, worked examples, common misconceptions, check questions and your own notes.
- **Review:** spaced repetition. Pick how sure you are, write an answer, and Claude grades it against the stored answer.
- **Marks:** flag a whole document or one section as *Complete* or *Need more understanding*, then filter by it or jump back to it.
- **Rewrite:** bring older documents up to the current rules while keeping your notes, card numbers and review history. The previous version can be restored.
- **Renaming:** rename lecture topics, document titles and courses.
- **Export:** download any document, course or marked set as a PDF, or the whole vault as an Obsidian folder (`.zip`).

## How it runs

`study-vault.html` is published as a Claude artifact. It relies on capabilities that only exist inside claude.ai:

| Capability | Used for |
|---|---|
| `db` | Storing courses, documents, review history and marks |
| `assets` | Storing uploaded files |
| `sample` | Asking Claude to plan, write, rewrite and grade |
| `downloads` | Saving PDFs and the Obsidian export |

Opened anywhere else, the page loads but shows a "not connected" notice and can't save anything.

**No study notes are in this repository.** Documents, uploads and review history live in the artifact's storage on claude.ai. This repo holds only the page's code.

### Publishing your own copy

1. In Claude Code, ask Claude to publish `study-vault.html` as an artifact with the capabilities `db`, `assets`, `sample` and `downloads`.
2. Open the link on claude.ai, add a course, and drop files into the Inbox.

## Design

"Calm paper & ink": warm off-white pages, a deep teal accent, soft rounded panels and a serif reading font (Literata) for long study sessions. It has a matching dark mode in warm charcoal with muted teal.

## Libraries

Loaded from cdnjs at runtime: marked, DOMPurify, MathJax, pdf.js, JSZip, html2canvas and jsPDF. Fonts come from Google Fonts (Nunito Sans, Literata, IBM Plex Mono).
