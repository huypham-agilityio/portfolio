# S-16: Show the owner's real profile and contact details

- **Priority:** P2
- **Step:** 3 (launch)
- **Covers:** FR-11, FR-03, FR-06, FR-09 · **Decisions:** Q-03, Q-05
- **Depends on stories:** S-05, S-09, S-10 · **External dependency:** the owner's real content (R-03)

## User story
As a visitor, I want to read the owner's real introduction and use his real contact details, so
that what I learn is true and my message reaches him.

## Acceptance criteria
1. **Real About content**
   - Given the owner has supplied his headline, bio and portrait
   - When the visitor views the About section
   - Then it shows the real headline, bio and portrait with real alt text, and no `[PLACEHOLDER]` marker
2. **Real contact details**
   - Given the owner has supplied his email, GitHub and LinkedIn URLs
   - When the visitor views and uses the Contact section
   - Then the real email is shown and opens the mail app addressed to it, and the GitHub and LinkedIn links open the owner's real profiles
3. **Real page title and description**
   - Given the owner has supplied or approved the wording
   - When the browser tab and the meta description are read
   - Then they contain real text and no `[PLACEHOLDER]` marker
4. **Only content changes, not layout**
   - Given the real content is in place
   - When the page is viewed at 320, 375, 768 and 1280 px in both themes
   - Then the layout is the same as before, the shared quality bar still passes, and a long real email or URL still wraps at 320 px

## Out of scope
- Real projects and skills (S-17).
- The final audit (S-18).

## Notes
- BR-04: replacing placeholders changes only text, links and images, never layout.
- "Huy Pham" is already real and stays unchanged (BR-02).
- How the user reaches it: the About and Contact sections of the home page (S-05, S-09).
