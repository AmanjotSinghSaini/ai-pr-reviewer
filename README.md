# 🤖 AI PR Reviewer

An automated **AI-powered pull request reviewer** for GitHub.  
This action analyzes code changes in pull requests and provides **constructive feedback** on:

- ✅ Security issues  
- ✅ Code quality & potential bugs  
- ✅ Performance optimizations  
- ✅ Best practices & maintainability  
- ✅ Documentation improvements  

It saves developers time by catching issues early and offering actionable suggestions.  

---

## 🔧 Features
- 🛡️ Detects **security vulnerabilities** (e.g., injection risks, unsafe practices)  
- 🐛 Highlights **logic errors and potential bugs**  
- ⚡ Suggests **performance improvements**  
- 📐 Promotes **clean coding standards**  
- 📄 Improves **readability & documentation**  
- 📊 Supports **configurable limits** for files and lines reviewed  
- 🔌 Fully **reusable** across repositories  

---

## 📦 Installation & Usage

Add the following workflow to your repository (e.g., `.github/workflows/ai-review.yml`):

```yaml
name: AI Code Review
on:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  contents: read
  pull-requests: write

jobs:
  ai-review:
    uses: AmanjotSinghSaini/ai-pr-reviewer/.github/workflows/review.yml@main
    with:
      ai_model: 'gpt-4o'  # Options: gpt-4o-mini, gpt-4o, llama-3.1-70b, etc.
      exclude_paths: '*.md,*.txt,*.json,package-lock.json,yarn.lock,dist/*'
      max_file_lines: 200   # 0 = no limit, otherwise set max lines per file
      max_files: 4          # Maximum number of files to review
    secrets:
      AI_GITHUB_TOKEN: ${{ secrets.AI_GITHUB_TOKEN }}
