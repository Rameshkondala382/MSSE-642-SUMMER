#### [🔙 Back to README](../../README.md)

# Week 1 Discussion: GitHub Actions and Markdown Linting for Text-Based Repositories

## Introduction

In this exercise, I explored how GitHub Actions can be used to automate linting of Markdown files in a repository dedicated to writing-based content such as discussion posts and documentation. The goal was to simulate a real-world CI (Continuous Integration) workflow while avoiding over-enforcement of markdown formatting rules that are unhelpful in text-heavy files.

## GitHub Actions Setup

I created a workflow file at:

```
.github/workflows/md-lint.yml
```

This file defines a GitHub Actions job that runs `markdownlint-cli` whenever a commit or pull request is made to the `main` branch. The CI job:

* Runs in a temporary `ubuntu-latest` runner
* Sets up Node.js (required by markdownlint)
* Installs `markdownlint-cli` globally
* Lints all `.md` files using the default or custom rules

```yaml
- name: Run markdownlint
  run: markdownlint "**/*.md"
```

## Managing PR Failures and Rule Fatigue

Initially, the strict default rules caused pull requests to fail due to trivial issues such as:

* Trailing spaces (`MD009`)
* Missing newline at the end of file (`MD047`)
* Blank lines around headings (`MD022`)

To reduce friction, I created a `.markdownlint.json` configuration file to disable rules that are not meaningful in a text-focused repo. This keeps the workflow helpful without being obstructive.

### `.markdownlint.json`

```json
{
  "MD009": false,
  "MD012": false,
  "MD013": false,
  "MD022": false,
  "MD036": false,
  "MD041": false,
  "MD047": false
}
```

## Enabling Flexible CI: Warning Instead of Failing

To make the CI workflow more forgiving, I modified the linter step to avoid failing the PR. This allows the linting to run and output warnings without blocking the merge:

```yaml
- name: Run markdownlint (non-blocking)
  run: markdownlint "**/*.md" || echo "Markdownlint completed with warnings."
```

This solution is ideal for future-proofing. It allows continuous integration feedback while respecting the nature of a writing-heavy workflow.

## Branch Protection

I enabled GitHub's branch protection rules to require review approvals before merging into the `main` branch. This added structure to my workflow and forced the use of pull requests for all changes. Since I'm working solo, I temporarily disabled the review requirement to merge when I encountered approval blockers.

## Diagram: GitHub Actions Workflow for Markdown Linting

```
+-----------------------+
| GitHub Repository     |
+----------+------------+
           |
           v
+-----------------------+
| Push / Pull Request   |
+----------+------------+
           |
           v
+-----------------------+
| GitHub Actions Runner |
| ubuntu-latest         |
+----------+------------+
           |
           v
+----------------------------+
| Checkout Repo             |
| Setup Node.js             |
| Install markdownlint-cli  |
| Run markdownlint          |
+----------------------------+
```

**Source:** Adapted from GitHub Actions documentation
[https://docs.github.com/en/actions](https://docs.github.com/en/actions)

## References

* GitHub Actions Documentation:
  [https://docs.github.com/en/actions](https://docs.github.com/en/actions)
* markdownlint Rules Reference:
  [https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md](https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md)
* markdownlint-cli (npm):
  [https://www.npmjs.com/package/markdownlint-cli](https://www.npmjs.com/package/markdownlint-cli)
