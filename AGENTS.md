# AGENTS.md

## Project Overview

`S2P2/s2p2blog` is a personal technical blog built with Astro.

The site is content-first: Markdown posts, simple pages, and a small number of reusable Astro components.

## Stack

- Astro
- MDX (`@astrojs/mdx`)
- RSS feed (`@astrojs/rss`)
- Sitemap (`@astrojs/sitemap`)
- `sharp` for image handling
- Node `>=22.12.0`

## Repository Structure

- `src/pages/` — routes and top-level pages
  - `index.astro` — homepage
  - `about.astro` — about page
  - `rss.xml.js` — RSS feed
  - `blog/` — blog routes
- `src/content/blog/` — blog posts in Markdown/MDX
- `src/layouts/` — shared layouts for posts/pages
- `src/components/` — reusable UI pieces
- `src/styles/global.css` — global styling
- `public/` — static assets

## Content Rules

- Prefer Markdown for posts and simple content.
- Use Astro components only when a page needs structure, reuse, or interactivity.
- Keep edits semantically clean and accessible.
- Avoid adding dependencies unless they solve a clear problem.

### Blog frontmatter

Blog posts are validated by `src/content.config.ts` and should include:

- `title` — required
- `description` — required
- `pubDate` — required
- `updatedDate` — optional
- `heroImage` — optional

### Blog image naming

- Keep post-specific images next to the post file in `src/content/blog/`.
- Use the same slug as the post file name.
- Prefer the suffix `-hero` for post banner images.

Example:

- `create-personal-blog-astro-github-cloudflare.md`
- `create-personal-blog-astro-github-cloudflare-hero.png`

## Site Conventions

- `src/consts.ts` defines the shared site title and description.
- Keep the homepage section list aligned with actual site routes.
- Keep `BlogPost.astro` and `global.css` in sync when changing blog typography or layout.
- Preserve the RSS feed and sitemap behavior when adding or renaming content.

## Editing Guidelines

- Make the smallest change that solves the problem.
- Prefer existing patterns over new abstractions.
- Keep copy lean and direct.
- Use clear, descriptive filenames for new posts or pages.
- When updating a post, preserve Markdown readability.
- Do not push directly to `main`.
- Always create a new branch for changes, even small ones.
- Open a pull request for review and merge through GitHub instead of committing straight to `main`.

## GitHub Branch Policy

`main` should be treated as a protected branch.

GitHub should be configured so that:
- direct pushes to `main` are blocked
- changes must arrive through pull requests
- branch deletion / force-push permissions stay restricted

If GitHub branch protection is not yet enabled, treat this as a required repo setup task before future changes land.

## Verification

Before finishing changes, run the appropriate checks:

```sh
npm run build
```

If you change routing, page structure, or content collections, also verify the affected pages in the browser or with a local dev server:

```sh
npm run dev
```

## Practical Notes

- The site currently uses a simple personal-blog structure, so changes should stay lightweight.
- If a page still contains placeholder text or demo content, treat that as content to replace rather than as a style reference.
- If you add a new blog post, make sure it is discoverable through the blog listing and RSS output.

## For Agents and Humans

- Read this file before making changes.
- Keep the repo easy to maintain for one person.
- Favor readable content and straightforward structure over clever implementation.
