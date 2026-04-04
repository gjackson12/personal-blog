# Homepage Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the Astro starter placeholder homepage with a thesis-first layout featuring a bold hook, expanded description, and a recent posts list.

**Architecture:** Two file changes only — expand `SITE_DESCRIPTION` in `src/consts.ts`, then rewrite `src/pages/index.astro` to render the hero + posts layout using the existing content collection API and components.

**Tech Stack:** Astro 6, `astro:content` getCollection API, existing CSS variables, Atkinson font

---

## File Map

| File | Change |
|---|---|
| `src/consts.ts` | Modify — expand `SITE_DESCRIPTION` |
| `src/pages/index.astro` | Full rewrite — new homepage layout |

---

### Task 1: Expand SITE_DESCRIPTION

**Files:**
- Modify: `src/consts.ts`

- [ ] **Step 1: Update SITE_DESCRIPTION**

Open `src/consts.ts` and replace its contents with:

```ts
// Place any global data in this file.
// You can import this data from anywhere in your site by using the `import` keyword.

export const SITE_TITLE = 'Eventual Consistency';
export const SITE_DESCRIPTION =
	"In distributed systems, eventual consistency means the data gets there — just not all at once. That's also how careers work. This is one engineer's honest account of adapting to AI, rethinking what it means to write good software, and figuring out what leadership looks like when the ground keeps shifting.";
```

- [ ] **Step 2: Verify dev server still starts**

```bash
npm run dev
```

Expected: server starts at `http://localhost:4321` with no errors.

- [ ] **Step 3: Commit**

```bash
git add src/consts.ts
git commit -m "content: expand site description with AI/craft/leadership topics"
```

---

### Task 2: Rewrite index.astro

**Files:**
- Modify: `src/pages/index.astro`

- [ ] **Step 1: Replace index.astro with the new layout**

Overwrite `src/pages/index.astro` with:

```astro
---
import { getCollection } from 'astro:content';
import BaseHead from '../components/BaseHead.astro';
import Footer from '../components/Footer.astro';
import FormattedDate from '../components/FormattedDate.astro';
import Header from '../components/Header.astro';
import { SITE_DESCRIPTION, SITE_TITLE } from '../consts';

const posts = (await getCollection('blog')).sort(
	(a, b) => b.data.pubDate.valueOf() - a.data.pubDate.valueOf(),
);
---

<!doctype html>
<html lang="en">
	<head>
		<BaseHead title={SITE_TITLE} description={SITE_DESCRIPTION} />
	</head>
	<body>
		<Header />
		<main>
			<section class="hero">
				<p class="topics">Software Engineering · AI · Leadership</p>
				<h1>The craft is changing.<br />Here's my honest take.</h1>
				<p class="description">{SITE_DESCRIPTION}</p>
			</section>
			<hr />
			<section class="posts">
				<p class="section-label">Recent Writing</p>
				{
					posts.map((post) => (
						<article>
							<a href={`/blog/${post.id}/`}>
								<h2>{post.data.title}</h2>
							</a>
							<p class="date">
								<FormattedDate date={post.data.pubDate} />
							</p>
							<p class="excerpt">{post.data.description}</p>
							<a href={`/blog/${post.id}/`} class="read-more">
								Read more →
							</a>
						</article>
					))
				}
			</section>
		</main>
		<Footer />
	</body>
</html>

<style>
	.hero {
		margin-bottom: 2rem;
	}
	.topics {
		font-size: 0.75rem;
		color: var(--accent);
		text-transform: uppercase;
		letter-spacing: 0.15em;
		margin-bottom: 1rem;
	}
	h1 {
		margin-bottom: 1.25rem;
	}
	.description {
		color: rgb(var(--gray-dark));
		line-height: 1.8;
		margin: 0;
	}
	.section-label {
		font-size: 0.65rem;
		color: rgb(var(--gray));
		text-transform: uppercase;
		letter-spacing: 0.1em;
		margin-bottom: 1.5rem;
	}
	article {
		border-left: 3px solid var(--accent);
		padding: 0.25rem 0 0.25rem 1.25rem;
		margin-bottom: 2rem;
	}
	article h2 {
		font-size: 1.25rem;
		margin-bottom: 0.25rem;
	}
	article h2 a {
		text-decoration: none;
		color: rgb(var(--black));
	}
	article h2 a:hover {
		color: var(--accent);
	}
	.date {
		font-size: 0.75rem;
		color: var(--accent);
		margin: 0 0 0.5rem;
	}
	.excerpt {
		font-size: 0.9rem;
		color: rgb(var(--gray));
		line-height: 1.7;
		margin-bottom: 0.5rem;
	}
	.read-more {
		font-size: 0.85rem;
		color: var(--accent);
		text-decoration: none;
	}
	.read-more:hover {
		text-decoration: underline;
	}
</style>
```

- [ ] **Step 2: Verify in browser**

With `npm run dev` running, open `http://localhost:4321`.

Expected:
- Topic tags appear in teal small-caps: "Software Engineering · AI · Leadership"
- H1 reads "The craft is changing. Here's my honest take."
- Description paragraph appears below
- Horizontal rule divides hero from posts
- "Recent Writing" label appears in small gray caps
- "A New World" post appears with teal left border, date, description excerpt, and "Read more →" link
- Clicking title or "Read more →" navigates to the post

- [ ] **Step 3: Commit**

```bash
git add src/pages/index.astro
git commit -m "feat: redesign homepage with thesis-first hero and recent posts"
```
