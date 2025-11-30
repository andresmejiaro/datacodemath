````markdown
# datacodemath.com

Personal site of **Andrés Mejía** — a hub for data, code, math, and systems experiments.  
Built with **Astro** and **Tailwind CSS**, deployed as a static site.

This repo is intentionally simple: content-first, fast to load, and easy to maintain for years.

---

## Tech stack

- [Astro](https://astro.build/) – static site framework (HTML-first, partial hydration capable)
- [Tailwind CSS](https://tailwindcss.com/) – utility-first styling
- Node.js (LTS) – for development and builds

No database, no backend app server. Production is just static files behind Nginx (or any static host).

---

## Getting started

Clone the repo and install dependencies:

```bash
git clone git@github.com:YOUR_USER/datacodemath.git
cd datacodemath

npm install
````

Start the dev server:

```bash
npm run dev
```

Then open:

* [http://localhost:4321](http://localhost:4321)

Astro will hot-reload on file changes.

---

## Scripts

Common npm scripts:

```bash
npm run dev     # start local dev server
npm run build   # build static site into dist/
npm run preview # serve the built site locally (dist/)
```

`dist/` is what gets deployed to the server.

---

## Project structure

Key folders and files:

```text
.
├─ astro.config.mjs       # Astro configuration
├─ package.json
├─ public/                # Static assets (served at /)
└─ src/
   ├─ layouts/
   │  └─ BaseLayout.astro # Shared HTML shell (head/body/container)
   ├─ components/
   │  └─ Header.astro     # Top navigation bar
   ├─ pages/
   │  ├─ index.astro      # Home
   │  ├─ work.astro       # Selected projects / case studies
   │  ├─ about.astro      # About Andrés
   │  └─ contact.astro    # Contact (stub / to be expanded)
   └─ styles/
      └─ global.css       # Tailwind import + base styling
```

Astro uses **file-based routing**:

* `src/pages/index.astro` → `/`
* `src/pages/work.astro` → `/work`
* `src/pages/about.astro` → `/about`
* `src/pages/contact.astro` → `/contact`

---

## Styling (Tailwind v4 via Vite plugin)

Tailwind is loaded through the Tailwind Vite plugin and a single global stylesheet:

```css
/* src/styles/global.css */
@import "tailwindcss";

body {
  background-color: black;
  color: white;
  -webkit-font-smoothing: antialiased;
}
```

Components and pages use Tailwind utility classes directly in their markup (e.g. `bg-black`, `rounded-2xl`, `text-teal-700`).

No design system or component library is enforced; everything is plain Tailwind.

---

## Build & deployment

Build a production-ready static site:

```bash
npm run build
```

This generates `dist/` with plain HTML, CSS, and JS.

You can serve `dist/` with any static web server. Example Nginx config (simplified):

```nginx
server {
    listen 80;
    server_name datacodemath.com;

    root /var/www/datacodemath/dist;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

Then:

* point your domain’s DNS A record at the server’s IP,
* add HTTPS via Let’s Encrypt / certbot if needed.

---

## Roadmap (high level)

Planned evolutions of this site:

* **Project data extraction** – move projects into a small data module (or content collection) and render them as cards on `/` and `/work`.
* **Better copy** – refine hero / project descriptions / About page to match current work.
* **“Build log” project** – add an entry documenting this site itself as an AI-assisted build.
* Optional:

  * long-form posts (blog/notes) via Astro content collections,
  * small interactive “lab” islands for experiments (RL demos, behavior tree visualizations, etc.).

---

## License

TBD. For now, treat this as “all rights reserved” unless a license file is added.

```
::contentReference[oaicite:0]{index=0}
```
