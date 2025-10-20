# Rick Dinh — Resume & Portfolio (Static Site)

A single-page resume and portfolio built with semantic HTML, modular CSS, and lightweight JavaScript. The site is fast, portable, and easy to customize.

## Overview
- Tabbed navigation for Profile, Resume, Portfolio, and Contact
- Filterable, lightbox-enabled Portfolio grid
- Skills displayed with data-driven ratings (standardized to 6 points)
- Fully static: works offline and deploys to any static host

## Tech Stack (Brief Introductions)
- **HTML5** — Semantic structure for sections, accessibility, and clean markup.
- **CSS3** (`reset.css`, `style.css`, `prettyPhoto.css`) — Visual styling, layout, and component presentation; reset ensures consistent defaults across browsers.
- **Google Fonts** — Web typography for improved readability and visual hierarchy.
- **jQuery** — Utility layer for DOM manipulation, event handling, and plugin initialization.
- **jQuery EasyTabs** — Powers the tabbed interface; switches sections without page reloads.
- **Isotope** — Handles the Portfolio’s filtering and animated layout of grid items.
- **prettyPhoto** — Lightbox effect for images and galleries, including grouped slides.
- **Respond.js** — Graceful degradation and responsive behavior in older browsers.
- **jQuery UI Map (optional)** — Integration layer if a map is embedded; safe to remove if unused.
- **jQuery Carousel (optional)** — Enables carousel-style sliders when needed.
- **Custom Scripts** (`plugins.js`, `custom.js`) — Site-specific behavior: tab initialization, portfolio filtering, lightbox setup, and rendering skill ratings based on `data-rat` attributes.

## Project Structure
```
index.html             # main single-page app (tabs + sections)
css/                   # stylesheets (reset, base styles, lightbox styles)
js/                    # third-party plugins + site scripts
images/                # profile/decorative images
portfolio/             # portfolio thumbnails and full-size assets
```

## Run Locally
**Option A:** open `index.html` directly in a browser.  
**Option B (recommended):** start a simple local server:
```bash
python3 -m http.server 5500
```
Then open your browser to the local server on port 5500 and navigate to `index.html`.

## Customize
- **Branding:** Edit name, title, email, phone, and location in the header/Profile.
- **Experience / Education / Projects:** Update the corresponding sections in `index.html`.
- **Portfolio:** Add list items under `#portfolio-list`. Use category classes (e.g., `apps`, `webdev`, `games`) that match the filter buttons.
- **Lightbox Grouping:** Add `class="folio"` to links and reuse the same `rel` value (e.g., `portfolio[my-project]`) to group multiple slides.
- **Skills Scale (6 points):** Set each item’s `data-rat="6"` for a uniform display.
- **Contact Form:** Static by default. Wire it to a service or backend and set the form’s `action` when you’re ready.

## Accessibility & Performance
- Provide meaningful `alt` text for images.
- Keep contrast and font sizes readable.
- Compress images (especially thumbnails) for faster load.
- Remove optional scripts (maps, carousel) if not used.

## Notes
- The layout assumes consistent thumbnail aspect ratios for a tidy grid.
- If a tab doesn’t switch, verify `href="#section-id"` matches `<section id="section-id">`.
- If the lightbox or filtering doesn’t work, ensure the related scripts are loaded and initialized in `custom.js`.

## License
Personal portfolio. Unless otherwise stated, content is © Rick Dinh.
