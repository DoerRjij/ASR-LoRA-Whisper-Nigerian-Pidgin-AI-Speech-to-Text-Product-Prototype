# Product Requirements

Status key: **Implemented** (in the notebook now) · **Proposed** (not built or not validated).

## Functional requirements

| ID | Requirement | Status |
|---|---|---|
| FR-1 | Load the Nigerian Pidgin 1.0 dataset and resample audio to 16 kHz | Implemented |
| FR-2 | Convert audio to Whisper features and transcripts to token IDs | Implemented |
| FR-3 | Fine-tune Whisper large-v2 with a LoRA adapter on `q_proj`/`v_proj` | Implemented |
| FR-4 | Evaluate WER on the held-out test set without reference-token leakage | Implemented (cell present; not yet run) |
| FR-5 | Upload the adapter to the Hugging Face Hub | Implemented (commented-out cell) |
| FR-6 | Load the adapter on an 8-bit base model for inference | Implemented |
| FR-7 | Transcribe a local audio file via a function | Implemented |
| FR-8 | Gradio demo with upload and microphone input | Implemented |
| FR-9 | Save the adapter locally | Proposed |
| FR-10 | Report CER and normalised WER alongside WER | Proposed |
| FR-11 | Zero-shot baseline and prompt-language comparison | Proposed |
| FR-12 | Evaluation by speaker/accent/noise slices | Proposed |
| FR-13 | Batch/long-form transcription (audio longer than Whisper's input window) | Proposed |
| FR-14 | Command-line or API inference outside notebooks | Proposed |
| FR-15 | Stable hosted demo (not a temporary share link) | Proposed |

## Non-functional requirements

| ID | Requirement | Status |
|---|---|---|
| NFR-1 | Reproducibility: pinned dependencies, fixed seeds, recorded hardware | Proposed |
| NFR-2 | Credentials never stored in source or outputs | Implemented (by design); verify before every push |
| NFR-3 | Transparent reporting of results and their limits | Implemented in documentation |
| NFR-4 | Inference fits constrained GPU memory | Implemented via 8-bit loading; no memory figure measured |
| NFR-5 | Latency targets | Proposed; not measured |
| NFR-6 | Privacy: clear handling of user audio | Proposed |

## Out of scope for the current prototype

Production deployment, real-time/streaming transcription, speaker diarisation, translation, and support for languages other than Nigerian Pidgin.
