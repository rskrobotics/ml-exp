# Froth Flotation Process - Iron Ore Concentration

## What It Does
Separates iron ore from silica (impurity) using **differences in surface chemistry**. This is a **reverse flotation** process - iron floats up, silica sinks.

## Process Flow
```
RAW ORE (iron + silica mixed)
         │
         ▼
    GRINDING → particles 2-500 μm
         │
         ▼
    SLURRY (pulp) → mix with water
         │
         ▼
    ADD REAGENTS:
    • Starch (depressant) → coats silica, makes it hydrophilic → SINKS
    • Amina (collector)   → coats iron, makes it hydrophobic → FLOATS
         │
         ▼
    FLOTATION COLUMNS (×7)
    ┌─────────────────┐
    │ ░░░ FROTH ░░░░  │ ← Iron concentrate (product)
    │  ○ ○ ○ ○ ○ ○ ○  │   scraped off top
    │   air bubbles   │
    │    + slurry     │
    │                 │
    │ ▓▓▓ TAILINGS ▓▓ │ ← Silica waste (sinks)
    └─────────────────┘
         │
    ┌────┴────┐
    ▼         ▼
CONCENTRATE  TAILINGS
(high iron)  (high silica)
```

## Key Variables in Dataset

| Type | Variables | Notes |
|------|-----------|-------|
| **Uncontrollable inputs** | % Iron Feed, % Silica Feed | Ore quality from mine - varies daily |
| **Controllable inputs** | Starch Flow, Amina Flow | Main reagent levers |
| | Ore Pulp Flow, pH, Density | Slurry properties |
| | Air Flow (×7), Level (×7) | Flotation column controls |
| **Outputs** | % Iron Concentrate | Product quality (higher = better) |
| | % Silica Concentrate | Impurity (lower = better) |

## Critical for Modeling

1. **Time delays:** Changes in inputs take **1-2 hours** to show in output (process residence time + lab measurement delay)

2. **Confounders:** Feed quality (% Iron/Silica Feed) affects both what operators do AND final quality

3. **Interactions:** Reagents work together - can't optimize one independently:
   - ↑ Starch → ↓ Silica in product, but may ↓ iron recovery
   - ↑ Amina → ↑ Iron recovery, but may ↑ silica carryover

4. **pH matters but isn't the control lever:** pH is controlled separately (usually with lime, not in dataset). Starch/amina effectiveness depends on pH being ~10-10.5.

## Goal
Predict `% Silica Concentrate` early so operators can take corrective action **before** the lab result arrives (1 hour later).

## Data Source
Kaggle: [Quality Prediction in a Mining Process](https://www.kaggle.com/datasets/edumagalhaes/quality-prediction-in-a-mining-process)  
Time range: March - September 2017
