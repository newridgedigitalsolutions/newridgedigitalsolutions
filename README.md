# New Ridge Digital Solutions — Website

A modern dark-mode site built with:
- **Svelte 5** (runes syntax)
- **Vite 6**
- **Tailwind CSS v4**
- **DaisyUI v5**

## Setup

```bash
npm install
npm run dev
```

Then open http://localhost:5173

## Build for production

```bash
npm run build
npm run preview   # preview the build locally
```

## Deploy to GitHub Pages (your current host)

The `static/CNAME` file (containing `www.newridgedigitalsolutions.com`) is already included.
Vite copies everything in `static/` into `dist/` automatically, so your custom domain is preserved.

A `.nojekyll` file is also included in `static/` — this tells GitHub Pages not to run Jekyll,
which would otherwise strip Vite's `_assets/` directory and break the site.

### Manual deploy
```bash
npm run build
# Then push the contents of dist/ to your gh-pages branch
```

### Recommended: GitHub Actions (auto-deploy on push)
Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npm run build
      - uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

This builds and pushes `dist/` to your `gh-pages` branch on every push to `main`.
Make sure your GitHub Pages source is set to the `gh-pages` branch in repo Settings → Pages.

---

## Customization

### Logo
Replace the placeholder icon in `src/lib/components/Navbar.svelte`.
Look for the comment `<!-- Logo placeholder — replace src with your actual logo -->` and swap in:
```html
<img src="/your-logo.png" alt="NRDS Logo" class="w-10 h-10 object-contain" />
```
Place your logo file in `static/`.

### Contact form
The contact form in `src/lib/components/Contact.svelte` uses a fake submit.
Connect it to a real endpoint — options:
- **Formspree**: https://formspree.io
- **Netlify Forms**: add `netlify` attribute to `<form>`
- **EmailJS**: client-side email sending

### Colors / theme
Edit the `@plugin "daisyui/theme"` block in `src/app.css` to adjust the palette.
Primary = sky blue (`#38bdf8`), Secondary = indigo (`#818cf8`), Accent = emerald (`#34d399`).

### Portfolio & Services
Edit the `projects` and `services` arrays directly in the component files:
- `src/lib/components/Services.svelte`
- `src/lib/components/Portfolio.svelte`

---

## Project structure

```
nrds-site/
├── index.html
├── vite.config.js
├── package.json
├── static/
│   ├── favicon.svg
│   └── fonts/
│       └── gaoel-webfont.woff2
└── src/
    ├── main.js
    ├── app.css          ← Tailwind 4 + DaisyUI 5 + custom theme
    ├── App.svelte       ← Root component
    └── lib/
        └── components/
            ├── Navbar.svelte
            ├── Hero.svelte
            ├── Services.svelte
            ├── Portfolio.svelte
            ├── About.svelte
            ├── Contact.svelte
            └── Footer.svelte
```
