---
name: TODO
description: TODO
---

# Index

```lua
--[[Aggregate All Agents]] exp = exp1:aggregate_agents(f, label)
--[[Aggregate Agents into Collection]] exp = exp1:aggregate_agents(f,  collection)
--[[Select One Agent by Name or Index]] exp = exp1:select_agent(name or index)
--[[Select Mulitple Agents by Names or Indices]] exp = exp1:select_agents({name or index, name or index, ...})
--[[Select Agents within a Collection]] exp = exp1:select_agents(collection)
--[[Select Agents within a Collection Element]] exp = exp1:select_agents(collection, name)
--[[Select Agents with a Query]] exp = exp1:select_agents(query)
--[[Select Agents by Regex]] exp = exp1:select_agents_by_regex(regex)
--[[Select Agent by Code]] exp = exp1:select_agent_by_code(code)
--[[Select Agents by Code]] exp = exp1:select_agents_by_code({code, code, ...})
--[[Remove One Agent by Name or Index]] exp = exp1:remove_agent(name or index)
--[[Remove Mulitple Agents by Names or Indices]] exp = exp1:remove_agents({name or index, name or index, ...})
--[[Rename One Agent]] exp = exp1:rename_agent(name)
--[[Rename Mulitple Agents with One Name]] exp = exp1:rename_agents(name)
--[[Rename Mulitple Agents with Mutiple Names]] exp = exp1:rename_agents({name, name, ...})
--[[Rename Mulitple Agents by Adding a Suffix]] exp = exp1:add_suffix(suffix)
--[[Rename Mulitple Agents by Adding a Prefix]] exp = exp1:add_prefix(prefix)
--[[Concatenate Agents]] exp = concatenate({ exp1,  exp2, ...})
--[[Aggregate Topology]] exp = exp1:aggregate_topology(f,  topology)
--[[Aggregate Topology with Min and Max Levels]] exp = exp1:aggregate_topology(f,  topology,  min,  max)
--[[Replace]] exp = exp1:replace(exp2)
--[[Select Smallest Agents]] exp = exp1:select_smallest_agents(n)
--[[Select Largest Agents]] exp = exp1:select_largest_agents(n)
--[[Cumulative Sum Agents]] exp = exp1:cumsum_agents()
--[[Remove Zeros]] exp = exp1:remove_zeros()
```

## Aggregate All Agents

```lua
hydro = Hydro();
gerhid = hydro:load("gerhid");
gerhid_sum = gerhid:aggregate_agents(BY_SUM(), "Total Hydro");
```

## Aggregate Agents into Collection

```lua
hydro = Hydro();
gerhid = hydro:load("gerhid");
gerhid_systems = gerhid:aggregate_agents(BY_SUM(), Collection.SYSTEM);
gerhid_buses = gerhid:aggregate_agents(BY_SUM(), Collection.BUSES);
```

## Select One Agent by Name or Index

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t1 = gerter:select_agent("Thermal 1");
gerter_t2 = gerter:select_agent(2);
```

## Select Mulitple Agents by Names or Indices

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t1_and_t2 = gerter:select_agents({"Thermal 1", 2});
```

## Select Agents within a Collection

```lua
expansion_project = ExpansionProject()
outidec = expansion_project:load("outidec");
outidec_dclinks = outidec:select_agents(Collection.DCLINK);
```

## Select Agents within a Collection Element

```lua
expansion_project = ExpansionProject()
outidec = expansion_project:load("outidec");
outidec_from_S1_system = outidec:select_agents(Collection.SYSTEM, "S1");
```

## Select Agents with a Query

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
non_zero_gerter = gerter:select_agents(gerter:ne(0));
```

## Select Agents by Regex

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
UFV_agents = gerter:select_agents_by_regex("(UFV_)(.*)");
```

## Select Agent by Code

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
agent = gerter:select_agent_by_code("1");
```

## Select Agents by Code

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
agents = gerter:select_agent_by_code({"1","2"});
```
## Remove One Agent by Name or Index

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t2_and_t3 = gerter:remove_agent("Thermal 1");
gerter_t1_and_t2 = gerter:remove_agent(3);
```

## Remove Mulitple Agents by Names or Indices

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t1 = gerter:remove_agents({"Thermal 2", 3});
```

## Rename One Agent

## Rename Mulitple Agents with One Name

## Rename Mulitple Agents with Mutiple Names

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_renamed = gerter:rename_agents({"T1", "T2", "T3"});
```

## Rename Mulitple Agents by Adding a Suffix

## Rename Mulitple Agents by Adding a Prefix

## Concatenate Agents

```lua
hydro = Hydro();
thermal = Thermal();
renewable = Renewable();

gerhid = hydro:load("gerhid");
gerter = thermal:load("gerter");
gergnd = renewable:load("gergnd");
generation = concatenate(gerhid, gerter, gergnd);
```

## Aggregate Topology

| Topologies                     |
|:------------------------------:|
| `Topology.CONTROLLED_BY`       | 
| `Topology.TURBINED_TO`         | 
| `Topology.TURBINED_FROM`       | 
| `Topology.SPILLED_TO`          |
| `Topology.SPILLED_FROM`        |  
| `Topology.FILTRATION_TO`       | 
| `Topology.ASSOCIATED_RESERVOIR`| 
| `Topology.NEUTRAL`             |
| `Topology.STORED_ENERGY_TO`    |

```lua
hydro = Hydro();
production_factor = hydro:load("fprodt");
production_factor_accumulated = production_factor:aggregate_topology(BY_SUM(), Topology.TURBINED_TO);
```

## Aggregate Topology with Min and Max Levels

```lua
hydro = Hydro();
spillage = hydro:load("qverti");
spillage_parents = spillage:aggregate_topology(BY_SUM(), Topology.TURBINED_FROM, 1, 1);
```

## Replace

```lua
thermal = Thermal();
potter_agent_1 = thermal:load("potter"):select_agent(1);
gerter = thermal:load("gerter");
gerter_replaced = gerter:replace(potter_agent_1);
```

## Select Smallest Agents

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_smallest = gerter:select_smallest_agents(5);
```

## Select Largest Agents

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_largest = gerter:select_largest_agents(5);
```

## Cumulative Sum Agents

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_sum = gerter:cumsum_agents();
```

## Remove Zeros

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_without_zeros = gerter:remove_zeros();
```