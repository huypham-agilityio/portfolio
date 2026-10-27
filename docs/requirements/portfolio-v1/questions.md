# Clarifying questions: Personal portfolio web app (v1)

- Slug: `portfolio-v1`
- Open: 0 · Answered: 0 · Confirmed: 12 · Deferred: 0
- Next batch to ask: none (all confirmed; ready for GATE 1)

Rules: the PM asks each question **verbatim** (translation allowed, no rephrasing, merging or
answering) and records the answer verbatim plus an English translation. Only the BA changes a
status to `confirmed` or `deferred`.

**Round 2 note (2026-10-27):** the stakeholder answered every question with the same reply,
an explicit delegation: "You decide all of them yourself; I will update later if needed. Stick as
closely as possible to the plan I sent." (also in `sources/stakeholder-notes.md`). The BA applied
one rule per question: where plan #3 (SRC-2), epic #2 (SRC-3) or the TeamLead design comment
("TL design") states the answer, that option is taken and cited; where they are silent, the
option that adds the least beyond the plan is taken and marked **delegated default**. Every
decision is listed in `understanding.md` so the stakeholder can override it at GATE 1.

---

### Q-01: Does the old plan carry over unchanged?
- **Question:** For this new repository, should we treat the old plan (v2.1, issue #3) together with your decisions in epic #2 and the TeamLead's design rules as the agreed starting point for v1, exactly as they are?
- **Why it matters:** It decides whether every requirement in `requirements.md` is already agreed or must be re-confirmed one by one. If something has changed since then (a section, a rule, the phase 2 list), we need to know now, before stories are written.
- **Related:** AMB-01, A-01, A-02, FR-01 to FR-15, Scope
- **Options:**
  - A) Yes, take all of it unchanged (four sections, theme, 404, accessibility, placeholder rules, design rules, phase 2 list).
  - B) Yes, with some changes (please list them).
  - C) Only your decisions in #2 count; plan and design details should be re-decided for this repo.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A**. The answer itself says "stick as closely as possible to the plan I sent", so plan v2.1 (SRC-2) with the PO decisions in #2 (SRC-3) and the TL design comment is the v1 baseline. A-01 and A-02 become decisions; AMB-01 resolved as reading (a). Exceptions only where the plan cannot be followed in this repo (prototype unreadable, Q-04; old code and tickets not reused, SRC-1). FR-01 to FR-15 status updated in `requirements.md`.

### Q-02: Where should the public page be hosted?
- **Question:** Where should the public version of the page live?
- **Why it matters:** In #2 you said "GitHub Pages or similar free hosting", the plan says Vercel, and the old team noted you never confirmed Vercel yourself. This repository is currently set up with no deployment. The choice decides the public URL, who needs an account, and the footer text.
- **Related:** C-01, G-02, FR-13, FR-15, NFR-10, R-02
- **Options:**
  - A) Vercel, with its free default URL (as in the plan). Please say whose Vercel account.
  - B) GitHub Pages on this repository's account, with its free default URL.
  - C) No public hosting in this project for now; build and check it locally, decide hosting later.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A, Vercel with its free default URL**, as stated in the plan (SRC-2 §2 goal 1, §4, D8; SRC-3 "Hosting: Vercel, default URL"). C-01 resolved in favor of the plan; Vercel default URL also satisfies the PO's earlier "default URL ... or similar free hosting". Per the plan (D8, §11), v1 is built and checked locally first and the Vercel deploy is its own later piece of work, so this does **not** change `deploy.platform: none` in `.squad/config.yml` now. Whose Vercel account is not a requirement decision: it stays a stakeholder-owned dependency needed before the deploy work (SRC-2 §7, §16; R-02), exactly as in the plan.

### Q-03: How far should this project go?
- **Question:** Which end point should this set of work cover?
- **Why it matters:** The plan had three steps: (1) a complete page on placeholders checked locally, (2) the same page on a public URL, (3) launch with your real content and a check that no placeholder remains. It decides which requirements become stories now.
- **Related:** G-03, C-03, FR-11, FR-12, FR-13, NFR-10
- **Options:**
  - A) Step 1 only: complete page with placeholders, checked locally.
  - B) Steps 1 and 2: public URL, still with placeholders.
  - C) Steps 1 to 3: all the way to launch with real content.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option C, steps 1 to 3**, because the plan covers all three milestones (SRC-2 §2, §11 M1 Local v1, M2 Public URL, M3 Launch). Order follows the plan: step 1 depends on nothing external; step 2 waits on the Vercel account; step 3 waits on the stakeholder's real content (SRC-2 §7). FR-11, FR-12, FR-13 and NFR-10 are in scope.

