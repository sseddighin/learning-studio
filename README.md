# Future Learning Studio

A responsive, single-page website for a fictional university initiative for faculty, educators, researchers, and community partners. It is not affiliated with UCI. All people and events are fictional, and no registration or data collection is offered.

## Files

- `index.html`: semantic page content and accessible in-page navigation.
- `styles.css`: responsive layouts and CSS illustrations; uses system fonts with no external assets or dependencies.
- `wrangler.jsonc`: Cloudflare Workers static-assets and branch-preview configuration.
- `.assetsignore`: limits Workers uploads to the two public website files.

## Local preview

Run `python3 -m http.server 8000` from this directory, then open the local server in a browser. No installation or build step is required.

## Deployment

### Cloudflare Workers Builds (current Git integration)

This is an assets-only Worker: no JavaScript entry point, build step, or backend is needed. `wrangler.jsonc` serves the repository root, and `.assetsignore` includes only `index.html` and `styles.css`. The empty `previews` block enables the current Worker Previews command; assets and compatibility settings remain at the top level.

In **Cloudflare dashboard → Workers & Pages → your Worker → Settings → Build**, edit the Git build configuration:

- Root directory: repository root (`/`, or leave the default).
- Build command: empty (no build required).
- Deploy command (production): `npx wrangler@4.151.0 deploy`.
- Non-production branch deploy command: `npx wrangler@4.151.0 preview`.
- Production branch: `main`; enable non-production branch builds for PR previews.

Save the settings and retry the failed branch build. Confirm that the Worker's dashboard name matches `learning-studio` in `wrangler.jsonc`; if the existing Worker has a different name, use that exact name in the configuration. Do not put `wrangler preview` in the production deploy field: it creates a preview rather than updating production. The wording “user deploy command” in a log alone does not identify which dashboard field was used.

Local deployment validation (no account or publication required):

```sh
npx wrangler@4.151.0 deploy --dry-run --outdir /tmp/learning-studio-worker
npx wrangler@4.151.0 dev --local
```

A real deployment/preview requires Cloudflare authorization, supplied by the Workers Builds integration. Never commit credentials. Wrangler is fetched on demand; the website itself still has no dependencies or build step.

### Cloudflare Pages or GitHub Pages (alternatives)

For Cloudflare Pages, create a **Pages** Git project, select no framework, leave the build command empty, and use the repository root (`.`) as the output directory. Pages manages branch previews itself; it does not use `wrangler preview` or this Workers configuration. There is no need to migrate the existing Workers integration to fix this error.

For GitHub Pages, publish the main branch from `/ (root)`. All asset paths are relative, so project subpaths work.

## Validation

The site can be checked using a local HTTP server and a browser at desktop and mobile widths. Check section links, keyboard focus, contrast, text wrapping, and horizontal overflow. There is no JavaScript, backend, form, or automated test suite.

## Content and accessibility

The page includes a hero, approach, three programs, dated sample workshops, fictional collaborators, and audience-specific involvement pathways. All events and people are fictional. It is not an official UCI site and offers no registration, contact form, or data collection. Navigation uses native anchor links and remains visible on mobile, with a skip link, visible focus, reduced-motion support, and semantic section headings. No JavaScript is required.
