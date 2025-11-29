# Agent Instructions for Analytiq Pages Starter

This file provides guidance for AI agents (Claude, Cursor, etc.) working with the Analytiq Pages Starter codebase. This file is excluded from Jekyll processing and will not appear as a page on the website.

## How This File is Excluded from Jekyll

This file is excluded from Jekyll processing by adding it to the `exclude` list in `_config.yml`:

```yaml
exclude:
  - AGENTS.md
  - CLAUDE.md
  - README.md
  - Gemfile
  - Gemfile.lock
  - Makefile
  - LICENSE
```

Files listed in `exclude` are:
- Not processed by Jekyll
- Not included in the `_site/` output directory
- Not accessible as web pages
- Still available in the repository for agents and developers to read

## Project Overview

The Analytiq Pages Starter is a Jekyll-based static site generator template that uses the Analytiq Pages Theme. It's designed for creating professional company websites, product pages, and documentation sites.

### Key Technologies

- **Jekyll**: Static site generator (Ruby-based)
- **Analytiq Pages Theme**: Theme providing layouts, styling, and components
- **Tailwind CSS**: Utility-first CSS framework (loaded via CDN)
- **Liquid**: Templating language used by Jekyll
- **GitHub Pages**: Deployment platform (via GitHub Actions)

## Project Structure

```
analytiq-pages-starter/
├── _config.yml              # Site configuration (YAML)
├── _includes/               # Site-specific includes (overrides theme)
│   └── docs-widget.html    # Custom docs navigation
├── _posts/                  # Blog posts collection
├── docs/                    # Documentation pages
├── assets/                  # Static assets
│   ├── excalidraw/         # Excalidraw diagram files
│   └── images/             # Image files
├── .github/workflows/      # GitHub Actions workflows
├── *.md                     # Root-level pages (index, about, etc.)
└── Gemfile                  # Ruby dependencies
```

## Important Files

### Configuration

- **`_config.yml`**: Main site configuration
  - Site metadata (title, author, description)
  - Navigation menus (`header_pages`, `site_map`)
  - Collections configuration (`posts`)
  - Pagination settings
  - Plugin list

### Content Files

- **Root `.md` files**: Main site pages (index.md, about.md, etc.)
  - Use front matter to specify layout and metadata
  - Markdown content below front matter

- **`docs/*.md`**: Documentation pages
  - Use `layout: docs` for sidebar navigation
  - Add links to `_includes/docs-widget.html` for navigation

- **`_posts/YYYY-MM-DD-title.md`**: Blog posts
  - Must follow date-prefixed naming convention
  - Use `layout: post`
  - Categories are space-separated in front matter

### Theme Integration

- **Theme**: Specified in `_config.yml` as `theme: analytiq-pages-theme`
- **Theme version**: Pinned in `Gemfile` (currently v0.1.8)
- **Overrides**: Create files in `_includes/` or `_layouts/` to override theme defaults

## Common Tasks

### Adding a New Page

1. Create `.md` file at root or in appropriate directory
2. Add front matter:
   ```yaml
   ---
   layout: page
   title: Page Title
   permalink: /page-url/
   ---
   ```
3. Add navigation link in `_config.yml` if needed

### Adding a Blog Post

1. Create file in `_posts/` with format: `YYYY-MM-DD-title.md`
2. Add front matter:
   ```yaml
   ---
   layout: post
   title: "Post Title"
   date: 2025-11-29 10:00:00 -0400
   categories: category1 category2
   author: "Author Name"
   image: /assets/images/blog/image.svg
   ---
   ```

### Adding Documentation

1. Create `.md` file in `docs/` directory
2. Use `layout: docs` in front matter
3. Add link to `_includes/docs-widget.html` navigation

### Embedding Excalidraw Diagrams

```liquid
{% include excalidraw-static.html file="/assets/excalidraw/diagram.excalidraw" %}
```

Add edit link:
```liquid
<div class="text-sm text-gray-500 mt-2 mb-6 text-center">
  <a href="{{ '/excalidraw-edit' | relative_url }}?file={{ '/assets/excalidraw/diagram.excalidraw' | relative_url }}" 
     class="text-gray-500 hover:text-gray-700 no-underline" 
     target="_blank">
    Edit diagram
  </a>
</div>
```

## Liquid Template Syntax

### Escaping Liquid Code in Documentation

When documenting Liquid syntax in markdown files, wrap examples in `{% raw %}` tags:

```liquid
{% raw %}{{ site.title }}{% endraw %}
```

This prevents Jekyll from processing the Liquid code during build.

### Common Variables

- `site.*`: Site configuration from `_config.yml`
- `page.*`: Current page front matter
- `paginator.*`: Pagination data (on paginated pages)
- `post.*`: Post data (in post layouts)

### Common Filters

- `relative_url`: Convert to relative URL
- `date`: Format dates
- `markdownify`: Convert markdown to HTML
- `where`: Filter arrays
- `sort`: Sort arrays

## Build and Deployment

### Local Development

```bash
bundle install
bundle exec jekyll serve
```

Visit http://localhost:4000

### Deployment

- **GitHub Pages**: Automatic via GitHub Actions workflow
- **Workflow**: `.github/workflows/pages.yml`
- **Trigger**: Push to `main` branch or manual dispatch

## Best Practices

1. **Always use front matter**: Every content file needs `layout` and `title`
2. **Use permalinks**: Explicit permalinks prevent URL changes
3. **Follow naming conventions**: kebab-case for files, space-separated categories
4. **Test locally**: Always test changes with `bundle exec jekyll serve`
5. **Exclude non-content files**: Add files like `AGENTS.md` to `exclude` in `_config.yml`

## Troubleshooting

### File Not Appearing on Site

- Check if file is in `exclude` list in `_config.yml`
- Verify front matter is correct
- Check for YAML syntax errors
- Restart Jekyll server

### Liquid Syntax Errors

- Wrap example code in `{% raw %}` tags
- Check for unclosed tags: `{% if %}...{% endif %}`
- Verify variable names match front matter

### Theme Not Loading

- Verify `theme: analytiq-pages-theme` in `_config.yml`
- Check Gemfile has correct theme reference
- Run `bundle install`

## Documentation References

- [Getting Started](/docs/getting-started/) - Setup and initial customization
- [User Guide](/docs/user-guide/) - Content management and customization
- [Architecture](/docs/architecture/) - Technical architecture details
- [API Reference](/docs/api-reference/) - Configuration and template APIs

## Notes for Agents

- This is a **static site generator**, not a dynamic web application
- There are **no REST APIs** - only configuration and template APIs
- Content is written in **Markdown** with YAML front matter
- **Liquid** is used for templating, not a programming language
- Files in `exclude` list are **not processed** by Jekyll
- The theme is loaded from a **Git repository** (GitHub)
- All pages are **pre-rendered** at build time, not runtime

