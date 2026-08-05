---
name: TODO
description: TODO
---

# Index

```lua
--[[Aggregate Scenarios]] exp = exp1:aggregate_scenarios(f)
--[[Aggregate Selected Scenarios]] exp = exp1:aggregate_scenarios(f, { scenario,  scenario, ...})
--[[Select One Scenario]] exp = exp1:select_scenario(scenario)
--[[Select One Scenario]] exp = exp1:select_scenario(scenario)
--[[Select Multiple Scenarios]] exp = exp1:select_scenarios({ scenario,  scenario, ...})
--[[Select Scenarios Range]] exp = exp1:select_scenarios(from_scenario,  to_scenario)
--[[Remove Multiple Scenarios]] exp = exp1:remove_scenarios({ scenario,  scenario, ...})
--[[Concatenate Scenarios]] exp = concatenate_scenarios({ exp1,  exp2, ...})
```

## Aggregate Scenarios

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_avg = cmgdem:aggregate_scenarios(BY_AVERAGE());
cmgdem_p90 = cmgdem:aggregate_scenarios(BY_PERCENTILE(90));
```

## Aggregate Selected Scenarios

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_max = cmgdem:aggregate_scenarios(BY_MAX(), {1, 2, 3, 4, 5});
```

## Select One Scenario

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_scenario32 = cmgdem:select_scenario(32);
```

## Select Multiple Scenarios



## Select Scenarios Range

```lua
```

## Remove Multiple Scenarios

```lua
```

## Concatenate Scenarios

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
gerhid_scenario_5 = gerhid:select_scenario(5);
gerhid_scenario_15 = gerhid:select_scenario(15);
gerhid_scenario_25 = gerhid:select_scenario(25);
gerhid_scenarios = concatenate_scenarios(
    gerhid_scenario_5,
    gerhid_scenario_15,
    gerhid_scenario_25
);
```