# GitHub Publishing and Updating Guide

This guide is for a first-time Git/GitHub user.

## The basic workflow

```text
Edit files → git status → git add . → git commit -m "..." → git push → GitHub
```

## Part 1 — First publication

### 1. Create a GitHub repository

Suggested name:

```text
Nigerian-Pidgin-ASR-Whisper-LoRA
```

The project already contains a README, so do not create a second one when creating the remote repository.

### 2. Open Git Bash/PowerShell in the project folder

```bash
cd path/to/Nigerian-Pidgin-ASR-Whisper-LoRA
```

### 3. Initialise Git and use `main`

```bash
git init
git branch -M main
```

### 4. Inspect the project

```bash
git status
```

Look carefully for credentials, audio files, model weights, notebook outputs, and large files.

### 5. Stage, inspect, commit

```bash
git add .
git status
git commit -m "Initial Nigerian Pidgin ASR Whisper LoRA project"
```

### 6. Connect to GitHub and push

```bash
git remote add origin https://github.com/YOUR-USERNAME/Nigerian-Pidgin-ASR-Whisper-LoRA.git
git remote -v
git push -u origin main
```

Future pushes normally use `git push`.

## Part 2 — Updating later

```bash
git status
git add .
git commit -m "Describe the change"
git push
```

Example:

```bash
git add ASR_Whisper_LoRA_Nigerian_Pidgin.ipynb
git commit -m "Add corrected WER evaluation results"
git push
```

## Part 3 — Safer routine before every push

```bash
git status
git diff
git add .
git status
git commit -m "Describe the change"
git push
```

Notebooks need extra care: review cell outputs for tokens, private URLs (including Gradio share links), file paths, and audio widgets. Consider clearing outputs before committing, or deliberately keep only outputs you have reviewed.

## Part 4 — Common situations

- **Nothing to commit:** `nothing to commit, working tree clean` means no changes since the last commit.
- **Wrong remote URL:** `git remote set-url origin https://github.com/YOUR-USERNAME/Nigerian-Pidgin-ASR-Whisper-LoRA.git`
- **Undo an uncommitted file change:** inspect with `git diff`, then, only if you are certain, `git restore path/to/file`.
- **Large file rejected:** model weights and audio should not be in Git. Use the Hugging Face Hub for adapters.

## Part 5 — If a secret is accidentally committed

1. Revoke or rotate the credential immediately.
2. Remove the secret from the project.
3. Deleting the current file does not remove it from Git history.
4. Clean the history as appropriate before considering the repository safe.

## Part 6 — Useful commit messages

Good:

```text
Initial Nigerian Pidgin ASR Whisper LoRA project
Add corrected WER evaluation
Pin tested dependency versions
Document dataset licence review
Add local adapter save step
```

Avoid vague messages such as `changes`, `update`, `stuff`.

## Final pre-publication checklist

- [ ] No API keys or access tokens (including in notebook outputs)
- [ ] No audio recordings or private conversations
- [ ] No model weights or checkpoints
- [ ] No unintended large files
- [ ] README is present and its results section is honest about the WER status
- [ ] requirements.txt is present (ideally pinned)
- [ ] .gitignore is present
- [ ] Licence has been reviewed for code, Whisper, and the dataset
- [ ] `HF_REPO_ID` points to a repository you intend to reference
- [ ] Notebook has been run from a clean runtime
