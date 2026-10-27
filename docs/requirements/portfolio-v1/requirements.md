# Requirement analysis: Personal portfolio web app (v1)
Signed-off: 2026-10-27 by Huy Pham

- Slug: `portfolio-v1`
- Status: Signed off (GATE 1, 2026-10-27)
- Sources: see the table below

## Changelog
| Date | Round | Change |
|---|---|---|
| 2026-10-27 | 1 | Initial analysis from the stakeholder brief, plan issue #3 (v2.1, incl. all comments) and epic issue #2 (incl. all comments) of `toinguyen-agilityio/my-portfolio` |
| 2026-10-27 | 2 | Stakeholder delegated all 12 questions ("You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent."). All Q-01 to Q-12 confirmed by the BA under that delegation, taking the plan's answer where it states one and the least-addition option otherwise (marked "delegated default", DD-nn in §12). FR-01 to FR-15 confirmed; FR-03, FR-04, FR-05, FR-10 refined; FR-13 dispute resolved (Vercel); NFR-09 changed to build from written design rules (prototype unreadable); NFR-10 owner set; scope fixed to steps 1 to 3 (M1 to M3); A-01 to A-04 and A-06 turned into decisions; C-01, AMB-01, AMB-02 resolved. |

## Sources
| ID | File (in `sources/`) | Origin | Retrieved | Notes |
|---|---|---|---|---|
| SRC-1 | `stakeholder-brief.md` | Stakeholder chat (Huy Pham) | 2026-10-27 | New repo `huypham-agilityio/portfolio`; reuse only the plan, not the old issues or code |
| SRC-2 | `plan-issue-3.md` | https://github.com/toinguyen-agilityio/my-portfolio/issues/3 | 2026-10-27 | Signed-off plan v2.1, body and all comments. Comments cited as: "Plan review" (@claude), "TL review" (TeamLead changes requested), "TL decisions" (TeamLead sign-off), "TL design" (issuecomment-6437477342, wins over the prototype), "TL M1 breakdown" (old repo tickets #9–#28; **not reused**, see Scope) |
| SRC-3 | `epic-issue-2.md` | https://github.com/toinguyen-agilityio/my-portfolio/issues/2 | 2026-10-27 | Parent epic; the PO's confirmed requirements are in the comments by @huypham-agilityio ("PO answers", "PO contact decision", "PO final decisions", "PO final note") |
| SRC-4 | (not converted) | https://claude.ai/artifact/97JaGNJomJK7emFVUcYLVY | 2026-10-27 | Prototype. **Unreadable**: WebFetch returned only the page shell "Claude Artifact", no content. Kept as a reference only (Q-04) |
| SRC-5 | `stakeholder-notes.md` | Stakeholder chat (Huy Pham) | 2026-10-27 | Delegation of all open questions to the team, "stick as closely as possible to the plan" (Q-01 to Q-12) |

## 1. Business goal and problem statement
Huy Pham wants one public web page that presents his profile, projects and skills and gives
visitors a way to contact him, shareable as a single clickable link (SRC-3 §Client Request;
SRC-2 §1). The work restarts in a new, empty repository on the stakeholder's own account,
reusing only the signed-off plan (SRC-1), which carries over as the v1 baseline (Q-01).
Success for v1 is the plan's epic criteria (SRC-2 §2): the page is public on one Vercel default
URL, all four sections work at 320px and up in the target browsers, the email/GitHub/LinkedIn
links work, the theme toggle works and defaults to the system theme, the page meets WCAG 2.1 AA
in both themes, and at launch no placeholder content remains. The work runs in the plan's three
steps: (1) local v1 on placeholders, (2) public URL, (3) launch with real content (Q-03).
Priority is "a working public URL first, then polish"; there is no hard deadline (SRC-3 PO
answers Q7; SRC-2 §6).

