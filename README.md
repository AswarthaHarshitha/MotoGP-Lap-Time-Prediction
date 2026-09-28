# MotoGP Lap Time Prediction

Regression notebook for the **Burnout 2025** challenge (IEEE Computer Society, MUJ) on Kaggle: predict `Lap_Time_Seconds` for MotoGP laps from rider history, circuit characteristics, tyre choices and weather.

Kaggle notebooks: [burnout-2025-challenge](https://www.kaggle.com/code/sugreevuharshitha/burnout-2025-challenge) · [motogp-analysis-notebook](https://www.kaggle.com/code/sugreevuharshitha/motogp-analysis-notebook)

## Data

Competition data (273,437 training rows, 45 columns; 546,874 rows to predict) covering racing category, circuit length and corners, grid position, average speed, tyre compounds, track condition, humidity, pit-stop duration, penalties and rider career statistics. The data is loaded from the Kaggle input directory and is not stored in this repository.

## Approach

- **EDA** — lap-time distribution (70–110 s), missing-value analysis (`Penalty` only), lap times by category and track condition.
- **Feature engineering** — 11 derived features such as rider finish rate, points rate and corners per km; label encoding of 7 categorical columns; 35 features in the final matrix.
- **Models** — Linear Regression, Ridge and Random Forest (100 trees, depth 10), trained on a 30,000-row sample with an 80/20 split and cross-validated RMSE.
- **Analysis** — Random Forest feature importance and residual plots.

## Results

| Model | Test RMSE (s) | Test MAE (s) |
|---|---|---|
| Random Forest | 11.42 | 9.85 |
| Ridge | 11.47 | 9.90 |
| Linear Regression | 11.47 | 9.90 |

All three models stay close to the target's standard deviation (≈11.5 s; R² ≈ 0), meaning the provided features explain very little of the lap-time variance. The submission therefore sits close to the mean lap time.

## Files

| File | Description |
|---|---|
| `Kaggle notebook burnout-2025-challenge.ipynb` | Full analysis and training notebook |
| `HackStream_output.csv` | Submitted predictions (`Unique ID`, `Lap_Time_Seconds`) |
