# ETF Monetari vs Conto Deposito

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-222?logo=github)](https://jacopo-monti.github.io/etf-vs-conto-deposito/)

A browser-based, tax-aware comparison tool for Italian monetary ETFs vs fixed-term deposit accounts — runs entirely in your browser, no installation required.

🔗 **[Open the app](https://jacopo-monti.github.io/etf-vs-conto-deposito/)**

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
- **Gross / Net toggle** — switch between pre-tax and after-tax views instantly
- **Scenario simulation** — model flat, rising, or falling €STR rate trajectories
- **Interactive chart** — toggle each instrument on/off with checkboxes
- **Fully configurable** — initial capital, deposit rate, lock-in duration, tax rate, *bollo*

---

## 🚀 Usage

Just open [`index.html`](index.html) in a browser, or visit the hosted version at:

**[https://jacopo-monti.github.io/etf-vs-conto-deposito/](https://jacopo-monti.github.io/etf-vs-conto-deposito/)**

### How it works

**Sidebar — left panel**

Set your initial capital, then configure the fixed deposit (rate, duration, tax rate, *imposta di bollo*). Select which monetary ETFs to display using the checkboxes. Choose a rate scenario and gross/net view.

**Chart — main area**

The line chart shows how your capital evolves year by year for each selected instrument. All lines share the same time axis; the deposit lock-in duration drives the default horizon.

**Summary cards**

Below the chart, summary cards show the projected final capital and absolute/percentage gain for each active instrument at the end of the deposit lock-in period.

---

## 📐 Methodology

### Monetary ETFs

Each ETF's gross annual yield is computed as:

```
gross_yield = €STR + spread − TER
```

Where `spread` is the ETF-specific basis-point premium over €STR and `TER` is the total expense ratio. Net yield additionally applies the instrument's Italian tax rate and subtracts *imposta di bollo* (0.20%/year).

### Fixed Deposit

Gross yield applies the stated annual rate directly. Net yield deducts the user-configured tax rate and any *imposta di bollo* from the annual interest.

### Rate Scenarios

| Scenario | Description |
|----------|-------------|
| Flat | €STR remains constant throughout the horizon |
| Rising | €STR increases by a configurable amount each year |
| Falling | €STR decreases by a configurable amount each year (floor: 0%) |

### Included ETFs

| Ticker | Issuer | Index / Strategy | TER | Tax rate (IT) |
|--------|--------|-----------------|-----|--------------|
| XEON | DWS / Xtrackers | €STR +8.5 bps | 0.10% | ~12.5% |
| C3M | Amundi | EuroMTS Govt Bill 0-6M | 0.14% | 12.5% |
| SMART | Lyxor / Amundi | Euro Overnight (active) | 0.05% | 26% |
| LEONIA | BNP Paribas | Euro Overnight Return | 0.10% | 26% |
| FLESA | Franklin Templeton | Short Maturity EUR (active) | 0.06% | ~19% |

Tax rates reflect the Italian *whitelist* regime as of 2026; verify current classification before making decisions.

---

## 🗂️ Repository Structure

```
etf-vs-conto-deposito/
├── index.html      # The entire application (HTML + CSS + JS)
├── README.md
└── LICENSE
```

The app is a single self-contained HTML file. There are no dependencies, no build step, and no framework.

---

## 🌐 Self-hosting / GitHub Pages

1. Fork or clone this repository
2. Go to **Settings → Pages → Source → Deploy from branch → main**
3. The app will be live at `https://<your-username>.github.io/etf-vs-conto-deposito/`

Alternatively, just download `index.html` and open it locally — it works fully offline (except for the live €STR fetch, which requires an internet connection).

---

## ⚖️ License

**Copyright © 2026 Jacopo Monti. All Rights Reserved.**

Licensed under the GNU Affero General Public License v3.0. You may use, modify, and share this software provided that any modifications or derivative works are also released under AGPL-3.0, including when deployed as a web service.

See [LICENSE](LICENSE) for full terms.

---

## 📧 Contact

**Issues & feature requests**: [open an issue](https://github.com/jacopo-monti/etf-vs-conto-deposito/issues)  
**Other inquiries**: jacopo.monti.jm@gmail.com  
🐙 [@jacopo-monti](https://github.com/jacopo-monti)
