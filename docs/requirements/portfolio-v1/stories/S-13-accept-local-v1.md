# S-13: Accept the local v1

- **Priority:** P0
- **Step:** 1 (local v1), exit check
- **Covers:** NFR-01, NFR-02, NFR-03, NFR-07 · **Decisions:** Q-01, Q-03, Q-11
- **Depends on stories:** S-01, S-02, S-03, S-04, S-05, S-06, S-07, S-08, S-09, S-10, S-11, S-12

## User story
As the owner, I want the complete page checked as one whole on the local production build, so
that I know step 1 is done and the page is ready to go public.

## Acceptance criteria
1. **Works in every target browser**
   - Given the local production build
   - When the home page and the 404 page are used in the last 2 versions of Chrome, Safari and Firefox, and in iOS Safari and Android Chrome (emulated)
   - Then all four sections, header links, theme toggle and contact links work the same in each
2. **Works at every target screen size**
   - Given the local production build
   - When the pages are viewed at 320, 375, 768 and 1280 px, portrait and landscape
   - Then there is no horizontal scroll or clipped text, and every header link lands with its section heading visible below the header
3. **Accessible in both themes**
   - Given the home page and the 404 page in light and in dark
   - When the automated accessibility check runs and a keyboard-only walkthrough is done
   - Then the check reports 0 serious or critical issues, and every interactive element is reachable with visible focus
4. **No outside requests**
   - Given the visitor opens the page
   - When its network activity is observed
   - Then the page loads nothing from other sites (fonts included) and sends no analytics or tracking
5. **All links work**
   - Given every link on the home and 404 pages
   - When each is followed
   - Then it reaches its target; `example.com` placeholder targets are expected at this step and count as passing

## Out of scope
- Public URL and real phones (S-14, S-15).
- Placeholder audit (S-18; placeholders are allowed at step 1).

## Notes
- This is the exit check for step 1 (plan M1). It does not add features; it verifies the shared quality bar (prd.md §5) across the whole page.
- How the user reaches it: the home page (S-01) and any unknown address (S-11).
