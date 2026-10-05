# Repository Structure

The repository separates the working prototype from the product-management and responsible-AI documentation used to explain how it could be developed toward a more mature product.

```text
Nigerian-Pidgin-ASR-Whisper-LoRA/
├── README.md
├── ASR_Whisper_LoRA_Nigerian_Pidgin.ipynb
├── requirements.txt
├── .gitignore
├── LICENSE                      (to be added after licence review)
├── data/
│   └── README.md
├── assets/
│   └── README.md
├── product/
│   ├── PRODUCT_CASE_STUDY.md
│   ├── PRODUCT_REQUIREMENTS.md
│   ├── USER_STORIES.md
│   ├── PRODUCT_BACKLOG.md
│   └── ROADMAP.md
├── portfolio/
│   └── ASR_PIDGIN_PORTFOLIO_CASE_STUDY.md
├── responsible-ai/
│   ├── AI_EVALUATION_PLAN.md
│   ├── AI_RISK_ASSESSMENT.md
│   └── RELEASE_READINESS.md
└── docs/
    ├── SETUP.md
    ├── PROJECT_STRUCTURE.md
    ├── GITHUB_PUBLISHING.md
    └── SECURITY.md
```

## Core implementation

- `README.md` — overview, architecture, configuration, results with caveats, limitations, documentation links.
- `ASR_Whisper_LoRA_Nigerian_Pidgin.ipynb` — LoRA fine-tuning, WER evaluation, 8-bit inference, and Gradio demo.
- `requirements.txt` — packages used by the notebook (unpinned).
- `.gitignore` — files that should not be committed.
- `LICENSE` — to be added by the repository owner.

## Product documentation

- `PRODUCT_CASE_STUDY.md` — problem, users, solution, implementation status, decisions, limitations, proposed validation.
- `PRODUCT_REQUIREMENTS.md` — implemented and proposed requirements.
- `USER_STORIES.md` — implemented and proposed stories with acceptance criteria.
- `PRODUCT_BACKLOG.md` — prioritised work.
- `ROADMAP.md` — proposed phases and milestones.

## Portfolio documentation

- `ASR_PIDGIN_PORTFOLIO_CASE_STUDY.md` — concise case study for applications and interviews.

## Responsible AI and release documentation

- `AI_EVALUATION_PLAN.md` — proposed approach to evaluating accuracy, robustness, fairness, and usability.
- `AI_RISK_ASSESSMENT.md` — risk register, current treatments, proposed mitigations, open questions.
- `RELEASE_READINESS.md` — checklist and decision framework for any release beyond the prototype.

## Supporting documentation

- `SETUP.md`, `PROJECT_STRUCTURE.md`, `GITHUB_PUBLISHING.md`, `SECURITY.md`.

## Scope note

The product and responsible-AI documents distinguish between what is implemented in the current prototype and what is proposed. Proposed work must not be presented as completed implementation.
