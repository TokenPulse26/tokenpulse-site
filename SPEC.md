# TokenPulse Landing Page — Build Spec

## Overview
Build a single-page static landing page for **TokenPulse** (tokenpulse.to) — a local-first AI usage tracking proxy + dashboard. This is a marketing/product page, not the app itself.

**Tech:** Static HTML + CSS + minimal vanilla JS (no frameworks, no build step). Must work deployed to GitHub Pages.

**Repo:** This repo (`TokenPulse26/tokenpulse-site`). The `main` branch deploys via GitHub Pages.

---

## Design Direction

- **Dark theme** — dark background (#0a0a0a or #0f0f0f), matching the dashboard's dark aesthetic
- **Accent color:** Teal/cyan (#00d4aa or similar green-teal) — matches the dashboard's green accent
- **Typography:** Inter (Google Fonts) or system sans-serif stack
- **Feel:** Clean, developer-focused, minimal. Think Helicone.ai or Supabase landing page energy — not SaaS enterprise, not indie hacker sloppy
- **Mobile responsive** but desktop-first (audience is developers and power users)
- **Fast loading** — no heavy JS, no animations that delay content paint
- **Single `index.html` file** with inline or linked CSS. Keep it simple.

---

## Page Sections (Top to Bottom)

### 1. HERO
- **Nav bar** at top: TokenPulse logo/wordmark (left), links: Features | How It Works | GitHub (right), with a "Get Started" CTA button
- **Headline:** "See every AI token you spend."
- **Subheadline:** "One dashboard for OpenAI, Anthropic, Google, Ollama, and more. Runs locally. Your data never leaves your machine."
- **Two CTA buttons:** "Get Started →" (links to #getting-started or GitHub README) + "View on GitHub" (links to https://github.com/TokenPulse26/TokenPulse)
- **Hero visual:** A stylized version of the proxy flow diagram:
  ```
  Your AI Tools → TokenPulse Proxy → AI Providers
                       ↓
                 Local Dashboard
  ```
  Make this an SVG or CSS-drawn diagram with subtle animation (dots flowing through the pipeline). Keep it lightweight.

### 2. THE PROBLEM (short, punchy)
- Section title: "The problem with AI spending"
- Three cards in a row:
  - 🔀 **Scattered billing** — "Juggling 4+ provider dashboards to understand what you're spending"
  - 🔒 **Invisible local usage** — "Running Ollama and LM Studio with zero visibility into what they're doing"  
  - 📊 **No single view** — "No way to compare cloud costs vs local performance in one place"

### 3. HOW IT WORKS
- Section title: "Three steps. Five minutes."
- Three numbered steps with icons:
  1. **Point your tools at TokenPulse** — "Change one environment variable. That's it."
     ```
     export OPENAI_BASE_URL=http://localhost:4100
     ```
  2. **TokenPulse intercepts and logs** — "Every request flows through the proxy. Usage metadata is stored locally in SQLite."
  3. **Open your dashboard** — "Real-time spend, model breakdowns, budgets, and optimization signals at localhost:4200"

### 4. DASHBOARD SHOWCASE (the money section)
- Section title: "Your AI command center"
- Display the dashboard screenshots in a visually appealing way:
  - Use the screenshots in `screenshots/` directory (move them there from root)
  - Show them in a stacked/overlapping card layout or a horizontal scroll/carousel
  - Add subtle shadow and rounded corners to make them look like app windows
  - The screenshots are: `dashboard-full.png` (hero view with live stats), `dashboard-mid.png` (charts/breakdowns), `dashboard-bottom.png` (more analytics), `dashboard-budget.png` (budget section), `dashboard-optimizer.png` (cost optimization), `dashboard-heatmap.png` (activity heatmap)
  - Pick the 3-4 best ones to feature prominently. `dashboard-full.png` and `dashboard-mid.png` are likely the best heroes.

### 5. FEATURES GRID
- Section title: "Built for power users"
- 2x4 grid of feature cards:
  1. 🔌 **8 Providers** — "OpenAI, Anthropic, Google, Mistral, Groq, Ollama, LM Studio, CLIProxy — all through one proxy"
  2. 💰 **Real-time cost tracking** — "Per-request token counts and cost calculation as requests flow through"
  3. 📈 **Budget alerts** — "Set spending limits, get notified before you blow through them"
  4. 🏠 **100% local** — "SQLite database on your machine. No account, no cloud, no data sharing"
  5. ⚡ **Streaming support** — "Full SSE streaming passthrough with live token counting"
  6. 🔍 **Cost optimizer** — "Detects model misuse and suggests cheaper alternatives that fit"
  7. 📊 **Forecasting** — "Monthly spend projections based on your actual usage patterns"
  8. 📤 **CSV export** — "Export everything for spreadsheets, reports, or your own analysis"

### 6. COMPARISON TABLE
- Section title: "How TokenPulse compares"
- Clean table:

| Feature | TokenPulse | Helicone | LiteLLM | CostGoat |
|---------|-----------|----------|---------|----------|
| Local model tracking | ✅ | ❌ | Partial | ❌ |
| Real-time proxy | ✅ | ✅ | ✅ | ❌ (polls) |
| 100% self-hosted | ✅ | ✅ (OSS) | ✅ (OSS) | ❌ |
| No account required | ✅ | ❌ | ❌ | ❌ |
| Data stays local | ✅ | ❌ | ❌ | ✅ |
| Price | Free | Free-$500/mo | Free | $9/mo |

### 7. GETTING STARTED
- Section title: "Up and running in 5 minutes"  
- Code block showing quick start:
  ```bash
  git clone https://github.com/TokenPulse26/TokenPulse.git
  cd TokenPulse/src-tauri && cargo build --release && cd ..
  python3 web-dashboard.py
  # Open http://localhost:4200
  ```
- Link to full Getting Started guide on GitHub
- Supported platforms: macOS, Linux (icons)

### 8. FOOTER
- TokenPulse wordmark
- Links: GitHub | Getting Started | Changelog
- "Built by New Age Investments"
- MIT License badge
- © 2026

---

## File Structure

```
/
├── index.html          # The entire landing page
├── style.css           # Styles (or inline in HTML)
├── screenshots/        # Dashboard screenshots
│   ├── dashboard-full.png
│   ├── dashboard-mid.png
│   ├── dashboard-bottom.png
│   ├── dashboard-budget.png
│   ├── dashboard-optimizer.png
│   └── dashboard-heatmap.png
├── CNAME               # Contains: tokenpulse.to
└── README.md           # Repo readme
```

---

## Important Notes

1. **Move the screenshot PNGs** from the repo root into a `screenshots/` directory and reference them from there
2. **Create a `CNAME` file** containing just `tokenpulse.to` (needed for GitHub Pages custom domain)
3. **Keep total page weight under 2MB** — optimize screenshot display (use CSS to control rendered size, consider lazy loading for below-fold images)
4. **Smooth scroll** for nav anchor links
5. **Sticky nav** that gets a slight background blur on scroll
6. **No external JS dependencies** — vanilla only
7. The page should look polished and professional. This is a real product with 27,000+ requests tracked. It should feel like it.
8. **GitHub repo link:** https://github.com/TokenPulse26/TokenPulse
9. **Website domain:** tokenpulse.to

---

## What NOT to include
- No pricing page (it's free/OSS for now)
- No signup form or email capture (not yet)
- No blog section
- No testimonials (we don't have any yet)
- No fake metrics or inflated claims
