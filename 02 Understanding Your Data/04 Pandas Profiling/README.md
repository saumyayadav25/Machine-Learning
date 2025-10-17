# Pandas Profiling (YData Profiling)

Use of **pandas profiling** for automated Exploratory Data Analysis (EDA).

[Refer to this](https://pypi.org/project/pandas-profiling/)

## Overview
Pandas Profiling automatically generates a detailed EDA report from a pandas DataFrame, providing insights into data quality, distributions, correlations, and missing values.

## Installation
```bash
pip install ydata-profiling
```

### Usage

```py
import pandas as pd
from ydata_profiling import ProfileReport

df = pd.read_csv("data.csv")
profile = ProfileReport(df, title="EDA Report", explorative=True)
profile.to_file("output.html")
```

## Output

An interactive HTML report summarizing:

- Dataset statistics

- Variable types and distributions

- Correlations

- Missing value patterns

- Sample data preview