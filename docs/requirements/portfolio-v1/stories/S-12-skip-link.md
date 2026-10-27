# S-12: Skip straight to the content with the keyboard

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-14, NFR-03 · **Decisions:** Q-01
- **Depends on stories:** S-02

## User story
As a keyboard user, I want a link that skips the header, so that I reach the page content
without tabbing through every header link first.

## Acceptance criteria
1. **Skip link comes first**
   - Given a keyboard user has just opened the home page
   - When they press Tab once
   - Then the first thing focused is a visible "skip to content" link
2. **Skip link moves past the header**
   - Given the skip link is focused
   - When the user activates it
   - Then focus and view move to the start of the main content, and the next Tab goes to the first focusable item in the content, not the header
3. **Visible focus**
   - Given the skip link is focused, in either theme
   - When the user looks at it
   - Then it is clearly visible with the focus outline and readable at WCAG 2.1 AA contrast

## Out of scope
- The full accessibility check of the page (S-13).

## Notes
- How the user reaches it: the first Tab on the home page (S-01).
