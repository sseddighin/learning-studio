# Learning Studio

A responsive, single-page website for a fictional independent learning collective. It is not affiliated with UCI. All people and events are fictional, and no registration or data collection is offered.

## Files

- `index.html`: semantic page content and accessible in-page navigation.
- `styles.css`: responsive layouts and CSS illustrations; uses system fonts with no external assets or dependencies.

## Local preview

Run `python3 -m http.server 8000` from this directory, then open the local server in a browser. No installation or build step is required.

## Deployment

For Cloudflare Pages, select no framework, leave the build command empty, and use the repository root (`.`) as the output directory. For GitHub Pages, publish the main branch from `/ (root)`. All asset paths are relative, so project subpaths work.

## Validation

The site can be checked using a local HTTP server and a browser at desktop and mobile widths. Check section links, keyboard focus, contrast, text wrapping, and horizontal overflow. There is no JavaScript, backend, form, or automated test suite.
