# Bassett Theatre — Squarespace Section Guide

This file explains how to break `index.html` into separate Squarespace Code Blocks.
Each section is clearly labelled in the HTML with `<!-- SECTION: ... -->` comments.

---

## Option A — Whole page as one block

Paste the entire `index.html` into a single Squarespace **Code Block** (or **Embed Block**) in a blank page.
Enable "Display source code" → off. Works best in a blank Squarespace template with the default header/footer disabled.

---

## Option B — Section by section (recommended for Squarespace)

Squarespace Code Blocks can each receive one chunk below.
Use **Edit > Add Block > Code** for each.
Keep the `<style>` tag in the **first** block only (or inject it via Settings > Custom CSS).

---

### Block 0 — Shared CSS + Google Fonts (inject once)

**Where:** Settings → Advanced → Code Injection → Header

Paste this entire `<style>` block (from `<link rel="preconnect"...>` through `</style>`).

---

### Block 1 — Navigation

**Where:** Header Code Block (Settings → Advanced → Code Injection → Header, after the CSS)
Or: A Code Block pinned to the top of your page.

```
<!-- NAV section in index.html -->
<nav id="main-nav"> ... </nav>
```

Cut from the first `<nav id="main-nav">` through `</nav>`.

**Nav links:** About / Productions / Press / Contact, in that order. To add or reorder links, edit the `<li>` items inside `<ul class="nav-links" id="nav-links">`.

---

### Block 2 — Hero

**Where:** First full-width Code Block on the page.

```html
<section id="hero"> ... </section>
```

Cut from `<section id="hero">` through its closing `</section>`.

---

### Block 3 — About

**Where:** Second Code Block.

```html
<section id="about"> ... </section>
```

---

### Block 4 — Productions

**Where:** Third Code Block.

```html
<section id="productions"> ... </section>
```

**To edit production copy:**
- `An Act(Or?)` card: update the `<p class="production-body">` paragraph inside the first `.production-card`
- `The Nose` card: update the same element in the second `.production-card`
- Credit lines: each card has a `<p class="production-credit">` directly under the title — update the name/role there
- Tags: change `"Available to tour"` / `"In development"` as needed

---

### Block 5 — Press

**Where:** Fourth Code Block, placed between Productions and Contact.

```html
<section id="press"> ... </section>
```

Cut from `<!-- SECTION: PRESS -->` through the closing `</section>` (matches the section between Productions and Contact).

**To edit reviews:**
- Each review lives in its own `<div class="press-card">` inside `.press-grid`
- Star rating: `<p class="press-stars">` (omit this element entirely for a review with no rating given)
- Pull quote: `<p class="press-quote">`
- Publication / production / date: `<p class="press-meta">`
- Review link: the `<a class="press-link">` — keep `target="_blank" rel="noopener"` on every link
- Grid is 2×2 on desktop and stacks to a single column on mobile (below 768px) automatically

---

### Block 6 — Contact + Mailing List

**Where:** Fifth Code Block.

```html
<section id="contact"> ... </section>
```

**Mailing list wiring:**
The form currently shows a success state on submit (placeholder behaviour).
To connect to a real service, replace the JS block inside the `form.addEventListener('submit', ...)` handler with your Mailchimp / ConvertKit / etc. embed or fetch call.

---

### Block 7 — Footer

**Where:** Settings → Advanced → Code Injection → Footer
Or: A Code Block at the bottom of the page.

```html
<footer> ... </footer>
```

Also paste the `<script>` block here if using Code Injection, or keep it at the end of Block 6.

---

## Quick edits reference

| What to change | Where in the HTML |
|---|---|
| Email address | `href="mailto:..."` in contact section |
| Google Maps link | Both `href="https://www.google.com/maps/search/..."` links |
| Hero tagline | `<p class="hero-tagline">` |
| About copy | `<p>` tags inside `.about-body` |
| An Act(Or?) body text | First `.production-card` → `<p class="production-body">` |
| The Nose body text | Second `.production-card` → `<p class="production-body">` |
| An Act(Or?) credit line | First `.production-card` → `<p class="production-credit">` |
| The Nose credit line | Second `.production-card` → `<p class="production-credit">` |
| Press review cards | `.press-grid` → each `<div class="press-card">` (stars, quote, meta, link) |
| Press section heading/label | `<h2 class="section-title">` and `<p class="section-label">` inside `#press` |
| Footer year | `&copy; 2026 Bassett Theatre...` in `<footer>` |
| Fonts | Change the Google Fonts `<link href="...">` URL |

---

## Fonts used

- **Cormorant Garamond** — headings, loglines, titles, press pull quotes (serif)
- **DM Sans** — body, labels, navigation (sans-serif)

Both loaded via Google Fonts CDN. No other external dependencies.

---

## Colour palette

| Variable | Hex | Used for |
|---|---|---|
| `--bg` | `#0c0b09` | Page background |
| `--bg-card` | `#141210` | Production cards, press cards |
| `--bg-section` | `#111009` | About / Press / Contact backgrounds |
| `--text` | `#f2ece0` | Primary text |
| `--text-muted` | `#8a7f6e` | Secondary / body text |
| `--gold` | `#c9a96e` | Accent, highlights, active states |
| `--gold-dim` | `#8a6f3e` | Subdued gold, borders, meta labels, credit lines |
| `--border` | `#2a2520` | Card borders, dividers |
