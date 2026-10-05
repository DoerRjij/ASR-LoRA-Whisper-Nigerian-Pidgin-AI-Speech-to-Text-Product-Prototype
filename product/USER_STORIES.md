# User Stories

Status key: **Implemented** · **Proposed**. Personas are hypotheses.

## Implemented

**US-1 — Train an adapter (learner/researcher)**
As a researcher, I want to fine-tune Whisper on Nigerian Pidgin with LoRA so that I can adapt a large model without training all of its weights.
*Acceptance:* the notebook runs training end-to-end in a Colab GPU runtime and produces a LoRA adapter.

**US-2 — Measure accuracy**
As a researcher, I want a WER evaluation on a held-out test set so that I can quantify transcription errors.
*Acceptance:* the evaluation cell generates predictions for all 892 test examples without using reference tokens as decoder inputs and prints WER. *(Cell implemented; corrected result pending.)*

**US-3 — Transcribe a file**
As a developer, I want a `transcribe_audio` function so that I can get a Pidgin transcript from an audio file.
*Acceptance:* given a path, the function returns a text string.

**US-4 — Try the demo**
As a non-technical visitor, I want to upload or record audio in a web page so that I can see the model work.
*Acceptance:* the Gradio interface accepts upload or microphone input and shows a transcript.

## Proposed

**US-5 — Trust the numbers**
As a reader, I want a clean WER with its setup documented so that I can compare it with other work.
*Acceptance:* WER, CER, decoding settings, dataset split, and software versions are published together.

**US-6 — Compare against a baseline**
As a reviewer, I want to see zero-shot Whisper results under the same settings so that I can judge the value of fine-tuning.
*Acceptance:* a table showing baseline vs fine-tuned results on the same test set.

**US-7 — Keep my adapter**
As a learner, I want the notebook to save the adapter locally so that I do not lose it when the runtime ends.
*Acceptance:* after training, adapter files exist in `OUTPUT_DIR`.

**US-8 — Understand where it fails**
As a product owner, I want errors broken down by speaker, accent, noise, and sentence type so that I can target improvements.
*Acceptance:* a slice report with sample sizes, using available metadata.

**US-9 — Long recordings**
As a media user, I want to transcribe recordings longer than a short clip so that the tool is useful in practice.
*Acceptance:* a documented chunking approach with tested examples.

**US-10 — Safe demo**
As a speaker, I want to know how my recording is handled so that I can decide whether to use the demo.
*Acceptance:* the demo states what is stored, for how long, and who can access it.
