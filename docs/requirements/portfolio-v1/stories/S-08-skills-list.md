# S-08: See the skills list

- **Priority:** P0
- **Step:** 1 (local v1)
- **Covers:** FR-05, FR-10 · **Decisions:** Q-05, Q-07 (DD-03)
- **Depends on stories:** S-01

## User story
As a visitor, I want to see the owner's skills at a glance, so that I can tell quickly whether
they match what I need.

## Acceptance criteria
1. **Skills as one simple list**
   - Given the visitor is on the home page
   - When they look at the Skills section
   - Then they see the skill names as small labels side by side, in one list, with no groups and no levels
2. **Labels wrap on small screens**
   - Given a screen 320 px wide
   - When the Skills section is shown
   - Then the labels wrap onto new lines with no horizontal scroll and no clipped label
3. **Read as a list by assistive technology**
   - Given a screen reader user reaches the Skills section
   - When it is read out
   - Then the skills are announced as a list with the number of items
4. **Placeholders are marked**
   - Given real content has not arrived yet
   - When the Skills section is shown
   - Then each skill name carries `[PLACEHOLDER]` in front

## Out of scope
- Real skills (S-17).
- Skill grouping or levels (out of v1, Q-07).

## Notes
- How the user reaches it: scroll the home page (S-01) or the "Skills" header link (S-02).
- Shared quality bar (prd.md §5) applies.
