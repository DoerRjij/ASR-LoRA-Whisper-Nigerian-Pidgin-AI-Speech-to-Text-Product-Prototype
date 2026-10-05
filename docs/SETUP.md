# Setup and Running Guide

This guide explains what is required before running the notebook `ASR_Whisper_LoRA_Nigerian_Pidgin.ipynb`.

## 1. Enter the project folder

```bash
cd Nigerian-Pidgin-ASR-Whisper-LoRA
```

## 2. Optional: create a virtual environment (local use)

Windows:

```powershell
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Google Colab does not require a local virtual environment.

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

The notebook also has its own installation cell for Colab use. Versions are not pinned yet (see `requirements.txt`).

## 4. Use a GPU environment

The notebook is designed for a Google Colab GPU runtime. Whisper large-v2 is large; a CUDA GPU is strongly recommended for training and evaluation.

The original run took approximately 132 minutes for one epoch. The GPU model and memory used were not recorded, so no minimum hardware requirement is claimed here.

## 5. Configure names and paths

In the configuration cell:

| Variable | Meaning |
|---|---|
| `MODEL_NAME` | Base model (`openai/whisper-large-v2`) |
| `DATASET_NAME` | Hub dataset ID |
| `WHISPER_PROMPT_LANGUAGE` | Decoder prompt language (`English` in the original workflow) |
| `HF_REPO_ID` | Hub repository for the adapter |
| `OUTPUT_DIR` | Local training output folder |

**Important:** `HF_REPO_ID` points at the original author's repository. If you re-train, change it to a repository you own, or load the adapter from a local path.

## 6. Hugging Face authentication (optional)

Needed only to upload an adapter to the Hub. The notebook contains a commented-out cell:

```python
from getpass import getpass
from huggingface_hub import login
# hf_token = getpass("Enter your Hugging Face token: ")
# login(token=hf_token)
```

Never hard-code a token.

## 7. Run the notebook

Run cells in order. A clean runtime is recommended when testing.

1. install dependencies
2. verify runtime / GPU
3. (optional) authenticate with Hugging Face
4. configure project settings
5. load dataset
6. load feature extractor, tokenizer, processor
7. resample audio and build features
8. define data collator and WER metric
9. load Whisper large-v2 and apply LoRA
10. train
11. save or upload the adapter
12. load the adapter and evaluate on the test set
13. load the 8-bit inference model
14. transcribe a file / launch Gradio

## 8. Saving the adapter — please read

With the notebook's training arguments (424 steps, Trainer default save interval), it is unlikely that a checkpoint is written to `OUTPUT_DIR` during training, and the notebook's save step is the commented-out `push_to_hub`. If you do not push to the Hub, add a local save before the runtime ends, for example `model.save_pretrained(OUTPUT_DIR)`. Please verify this in your own run.

## 9. Inference only

To use an existing adapter without training, run the configuration cell, then the 8-bit inference cells (sections 16–18), with `HF_REPO_ID` pointing to an adapter you can access.

## 10. Known evaluation note

Use the corrected evaluation cell (section 15). The historical 20.40% WER came from a loop that leaked reference tokens and is not a clean benchmark.
