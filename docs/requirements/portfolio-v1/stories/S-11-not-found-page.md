# S-11: Find the way back from a wrong address

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-08 · **Decisions:** Q-01
- **Depends on stories:** S-03

## User story
As a visitor who followed a broken or mistyped link, I want a clear "page not found" page with a
way back, so that I still reach the portfolio.

## Acceptance criteria
1. **Unknown address shows the 404 page**
   - Given any address on the site that does not exist (for example `/does-not-exist`)
   - When the visitor opens it
   - Then they see a basic "page not found" page instead of a browser error
2. **Link back to the home page**
   - Given the visitor is on the 404 page
   - When they activate its link home (mouse, touch or keyboard)
   - Then the home page (`/`) opens
3. **Same theme as the rest of the site**
   - Given the visitor's device theme, or a theme they chose earlier on the home page
   - When the 404 page opens
   - Then it shows that theme, readable at WCAG 2.1 AA, with no flash of the other theme
4. **No theme toggle**
   - Given the 404 page
   - When the visitor looks at its header
   - Then there is no theme toggle

## Out of scope
- The 404 page on the public URL (checked in S-14).

## Notes
- How the user reaches it: by opening any unknown address; it links back to the home page (S-01).
- Shared quality bar (prd.md §5) applies.
