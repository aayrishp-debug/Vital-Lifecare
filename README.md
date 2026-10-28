# Vital Lifecare – Lifestyle & Behavior Dashboard (Emily Rodriguez)

An HTML page that embeds a Tableau Public dashboard, plus scripts to measure how quickly it loads.

**Dashboard:** [Vital Lifecare – Lifestyle and Behavior](https://public.tableau.com/views/VitalLifecare/LifestyleandBehaviorEmilyRodriguez)

---

## Project Structure

```
.
├── index.html        # Page embedding the Tableau dashboard (with in-page timing)
├── perf-test.js      # Automated repeated load test (Node + Playwright)
├── package.json
└── README.md
```

## Features

- Responsive embed of the Tableau Public dashboard using the Tableau Embedding API v3
- In-browser timing logged to the console when the viz becomes interactive
- Repeated load testing with average, min, max and P95 load times
- Optional Lighthouse audit for page-level performance

## Prerequisites

- A modern browser (Chrome, Edge, Firefox, Safari)
- [Node.js](https://nodejs.org/) 18 or later (for performance tests only)
- Internet access (the viz and Tableau's JS library load from `public.tableau.com`)

## Getting Started

### 1. View the dashboard

Serve the page locally, then open http://localhost:8080:

```bash
npx http-server -p 8080
```

### 2. Customize the embed

Edit these attributes on the `<tableau-viz>` tag in `index.html`:

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `src` | Dashboard URL | `https://public.tableau.com/views/VitalLifecare/LifestyleandBehaviorEmilyRodriguez` |
| `device` | Layout: `desktop`, `tablet`, `phone` | `desktop` |
| `toolbar` | Toolbar position: `top`, `bottom`, `hidden` | `bottom` |
| `hide-tabs` | Hides sheet tabs | (flag) |
| `height` / `width` | Embed size | `800` / `100%` |

## Performance Testing

### A. In-page timing

Open `index.html` with DevTools open (Console tab). When the viz loads, you'll see:

- Time to interactive in ms
- A table of Tableau network requests (duration and size)

### B. Automated load test

```bash
npm install
npx playwright install chromium
node perf-test.js
```

- Runs 10 loads (change `RUNS` in `perf-test.js`), each with a fresh browser context so nothing is cached
- Reports per-run load time, request count and