### Q-04: Can you share the prototype?
- **Question:** The plan says the prototype (https://claude.ai/artifact/97JaGNJomJK7emFVUcYLVY) is the visual design for v1, but we cannot open it. How should we get the design?
- **Why it matters:** Layouts, sample text, buttons and illustrations come from it, and every screen is reviewed against it. Without it, the team would build only from the written design rules and you would see the look for the first time in the built page.
- **Related:** G-01, G-07, NFR-09, FR-03, FR-04, FR-10, R-01
- **Options:**
  - A) I will export it (HTML file or screenshots of all boards: desktop 1280, tablet 768, mobile 375 dark, mobile 320, 404, tokens) and add it to the repo.
  - B) I will make the link public or share it another way.
  - C) Skip the prototype: the written design rules in #3 (colors, fonts, layout, the 6 fixes) are enough, and I will give feedback on the first built version.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation (**delegated default**, effectively option C): the prototype still cannot be read, so the closest workable choice is to build from the written design rules in the plan (SRC-2 §9: tokens, type, layout, images, the 6 fixes) and the TL design comment. The prototype link stays in the requirements as a reference; if it becomes readable (or the stakeholder exports it), it is used for visual review, and where it disagrees with the TL design comment the comment still wins (BR-06). Consequences: visual review is against the written rules, not prototype boards; placeholder copy is sample text with the marker in front (FR-10), not the prototype's copy; the prototype's SVG illustrations are not available, so placeholder images are simple marked placeholders (their look is the Team Lead's call). The stakeholder sees the look for the first time on the built page and may give feedback then (as in SRC-3 PO answers Q4).

### Q-05: Is your real content ready?
- **Question:** Do you already have the real content: headline, short bio, portrait photo, projects, skills, email address, GitHub and LinkedIn links?
- **Why it matters:** If it is ready, we can build with real content and skip most of the placeholder work. If not, everything is built with clearly marked placeholders that must all be replaced before launch.
- **Related:** G-04, A-04, FR-10, FR-11, R-03
- **Options:**
  - A) Yes, all of it; I will send it now.
  - B) Part of it (please say which parts); the rest comes later.
  - C) Not yet; build with marked placeholders and I will send it before launch.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option C**, as stated in the plan (SRC-2 §6 "The PO provides real content before M3", §7, §16; TL decisions "Content ETA: not a dependency. We build everything with placeholders"; SRC-3 PO answers Q3). Everything except the name "Huy Pham" is built with marked placeholders; real content is a stakeholder-owned dependency for step 3 (launch) only. A-04 becomes a decision. No content is invented.

### Q-06: What does each project card show?
- **Question:** What should each project card in the Projects section show?
- **Why it matters:** It defines the content you need to supply for every project and what visitors see. The plan only names a picture and "Live demo" / "Source" links.
- **Related:** G-05, A-03, FR-04
- **Options:**
  - A) Picture, title, short description, technology tags, "Live demo" and "Source" links; a link is hidden when a project does not have it.
  - B) Same as A, but without technology tags.
  - C) Same as A, plus my role and year for each project.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A**. The plan states the 16:9 thumbnail and the "Live demo" / "Source" links (SRC-2 §9, §9 fix 4); the TL design comment includes a `Tag` element and a tag style (TL design §1 Layout "999 (tags)", §2 Components), which supports technology tags; title and short description are the minimum to identify a project. Option C (role, year) would add beyond the plan and is not taken. **Delegated default:** "a link is hidden when a project does not have it" is not in the plan; it is the simplest behavior and the stakeholder may change it. A-03 becomes a decision.

### Q-07: How should skills be shown?
- **Question:** How should the Skills section present your skills?
- **Why it matters:** It decides the content format you supply and how the section looks. The plan only says "skill list".
- **Related:** G-06, FR-05
- **Options:**
  - A) One simple list of skill names (for example small labels side by side).
  - B) Skills grouped by category (for example Frontend, Backend, Tools), each group a list of names.
  - C) Skills with a level (for example beginner / advanced or years of experience).
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A**, one simple list of skill names. The plan says "Skill list" (SRC-2 §12 T5) and the design has chips (SRC-2 §9 `--surface` "chips"; TL design §2 `Chip`). Grouping and levels add beyond the plan. **Delegated default** (the plan does not explicitly rule out grouping); the stakeholder may change it.

