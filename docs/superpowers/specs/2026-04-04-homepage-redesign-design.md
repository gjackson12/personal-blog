# Homepage Redesign — Design Spec

**Date:** 2026-04-04  
**Blog:** Eventual Consistency  
**Status:** Approved

---

## Goal

Replace the default Astro starter placeholder homepage with a custom page that makes a first-time visitor immediately understand what the blog is about and want to read it (thesis-first).

## Design Decisions

| Decision | Choice | Rationale |
|---|---|---|
| Primary goal | Thesis-first | Visitor should understand the blog in 30 seconds, not feel like they know the author |
| Structure | Intro + recent posts | Strong intro above fold, recent posts below |
| Intro length | Expanded | Use existing site description + 1–2 sentences about AI, craft, and leadership |
| Personal attribution | None | No byline or About link on the homepage |
| Layout | Bold Statement Opener | Punchy hook, then expanded description, then posts |

## Page Structure

### 1. Header (unchanged)
The existing `<Header />` component — logo SVG top-left, nav links centered, social icons right. No changes.

### 2. Hero Section
- **Topic tags:** `Software Engineering · AI · Leadership` in teal (`--accent`), small-caps, spaced lettering
- **H1 hook:** "The craft is changing. Here's my honest take." — large, bold, two lines
- **Description paragraph:** Expand the current `SITE_DESCRIPTION` in `src/consts.ts` to include a sentence about what topics the blog covers (AI, rethinking craft, leadership in flux)

### 3. Divider
A single `<hr>` using the existing `border-top: 1px solid rgb(var(--gray-light))` style.

### 4. Recent Writing Section
- **Section label:** "Recent Writing" in small-caps, gray, spaced lettering
- **Post cards:** One per published post, each with:
  - Teal left-border accent (`border-left: 3px solid var(--accent)`)
  - Post title (bold, dark)
  - Publication date (small, teal)
  - Excerpt — the post's `description` field from frontmatter
  - "Read more →" link in teal
- Posts sourced dynamically from the blog content collection, sorted by `pubDate` descending, no hard limit (show all posts — the blog is new)

### 5. Footer (unchanged)
The existing `<Footer />` component. No changes.

## Files Changed

| File | Change |
|---|---|
| `src/pages/index.astro` | Full rewrite — remove Astro starter content, implement new layout |
| `src/consts.ts` | Expand `SITE_DESCRIPTION` by 1–2 sentences covering AI, craft, and leadership topics |

## Files NOT Changed

- `src/components/Header.astro` — untouched
- `src/components/Footer.astro` — untouched
- `src/styles/global.css` — untouched (existing CSS variables used throughout)
- All blog content files — untouched

## Styling Notes

- Use existing CSS variables: `--accent` (#3d9b8a), `--gray`, `--gray-light`, `--black`, `--gray-dark`
- Font: Atkinson (already loaded globally)
- Max content width: 720px, centered — matches existing `main` styles
- No new CSS files — scoped `<style>` in `index.astro` only if needed
