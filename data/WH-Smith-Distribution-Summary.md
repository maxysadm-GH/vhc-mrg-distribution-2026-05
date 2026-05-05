# WH Smith / MRG — Distribution Depth Analysis
**Period:** July 2025 – May 2026 · **Source:** Fishbowl ERP, customerId 74 (Marshall Retail Group / WH Smith) · **Pulled:** 2026-05-04

---

## The headline answer

> **Yes — distribution depth is genuinely expanding.** 69% of locations are adding SKUs over time, the footprint grew net +40 ship-tos vs. the opening period, and concentration is healthy (HHI 230). The constraint on further growth is the assortment itself: only 7 SKUs are active, so every location caps at 7 by definition.

---

## What the numbers show

| Metric | Value |
|---|---|
| Active ship-to locations (period total) | **83** |
| Active SKUs (period total) | **7** (5 bars + 6PC caramel + 4PC truffle) |
| Sales orders shipped | **232** (220 Fulfilled · 12 Issued · 0 voided) |
| Total units shipped | **13,488** |
| Locations expanding (positive SKU-breadth slope) | **57** (69%) |
| Locations flat | **10** (12%) |
| Locations contracting | **16** (19%) |
| Active in earliest 3 mo only | 8 |
| Active in latest 3 mo only | **48** |
| Active in both windows | 19 |
| **Net change in footprint** | **+40 locations** |
| Top 1 / Top 5 / Top 10 / Top 20 share of volume | 6.1% / 21.9% / 35.9% / 58.0% |
| Herfindahl–Hirschman Index | **230** (highly diversified — under 1,500) |

## SKU mix (7-SKU assortment)

| SKU | Description | Units | Share |
|---|---|---:|---:|
| 1801012 | Pink Himalayan Salt Caramel Bar 3oz | 2,976 | 22% |
| 1801009 | Matcha Green Tea Bar 3oz | 2,628 | 19% |
| 1801004 | Coconut & Banana Super Dark Bar 3oz | 2,436 | 18% |
| 1801022 | Barcelona Bar 3oz | 1,764 | 13% |
| 1801021 | Bacon Bar 3oz | 1,596 | 12% |
| 1801027 | Red Hawaiian Salt Caramel 6PC | 1,200 | 9% |
| 1801758 | Maison Truffle Collection 4PC | 888 | 7% |

The 5 bars carry 84% of volume. 6PC + 4PC do the remaining 16%.

## Four key insights

1. **Growth is broad, not concentrated.** The expanding locations cohort is 57 stores — this isn't one or two airports doing all the work. HHI of 230 confirms it: no single store is over-weighted.

2. **March 2026 was a step-change, not a drift.** 32 ship-tos activated in a single month (more than the prior six months combined). This is a discrete onboarding wave from MRG, almost certainly tied to a roll-out program. Worth confirming what cycle this represents and what's planned next.

3. **The assortment IS the ceiling.** Every location is bounded at 7 SKUs because that's all that's active. If the goal is meaningful depth growth beyond the current trajectory, the lever is adding SKUs to the airport assortment — not chasing more doors.

4. **16 contracting locations need a name-by-name look.** Some of these will be airport remodels or shelf-space pulls (out of our hands), some will be coachable through MRG. The deck lists all 83 by state with their sparkline so the conversation can go specific.

## What I'd recommend before the contract review

- **Confirm the March wave with MRG** — which program drove the 32 new doors, what's coming next.
- **Pull the 16 contracting locations by name** — ask MRG whether shelf space was reduced or assortment was edited.
- **Build the SKU-expansion ask** — which 3–5 additional Vosges items pilot well in airport travel-retail (the 7-SKU set is two years old).
- **Lock the data definition** — ship-to identity = (Name, City, State, Zip, Country) tuple. Repeatable on demand from Fishbowl.

## Method note

- Source: Fishbowl `so` + `soitem` joined to ship-to fields embedded on the SO header.
- Filter: `customerId = 74`, `dateIssued ≥ 2025-07-01`, status ≠ Voided/Cancelled.
- Excluded the `ShipStation Shipping` freight-charge pseudo-line.
- Ship-to identity = `shipToName | city | stateId | zip | country`. 83 unique tuples observed.
- Trend bucket = linear-regression slope of monthly SKU breadth: > +0.05 / mo = Expanding · between ±0.05 = Flat · < −0.05 = Contracting.

Every metric in this report traces directly to a Fishbowl SQL query — no narrative-derived numbers.

## Deliverable bundle

- **Excel workbook** (7 sheets, charts): `output/WH-Smith-Distribution-Analysis_2025-07_2026-05.xlsx`
- **Animated HTML deck** (4 pages, brand-aligned): `output/wh-smith-deck.html`
- **This summary**: `output/WH-Smith-Distribution-Summary.md`
- **Raw data** (line + order CSVs): `data/whsmith_lines.csv`, `data/whsmith_orders.csv`
- **Analysis tables** (matrix, trends, concentration, penetration): `data/analysis/*.csv`
