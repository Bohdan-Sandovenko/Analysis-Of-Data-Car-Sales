# Car Mileage Analysis Project

## Overview

This project aims to analyze and visualize the **average mileage of cars over the years**. The dataset contains information on the **year of manufacture** and **mileage** of various cars. The analysis includes:

- Grouping the data by the **year** of the car and calculating the **average mileage** for each year.
- Visualizing the results with a line plot that shows how the **average mileage** changes over time.
- Adding a **trendline** to highlight the general trend in mileage over the years.

## Data

The dataset contains two key columns:
- **year**: The year the car was manufactured.
- **mileage**: The mileage of the car in kilometers.

## Steps and Visualizations

1. **Data Preprocessing**:
   - The data is grouped by the **year**, and the **average mileage** for each year is calculated.

2. **Visualization**:
   - A **line plot** is created to show the **average mileage** across the years.
   - A **trendline** is added to the scatter plot using **OLS regression** to capture the overall trend.

### Code Overview:

```python
import pandas as pd
import plotly.express as px

# Group by year and calculate the average mileage
df_grouped = df.groupby('year')['mileage'].mean().reset_index()

# Create a line plot for average mileage over the years
fig = px.line(df_grouped, x='year', y='mileage', title='Average Mileage over the Years with Trend Line')

# Add trendline using scatter plot with OLS regression
fig.add_traces(px.scatter(df_grouped, x='year', y='mileage', trendline='ols').data)

# Update plot layout for better readability
fig.update_layout(
    title="Rok i przebieg",  # Polish for "Year and Mileage"
    xaxis_title="Rok",       # "Year"
    yaxis_title="Przebieg",  # "Mileage"
    template="plotly_white",
    xaxis=dict(tickmode='linear', tick0=1980, dtick=5),
    width=1200,
    height=600
)

# Display the plot
fig.show()