## 2. Actors / personas
| Actor | Description | Goals |
|---|---|---|
| Visitor | Anyone who opens the shared link (e.g. recruiter, client, peer), on phone or desktop | Get to know Huy Pham quickly; see projects and skills; contact him |
| Owner / PO (Huy Pham) | Subject of the portfolio and stakeholder | Present himself professionally; supply the Vercel account and the real content; run the real-device check; sign off launch |

## 3. Functional requirements
| ID | Requirement | Source | Status |
|---|---|---|---|
| FR-01 | The site shall be a single page in English with four sections in this order: About, Projects, Skills, Contact. | SRC-3 PO answers Q2, Q4; SRC-2 §4; Q-01 | confirmed |
| FR-02 | The page shall have a header with the owner's name, anchor links to the four sections (About · Projects · Skills · Contact) and the theme toggle. No hamburger menu; the four links fit in one row at 320px. The header stays visible while scrolling, except on short screens (height ≤ 480px, e.g. phones in landscape) where it scrolls away. Following an anchor link shows the section heading below the header, not under it. | SRC-2 §5 Navigation, D5; TL design §3 fix 2, §4; Q-01 | confirmed |
| FR-03 | The About section shall show the name "Huy Pham" (real, never a placeholder), a headline, a short bio and a square portrait image. It has no call-to-action buttons. | SRC-3 PO answers Q1; SRC-2 §9 Images, §10, §12 T3; Q-08 (DD-04) | confirmed |
| FR-04 | The Projects section shall show 1 to 3 project cards. Each card shows a 16:9 thumbnail, the project title, a short description, technology tags, and "Live demo" and "Source" links. A link is not shown when the project does not have it. The card itself is not clickable; only its links are (only the links have hover states). | SRC-2 §9, §9 fix 4, §12 T4; TL design §1 Layout, §2, §3 fix 4, §6; Q-06 (DD-02), Q-09 (DD-05) | confirmed |
| FR-05 | The Skills section shall show the owner's skills as one simple, ungrouped list of skill names (small labels side by side), without levels. | SRC-2 §9 tokens ("chips"), §12 T5; TL design §2 `Chip`; SRC-3 PO answers Q2; Q-07 (DD-03) | confirmed |
| FR-06 | The Contact section shall show the email address as visible text and as a `mailto:` link, plus GitHub and LinkedIn links. GitHub and LinkedIn open in a new tab and tell assistive technology so ("(opens in a new tab)" in the accessible name). There is no contact form. A long email or URL wraps at 320px instead of causing horizontal scroll. | SRC-3 PO contact decision, PO final decisions §Contact; SRC-2 §5 Contact, §12 T6 | confirmed |
| FR-07 | The page shall support a light and a dark theme. On first visit it follows the device's system preference and keeps following system changes until the visitor chooses. A manual toggle overrides it, and the choice persists across reloads. If browser storage is blocked, the page still renders in the system theme and the toggle works for the current visit. No visible flash of the wrong theme on load. The toggle announces its on/off state to screen readers with a fixed name ("Dark theme"). | SRC-3 PO final decisions §2; SRC-2 §5 Theme, D4, D6; TL design §3 fix 3, §5 | confirmed |
| FR-08 | Any unknown path shall show a basic 404 page with a link back to the home page, in both themes, without the theme toggle. | SRC-3 PO final decisions §4; SRC-2 §5 404, §9 fix 6, §12 T7b | confirmed |
| FR-09 | The page shall have a page title, a meta description and a favicon. | SRC-3 PO final decisions §4; SRC-2 §5 SEO, §12 T7a | confirmed |
| FR-10 | Until real content arrives, every placeholder shall carry the searchable marker `[PLACEHOLDER]` in the agreed formats: text is sample copy with the marker in front (e.g. `"[PLACEHOLDER] Frontend engineer building fast, accessible web apps"`); web links `https://example.com/?ph=[PLACEHOLDER]`; email text `placeholder@example.com [PLACEHOLDER]` and link `mailto:placeholder@example.com?subject=[PLACEHOLDER]`; image alt text includes the marker and image file names include `placeholder`. This covers page title, meta description, alt text and link targets. "Huy Pham" never carries the marker. | SRC-3 PO answers Q3, PO final decisions §3; SRC-2 §10, §9 fix 5; Q-04 (DD-01), Q-05 | confirmed |
| FR-11 | Before launch (step 3), all placeholders shall be replaced with the owner's real content: headline, bio, portrait, projects, skills, email address, GitHub and LinkedIn URLs (and real images). Replacing content changes only content, not layout. | SRC-3 PO final note; SRC-2 §7, §12 T8a, §16; Q-03, Q-05 | confirmed |
| FR-12 | Launch sign-off shall require a placeholder audit that finds nothing: a case-insensitive search for `[PLACEHOLDER]` and its URL-encoded form `%5BPLACEHOLDER%5D` in the source, the built HTML and image file names, followed by a re-check of the page on the public URL. A manual checklist is enough for v1. | SRC-3 PO final decisions §3; SRC-2 §2 goal 5, §12 T8, §14; Q-03 | confirmed |
| FR-13 | The page shall be reachable by anyone on one public Vercel default URL (no custom domain). This comes after the local v1 is complete (step 2) and needs the stakeholder's Vercel account. | SRC-3 PO answers Q6; SRC-2 §2 goal 1, §4, D8, §11 M2; Q-02, Q-03 | confirmed |
| FR-14 | The page shall provide a skip-to-content link for keyboard users. | SRC-2 §12 T7c; TL design §0; Plan review item 6 | confirmed |
| FR-15 | The page shall have a footer showing only a credit line: "Built with Next.js" until the public Vercel deployment exists, then "Built with Next.js and deployed on Vercel". | SRC-2 §12 T1b; TL design §7; Q-12 | confirmed |

