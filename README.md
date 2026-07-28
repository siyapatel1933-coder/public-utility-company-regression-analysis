# public-utility-company-model
# Hotazel Steam Forecasting

A regression analysis that forecasts monthly steam-plant **revenue** from operating
and weather data, built in Google Colab using an AICPA regression-analysis dataset.
The notebook loads the monthly data, engineers a seasonal feature, fits a regression
on a training period, and evaluates the revenue forecast on a held-out testing period
using an absolute percentage error (APE) score.

**Author:** Siya Patel

## Overview

Monthly observations are split into a training period (2011–2013) and a testing
period (2014). A regression is fit on the training data to forecast `revenue`, and
its accuracy is measured on the testing data via APE.

## Data

The dataset (`AICPA_regressionAnalysisData.csv`) spans January 2011 – December 2014
at monthly frequency (48 observations), split by the `type` column:

| Split    | `type` value  | Date range              | Observations |
|----------|---------------|-------------------------|:------------:|
| Training | `dt4training` | 2011-01-31 → 2013-12-31 | 36           |
| Testing  | `dt4testing`  | 2014-01-31 → 2014-12-31 | 12           |

### Columns

| Column       | Description                                   |
|--------------|-----------------------------------------------|
| `type`       | Split label: `dt4training` or `dt4testing`    |
| `date`       | Month-end date (parsed to datetime)           |
| `revenue`    | Monthly revenue — the forecast target         |
| `production` | Monthly production                            |
| `coolDD`     | Cooling degree days                           |
| `heatDD`     | Heating degree days                           |
| `winter_DV`  | Engineered dummy = 1 for Dec/Jan/Feb, else 0  |

## Method

1. Load the dataset and parse `date` to datetime.
2. Engineer `winter_DV`, a winter seasonal dummy (December, January, February).
3. Fit a regression on the training split (`dt4training`) to forecast `revenue`
   from the production, degree-day, and seasonal predictors.
4. Forecast `revenue` on the testing split (`dt4testing`).
5. Evaluate accuracy with an absolute percentage error (APE) score.

## Requirements

- numpy
- pandas
- matplotlib
- statsmodels

Install with:

```bash
pip install numpy pandas matplotlib statsmodels
```

## Usage

1. Place `AICPA_regressionAnalysisData.csv` in the same directory as the notebook.
2. Open `Hotazel_Steam_Forecasting.ipynb` in Google Colab or Jupyter.
3. Run the cells in order.

## Files

| File                               | Description            |
|------------------------------------|------------------------|
| `Hotazel_Steam_Forecasting.ipynb`  | Main analysis notebook |
| `AICPA_regressionAnalysisData.csv` | Input dataset          |

