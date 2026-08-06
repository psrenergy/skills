---
name: TODO
description: TODO
---

# Index

```lua
--[[Create a Dashboard]] dashboard = Dashboard()
--[[Push a Tab to a Dashboard]] dashboard:push(tab)
--[[Save a Dashboard]] dashboard:save(string)
--[[Create a Tab]] tab = Tab(label)
--[[Set the Tab Icon]] tab:set_icon(icon)
--[[Disable the Tab]] tab:set_disabled()
--[[Set the Collapse Flag]] tab:set_collapsed(boolean)
--[[Push a Chart to a Tab]] tab:push(chart)
--[[Push a Markdown to a Tab]] tab:push(string)
--[[Push a Tab to a Tab]] tab:push(tab)
```

## Create a Tab

```lua
tab = Tab("Tab title");
```

## Set the Tab Icon

```lua
tab = Tab("Tab title");
tab:set_icon("home");
```

## Disable the Tab

```lua
tab = Tab("Tab title");
tab:set_disabled();
```

## Set the Collapse Flag

```lua
tab = Tab("Tab title");
tab:set_collapsed(true);
```

## Push a Chart to a Tab

```lua
tab = Tab("Tab title");
chart = Chart("Chart title");
tab:push(chart);
```

## Push a Markdown to a Tab

```lua
tab = Tab("Tab title");
tab:push("# Heading 1");
```

## Push a Tab to a Tab

```lua
tab = Tab("Tab title");
subtab = Tab("Sub Tab title");
tab:push(subtab);
```

## Create a Dashboard

```lua
dashboard = Dashboard();
```

## Push a Tab to a Dashboard

```lua
tab = Tab("Tab title");
dashboard = Dashboard();
dashboard:push(tab);
```

## Save a Dashboard

```lua
dashboard = Dashboard();
dashboard:save("example");
```