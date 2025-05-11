# MarkdownLint Rule Configuration

This document explains the custom `.markdownlint.json` configuration used in this repository. These rules are tailored for a writing-heavy markdown workflow (e.g., discussion posts, essays, documentation), where strict formatting is often more disruptive than helpful.

---

## 🔧 Disabled Rules

| Rule | Description | Reason for Disabling |
|------|-------------|----------------------|
| `MD009` | Trailing spaces | Often harmless in prose writing and can result from common typing behavior |
| `MD012` | Multiple consecutive blank lines | Blank lines are often intentional for readability when writing |
| `MD013` | Line length | Long lines are acceptable in essays and markdown is usually rendered with wrapping |
| `MD022` | Blank lines around headings | Strict spacing around headings is less important in freeform writing |
| `MD036` | Emphasis used instead of heading | Bolded text like `**Note:**` is common and doesn't need to be a heading |
| `MD041` | First line must be a heading | Documents may begin with a comment or preamble instead of a title |
| `MD047` | Files should end with a single newline | Trailing newline issues are not significant for markdown rendering |

---

## 📁 Related File: `.markdownlint.json`

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
