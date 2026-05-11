# VaultPath — Finance Career Platform

> The all-in-one finance career platform for students and professionals pursuing investment banking, private equity, asset management, fintech, and beyond.

**Live Demo:** [https://vaultpath-app.surge.sh](https://vaultpath-app.surge.sh)

---

## What Is VaultPath?

VaultPath is a fully functional, single-page web application that serves as a complete finance recruiting command center. It was built for students and early-career professionals navigating competitive finance job applications.

---

## Features

| Tab | What It Does |
|-----|-------------|
| **Overview** | Landing page explaining the platform and its tools |
| **Resume Review** | Upload or paste a resume → get an AI-style score (0–100), strengths, gaps, keyword analysis, ATS feedback, and download/copy options |
| **Interview Prep** | Generate 12–15 tailored interview questions from your resume + job description. Includes behavioral, technical finance, accounting, valuation, market awareness, and fit questions — each with a model answer and answer practice area with feedback |
| **Technical Practice** | Dedicated technical drill mode: type your answer first, then reveal the correct answer. Comparison shows what you got right vs. missed. Progress tracked across sessions |
| **Job Portal** | Browse 27+ curated finance jobs (Goldman, Blackstone, KKR, Citadel, Stripe, Two Sigma, etc.) with search, 5 filter dimensions, save-to-tracker, and one-click apply |
| **Application Tracker** | Full recruiting dashboard: add jobs manually or from the board, track status (Interested → Offer), edit/delete entries, export to CSV. All data persists in localStorage |
| **News & Events** | Live finance news via RSS (Reuters, MarketWatch, CNBC, Yahoo Finance) + 17 curated seed articles. Sorted newest-first. Role-based personalisation filter (IB, PE, AM, Macro, etc.) |
| **Cover Letter** | Generate a finance-specific cover letter from scratch (company, role, resume, JD, tone) or revise an existing one. Quick-action buttons: shorter, more formal, finance-specific, more confident |
| **Networking Tracker** | Track every finance contact with 15 fields, auto-compute follow-up dates (60 days after last conversation), highlight overdue contacts. Built-in message generator for LinkedIn requests, cold emails, follow-ups, thank-yous, referral requests |
| **Sign Up / Log In** | Full auth flow with account creation, password strength meter, localStorage persistence, user avatar in nav, and sign-out |

---

## Tech Stack

This is a **zero-dependency, single-file web application** — no npm, no build step, no framework required.

- **HTML5** — semantic structure
- **CSS3** — custom design system with CSS variables, flexbox, grid, animations
- **Vanilla JavaScript** — all logic, state management, localStorage persistence
- **Google Fonts** — Inter typeface
- **rss2json API** — free CORS proxy for live RSS news feeds

Everything runs directly in the browser. No server required.

---

## Running Locally

### Option 1 — Open directly (simplest)
```bash
# Just open index.html in any modern browser
open index.html          # macOS
start index.html         # Windows
xdg-open index.html     # Linux
```

### Option 2 — Local server (recommended, avoids any CORS quirks)
```bash
# Python 3
python3 -m http.server 8080
# Then visit: http://localhost:8080

# Node.js (npx)
npx serve .
# Then visit: http://localhost:3000
```

No installation, no `npm install`, no build step.

---

## Deploying

### GitHub Pages (recommended — free, permanent)

1. Push this repository to GitHub
2. Go to **Settings → Pages**
3. Set **Source** to `Deploy from a branch`
4. Set **Branch** to `main` and folder to `/ (root)`
5. Click **Save**
6. Your site will be live at `https://YOUR-USERNAME.github.io/vaultpath/`

The included GitHub Actions workflow (`.github/workflows/pages.yml`) will auto-deploy on every push to `main`.

### Netlify (30 seconds, no account required)
1. Go to [netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop `index.html` onto the page
3. Get a permanent public URL instantly

### Vercel
```bash
npx vercel --prod
# Follow the prompts
```

### surge.sh
```bash
npm install -g surge
surge . vaultpath-finance.surge.sh
```

---

## Project Structure

```
vaultpath/
├── index.html              # Complete self-contained app (HTML + CSS + JS)
├── README.md               # This file
└── .github/
    └── workflows/
        └── pages.yml       # GitHub Pages auto-deploy workflow
```

---

## Key Technical Details

### State & Persistence
All user data (applications, networking contacts, auth session, tech practice progress, news cache) is stored in `localStorage` under these keys:

| Key | Contents |
|-----|----------|
| `vp_app_tracker` | Job applications (title, company, status, dates, notes) |
| `vp_net_contacts` | Networking contacts (15 fields each) |
| `vp_accounts` | User accounts (email, hashed password, profile) |
| `vp_current_user` | Active session |
| `vp_tech_session` | Technical practice progress (score, history) |
| `vp_news_cache2` | Cached live news articles (24h TTL) |

### Resume Scoring
Rule-based scoring across 5 dimensions: section completeness (22pts), quantification (24pts), action verbs (18pts), role-specific keywords (24pts), word count (12pts). Keywords are tailored per role (IB, PE, AM, Corporate Finance, Fintech, Accounting, Financial Analyst).

### Live News
Fetches from Reuters Business, MarketWatch, CNBC Economy, and Yahoo Finance via the free [rss2json.com](https://rss2json.com) API. Results cached in localStorage for 24 hours. Falls back to 17 curated seed articles if RSS is unavailable.

---

## Browser Compatibility

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires JavaScript enabled. No IE11 support.

---

## License

MIT License — free to use, modify, and deploy for personal or educational purposes.

---

*Built with VaultPath — your finance career command center.*
