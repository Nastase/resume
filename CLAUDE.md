# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build

Compile the resume locally with XeLaTeX:

```bash
xelatex -interaction=errorstopmode resume.tex
```

The CI/CD pipeline (`.github/workflows/main.yml`) runs this automatically on every push to `main` using the `texlive/texlive:latest` Docker image and uploads the resulting PDF as a GitHub Actions artifact.

## Architecture

This is a modular LaTeX resume using the [Awesome CV](https://github.com/posquit0/Awesome-CV) template.

- **`resume.tex`** — root document; sets global options (page size, color, fonts) and `\input{}`s each section
- **`awesome-cv.cls`** — the Awesome CV LaTeX class; controls all styling and layout macros
- **`resume/`** — one `.tex` file per section (summary, skills, experience, education, certificates, committees, extracurricular, honors, presentation, writing)

Several sections are currently commented out in `resume.tex` with `%\input{resume/<section>}` — they exist as files but are excluded from the compiled output.

## Key LaTeX Commands

Awesome CV provides these section-level macros (defined in `awesome-cv.cls`):

- `\cvsection{Title}` — section header
- `\cventry{...}` — experience/education entry
- `\cvskill{Category}{Items}` — skill line

When editing content, only modify files in `resume/`. Changes to `awesome-cv.cls` affect global styling for all sections.

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>: <description>
```

Common types for this repo: `feat` (new section or entry), `fix` (correction), `style` (formatting/layout), `chore` (CI, config).
