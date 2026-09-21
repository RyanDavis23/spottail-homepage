# Spottail Digital — homepage rebuild

A rebuilt homepage for [spottaildigital.com](https://spottaildigital.com), built as a
single self-contained static page.

**Live preview:** <https://ryandavis23.github.io/spottail-homepage/>

If you're Dave and you want to extend this, start with **[PROMPT_FOR_DAVE.md](PROMPT_FOR_DAVE.md)** —
it has a copy-paste prompt for building the rest of the site in this same style.

---

## What's here

```
index.html                  the entire homepage — markup, styles, and scripts
assets/spottail-logo.png    full logo lockup (white wordmark, for dark backgrounds)
assets/spottail-mark.png    the tail mark on its own, used as the nav icon and favicon
PROMPT_FOR_DAVE.md          how to continue this with Claude
```

No build step, no dependencies, no framework. It's one HTML file and two images.

## Running it locally

```bash
python3 -m http.server 4173
```

Then open <http://localhost:4173>. (Open `index.html` directly and it'll mostly work, but
serving it over HTTP is closer to production.)

## Deploying

It's plain static files, so anything works — GitHub Pages, Netlify, Cloudflare Pages, or
dropping the folder onto existing hosting. For GitHub Pages: **Settings → Pages → Deploy
from a branch → `main` / `(root)`**.

## Connecting the contact form

The form validates input but isn't wired to an inbox. To make it live, open `index.html`,
find `FORM_ENDPOINT` near the top of the `<script>` block, and set it:

```js
var FORM_ENDPOINT = "https://formspree.io/f/your-id-here";
```

It'll POST the form data and show a success message. Leave it empty and the form tells the
visitor it's a demo — it never silently pretends to send.

## How this was built

Content, brand palette, and structure all came from the live spottaildigital.com:

- **Colors** were sampled from the running site — navy `#141A39`, indigo `#2E3B76`, and
  brand blue `#4DAFE2` are theirs.
- **Copy** is their own, lightly tightened. The four pillars, five platform capabilities,
  six key features, leadership bios, and the Cunningham Broadcasting paragraph are
  unchanged in substance. One typo fixed: "tailed publisher lists" → "tailored publisher lists."
- **Logo** assets were pulled from the live site. `spottail-mark.png` is the tail mark
  cropped out of the full lockup so it can sit on any background.

What changed is the execution: a real type system instead of all-caps Roboto, an original
dashboard visual built in CSS and SVG instead of stock photography, a tabbed walkthrough of
the five platform tools, and a responsive, accessible layout.

### Deliberate choices worth knowing

- **The hero dashboard is illustrative and labeled as such.** Its numbers are invented for
  demonstration, and the card says so rather than implying it's live campaign data.
- **No client logos.** The current site shows Fox News, NFL, and NBA marks. Those are
  inventory brands rather than Spottail customers, so reproducing them here risked implying
  an endorsement. Premium supply is described in words instead.
- **No invented statistics.** Every figure on the page traces back to Spottail's own copy:
  20 stations, 18 markets, 20+ years, and "hundreds of thousands of audience segments."
- **Team avatars are initials**, because there are no headshots on the current site.

### Accessibility

Semantic landmarks, one `h1` with no skipped heading levels, labeled form fields, visible
focus rings, keyboard-navigable tabs (arrow keys, Home/End), and `prefers-reduced-motion`
honored throughout. All body text meets WCAG AA contrast (4.5:1). Scroll reveals only
activate once JavaScript confirms it's running, so the page can never render blank.