### Q-08: What is in the About section?
- **Question:** Besides your name, headline and short bio, what should the About section show?
- **Why it matters:** The plan mentions a square portrait and the design has a "primary button", but the exact contents were in the prototype we cannot read.
- **Related:** G-07, FR-03
- **Options:**
  - A) A portrait photo and two buttons: "View projects" and "Contact me" (jump to those sections).
  - B) A portrait photo, no buttons.
  - C) No photo and no buttons; text only.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option B**, name, headline, short bio and a square portrait, no buttons. The portrait is stated in the plan (SRC-2 §9 Images "portrait 1:1 at 220px"; TL design §6). The plan does not say what the About section's buttons would be or say; the header already links to Projects and Contact (FR-02), so buttons would add beyond the written plan. **Delegated default**; if the prototype becomes readable and shows buttons, or the stakeholder wants them, this can change.

### Q-09: How many projects?
- **Question:** About how many projects should the page show at launch?
- **Why it matters:** The plan only says "at least 1". The number affects layout checks and the content you need to prepare.
- **Related:** G-08, FR-04
- **Options:**
  - A) 1 to 3
  - B) 4 to 6
  - C) More than 6
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A, 1 to 3 projects**. The plan only requires "at least 1 card" (SRC-2 §12 T4); 1 to 3 is the smallest range that meets it. **Delegated default**; the actual number at launch comes from the stakeholder's real content.

### Q-10: Who checks on real phones?
- **Question:** Before launch the plan requires a check on a real iPhone (Safari) and a real Android phone (Chrome). Who does it?
- **Why it matters:** The team works with emulators; real devices catch issues emulators miss. Someone needs the phones and the public URL.
- **Related:** G-09, NFR-10, R-05
- **Options:**
  - A) I will do it myself on my phones when the public URL is ready.
  - B) The team should arrange it (please say which devices are available).
  - C) Skip it for v1; emulator checks are enough.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A**. The check itself stays, as the plan requires it on the public URL (SRC-2 §11 M2, §14 "Real devices"), so option C is not taken. The plan does not say who has the phones; the team has no real devices, and the stakeholder is accountable for launch sign-off (SRC-2 §3 RACI), so the closest workable choice is that the stakeholder runs the check on his own iOS Safari and Android Chrome phones once the public URL exists, and the team does everything else with emulators. **Delegated default**; the stakeholder may name someone else.

### Q-11: Any extra features?
- **Question:** None of the sources mention visitor analytics, a downloadable CV/resume, or a blog. Should any of these be in v1?
- **Why it matters:** We assume none of them are in v1. Analytics in particular may add a third-party service and a privacy notice.
- **Related:** G-10, A-06, Scope
- **Options:**
  - A) None of them in v1.
  - B) A downloadable CV (PDF) link.
  - C) Simple visitor analytics (please say which service, if any).
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A, none of them in v1**. The plan's scope (SRC-2 §4) does not include them, and adding them would be new scope. A-06 becomes a decision (out of scope for v1).

### Q-12: What goes in the footer?
- **Question:** What should the page footer show?
- **Why it matters:** The only footer text in the plan is a credit ("Built with Next.js", later "...and deployed on Vercel"), which depends on Q-02.
- **Related:** AMB-02, FR-15, C-01
- **Options:**
  - A) Only the credit line, as in the plan (adjusted to the chosen host).
  - B) Copyright line "© <year> Huy Pham" plus the credit line.
  - C) Copyright line only, no credit.
  - D) Other (please describe)
- **Answer (original):** bạn tự chốt hết đi, tôi sẽ update sau nếu cần, bám sát plan tôi gửi nhất có thể
- **Answer (English):** You decide all of them yourself; I will update later if needed. Stick as closely as possible to the plan I sent.
- **Status:** confirmed
- **BA note:** Decided under the stakeholder's delegation: **option A**, only the credit line as in the plan: "Built with Next.js" until the public Vercel deployment exists, then "Built with Next.js and deployed on Vercel" (SRC-2 §12 T1b; TL design §7). With Q-02 = Vercel, no adjustment is needed. AMB-02 resolved.
