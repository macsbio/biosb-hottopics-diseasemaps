# Hot Topic: Disease Maps — event site

Plain HTML/CSS, no build step. Five pages that share one stylesheet:

- `index.html` — home (key facts, registration, previews)
- `speakers.html` — speaker bios (placeholders — see below)
- `program.html` — the timed schedule
- `materials.html` — breakout / hands-on session materials
- `contact.html` — contact email
- `style.css` — all styling and colors, shared by every page

## Put it on GitHub Pages

1. Create a new repository on GitHub (e.g. `disease-maps-hottopic`).
2. Add these files to the repo root (drag-and-drop on github.com works fine, or `git add . && git commit -m "site" && git push`).
3. In the repo: **Settings → Pages**.
4. Under "Build and deployment", set **Source: Deploy from a branch**, branch **main**, folder **/(root)**.
5. Save. GitHub gives you a URL like `https://<your-username>.github.io/disease-maps-hottopic/` within a minute or two.
6. (Optional) Add a custom domain under the same Pages settings if you have one.

No Jekyll config, no dependencies — it's just static files, so this is the whole setup.

## Editing content

Everything is plain text in the HTML files — no template language. Places marked
`<!-- EDIT ME -->` are the ones you'll touch most:

- **Speaker bios/photos** (`speakers.html`): each speaker is one `.speaker-card` block.
  Replace the `bio-placeholder` paragraph with real text, and swap the dashed
  `photo` placeholder `<div>` for `<img src="assets/speakers/name.jpg" alt="Name">`
  once you have photos (create an `assets/speakers/` folder for the images).
- **Program** (`program.html`): each row is one `<li>` in the `.timeline` list.
  Add/remove/reorder `<li>` blocks freely. Use `class="is-break"` for
  breaks/registration and `class="is-highlight"` to make an item stand out.
- **Breakout materials** (`materials.html`): one `.breakout-card` per room/session.
  Add logo images inside `.logo-row` (create an `assets/logos/` folder) and links
  inside `.materials-list`.
- **Contact email** (`contact.html`): one `mailto:` link.
- **Colors/fonts**: all in `style.css` under `:root { ... }` at the top — change a
  value there and it updates across every page.

## Adding a new page

Copy any existing page, change the `<title>`, update the `<main>` content, and add
a link to it in the `.site-nav__links` list in **every** page's nav (there's no
shared include — it's plain files, so the nav is duplicated on purpose to keep
things dependency-free).
