# nebulacdr.com

Hugo website for [Nebula Commander](https://github.com/nebula-commander/nebula-commander), built with the [Docsy](https://themes.gohugo.io/themes/docsy/) theme.

## Prerequisites

- [Hugo extended](https://gohugo.io/installation/) (v0.110.0 or later)
- [Node.js](https://nodejs.org/) (for PostCSS; used by Docsy)
- Go (for Hugo modules)

## Run locally

From the repo root:

```bash
npm install   # install PostCSS and Autoprefixer for Docsy SCSS
hugo mod get  # fetch Docsy theme (first time only)
hugo server
```

Open http://localhost:1313.

## Build

```bash
hugo
```

Output is in `public/`.

## Deploy

Every push to `main` builds the site and publishes it as an nginx image,
`ghcr.io/nebula-commander/docs` (`docker/`, `.github/workflows/docs-image.yml`). The Cloud server
runs that image behind Traefik, and Watchtower deploys each new one within about 5 minutes
(nebula-commander-cloud: `deploy/docs/`). **A push to `main` goes live**, so keep docs for
unreleased features on a branch until the release.

The image serves `nebulacommander.com` and redirects `nebulacdr.com`, `www.nebulacdr.com` and
`www.nebulacommander.com` to the same path there.

## Project structure

- `content/en/` — English content (home, About, Docs, Blog, Community)
- `assets/scss/_styles_project.scss` — Custom nebula-style cover background
- `assets/icons/logo.svg` — Navbar logo
- `static/logo.svg` — Logo used on the landing cover
- `hugo.yaml` — Site config and Docsy module

## Theme

The site uses the Docsy Hugo theme as a module (see `module.imports` in `hugo.yaml`). Custom styles and content are in this repo.
