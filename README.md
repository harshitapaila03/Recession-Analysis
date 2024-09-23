# Recession-Analysis


## Introduction
A recession is defined as an economic downturn occurring when there is a sustained decrease in economic activity for two consecutive quarters. This decline often results in reduced consumer spending, business losses, and potential layoffs, as witnessed globally in 2023.

Recessions are typically assessed using various indicators, such as GDP growth, unemployment rates, and consumer spending trends. However, the most straightforward approach is to analyze the monthly GDP growth data.

## Recession Analysis
Recession periods are determined by examining monthly GDP growth data to identify sequences of consecutive negative growth, signaling economic downturns. These patterns are visualized through various charts and graphs to offer a clearer understanding of the timing and impact of recession periods.
## Features
- Data preprocessing and transformation of UK monthly GDP data.
- Identification of recession periods based on consecutive negative GDP growth.
- Visualization of:
  - Monthly GDP growth with highlighted recession periods.
  - Quarterly GDP growth with recession annotations.
  - Recession severity analysis using scatter plots.

## Dataset
The dataset used in this analysis contains the following columns:
- `Time Period`: The month and year of the GDP data point.
- `GDP Growth`: The GDP growth rate for the given month.
## Visualizations

### 1. Monthly GDP Growth with Recession Periods
This line chart displays the monthly GDP growth of the UK. Recession periods, identified by consecutive months of negative growth, are highlighted in red.

![Monthly GDP Growth](images/monthly_gdp_growth.png)

```python
# Code snippet to generate the visualization
fig1 = go.Figure()
fig1.add_trace(go.Scatter(x=data.index, y=data['GDP Growth'], mode='lines+markers', name='GDP Growth',
                          line=dict(color='blue'), marker=dict(size=8)))
for i in range(len(data)):
    if data['Recession'].iloc[i] == 1:
        fig1.add_shape(type="rect",
                       x0=data.index[i-1], y0=min(data['GDP Growth'])-2, 
                       x1=data.index[i], y1=max(data['GDP Growth'])+2,
                       fillcolor="red", opacity=0.3, line_width=0)
fig1.update_layout(title='UK Monthly GDP Growth (2020-2022) with Recession Periods Highlighted',
                   xaxis_title='Time Period',
                   yaxis_title='GDP Growth Rate (%)')
fig1.show()
