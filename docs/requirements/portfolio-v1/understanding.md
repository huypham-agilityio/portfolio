# How I understand it: Personal portfolio web app (v1)

Round 2, 2026-10-27. You asked us to decide every open question ourselves and to stay as close
as possible to your plan. I did that; every decision is listed below so you can change any of
them before you sign off.

## What we are building
One public web page in English about you, Huy Pham, that you can share as a single link. It has
four sections:
- **About:** your name, a headline, a short bio and a square photo. No buttons.
- **Projects:** 1 to 3 cards. Each card has a picture, the project title, a short description,
  technology tags, and "Live demo" / "Source" links. If a project has no demo or no public
  source, that link is simply not shown. The card itself is not clickable.
- **Skills:** one simple list of skill names shown as small labels side by side.
- **Contact:** your email shown as text and as a clickable link, plus GitHub and LinkedIn links
  that open in a new tab. No contact form.

A header shows your name, links to the four sections and a light/dark switch. On the first visit
the page follows the visitor's phone or computer setting; once they flip the switch, the page
remembers it. There is a simple "page not found" page with a link home, a page title,
description and small icon for the browser tab, and a footer with one line: "Built with Next.js"
(later "Built with Next.js and deployed on Vercel").

It must work on phones from 320px wide up to large screens, in current Chrome, Safari and
Firefox (and phone Safari/Chrome), be usable with a keyboard and screen reader, and have good
contrast in both themes. No server: the page is plain files. No analytics, CV download or blog.

## How far we go (three steps, as in your plan)
1. **Local version:** the complete page on clearly marked placeholders, checked on our side.
2. **Public URL:** the page on a free Vercel address. This needs your Vercel account.
3. **Launch:** your real content replaces every placeholder, a search confirms none is left, and
   the public page is checked again. This needs your real content.

## Placeholders
Until your real content arrives, every made-up text, link and picture is marked `[PLACEHOLDER]`.
Your name is real and is not marked. Before launch, a search for the marker must find nothing.

## Not in v1 (phase 2)
Experience and Education sections, contact form, Vietnamese version, custom domain, social-media
preview cards, a formal speed budget, and automatically blocking a launch while placeholders
remain.

## Decisions we made for you (please check; you can change any of them)
Taken straight from your plan:
1. The old plan, your #2 decisions and the TeamLead's design rules carry over unchanged (Q-01).
2. Hosting is Vercel with its free default address (Q-02). The deployment is its own later step,
   as in the plan; our project settings stay "no deployment" until then.
3. We go all three steps: local, public URL, launch (Q-03).
4. Your real content is not needed yet; we build with placeholders and you send it before launch (Q-05).
5. Project cards: picture, title, short description, tags, "Live demo" and "Source" links (Q-06).
6. No analytics, CV download or blog in v1 (Q-11).
7. Footer shows only the credit line from the plan (Q-12).

Our own choices, because the plan does not say (simplest option, nothing extra added):
8. **Design:** we cannot open the prototype link, so we build from the written design rules
   (colors, fonts, layout and the 6 fixes). You see the look for the first time on the built
   page. Placeholder texts are sample texts and placeholder pictures are simple marked images,
   not the prototype's. If you can share the prototype later, we will use it (Q-04).
9. **Missing project links:** if a project has no demo or no public source, the link is hidden (Q-06).
10. **Skills:** one flat list, no groups, no levels (Q-07).
11. **About:** photo, no buttons (Q-08).
12. **Number of projects:** 1 to 3 (Q-09).
13. **Real-phone check:** you check the public page on your own iPhone (Safari) and Android phone
    (Chrome) before launch; we use emulators for everything else (Q-10).

## What you still need to provide (not decisions, just inputs)
- Before step 2: which Vercel account hosts the page.
- Before step 3: headline, bio, photo, projects, skills, email address, GitHub and LinkedIn links.

## Still assumed (small)
- "Last 2 versions" applies to all five browsers, including phone Safari and Chrome.
