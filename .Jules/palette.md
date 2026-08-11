# Palette's Journal

This journal documents critical UX and accessibility learnings for this repository.

## 2026-08-09 - WCAG Color Contrast & Proper DOM-based aria-live Announcements
**Learning:** For interactive custom components (such as our random theme/palette generator), asserting that colors are contrast-compliant is vital. Standard vibrant values (e.g. Cyan-600, Emerald-600, Red-600, Amber-600) often fail WCAG AA's minimum 4.5:1 ratio against white text. Instead, using deeper 900-series shades guarantees compliant contrast ratio over 10:1 (exceeding WCAG AAA). Furthermore, a statically placed `aria-live` element whose visibility/opacity is toggled is frequently ignored or misread by screen readers on page load. To fix this, keeping the `aria-live` container initially empty and dynamically inserting text content via DOM APIs (e.g. `textContent`) on action forces the screen reader to intercept the node insertion and correctly announce the state change.
**Action:** Always verify all color choices with contrast checking tools (requiring >= 4.5:1 for standard text) and dynamically populate empty `aria-live` containers to ensure proper announcements.
