# S-15: Check the public page on real phones

- **Priority:** P1
- **Step:** 2 (public URL), exit check
- **Covers:** NFR-10, NFR-01, NFR-02 · **Decisions:** Q-10 (DD-06)
- **Depends on stories:** S-14

## User story
As the owner, I want to check the public page on my own iPhone and Android phone, so that
problems that only show on real devices are found before launch.

## Acceptance criteria
1. **iPhone (iOS Safari) check passes**
   - Given the public URL (S-14)
   - When the owner opens it in Safari on his iPhone, in portrait and landscape
   - Then all four sections show with no horizontal scroll or clipped text, header links land on the section headings, the theme toggle works, and the email, GitHub and LinkedIn links open
2. **Android (Chrome) check passes**
   - Given the public URL (S-14)
   - When the owner opens it in Chrome on his Android phone, in portrait and landscape
   - Then the same checks as AC 1 pass
3. **Problems are fixed before step 2 is done**
   - Given the owner reports a problem from either phone
   - When the team has fixed it
   - Then the owner repeats the affected check, and step 2 is done only when both phones pass

## Out of scope
- Other devices and browsers (covered by emulation in S-13).

## Notes
- The owner runs this check himself (DD-06); the team supplies the checklist from AC 1.
- How the user reaches it: the public URL from S-14.
