# Migration plan: single-file site to multi-file

## Stage 1 result
`index.html` is the original site, byte-identical to the version that was working. Nothing was removed or rewritten.

## Where existing features will live
| Existing feature | Current form | Planned home |
|---|---|---|
| Lessons b1, b2, b3 | `L` array in `index.html` | Nuclear Physics Foundation (`np-f-1`, `np-f-2`, `np-f-3`) |
| Lessons i1, i2 | same | Nuclear Physics Intermediate (`np-i-3`, `np-i-2`) |
| Lesson i3 | same | Reactor Engineering Foundation (`re-f-1`) |
| Lesson u1 | same | Nuclear Physics Advanced (`np-a-3`) |
| Lesson u2 | same | Thermal Hydraulics Intermediate (`th-i-2`) |
| Lesson u3 | same | Nuclear Safety Foundation (`ns-f-2`) |
| Textbook ch5, ch10, ch11 | `T` array | Nuclear Physics Intermediate (`np-i-1`, `np-i-2`, `np-i-3`) |
| Diagrams atom, fission, pwr, shield | `DG` array | `np-f-1`, `np-i-3`, `re-i-1`, `rs-f-1`; move SVG strings to `assets/images/` |
| Atom explorer | `atom()` function | `simulations/atom-explorer/`, linked from `np-f-1` |
| Glossary and flashcards | `G` array | `content/shared/glossary.json` |
| Progress, bookmarks, text size | localStorage keys `na_p`, `na_x` | Keep the same keys and ID formats |

Some chapters of a school overlap with later schools (for example lesson i3 also supports Reactor Engineering Intermediate). Mappings can be revisited when content is moved.

## Planned order
1. Stage 2: split CSS and JS out of `index.html` into `assets/`, keeping behaviour identical, then restyle.
2. Stage 3: move lesson and textbook data into `content/` files and load them through one loader.
3. Later stages as in the roadmap.

## Outstanding technical decisions (need your input before Stage 2)
- **Loading JSON:** `fetch()` of local JSON files works on GitHub Pages but is blocked if someone opens `index.html` by double-clicking it (`file://`). Options: (a) JSON plus a note to use a simple local server or GitHub Pages; (b) store content as `.js` files loaded with `<script>` tags, which also work from `file://`. I lean towards (b) for a no-build, no-server workflow, but it is your call.
- **Equation display:** options are plain Unicode text (current), native MathML, or a self-hosted copy of KaTeX (one dependency, no network needed). Not decided.