## 4. Non-functional requirements
| ID | Category | Requirement | Source |
|---|---|---|---|
| NFR-01 | Platform (browsers) | Supported: last 2 versions of Chrome, Safari and Firefox, plus iOS Safari and Android Chrome. Edge is not tested separately (Chromium). | SRC-3 PO final decisions §1; SRC-2 §5, D9 |
| NFR-02 | Platform (screens) | Works at 320 / 375 / 768 / 1280+ px, portrait and landscape. Minimum width 320px. No horizontal scroll, no clipped text. | SRC-3 PO final decisions §1; SRC-2 §5 |
| NFR-03 | Accessibility | WCAG 2.1 AA in both themes (4.5:1 text, 3:1 large text and UI components); keyboard navigation; visible focus; correct landmarks and heading order; alt text; accessible link names; `lang="en"`; 44px touch targets; smooth scrolling and motion only when the visitor has not asked for reduced motion; automated accessibility check reports 0 serious or critical issues. | SRC-3 PO final decisions §2, §4; SRC-2 §2, §5, §13 DoD; TL decisions §Navigation; TL design intro |
| NFR-04 | i18n | English only in v1. Vietnamese is phase 2. | SRC-3 PO answers (follow-up 2, Q5) |
| NFR-05 | Architecture constraint | Static output only, no backend. | SRC-2 §6 Constraints; SRC-3 PO contact decision ("Why no form") |
| NFR-06 | Performance (basic hygiene) | Images have explicit width/height (no layout shift), images below the fold load lazily, images are local files (no hotlinking). No formal performance budget in v1. | SRC-2 §5 Images; TL decisions §Known tradeoffs; SRC-3 PO final decisions §4 |
| NFR-07 | Privacy / third parties | No third-party requests at runtime for fonts (the font is self-hosted). No analytics or other tracking in v1. | SRC-2 D7; TL design §1 Typography; Q-11 |
| NFR-08 | Security | External links open with `rel="noopener noreferrer"`. | SRC-3 PO final decisions §Contact; SRC-2 §5 |
| NFR-09 | Visual design | Clean, minimal, single page, built from the **written** design rules: the plan's design section (SRC-2 §9: tokens per theme, typography Inter, layout, images, the 6 fixes) and the TL design comment. Visual review is against these rules. The prototype (SRC-4) is kept as a reference only; if it becomes readable it may be used for visual review, and where it disagrees with the TL design comment, the comment wins. The look of placeholder images is the Team Lead's call. | SRC-3 PO answers Q4; SRC-2 D11, §9; TL design; Q-04 (DD-01) |
| NFR-10 | Devices | Before launch, a real-device check on iOS Safari and Android Chrome on the public URL, performed by the stakeholder on his own phones. All other device checks use emulation. | SRC-2 §11 M2, §14; TL decisions §Testing on real phones; Q-10 (DD-06) |

