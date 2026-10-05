# Security Notes

## Credentials

Never commit Hugging Face tokens, API keys, passwords, or other credentials.

The notebook keeps authentication in a commented-out `getpass` + `login` cell instead of embedding a token. Do not replace this with a hard-coded token. Check notebook **outputs** too, since tokens can appear in cell output or logs.

If any older copy of the notebook contains an exposed credential, revoke or rotate it before publishing.

## User audio and Gradio

The demo accepts uploaded audio and microphone recordings. Speech can contain personal information.

- `iface.launch(share=True)` creates a temporary public link. Anyone with the link can use the demo while it runs. Do not use it with private or sensitive recordings, and stop the cell when finished.
- Do not commit recordings or screenshots that reveal other people's speech or data.
- Gradio may store temporary copies of uploaded files on the host machine.

## Dataset and model artefacts

- Dataset files and caches are excluded by `.gitignore`. Review the dataset licence before redistributing any part of it.
- Adapter weights and checkpoints are excluded by `.gitignore`. Publish the adapter via the Hugging Face Hub deliberately, after reviewing its model card and permissions.
- Confirm that the repository referenced by `HF_REPO_ID` is public or private as you intend.

## Supply chain

Dependencies are not pinned and some (for example `bitsandbytes`) are sensitive to CUDA/driver versions. Pin tested versions before relying on the project, and avoid installing development builds from moving Git branches.

## Important reminder

`.gitignore` reduces accidental commits, but it is not a security boundary. Always inspect the files you are about to commit.
