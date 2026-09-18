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

## Branding

Colors follow Maastricht University's public house style (dark blue `#001C3D`
primary, orange-red `#E84E10` and light blue `#00A2DB` accents) — set once in
`style.css` under `:root`. I couldn't find published brand colors specifically
for MaCSBio or BioSB (MaCSBio is a UM institute and likely just follows the UM
house style; BioSB's own site doesn't publish a color spec), so the palette
leans on UM's. Swap the `--um-*` values if MaCSBio or BioSB give you different
guidance.

Each page has a white **"Organized by"** bar at the top with the UM, MaCSBio
and BioSB logos (white background because UM's own logo guidelines say it
should sit on a white or light background).

**The three logos are currently hotlinked to the URLs you gave me** — I don't
have the ability to download binary image files in this sandbox, so I wired
the `<img>` tags straight to their source URLs rather than committing copies.
This will render fine once the site is live, but it's not reliable long-term
(any of those pages could move, rename, or take the image down, and you'd
have no control over it). Before this goes live for real, self-host them:

1. Save each image locally (right-click → save image, or download from the
   same URLs you gave me):
   - Maastricht University: the Wikimedia Commons URL
   - MaCSBio: the maastrichtuniversity.nl URL
   - BioSB: the dtls.nl URL
2. Create an `assets/logos/` folder in the repo and put the files there
   (e.g. `um.png`, `macsbio.png`, `biosb.png`).
3. In every page's `<div class="partner-bar__inner">` block, change each
   `src="https://..."` to the local path, e.g.
   `src="assets/logos/um.png"`.

Ideally use the actual official logo files from each institution's brand/
house-style page rather than a Wikipedia thumbnail or a page screenshot —
they'll be higher resolution and (for UM in particular) in the exact approved
file. If the UM logo you use is the full-colour/dark-blue version, it should
keep working fine on the white bar as-is.

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
