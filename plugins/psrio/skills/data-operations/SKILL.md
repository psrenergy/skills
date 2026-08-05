---
name: data-operations
description: Combine, transform, and compare PSRIO result series in a Lua script — unary transforms, arithmetic, zero-safe division, comparisons, logical operators, max/min, and conditionals. Use when writing expressions over loaded series such as total outflow, capacity factors, unit conversions, or flags for stages meeting a condition.
---

# Index

```lua
--[[Minus]] exp = -exp1
--[[Absolute Value]] exp = exp1:abs()
--[[Round]] exp = exp1:round(digits)
--[[Fill]] exp = exp1:fill(value)
--[[Unit Conversion]] exp = exp1:convert(unit)
--[[Force Unit]] exp = exp1:force_unit(unit)
--[[Addition]] exp = exp1 + exp2
--[[Subtraction]] exp = exp1 - exp2
--[[Multiplication]] exp = exp1 * exp2
--[[Division]] exp = exp1 / exp2
--[[Safe Division]] exp = safe_divide(exp1, exp2)
--[[Power]] exp = exp1 ^ exp2
--[[Equal to]] exp = exp1:eq(exp2)
--[[Not Equal to]] exp = exp1:ne(exp2)
--[[Less-than]] exp = exp1:lt(exp2)
--[[Less-than-or-equals to]] exp = exp1:le(exp2)
--[[Greater-than]] exp = exp1:gt(exp2)
--[[Greater-than-or-equals to]] exp = exp1:ge(exp2)
--[[And]] exp = exp1 & exp2
--[[Or]] exp = exp1 | exp2
--[[Maximum]] exp = max(exp1, exp2)
--[[Minimum]] exp = min(exp1, exp2)
--[[Conditional]] exp = ifelse(exp1, exp2, exp3)
```

Comparisons are methods (`:eq`, `:lt`, ...), not Lua's `==` or `<` operators.
They return 0/1 indicator series, so they compose with arithmetic and feed
`ifelse`.

## Minus

## Absolute Value

```lua
circuit = Circuit();
cirflw = circuit:load("cirflw");
abs_cirflw = cirflw:abs();
```

## Round

## Fill

## Unit Conversion

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_mw = gerter:convert("MW");
```

## Force Unit

```lua
hydro = Hydro();
final_head = hydro:load("cotfin");
final_head_msmn = final_head:force_unit("msmn");
```

## Addition

```lua
hydro = Hydro();
spilled_outflow = hydro:load("qverti");
turbined_outflow = hydro:load("qturbi");
total_outflow = spilled_outflow + turbined_outflow;
```

## Subtraction

```lua
hydro = Hydro();
useful_storage = hydro.max_storage - hydro.min_storage;
```

## Multiplication

```lua
renewable = Renewable();
renewable_generation = renewable:load("gergnd");
renewable_om_cost = renewable_generation * renewable.om_cost;
```

## Division

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_loading = circuit_flow / circuit.capacity;
```

## Safe Division

Returns zero instead of `inf` or `nan` where the denominator is zero. Use it
whenever the denominator is itself a result series.

```lua
renewable = Renewable();
generation = renewable:load("gergnd");
spillage = renewable:load("vergnd");
spillage_proportion = safe_divide(spillage, (spillage + generation));
```

## Power

## Equal to

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_in_max_charge = circuit_flow:abs():eq(circuit.capacity);
```

## Not Equal to

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_not_in_max_charge = circuit_flow:abs():ne(circuit.capacity);
```

## Less-than

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_less_than_the_max_charge = circuit_flow:abs():lt(circuit.capacity);
```

## Less-than-or-equals to

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_less_or_equal_the_max_charge = circuit_flow:abs():le(circuit.capacity);
```

## Greater-than

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_greater_than_the_max_charge = circuit_flow:abs():gt(circuit.capacity);
```

## Greater-than-or-equals to

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_greater_than_or_equal_the_max_charge = circuit_flow:abs():ge(circuit.capacity);
```

## And

## Or

## Maximum

```lua
hydro = Hydro();
turbined_outflow = hydro:load("qturbi");
minimum_turbined_outflow = max(hydro.min_turbining_outflow - turbined_outflow, 0);
```

## Minimum

```lua
hydro = Hydro();
production_factor = hydro:load("fprodt");
available_hydro_capacity = min(hydro.max_turbining_outflow * production_factor, hydro.max_generation_available);
```

## Conditional

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_gt_zero = ifelse(gerter:gt(0.0), 1, 0);
```
