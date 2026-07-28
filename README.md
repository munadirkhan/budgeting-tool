# Cost of Eating

Personal food-and-money tracker for a year off residence at Western. Single HTML file,
no build step, no dependencies. State lives in `localStorage`.

## The starting numbers

| Line | Monthly |
|---|---|
| Rent | $950 |
| Utilities | $50 |
| Phone | $45 |
| Household + toiletries | $25 |
| Eating out | $60 |
| **Groceries** | **$450** |
| **All-in** | **$1,580** |

Default basket comes out to **$426/month**, delivering **~187 g protein** and
**~2,376 kcal per day** — a ~500 kcal deficit, roughly 1 lb/week, 220 → 185 lb by around May.
Everything is editable and recalculates live.

## Tabs

- **Eat** — tap `+` on a food to log a serving. Running protein / kcal / dollars for the day.
  `‹` `›` moves between days.
- **Shop** — the weekly basket. Quantities drive the monthly grocery budget *and* the daily
  macros, so you can see what a change costs in both currencies. Tap any price to correct it.
  Checkboxes are for the actual store run.
- **Spend** — fixed costs, grocery budget burn-down, safe-to-spend per day for the rest of
  the month, and a log of each shop.
- **Weight** — weigh-in log, trend chart with a dashed 185 lb line, 7-day average, actual
  lb/week rate, and a projected finish date based on that real rate rather than the plan.

## Run it

Open `index.html` in a browser. That's it.

## Deploy

```bash
vercel --prod
```

From Safari on iPhone: Share → Add to Home Screen. It opens fullscreen without the browser chrome.

## Data

`localStorage` is per-device and per-browser. **Weight → Export backup** writes a JSON file;
**Import** restores it. Do that before clearing Safari data or switching phones.

To make it multi-device, move state to Supabase — one `entries` table with
`date`, `type`, `payload jsonb` covers all four tabs.
