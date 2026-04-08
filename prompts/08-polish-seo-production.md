# Prompt 8: Landing Page Polish, SEO, and Production Readiness

## Objective

Replace all placeholder content on the landing page with real Caddi branding, optimize for SEO and performance, and prepare the application for a public launch.

## Tasks

### 1. Replace placeholder content

- Rewrite all hero text, feature descriptions, and testimonials with real Caddi product copy that describes the project management / productivity platform.
- Replace Tailwind UI placeholder images with custom illustrations, screenshots, or SVG graphics.
- Update the logo cloud section with real partner/integration logos or remove it.
- Replace the footer company name ("Your Company, Inc.") and copyright year with "Caddi" and the current year.

### 2. Add SEO meta tags

- Install `@unhead/vue` (or use Vite plugin) for managing `<head>` tags.
- Add essential meta tags to every page:
  - `<title>`, `<meta name="description">`, `<meta name="keywords">`
  - Open Graph tags (`og:title`, `og:description`, `og:image`, `og:url`)
  - Twitter card tags
- Create a `public/robots.txt` and `public/sitemap.xml`.

### 3. Add a favicon and app icons

- Design or generate a Caddi favicon and app icons.
- Replace the default `vite.svg` favicon.
- Add `apple-touch-icon`, `manifest.json` for PWA support.

### 4. Performance optimization

- Enable code splitting: use `defineAsyncComponent` or dynamic `import()` for heavy pages (dashboard, project detail).
- Configure Vite to tree-shake unused Heroicons.
- Add `loading="lazy"` to all images.
- Run Lighthouse audit and address any issues.

### 5. Error and 404 pages

- Create a `NotFoundPage.vue` for unmatched routes.
- Create a generic `ErrorPage.vue` for unexpected errors.
- Add a Vue error handler in `main.ts` that catches unhandled errors and displays the error page.

### 6. Accessibility audit

- Ensure all interactive elements have proper ARIA labels.
- Verify keyboard navigation works throughout the app.
- Check color contrast ratios meet WCAG AA standards.
- Add skip-to-content links.
