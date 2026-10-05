# Roadmap (proposed)

No dates are committed. Each phase should end with a decision, not just a deliverable.

## Phase 0 — Prototype (done)
LoRA training run, test-evaluation loop, 8-bit inference, Gradio demo, documentation.

## Phase 1 — Make the results trustworthy
Corrected WER, clean-runtime re-run, local adapter saving, pinned dependencies, licence review.
**Decision:** are results solid enough to publish publicly with the numbers?

## Phase 2 — Understand the model
Zero-shot baseline, CER, normalisation, prompt comparison, error analysis, validation split.
**Decision:** does fine-tuning give a clear, repeatable gain? What is worth improving?

## Phase 3 — Improve
Training schedule and hyperparameters, augmentation, slice evaluation, long-form transcription.
**Decision:** is performance adequate for any named use case?

## Phase 4 — Validate with users
Interviews or pilot with prospective users (researchers, media, educators). Privacy notice for the demo.
**Decision:** is there a real use case worth building toward?

## Phase 5 — Release readiness
Work through `responsible-ai/RELEASE_READINESS.md` before any deployment beyond a demo.
