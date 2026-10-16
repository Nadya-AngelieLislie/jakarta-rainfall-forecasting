# Jakarta Rainfall Forecasting

> Testing whether simple statistics or deep learning forecasts rainfall better.

## Overview

- Time Series course project; I built the classical-model track in R within a 2-person team.
- Jakarta is flood-prone: a January 2026 flood hit 129 locations, with about IDR 1.69 trillion in losses.

## Data / Scope

- NASA POWER daily rainfall, 2010-2026: 5,845 readings aggregated to 835 weekly and 193 monthly totals. 80/20 train/test split.

## Workflow

- Built 4 classical models in R: Seasonal Naive, TSR, ARIMA and SARIMA.
- A teammate built Neural Net, LSTM and GRU in Python on the same data and setup.
- Compared all 7 models on held-out test data using RMSE and MAE.

## Results

- Time Series Regression won: test RMSE 26.95 mm/week, MAE 20.38 mm.
- It beat SARIMA (29.49) and the best deep model, LSTM (32.46).
- Same ranking held at monthly level.

## Tech Stack

R, ARIMA, SARIMA, Time series regression, Python, PyTorch

## Repository Structure

```
r/                  R Markdown: naive, time-series regression, ARIMA, SARIMA (monthly and weekly)
notebooks/          PyTorch notebooks: NN, LSTM, GRU (monthly and weekly)
data/               NASA POWER daily rainfall (2010-2026, Jakarta)
report/             Final report (PDF) and knitted outputs
```

## How to Run

**R models** (naive, time-series regression, ARIMA, SARIMA): open the `.Rmd` files in `r/` with RStudio and knit. Data is read from `data/Dataset16Tahun.xlsx` (set the working directory to the repository root).

**Deep learning models**: `pip install numpy pandas scikit-learn matplotlib torch jupyter`, then run the notebooks in `notebooks/`.

## Links

- Report: report/AoL_Time_Series_Report.pdf

## Team

Time Series Analysis course project by Britney Angeline Soeseno and Nadya Angelie Lislie.

## Notes

- `data/` also holds the raw NASA POWER daily CSV.
- Data source: NASA POWER (MERRA-2), variable PRECTOTCORR (mm/day), Jakarta coordinates.
- The project was run at monthly and weekly aggregation levels to compare how aggregation affects model accuracy.
- Plagiarism-check certificates are intentionally not included.

## Author

Nadya Angelie Lislie, BINUS University (Computer Science and Statistics). [LinkedIn](https://www.linkedin.com/in/nadya-angelie-lislie/) | [GitHub](https://github.com/Nadya-AngelieLislie)

## Experiment Tracking

`src/experiment_tracking.py` provides an optional MLflow wrapper (`track_run`) for logging parameters, metrics and artifacts; it does nothing when MLflow is not installed. Run `mlflow ui` after logging runs to compare experiments.

## Continuous Integration

GitHub Actions (`.github/workflows/ci.yml`) runs `ruff` and `pytest` repository-health checks on every push; run them locally with `make lint test`.
