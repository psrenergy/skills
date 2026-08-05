---
name: TODO
description: TODO
---

# Index

```lua
--[[Save]] exp1:save(filename)
--[[Save with Options]] exp1:save(filename, { options... })
--[[Save and Load into an Expression]] exp = exp1:save_and_load(filename)
--[[Save with Options and Load into an Expression]] exp = exp1:save_and_load(filename, { options... })
--[[Save Cache]] exp = exp1:save_cache()
```

## Save

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter:save("example");
```

## Save with Options

| Description               | Syntax    | Default    |
|:--------------------------|:----------|:-----------|
| Save output as BIN/HDR    | `bin`     | `true`     |
| Save output as CSV        | `csv`     | `false`    |
| Save output as DAT        | `dat`     | `false`    |

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter:save("example", { csv = true });
```

## Save and Load into an Expression 

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
example = gerter:save_and_load("example");
```

## Save with Options and Load into an Expression

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
example = gerter:save_and_load("example", { csv = true });
```

## Save Cache

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
cache = gerter:save_cache();
```
