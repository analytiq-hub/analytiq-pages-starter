# Company Website Starter

A professional Jekyll-based starter website using the [analytiq-pages-theme](https://github.com/analytiq-hub/analytiq-pages-theme). Perfect for company websites, product pages, and documentation sites.

## Features

- **Modern Design**: Built with Tailwind CSS for a clean, professional look
- **Complete Navigation**: Multi-level dropdown menus and footer sitemap
- **Blog**: Ready-to-use blog with pagination and sample posts
- **Documentation**: Comprehensive docs section with getting started, user guide, and API reference
- **Case Studies**: Showcase your success stories
- **Product Pages**: Highlight your products and features
- **Contact Form**: Pre-configured contact page (requires form service setup)
- **Responsive**: Mobile-first design that looks great on all devices
- **SEO Optimized**: Built-in SEO tags and sitemap
- **Fast**: Optimized for performance

## Quick Start

1. **Install dependencies:**
   ```bash
   bundle install
   ```

2. **Customize the site:**
   - Edit `_config.yml` with your company information
   - Update navigation menus in `_config.yml`
   - Customize pages in the root directory
   - Add your logo and images to `assets/images/`

3. **Run locally:**
   ```bash
   bundle exec jekyll serve
   ```

   Visit http://localhost:4000 to see your site

4. **Deploy:**
   - Push to GitHub and enable GitHub Pages
   - Or deploy to any static hosting service

## Structure

```
.
├── _config.yml           # Site configuration
├── _posts/               # Blog posts
├── docs/                 # Documentation pages
│   ├── getting-started.md
│   ├── user-guide.md
│   └── api-reference.md
├── index.md              # Homepage
├── about.md              # About page
├── contact.md            # Contact page
├── products.md           # Products overview
├── features.md           # Features page
├── case-studies.md       # Case studies
├── blog.md               # Blog listing page
└── 404.html              # Custom 404 page
```

## Customization

### Site Information

Edit `_config.yml` to update:
- Site title and description
- Author information
- Social media links
- Navigation menus
- Footer sitemap

### Branding Assets

Add your branding assets to customize the look:

- **Favicon**: Add `favicon.ico` to the root directory (you can generate one at [favicon.io](https://favicon.io/))
- **Logo**: Add your logo to `assets/images/logo.png`
- **Images**: Store other images in `assets/images/`

### Navigation Menu

The header navigation is configured in `_config.yml` under `header_pages`. You can create multi-level dropdown menus:

```yaml
header_pages:
  - title: "Products"
    url: "#"
    children:
      - title: "Overview"
        url: "/products"
      - title: "Features"
        url: "/features"
```

### Adding Blog Posts

Create new posts in the `_posts` directory with the naming format:
```
YYYY-MM-DD-post-title.md
```

Include front matter at the top:
```yaml
---
layout: post
title: "Your Post Title"
date: 2025-11-29 10:00:00 -0400
categories: category1 category2
author: "Author Name"
---
```

### Contact Form

The contact form requires a form submission service. Update the form action in `contact.md`:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

Popular options:
- [Formspree](https://formspree.io/)
- [Netlify Forms](https://www.netlify.com/products/forms/)
- [Getform](https://getform.io/)

## Theme

This starter uses the [analytiq-pages-theme](https://github.com/analytiq-hub/analytiq-pages-theme), which provides:
- Tailwind CSS styling
- Responsive layouts
- Blog and documentation layouts
- SEO optimization
- Social sharing

## Deployment

### GitHub Pages (Recommended)

This starter includes a GitHub Actions workflow for automatic deployment to GitHub Pages.

#### Initial Setup

1. **Push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/yourrepo.git
   git push -u origin main
   ```

2. **Enable GitHub Pages**:
   - Go to your repository on GitHub
   - Navigate to **Settings** → **Pages** (in the left sidebar)
   - Under **Source**, select **GitHub Actions**
   - Click **Save**

3. **Deploy**:
   - The site will automatically build and deploy when you push to the `main` branch
   - The workflow is configured in `.github/workflows/pages.yml`
   - Your site will be available at `https://yourusername.github.io/repo-name`

4. **Monitor Deployment**:
   - Go to the **Actions** tab in your repository to see build progress
   - Once the workflow completes, your site will be live
   - The deployment URL is shown in the workflow output 

#### Custom Domain (Optional)

To use a custom domain with GitHub Pages:

1. Add a `CNAME` file to your repository root with your domain:
   ```
   www.yourdomain.com
   ```

2. Configure DNS with your domain provider:
   - For apex domain (`yourdomain.com`): Add A records pointing to GitHub's IPs
   - For www subdomain: Add a CNAME record pointing to `yourusername.github.io`

3. In GitHub Settings → Pages, enter your custom domain and enable HTTPS

See [GitHub's custom domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site) for detailed instructions.

### Other Platforms

This is a standard Jekyll site and can be deployed to:
- **Netlify**: Connect your GitHub repo and it will auto-deploy
- **Vercel**: Import your GitHub repo for automatic deployments
- **CloudFlare Pages**: Connect repository and configure build command: `bundle exec jekyll build`
- **Any static hosting**: Run `bundle exec jekyll build` and upload the `_site` folder

## License

This starter template is open source and available under the MIT License.

## Support

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Theme Documentation](https://github.com/analytiq-hub/analytiq-pages-theme)
- [GitHub Issues](https://github.com/yourusername/yourrepo/issues)

## Credits

Built with:
- [Jekyll](https://jekyllrb.com/)
- [analytiq-pages-theme](https://github.com/analytiq-hub/analytiq-pages-theme)
- [Tailwind CSS](https://tailwindcss.com/)
