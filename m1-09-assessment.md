<!-- # Day 10 Assessment: Air Quality Trends -->

## Overview

You are supporting a public health and urban planning team that needs a quick, reliable analysis of daily air quality and weather conditions across multiple European cities. Your task is to clean imperfect data, analyze trends, and communicate findings with clear visuals and short written interpretations. The dataset is intentionally not pre-cleaned, so your first responsibility is to make it trustworthy.

## Learning Goals

By the end of the mini-project, you should be able to load and inspect a real-world dataset, clean invalid values, apply pandas indexing and filtering, aggregate and reshape data, compute rolling statistics, and create clear visualizations. You should also be able to interpret trends, uncertainty, and data limitations in concise written answers.

## Setup and Context

Use the following files for this assessment:

- **Dataset:** `m1-09-assessment.csv`
- **Starter notebook:** `m1-09-assessment.ipynb`

Each row of the CSV is a daily observation with columns `date`, `city`, `avg_temp_c`, `humidity_pct`, and `pm25`. The dataset includes missing values and invalid strings like `"NA"` inside numeric fields. Parse the `date` column as datetime. Use the starter notebook in this repository and complete your work there.

## Tasks

### Part A: Core Data Handling

1. **Load & parse**  
   Load the CSV with proper date parsing. Set `date` as a datetime index. Confirm row count and show `head()`.

2. **Inspect structure**  
   Use `info()`, `describe()`, and missing value counts to summarize the dataset. Record the number of missing values per column.

3. **Clean pm25**  
   Coerce invalid `pm25` strings to `NaN`. Show the number of invalid values converted.

4. **Handle missing values**  
   Choose a missing-value strategy for `pm25` and justify it in a short markdown cell. Apply it and confirm the new missing count.

### Part B: Required Analysis Tasks

5. **Data quality analysis**  
   Determine which city has the highest percentage of invalid or missing `pm25` readings. Show the calculation.

6. **Rolling time-series analysis**  
   Compute a 7‑day rolling average of `pm25` per city. Explain in 2–3 sentences why rolling averages help interpretation.

7. **Event detection**  
   Define a "high pollution event" using a percentile‑based threshold of `pm25`. Count events per city and show the threshold you used.

8. **Volatility comparison**  
   Choose two cities and decide which has more volatile air quality over time. Define your metric (e.g., rolling standard deviation) and justify your conclusion.

9. **Reshaping task**  
   Create a pivot table with months as rows and cities as columns showing average `pm25`.

### Part C: Aggregation Tasks

10. **Average pm25 by city**  
    Compute and display average `pm25` by city.

11. **Monthly average pm25 per city**  
    Compute monthly averages for each city.

12. **Hottest day per city**  
    Identify the date of maximum `avg_temp_c` for each city.

### Part D: Visualization

13. **Line plot**  
    Plot monthly `pm25` trends for at least two cities.

14. **Bar chart**  
    Plot overall average `pm25` by city.

15. **One additional plot**  
    Create one more plot of your choice, such as rolling averages or event frequency.

### Part E: Interpretation Questions

Answer the following in short text (no code):
1. Which city shows the most persistent high `pm25` levels, and what evidence supports that?
2. How does missing or invalid data affect your confidence in the results?
3. Does temperature appear related to `pm25` in your analysis? Explain briefly.
4. What is one limitation of using daily averages for air-quality policy decisions?
5. If you had one more dataset to improve this analysis, what would it be and why?

## Hints

- Use `pd.read_csv(..., parse_dates=["date"])` and `set_index("date")`.
- `pd.to_numeric(..., errors="coerce")` is helpful for invalid strings.
- `groupby(["city", pd.Grouper(freq="M")])` works well for monthly aggregation.
- `pivot_table` is ideal for month-by-city views.
- `rolling(7)` can be applied after sorting by date.

## Common Pitfalls and Debugging Notes

Make sure the index is a datetime index before resampling or rolling. If you see unexpected `NaN` values after rolling, check that each city has enough data points. When computing percentages of missing values, use the total count per city as the denominator, not the entire dataset.

## Submission Requirements

Submit the following:
- The completed notebook `m1-09-assessment.ipynb`
- A Pull Request URL with your final assessment solution
