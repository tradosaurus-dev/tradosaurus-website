# Tradosaurus Marketing Website

A static, framework-free marketing site for the Tradosaurus desktop trading app.
No build step. No JavaScript framework. No tracking. Just HTML + CSS + a sprinkle of vanilla JS.

## Files

```
website/
├── index.html        — Long-scroll landing page (hero, numbers, features, tour, pricing, FAQ)
├── download.html     — Download landing with SmartScreen warning + first 5 minutes guide
├── disclaimer.html   — SEBI compliance disclaimer
├── privacy.html      — Privacy policy (no tracking, minimal data collection)
├── refund.html       — 7-day refund policy
├── terms.html        — Terms of service
├── styles.css        — Single stylesheet with full design system
├── images/           — Drop your real GUI screenshots here (see below)
└── README.md         — This file
```

## Five things you MUST do before going live

1. **Drop in real screenshots.** Put your GUI tab screenshots into `images/` with these exact filenames:
   - `screenshot-universe.png`
   - `screenshot-screener.png`
   - `screenshot-backtest.png`
   - `screenshot-summary.png` *(use the version with the new metric cards — Final Equity, CAGR)*
   - `screenshot-builder.png`
   
   The site is built to gracefully degrade — if any image is missing it shows a "[Screenshot · Tab Name]" placeholder. So you can ship without all five and add the rest later. But before launch, all five should be real.

2. **Replace the Razorpay placeholder.** In `index.html`, find:
   ```html
   <div class="razorpay-slot" id="razorpay-button-placeholder">
       RAZORPAY_BUTTON_PLACEHOLDER ...
   </div>
   ```
   Replace this entire `<div>` with your Razorpay Payment Button embed code (you get this from the Razorpay dashboard once your business KYC is complete).

3. **Replace `YOUR_USERNAME`** in `download.html`. Find:
   ```
   https://github.com/YOUR_USERNAME/swing-trading-website/releases/...
   ```
   Replace `YOUR_USERNAME` with your actual GitHub handle. The .exe gets uploaded as a GitHub Release asset.

4. **Pick a real brand name (or keep "Tradosaurus").** I used "Tradosaurus" throughout. If you want a different name, do a project-wide search-and-replace for "Tradosaurus" → "YourName". Also replace `support@tradosaurus.in` with your real support email.

5. **Add real testimonials when you have them.** The "Trusted by early users" section currently shows an honest "coming soon" placeholder. **Do not fabricate testimonials** — once you have 2–3 real paying users who give you written reviews, replace the placeholder card in `index.html` with their real quotes (with names and permission). Until then, leave it as-is.

## Deploying to Vercel

```
1. Create a new GitHub repo, push these files
2. Go to vercel.com, click "Add New Project", connect the repo
3. Framework preset: "Other" (no build command, no output directory)
4. Click Deploy. Vercel auto-detects it's a static site.
5. Add your custom domain in Vercel → Settings → Domains
```

That's it. Auto-deploys on every push to `main`.

## Hosting the .exe

The download button on `download.html` points to a GitHub Releases asset URL. To host your .exe:

```
1. In your GitHub repo, go to Releases → "Draft a new release"
2. Tag: v0.1.0
3. Title: "Tradosaurus 0.1.0"
4. Attach your built Tradosaurus-Windows.zip as a release asset
5. Publish release
```

The download URL in `download.html` is already in the right format:
`github.com/USER/REPO/releases/latest/download/Tradosaurus-Windows.zip`

`/releases/latest/download/` always points to the most recent release, so you never have to update the link when you ship a new version.

## What's deliberately NOT in this website

- **No fake testimonials.** Fabricated user reviews are fraud and risk your Razorpay account. The placeholder section says so honestly.
- **No fake user counts.** No "10,000 traders trust us" claims. We don't have 10,000 traders yet.
- **No stock photos of dashboards.** Only your real product screenshots.
- **No tracking, no analytics, no cookies.** Clean. Use server-side log review if you want visit counts.
- **No "AI-powered", "revolutionary", "game-changing" buzzwords.** This isn't that kind of product.
- **No file inventory exposing your Python source.** The old site had a section listing `gui_app.py`, `backtester.py` etc. — that's gone, customers get the .exe.

## Design system summary

- **Aesthetic direction:** Editorial financial — Financial Times meets Bloomberg Terminal
- **Background:** Warm cream `#F5F1E8`, not stark white. Reads like newsprint.
- **Type:** Fraunces (display, free Google Font, optical sizing) + Inter (body) + JetBrains Mono (numbers and labels)
- **Accent:** Deep emerald `#1A6E3A`. Single accent color, used sparingly. No purple gradients.
- **Numbers:** Tabular monospace everywhere. Financial products live and die by aligned numbers.
- **Motion:** Reveal-on-scroll, animated counters, FAQ accordion. No bouncing, no parallax, no jank.

If you want to change the brand color, update `--accent` and `--accent-bright` in `styles.css`. Everything else cascades from those tokens.

## Local preview

```bash
cd website
python3 -m http.server 8000
# open http://localhost:8000
```
