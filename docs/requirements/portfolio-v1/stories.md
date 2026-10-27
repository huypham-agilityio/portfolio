# Stories: Personal portfolio web page v1

- Slug: `portfolio-v1` · PRD: `prd.md` · Requirements: `requirements.md` (signed off 2026-10-27 by Huy Pham)
- Priority encodes the plan's three steps: **P0 = step 1 (local v1)**, **P1 = step 2 (public URL)**,
  **P2 = step 3 (launch)**. Each step ends with an exit-check story (S-13, S-15, S-18).
- Every story that shows something on screen also meets the **shared quality bar** in `prd.md` §5
  (design rules, keyboard and focus, landmarks, both themes at WCAG 2.1 AA, no horizontal scroll
  at 320–1280 px, 0 serious/critical automated accessibility issues, image hygiene). It is a
  common Definition of Done, not counted as ACs.
- Written fresh from the signed requirements; the old repository's T1a…T9 list and tickets are
  not reused (SRC-1). Technical tasks are the Team Lead's job.

## Stories
| ID | Title | Step | Priority | ACs | Covers | Depends on |
|---|---|---|---|---|---|---|
| S-01 | See the page with its four sections | 1 | P0 | 5 | FR-01, FR-15, NFR-02, NFR-04 | none |
| S-02 | Jump to a section from the header | 1 | P0 | 5 | FR-02, NFR-03 | S-01 |
| S-03 | Page follows the device theme | 1 | P0 | 5 | FR-07, NFR-03 | S-01 |
| S-04 | Switch and keep the theme | 1 | P0 | 5 | FR-07, NFR-03 | S-03 |
| S-05 | Read the About section | 1 | P0 | 4 | FR-03, FR-10, NFR-06 | S-01 |
| S-06 | Browse project cards | 1 | P0 | 5 | FR-04, FR-10, NFR-06, NFR-08 | S-01 |
| S-07 | Hide project links a project does not have | 1 | P0 | 3 | FR-04 | S-06 |
| S-08 | See the skills list | 1 | P0 | 4 | FR-05, FR-10 | S-01 |
| S-09 | Contact the owner | 1 | P0 | 5 | FR-06, FR-10, NFR-05, NFR-08 | S-01 |
| S-10 | Recognize the page in the browser tab and search results | 1 | P0 | 3 | FR-09, FR-10 | S-01 |
| S-11 | Find the way back from a wrong address | 1 | P0 | 4 | FR-08 | S-03 |
| S-12 | Skip straight to the content with the keyboard | 1 | P0 | 3 | FR-14, NFR-03 | S-02 |
| S-13 | Accept the local v1 | 1 (exit) | P0 | 5 | NFR-01, NFR-02, NFR-03, NFR-07 | S-01 … S-12 |
| S-14 | Open the page from one public link | 2 | P1 | 4 | FR-13, FR-15, NFR-05 | S-13, Vercel account |
| S-15 | Check the public page on real phones | 2 (exit) | P1 | 3 | NFR-10, NFR-01, NFR-02 | S-14 |
| S-16 | Show the owner's real profile and contact details | 3 | P2 | 4 | FR-11, FR-03, FR-06, FR-09 | S-05, S-09, S-10, real content |
| S-17 | Show the owner's real projects and skills | 3 | P2 | 4 | FR-11, FR-04, FR-05, NFR-06 | S-06, S-07, S-08, real content |
| S-18 | Pass the placeholder audit and launch | 3 (exit) | P2 | 5 | FR-12, FR-10 | S-14, S-16, S-17 |

## How each screen is reached
| Screen / area | Way in | Provided by |
|---|---|---|
| Home page (all sections) | Opening the home address `/` (the shared link) | S-01; public link S-14 |
| About, Projects, Skills, Contact | Scrolling the home page or the header links | S-01, S-02 |
| Theme toggle | Header of the home page | S-04 |
| 404 page | Opening any unknown address; links back to `/` | S-11 |
| Skip link | First Tab on the home page | S-12 |

## FR → Story traceability
| FR | Stories |
|---|---|
| FR-01 | S-01 |
| FR-02 | S-02 |
| FR-03 | S-05, S-16 |
| FR-04 | S-06, S-07, S-17 |
| FR-05 | S-08, S-17 |
| FR-06 | S-09, S-16 |
| FR-07 | S-03, S-04 |
| FR-08 | S-11 |
| FR-09 | S-10, S-16 |
| FR-10 | S-05, S-06, S-08, S-09, S-10, S-18 |
| FR-11 | S-16, S-17 |
| FR-12 | S-18 |
| FR-13 | S-14 |
| FR-14 | S-12 |
| FR-15 | S-01, S-14 |

All 15 in-scope FRs are covered; no empty cells.

## NFR → Story traceability
| NFR | Stories |
|---|---|
| NFR-01 | S-13, S-15 |
| NFR-02 | S-01, S-13, S-15 (and the shared quality bar) |
| NFR-03 | S-02, S-03, S-04, S-12, S-13 (and the shared quality bar) |
| NFR-04 | S-01 |
| NFR-05 | S-09, S-14 |
| NFR-06 | S-05, S-06, S-17 (and the shared quality bar) |
| NFR-07 | S-13 |
| NFR-08 | S-06, S-09 |
| NFR-09 | shared quality bar (every UI story) |
| NFR-10 | S-15 |

## Size self-check
Limit: `limits.story_max_ac` = 5.

| Story | ACs | ≤ limit? | Split pattern used |
|---|---|---|---|
| S-01 | 5 | yes | simple version first (page frame before section content) |
| S-02 | 5 | yes | by workflow (navigation separate from page frame and theme) |
| S-03 | 5 | yes | simple version first (system theme before manual toggle) |
| S-04 | 5 | yes | by workflow (manual choice, persistence, storage-blocked edge case) |
| S-05 | 4 | yes | by data type (one section per story) |
| S-06 | 5 | yes | by data type; happy path first |
| S-07 | 3 | yes | by business rule (BR-07 split from S-06) |
| S-08 | 4 | yes | by data type |
| S-09 | 5 | yes | by data type |
| S-10 | 3 | yes | by data type (page metadata) |
| S-11 | 4 | yes | by workflow (error path: unknown address) |
| S-12 | 3 | yes | by user role (keyboard user) |
| S-13 | 5 | yes | by workflow (step 1 exit check) |
| S-14 | 4 | yes | by channel (public URL) |
| S-15 | 3 | yes | by channel (real devices), split from S-14 |
| S-16 | 4 | yes | by data type (profile and contact content) |
| S-17 | 4 | yes | by data type (projects and skills content), split from S-16 |
| S-18 | 5 | yes | by workflow (step 3 exit check) |

Every story has at most 5 Given/When/Then ACs. No story is expected to need more than
`limits.story_max_tasks` (5) tasks; the Team Lead returns any that does.
