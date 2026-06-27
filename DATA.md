# Dataset Description

## Source

This project uses the ILINet dataset exported from the CDC FluView system.

Official CDC source pages:

- CDC FluView Interactive overview: https://www.cdc.gov/fluview/overview/fluview-interactive.html
- CDC FluView Interactive data dashboard: https://gis.cdc.gov/grasp/fluview/fluportaldashboard.html

To reproduce the dataset manually, open the FluView Interactive data dashboard, select the national/regional/state outpatient illness and viral surveillance view, choose ILINet data for New York, select the desired seasons/weeks, and use the dashboard's **Download Data** option.

Dataset file used in this repository:

```text
data/ILINet.csv
```

The raw export describes weekly influenza-like illness (ILI) activity reported by sentinel healthcare providers.

## Selected Series

The project focuses on New York state only.

The target variable is:

```text
%UNWEIGHTED ILI
```

In the notebook this column is renamed to:

```text
ili
```

This variable represents the percentage of outpatient visits classified as influenza-like illness during each week.

## Time Range

The raw data is reported by:

```text
YEAR
WEEK
```

The selected period starts at week 40 of 2010 and ends at week 20 of 2026.

In the notebook, `YEAR` and `WEEK` are converted into a continuous weekly date index so the data can be analyzed as a regular time series.

## Columns Not Used

Several columns are not used for modeling:

```text
% WEIGHTED ILI
AGE 0-4
AGE 25-49
AGE 25-64
AGE 5-24
AGE 50-64
AGE 65
```

These columns contain unavailable values (`X`) in this export.

The raw count column `ILITOTAL` is also not used as the target because it depends on reporting volume and total patient visits. `%UNWEIGHTED ILI` is preferred because it measures relative ILI intensity.

## Reproduction Steps

1. Place the CDC FluView ILINet CSV export at:

```text
data/ILINet.csv
```

2. Open and run:

```text
TimeSeries_ILI_EDA.ipynb
```

3. The notebook loads the file with:

```python
pd.read_csv("data/ILINet.csv", skiprows=1)
```

The first row of the raw export is a title line, so the real CSV header starts on the second row.

## License And Use

The dataset is a public health data export from CDC FluView.