# GitHub CI Pipeline Setup

This repository shows how to set up a **Continuous Integration (CI) pipeline** using GitHub Actions to automate build, test, and deployment.

---

## Features

* Automated build on push or pull request
* Run tests and lint checks
* Optional deployment step

---

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```

2. **Install dependencies** (for Node.js projects):

   ```bash
   npm install
   ```

3. **Add GitHub secrets** (if required):

   * Go to **Settings → Secrets → Actions**
   * Example: `NODE_ENV`, `API_KEY`, `DEPLOY_KEY`

---

## Workflow Configuration

The workflow file is located at `.github/workflows/ci.yml`. Example:

```yaml
name: CI Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '20'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

      - name: Run lint
        run: npm run lint

      - name: Deploy (optional)
        if: github.ref == 'refs/heads/main'
        run: npm run deploy
```

---

## Usage

1. Push your code to `main` or `develop`.
2. GitHub Actions will automatically run the CI workflow.
3. Check the **Actions** tab for build status and test results.

---

## License

This project is licensed under the MIT License.
