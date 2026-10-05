# Release Readiness

Use this checklist before any release beyond the current prototype (for example, a public model card, a hosted demo, or a user pilot).

**Current recommendation: not ready for release as a product.** Suitable as a documented prototype once Gate 1 is complete.

## Gate 1 — Publish as a portfolio/research repository
- [ ] Corrected WER run and recorded with decoding settings
- [ ] Notebook re-run from a clean runtime
- [ ] Dependencies pinned and tested
- [ ] Licences reviewed (code, Whisper, dataset); `LICENSE` added
- [ ] Notebook outputs reviewed for tokens, private URLs, personal data
- [ ] README results table matches the evaluation report
- [ ] Adapter saved and its Hub repository permissions checked

## Gate 2 — Public model card / shared adapter
- [ ] Zero-shot baseline and fine-tuned comparison reported
- [ ] CER and normalised WER reported
- [ ] Prompt-language effect examined
- [ ] Known failure modes and error examples documented
- [ ] Intended use and out-of-scope use stated
- [ ] Dataset provenance and consent questions addressed

## Gate 3 — User pilot or hosted demo
- [ ] Slice evaluation completed with sample sizes
- [ ] Robustness tests (noise, silence, long audio) done
- [ ] Privacy notice and data-retention approach defined
- [ ] No reliance on temporary `share=True` links
- [ ] Monitoring and a way to report bad transcripts
- [ ] Target performance agreed with users, and met

## Decision framework
| Outcome | Condition |
|---|---|
| **Go** | All items in the relevant gate complete; open risks rated L or accepted in writing |
| **Conditional go** | Minor items open with owners and dates; no H risks unaddressed |
| **No-go** | Any unresolved H risk (e.g. unverified results, unclear licence, privacy exposure) |

Record the date, decision, reviewer, and open items each time the checklist is used.
