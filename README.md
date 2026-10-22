# OOP with Python – Assignment 1, Advent 2026

## Student submission package

This repository implements all five mini-projects in the assignment:
1. UBOS District Population Forecaster
2. Solar Micro-Grid Dispatch Planner
3. Lake Victoria Fish Stock & Export Risk Model
4. Rainfall Pattern & Crop Suitability Analyser
5. Taxi Route Revenue, Pricing & Fleet Planner

## Structure

```text
src/          Reusable OOP Python modules
notebooks/    One Jupyter Notebook per mini-project
tests/        pytest unit tests
data/         Generated illustrative CSV
```

## Setup

Python 3.10+ is recommended.

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/macOS:
source .venv/bin/activate

pip install -r requirements.txt
pytest -q
```

Open Jupyter:

```bash
jupyter notebook
```

Run each notebook top-to-bottom with **Restart & Run All**.

## Reproducibility

Random simulations use `np.random.default_rng(seed)` with fixed seeds, principally seed 42.

## Important assumptions

- Population data are illustrative as supplied by the assignment; Mbarara and Mbale are additional illustrative districts.
- Solar micro-grid demand is synthetic and generated with a weekly pattern plus seeded noise.
- Fish price follows a bounded seeded random walk.
- Fish risk thresholds are modelling conventions: CV < 0.15 = Low, 0.15–0.30 = Moderate, > 0.30 = High.
- Rainfall crop rules are simplified screening rules, not agronomic prescriptions.
- Taxi fleet capacity is 8 one-way trips × 14 seats per vehicle, with a 15% planning buffer.

## Rainfall references

FAO crop-water guidance:
- https://www.fao.org/4/S2022E/s2022e07.htm
- https://www.fao.org/4/x6939e/X6939e01.htm
- https://www.fao.org/giews/countrybrief/country.jsp?code=UGA

## AI-use declaration

AI assistance was used to support code scaffolding, debugging, organisation of the repository, and drafting explanatory comments. The student remains responsible for understanding the implementation, checking results, running the tests, and explaining the code during any viva. The notebooks and modules were reviewed for consistency with the assignment requirements.

## Summary of findings

Across the projects, the analyses show that model choice should be driven by validation and domain logic rather than by mathematical complexity alone. The population project compares trend, proportional-growth and Fibonacci forecasts; the Fibonacci model is treated critically because it lacks a demographic mechanism. The micro-grid project demonstrates that an exact linear solution can produce physically impossible negative dispatch values and therefore needs feasibility checks. The fish project replaces unbounded Fibonacci growth with a logistic harvesting model and evaluates revenue risk with coefficient of variation and Monte Carlo VaR. The rainfall project demonstrates that similarity metrics answer different questions and that simplified crop rules require caution. The taxi project uses walk-forward validation and capacity planning rather than a single naive forecast.
