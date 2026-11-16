# Content schema (version 1)

Content is plain JSON, separate from application code. IDs are stable and used for links and saved progress.

## IDs
- School: `np re pg rs th me fc ns fe ap`
- Level: `<school>-<f|i|a>` (Foundation, Intermediate, Advanced), e.g. `np-i`
- Chapter: `<school>-<level>-<n>`, e.g. `np-i-3`; section: `np-i-3.2`
- Existing lessons keep their IDs (`b1`..`u3`) and textbook chapters keep `ch5`, `ch10`, `ch11`, so saved progress stays valid.

## Files
- `school.json`: school metadata, `levels[]` (objectives, `chapters[]` with `subchapters[]` and an `existing` mapping, suggested diagrams and simulations, assessment plan, difficulty 1-3) and a `finalExam` entry.
- Chapter files follow `_templates/chapter.template.json`, with block types `paragraph`, `definition`, `equation`, `diagram`, `note`, `keyFact`.
- Equations carry `plain`, optional `latex`, `variables` (symbol, meaning, unit), and a `workedExample` with steps, result and physical meaning.
- Quizzes follow `_templates/quiz.template.json`: `multiple-choice` and `numerical` (with unit and tolerance), explanations for correct and wrong answers, and a `scope` of chapter, topic, level or final.
- Diagrams and simulations follow their templates. Every simulation must state `principle` and `modelLimits`.
- References carry `verified: false` until the source has actually been checked.

## Chapter status values
`planned` (title and subchapters only; never shown to learners as a chapter), `draft`, `reviewed`, `published`. The site must only list chapters with real content.
