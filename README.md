# Eventual Consistency

My personal blog. I write about AI and what it's actually doing to software development, engineering craft, and leadership when the ground won't stop moving. No clean answers. Just the work.

Built with [Astro](https://astro.build), deployed on Vercel.

## Commands

Run from the project root:

| Command             | Action                                      |
| :------------------ | :------------------------------------------ |
| `npm install`       | Install dependencies                        |
| `npm run dev`       | Start local dev server at `localhost:4321`  |
| `npm run build`     | Build for production to `./dist/`           |
| `npm run preview`   | Preview the production build locally        |

## Writing a Post

Add a `.md` or `.mdx` file to `src/content/blog/`. The frontmatter schema:

```md
---
title: 'Post title'
description: 'One or two sentences. This shows up in SEO and the post list.'
pubDate: 'Mon DD YYYY'
---
```

## Deploying

Pushing to `master` triggers a Vercel deployment automatically. Run `npm run build` first if you want to sanity-check the build locally before pushing.

## Project Structure

```
src/
  content/blog/   ← posts go here
  pages/          ← index, about, rss, etc.
  components/     ← shared layout pieces
  layouts/        ← page wrappers
public/           ← static assets
```
