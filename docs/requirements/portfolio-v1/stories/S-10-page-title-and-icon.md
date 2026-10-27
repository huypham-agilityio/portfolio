# S-10: Recognize the page in the browser tab and search results

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-09, FR-10 · **Decisions:** Q-01, Q-05
- **Depends on stories:** S-01

## User story
As a visitor, I want the page to have a clear title, description and icon, so that I can
recognize it among my browser tabs, bookmarks and search results.

## Acceptance criteria
1. **Title and icon in the browser tab**
   - Given the visitor opens the home page
   - When they look at the browser tab
   - Then it shows the page title and the site's icon (no missing-icon error)
2. **Description for search and link previews**
   - Given a search engine or tool reads the home page
   - When it looks for the page description
   - Then a meta description is present
3. **Placeholders are marked; the name is not**
   - Given real content has not arrived yet
   - When the page title and meta description are read
   - Then any placeholder part carries `[PLACEHOLDER]` (visible in the tab, as intended), and "Huy Pham" has no marker

## Out of scope
- Real title and description wording (S-16).
- Open Graph social preview (phase 2).

## Notes
- How the user reaches it: the home page (S-01).
- The exact title wording is not fixed by the requirements; it is real content supplied at step 3.
