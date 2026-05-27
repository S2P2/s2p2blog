---
title: 'How I Built This Blog with Astro, GitHub, and Cloudflare Pages'
description: 'A practical walkthrough for creating a personal technical blog using Astro, GitHub, and Cloudflare Pages.'
pubDate: 2026-05-25
heroImage: './create-personal-blog-astro-github-cloudflare-thumbnail.png'
---

I wanted a personal blog that was more flexible than a hosted writing platform. The main requirement was simple: most posts should be easy to write in Markdown, but the site should still leave room for custom pages, JavaScript experiments, notebooks, and future interactive work.

The stack I chose is:

- **Astro** for the site framework
- **GitHub** for source control
- **Cloudflare Pages** for hosting and automatic deployment

This post documents the basic setup.

## Why Astro

Astro is a good fit for a technical personal blog because it starts from content. Markdown is treated as a first-class format, while `.astro` pages and components give enough flexibility for custom layouts and interactive sections.

For this blog, Astro gives me a clean path for:

- Markdown posts
- custom HTML pages
- JavaScript snippets
- future MDX components
- future notebook embeds
- static output that is easy to host

The important part is that Astro can stay simple at the beginning. I do not need to design the full system before publishing the first post.

## Step 1: Create the Astro project

I started with the Astro blog template:

```bash
npm create astro@latest s2p2blog
cd s2p2blog
npm run dev
```

The blog template creates the basic structure for posts, layouts, and routes. That means I can begin by editing existing files instead of building the whole blog structure from scratch.

## Step 2: Create a GitHub repository

The repository is named:

```text
s2p2blog
```

After creating the repository on GitHub, I connected my local project:

```bash
git init
git add .
git commit -m "Initial Astro blog"
git branch -M main
git remote add origin https://github.com/S2P2/s2p2blog.git
git push -u origin main
```

GitHub is not the hosting layer here. It is the source of truth for the project. Cloudflare Pages watches the repository and deploys changes whenever I push to `main`.

## Step 3: Connect Cloudflare Pages

In Cloudflare, I used the Pages flow, not the Worker flow:

```text
Workers & Pages → Create → Pages → Import an existing Git repository
```

Then I selected:

```text
S2P2/s2p2blog
```

The key build settings were:

```text
Framework preset: Astro
Build command: npm run build
Build output directory: dist
```

One easy mistake is choosing the Worker deployment flow. If the screen asks for a deploy command like `npx wrangler deploy`, that is not the right path for a basic Astro static blog. For this setup, Cloudflare Pages should build the site and publish the generated `dist` folder.

## Step 4: Use the free Pages URL

Cloudflare Pages gives the project a free subdomain:

```text
https://s2p2blog.pages.dev/
```

A custom domain can come later. It is not required to start writing.

## Step 5: Publish updates

The publishing loop is now straightforward:

```bash
npm run dev
```

Edit locally, then publish:

```bash
git add .
git commit -m "Update blog"
git push
```

Cloudflare Pages automatically rebuilds and redeploys the site after each push.

## What this stack gives me

This setup is small, but it leaves room to grow. The first version can stay as a normal Markdown blog. Later, I can add MDX, custom components, notebook exports, Marimo embeds, theme controls, or JavaScript demos without migrating to a different platform.

That is the main reason I chose this stack: it starts simple, but does not trap the blog inside a fixed publishing system.
