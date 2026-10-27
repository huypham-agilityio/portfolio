# PRD: Personal portfolio web page (v1)

- Slug: `portfolio-v1` · Analysis: `requirements.md` (signed off 2026-10-27 by Huy Pham) · Version: 1
- Epic title: Personal portfolio web page v1

## 1. Summary
We build one public, English, single-page portfolio for Huy Pham with four sections (About,
Projects, Skills, Contact), a light/dark theme, a 404 page and basic page metadata, so that
visitors (recruiters, clients, peers) can get to know him and contact him from one shareable
link. The signed-off plan (SRC-2) is the baseline (Q-01). Work runs in the plan's three steps:
(1) local v1 on marked placeholders, (2) the same page on a public Vercel default URL,
(3) launch with real content and a clean placeholder audit (Q-03).

## 2. Goals and success metrics
| Goal | Metric | Target | Step |
|---|---|---|---|
| Works on every target screen | All four sections visible and usable at 320 / 375 / 768 / 1280+ px, portrait and landscape, in the target browsers (NFR-01, NFR-02) | No horizontal scroll, no clipped text | 1 |
| Visitors can reach the owner | Email, GitHub and LinkedIn links work (FR-06) | All three work | 1 |
| Theme works | Manual toggle; default follows the system (FR-07) | Passes, incl. storage blocked and no flash | 1 |
| Accessible | WCAG 2.1 AA in both themes; automated accessibility check (NFR-03) | 0 serious or critical issues | 1 |
| The page is public | Reachable on one Vercel default URL (FR-13) | Reachable by anyone, no login | 2 |
| Works on real phones | Real-device check on iOS Safari and Android Chrome (NFR-10) | Passes | 2 |
| Launch is clean | Placeholder audit (FR-12) | Finds nothing | 3 |

## 3. Users
- **Visitor:** anyone who opens the shared link, on a phone or a desktop (recruiter, client, peer).
- **Owner / PO (Huy Pham):** subject of the page; supplies the Vercel account (step 2) and the
  real content (step 3), runs the real-device check, signs off launch.

## 4. Scope
- **In this release (all three steps, Q-03):**
  - Step 1, local v1: FR-01 single English page with four sections in order; FR-02 header
    navigation; FR-03 About; FR-04 Projects; FR-05 Skills; FR-06 Contact; FR-07 light/dark theme
    with toggle; FR-08 404 page; FR-09 page title, meta description, favicon; FR-10 marked
    placeholders; FR-14 skip link; FR-15 footer credit ("Built with Next.js"); checked on the
    local production build.
  - Step 2, public URL: FR-13 one Vercel default URL; FR-15 footer credit updated; NFR-10
    real-device check. Blocked by the owner's Vercel account (R-02).
  - Step 3, launch: FR-11 real content replaces all placeholders; FR-12 placeholder audit finds
    nothing and the page is re-checked on the public URL. Blocked by the owner's real content (R-03).
- **Out / later:**
  - Phase 2 (SRC-2 §4, SRC-3): Experience and Education sections; contact form; Vietnamese
    version (NFR-04); custom domain; Open Graph social preview; formal performance budget;
    automated deploy block while placeholders remain.
  - Not in v1 (Q-11): analytics/visitor tracking, downloadable CV, blog, CMS/admin screen.
  - Not in v1: About call-to-action buttons (Q-08, DD-04); skill grouping or levels (Q-07,
    DD-03); project role/year (Q-06); footer copyright line (Q-12).
  - Excluded by stakeholder instruction (SRC-1): the old repository's code, issues, task list
    T1a…T9 and tickets #9–#28.

## 5. Requirements
Confirmed FRs and NFRs are defined in `requirements.md` §3–§4; this table only points to them.

