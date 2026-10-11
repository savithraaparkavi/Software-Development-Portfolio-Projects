# Chapter Clear — Readability Studio

A free, browser-based tool for authors. Paste an English chapter to get a Flesch Reading Ease score, word/sentence counts, and the five sentences ranked as hardest by a transparent heuristic. Hard sentences are highlighted in the chapter preview.

## Run locally
Open `index.html` in a modern browser. No install, account, API key, or backend is needed.

## How it works
- Calculates an approximate Flesch Reading Ease score using sentence count, word count, and estimated syllables.
- Ranks sentences using length, estimated polysyllabic-word count, and punctuation/clauses.
- Highlights the five highest-ranked sentences.
- Runs entirely in the browser; text is not uploaded.

## Limitations
This is a heuristic, not an AI editor. Syllable counting is approximate and English-only. A long sentence is not necessarily bad writing, and specialist terms may be appropriate for the intended audience. Treat the score as a prompt for review, not a quality judgment.

## Built with
HTML, CSS, vanilla JavaScript. ChatGPT was used as an AI coding assistant; no external AI API is called at runtime.
