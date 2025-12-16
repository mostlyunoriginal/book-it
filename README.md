# BookIt

A Python package for creating professional PDF codebooks from DataFrames.

[![PyPI version](https://badge.fury.io/py/bookit-df.svg)](https://badge.fury.io/py/bookit-df)
[![Documentation](https://img.shields.io/badge/docs-online-blue)](https://mostlyunoriginal.github.io/bookit-df/)

## Features

- **DataFrame support** — Works with polars and pandas
- **Automatic statistics** — Count, missing, unique, mean, std, min, max
- **Charts** — Bar charts for categorical, histograms for numeric variables
- **Value labels** — Document coded values (e.g., `1 = "Male"`)
- **Context manager** — Auto-save with `with BookIt(...) as book:`

## Installation

```bash
pip install bookit-df

# With polars support (recommended)
pip install bookit-df[polars]

# With pandas support
pip install bookit-df[pandas]
```

## Quick Example

```python
import polars as pl
from bookit_df import BookIt

df = pl.read_csv("survey_data.csv")

with BookIt("Survey Codebook", output="codebook.pdf", author="Research Team") as book:
    book.from_dataframe(
        df,
        descriptions={
            "age": "Respondent's age in years",
            "income": "Annual household income (USD)",
        },
        value_labels={
            "gender": {1: "Male", 2: "Female"}
        },
        suppress_numeric_stats=["gender"],
    )
# PDF saved automatically!
```

## Documentation

**Full documentation**: [mostlyunoriginal.github.io/bookit-df](https://mostlyunoriginal.github.io/bookit-df/)

- [Getting Started Tutorial](https://mostlyunoriginal.github.io/bookit-df/tutorials/01_getting_started/)
- [API Reference](https://mostlyunoriginal.github.io/bookit-df/reference/core/)
