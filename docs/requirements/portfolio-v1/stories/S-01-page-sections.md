# S-01: See the page with its four sections

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-01, FR-15, NFR-02, NFR-04 · **Decisions:** Q-01, Q-03, Q-12
- **Depends on stories:** none

## User story
As a visitor, I want to open one page that shows who it belongs to and is organized into clear
sections, so that I can find what I am looking for in one place.

## Acceptance criteria
1. **Page opens at the home address**
   - Given the page is running
   - When a visitor opens the home address (`/`)
   - Then a single page loads with a header showing the name "Huy Pham", a main content area and a footer
2. **Four sections in the agreed order**
   - Given the visitor is on the home page
   - When they scroll from top to bottom
   - Then they see four sections, each with its own heading, in this order: About, Projects, Skills, Contact
3. **Footer shows only the step 1 credit**
   - Given the page is not yet on the public URL
   - When the visitor reaches the footer
   - Then it shows only the text "Built with Next.js" and nothing else
4. **English only**
   - Given the visitor is on the home page
   - When they read the page, or assistive technology reads its language
   - Then all visible text is in English and the page declares its language as English
5. **Fits every target screen**
   - Given the home page
   - When it is viewed at 320, 375, 768 and 1280 px wide, in portrait and landscape
   - Then there is no horizontal scroll and no clipped text

## Out of scope
- Header anchor links (S-02) and the theme toggle (S-04).
- The content of each section (S-05, S-06, S-08, S-09).
- Footer text after the public deployment (S-14).
- Footer copyright line (out of v1, Q-12).

## Notes
- How the user reaches it: this is the home page; it is what the shared link opens.
- Shared quality bar (prd.md §5) applies.
- "Huy Pham" is real content and never carries the `[PLACEHOLDER]` marker (BR-02).
