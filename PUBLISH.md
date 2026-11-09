# Publish this knowledge base to GitHub

The Markdown content is ready, but the connected GitHub actions available during this session can inspect repositories and create or update files inside an existing repository; they do not expose a create-repository operation. The repository name `TshepisoMLT/ai-knowledge-base` was checked and did not already exist.

## One-time setup

1. Open [GitHub's new repository page](https://github.com/new).
2. Create a repository named **`ai-knowledge-base`** under `TshepisoMLT`.
3. Choose Public or Private according to how widely you want your project context shared. Private is the safer default if later notes may include proprietary architecture details.
4. Leave the repository empty (do not add a README or license, because this folder already contains them).
5. Download and extract this ZIP, then from the extracted `ai-knowledge-base` folder run:

```bash
git init -b main
git add .
git commit -m "Add AI knowledge base and project context"
git remote add origin https://github.com/TshepisoMLT/ai-knowledge-base.git
git push -u origin main
```

Alternatively, upload the extracted files using GitHub's **Add file → Upload files** flow.

## After the empty repository exists

Share its URL in the conversation. The connected GitHub integration can then create the Markdown files in that existing repository. Do not paste a personal access token into chat.
