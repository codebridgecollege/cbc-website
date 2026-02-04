# Development

### Stack

- **Framework**: Next.js 15 (App Router) with `output: 'export'`
- **Styling**: Tailwind CSS v4, shadcn/ui (new-york, neutral)
- **i18n**: next-intl (single hardcoded locale: `en`)
- **Hosting**: GitHub Pages (or Netlify/Cloudflare Pages); deploy on push to `main`

### Dev server

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

### Build

```bash
npm run build
```

Output is in the `out/` directory (static HTML/CSS/JS).

### Updating content

- **Reviews**: Edit `content/reviews/index.json` (name, profilePic, rating, text). Add or remove entries; use a unique `slug` per review.
- **Courses**: Edit `content/courses/index.json` (slug, title, description, duration). Add or remove entries.
- **Translations**: Edit `messages/en.json` for copy. Locale is hardcoded to `en` for the static build.

Push changes to the `main` branch to trigger a new build and deploy (when GitHub Actions and GitHub Pages are configured).

### Deploying to GitHub Pages

1. In the repo: **Settings → Pages → Build and deployment**: Source = **GitHub Actions**.
2. Push to `main`. The workflow in `.github/workflows/deploy.yml` runs `npm ci`, `npm run build`, and deploys the `out/` directory to GitHub Pages.

### Deploying to Netlify or Cloudflare Pages

- **Build command**: `npm run build`
- **Publish directory**: `out`
- Connect the repo; each push to `main` will build and deploy.