| ID | Summary | Decided by |
|---|---|---|
| FR-01 | Single English page, four sections in order About, Projects, Skills, Contact | Q-01 |
| FR-02 | Header: name, four anchor links in one row at 320px, theme toggle; sticky except on short screens; headings land below the header | Q-01 |
| FR-03 | About: real name, headline, bio, square portrait, no buttons | Q-08 (DD-04) |
| FR-04 | Projects: 1 to 3 cards (thumbnail, title, description, tags, "Live demo" / "Source"); missing link hidden; card not clickable | Q-06 (DD-02), Q-09 (DD-05) |
| FR-05 | Skills: one flat list of names, no grouping or levels | Q-07 (DD-03) |
| FR-06 | Contact: visible email + mailto, GitHub and LinkedIn in a new tab, no form, wraps at 320px | Q-01 |
| FR-07 | Light/dark theme: follows system, toggle overrides and persists, storage-blocked fallback, no flash, fixed accessible name | Q-01 |
| FR-08 | 404 page with link home, both themes, no toggle | Q-01 |
| FR-09 | Page title, meta description, favicon | Q-01 |
| FR-10 | `[PLACEHOLDER]` marker formats on all placeholder content | Q-04 (DD-01), Q-05 |
| FR-11 | Real content replaces all placeholders before launch, content only | Q-03, Q-05 |
| FR-12 | Placeholder audit finds nothing, then re-check on the public URL | Q-03 |
| FR-13 | One public Vercel default URL, after local v1 | Q-02, Q-03 |
| FR-14 | Skip-to-content link | Q-01 |
| FR-15 | Footer credit only; text changes when the public deployment exists | Q-12 |
| NFR-01 | Browsers: last 2 versions of Chrome, Safari, Firefox, iOS Safari, Android Chrome | Q-01 |
| NFR-02 | Screens 320 / 375 / 768 / 1280+ px, portrait and landscape | Q-01 |
| NFR-03 | WCAG 2.1 AA in both themes, keyboard, focus, landmarks, 44px targets, reduced motion, 0 serious/critical automated issues | Q-01 |
| NFR-04 | English only | Q-01 |
| NFR-05 | Static output only, no backend | Q-01 |
| NFR-06 | Image hygiene: explicit size, lazy below the fold, local files | Q-01 |
| NFR-07 | No third-party runtime requests for fonts; no analytics | Q-11 |
| NFR-08 | External links open with `rel="noopener noreferrer"` | Q-01 |
| NFR-09 | Visual design from the written design rules; prototype is reference only | Q-04 (DD-01) |
| NFR-10 | Real-device check by the owner on his phones, on the public URL | Q-10 (DD-06) |

### Shared quality bar (applies to every story that shows something on screen)
Taken from NFR-02, NFR-03, NFR-06 and NFR-09 and the plan's Definition of Done (SRC-2 §13). It
is part of every UI story's acceptance and is not repeated as a numbered AC:
- Follows the written design rules (NFR-09).
- Keyboard reachable, visible focus, correct landmarks and heading order, accessible names and
  alt text, touch targets at least 44px (NFR-03).
- Correct in both themes at WCAG 2.1 AA contrast, once the theme stories (S-03, S-04) exist.
- No horizontal scroll and no clipped text at 320, 375, 768 and 1280 px, portrait and landscape (NFR-02).
- Automated accessibility check reports 0 serious or critical issues (NFR-03).
- Images have a fixed size (no layout shift), are local files, and load lazily below the fold (NFR-06).

## 6. Key decisions
| Question | Decision |
|---|---|
| Q-01 | Plan v2.1 + PO decisions in #2 + TL design comment are the v1 baseline |
| Q-02 | Hosting on Vercel, free default URL; the deploy is its own later piece of work |
| Q-03 | Scope is steps 1 to 3 (local v1, public URL, launch) |
| Q-04 | Build from the written design rules; prototype is a reference only (DD-01) |
| Q-05 | Real content not ready; marked placeholders until step 3 |
| Q-06 | Card: thumbnail, title, description, tags, "Live demo" / "Source"; missing link hidden (DD-02) |
| Q-07 | Skills: one flat list of names (DD-03) |
| Q-08 | About: portrait, no buttons (DD-04) |
| Q-09 | 1 to 3 projects (DD-05) |
| Q-10 | The owner does the real-device check on his own phones (DD-06) |
| Q-11 | No analytics, CV download or blog in v1 |
| Q-12 | Footer shows only the credit line |

## 7. Assumptions, deferred items and risks
- Remaining assumptions (accepted at GATE 1): A-05, "last 2 versions" applies to all five listed browsers.
- Delegated defaults DD-01 to DD-06 (requirements §12): the stakeholder may override them later
  through a requirement change.
- Deferred: nothing deferred within v1; phase 2 items are listed in §4.
- Risks: R-01 look first seen on the built page (prototype unreadable); R-02 Vercel account
  blocks step 2; R-03 real content blocks step 3; R-04 a placeholder leaks into launch
  (mitigated by S-18); R-05 iOS Safari quirks found late (S-15); R-06 visible email scraped for
  spam (accepted, BR-05).

## 8. Story map
Suggested delivery order. Priority reflects the step: P0 = step 1 (local v1), P1 = step 2
(public URL), P2 = step 3 (launch). This follows the plan's "a working public URL first, then
polish" and the external blockers of steps 2 and 3.

**Step 1: local v1 (P0)**
1. S-01: See the page with its four sections
2. S-02: Jump to a section from the header
3. S-03: Page follows the device theme
4. S-04: Switch and keep the theme
5. S-05: Read the About section
6. S-06: Browse project cards
7. S-07: Hide project links a project does not have
8. S-08: See the skills list
9. S-09: Contact the owner
10. S-10: Recognize the page in the browser tab and search results
11. S-11: Find the way back from a wrong address
12. S-12: Skip straight to the content with the keyboard
13. S-13: Accept the local v1

**Step 2: public URL (P1)**
14. S-14: Open the page from one public link
15. S-15: Check the public page on real phones

**Step 3: launch (P2)**
16. S-16: Show the owner's real profile and contact details
17. S-17: Show the owner's real projects and skills
18. S-18: Pass the placeholder audit and launch
