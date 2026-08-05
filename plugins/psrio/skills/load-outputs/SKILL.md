---
name: TODO
description: TODO
---

# Index

```lua
--[[Loading outputs from collections]] output = collection:load("filename")
--[[Loading outputs from collections (force)]] output = collection:force_load("filename")
```

## Loading outputs with collections

PSRIO can load output data from the PSR models, particularly those in the graph format that can be loaded by PSRIO using the `load` method. Please note that data should be loaded using the specific collection associated with them. The generic collection can load any output with any agent type.

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
fprodt = hydro:load("fprodt");
```

```lua
system = System();

cmgdem = system:force_load("cmgdem");
demand = system:force_load("demand");
```

```lua
thermal = Thermal();

gerter = thermal:force_load("gerter");
coster = thermal:load("coster");
```

```lua
generic = Generic();

objcop = generic:load("objcop");
outdfact = generic:force_load("outdfact");
```