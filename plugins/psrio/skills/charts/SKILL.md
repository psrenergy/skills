---
name: TODO
description: TODO
---

# Index

```
--[[Create a Chart]]                             chart = Chart()
--[[Create a Chart with a title]]                chart = Chart(title)
--[[Create a Chart with a title and a subtitle]] chart = Chart(title, subtitle)
--[[Line]]                                       chart:add_line(exp)                               
--[[Line Categories]]                            chart:add_line_categories(exp)                    
--[[Spline]]                                     chart:add_spline(exp)
--[[Column]]                                     chart:add_column(exp)
--[[Column Categories]]                          chart:add_column_categories(exp, label)
--[[Column Stacking]]                            chart:add_column_stacking(exp)
--[[Column Stacking Categories]]                 chart:add_column_stacking_categories(exp, label)
--[[Column Percent]]                             chart:add_column_percent(exp)
--[[Column Percent Categories]]                  chart:add_column_percent_categories(exp)
--[[Column Range]]                               chart:add_column_range(exp1, exp2)
--[[Column Range Categories]]                    chart:add_column_range_categories(exp1, exp2)
--[[Area]]                                       chart:add_area(exp)
--[[Area Stacking]]                              chart:add_area_stacking(exp)
--[[Area Percent]]                               chart:add_area_percent(exp)
--[[Area Range]]                                 chart:add_area_range(exp1, exp2)
--[[Area Spline]]                                chart:add_area_spline(exp)
--[[Area Spline Stacking]]                       chart:add_area_spline_stacking(exp)
--[[Area Spline Percent]]                        chart:add_area_spline_percent(exp)
--[[Area Spline Range]]                          chart:add_area_spline_range(exp1, exp2)
--[[Error Bar]]                                  chart:add_error_bar(exp1, exp2)
--[[Pie]]                                        chart:add_pie(exp)
--[[Histogram]]                                  chart:add_histogram(exp)
--[[Heatmap]]                                    chart:add_heatmap(exp)
--[[Heatmap Series]]                             chart:add_heatmap_series(exp)
--[[Scatter]]                                    chart:add_scatter(exp1, exp2, label)
--[[Probability of Exceedance]]                  chart:add_probability_of_exceedance(exp)
--[[Probability of Non Exceedance]]              chart:add_probability_of_nonexceedance(exp)
--[[Cumulative Distribution Function]]           chart:add_cumulative_distribution_function(exp)
--[[Box Plot]]                                   chart:add_box_plot(exp1, exp2, exp3, exp4, exp5)
```


### Line

