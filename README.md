# Interview Drill

A self-contained flashcard app for practising senior full-stack interview answers out loud. Say the whole answer before revealing the model answer, grade yourself honestly, and the spaced-repetition scheduler resurfaces what you miss and retires what you know.

Live at **https://pablomotta.github.io/Interview-prep/**

Progress is stored in `localStorage`, so ratings persist per browser, per device. The site is excluded from search indexing.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app — markup, styles, card bank, and logic in one file. No build step, no dependencies. |
| `revisions.json` | A revised question bank, not yet merged into the app. |
| `security-cards.json` | A proposed Security category, not yet merged. |
| `robots.txt` | Blocks search-engine indexing. |

## The card bank

Cards live in a `BANK` array inside `index.html`. Each category holds its cards; each card has an id, a difficulty level, a question, an answer, a tag, and a practice note.

```js
{
  id: "react", name: "React", domain: "frontend", slope: "climb",
  cards: [
    { id: "react-1", level: 2, q: "…", a: "First paragraph||Second paragraph",
      tag: "Teachable", note: "Shown after grading, never before." }
  ]
}
```

Answers use `||` to separate paragraphs. The practice note renders after you grade a card, so it can't hint at the answer beforehand.

## Revisions in progress

`revisions.json` is a rewrite of the question set: redundant questions merged, vague ones sharpened, and missing topics added. It holds **431 questions across 17 topic categories**, plus selections that reference those questions by id rather than restating them.

Selections come in two kinds:

- **`core-*`** — a condensed pass organised by topic (47 cards across 8 categories)
- **`prep-*`** — job-oriented sets drawn across topics: frontend (28), full-stack (34), and an AI-native add-on (16) meant to stack on top of another preset

Because selections reference ids, a question's text exists in exactly one place and the two layers can't drift apart.

Questions only for now — answers still need writing, and nothing here has been merged into `index.html`.
