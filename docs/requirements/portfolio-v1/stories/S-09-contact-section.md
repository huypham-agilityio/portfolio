# S-09: Contact the owner

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-06, FR-10, NFR-05, NFR-08 · **Decisions:** Q-01, Q-05
- **Depends on stories:** S-01

## User story
As a visitor, I want the owner's email, GitHub and LinkedIn in one place, so that I can get in
touch with him or look at his profiles.

## Acceptance criteria
1. **Email is visible and clickable**
   - Given the visitor is on the Contact section
   - When they look at it and activate the email link
   - Then the email address is shown as readable text, and activating it opens their mail app addressed to it
2. **GitHub and LinkedIn open in a new tab, safely**
   - Given the GitHub and LinkedIn links
   - When a screen reader reads them, and when the visitor opens them
   - Then each opens in a new tab, its accessible name includes "(opens in a new tab)", and the opened site gets no access back to this page (NFR-08)
3. **No contact form**
   - Given the Contact section
   - When the visitor looks at it
   - Then there is no form or input field; contact happens only through the links
4. **Long addresses wrap on small screens**
   - Given a screen 320 px wide
   - When a long email address or URL is shown
   - Then it wraps onto the next line with no horizontal scroll and no clipped text
5. **Placeholders use the agreed formats**
   - Given real content has not arrived yet
   - When the Contact section is shown
   - Then the email text is `placeholder@example.com [PLACEHOLDER]`, its link is `mailto:placeholder@example.com?subject=[PLACEHOLDER]`, and the GitHub and LinkedIn links point to `https://example.com/?ph=[PLACEHOLDER]`

## Out of scope
- Real email and profile URLs (S-16).
- Contact form (phase 2).

## Notes
- How the user reaches it: scroll the home page (S-01) or the "Contact" header link (S-02).
- Shared quality bar (prd.md §5) applies.
- BR-05: the plain-text email is an accepted v1 tradeoff (spam risk).
