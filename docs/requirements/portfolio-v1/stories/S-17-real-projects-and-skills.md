# S-17: Show the owner's real projects and skills

- **Priority:** P2
- **Step:** 3 (launch)
- **Covers:** FR-11, FR-04, FR-05, NFR-06 · **Decisions:** Q-03, Q-05, Q-06 (DD-02), Q-07 (DD-03), Q-09 (DD-05)
- **Depends on stories:** S-06, S-07, S-08 · **External dependency:** the owner's real content (R-03)

## User story
As a visitor, I want to see the owner's real projects and skills, so that I can judge his actual
work and experience.

## Acceptance criteria
1. **Real projects**
   - Given the owner has supplied 1 to 3 projects
   - When the visitor views the Projects section
   - Then each card shows the real title, description, technology tags and 16:9 screenshot with real alt text, and its real links; a link the project does not have is not shown
2. **Real skills**
   - Given the owner has supplied his skills
   - When the visitor views the Skills section
   - Then it shows the real skill names as one flat list with no `[PLACEHOLDER]` marker
3. **Real images behave like the placeholders did**
   - Given the real project screenshots are in place
   - When the page loads and the visitor scrolls to the Projects section
   - Then the images are served with the page, load only when needed, and do not make the cards jump
4. **Only content changes, not layout**
   - Given the real content is in place
   - When the page is viewed at 320, 375, 768 and 1280 px in both themes
   - Then the layout is the same as before and the shared quality bar still passes

## Out of scope
- Real profile and contact details (S-16).
- The final audit (S-18).

## Notes
- BR-04: replacing placeholders changes only text, links and images, never layout.
- How the user reaches it: the Projects and Skills sections of the home page (S-06, S-08).
