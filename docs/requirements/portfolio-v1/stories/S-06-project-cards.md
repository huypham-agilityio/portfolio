# S-06: Browse project cards

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-04, FR-10, NFR-06, NFR-08 · **Decisions:** Q-04 (DD-01), Q-05, Q-06, Q-09 (DD-05)
- **Depends on stories:** S-01

## User story
As a visitor, I want to see the owner's projects as cards with a picture, a description and
links, so that I can judge his work and open the projects that interest me.

## Acceptance criteria
1. **Cards show the project details**
   - Given the visitor is on the home page
   - When they look at the Projects section
   - Then they see 1 to 3 project cards, each with a 16:9 thumbnail, the project title, a short description, technology tags, and "Live demo" and "Source" links
2. **Only the links are clickable**
   - Given a project card
   - When the visitor hovers over or clicks the card outside its links
   - Then nothing happens; only "Live demo" and "Source" react to hover and open their targets
3. **Project links open safely and say what they do**
   - Given a "Live demo" or "Source" link
   - When a screen reader reads it, and when the visitor opens it
   - Then its accessible name identifies the project and the link, says "(opens in a new tab)" if it opens a new tab, and the opened site gets no access back to this page (NFR-08)
4. **Placeholders are marked**
   - Given real content has not arrived yet
   - When the Projects section is shown
   - Then titles, descriptions and tags carry `[PLACEHOLDER]` in front, links point to `https://example.com/?ph=[PLACEHOLDER]`, thumbnail alt text includes `[PLACEHOLDER]` and thumbnail file names include `placeholder`
5. **Thumbnails load without shifting the page**
   - Given the Projects section is below the first screen
   - When the page loads and the visitor scrolls to it
   - Then the thumbnails load only when needed, the cards do not jump as they load, and the images are served with the page

## Out of scope
- Hiding a link a project does not have (S-07).
- Real projects and screenshots (S-17).
- Project role or year (out of v1, Q-06).

## Notes
- How the user reaches it: scroll the home page (S-01) or the "Projects" header link (S-02).
- Shared quality bar (prd.md §5) applies.
- The look of placeholder thumbnails is the Team Lead's call (NFR-09, DD-01).
- Whether project links open in a new tab is not stated in the requirements; AC 3 only requires that the accessible name says so when they do.
