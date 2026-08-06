---
name: TODO
description: TODO
---

# Index

```lua
--[[Minus]] exp = -exp1
```

```lua
local thermal = Thermal();
local gerter = thermal:load("gerter");

local hydro = Hydro();
local gerhid = hydro:load("gerhid");

local renewable = Renewable();
local gergnd = renewable:load("gergnd");

local tab = Tab("Tutorial");

-- push charts to tab here --

local dashboard = Dashboard();
dashboard:push(tab);
dashboard:save("tutorial");
```