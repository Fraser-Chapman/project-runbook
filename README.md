# Project Runbook

A single-file, no-dependency web app for working through a "starting a new project" runbook. Each project gets its own copy of the checklist, so you can see at a glance whether anything has been missed.

## Use

Open `project-runbook.html` in Chrome or Edge. There is no build step and nothing is loaded from the network.

- **New project** copies the current template into a fresh checklist.
- Each question has an **Answer** (Yes / No / Unsure), a **Status** (To do / In progress / Done / N/A), an owner and notes.
- **Review open items** lists everything not done, answered Unsure, or missing a follow-up.
- **Export Markdown** produces a checklist you can paste into Obsidian.
- **Backup / restore** copies all projects and the template as JSON. In Chrome/Edge you can also pick a file for automatic backup after every change.
- Light and dark themes, plus confetti when things are completed.

## Template syntax

Edit the template with **Edit template**. It is plain nested Markdown bullets:

```
* Section
   * Question
      * Hint shown under the question
      * If yes: Follow-up field shown only when the answer is Yes
* Integrations
   * For each integration:
      * Question asked once per integration you add
```

- Top level is a section, second level is a question, third level is a hint.
- `If yes:`, `If no:` and `If unsure:` become follow-up inputs that appear for that answer.
- `For each <thing>:` makes a section repeatable. You add items by name and each gets its own copy of the questions.

Changes to the template only apply to new projects.

## Data

Everything is stored in the browser's localStorage, so each browser or app keeps its own data. Use Backup / restore to move projects between copies. Backup files contain your project data, so they are git-ignored.

## Code layout

Everything is in `project-runbook.html`: CSS in a `<style>` block, markup, then one `<script>` split by `// ----------` comment headers (template parsing, rendering, groups, confetti, export, backup, theme).
