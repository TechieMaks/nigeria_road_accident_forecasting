# Machine Learning-Based Forecasting of Road Traffic Accident Trends in Nigeria Using Historical Transport Data

## Project Overview

This repository contains the Python implementation and supporting analytical materials for an MSc Data Science dissertation investigating machine-learning approaches to forecasting road traffic accident trends in Nigeria.

The research examines historical road traffic crash patterns and compares conventional statistical forecasting methods with machine-learning models. It also investigates the reproducibility and retrospective forecasting performance of the ARIMA models reported by Sanusi, Adebola and Adegoke (2016).

The analysis consists of two distinct components:

1. **National annual forecasting:** An examination of annual road traffic accident trends from 1960 to 2024, including a comparison of ARIMA, Linear Regression, Random Forest, Gradient Boosting and naive forecasting approaches.
2. **State-quarter forecasting:** A machine-learning analysis of quarterly road traffic crash counts across Nigeria's 36 states and the Federal Capital Territory, using historical crash counts, recorded accident causes and geographical information.

The overall aim is to evaluate the predictive performance of these approaches and their potential contribution to evidence-informed road-safety planning.

## Research Objectives

- Examine historical patterns and trends in reported road traffic accidents in Nigeria.
- Investigate the reproducibility of previously published ARIMA forecasts.
- Compare statistical and machine-learning forecasting approaches using appropriate time-series evaluation procedures.
- Develop and evaluate a Random Forest model for state-quarter crash-count forecasting.
- Assess forecasting accuracy, model interpretation and limitations relevant to responsible road-safety planning.

## Data Sources

### 1. National Annual Road Traffic Accident Data

- **Source:** Federal Road Safety Corps (FRSC).
- **Coverage:** 1960–2024.
- **Observations:** 65 annual records.
- **Variables:** Reported minor, serious, fatal and total road traffic crashes.

The annual dataset supports the historical forecasting analysis and the comparison with Sanusi, Adebola and Adegoke (2016).

The analysis uses an updated historical FRSC series. Some earlier historical records differ from the revised series, particularly for 2010–2012. Consequently, the reproduction of published forecasts is treated as approximate rather than an exact replication of the original study.

### 2. State-Quarter Road Traffic Accident Data

- **Source:** National Bureau of Statistics (NBS), using FRSC road traffic crash statistics.
- **Coverage:** Q2 2020–Q4 2025.
- **Geographical coverage:** 36 Nigerian states and the Federal Capital Territory.
- **Observations:** 851 state-quarter records before lag-based feature construction.
- **Target variable:** `total_cases`.

Following feature engineering and removal of observations without the required historical lags, 703 records were available for modelling.

**Data availability:** The repository contains datasets only where redistribution is permitted. Where source files are not provided, users should consult the original FRSC and NBS publications.

## Forecasting Methods

### National Annual Forecasting

The following approaches were evaluated:

- Naive previous-year forecasting
- Autoregressive Integrated Moving Average (ARIMA)
- Linear Regression
- Random Forest Regression
- Gradient Boosting Regression

The annual comparison uses an expanding-window, one-year-ahead forecasting procedure across 2014–2024, producing 11 evaluation forecasts per accident category.

A separate analysis investigates the reproduction of the ARIMA forecasts reported by Sanusi, Adebola and Adegoke (2016), including comparison with the study's published projections.

### State-Quarter Forecasting

The state-quarter analysis uses lagged historical crash counts, recorded accident-cause variables and geographical indicators to predict quarterly crash counts.

The final Random Forest configuration includes:

- Number of trees: 700
- Maximum features: Square root
- Minimum samples per leaf: 2
- Minimum samples per split: 5
- Random seed: 42

The modelling procedure uses chronological training and validation, with 2025 reserved for final evaluation.

The final evaluation employs rolling one-quarter-ahead predictions. Consequently, observed crash counts from earlier quarters of 2025 may be used as historical lag inputs when predicting subsequent quarters.

## Model Evaluation

