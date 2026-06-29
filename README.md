# Rick Dinh — Resume & Portfolio (Static Site)

A single-page resume and portfolio built with semantic HTML, modular CSS, and lightweight JavaScript — plus a couple of custom touches that go beyond a typical resume template. The site is fast, portable, and easy to customize.

## Overview
- Tabbed navigation for Profile, Resume, Portfolio, and Contact
- Profile section opens with a combined bio (About + Objective merged into one scannable block) instead of two separate walls of text
- Interactive hover effects on the Profile photo (cursor-tracking 3D tilt + glow), headline, and personal info rows
- A hidden-gem mini-game: a canvas-based "cat vs. snakes" runner (Chrome-dino style) embedded where the old Objective block used to live — Play button on load, Space/tap to jump, difficulty ramps up the longer you survive
- Skills displayed with data-driven ratings rendered as small pixel-art cats instead of plain dots (`data-rat` ranges 4–7 depending on skill strength, not a fixed scale)
- Filterable, lightbox-enabled Portfolio grid
- Fully static: works offline and deploys to any static host

## Tech Stack (Brief Introductions)
- **HTML5** — Semantic structure for sections, accessibility, and clean markup.
- **CSS3** (`reset.css`, `style.css`, `prettyPhoto.css`, plus an inline `<style>` block in `index.html` for custom animations, the pixel-cat ratings, and the game UI) — Visual styling, layout, and component presentation; reset ensures consistent defaults across browsers.
- **Google Fonts** — Web typography for improved readability and visual hierarchy.
- **jQuery** — Utility layer for DOM manipulation, event handling, and plugin initialization.
- **jQuery EasyTabs** — Powers the tabbed interface; switches sections without page reloads.
- **Isotope** — Handles the Portfolio's filtering and animated layout of grid items.
- **prettyPhoto** — Lightbox effect for images and galleries, including grouped slides.
- **Respond.js** — Graceful degradation and responsive behavior in older browsers.
- **jQuery UI Map (optional)** — Integration layer if a map is embedded; safe to remove if unused.
- **jQuery Carousel (optional)** — Enables carousel-style sliders when needed.
- **Custom Scripts** (`plugins.js`, `custom.js`) — Site-specific behavior: tab initialization, portfolio filtering, lightbox setup, and rendering skill ratings based on `data-rat` attributes.
- **Inline vanilla JS** (bottom of `index.html`, no extra files) — Photo tilt effect, pixel-cat rating paint logic (via `MutationObserver`, since the rating `<span>`s are added asynchronously by `custom.js`), and the full cat-vs-snakes game loop (physics, collision detection, scoring, rendering) drawn entirely on an HTML5 `<canvas>` — no image or sprite assets required.

## Project Structure
```
index.html             # main single-page app (tabs + sections + game + custom styles/scripts)
css/                   # stylesheets (reset, base styles, lightbox styles)
js/                    # third-party plugins + site scripts
images/                # profile/decorative images
portfolio/             # portfolio thumbnails and full-size assets
```

> Note: there are no separate image or sprite files for the pixel cats or the game — both are drawn with CSS (`box-shadow` pixel grids) and Canvas drawing calls respectively, defined inline in `index.html`.

## Run Locally
**Option A:** open `index.html` directly in a browser.  
**Option B (recommended):** start a simple local server:
```bash
python3 -m http.server 5500
```
Then open your browser to the local server on port 5500 and navigate to `index.html`.

## Customize
- **Branding:** Edit name, title, email, phone, and location in the header/Profile.
- **Bio:** The combined About/Objective copy lives in `.about p` and `.about-highlights` inside the Profile section — edit the intro paragraph and the three highlight bullets there.
- **Experience / Education / Projects:** Update the corresponding sections in `index.html`.
- **Skills & Ratings:** Set each item's `data-rat` (current scale: 1–7) to control how many pixel cats appear filled. The cat colors and pixel pattern are defined in the `<style>` block under "Pixel-cat skill rating."
- **Mini-Game:** Lives in `#blurb` where the old Objective block used to be. Game constants (jump height, gravity, base speed, difficulty ramp, spawn rate) are declared near the top of the game's `<script>` block and are safe to tweak independently of the drawing code.
- **Portfolio:** Add list items under `#portfolio-list`. Use category classes (e.g., `apps`, `webdev`, `games`) that match the filter buttons.
- **Lightbox Grouping:** Add `class="folio"` to links and reuse the same `rel` value (e.g., `portfolio[my-project]`) to group multiple slides.
- **Contact Form:** Static by default. Wire it to a service or backend and set the form's `action` when you're ready.

## Accessibility & Performance
- Provide meaningful `alt` text for images.
- Keep contrast and font sizes readable.
- Compress images (especially thumbnails) for faster load.
- Remove optional scripts (maps, carousel) if not used.
- The mini-game listens for the Space bar globally but ignores it while a form `<input>` or `<textarea>` is focused, so it won't interfere with the Contact form.

## Notes
- The layout assumes consistent thumbnail aspect ratios for a tidy grid.
- If a tab doesn't switch, verify `href="#section-id"` matches `<section id="section-id">`.
- If the lightbox or filtering doesn't work, ensure the related scripts are loaded and initialized in `custom.js`.
- The pixel-cat ratings depend on `custom.js` having already appended its placeholder `<span>` elements; a `MutationObserver` in the inline script handles this automatically, so no manual timing/ordering changes should be needed if you add new skill rows.

## License
Personal portfolio. Unless otherwise stated, content is © Rick Dinh.