```lua
local chart = Chart("Line");
chart:add_line(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Spline

```lua
local chart = Chart("Spline");
chart:add_spline(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Column

```lua
local chart = Chart("Column");
chart:add_column(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Column Categories

```lua
local chart = Chart("Column Categories");
chart:add_column_categories(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), Collection.SYSTEM), "Thermal");
chart:add_column_categories(gerhid:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), Collection.SYSTEM), "Hydro");
chart:add_column_categories(gergnd:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), Collection.SYSTEM), "Renewable");
tab:push(chart);
```

### Column Stacking

```lua
local chart = Chart("Column Stacking");
chart:add_column_stacking(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Column Stacking Categories

```lua
local chart = Chart("Column Stacking Categories");
chart:add_column_stacking_categories(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), Collection.SYSTEM), "Thermal");
chart:add_column_stacking_categories(gerhid:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), Collection.SYSTEM), "Hydro");
chart:add_column_stacking_categories(gergnd:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), Collection.SYSTEM), "Renewable");
tab:push(chart);
```

### Column Percent

```lua
local chart = Chart("Column Percent");
chart:add_column_percent(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Column Range

```lua
local chart = Chart("Column Range");
chart:add_column_range(
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p10"):aggregate_scenarios(BY_PERCENTILE(10)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p90"):aggregate_scenarios(BY_PERCENTILE(90))
);
tab:push(chart);
```

### Area

```lua
local chart = Chart("Area");
chart:add_area(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Area Stacking

```lua
local chart = Chart("Area Stacking");
chart:add_area_stacking(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Area Percent

```lua
local chart = Chart("Area Percent");
chart:add_area_percent(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Area Range

```lua
local chart = Chart("Area Range");
chart:add_area_range(
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p10"):aggregate_scenarios(BY_PERCENTILE(10)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p90"):aggregate_scenarios(BY_PERCENTILE(90))
);
tab:push(chart);
```

### Area Spline

```lua
local chart = Chart("Area Spline");
chart:add_area_spline(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Area Spline Stacking

```lua
local chart = Chart("Area Spline Stacking");
chart:add_area_spline_stacking(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Area Spline Percent

```lua
local chart = Chart("Area Spline Percent");
chart:add_area_spline_percent(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):select_largest_agents(5));
tab:push(chart);
```

### Area Spline Range

```lua
local chart = Chart("Area Spline Range");
chart:add_area_spline_range(
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p10"):aggregate_scenarios(BY_PERCENTILE(10)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p90"):aggregate_scenarios(BY_PERCENTILE(90))
);
tab:push(chart);
```

### Error Bar

```lua
local chart = Chart("Error Bar");
chart:add_error_bar(
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p10"):aggregate_scenarios(BY_PERCENTILE(10)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p90"):aggregate_scenarios(BY_PERCENTILE(90))
);
tab:push(chart);
```

### Pie

```lua
local chart = Chart("Pie");
chart:add_pie(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_stages(BY_SUM()));
tab:push(chart);
```

### Histogram

```lua
local chart = Chart("Histogram");
chart:add_histogram(gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "Total"));
tab:push(chart);
```

### Heatmap (Hourly)

```lua
local chart = Chart("Heatmap (Hourly)");
chart:add_heatmap(gerter:aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), "total"));
tab:push(chart);
```

### Heatmap (Daily)

```lua
local chart = Chart("Heatmap (Daily)");
chart:add_heatmap(gerter:reshape_stages(Profile.DAILY):aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), "total"));
tab:push(chart);
```

### Heatmap Series

```lua
local chart = Chart("Heatmap Series");
chart:add_heatmap_series(gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "total"));
tab:push(chart);
```

### Scatter Plot
```lua
local chart = Chart("Scatter Plot");
local x = gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "Thermal"):aggregate_scenarios(BY_AVERAGE())
local y = gerhid:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "Hydro"):aggregate_scenarios(BY_AVERAGE())
chart:add_scatter(x, y, "Label");
tab:push(chart);
```

### Probability of Exceedance

```lua
local chart = Chart("Probability of Exceedance");
chart:add_probability_of_exceedance(gerter:aggregate_blocks(BY_SUM()));
tab:push(chart);
```

### Probability of Non Exceedance

```lua
local chart = Chart("Probability of Non Exceedance");
chart:add_probability_of_nonexceedance(gerter:aggregate_blocks(BY_SUM()));
tab:push(chart);
```

### Cumulative Distribution Function

```lua
local chart = Chart("Cumulative Distribution Function");
chart:add_cumulative_distribution_function(gerter:aggregate_blocks(BY_SUM()));
tab:push(chart);
```

### Box Plot

```lua
local chart = Chart("Box Plot");
chart:add_box_plot(
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "thermal"):aggregate_scenarios(BY_MIN()),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "thermal"):aggregate_scenarios(BY_PERCENTILE(25)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "thermal"):aggregate_scenarios(BY_PERCENTILE(50)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "thermal"):aggregate_scenarios(BY_PERCENTILE(75)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "thermal"):aggregate_scenarios(BY_MAX())
);
tab:push(chart);
```

### Multiple (Line and Area Range)

```lua
local chart = Chart("Multiple (Line and Area Range)");
chart:add_area_range(
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p10"):aggregate_scenarios(BY_PERCENTILE(10)),
    gerter:aggregate_blocks(BY_SUM()):aggregate_agents(BY_SUM(), "p90"):aggregate_scenarios(BY_PERCENTILE(90))
);
chart:add_line(
    gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), "avg")
);
tab:push(chart);
```


### Multiple (Line and Column)

```lua
local chart = Chart("Multiple (Line and Column)");
chart:add_column(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), "column"));
chart:add_line(gerter:aggregate_blocks(BY_SUM()):aggregate_scenarios(BY_AVERAGE()):aggregate_agents(BY_SUM(), "line"));
tab:push(chart);
```

