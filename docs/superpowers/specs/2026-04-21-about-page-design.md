# About Page Design

**Date:** 2026-04-21
**Status:** Approved

## Overview

Replace the placeholder About page with a thesis-first personal page that serves both intellectual peers (engineers and practitioners) and professional contacts (employers, recruiters, collaborators).

## Approach

**Thesis-first layout.** Opens with a sharp POV blockquote, earns it with credentials and context, ends with a personal note. Matches the homepage's "honest take" voice rather than reading like a resume or profile page.

## Content

### Opening label
Small caps label: `About` — styled with the site's teal accent (`#3d9b8a`), uppercase, letter-spaced. Consistent with the homepage's `Software Engineering · AI · Leadership` topic label.

### Thesis blockquote
Rendered using the site's existing `blockquote` style (4px teal left border, 1.333em font size):

> "The software engineering world is shifting — some of it is genuine, material change. Some of it is hype. Telling the difference is the hard part."

### Bio paragraphs (3)

1. **Who Graham is:** Senior Engineering Manager and tech lead at a Fortune 500 company, nearly 20 years in software, building systems and leading teams under uncertainty.

2. **Why the blog exists + topic areas:** Thinks out loud about what's actually changing vs. what isn't. Three topics: AI's real impact on software development, the craft of engineering (building things well), engineering leadership as the ground shifts.

3. **Closing voice line:** "I'm not here to sell optimism or pessimism. Just honest takes from someone in the middle of it."

### Personal note
Separated from the bio by a `<hr>`. Styled in muted gray (`rgb(96, 115, 159)`), slightly smaller text (`0.9em`):

> When he's not thinking about AI and engineering, Graham is watching hockey or being supervised by two Labrador Retrievers.

### Social links
LinkedIn (`https://www.linkedin.com/in/gjackson2013`) and GitHub (`https://github.com/gjackson12`) as teal text links, inline, below the personal note.

## Layout & Styling

- Uses the existing `BlogPost.astro` layout (or a new custom layout — see Implementation Notes)
- Removes the `heroImage` and `pubDate` fields — they don't apply to an About page
- No hero image — the page leads with text
- All colors, fonts, and spacing match `global.css`: Atkinson font, teal accent, gray-dark body text, gray-light `<hr>`

## Implementation Notes

The current `about.astro` uses `BlogPost.astro` as its layout, which renders a hero image, a publication date, and a centered title block. These are blog-post conventions that don't belong on an About page. Two options:

1. **Reuse `BlogPost.astro`** with the hero image omitted and date hidden — simpler but slightly awkward structurally.
2. **Write `about.astro` as a standalone page** using `BaseHead`, `Header`, and `Footer` directly — clean, no layout hacks needed. Recommended.

Recommended option 2: standalone page, mirroring `index.astro`'s structure.

## Out of Scope

- A contact form
- A photo/headshot
- A resume download
- Dark mode
