# Portfolio Case Study — Nigerian Pidgin Speech Recognition

**Role:** Builder and documenter (data prep, fine-tuning, evaluation, demo, documentation).
**Stack:** Whisper large-v2, LoRA/PEFT, Hugging Face Transformers/Datasets, BitsAndBytes (8-bit inference), Gradio, Google Colab.

## The challenge
Nigerian Pidgin is widely spoken but poorly served by speech-recognition tools. I wanted to see how far a parameter-efficient approach could adapt a strong multilingual model with limited compute.

## What I built
- A pipeline that prepares 3,385 training and 892 test utterances for Whisper.
- A LoRA adapter (r=32) on a frozen Whisper large-v2, trained for one epoch.
- A WER evaluation loop and an 8-bit inference path.
- A Gradio demo that accepts uploads and microphone recordings.

## What I learned (and corrected)
- **Evaluation integrity:** I found that my original evaluation fed reference tokens into the decoder, which made the 20.40% WER unreliable. I rewrote the loop, and I report that number only as a historical result. The corrected WER has not been run yet, so I do not claim one.
- **Honest descriptions:** my early notes implied INT8 training; the notebook actually trains in standard precision and uses 8-bit only at inference. I fixed the documentation to match the code.
- **Language prompts:** Whisper had no Pidgin option, so I used an English decoder prompt with Pidgin labels, and documented that it is a prompt choice with untested effects.

## What I would do next
Run the corrected evaluation, add a zero-shot baseline, report CER and normalised WER, analyse errors by speaker and noise, and pin dependencies.

## Why it matters
It shows end-to-end practical ML work on a low-resource language, along with the habits that matter in real projects: checking for data leakage, separating implemented from proposed work, and not overclaiming results.
