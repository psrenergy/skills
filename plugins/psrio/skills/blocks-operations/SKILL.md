---
name: TODO
description: TODO
---

# Index

```lua
--[[Aggregate Blocks/Hours]] exp = exp1:aggregate_blocks(f)
--[[Select One Block/Hour]] exp = exp1:select_block(int)
--[[Map Blocks into Hours]] exp = exp1:to_hour(f)
--[[Map Hours into Blocks]] exp = exp1:to_block(f)
```

## Aggregate Blocks/Hours

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_agg = cmgdem:aggregate_blocks(BY_AVERAGE());
```

```lua
renewable = Renewable();
gergnd = renewable:load("gergnd");
gergnd_agg = gergnd:aggregate_blocks(BY_SUM());
```

## Select One Block/Hour

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_block21 = cmgdem:select_block(21);
```

## Map Blocks into Hours

```lua
system = System();
cmgdem_block = system:load("cmgdem");
cmgdem_hourly = cmgdem_block:to_hour(BY_REPEATING());
```

## Map Hours into Blocks

```lua
thermal = Thermal();
gerter_hourly = thermal:load("gerter");
gerter_block = gerter_hourly:to_block(BY_SUM());
```