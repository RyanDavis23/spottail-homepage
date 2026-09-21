# Rebuilding the Spottail site with Claude — start here

Dave — this is everything you need, in order. No coding required, and no terminal.
Budget about 15 minutes for setup, then you can iterate on the site for as long as you like.

**The live rebuilt homepage:** <https://ryandavis23.github.io/spottail-homepage/>

---

## Part 1 — Get Claude on your computer (5 minutes)

You need the **Claude desktop app**, not the website. The website can write code but can't
save files onto your machine — the desktop app can, and that's the whole trick.

1. Go to **<https://claude.ai/download>** and download the Mac or Windows app.
2. Install it and sign in. You'll need a **Claude Pro or Max** subscription for this kind
   of work — the free tier will run out partway through a website.
3. Open the app. In the left sidebar, look for the **Code** tab. That's the one that can
   read and write files in a folder. Click it.

That's the whole setup. If you can find the Code tab, you're ready.

---

## Part 2 — Get the files (3 minutes)

1. Go to **<https://github.com/RyanDavis23/spottail-homepage>**
2. Click the green **Code** button near the top right.
3. Choose **Download ZIP**.
4. Find the ZIP in your Downloads, double-click to unzip it, and drag the resulting
   folder onto your **Desktop**. Rename it to `spottail` to keep things simple.

You now have a folder on your Desktop called `spottail` with the rebuilt homepage inside.

> **Want to see it right now?** Open the `spottail` folder and double-click `index.html`.
> It opens in your browser. That's the whole website — one file.

---

## Part 3 — Point Claude at the folder

1. In the Claude desktop app, on the **Code** tab, start a new session.
2. It will ask which folder you want to work in. Choose the `spottail` folder on your Desktop.
3. Now paste the prompt in Part 4 and hit enter.

---

## Part 4 — The prompt

Copy everything in the grey box below and paste it into Claude as your first message.

```
I'm the CRO of Spottail Digital, an adtech company and a subsidiary of Cunningham
Broadcasting Corporation. We sell a single dashboard that local advertisers and
agencies use to plan, activate, measure, and report across Streaming TV / OTT,
online video, audio, display, walled gardens, digital out of home, and now social
and search keywords. Our pitch is "one platform, every channel, simplified and
localized."

This folder contains a rebuilt homepage at index.html. Please read that file first —
it defines the design system (colors, fonts, spacing, section patterns) and I want
everything else on the site to match it exactly.

Please build these three additional pages, each as its own self-contained HTML file
in this folder, reusing the exact same header, footer, colors, and type:

1. platform.html — the full product story. Expand each of the five capabilities the
   homepage only summarizes: forecasting, campaign activation, pacing, pixel
   management, and reporting. Give each one a real section with a diagram or UI mock
   drawn in code — no stock photos.
2. about.html — the Cunningham Broadcasting story and the full leadership team.
3. contact.html — a "build my dashboard" page with the request form, and a clear
   explanation of what happens after someone submits it.

Rules that matter to me:

- Keep every page a single self-contained HTML file. No build step, no framework,
  nothing to install. It has to keep working as plain files I can open by
  double-clicking.
- Do NOT invent statistics, client names, case studies, testimonials, or pricing.
  If a page needs a number I haven't given you, put a clearly marked TODO instead of
  making one up. The only real figures we have are: 20 television stations,
  18 markets, 20+ years in broadcast, and "hundreds of thousands of audience segments."
- Every page has to look right on a phone and meet WCAG AA contrast standards.
- Update the navigation on all pages, including the homepage, so the links point at
  the real pages instead of placeholder anchors.

Start by reading index.html, then tell me your plan before you write any new files.
When you're done, show me screenshots of each page at desktop and phone width.
```

---

## Part 5 — Good follow-up prompts

Once it's built the first version, this is where the real improvement happens. Just type
these in plain English — you don't need special syntax.

- `Show me the site and take screenshots of every page on desktop and on a phone.`
- `The homepage headline is too generic. Give me five alternatives that lead with what a local advertiser actually gets out of this.`
- `Make the platform page feel less like a brochure and more like a product tour.`
- `Here are headshots for the leadership team — use these instead of the initials.`
  (then drag the image files into the chat)
- `Connect the contact form to a real inbox and walk me through it step by step.`
- `I don't like the blue on the pricing cards. Show me three other options.`
- `Check every page for accessibility problems and fix them.`

**The single most useful habit:** when you don't like something, say what bothers you in
plain words and ask for options rather than one fix. "This section feels cluttered, show
me three ways to simplify it" gets you much further than "fix this section."

---

## Part 6 — Putting it online so people can see it

When you're happy with it, here's how to get a public link. This is the fiddliest part,
so the easiest path is simply to **ask Claude to do it for you**:

```
Publish this site to GitHub Pages under my account and give me the link.
Walk me through anything you need me to click.
```

If you'd rather do it by hand:

1. Make a free account at **<https://github.com>** if you don't have one.
2. Click the **+** in the top right → **New repository**. Name it `spottail-site`,
   set it to **Public**, and click **Create repository**.
3. On the next screen click **uploading an existing file**, then drag in every file from
   your `spottail` folder. Click **Commit changes**.
4. Go to the **Settings** tab → **Pages** in the left sidebar.
5. Under **Source**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and click **Save**.
6. Wait two or three minutes, then refresh. Your link appears at the top of that page.

To point **spottaildigital.com** itself at the new site, that's a DNS change your IT or
hosting provider handles — worth doing only once you're genuinely happy with it.

---

## A few honest caveats

**The contact form doesn't go anywhere yet.** It checks that the email looks valid and
then tells the visitor it's a demo — it never pretends to have sent something. Ask Claude
`connect the contact form to a real inbox` when you want it live.

**The dashboard graphic on the homepage is illustrative, and the card says so.** Those
numbers are invented for the demo. If you'd rather show the real product, swap in an
actual screenshot.

**All the writing came from your current site**, lightly tightened. The leadership bios,
the four pillars, the five platform tools, and the Cunningham paragraph are yours. One
typo got fixed along the way: "tailed publisher lists" is now "tailored publisher lists."

**Claude will confidently make up a statistic if you let it.** It's excellent at layout,
structure, and polish. It is not a source of truth about your business. Any number, client
name, or marketing claim on the finished site should come from you — which is why the
prompt above explicitly tells it to write TODO instead of guessing.

**Nothing you do here can break the real spottaildigital.com.** You're working on files on
your own computer. The live site is untouched until somebody deliberately repoints the domain.
