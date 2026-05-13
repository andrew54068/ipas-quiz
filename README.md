# iPAS AI 應用規劃師 (中級) 練習

A self-contained static webapp for practicing the **iPAS AI 應用規劃師中級能力鑑定** exam across all three subjects:

- **科目一** · 人工智慧技術應用與規劃 (AI Technology Application & Planning)
- **科目二** · 大數據處理分析與應用 (Big Data Processing, Analysis & Applications)
- **科目三** · 機器學習技術與應用 (Machine Learning Technology & Applications)

195 verified MCQ questions (50 past-exam + 15 sample per subject) with pre-generated Markdown explanations, source citations, and topic categorization.

## Run locally

```bash
open index.html   # macOS
# or just double-click index.html in Finder/Explorer
```

No build step, no server required. State persists in `localStorage`.

## Features

- **Subject + topic filters** — drill into a specific subject or topic block
- **Configurable rounds** — 5/10/15/20/all questions per session
- **Instant feedback** — correct/wrong + correct answer + source page
- **"💡 為什麼？" panel** — pre-generated explanation per question (why correct, why each wrong option, memory hook) + deep-link to study guide PDF at the right page
- **Option shuffle mode** — randomize A/B/C/D order to prevent position-memorization; explanation auto-rewrites to match displayed order
- **Round history + cumulative weak-topic tracking** — scoped per subject
- **Keyboard shortcuts** — `A`/`B`/`C`/`D` (with `Cmd+C` etc. preserved), `Enter` to advance, `W` to toggle the why panel

## Project structure

```
.
├── index.html                  # The app — single self-contained HTML
├── README.md
├── subjects/
│   ├── 1-ai/
│   │   ├── past-exam.pdf       # 114年第二梯次 official past exam
│   │   ├── study-guide.pdf     # 學習指引
│   │   └── progress.json       # Verified question pool (50+15)
│   ├── 2-bigdata/
│   │   ├── past-exam.pdf
│   │   ├── study-guide.pdf
│   │   └── progress.json
│   └── 3-ml/
│       ├── past-exam.pdf
│       ├── study-guide.pdf
│       └── progress.json
└── shared/
    ├── sample-questions.pdf    # 114年9月版 樣題 (covers all 3 subjects)
    └── images/                 # Reference figures used by image-based questions
```

> Personal study notes (e.g. per-round score trackers) live under `notes/` locally, but `notes/` is gitignored so nothing personal lands in the public repo. Each visitor's quiz progress is kept in their own browser's `localStorage` — never sent anywhere.

## Deploy to Vercel

This repo is structured for zero-config Vercel deployment.

```bash
gh repo create <name> --private --source=. --remote=origin --push
# then: vercel.com → New Project → Import → Deploy
```

Vercel auto-detects this as a static site. `index.html` is served at `/`. PDF deep-links use relative paths (`subjects/.../study-guide.pdf#page=N`) which work without modification.

## Disclaimer

The PDFs under `subjects/*/` and `shared/` are official materials published by the **經濟部產業發展署** (Industrial Development Administration, MOEA) for the iPAS certification program. They are included here for personal study reference. If you deploy this publicly, verify the iPAS materials' redistribution terms first — consider password-protecting the deployment, or replacing the embedded PDFs with links to the official iPAS download pages.

Question correctness is verified directly against the answer columns printed in the official past-exam PDF and sample-question PDF. Explanations are written from the study guides. Any error is mine, not the official source's.
