# S-03: Page follows the device theme

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-07, NFR-03 · **Decisions:** Q-01
- **Depends on stories:** S-01

## User story
As a visitor, I want the page to appear in the same light or dark theme as my device, so that
it is comfortable to read without me doing anything.

## Acceptance criteria
1. **First visit matches the device**
   - Given a visitor who has never chosen a theme on this page
   - When they open the page with their device set to dark (or light)
   - Then the page shows the dark (or light) theme
2. **Follows device changes**
   - Given a visitor who has not chosen a theme and has the page open
   - When they switch their device between light and dark
   - Then the page switches to the matching theme without a reload
3. **No flash of the wrong theme**
   - Given the device is set to dark
   - When the visitor opens or reloads the page, including on a slow device
   - Then the page never briefly shows the light theme first (and the reverse for light)
4. **Both themes are readable**
   - Given the page in the light theme and in the dark theme
   - When text, links, controls and the focus outline are checked
   - Then they meet WCAG 2.1 AA contrast (4.5:1 text, 3:1 large text and UI components) in both themes
5. **Browser controls match the theme**
   - Given the page in the dark theme
   - When the visitor sees scrollbars and the mobile browser toolbar area
   - Then they match the dark theme (and the light theme in light)

## Out of scope
- Manual toggle, remembered choice and storage-blocked behavior (S-04).

## Notes
- How the user reaches it: applies to the home page (S-01); the 404 page reuses it (S-11).
- Shared quality bar (prd.md §5) applies.
- AC 5 comes from the TL design rules (SRC-2 TL design §5), part of the signed baseline (Q-01).
