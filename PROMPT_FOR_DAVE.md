# Rebuilding spottaildigital.com with Claude

Dave — this repo contains a rebuilt **homepage** for Spottail Digital. It's a single
self-contained `index.html` file, so there's no build step, no framework, and nothing
to install to work on it.

Below is everything you need to (1) get Claude running on your machine, (2) point it at
this homepage, and (3) have it build the rest of the site in the same style.

---

## Step 1 — Get set up (about 5 minutes)

You have two options:

**Option A — Claude Code (recommended).** This is the one that can actually edit files
and see the result. Install it, then in a terminal:

```bash
npm install -g @anthropic-ai/claude-code
```

Download this repo (green **Code** button → **Download ZIP**, then unzip it), open a
terminal in that folder, and run:

```bash
claude
```

**Option B — claude.ai in the browser.** Works fine for generating pages, but you'll be
copying and pasting files by hand. Fine for a quick look, slower for real work.

To preview the site locally at any point, run this in the project folder and open
<http://localhost:4173>:

```bash
python3 -m http.server 4173
```

---

## Step 2 — The main prompt

Paste everything between the lines into Claude. It's written to be self-contained —
you don't need to explain anything else first.

---

> I'm working on the website for **Spottail Digital**, an adtech company and a subsidiary
> of Cunningham Broadcasting Corporation. We sell a single dashboard that local advertisers
> and agencies use to plan, activate, measure, and report across Streaming TV / OTT, online
> video, audio, display, walled gardens, digital out of home, and now social and search
> keywords. The pitch is "one platform, every channel, simplified and localized."
>
> This folder already contains a finished homepage at `index.html`. **Read it first.** It
> defines the whole design system, and I want everything else to match it exactly.
>
> The design system, for reference:
>
> - **Colors** (CSS custom properties at the top of `index.html`): deep ink `#070C1E`,
>   navy `#101736`, indigo `#2E3B76`, brand blue `#4DAFE2`, lighter blue `#7FCBF0`,
>   `--brand-ink` `#1F6E9C` for brand-colored text on light backgrounds, warm accent
>   `#F0B775` used sparingly, off-white `#F4F7FB`, body text `#5A6784`.
> - **Type**: Inter Tight for headings (tight letter-spacing), Inter for body,
>   IBM Plex Mono for the small uppercase eyebrow labels.
> - **Rhythm**: alternating light and dark full-bleed sections, `1180px` max content
>   width, generous vertical padding, `16px`/`24px` corner radii, soft shadows.
> - **Motion**: subtle fade-and-rise on scroll via IntersectionObserver, and everything
>   is disabled under `prefers-reduced-motion`.
>
> **Please build these additional pages, each as its own self-contained HTML file in this
> folder, reusing the exact same header, footer, colors, type, and section patterns:**
>
> 1. `platform.html` — the full product story. Expand each of the five capabilities the
>    homepage only summarizes: forecasting, campaign activation, pacing, pixel management,
>    and reporting. One substantial section each, with a purpose-built diagram or UI mock
>    in inline SVG/CSS (no stock photos, no fake screenshots).
> 2. `about.html` — the Cunningham Broadcasting story and the full leadership team.
> 3. `contact.html` — a proper "build my dashboard" page with the request form and what
>    happens after someone submits.
>
> **Rules I care about:**
>
> - Keep every page a single self-contained HTML file. No build step, no framework, no npm.
>   It has to keep working on GitHub Pages as plain static files.
> - **Do not invent statistics, client names, case studies, testimonials, or pricing.**
>   If a page needs a number I haven't given you, leave a clearly marked `TODO` instead
>   of making one up. The only hard figures we have are: 20 television stations,
>   18 markets, 20+ years in broadcast, and "hundreds of thousands of audience segments."
> - Every page must work at 375px wide and pass WCAG AA contrast (4.5:1 for normal text).
> - Update the nav on every page, including the homepage, so the links point at the real
>   pages instead of `#` anchors.
>
> Start by reading `index.html`, then tell me your plan before you write any new files.

---

## Step 3 — Useful follow-up prompts

Once the first pass exists, these are the prompts that actually improve it:

- `Show me the site running locally and take a screenshot of each page at desktop and mobile width.`
- `The hero copy is too generic. Give me five alternative headlines that lead with what a local advertiser actually gets.`
- `Swap the placeholder team initials for real headshots — here are the image files.`
- `Connect the contact form to Formspree and walk me through getting the endpoint.`
- `Run an accessibility pass on every page and fix anything that fails WCAG AA.`
- `Add a simple Resources section I can drop one-pagers and case studies into later.`

---

## Step 4 — Things worth knowing

**The contact form isn't connected to anything yet.** It validates input and then tells
the visitor it's a demo. To make it live, open `index.html`, find `FORM_ENDPOINT` near the
top of the `<script>` block, and paste in an endpoint from [Formspree](https://formspree.io)
(free tier is fine), HubSpot, or whatever your team already uses. It will then POST the
form and show a proper success message.

**The dashboard visual in the hero is illustrative, and it says so on the card.** The
numbers in it are made up for demonstration. If you'd rather show the real product, swap
it for an actual screenshot — but keep the label honest either way.

**All of the copy came from your current site**, lightly tightened. The leadership bios,
the four pillars, the five platform capabilities, the key features, and the Cunningham
paragraph are all yours. I fixed one typo along the way — "tailed publisher lists" is now
"tailored publisher lists."

**Anything Claude writes is a draft, not a fact.** It's very good at structure, layout, and
polish, and it will confidently invent a statistic if you let it. Marketing claims, client
names, and numbers should come from you.
