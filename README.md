# CashParkFinder

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-222?logo=github)](https://jacopo-monti.github.io/cash-park-finder/)

A browser-based, tax-aware comparison tool for Italian monetary ETFs vs fixed-term deposit accounts — runs entirely in your browser, no installation required.

🔗 **[Open the app](https://jacopo-monti.github.io/cash-park-finder/)**

---

## ⚠️ Disclaimer

**THIS SOFTWARE DOES NOT PROVIDE FINANCIAL, INVESTMENT, TAX, OR LEGAL ADVICE.**

This is a mathematical simulation tool only. It:

- ✅ Computes projected capital growth for monetary ETFs and fixed deposit accounts over time
- ✅ Accounts for Italian capital gains taxation, TER costs, and *imposta di bollo*
- ✅ Fetches the live €STR rate from the ECB public API
- ❌ Does NOT predict future interest rates or ETF performance
- ❌ Does NOT optimize returns or portfolio allocation
- ❌ Does NOT recommend which instrument to choose

**All investment decisions are entirely your own responsibility. Consult qualified professionals for personalized advice.**

---

## ✨ Features

- **No installation** — single HTML file, runs in any modern browser
- **No server, no data upload** — all calculations happen locally in JavaScript
- **Live €STR rate** — fetched automatically from the ECB Data Portal API on page load
- **Tax-aware** — applies the correct Italian tax rate per instrument (12.5% or 26%) and *imposta di bollo*
- **Whitelist links** — each ETF card links directly to the official whitelist source for tax verification
- **Gross / Net toggle** — switch between pre-tax and after-tax views instantly
- **Scenario simulation** — model flat, rising, or falling €STR rate trajectories
- **Interactive ETF cards** — toggle each instrument on/off; each card shows real-time yield estimate and projected capital
- **Fully configurable** — initial capital, deposit rate, lock-in duration, tax rate, *bollo*

---

## 🚀 Usage

Just open [`index.html`](index.html) in a browser, or visit the hosted version at:

**[https://jacopo-monti.github.io/cash-park-finder/](https://jacopo-monti.github.io/cash-park-finder/)**

### How it works

**Sidebar — left panel**

Set your initial capital and configure the fixed deposit parameters (rate, duration, tax rate, *imposta di bollo*). A summary card shows the projected net outcome of the deposit at lock-in expiry.

**Chart — top of main area**

The line chart shows capital evolution year by year for all active instruments. Use the Netto/Lordo toggle above the chart to switch views.

**ETF cards — bottom panel**

Click any ETF card to toggle it on the chart. Each card shows the issuer, ISIN, TER, whitelist percentage, a link to the official whitelist source, and the projected yield and capital at the deposit lock-in date.

**Scenario bar**

Select Flat / Rising / Falling to model different €STR trajectories. In Rising and Falling mode, set the annual variation in percentage points.

---

## 📐 Methodology

### Monetary ETFs

Each ETF's gross annual yield is computed as:

```
gross_yield = €STR + spread − TER
```

Net yield additionally applies the instrument's Italian effective tax rate (derived from the whitelist percentage) and subtracts *imposta di bollo* (0.20%/year).

### Fixed Deposit

Gross yield applies the stated annual rate. Net yield deducts the user-configured tax rate and *imposta di bollo* from the annual interest.

### Rate Scenarios

| Scenario | Description |
|----------|-------------|
| Flat | €STR remains constant throughout the horizon |
| Rising | €STR increases by a configurable amount each year |
| Falling | €STR decreases by a configurable amount each year (floor: 0%) |

### Included ETFs

| Ticker | Issuer | Index / Strategy | TER | Whitelist | Tax rate (IT) |
|--------|--------|-----------------|-----|-----------|--------------|
| XEON | DWS / Xtrackers | Solactive €STR +8.5 bps | 0.10% | ~97% | ~12.5% |
| C3M | Amundi | EuroMTS Govt Bill 0-6M | 0.14% | 100% | 12.5% |
| SMART | Lyxor / Amundi | Euro Overnight (active) | 0.05% | <20% | 26% |
| LEONIA | BNP Paribas | Euro Overnight Return | 0.10% | <20% | 26% |
| FLESA | Franklin Templeton | Short Maturity EUR (active) | 0.06% | ~50% | ~19% |

Tax rates reflect the Italian *whitelist* regime as of 2026. Each ETF card in the app links to the official source. Always verify before making decisions.

---

## 🗂️ Repository Structure

```
cashparkfinder/
├── index.html      # The entire application (HTML + CSS + JS)
├── README.md
└── LICENSE
```

The app is a single self-contained HTML file. There are no dependencies, no build step, and no framework.

---

## 🌐 Self-hosting / GitHub Pages

1. Fork or clone this repository
2. Go to **Settings → Pages → Source → Deploy from branch → main**
3. The app will be live at `https://<your-username>.github.io/cash-park-finder/`

Alternatively, just download `index.html` and open it locally — it works fully offline (except for the live €STR fetch, which requires an internet connection).

---

## ⚖️ License

**Copyright © 2026 Jacopo Monti. All Rights Reserved.**

Licensed under the GNU Affero General Public License v3.0. You may use, modify, and share this software provided that any modifications or derivative works are also released under AGPL-3.0, including when deployed as a web service.

See [LICENSE](LICENSE) for full terms.

---

## 📧 Contact

**Issues & feature requests**: [open an issue](https://github.com/jacopo-monti/cash-park-finder/issues)  
**Other inquiries**: jacopo.monti.jm@gmail.com  
🐙 [@jacopo-monti](https://github.com/jacopo-monti)
