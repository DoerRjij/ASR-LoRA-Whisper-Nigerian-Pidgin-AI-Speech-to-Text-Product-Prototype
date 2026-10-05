# Product Case Study — Nigerian Pidgin Speech-to-Text

> **Scope note:** This document separates what is **implemented** in the prototype from what is **proposed**. User needs and use cases below are hypotheses; no user research has been conducted in this project.

## 1. Problem

Nigerian Pidgin is widely spoken, but mainstream speech recognition tools are built mainly for high-resource languages. Whisper has no dedicated Nigerian Pidgin decoder language option, so out-of-the-box transcription of Pidgin speech is likely to be unreliable. (The size of that gap has not been measured in this project: no zero-shot baseline has been run.)

## 2. Who might benefit (hypotheses, not validated)

- Researchers and students working on low-resource African-language NLP
- Media and community organisations wanting transcripts of Pidgin audio
- Educators building Pidgin-language learning or accessibility materials
- Developers prototyping voice interfaces for Pidgin speakers

## 3. Solution (implemented)

A LoRA-adapted Whisper large-v2 model trained on the Nigerian Pidgin 1.0 dataset, with:

- training and evaluation workflow in one notebook
- 8-bit quantised inference to reduce memory use
- Gradio demo for file upload and microphone input

## 4. Implementation status

| Capability | Status |
|---|---|
| LoRA fine-tuning (1 epoch, 3,385 examples) | Implemented; historical run recorded |
| Held-out test evaluation (892 examples) | Implemented; corrected loop **not yet run** |
| Historical WER 20.40% | Recorded, **contaminated by reference-token leakage** |
| 8-bit inference | Implemented |
| Gradio demo | Implemented (temporary `share=True` link) |
| Adapter on Hugging Face Hub | Referenced by the notebook (`HF_REPO_ID`) |
| Zero-shot baseline comparison | Not done |
| Evaluation by speaker/accent/noise | Not done |
| Pinned environment | Not done |

## 5. Key decisions and trade-offs

- **LoRA instead of full fine-tuning:** small trainable adapter, lower memory and storage than a full copy of the model.
- **Standard-precision training, 8-bit inference only:** training was not quantised; 8-bit is applied at inference to reduce memory.
- **English decoder prompt:** used because Pidgin was not a Whisper language option. Labels remain Pidgin. Effect untested.
- **Train + validation merged:** more training data, but no separate model-selection set.
- **Evaluation corrected:** the original loop leaked reference tokens; the notebook now generates without them.

## 6. Limitations

One epoch, one run, no baseline, no clean benchmark yet, unpinned dependencies, no subgroup analysis, demo not production-ready.

## 7. Proposed validation

1. Run the corrected evaluation and report WER (and CER) with the exact setup.
2. Run a zero-shot Whisper baseline under the same decoding settings.
3. Compare decoder-prompt options.
4. Evaluate by available metadata (speaker, gender, region, noise) and on out-of-domain audio.
5. Talk to prospective users before committing to a use case.
