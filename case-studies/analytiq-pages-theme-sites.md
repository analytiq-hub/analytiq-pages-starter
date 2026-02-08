---
layout: case-study
title: Analytiq Pages Theme in Action
subtitle: How five sites use the same Jekyll theme for consulting, products, and personal sites
permalink: /case-studies/analytiq-pages-theme-sites/
date: 2025-02-08
---

The [Analytiq Pages Theme](https://github.com/analytiq-hub/analytiq-pages-theme) is a modern Jekyll theme built with Tailwind CSS, designed for technical content, product marketing, and documentation. Here’s how it’s used across five real sites: a consulting site, three product sites, and a personal knowledge site.

## Analytiq Hub — analytiqhub.com

**Use case:** Consulting and services marketing

Analytiq Hub’s main site runs on the theme to present services, success stories, talks, and blog content. The site uses:

- **Header logo** — Custom logo (40px / 80px retina) next to the site title for brand consistency.
- **Success Stories** — A dedicated case-studies section with the theme’s case-study layout and cards linking to individual stories (e.g. DocRouter.AI, healthcare, insurance).
- **Nested navigation** — Resources (Success Stories, Technology), Talks, Blog, About, and a prominent “Get Started” CTA.
- **Calendly** — Optional `calendly_url` for booking calls.
- **Dark skin** — Minima dark theme for a focused, readable look.

The theme’s customization hooks (`custom-head`, `custom-header`, `custom-footer`) keep analytics and site-specific content separate from the theme, so updates are straightforward.

## SMAHT AI — smaht.ai

**Use case:** Product and initiative site

SMAHT AI uses the theme to describe the initiative and link to resources. Typical usage includes:

- **Page layout** — Clean, content-first pages using the default and page layouts.
- **Docs-style structure** — Navigation and optional docs sidebar for getting started and reference content.
- **Consistent styling** — Same Tailwind-based components (alerts, buttons, cards) and typography as other theme sites.

The theme’s single codebase and shared components make it easy to keep branding and behavior consistent with other Analytiq-related sites.

## DocRouter.AI — docrouter.ai

**Use case:** Product marketing and documentation

DocRouter.AI uses the theme for the main marketing site and for detailed case studies. In practice:

- **Case study layout** — Long-form success stories (e.g. “DocRouter.AI - Document Processing Platform”) use the theme’s `case-study` layout with optional hero image, subtitle, and table-of-contents sidebar.
- **Technical content** — Blog posts and docs use the theme’s syntax highlighting (highlight.js), enhanced code blocks, and optional MathJax for equations.
- **Excalidraw** — Architecture and workflow diagrams are embedded via the theme’s Excalidraw integration (static SVG or interactive iframe).

The combination of case-study layout, code blocks, and diagrams supports both high-level storytelling and technical depth.

## SigAgent.AI — sigagent.ai

**Use case:** Product and developer-focused site

SigAgent.AI uses the theme to present the product and support developers:

- **Structured navigation** — Header and footer driven by `header_pages` and `site_map`, with optional nested menus (e.g. Docs with subsections).
- **Blog and docs** — Post layout with sidebar (recent posts, categories, archives) and docs layout with floating docs widget for multi-page documentation.
- **RSS and SEO** — Built-in jekyll-feed and jekyll-seo-tag for feeds and meta tags.

The theme’s blog sidebar and docs widget reduce custom layout work while keeping content organized.

## Bitdribble — bitdribble.github.io

**Use case:** Personal knowledge and portfolio site

Bitdribble uses the theme as a personal site (knowledge repository, writing, and projects):

- **Minimal config** — Same theme, with different `header_pages`, `site_map`, and content; no product-specific features required.
- **Dark theme** — Same Minima dark skin option for a consistent reading experience.
- **Markdown and assets** — Standard Jekyll content (Markdown, images, PDFs) with optional PDF embed and Excalidraw for diagrams.

This shows the theme scaling down to a simple, content-focused site without extra product or consulting sections.

## What the theme provides across all sites

Across these five sites, the theme delivers:

| Feature | Purpose |
|--------|---------|
| **Tailwind CSS** | Responsive layout, typography, and components without custom CSS |
| **Responsive nav** | Dropdowns and mobile hamburger driven by `header_pages` |
| **Nested menus** | Sub-menus (and deeper) in header and footer |
| **Case study layout** | Long-form stories with optional TOC sidebar |
| **Blog + sidebar** | Posts with pagination, categories, archives |
| **Docs widget** | Floating docs nav from `docs_sidebar_pages` |
| **Excalidraw** | Static or interactive diagram embeds |
| **Customization hooks** | custom-head, custom-header, custom-footer for analytics and branding |
| **Logo** | Optional `logo` / `logo_2x` in the header |
| **Dark skin** | Minima dark (and other skins) for consistent look |

Using one theme across consulting (Analytiq Hub), product (SMAHT AI, DocRouter.AI, SigAgent.AI), and personal (Bitdribble) sites keeps maintenance low and lets each site focus on content and config rather than layout and styling.
