# Data

This repository contains **no audio and no dataset files**.

## Dataset used

The notebook loads **Nigerian Pidgin 1.0** from the Hugging Face Hub:

```text
asr-nigerian-pidgin/nigerian-pidgin-1.0
```

Language code used by the dataset: `pcm`. Splits: `train`, `validation`, `test`.

In the recorded experiment, `train` and `validation` were combined (2,708 + 677 = 3,385 examples) and `test` (892 examples) was held out.

## Columns the notebook reads

An `audio` column (resampled to 16 kHz) and a `sentence` column (the Nigerian Pidgin transcript).

## Before publishing or redistributing

- Review the dataset's licence and terms on its Hub page. This project has not established them.
- Do not commit audio, transcripts, or cached dataset files.
- Do not commit your own recordings (for example, Gradio microphone inputs).

## Not yet documented

Speaker demographics, regional/accent coverage, recording conditions, and domain coverage are not described in this project. Add them from the dataset card if you evaluate fairness or coverage (see `responsible-ai/AI_EVALUATION_PLAN.md`).
