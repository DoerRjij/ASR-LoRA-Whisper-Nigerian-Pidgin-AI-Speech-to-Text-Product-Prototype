# AI Risk Assessment

Status: initial register for a prototype. Ratings are judgement calls (H/M/L), not measurements.

| ID | Risk | Likelihood / Impact | Current treatment | Proposed mitigation |
|---|---|---|---|---|
| R-1 | **Evaluation leakage** inflates reported accuracy | Occurred / H | Loop corrected; historical WER labelled as contaminated | Run corrected evaluation; report only that |
| R-2 | **Overclaiming** results or capabilities | M / H | Docs separate implemented vs proposed | Review every public claim against the evaluation report |
| R-3 | **English decoder prompt** biases output toward English spelling or phrasing | M / M | Documented as a prompt choice | Test alternative prompts; error analysis of English-ification |
| R-4 | **Uneven performance** across accents, regions, genders, ages, noise | M / H | None; not evaluated | Slice evaluation; state coverage limits |
| R-5 | **Non-standard spelling** makes WER misleading | H / M | None | Report CER and normalised WER |
| R-6 | **Hallucinated text** on silence, noise, or unclear speech | M / M | None | Test non-speech audio; consider confidence/voice-activity checks |
| R-7 | **Dataset licence or consent** unclear | M / H | Dataset not redistributed | Review dataset card/terms; document provenance |
| R-8 | **Privacy of user speech** in the demo (microphone, share link) | M / H | Security notes warn against sensitive audio | Privacy notice; avoid public share links for real users; no logging by default |
| R-9 | **Credential exposure** (Hugging Face token) | L–M / H | Token never hard-coded; commented-out login; `.gitignore` | Check notebook outputs and history before each push; rotate if exposed |
| R-10 | **Irreproducibility** (unpinned deps, no seeds, hardware unrecorded) | H / M | `requirements.txt` unpinned, noted | Pin versions, set seeds, record hardware |
| R-11 | **Lost adapter** (not saved locally) | M / M | Optional Hub upload | Add local save step |
| R-12 | **Misuse** (covert transcription, surveillance of speakers) | L–M / H | None | State intended uses; avoid positioning for monitoring; consider usage guidance in model card |
| R-13 | **Harmful or sensitive transcripts** (names, health, political speech) | M / M | None | Treat transcripts as personal data; retention guidance |
| R-14 | **Quantisation accuracy loss** at inference | L–M / M | None measured | Compare 8-bit vs full-precision WER |

## Open governance questions
- Under what licence can the adapter be shared, given Whisper's and the dataset's terms?
- Did speakers consent to uses beyond the dataset's stated purpose?
- Who is accountable for correcting errors found after publication?
- What intended-use statement will the model card carry?
