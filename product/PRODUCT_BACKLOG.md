# Product Backlog

Priorities: **P0** do before sharing results · **P1** next · **P2** later · **P3** exploratory. All items are proposed unless marked done.

## P0 — Credibility

| ID | Item | Why |
|---|---|---|
| B-1 | Run the corrected evaluation and record WER with settings | The only existing number is contaminated |
| B-2 | Re-run from a clean runtime; confirm the notebook works end-to-end | Pre-publication checklist |
| B-3 | Add a local `save_pretrained` step for the adapter | Default checkpointing may not save within 424 steps |
| B-4 | Review dataset, Whisper, and code licences; add `LICENSE` | Required before publishing |
| B-5 | Pin tested package versions | Reproducibility |

## P1 — Evidence

| ID | Item |
|---|---|
| B-6 | Zero-shot Whisper baseline under identical decoding |
| B-7 | Report CER and text-normalised WER |
| B-8 | Re-examine training: loss curve, learning rate (1e-3), number of epochs |
| B-9 | Compare decoder-prompt options (English vs alternatives) |
| B-10 | Hold out a validation split for tuning, keep test untouched |
| B-11 | Error analysis: sample of worst predictions, categorised |

## P2 — Quality and usability

| ID | Item |
|---|---|
| B-12 | Clean notebook (remove unused calls such as the initial full `load_dataset`; wire or remove unused `compute_metrics`) |
| B-13 | Slice evaluation by speaker/accent/noise using dataset metadata |
| B-14 | Long-form transcription via chunking |
| B-15 | Script/CLI for inference |
| B-16 | Model card for the adapter on the Hub |

## P3 — Exploration

| ID | Item |
|---|---|
| B-17 | Hyperparameter search (rank, target modules, epochs) |
| B-18 | Data augmentation (noise, speed) |
| B-19 | Smaller Whisper models for lower-cost deployment |
| B-20 | Stable hosted demo with privacy notice |