Technology (framework, styling, hosting tooling, CI, test tools) is recorded in SRC-2 D1–D9 and
already in `.squad/config.yml` `stack`. It is the Team Lead's domain and is not treated as a
requirement here, except where it states visible behavior (above). The hosting decision (Vercel,
Q-02) does not change `deploy.platform: none` in `.squad/config.yml` now: per the plan (D8) the
deploy is its own later piece of work.

## 5. Scope
- **In (confirmed, Q-01, Q-03):** the plan's three steps.
  - Step 1, local v1 (SRC-2 §11 M1): single English page with About, Projects, Skills, Contact;
    header navigation; light/dark theme with toggle; 404 page; page title, meta description,
    favicon; footer credit; accessibility and skip link; everything on marked placeholders;
    checked on the local production build.
  - Step 2, public URL (M2): the page on one Vercel default URL; footer credit updated; real-device
    check. Depends on the stakeholder's Vercel account.
  - Step 3, launch (M3): real content replaces all placeholders; placeholder audit finds nothing;
    re-check on the public URL. Depends on the stakeholder's real content.
- **Out (phase 2, from SRC-2 §4 and SRC-3):** Experience and Education sections; contact form
  (needs a backend/third-party service and spam handling); Vietnamese version; custom domain;
  Open Graph social preview; formal performance budget; automated deploy block while
  placeholders remain.
- **Out (by stakeholder instruction, SRC-1):** the old repository's code and issues, including
  its task list T1a…T9 and tickets #9–#28 (SRC-2 §12 and "TL M1 breakdown"). They are not copied
  as stories; stories for this repo are written fresh from these requirements after sign-off.
- **Out of v1 (Q-11, delegated decision):** analytics/visitor tracking, downloadable CV/resume,
  blog, CMS/admin screen for editing content. Also out: About call-to-action buttons (Q-08),
  skill grouping or levels (Q-07), project role/year (Q-06), footer copyright line (Q-12).

## 6. Business rules and data entities
- BR-01: No placeholder content may ship at launch (SRC-3 PO answers Q3, PO contact decision).
- BR-02: "Huy Pham" is real content and never carries the marker (SRC-2 §10).
- BR-03: The visitor's explicit theme choice always wins over the system preference (SRC-2 TL design §5).
- BR-04: Replacing placeholders with real content changes only content (text, links, images), not layout (SRC-2 D3, §12 T8a).
- BR-05: A visible plain-text email is an accepted v1 tradeoff (spam risk); revisit with the phase 2 contact form (SRC-2 D10, §15).
- BR-06: Where the prototype and the TeamLead design comment disagree, the design comment wins (SRC-2 §9). While the prototype is unreadable, the written rules alone apply (Q-04).
- BR-07: A project link ("Live demo" or "Source") that a project does not have is not shown (Q-06, DD-02).
- Entities (content, no database):
  - `Profile`: name (real: Huy Pham), headline, bio, portrait image (square) + alt text, email, GitHub URL, LinkedIn URL.
  - `Project` (1 to 3): title, short description, technology tags, thumbnail (16:9) + alt text, live demo URL (optional), source URL (optional).
  - `Skill`: name (flat list, no grouping, no level).
  - `Theme preference`: light or dark, stored per browser; absent means "follow system".
  - `Site metadata`: page title, meta description, favicon.

