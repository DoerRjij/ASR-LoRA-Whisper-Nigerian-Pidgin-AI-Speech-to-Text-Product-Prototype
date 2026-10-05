# Nigerian Pidgin ASR — Whisper large-v2 + LoRA

Fine-tuning **OpenAI Whisper large-v2** for automatic speech recognition (ASR) in **Nigerian Pidgin**, using **LoRA** (parameter-efficient fine-tuning) on the **Nigerian Pidgin 1.0** dataset, with an 8-bit inference path and a Gradio demo.

> **Status: research/learning prototype.** One training run, one epoch, no clean benchmark yet. See [Results and caveats](#results-and-caveats) before quoting any number.

## What this project does

1. Loads the Nigerian Pidgin 1.0 dataset (train + validation combined for training; test held out).
2. Resamples audio to 16 kHz and converts it to Whisper log-Mel features.
3. Trains a LoRA adapter (`q_proj`, `v_proj`) on top of a frozen Whisper large-v2.
4. Evaluates Word Error Rate (WER) with a manual generation loop on the test set.
5. Loads the base model in 8-bit (BitsAndBytes) and attaches the adapter for inference.
6. Serves a Gradio demo (upload or microphone).

## Architecture

```text
Audio (any format)
   ↓  librosa / datasets Audio → 16 kHz mono
Whisper feature extractor (log-Mel)
   ↓
Whisper large-v2 (frozen)  +  LoRA adapter (r=32, alpha=64, dropout=0.05)
   ↓  decoder prompt: language="English", task="transcribe"
Nigerian Pidgin transcript
```

**Training:** standard (non-quantised) Whisper large-v2 + LoRA.
**Inference:** 8-bit quantised base model + LoRA adapter. 8-bit is *not* used in training.

## Key configuration (as recorded in the notebook)

| Item | Value |
|---|---|
| Base model | `openai/whisper-large-v2` |
| Dataset | `asr-nigerian-pidgin/nigerian-pidgin-1.0` (code `pcm`) |
| Training examples | 3,385 (2,708 train + 677 validation) |
| Test examples | 892 |
| LoRA | r=32, alpha=64, dropout=0.05, bias none, targets `q_proj`, `v_proj` |
| Batch | 1 per device × 8 gradient accumulation |
| Learning rate / epochs | 1e-3 / 1 |
| Precision | `fp16=False` |

## Results and caveats

| Measure | Value | Status |
|---|---|---|
| Global steps | 424 | Historical, original run |
| Training loss (aggregate) | 6.7274 | Historical, original run |
| Training time | ~132 min | Historical, original run |
| WER (original) | 20.40% | **Not a clean benchmark** — original loop fed the first four reference tokens as `decoder_input_ids` (reference leakage) |
| WER (corrected loop) | *not yet run* | The corrected cell is in the notebook; run it to get the repository benchmark |

No corrected WER is claimed in this repository until the corrected evaluation has actually been run.

## Language-prompt note

The decoder prompt is set to `English` because Nigerian Pidgin was not available as a Whisper decoder language in the original workflow. Training labels and evaluation references remain Nigerian Pidgin. This is a prompt choice, not a relabelling of the data. Its effect has not been tested against alternatives.

## Quick start

See [docs/SETUP.md](docs/SETUP.md). In short: open the notebook in a Colab GPU runtime, run cells in order, and (optionally) authenticate with Hugging Face if you want to upload your adapter.

## Limitations

- One epoch, one run, no hyperparameter search.
- Validation split merged into training, so there is no separate model-selection set.
- Original WER is contaminated (see above); corrected WER pending.
- English decoder prompt for a non-English target.
- Dependencies not pinned; exact reproduction is not guaranteed.
- Gradio `share=True` links are temporary and not a deployment.
- No evaluation yet by speaker, accent, region, noise condition, or domain.

## Documentation

- Setup: [docs/SETUP.md](docs/SETUP.md)
- Structure: [docs/PROJECT_STRUCTURE.md](docs/PROJECT_STRUCTURE.md)
- Publishing: [docs/GITHUB_PUBLISHING.md](docs/GITHUB_PUBLISHING.md)
- Security: [docs/SECURITY.md](docs/SECURITY.md)
- Data: [data/README.md](data/README.md)
- Product: [product/](product/) · Portfolio: [portfolio/](portfolio/)
- Responsible AI: [responsible-ai/](responsible-ai/)

## Licence

Add a `LICENSE` file after reviewing the licences of the code you publish, Whisper, and the dataset.
