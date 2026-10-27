# S-18: Pass the placeholder audit and launch

- **Priority:** P2
- **Step:** 3 (launch), exit check
- **Covers:** FR-12, FR-10 · **Decisions:** Q-03
- **Depends on stories:** S-14, S-16, S-17

## User story
As the owner, I want a final check that no placeholder is left anywhere, so that I can launch
the page knowing visitors will never see fake content.

## Acceptance criteria
1. **No marker in the source content**
   - Given all real content is in place (S-16, S-17)
   - When the source is searched case-insensitively for `[PLACEHOLDER]` and `%5BPLACEHOLDER%5D`
   - Then nothing is found
2. **No marker in the built pages**
   - Given the built pages that are published
   - When their HTML is searched case-insensitively for `[PLACEHOLDER]` and `%5BPLACEHOLDER%5D`
   - Then nothing is found, including in the page title, meta description, alt text and link targets
3. **No placeholder images**
   - Given the published image files
   - When their file names are checked
   - Then no file name contains `placeholder` or the `[PLACEHOLDER]` marker
4. **Re-check on the public URL**
   - Given the real-content version is live on the public URL
   - When the step 1 acceptance checks (S-13) are repeated there
   - Then they all pass and no placeholder text, link or image is visible
5. **Launch sign-off**
   - Given ACs 1 to 4 pass and are recorded in a manual checklist
   - When the owner reviews the checklist
   - Then he can sign off the launch; if any item fails, launch is not signed off until it is fixed and re-checked

## Out of scope
- An automated block on deploying while placeholders remain (phase 2).

## Notes
- BR-01: no placeholder content may ship at launch. R-04 (placeholder leak) is the main risk this story mitigates.
- AC 3 applies the FR-10 rule that placeholder image file names include `placeholder`.
- A manual checklist is enough for v1 (FR-12).
