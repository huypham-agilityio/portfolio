# S-07: Hide project links a project does not have

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-04 · **Decisions:** Q-06 (DD-02)
- **Depends on stories:** S-06

## User story
As a visitor, I want a project card to show only the links that really exist, so that I never
click a link that leads nowhere.

## Acceptance criteria
1. **No live demo**
   - Given a project that has a source link but no live demo
   - When its card is shown
   - Then the card shows "Source" and no "Live demo" link
2. **No source**
   - Given a project that has a live demo but no source link
   - When its card is shown
   - Then the card shows "Live demo" and no "Source" link
3. **No links at all**
   - Given a project that has neither link
   - When its card is shown
   - Then the card shows its thumbnail, title, description and tags with no links and no empty gap or broken layout

## Out of scope
- The card itself (S-06).

## Notes
- Business rule BR-07 (delegated default DD-02; the stakeholder may change it).
- How the user reaches it: the Projects section (S-06).
- In step 1 this can be shown with placeholder projects that omit a link.
