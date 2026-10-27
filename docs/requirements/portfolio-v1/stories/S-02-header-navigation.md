# S-02: Jump to a section from the header

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-02, NFR-03 · **Decisions:** Q-01
- **Depends on stories:** S-01

## User story
As a visitor, I want links in the header that take me straight to each section, so that I can
reach the part I care about without scrolling through the whole page.

## Acceptance criteria
1. **Link lands on the section heading**
   - Given the visitor is anywhere on the home page
   - When they activate "About", "Projects", "Skills" or "Contact" in the header (mouse, touch or keyboard)
   - Then the page moves to that section and its heading is fully visible below the header, not hidden under it, at 320, 375, 768 and 1280 px and at 375 px in landscape
2. **All four links fit in one row**
   - Given a screen 320 px wide
   - When the visitor looks at the header
   - Then the four links About · Projects · Skills · Contact are shown in one row, and there is no hamburger menu
3. **Header stays visible while scrolling**
   - Given a screen taller than 480 px
   - When the visitor scrolls down the page
   - Then the header stays visible at the top
4. **Header scrolls away on short screens**
   - Given a screen 480 px tall or less (for example a phone in landscape)
   - When the visitor scrolls down the page
   - Then the header scrolls away with the page and does not take up screen space
5. **Smooth scrolling respects reduced motion**
   - Given the visitor has asked their device for reduced motion
   - When they activate a header link
   - Then the page jumps to the section without an animated scroll (visitors without that setting get a smooth scroll)

## Out of scope
- Theme toggle in the header (S-04).
- Active-section highlighting while scrolling (not in the requirements).
- Skip-to-content link (S-12).

## Notes
- How the user reaches it: the header is part of the home page (S-01).
- Shared quality bar (prd.md §5) applies; each link is a touch target of at least 44px.
