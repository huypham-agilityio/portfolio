# S-14: Open the page from one public link

- **Priority:** P1
- **Step:** 2 (public URL)
- **Covers:** FR-13, FR-15, NFR-05 · **Decisions:** Q-02, Q-03, Q-12
- **Depends on stories:** S-13 · **External dependency:** the owner's Vercel account (R-02)

## User story
As a visitor, I want to open the portfolio from one public link, so that I can see it from any
device without anything installed or any login.

## Acceptance criteria
1. **Public and open to anyone**
   - Given the owner's Vercel account is available and the local v1 is accepted (S-13)
   - When anyone opens the page's Vercel default URL from any network
   - Then the home page loads with no login or password
2. **Same page as the accepted local v1**
   - Given the public URL
   - When the visitor uses the header links, the theme toggle and the contact links
   - Then they behave as accepted in S-13
3. **Wrong addresses show the 404 page**
   - Given the public URL
   - When the visitor opens an address under it that does not exist
   - Then the 404 page (S-11) is shown, with its link back to the home page
4. **Footer credit is updated**
   - Given the page is live on the public URL
   - When the visitor reaches the footer
   - Then it shows only "Built with Next.js and deployed on Vercel"

## Out of scope
- Custom domain (phase 2).
- Real-device check (S-15).
- Real content (S-16, S-17); placeholders are still allowed at step 2.

## Notes
- How the user reaches it: the public Vercel default URL is the link the owner shares.
- The footer must not claim "deployed on Vercel" before the public deployment exists (FR-15).
