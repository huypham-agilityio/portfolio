# S-05: Read the About section

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-03, FR-10, NFR-06 · **Decisions:** Q-04 (DD-01), Q-05, Q-08 (DD-04)
- **Depends on stories:** S-01

## User story
As a visitor, I want a short introduction with the owner's name, headline, bio and photo, so
that I quickly know who he is and what he does.

## Acceptance criteria
1. **About content is shown**
   - Given the visitor is on the home page
   - When they look at the About section
   - Then they see the name "Huy Pham", a headline, a short bio and a square portrait image
2. **Placeholders are marked; the name is not**
   - Given real content has not arrived yet
   - When the About section is shown
   - Then the headline and bio are sample text with `[PLACEHOLDER]` in front (e.g. "[PLACEHOLDER] Frontend engineer building fast, accessible web apps"), the portrait's alt text includes `[PLACEHOLDER]` and its file name includes `placeholder`, and "Huy Pham" has no marker
3. **No call-to-action buttons**
   - Given the About section
   - When the visitor looks at it
   - Then it contains no buttons
4. **Portrait does not shift the page**
   - Given the page is loading
   - When the portrait appears
   - Then the text around it does not jump, and the image is served with the page (not loaded from another site)

## Out of scope
- Real headline, bio and portrait (S-16).
- About buttons such as "View projects" or "Contact me" (out of v1, Q-08).

## Notes
- How the user reaches it: top of the home page (S-01) and the "About" header link (S-02).
- Shared quality bar (prd.md §5) applies.
- The look of the placeholder portrait is the Team Lead's call (NFR-09, DD-01).
