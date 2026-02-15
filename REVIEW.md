# Code Review: `public/index.html`

## Rating
**4/10**

Major portions of the MVP spec are implemented (single-file app, AFD fetch, glossary, section parsing), but there are significant requirement misses and several functional bugs.

## JS Bugs
- **No mode toggle behavior implemented (spec miss + behavior bug):** The UI always renders both columns and never switches modes. Required two-mode interaction is absent. (`public/index.html:925`, `public/index.html:937`)
- **Tooltip annotation pass can reprocess injected markup:** `annotateText()` repeatedly runs regex replacement on an already HTML-expanded string, which can match glossary terms inside tooltip content and create nested/broken spans. (`public/index.html:849`)
- **Potential HTML injection in Plain English path:** `translateToPlainEnglish()` returns unescaped HTML and is inserted via `innerHTML`. If upstream text ever includes HTML-like payload, it is rendered. (`public/index.html:830`, `public/index.html:834`, `public/index.html:940`)
- **Cache is write-only:** Spec asks to cache in `sessionStorage`, but cached data is never read before refetching. (`public/index.html:1000`)
- **Time conversion logic is hardcoded to PST for `Z` conversions:** This is wrong for DST/PDT and for non-California offices. (`public/index.html:786`)
- **Issue time uses viewer locale, not office local time:** `toLocaleString` has no explicit office time zone mapping, so "local time" drifts by user location. (`public/index.html:988`)
- **No `response.ok` checks before JSON parsing:** Failed HTTP responses go straight to `.json()`, producing less controlled error handling. (`public/index.html:962`, `public/index.html:971`)
- **Section-id generation can produce invalid/fragile anchors:** IDs are built from raw section titles with only spaces replaced, leaving punctuation/slashes unnormalized. (`public/index.html:922`, `public/index.html:935`)

## Leaked Abbreviations (Plain English)
These are likely to remain in rendered "Plain English" because they are in glossary/spec language but not expanded in `translateToPlainEnglish()`:
- `LI`
- `OFB`
- `FROPA`
- `GS`
- `UTC` (non-`Z` forms)
- `WFO`
- `CWA`
- `RAOB`
- `MOS`

## Missing Glossary Terms (per SPEC minimum set)
- `NW flow`
- `SW flow`
- `SE flow`

The spec explicitly calls out "NW/SW/SE flow patterns"; those exact directional flow pattern entries are not present in `GLOSSARY`.

## CSS Issues
- **No visible keyboard focus styling** for links/select/pills/tooltips, hurting keyboard accessibility. (global styles; no `:focus` / `:focus-visible` rules)
- **Tooltip is hover-only** (`.jargon:hover .tip`), which is unreliable on touch/mobile and inaccessible for keyboard users. (`public/index.html:224`)
- **Tooltip overflow risk:** absolutely positioned centered tooltip with `max-width: 280px` can overflow viewport edges near container boundaries. (`public/index.html:210`)
- **Low-contrast small text risk:** several 0.7–0.8rem labels with muted color likely miss WCAG contrast/readability targets. (`public/index.html:131`, `public/index.html:241`)

## UX Problems
- **Missing confidence indicator** (required in spec).
- **Missing mode toggle UI** (required two-pill switch).
- **Editorial reading goal diluted** by always-on dual-column layout instead of mode-based focus.
- **No click interaction for jargon definitions** despite spec saying hover/click.
- **Footer data attribution mismatch with spec format:** should show `Data: NWS {office}` (dynamic office), currently static "National Weather Service" text. (`public/index.html:283`)
- **`target="_blank"` links omit `rel="noopener noreferrer"`**, a UX/security hygiene issue. (`public/index.html:283`, `public/index.html:284`, `public/index.html:285`)

## Requirement Coverage Summary
- Implemented: single-file vanilla app, AFD fetch, section parsing, key takeaway, section nav, glossary annotations, mobile breakpoint.
- Missing/partial vs spec: mode toggle, confidence indicator, office-local time handling, glossary directional flow terms, cache read path, click-accessible annotations.
