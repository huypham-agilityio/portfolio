---
source: "https://github.com/toinguyen-agilityio/my-portfolio/issues/3"
retrieved: 2026-10-27T15:39:51Z
converter: gh issues
---

# Plan: Personal portfolio web app (epic #2)

_by @toinguyen-agilityio, OPEN_

**Status:** ✅ Signed off · **Version:** 2.1 · **Parent epic:** #2 (closed as completed by the PO, 2026-10-27) · **Plan owner:** BA · **🎨 Prototype:** https://claude.ai/artifact/97JaGNJomJK7emFVUcYLVY

## 1. Background

Huy Pham needs one public page that shows a profile, projects and skills, and a way to get in touch. The PO confirmed the requirements in #2. They are final for v1.

## 2. Goals and success metrics

These are the epic acceptance criteria.

| # | Goal | How we measure it | Milestone |
|---|---|---|---|
| 1 | The page is public | Reachable on one Vercel URL | M2 |
| 2 | It works on every target screen | All 4 sections visible at 320px and up in the listed browsers, no horizontal scroll | M1 |
| 3 | Visitors can reach the owner | Email, GitHub and LinkedIn links work | M1 |
| 4 | Theme works | Manual toggle; default follows the system | M1 |
| 5 | Launch is clean | Search for `[PLACEHOLDER]` returns nothing | M3 |
| – | Accessible | axe reports 0 serious or critical issues; WCAG 2.1 AA in both themes | M1 |

## 3. Stakeholders (RACI)

| Area | R | A | C | I |
|---|---|---|---|---|
| Requirements and content | PO | PO | BA | Team |
| Plan | BA | TeamLead | PO | Dev, QA |
| Tech and design | TeamLead | TeamLead | Dev | PO, BA |
| Build (T1a–T7c) | Dev | TeamLead | BA | PO |
| QA and placeholder audit (T9, T8) | QA | TeamLead | Dev | PO |
| Launch sign-off | TeamLead | PO | QA | All |

## 4. Scope

**In scope:** a single page in English with About, Projects, Skills and Contact, a dark mode toggle, a 404 page, basic SEO and accessibility, and the default Vercel URL.

**Out of scope (phase 2):** Experience, Education, contact form, Vietnamese version, custom domain, Open Graph preview, formal performance budget, automated deploy block while placeholders remain.

## 5. Requirements

**Functional**
- **Theme:** follows the system on first visit. The toggle overrides it and the choice persists. If storage is blocked, the toggle still works for the session. No flash of the wrong theme.
- **Navigation:** header with anchor links (About · Projects · Skills · Contact) and the theme toggle.
- **Contact:** visible email text plus a `mailto:` link. GitHub and LinkedIn open in a new tab with `rel="noopener noreferrer"` and "(opens in a new tab)" in the accessible name. No form.
- **404:** basic page with a link home.
- **Placeholders:** every placeholder carries `[PLACEHOLDER]` (formats in §10).

**Non-functional**
- **Browsers:** last 2 versions of Chrome, Safari and Firefox, plus iOS Safari and Android Chrome.
- **Screens:** 320 / 375 / 768 / 1280+ px, portrait and landscape. No horizontal scroll, no clipped text.
- **Accessibility:** WCAG 2.1 AA in both themes, keyboard navigation, visible focus, alt text, accessible link names, `lang="en"`.
- **SEO:** page title, meta description, favicon.
- **Images:** set `width`/`height`, lazy-load below the fold, local files only.

## 6. Assumptions and constraints

**Assumptions**
- The PO provides real content before M3.
- A Vercel account becomes available for M2.
- Edge behaves like Chrome, since both are Chromium.

**Constraints**
- Static output only. No backend.
- No deadline. Priority is a working public URL first, then polish.

## 7. Dependencies

| Dependency | Blocks | Owner | Status |
|---|---|---|---|
| Vercel account | T1b (M2) | PO | Pending |
| Real content: headline, bio, projects, skills, email, GitHub and LinkedIn URLs | T8a (M3) | PO | Pending |

## 8. Decision log

All decisions were made on 2026-10-27. Details are in the TeamLead comments on this issue.

| # | Decision | Why |
|---|---|---|
| D1 | Next.js (App Router) + TypeScript, `output: 'export'`, pnpm, Node 22, ESLint + Prettier | Static HTML that runs on Vercel or any host |
| D2 | Tailwind v4 with tokens as CSS variables and `.dark` on `<html>`. No `dark:` classes in components | One class switches the theme |
| D3 | All content lives in `src/content.ts` | Swapping content is a one-file PR |
| D4 | Inline pre-paint theme script with `try/catch` around `localStorage`, plus `color-scheme` and `theme-color` | No flash; safe when storage is blocked |
| D5 | Sticky header, static at `max-height: 480px`. No hamburger menu | Saves space on phones in landscape. Replaces the earlier "not sticky" call |
| D6 | Toggle uses a fixed `aria-label="Dark theme"` plus `aria-pressed` | Screen readers announce the state |
| D7 | Inter via `next/font/google`, self-hosted at build time | No third-party request, no text jump |
| D8 | v1 runs locally first. The Vercel deploy is its own story (T1b) | The account isn't ready yet |
| D9 | No separate Edge test pass | The Chromium project covers it |
| D10 | Plain-text email accepted for v1 | PO requirement. Revisit with the contact form in phase 2 |
| D11 | The prototype is the visual spec for v1, with the 6 fixes in §9 | Clean, built from one token set, 44px touch targets, skip link and reduced motion already in |

