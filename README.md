# public-utility-company-model
# Hotazel Steam Forecasting

A regression-based analysis of steam plant data, built in Google Colab using an
AICPA regression-analysis dataset. The project loads monthly operating data,
prepares it for modeling, and (based on the imported libraries) is set up to fit
a regression model for forecasting.

> **Note:** This README was drafted from a PDF export of the notebook that only
> captured the data-loading and feature-engineering steps. Sections marked
> **_TODO_** below could not be verified from that export and should be filled in
> or corrected against the full notebook.

---

## Overview

The notebook works with the file `AICPA_regressionAnalysisData.csv`, which
contains monthly observations split into a training period and a testing period.
Weather-based variables (degree days) and a seasonal indicator are used as
predictors.

The dependent (target) variable is **_TODO_** — the dataset contains both
`revenue` and `production`, and the notebook export does not show which one is
being forecast. Please confirm before relying on this README.

## Data

The dataset spans **January 2011 – December 2014** at a monthly frequency
(48 observations total) and is split by the `type` column:

| Split         | `type` value | Date range              | Observations |
|---------------|--------------|-------------------------|:------------:|
| Training      | `dt4training`| 2011-01-31 → 2013-12-31 | 36           |
| Testing       | `dt4testing` | 2014-01-31 → 2014-12-31 | 12           |

### Columns

| Column       | Description                                                        |
|--------------|--------------------------------------------------------------------|
| `type`       | Split label: `dt4training` or `dt4testing`                         |
| `date`       | Month-end date (parsed to datetime in the notebook)               |
| `revenue`    | Monthly revenue                                                    |
| `production` | Monthly production                                                 |
| `coolDD`     | Cooling degree days (standard weather metric)                     |
| `heatDD`     | Heating degree days (standard weather metric)                     |
| `winter_DV`  | Engineered dummy = 1 for December/January/February, else 0        |

> I'm reasonably confident `coolDD`/`heatDD` are cooling/heating degree days —
> these are standard energy-industry terms — but I don't have a data dictionary
> from the source to confirm the exact units. You may want to verify this against
> the original AICPA case materials.

## What the notebook does (verified from the PDF)

1. Imports `numpy`, `pandas`, `matplotlib.pyplot`, and `statsmodels.api`.
2. Reads `AICPA_regressionAnalysisData.csv` into a DataFrame.
3. Converts the `date` column to datetime with `pd.to_datetime`.
4. Creates a `winter_DV` seasonal dummy variable flagging winter months
   (December, January, February).

## What the notebook likely does next (NOT verified — _TODO_)

`statsmodels` is imported, so the notebook is presumably set up to fit a
regression (e.g., OLS) and forecast on the testing split, but that code was not
in the PDF export. Fill in the actual steps here, for example:

- Model specification (target variable and chosen predictors)
- Fitting the model on the training split
- Evaluating fit / forecasting on the testing split
- Any plots or error metrics produced

## Requirements

```
numpy
pandas
matplotlib
statsmodels
```

Install with:

```bash
pip install numpy pandas matplotlib statsmodels
```

## Usage

1. Place `AICPA_regressionAnalysisData.csv` in the same directory as the notebook.
2. Open `Hotazel_Steam_Forecasting.ipynb` in Google Colab or Jupyter.
3. Run the cells in order.

## Files

| File                                   | Description                          |
|----------------------------------------|--------------------------------------|
| `Hotazel_Steam_Forecasting.ipynb`      | Main analysis notebook               |
| `AICPA_regressionAnalysisData.csv`     | Input dataset (not included in repo) |

## License / Attribution

The dataset is described as an AICPA regression-analysis dataset. Confirm any
usage or redistribution terms with the original source before publishing.
**_TODO_** — add a license if you intend one for your own code.