## 7. Gaps (missing information)
All resolved in round 2 under the stakeholder's delegation:
- G-01 (prototype unreadable) → Q-04: build from written design rules; prototype kept as reference (DD-01).
- G-02 (hosting) → Q-02: Vercel default URL, per plan.
- G-03 (end point) → Q-03: steps 1 to 3, per plan.
- G-04 (real content) → Q-05: not ready; placeholders until step 3, per plan.
- G-05 (project card fields) → Q-06: per plan and TL design; hidden missing link is DD-02.
- G-06 (skills format) → Q-07: flat list (DD-03).
- G-07 (About contents) → Q-08: portrait, no buttons (DD-04).
- G-08 (project count) → Q-09: 1 to 3 (DD-05).
- G-09 (real-device check) → Q-10: stakeholder on his own phones (DD-06).
- G-10 (extra features) → Q-11: none in v1.

## 8. Ambiguities (more than one reading)
- AMB-01: resolved as reading (a): the plan v2.1 with the PO decisions from #2 and the TeamLead design rules is the v1 baseline (Q-01).
- AMB-02: resolved: the footer shows only the credit line (Q-12).
- AMB-03: "Last 2 versions" for iOS Safari and Android Chrome: assumed to apply to all five browsers (A-05). Low impact, not asked; follows the plan's wording (Q-01).

## 9. Conflicts (sources disagree)
- C-01 (hosting): resolved in favor of the plan: Vercel, default URL (Q-02). This also meets the PO's "default URL ... or similar free hosting" (SRC-3 PO answers Q6).
- C-02 (header, resolved in source): sticky header with the short-screen exception (SRC-2 D5, TL design §4; BR-06).
- C-03 (milestones, resolved in source): the signed-off three milestones (SRC-2 §11) apply; Q-03 confirmed all three.
- C-04 (storage blocked, refinement not conflict): compatible; FR-07 states both.

## 10. Assumptions (provisional until confirmed)
- A-01, A-02: became decisions (Q-01).
- A-03: became a decision (Q-06).
- A-04: became a decision (Q-05).
- A-06: became a decision (Q-11).
- A-05 (remaining, low impact): "Last 2 versions" applies to all five listed browsers.

## 11. Risks and external dependencies
- R-01: The prototype is unreadable; the team builds from the written rules and the stakeholder first sees the look on the built page (Q-04). Mitigation: stakeholder feedback on the first built version; prototype used if it becomes readable.
- R-02: The stakeholder's Vercel account must exist before step 2 (SRC-2 §7, §16). Whose account is still to be provided by the stakeholder; it blocks step 2 only.
- R-03: Real content from the stakeholder blocks step 3 only (SRC-2 §15).
- R-04: A placeholder leaks into launch (high impact); mitigated by FR-12 searching built output and the encoded form (SRC-2 §15).
- R-05: iOS Safari quirks found late; real-device check by the stakeholder at step 2 (Q-10).
- R-06: Visible email gets scraped for spam (accepted, BR-05).

## 12. Delegated decisions (stakeholder may override)
The stakeholder delegated all open questions (SRC-5). Decisions taken directly from the plan are
cited in §3–§5 and in `questions.md`. The following are **delegated defaults**, where the plan is
silent and the BA chose the least addition:
| ID | Decision | Question |
|---|---|---|
| DD-01 | Build from the written design rules; the prototype is a reference only; placeholder copy is sample text with the marker in front; placeholder images are simple marked placeholders | Q-04 |
| DD-02 | A project link the project does not have is hidden | Q-06 |
| DD-03 | Skills are one flat list of names, no grouping or levels | Q-07 |
| DD-04 | About has a portrait but no buttons | Q-08 |
| DD-05 | 1 to 3 projects | Q-09 |
| DD-06 | The stakeholder does the real-device check on his own phones | Q-10 |
