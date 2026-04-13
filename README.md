# Marketing Campaign ROI Simulator

A fully client-side A/B/C testing simulator for marketing teams. No backend, no dependencies to install — just open the HTML file in a browser.

<img width="3072" height="1656" alt="campaign-roi-results" src="https://github.com/user-attachments/assets/961ba0ca-e654-4ad1-a7fd-6bf074afda98" />

---

## Features

- **Three-variant A/B/C testing** — configure control (A) and two challenger variants (B, C) independently
- **Real-time statistics** — p-value, statistical power, and minimum sample size recalculate on every slider change
- **ROI calculations** — expected revenue, return on investment, and conversion lift per variant
- **Side-by-side charts** — revenue comparison, baseline vs. lifted conversion rates, statistical power gauge, and budget vs. revenue return
- **CSV import** — load campaign settings from a structured CSV file; a sample file is included
- **Export results** — download the results panel as a PNG image or PDF report via jsPDF + html2canvas

---

## Getting Started

No build step required. Everything runs in the browser.

```bash
git clone https://github.com/your-org/marketing-roi-simulator.git
cd marketing-roi-simulator
open index.html
```

Or just drag `index.html` into any browser window.

---

## CSV Import Format

Upload a CSV with three columns — `setting`, `variant`, and `value` — to populate all sliders at once.

```csv
setting,variant,value
budget,global,75000
sample_size,global,15000
baseline_conversion,global,3.5
revenue_per_conversion,global,150
budget_allocation,a,30
conversion_lift,a,0
cost_per_click,a,1.50
click_through_rate,a,2.2
budget_allocation,b,35
conversion_lift,b,22
cost_per_click,b,2.10
click_through_rate,b,3.4
budget_allocation,c,35
conversion_lift,c,45
cost_per_click,c,2.80
click_through_rate,c,4.1
```

A ready-to-use `sample_campaign_data.csv` is included in the repo. You can also download it directly from within the app.

### Supported settings

| `setting` | `variant` | Description |
|---|---|---|
| `budget` | `global` | Total campaign budget ($) |
| `sample_size` | `global` | Total users in the test |
| `baseline_conversion` | `global` | Control conversion rate (%) |
| `revenue_per_conversion` | `global` | Average revenue per conversion ($) |
| `budget_allocation` | `a` / `b` / `c` | Share of total budget (%) |
| `conversion_lift` | `a` / `b` / `c` | Expected lift over baseline (%) |
| `cost_per_click` | `a` / `b` / `c` | CPC for this variant ($) |
| `click_through_rate` | `a` / `b` / `c` | CTR for this variant (%) |

---

## Statistics Reference

| Metric | Method |
|---|---|
| **p-value** | Two-proportion z-test comparing variant vs. control |
| **Statistical power** | Normal CDF approximation at α = 0.05 |
| **Min. sample size** | Derived from desired 80% power, α = 0.05 |
| **Significance threshold** | p < 0.05 |

Power is colour-coded in the chart: green ≥ 80%, amber ≥ 50%, red below 50%.

---

## File Structure

```
marketing-roi-simulator/
├── index.html               # Self-contained app (HTML + CSS + JS)
├── sample_campaign_data.csv # Example CSV to test the import feature
└── README.md
```

---

## Dependencies

All loaded from CDN at runtime — no npm install needed.

| Library | Version | Purpose |
|---|---|---|
| [Chart.js](https://www.chartjs.org) | 4.4.1 | All four result charts |
| [jsPDF](https://github.com/parallax/jsPDF) | 2.5.1 | PDF export |
| [html2canvas](https://html2canvas.hertzen.com) | 1.4.1 | PNG + PDF canvas capture |

---

## Exporting Results

Click **Export as PNG** or **Export as PDF** in the results panel to download a snapshot of the full results card including all four charts and the comparison table.

---

## License

MIT
