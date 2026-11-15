# Run results – supplied COMP3010 datasets

This file records a local run using the supplied `train.csv` and `test.csv` files. The run uses scenario grouping derived from the verified 27-sensor ID sequence and a modest 2-fold / 2-candidate random search configuration.

## Data processing

| Item | Rows |
|---|---:|
| Source training rows | 10,050 |
| Competition test rows | 3,203 |
| Missing target rows removed | 10 |
| Duplicate labelled rows removed (ignoring ID) | 50 |
| Rows removed for at least 40% missing predictors | 0 |
| Clean labelled rows | 9,990 |
| Scenario groups | 371 |
| Training partition | 6,985 |
| Validation partition | 1,512 |
| Internal-test partition | 1,493 |

## Candidate model comparison

| Model | CV MAPE | Train MAPE | Validation MAPE | Validation R² |
|---|---:|---:|---:|---:|
| Random Forest | 0.33727 | 0.14206 | 0.28375 | 0.83967 |
| XGBoost | 0.34154 | 0.24841 | 0.31170 | 0.78298 |
| Ridge Regression | 0.60460 | 0.49274 | 0.49077 | 0.59506 |
| Linear Regression | – | 0.49164 | 0.50267 | 0.61695 |
| Linear SVR | 0.64045 | 0.49745 | 0.50791 | 0.62239 |
| MLP Neural Network | 1.09180 | 0.16344 | 0.57646 | 0.78821 |

Random Forest was selected by lowest validation MAPE.

## Selected-model holdout metrics

| Metric | Value |
|---|---:|
| Internal-test MAPE | 0.25812 |
| Internal-test R² | 0.83703 |
| Internal-test MAE | 0.09002 |
| Internal-test RMSE | 0.19004 |

## Competition prediction file

- File: `outputs/prediction.csv`
- Rows: 3,203
- Columns: `ID`, `Target Pressure (bar)`
- Prediction range: approximately 0.03672 to 4.01298 bar
