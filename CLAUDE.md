# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a portfolio website built with Astro, based on the Astro Blog starter template. It uses TypeScript with strict null checks and includes MDX support for blog content.

## Development Commands

- `npm run dev` - Start development server at localhost:4321
- `npm run build` - Build production site to ./dist/
- `npm run preview` - Preview production build locally
- `npm run astro ...` - Run Astro CLI commands (e.g., `npm run astro add`, `npm run astro check`)

## Architecture

### Content Management

The site uses Astro Content Collections for managing blog posts:
- Blog posts are stored in `src/content/blog/` as Markdown or MDX files
- Use `getCollection('blog')` to retrieve posts in pages
- Dynamic blog post pages are rendered via `src/pages/blog/[...slug].astro`

### Routing

- Pages in `src/pages/` are automatically exposed as routes based on filename
- Blog posts use dynamic routing with `[...slug].astro` for individual post pages
- `src/pages/blog/index.astro` serves as the blog listing page

### Layouts & Components

- `src/layouts/BlogPost.astro` - Main layout for blog posts, handles frontmatter (title, description, pubDate, updatedDate, heroImage)
- `src/components/BaseHead.astro` - HTML head with SEO meta tags
- `src/components/Header.astro` - Site header navigation
- `src/components/Footer.astro` - Site footer
- `src/components/FormattedDate.astro` - Date formatting component

### Configuration

- Site title and description are centralized in `src/consts.ts` (SITE_TITLE, SITE_DESCRIPTION)
- `astro.config.mjs` includes MDX and sitemap integrations
- Update the `site` URL in `astro.config.mjs` before deployment

### TypeScript

The project uses Astro's strict TypeScript configuration. Content collections use typed props via `CollectionEntry<'blog'>`.