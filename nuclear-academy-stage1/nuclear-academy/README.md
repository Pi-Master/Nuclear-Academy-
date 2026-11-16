# Nuclear Academy

A static, framework-free nuclear engineering education site (vanilla HTML, CSS and JavaScript), designed for GitHub Pages.

**Status: Stage 1 (architecture and curriculum map) only.** `index.html` is still the original single-file site, unchanged and working. The new folders hold the curriculum plan, content templates and documentation for later stages.

| Path | Purpose |
|---|---|
| `index.html` | Current working site (unchanged in Stage 1) |
| `assets/css`, `assets/js`, `assets/images` | Shared styling, application code, SVG diagrams (empty until Stage 2) |
| `content/curriculum.json` | Index of the 10 schools |
| `content/<school>/school.json` | Curriculum for one school: 3 levels, chapters, subchapters, objectives, suggested diagrams, simulations, assessments |
| `content/_templates/` | Templates for chapters, quizzes, diagrams and simulations |
| `content/shared/` | Cross-school data such as the glossary (Stage 3+) |
| `simulations/` | One folder per simulation (Stage 6) |
| `docs/` | `CURRICULUM.md`, `SCHEMA.md`, `MIGRATION.md`, `SOURCES.md` |

All paths are relative, so the site works from a GitHub Pages project URL.
