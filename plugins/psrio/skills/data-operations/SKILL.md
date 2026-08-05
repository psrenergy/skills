---
name: data-operations
description: TODO
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
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
```

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