Forecasting performance is evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE), where appropriate
- Coefficient of Determination (R²), for the state-quarter comparison

The analysis also examines residuals, differences in forecasting performance across geographical units and the predictive importance of selected features.

Model performance is compared with relevant naive forecasting benchmarks.

## Repository Contents

The main Jupyter notebooks are:

| Notebook | Purpose |
|---|---|
| `01_Exploratory_Data_Analysis.ipynb` | Exploratory analysis and visualisation of road traffic accident data |
| `02_Sanusi_Research_Comparison.ipynb` | Investigation and reproduction of published Sanusi ARIMA forecasts |
| `03_Sanusi_Research_ML_Comparison.ipynb` | National annual forecasting and machine-learning model comparison |
| `04_Feature_Engineering_and_State_Quarter_Analysis.ipynb` | State-quarter feature engineering, Random Forest modelling and evaluation |

Additional exploratory notebooks or supporting files may also be included.

## Software and Dependencies

The analysis was implemented in Python using Jupyter notebooks.

The main libraries include:

- pandas
- NumPy
- matplotlib
- seaborn
- scikit-learn
- statsmodels

Install the required dependencies using:

```bash
pip install -r requirements.txt
```

The `requirements.txt` file should specify the dependencies required to execute the notebooks.

## Reproducing the Analysis

To reproduce the analysis:

1. Clone or download this repository.
2. Install the Python dependencies listed in `requirements.txt`.
3. Obtain the required FRSC and NBS datasets, if they are not included in the repository.
4. Update any dataset paths to match the local directory structure.
5. Open the notebooks in JupyterLab or Jupyter Notebook.
6. Execute the notebooks in the documented sequence, beginning with exploratory analysis and progressing to forecasting and evaluation.

The annual and state-quarter analyses use separate datasets and should be interpreted as distinct forecasting exercises.

Reproduction of the results requires the corresponding source data, software dependencies and model specifications.

## Key Findings

The research found that:

- Naive previous-year forecasting remained competitive in the national annual comparisons, demonstrating the importance of historical persistence.
- No single forecasting approach consistently achieved the lowest error across all annual accident categories and evaluation measures.
- The state-quarter Random Forest model achieved an MAE of approximately 13.08, RMSE of 18.01 and R² of 0.903 on the 2025 evaluation data.
- Historical crash counts and recorded accident-cause features contributed substantially to state-quarter predictive performance.
- Differences in reporting practices, historical data revisions and the absence of direct traffic-exposure measures limit the interpretation and application of the forecasts.

These findings relate to predictive performance and should not be interpreted as evidence of causal relationships.

## Research Limitations

The study relies on administrative accident records, which may be affected by underreporting, inconsistent reporting practices and historical revisions.

The national annual comparison includes 11 one-year-ahead evaluation periods, limiting the strength of conclusions about long-term model superiority.

The state-quarter forecasts predict reported crash counts rather than exposure-adjusted accident risk. Feature importance indicates predictive contribution within the fitted model and does not establish causality.

The ARIMA sensitivity analysis includes exploratory specification selection informed by the extended historical series and should not be interpreted as fully independent prospective model selection.

## Academic Use and Attribution

This repository accompanies an MSc Data Science dissertation entitled *Machine Learning-Based Forecasting of Road Traffic Accident Trends in Nigeria Using Historical Transport Data*.

The notebooks and research materials are provided to support academic transparency, reproducibility and further examination of the analytical methodology.

Users should acknowledge the original FRSC and NBS data sources and consult the associated dissertation for the complete methodology, results, discussion and references.

## References and Data Sources

Federal Road Safety Corps (FRSC). Annual road traffic crash statistics and reports. https://frsc.gov.ng/documentations/annual-reports/

National Bureau of Statistics (NBS). Road transport data and statistical publications. https://microdata.nigerianstat.gov.ng/

Sanusi, Adebola and Adegoke (2016). ARIMA-based road traffic accident forecasting study. Full bibliographic details are provided in the accompanying dissertation.
