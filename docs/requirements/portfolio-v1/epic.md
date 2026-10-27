# Personal portfolio web page v1

One public, English, single-page portfolio for Huy Pham with About, Projects, Skills and Contact
sections, a light/dark theme, a 404 page and basic page metadata, so that visitors can get to
know him and contact him from one shareable link. Built in three steps: (1) local v1 on marked
`[PLACEHOLDER]` content, (2) the same page on one public Vercel default URL, (3) launch with real
content after a placeholder audit that finds nothing.

- Requirements: `docs/requirements/portfolio-v1/requirements.md` (signed off 2026-10-27 by Huy Pham)
- PRD: `docs/requirements/portfolio-v1/prd.md`
- Stories index and traceability: `docs/requirements/portfolio-v1/stories.md`

## Success criteria
- All four sections work at 320 px and up in the target browsers, with no horizontal scroll (step 1).
- Email, GitHub and LinkedIn links work (step 1).
- The theme toggle works and the default follows the system (step 1).
- WCAG 2.1 AA in both themes; automated accessibility check reports 0 serious or critical issues (step 1).
- The page is reachable on one public Vercel default URL and passes the real-device check (step 2).
- The placeholder audit finds nothing at launch (step 3).

## Out of scope
Experience and Education sections, contact form, Vietnamese version, custom domain, Open Graph
preview, formal performance budget, automated deploy block, analytics, CV download, blog, CMS.

## Stories
**Step 1: local v1 (P0)**
- S-01: See the page with its four sections
- S-02: Jump to a section from the header
- S-03: Page follows the device theme
- S-04: Switch and keep the theme
- S-05: Read the About section
- S-06: Browse project cards
- S-07: Hide project links a project does not have
- S-08: See the skills list
- S-09: Contact the owner
- S-10: Recognize the page in the browser tab and search results
- S-11: Find the way back from a wrong address
- S-12: Skip straight to the content with the keyboard
- S-13: Accept the local v1

**Step 2: public URL (P1)** (needs the owner's Vercel account)
- S-14: Open the page from one public link
- S-15: Check the public page on real phones

**Step 3: launch (P2)** (needs the owner's real content)
- S-16: Show the owner's real profile and contact details
- S-17: Show the owner's real projects and skills
- S-18: Pass the placeholder audit and launch