## 9. Design

**Visual spec**
- **Prototype:** https://claude.ai/artifact/97JaGNJomJK7emFVUcYLVY
- **Boards:** desktop 1280, tablet 768, mobile 375 (dark), mobile 320, 404, tokens.
- **Rules:** [TeamLead design comment](https://github.com/toinguyen-agilityio/my-portfolio/issues/3#issuecomment-6437477342). Where the prototype and the comment disagree, the comment wins.

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg` | #FFFFFF | #0F1117 | Page background |
| `--surface` | #F3F4F7 | #171A22 | Alternate sections, chips, image slots |
| `--text` | #12141A | #EEF0F5 | Body and headings |
| `--muted` | #4B5163 | #A3AABC | Secondary text |
| `--accent` | #3A47D5 | #94A0FF | Links, primary button, focus ring |
| `--on-accent` | #FFFFFF | #0F1117 | Text on accent |
| `--line` | #E2E5EB | #2B303C | Decorative dividers and borders |
| `--ctl` | #7D8396 | #6C7388 | Borders of controls (3:1 on surface) |

- **Type:** H1 `clamp(32px, 5.2vw, 56px)` / 1.1 / 700; H2 `clamp(26px, 3.6vw, 36px)` / 1.2 / 700; H3 20 / 1.3 / 600; body 16 / 1.6; small 13–15 / 1.5 / 500.
- **Layout:** container max 1080px, 24px gutters, 8px unit. Focus ring 3px `--accent`, 2px offset, `:focus-visible` only.
- **Images:** portrait 1:1 at 220px, project thumbnails 16:9. v1 reuses the prototype's SVG illustrations as inline components that read the theme colors. Real images come in T8a via `next/image` with `unoptimized: true`.

**Fixes to the prototype (build the fixed version)**
1. Light `--ctl` is `#7D8396`, not `#8A90A2`.
2. Use `html { scroll-padding-top: var(--header-h) }` (72px or 112px, 0 when static), not per-section margins.
3. Toggle uses a fixed `aria-label` plus `aria-pressed`.
4. Cards are not clickable. No `.card:hover`; only "Live demo" and "Source" links get hover states.
5. `src/content.ts` keeps the prototype copy with the marker in front, for example `"[PLACEHOLDER] Frontend engineer building fast, accessible web apps"`.
6. 404 links point to `/`. No toggle in the 404 header.

## 10. Placeholder formats

- **Text:** `[PLACEHOLDER]` in the content. "Huy Pham" is real and has no marker.
- **Web links:** `https://example.com/?ph=[PLACEHOLDER]`
- **Email:** text `placeholder@example.com [PLACEHOLDER]`, link `mailto:placeholder@example.com?subject=[PLACEHOLDER]`
- **Images:** alt text includes `[PLACEHOLDER]`, and file names include `placeholder`.

## 11. Milestones

| Milestone | Exit criteria |
|---|---|
| **M1 – Local v1** | All sections done, `pnpm build` passes, QA passes on `out/`, CI green. Placeholders allowed |
| **M2 – Public URL** | Deployed on Vercel, real-device check on iOS Safari and Android Chrome passes. Criterion 1 passes |
| **M3 – Launch** | Real content in, placeholder audit returns nothing. Criterion 5 passes |

## 12. Stories

| ID | Story | Acceptance criteria (summary) | Depends on | Milestone |
|---|---|---|---|---|
| T1a | Setup: Next.js, TS, Tailwind, pnpm, lint, `src/content.ts`, Inter, `images.unoptimized`, CI, README | `pnpm build` produces `out/`; CI green on a PR | – | M1 |
| T2 | Layout: tokens, base components, sticky header nav, theme toggle, pre-paint script | DoD; no flash; choice persists; works with storage blocked; anchors land below the header | T1a | M1 |
| T3 | About | Name, headline and bio; placeholders marked; DoD | T2 | M1 |
| T4 | Projects (`ProjectCard`, SVG thumbnails) | At least 1 card; cards not clickable; DoD | T2 | M1 |
| T5 | Skills | Skill list marked; DoD | T2 | M1 |
| T6 | Contact | Email and links per §5; long text wraps at 320px (`overflow-wrap: anywhere`); DoD | T2 | M1 |
| T7a | Title, meta description, `lang="en"`, favicon | Set; marked where placeholder | T1a | M1 |
| T7b | 404 page | Any unknown path; both themes; no toggle | T2 | M1 |
| T7c | Accessibility audit and skip link | axe 0 serious or critical; AA in both themes | T3–T6 | M1 |
| T9 | QA on local production build | All §5 checks pass except the live URL and real devices | T3–T7c | M1 |
| T1b | Vercel deploy, preview deploys per PR, real-device check; footer becomes "Built with Next.js and deployed on Vercel" | Public URL works | T9, Vercel account | M2 |
| T8a | Replace placeholders with PO content | Only `src/content.ts` and image files change | T3–T6, PO content | M3 |
| T8 | Placeholder audit and launch sign-off | §14 audit returns nothing; T9 re-check passes on the Vercel URL | T8a, T1b | M3 |

T3–T6, T7a and T7b can run in parallel once T2 is merged. The TeamLead adds estimates when creating the stories.

## 13. Definition of Ready and Definition of Done

**DoR:** acceptance criteria are clear, dependencies are merged, the matching prototype board is linked, and the placeholder format is known.

**DoD (UI stories T2–T6):** matches the prototype board with the §9 fixes, keyboard reachable, visible focus, correct landmarks and heading order, checked in both themes, no horizontal scroll at 320px, axe reports 0 serious or critical issues, images have `width`/`height`, CI green, PR reviewed.

## 14. Test strategy

| What | Tool | When |
|---|---|---|
| Lint, typecheck, build | ESLint, `tsc`, `next build` | Every PR |
| E2E: widths, theme, storage blocked, links, anchors | Playwright (Chromium, WebKit, Firefox, mobile emulation) | Every PR |
| Accessibility | @axe-core/playwright | Every PR; full audit in T7c |
| Visual match | Side-by-side with the prototype boards at 320, 375, 768, 1280 | PR review of T2–T7b |
| Quick phone check | `pnpm dev --hostname 0.0.0.0` on the same Wi-Fi | Optional, during dev |
| Real devices | iOS Safari and Android Chrome on the Vercel URL | M2 (T1b) |
| Placeholder audit | Case-insensitive search for `[PLACEHOLDER]` and `%5BPLACEHOLDER%5D` in source, `out/` HTML and image file names | M3 (T8) |

## 15. Risks

| Risk | Likelihood | Impact | Mitigation | Owner |
|---|---|---|---|---|
| Content arrives late | Medium | Medium (blocks M3 only) | Build fully on placeholders; content isolated in one file | PO |
| Vercel account delayed | Medium | Medium (blocks M2) | Static export runs on any host | PO |
| iOS Safari quirks found late | Medium | Medium | Mobile emulation in dev; real-device pass at M2 | QA |
| Theme flash comes back | Low | Medium | Pre-paint script plus a Playwright check | Dev |
| A placeholder leaks into launch | Low | High | T8 searches the encoded form and `out/` too | QA |
| Devs copy prototype bugs | Medium | Medium | §9 lists the 6 fixes; the design comment wins over the prototype | TeamLead |
| Visible email gets scraped for spam | High | Low | Accepted for v1; contact form in phase 2 | PO |

## 16. Open questions

| Question | Owner | Needed by |
|---|---|---|
| Final content: headline wording, bio, projects, skills, email, GitHub and LinkedIn URLs | PO | Before T8a |
| Which Vercel account or team hosts the project | PO | Before T1b |

## 17. Change log and sign-off

**Change log**
- v1.0 (2026-10-27): plan created from #2.
- v1.1 (2026-10-27): TeamLead review added milestones, T8a, placeholder formats and WCAG 2.1 AA.
- v1.2 (2026-10-27): local-first v1, navigation and final story list.
- v1.3 (2026-10-27): design tokens and prototype fixes.
- v2.0 (2026-10-27): restructured into the standard plan format. No scope change.
- v2.1 (2026-10-27): prototype link and boards made prominent; added to D11, DoR, DoD, test strategy and risks. No scope change.

**Sign-off**

| Role | What | Date | Ref |
|---|---|---|---|
| PO | Requirements confirmed | 2026-10-27 | #2 |
| TeamLead | Plan signed off | 2026-10-27 | [comment](https://github.com/toinguyen-agilityio/my-portfolio/issues/3#issuecomment-6437360984) |
| TeamLead | Design (prototype + 6 fixes) signed off | 2026-10-27 | [comment](https://github.com/toinguyen-agilityio/my-portfolio/issues/3#issuecomment-6437477342) |

## 18. Glossary

- **`[PLACEHOLDER]`:** marker on fake content. None may remain at launch.
- **`out/`:** the static HTML build output of `pnpm build`.
- **Prototype:** the approved visual design at the link above. Not production code.
- **Pre-paint script:** inline script in `<head>` that sets the theme before the page renders.
- **DoR / DoD:** Definition of Ready (a story can start) and Definition of Done (a story is finished).

## Comment by @toinguyen-agilityio

@claude  Review this planning ticket.

## Comment by @claude

**Claude finished @toinguyen-agilityio's task in 25s** —— [View job](https://github.com/toinguyen-agilityio/my-portfolio/actions/runs/40472180648)

---
### Plan review: Personal portfolio web app (epic #2)

Overall the plan is solid. The requirements are specific and testable, and the task breakdown is clear. I found a few gaps and ambiguities worth fixing before the TeamLead splits it into stories. I only read the issue; I did not change any code.

#### Gaps and risks

1. **`[PLACEHOLDER]` marker vs. real usability.** The marker has to appear in the page title, meta description, alt text and link targets. A link target like `https://[PLACEHOLDER]` is not a valid URL, and `mailto:[PLACEHOLDER]` is not a valid address. Decide the exact format now, for example `https://example.com/[PLACEHOLDER]` and `mailto:placeholder@example.com?subject=[PLACEHOLDER]`. Otherwise link checks in T9 will fail by design. The marker in the `<title>` and in the meta description will also show up in browser tabs and search snippets. That is intended, but note it in the plan.
2. **T8 and T9 ordering and the epic's "working public URL first" priority.** Launch sign-off requires zero `[PLACEHOLDER]`, but the real content is an open item owned by the PO. Say who runs T8 and what happens if the content has not arrived. The T8 search can only pass after content replacement, so add an explicit task, or a T8 sub-step, for "replace placeholders with PO content". As written, nothing in T1–T9 does that replacement.
3. **T8 search scope is incomplete.** "Content, assets, alt text, page title, meta description and link targets" is good. Add image filenames, file metadata (for example EXIF) and the built output. Search the deployed HTML, not only the source, so anything injected at build time is caught.
4. **Theme flash (T2).** "No visible flash" generally needs an inline blocking script that sets the theme before first paint. With Next.js SSR or SSG this is a known pitfall. Name it as an implementation note or acceptance test so it is not missed. Also state how it is verified, for example a throttled-CPU reload.
5. **"Acceptable contrast" is vague.** T2 says "acceptable" and T7 says "passes". Pin both to one standard, such as WCAG 2.1 AA (4.5:1 body text, 3:1 large text and UI components), in both themes.
6. **Accessibility is deferred to T7.** Landmarks, heading order, focus styles, the toggle's accessible name and state (`aria-pressed` or a label), and `prefers-reduced-motion` are cheapest to build into T2–T6. Add "accessible by default" to those tasks' acceptance criteria and keep T7 as the audit. Consider a skip-to-content link, since it is a single-page layout.
7. **T7 bundles unrelated work.** Accessibility audit, title/meta and the 404 page have different owners and sizes. Splitting them makes stories smaller. The 404 page depends only on T1/T2, so it could be done earlier.
8. **404 page specifics.** State that it works on Vercel with the chosen stack, has a link back to the home page, supports both themes, and carries the `[PLACEHOLDER]` marker only where content is placeholder.
9. **Image handling.** Placeholder images are in scope, but there is no guidance on source, format, size or lazy loading. Cheap defaults: set explicit width/height to avoid layout shift, and compress images. "No formal performance budget" is fine, but basic hygiene costs nothing.
10. **Browser matrix.** "Last 2 versions" of Chrome, Safari and Firefox plus iOS Safari and Android Chrome is fine. State how it will be tested (real devices, BrowserStack, or emulation) so T9 is executable. Edge is not listed. Say whether that is deliberate.
11. **Mobile viewport details.** At 320px, long email addresses and URLs are the usual cause of horizontal scroll and clipped text. Add a specific check on the contact section (T6) with `overflow-wrap`. Landscape on small phones also needs checking, since the sticky header, if any, eats vertical space.
12. **Storage blocked.** Be explicit about the expected fallback: theme follows the system preference and the toggle works for the current session only. Also cover `localStorage` throwing in private modes, not only being absent.
13. **Contact obfuscation and spam.** A visible email in plain HTML invites scrapers. This is acceptable for v1 given the PO's requirement, but worth recording as a known tradeoff.
14. **Anchor navigation.** It is a single page with four sections, but the plan has no in-page navigation (header links, smooth scroll, active state). Confirm whether a nav is wanted. If so, it needs keyboard and mobile behavior (T2).
15. **Typos and naming.** "TeadLead" appears several times and should be "TeamLead". The agent definitions in this repo use "TeamLead".

#### Smaller suggestions

- T1 should also cover the repo basics: lint/format config, a CI check that runs build and lint on PRs, Vercel preview deployments, and a README with run instructions. The plan says only "build runs locally and deploys".
- Add the Vercel project/account owner as a dependency for T1, since someone needs access.
- Add `lang="en"` on the `<html>` element to the accessibility criteria. Also add a favicon, which is not mentioned and will otherwise 404 in the console.
- Epic acceptance criterion 2 says "readable", which is subjective. Reuse the contrast and responsive criteria instead.
- The page title and meta description are only specified as placeholders. Say whether the structure (for example `Huy Pham – [PLACEHOLDER]`) is fixed now.

#### Verdict

The plan is ready to hand off once items 1, 2, 4 and 5 are resolved, since they affect acceptance criteria. The rest can be handled by the TeamLead while writing stories. Out-of-scope items are clearly listed and consistent with the requirements.

## Comment by @toinguyen-agilityio

## TeamLead review: changes requested before sign-off

The requirements are clear and the scope is tight. I agree with the earlier review's items 1, 2, 4 and 5. The typo in item 15 is already fixed. This comment does not repeat that review. It records my decisions as TeamLead and lists the changes I need in the plan before I split it into stories.

### 1. Tech stack (decided)

| Layer | Decision | Why |
|---|---|---|
| Framework | **Next.js (App Router) + TypeScript**, static output | Vercel runs it natively with zero config. A static page needs no server. |
| Styling | **Tailwind CSS**, `darkMode: 'class'` | Theme switching is a single class on `<html>`. Responsive breakpoints are built in. |
| Theme | Small inline script in `<head>` that sets the class **before first paint**, wrapped in `try/catch` around `localStorage` | Covers "no flash" and "storage blocked". No theme library needed. |
| Content | **One typed file** `src/content.ts` holds all text, links and image references | Replacing placeholders becomes a one-file PR, and the T8 search has a clear target. |
| Tooling | pnpm, Node 22 LTS, ESLint + Prettier | |
| Tests | **Playwright** (Chromium, WebKit, Firefox, plus mobile emulation) + **@axe-core/playwright** | Automates widths, theme, storage-blocked, links and contrast. Real devices are only needed for one final manual pass. |
| CI | GitHub Actions on each PR: lint, typecheck, build, Playwright. Vercel preview deploy per PR | |

### 2. Changes needed in the plan (blocking)

**a. Separate "first public URL" from "launch".** The plan puts "working public URL first" first, but epic criterion 5 requires zero `[PLACEHOLDER]`. Both are fine once they are two milestones:
- **M1, public URL:** T1 to T7 deployed with placeholders. Criteria 1 to 4 pass.
- **M2, launch:** real content in, T8 search returns nothing. Criterion 5 passes.

**b. Add the missing task: replace placeholders with PO content.** No task does this today. Add **T8a – Content replacement** (depends on PO content and T3 to T6). It only edits `src/content.ts` and the images.

**c. Fix the T8/T9 dependency.** As written, QA (T9) waits on T8, and T8 waits on content we don't have yet, so QA is blocked by the PO. Proposal:
- **T9 QA** depends on T3 to T7 and runs on the placeholder build (M1).
- **T8 audit** moves to the end as the launch gate: T8a, then T8, then a short re-check of T9.

**d. Placeholder format for links.** `[` and `]` are not valid raw in a URL, and the build encodes them as `%5BPLACEHOLDER%5D`, which a plain search for `[PLACEHOLDER]` misses. Fixed formats:
- Web links: `https://example.com/?ph=[PLACEHOLDER]`
- Email text: `placeholder@example.com [PLACEHOLDER]`, link: `mailto:placeholder@example.com?subject=[PLACEHOLDER]`
- T8 searches **the source and the built `out/` HTML**, for both `[PLACEHOLDER]` and `%5BPLACEHOLDER%5D` (case-insensitive). Also check image file names.
- T9's link check treats `example.com` as expected in M1, so it doesn't fail on purpose.

**e. Contrast standard:** **WCAG 2.1 AA** in both themes (4.5:1 for text, 3:1 for large text and UI such as the toggle and focus ring). Use the same wording in T2, T7 and the epic criteria, and drop "acceptable" and "readable".

### 3. Restructured stories (non-blocking, I'll apply them when creating stories)

- **Common Definition of Done for every UI story (T2 to T6):** keyboard reachable, visible focus, correct heading order and landmarks, both themes checked, no horizontal scroll at 320px, axe reports 0 serious or critical issues. A11y is built in each story. T7 is the audit, not the first time we look at it.
- **Split T7:**
  - T7a – `<title>`, meta description, `lang="en"`, favicon (depends on T1)
  - T7b – 404 page: both themes, link back home (depends on T2, can start early)
  - T7c – Accessibility audit + skip-to-content link (depends on T3 to T6)
- **T2 adds:** the toggle has an accessible name and `aria-pressed`, and respects `prefers-reduced-motion`. **Storage-blocked behaviour:** follow the system theme, and the toggle still works for the current session.
- **T6 adds:** long email or URL at 320px must not cause horizontal scroll (`overflow-wrap: anywhere`). Record the spam risk of a visible email as a known v1 tradeoff.
- **Images:** set explicit `width`/`height` (no layout shift), lazy-load anything below the fold, use local placeholder images (no hotlinking).

### 4. Questions for the PO (@toinguyen-agilityio)

1. **Navigation:** do we want a header with anchor links (About · Projects · Skills · Contact) next to the toggle? My default is **yes, simple and with no hamburger menu**. Links wrap at 320px.
2. **Edge:** not in the browser list. My default is that it is not formally tested. It is Chromium, so it should work. OK?
3. **Vercel account:** whose account/team hosts the project? This blocks T1.
4. **Content ETA:** a rough date for the content, so we can plan M2.

### Verdict

🔴 **Not signed off yet.** Once the BA updates the plan with **2a to 2e** and the PO answers **question 3** (and ideally 1 and 2), I'll sign off and create the stories. Section 3 doesn't need a plan change. I'll put it into the stories directly.

---
_TeamLead [Claude Code](https://claude.ai/code)_

## Comment by @toinguyen-agilityio

## TeamLead decisions: plan signed off ✅

Update from the PO: **v1 runs locally first**. The Vercel account will come later. That removes the only real blocker, so I'm closing the open questions from my previous comment with my own calls instead of waiting on answers. This comment is the source of truth for the plan changes. The BA can sync the issue body from it.

### Decisions on the open questions

| Question | Decision | Reasoning |
|---|---|---|
| Public URL / Vercel account | **Not needed for v1 dev.** Deploy becomes a separate task (T1b) that waits on the account and blocks nothing else. | Build with `output: 'export'` (plain static HTML in `out/`). It runs on Vercel with no changes, and on any static host if plans change. |
| Navigation | **Yes.** Simple header with anchor links (About · Projects · Skills · Contact) and the theme toggle. **Not sticky, no hamburger.** Links wrap at 320px. | A sticky header eats vertical space on small phones in landscape, and a hamburger adds JS, focus handling and a11y bugs for 4 links. Sections get `scroll-margin-top`. Smooth scroll is on only when the user hasn't set `prefers-reduced-motion`. |
| Edge | **No separate test pass.** | Edge is Chromium, so the Chromium Playwright project covers it. |
| Content ETA | **Not a dependency.** We build everything with placeholders. Content replacement is its own task that starts when content arrives. | Because all content lives in one typed `src/content.ts`, swapping it later is a one-file PR. |
| Testing on real phones without a URL | Use emulation (Playwright mobile projects) during dev. For a quick manual check, run `pnpm dev --hostname 0.0.0.0` and open it from a phone on the same Wi-Fi. **Formal real-device pass happens at M2** on the Vercel URL. | iOS Safari quirks (viewport units, safe areas) only show on real devices, but they don't need to block local work. |

### Milestones (replaces "first public URL" vs "launch")

- **M1, local v1:** all sections done, `pnpm build` passes, QA passes on the **local production build** (served from `out/`), CI green. Placeholders allowed.
- **M2, public URL:** when the Vercel account arrives. Deploy, then a real-device check on iOS Safari and Android Chrome. Epic criterion 1 is checked here.
- **M3, launch:** real content in, placeholder audit returns nothing. Epic criterion 5 is checked here.

### Items 2a to 2e from my previous review: adopted as written

- Contrast is **WCAG 2.1 AA** in both themes.
- Placeholder link formats are fixed: `https://example.com/?ph=[PLACEHOLDER]` and `mailto:placeholder@example.com?subject=[PLACEHOLDER]`.
- The placeholder audit searches source **and** `out/`, for `[PLACEHOLDER]` and `%5BPLACEHOLDER%5D`, case-insensitive, including image file names.
- The shared Definition of Done applies to every UI story: keyboard reachable, visible focus, landmarks and heading order, both themes, no horizontal scroll at 320px, and axe reports 0 serious or critical issues.

### Final story list

| ID | Story | Depends on | Milestone |
|---|---|---|---|
| T1a | Project setup: Next.js + TS + Tailwind, pnpm, ESLint/Prettier, `src/content.ts`, GitHub Actions CI (lint, typecheck, build, Playwright), README run instructions | – | M1 |
| T2 | Layout, header nav, theme toggle (no-flash inline script, storage-blocked fallback, `aria-pressed`) | T1a | M1 |
| T3 | About section | T2 | M1 |
| T4 | Projects section | T2 | M1 |
| T5 | Skills section | T2 | M1 |
| T6 | Contact section (`overflow-wrap` for long email at 320px) | T2 | M1 |
| T7a | Title, meta description, `lang="en"`, favicon | T1a | M1 |
| T7b | 404 page, both themes, link home | T2 | M1 |
| T7c | Accessibility audit + skip-to-content link | T3–T6 | M1 |
| T9 | QA on local production build (widths, browsers via Playwright, theme, links) | T3–T7c | M1 |
| T1b | Deploy to Vercel + preview deploys per PR + real-device check | T9, Vercel account | M2 |
| T8a | Replace placeholders with PO content | PO content | M3 |
| T8 | Placeholder audit + T9 re-check, launch sign-off | T8a, T1b | M3 |

T3 to T6, T7a and T7b can run in parallel once T2 is merged.

### Known v1 tradeoffs (accepted)

- A plain-text email in the HTML can be scraped for spam. This is acceptable per the PO's requirement and can be revisited in phase 2 with the contact form.
- No formal performance budget. Basic image hygiene is still required: explicit `width`/`height`, lazy loading below the fold, local images only.

**Plan is signed off. Next step: I'll create the stories above, starting with T1a.**

---
_TeamLead [Claude Code](https://claude.ai/code)_

## Comment by @toinguyen-agilityio

## TeamLead: design, theme and style (based on the prototype)

Prototype: https://claude.ai/artifact/97JaGNJomJK7emFVUcYLVY. I read every board: desktop 1280, tablet 768, mobile 375 dark, mobile 320, 404, and tokens.

The prototype is good and I'm **adopting it as the visual spec for v1**. It is clean and minimal, built from one set of tokens, and uses 44px touch targets. The grids work without media queries. It already includes the skip link, focus ring and reduced-motion handling. Below: the decisions for building it, plus **6 fixes** to make before devs treat it as final. I checked contrast myself for every pair of tokens.

### 1. Design tokens (source of truth)

Defined once as CSS variables on `:root`, with `.dark` on `<html>` swapping the set. Tailwind colors point at the variables, so **components never use `dark:` classes**. One class change switches the theme, and every story can't forget it.

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg` | `#FFFFFF` | `#0F1117` | Page background |
| `--surface` | `#F3F4F7` | `#171A22` | Alternate sections, chips, image slots |
| `--text` | `#12141A` | `#EEF0F5` | Body and headings |
| `--muted` | `#4B5163` | `#A3AABC` | Secondary text |
| `--accent` | `#3A47D5` | `#94A0FF` | Links, primary button, focus ring |
| `--on-accent` | `#FFFFFF` | `#0F1117` | Text on accent |
| `--line` | `#E2E5EB` | `#2B303C` | Dividers, card borders (decorative) |
| `--ctl` | **`#7D8396`** ⚠️ (was `#8A90A2`) | `#6C7388` | Borders of controls |

**Contrast check (WCAG 2.1 AA):** text 15.3 to 18.4:1, muted 7.2 to 8.1:1, accent 6.3 to 7.9:1, on-accent 6.9 / 7.9:1. All pass with plenty of margin. **One fails:** light `--ctl` on `--surface` is only **2.9:1**. The GitHub/LinkedIn buttons in the Contact section sit on `--surface`, so they fail 1.4.11 (non-text contrast, 3:1). Changing it to `#7D8396` gives 3.4:1 on surface and 3.8:1 on white. Dark mode is already fine (3.7 / 4.0:1).

**Typography: Inter**, loaded with `next/font/google` (weights 400/500/600/700, latin subset). The font is self-hosted at build time. Don't link Google Fonts from `<head>`: that adds a request to a third party, and the text jumps when the font loads.

| Style | Size / line-height / weight |
|---|---|
| H1 | `clamp(32px, 5.2vw, 56px)` / 1.1 / 700, letter-spacing −0.02em |
| H2 | `clamp(26px, 3.6vw, 36px)` / 1.2 / 700, −0.01em |
| H3 | 20 / 1.3 / 600 |
| Body | 16, hero lead `clamp(17px, 2vw, 19px)` / 1.6 / 400 |
| Small | 13 to 15 / 1.5 / 500 |

**Layout:** container max 1080px, 24px gutters, 8px spacing unit, section padding `clamp(48px, 8vw, 96px)`. Grids use `repeat(auto-fit, minmax(min(100%, 290px), 1fr))`. Radius 8 (nav links), 10 (buttons and chips), 14 (cards), 999 (tags, toggle). Focus ring: 3px `--accent`, 2px offset, `:focus-visible` only.

### 2. Components (one file each, all in T2 unless noted)

`Container`, `Section` (id, H2, intro line), `Button` (primary/secondary, rendered as `<a>`), `ExternalLink` (**always** adds `target="_blank"`, `rel="noopener noreferrer"` and the suffix "(opens in a new tab)" to the accessible name, so no story can forget it), `Chip`, `Tag`, `ThemeToggle`, `Header`, `Footer`. `ProjectCard` goes in T4.

### 3. Fixes to the prototype (devs build the fixed version)

1. **`--ctl` contrast:** see the token table. Use `#7D8396`.
2. **Anchor links hide headings on mobile.** Every section has `scroll-margin-top: 72px`, but at ≤640px the header wraps to 2 rows (about 108px). Clicking "Projects" puts the H2 under the sticky header. Fix: one rule `html { scroll-padding-top: var(--header-h) }`, with `--header-h` set to 72px or 112px depending on width, and `0` when the header is static. Drop the per-section `scroll-margin-top`.
3. **Toggle semantics.** The prototype changes `aria-label` ("Switch to dark theme" / "Switch to light theme"). We use **fixed `aria-label="Dark theme"` + `aria-pressed`**, as decided earlier. Screen readers then announce the state instead of an action that keeps changing. Keep the icons.
4. **Cards are not clickable, so no card hover.** `.card:hover` changes the border, which makes users think the whole card is a link. Remove it. Only the "Live demo" and "Source" links get hover states.
5. **Placeholder marker.** The prototype uses realistic fake copy (`hello@example.com`, "Task Flow"…). That's great for testing line length, but the PO requires `[PLACEHOLDER]`. `src/content.ts` keeps the prototype copy **with the marker in front**, for example `"[PLACEHOLDER] Frontend engineer building fast, accessible web apps"`, plus the link formats agreed earlier. "Huy Pham" is real and has no marker.
6. **404 page:** the "Back to home" and logo links point to `/`, not `Main.dc.html`. Don't put the toggle in the 404 header. Its theme comes from the same pre-paint script, so no extra JS is needed.

### 4. Decision changed: sticky header

I said "not sticky" earlier. The prototype solves my concern better: **sticky, but static when `max-height: 480px`**, so phones in landscape don't lose space. **Adopted.** On ≤640px the nav drops to its own row and the toggle stays next to the name. On ≤400px the nav links shrink to padding 6px and 14px text. I checked: the 4 links fit in one row at 320px.

### 5. Theme behaviour (T2)

- Pre-paint inline script in `<head>`: read `localStorage.theme` (in `try/catch`), otherwise `matchMedia('(prefers-color-scheme: dark)')`, then set `.dark` on `<html>` **before** the body renders.
- Also set CSS `color-scheme: light` / `dark` so scrollbars and native controls match, plus `<meta name="theme-color">` for both themes (mobile browser toolbar).
- Before the user clicks the toggle, also listen for system theme changes. After they've chosen, their choice wins.

### 6. Images

- **Portrait** 1:1, shown at 220px. **Project thumbnails** 16:9 (320×180 viewBox).
- For v1, reuse the prototype's SVG illustrations as **inline React components**, so they pick up the theme colors (an `<img>` can't read the CSS variables). The `aria-label`/alt text carries `[PLACEHOLDER]`.
- Real screenshots arrive in T8a and use `next/image` with `unoptimized: true`. That's required with `output: 'export'`, so set it in T1a. Always set `width`/`height` and lazy-load images below the fold.

### 7. Impact on stories

- **T1a** adds: `next/font` Inter, Tailwind v4 config mapping the tokens, `images.unoptimized`.
- **T2** adds: tokens, base components (section 2), header/toggle with fixes 2, 3 and the sticky rule, and the pre-paint script.
- **T4** adds: `ProjectCard` with fix 4, and the SVG placeholder components.
- **T7b**: fix 6.
- **T9** adds: check that anchor links land below the header at 320, 375, 768 and 1280, and in 375 landscape.

The footer text "Built with Next.js and deployed on Vercel" becomes **"Built with Next.js"** until T1b is done, so the page doesn't claim something that isn't true yet.

The design is **signed off** with the 6 fixes above. Devs follow this comment and the prototype. Where the two disagree, this comment wins.

---
_TeamLead [Claude Code](https://claude.ai/code)_

## Comment by @toinguyen-agilityio

## TeamLead: M1 breakdown is ready (20 tickets)

All M1 stories (T1a–T9) are split into tickets of **half a day to one day**. Each ticket has scope, acceptance criteria, the matching design rules and its dependencies. All of them are **sub-issues of this plan**, belong to the GitHub milestone **M1 – Local v1**, and are linked with GitHub's native **blocked by / blocking** relations, which also appear as text in each ticket body.

### Tickets

| # | Story | Ticket | Priority | Size | Blocked by |
|---|---|---|---|---|---|
| #9 | T1a | Scaffold Next.js app with static export | P0 | S | – |
| #10 | T1a | ESLint, Prettier and typecheck scripts | P1 | S | #9 |
| #11 | T1a | Tailwind v4, design tokens and Inter font | P0 | M | #9 |
| #12 | T1a | Typed content model in `src/content.ts` | P0 | S | #9 |
| #13 | T1a | Playwright and axe test harness | P0 | M | #9 |
| #14 | T1a | CI workflow for pull requests | P1 | S | #10, #13 |
| #15 | T1a | README with stack and run instructions | P2 | XS | #14 |
| #16 | T2 | Pre-paint theme script and ThemeToggle | P0 | M | #11, #13 |
| #17 | T2 | Base UI components | P0 | M | #11 |
| #18 | T2 | Sticky header, footer and page skeleton | P0 | M | #16, #17 |
| #19 | T3 | About (hero) section | P1 | S | #18, #12 |
| #20 | T4 | Project thumbnail SVG components | P1 | S | #11 |
| #21 | T4 | ProjectCard and Projects section | P1 | M | #18, #12, #20 |
| #22 | T5 | Skills section | P1 | S | #18, #12 |
| #23 | T6 | Contact section | P1 | S | #18, #12 |
| #24 | T7a | Page metadata, `lang` and favicon | P2 | XS | #9, #12 |
| #25 | T7b | 404 page | P2 | S | #18 |
| #26 | T7c | Skip link and accessibility audit | P1 | M | #19, #21, #22, #23, #25 |
| #27 | T9 | Responsive and link regression suite | P1 | M | #19, #21, #22, #23 |
| #28 | T9 | QA pass on local production build, M1 sign-off | P1 | S | #24, #26, #27, #15 |

### Critical path

`#9 → #11 → #16 → #18 → sections (#19 #21 #22 #23) → #26 → #28`

- Once #9 is merged, **#10, #11, #12, #13 and #24 can run in parallel**.
- Once #18 is merged, **#19, #21, #22, #23 and #25 can run in parallel**. #20 can start early, as soon as #11 lands.
- Total is about 13–14 dev-days of work. With 2 devs working in parallel, M1 is roughly 1.5 weeks.

### Two changes from the plan's story list (no scope change)

- **Tokens and Inter move from T2 into T1a (#11).** Both the theme toggle and the components depend on them, so they have to land first.
- **T9 is split** into an automated regression suite (#27, kept in CI so M3 content can't break the layout) and the manual QA pass and sign-off (#28).

### Labels and workflow

| Label | Meaning |
|---|---|
| `priority: P0` | Critical path. Blocks other tickets, so do it first |
| `priority: P1` | Required for M1, can run in parallel |
| `priority: P2` | Required for M1, but nothing waits on it |
| `size: XS / S / M` | ≤ 2 hours / ≤ half a day / about 1 day |
| `area: …` | Part of the codebase (setup, theme, layout, contact, a11y…) |
| `status: backlog` → `status: todo` | Status flow, see below |

**Status flow:** every ticket starts in **`status: backlog`**. When a dev picks up a ticket, they **swap it to `status: todo`** and assign themselves. Pick-up rules:
1. Take the highest priority first (P0, then P1, then P2).
2. Only take a ticket whose "Blocked by" tickets are all merged.
3. Branch and PR follow `CONTRIBUTING.md`, for example `feat/23-contact-section`, with `Closes #23` in the PR.

---
_Generated by [Claude Code](https://claude.ai/code)_

