# AI Evaluation Plan (proposed)

Nothing in this plan has been run unless stated. Current evidence: one historical, contaminated WER (20.40%) and an unrun corrected evaluation cell.

## 1. Goals
Establish a trustworthy accuracy figure, show whether fine-tuning beats the base model, and find where the model fails.

## 2. Test-set discipline
- The 892-example test split stays untouched during tuning.
- Because train and validation were merged, any further tuning needs a new validation split carved from training data.
- Decoding must not use reference tokens. Record the decoding settings (`max_length`, prompt, beam/greedy).

## 3. Metrics
| Metric | Purpose |
|---|---|
| WER (as in the notebook) | Headline, comparable with the historical setup |
| Normalised WER (lower-casing, punctuation handling; rules documented) | Separates spelling/formatting variation from real errors |
| CER | Useful when Pidgin spelling is not standardised |
| Substitution / deletion / insertion breakdown | Diagnose error types |
| Empty or repeated-output rate | Catch Whisper-style failures and hallucinated text |

Report all of them with the exact normalisation used.

## 4. Baselines and ablations
1. Zero-shot Whisper large-v2 (same prompt, same decoding).
2. Fine-tuned adapter (fp16/standard precision inference).
3. Fine-tuned adapter with 8-bit inference — to measure any accuracy cost of quantisation.
4. Decoder-prompt options (English vs alternatives).

## 5. Slice analysis
Where dataset metadata allows: speaker, gender, region/accent, recording conditions, utterance length, and vocabulary type (names, numbers, English loanwords, code-switching). Report sample sizes; do not draw conclusions from tiny slices.

## 6. Qualitative review
Read a sample of predictions, including the worst and a random set. Categorise errors (spelling variants, English-ification, dropped words, hallucinations).

## 7. Robustness
Test short clips, long clips, noise, phone-quality audio, and music/silence. Check for hallucinated text on non-speech.

## 8. Usability checks for the demo
Transcribe a handful of real recordings with consent; check latency and failure messages.

## 9. Reporting template
Dataset and split · model/adapter ID · software versions · hardware · decoding settings · normalisation · metrics with sample counts · known limitations.

## 10. Acceptance (to be defined)
No target WER is set because no use case has been defined. Set one with users before calling the model "good enough".
