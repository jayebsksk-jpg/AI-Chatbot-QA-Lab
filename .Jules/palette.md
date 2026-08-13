# Palette's Journal

This journal documents critical UX and accessibility learnings for this repository.

## 2026-08-09 - WCAG Color Contrast & Proper DOM-based aria-live Announcements
**Learning:** For interactive custom components (such as our random theme/palette generator), asserting that colors are contrast-compliant is vital. Standard vibrant values (e.g. Cyan-600, Emerald-600, Red-600, Amber-600) often fail WCAG AA's minimum 4.5:1 ratio against white text. Instead, using deeper 900-series shades guarantees compliant contrast ratio over 10:1 (exceeding WCAG AAA). Furthermore, a statically placed `aria-live` element whose visibility/opacity is toggled is frequently ignored or misread by screen readers on page load. To fix this, keeping the `aria-live` container initially empty and dynamically inserting text content via DOM APIs (e.g. `textContent`) on action forces the screen reader to intercept the node insertion and correctly announce the state change.
**Action:** Always verify all color choices with contrast checking tools (requiring >= 4.5:1 for standard text) and dynamically populate empty `aria-live` containers to ensure proper announcements.

## 2026-08-11 - Theme-Driven Outlines and Action-Discoverable Keyboard Hotkeys
**Learning:** Hardcoded focus-visible outline rings on custom buttons disrupt the visual cohesion of dynamically-themed sites by clashing with active color-ways. Leveraging CSS custom properties (`var(--p)`) on both backgrounds and focus-ring outlines unifies interactive aesthetics across color cycles. Additionally, incorporating semantic `<kbd>` layout hints alongside simple global event handlers dramatically boosts power-user efficiency without introducing visual noise or conflicting with default screen-reader navigation.
**Action:** Always map focus-ring styling properties directly to dynamic theme tokens and pair simple keystroke listeners with standard HTML `<kbd>` tooltips for intuitive discovery.

## 2026-08-12 - Cognitive Color Previews and Temporary Visual State Transitions
**Learning:** Raw hexadecimal values lack immediate cognitive visual clarity, forcing users to mentally construct colors. Providing an adjacent visual preview swatch paired with a semantic `role="img"` and screen-reader accessible `aria-label` satisfies both sighted and assistive use cases. Furthermore, while ARIA live announcements confirm actions for screen readers, standard users benefit heavily from temporary, interactive feedback states on buttons (like temporarily changing the "Copy" text and styling to a filled state). These temporary visual cues deliver immediate, gratifying visual confirmation of action success without cluttering the long-term UI state.
**Action:** Always pair abstract data (like hex codes) with matching visual helpers, and implement transient transition states on interactive elements to acknowledge actions visually.
