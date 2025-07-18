# 🤖 AI Code Reviewer using GPT-4

This GitHub Action automatically reviews Pull Requests using **OpenAI GPT-4** and comments suggestions directly on the PR.  
Boost your code quality with the power of AI. Built using GitHub Actions + OpenAI API.

---

## 📸 Demo Proof

✅ Below is a live screenshot showing the action successfully triggered on a PR:

![AI Code Review Screenshot](<paste_your_screenshot_link_here>)

👉 **Live Demo PR:** [Click to view](https://github.com/vansh-1410/ai-code-reviewer-demo/pull/1)

---

## ⚙️ How to Use This GitHub Action

1. Generate your **OpenAI API Key** from [https://platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys)

2. Go to your GitHub repo → **Settings** → **Secrets and variables** → **Actions**

3. Click **New repository secret** → Add the following:
   - Name: `OPENAI_API_KEY`
   - Value: *your OpenAI API key*

4. Create the following workflow file in your repo:

📁 `.github/workflows/code-review.yml`

```yaml
name: AI Code Reviewer

on:
  pull_request:
    types:
      - opened
      - synchronize

permissions: write-all

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3

      - name: AI Code Reviewer
        uses: freeedcom/ai-codereviewer@main
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
          OPENAI_API_MODEL: "gpt-4" # Optional
          exclude: "**/*.json, **/*.md" # Optional
