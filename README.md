# Efes Beer Distribution Optimization

**Type:** Team Project · Prescriptive Analytics

## Overview
Applied linear programming and mixed-integer optimization to the real-world distribution network of Efes, Turkey's dominant beer producer, to minimize malt and beer transportation costs and recommend optimal brewery expansion locations ahead of projected demand growth and increasing competitive pressure from Carlsberg.

## Problem
- Demand projected to grow beyond current brewing capacity
- Distribution expenses make up a large portion of total costs
- Competitive pressure increasing after Carlsberg's acquisition of Turk Tuborg
- Need to combine short-term distribution improvements with long-term strategic brewery location decisions

## Part 1 — Distribution Plan Optimization (LP)

**Objective function:**
```
Min Z = Σi Σj malt_cost(i,j) × malt_shipped(i,j) + Σj Σk beer_cost(j,k) × beer_shipped(j,k)
Where: i = malt plant, j = brewery, k = distribution center
```

**Key changes:**
- Reassigned Afyon malt to Istanbul and Konya malt to Ankara
- Eliminated all imported malt — domestic capacity (98K tons) far exceeds demand (55.4K tons) at lower cost on every route
- Matched breweries to geographically closer distribution centers

**Result: $14.16M → $11.8M — saving $2.36M (16.7%)**

## Part 2 — Sensitivity Analysis
| Distribution Center | Shadow Price | Interpretation |
|---|---|---|
| Export/Izmir | $45K/ML | Most expensive to serve — port shipping costs |
| Istanbul | $3K/ML | Cheapest — local brewery, near-zero transport cost |
| System growth limit | 8ML | Tied to Istanbul brewery slack capacity |

Import malt viability thresholds:
- Istanbul route: needs **9% cost reduction** to become viable
- Ankara route: needs **44% cost reduction** to become viable

## Part 3 — Capacity Expansion (Mixed-Integer Programming)
Optimal solution opens 3 new breweries:

| Site | Capacity | Fixed Cost | Rationale |
|---|---|---|---|
| Izmir (expand) | 120ML | $6.0M/yr | Serves Izmir demand and exports at near-zero transport cost |
| Samsun (new) | 90ML | $2.5M/yr | Lowest fixed cost, serves Samsun at zero transport cost |
| AnkNew (new) | 90ML | $3.5M/yr | Serves Kayseri and Export overflow |

**Total minimum annual cost: $23.56M** ($1.74M malt transport + $9.83M beer transport + $12M fixed investment)

## Non-Optimal Scenario Analysis
| Scenario | Total Cost | Difference |
|---|---|---|
| Optimal | $23.56M | — |
| Remove AnkNew | $23.62M | +$0.06M |
| Don't expand Izmir | $23.86M | +$0.30M |
| Remove Samsun | $27.05M | +$3.49M |

**Izmir and Samsun are non-negotiable. AnkNew is interchangeable with Sakarya at near-zero cost.**

## Capacity Utilization Recommendation
Operating at **95% capacity** costs only +$0.24M vs full capacity and provides meaningful operational buffer. Costs accelerate sharply below 90%.

## Tech Stack
`Linear Programming` `Mixed-Integer Programming` `Excel Solver` `Sensitivity Analysis` `Supply Chain Modeling`

## Files
- `Efes_Beer_Distribution_Slides.pdf` — Project presentation
- `Efes_Beer_Distribution_Appendix.pdf` — Full written analysis
- `Efes_Beer_Distribution_Model.xlsx` — Live Excel Solver model
