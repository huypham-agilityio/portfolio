# S-04: Switch and keep the theme

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-07, NFR-03 · **Decisions:** Q-01
- **Depends on stories:** S-03

## User story
As a visitor, I want a switch to choose light or dark myself and have the page remember it, so
that I can read it the way I prefer every time I come back.

## Acceptance criteria
1. **Toggle switches the theme**
   - Given the visitor is on the home page
   - When they activate the theme toggle in the header (mouse, touch or keyboard)
   - Then the page switches between light and dark
2. **Choice is remembered without a flash**
   - Given the visitor chose a theme with the toggle
   - When they reload the page or come back later in the same browser
   - Then the page opens in the chosen theme, with no brief flash of the other theme
3. **The visitor's choice wins over the device**
   - Given the visitor chose a theme with the toggle
   - When their device switches between light and dark
   - Then the page keeps the visitor's chosen theme (BR-03)
4. **Works when browser storage is blocked**
   - Given the browser blocks or refuses page storage (for example some private modes)
   - When the visitor opens the page and uses the toggle
   - Then the page loads in the device theme without errors, and the toggle still switches the theme for the current visit
5. **Screen readers announce the state**
   - Given a screen reader user reaches the toggle
   - When it is read out and when they activate it
   - Then it is announced with the fixed name "Dark theme" and an on/off (pressed) state that changes with the theme

## Out of scope
- Theme on the 404 page (S-11; the 404 page has no toggle).

## Notes
- How the user reaches it: the toggle is in the header of the home page (S-01).
- Shared quality bar (prd.md §5) applies; the toggle is a touch target of at least 44px.
