---
name: TODO
description: TODO
---

# Index

```lua
--[[Aggregate All Agents]] exp = exp1:aggregate_agents(f, label)
--[[Aggregate Agents into Collection]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
--[[]]
```

## Aggregate All Agents

```lua
hydro = Hydro();
gerhid = hydro:load("gerhid");
gerhid_sum = gerhid:aggregate_agents(BY_SUM(), "Total Hydro");
```

## Aggregate Agents into Collection

$$ exp}=exp1:aggregate\_agents}(f}, collection}) $$

Where `collection` is Collection Enumerate.

#### Example

```lua
hydro = Hydro();
gerhid = hydro:load("gerhid");
gerhid_systems = gerhid:aggregate_agents(BY_SUM(), Collection.SYSTEM);
gerhid_buses = gerhid:aggregate_agents(BY_SUM(), Collection.BUSES);
```

## Select One Agent by Name or Index

$$ exp}=exp1:select\_agent}(\text{string or int}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t1 = gerter:select_agent("Thermal 1");
gerter_t2 = gerter:select_agent(2);
```

## Select Mulitple Agents by Names or Indices

$$ exp}=exp1:select\_agents}(\{\text{string or int}, \text{string or int}, ...\}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t1_and_t2 = gerter:select_agents({"Thermal 1", 2});
```

## Select Agents within a Collection

$$ exp}=exp1:select\_agents}(collection}) $$

Where `collection` is Collection Enumerate.

#### Example

```lua
expansion_project = ExpansionProject()
outidec = expansion_project:load("outidec");
outidec_dclinks = outidec:select_agents(Collection.DCLINK);
```

## Select Agents within a Collection Element

$$ exp}=exp1:select\_agents}(collection},string}) $$

Where `collection` is Collection Enumerate and `string` the name of a element that belongs to Collection.

#### Example

```lua
expansion_project = ExpansionProject()
outidec = expansion_project:load("outidec");
outidec_from_S1_system = outidec:select_agents(Collection.SYSTEM, "S1");
```

## Select Agents with a Query

$$ exp}=exp1:select\_agents}(string}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
non_zero_gerter = gerter:select_agents(gerter:ne(0));
```

## Select Agents by Regex

$$ exp}=exp1:select\_agents\_by\_regex}(string}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
UFV_agents = gerter:select_agents_by_regex("(UFV_)(.*)");
```

## Select Agent by Code

$$ exp}=exp1:select\_agent\_by\_code}(string}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
agent = gerter:select_agent_by_code("1");
```

## Select Agents by Code

$$ exp}=exp1:select\_agents\_by\_code}(\{string}\}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
agents = gerter:select_agent_by_code({"1","2"});
```
## Remove One Agent by Name or Index

$$ exp}=exp1:remove\_agent}(\text{string or int}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t2_and_t3 = gerter:remove_agent("Thermal 1");
gerter_t1_and_t2 = gerter:remove_agent(3);
```

## Remove Mulitple Agents by Names or Indices

$$ exp}=exp1:remove\_agents}(\{\text{string or int}, \text{string or int}, ...\}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_t1 = gerter:remove_agents({"Thermal 2", 3});
```

## Rename One Agent

$$ exp}=exp1:rename\_agent}(\text{string}) $$

## Rename Mulitple Agents with One Name

$$ exp}=exp1:rename\_agents}(\text{string}) $$

## Rename Mulitple Agents with Mutiple Names

$$ exp}=exp1:rename\_agents}(\{\text{string}, \text{string}, ...\}) $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_renamed = gerter:rename_agents({"T1", "T2", "T3"});
```

## Rename Mulitple Agents by Adding a Suffix

$$ exp}=exp1:add\_suffix}(\text{string}) $$

## Rename Mulitple Agents by Adding a Prefix

$$ exp}=exp1:add\_prefix}(\text{string}) $$

## Concatenate Agents

$$ exp}=concatenate}(\{exp1}, exp2}, ...\}) $$

#### Example 1

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

$$ exp}=exp1:aggregate\_topology}(f}, topology}) $$

Where `topology` is the following enumerate:

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

#### Example

```lua
hydro = Hydro();
production_factor = hydro:load("fprodt");
production_factor_accumulated = production_factor:aggregate_topology(BY_SUM(), Topology.TURBINED_TO);
```

## Aggregate Topology with Min and Max Levels

$$ exp}=exp1:aggregate\_topology}(f}, topology}, min}, max}) $$

#### Example

```lua
hydro = Hydro();
spillage = hydro:load("qverti");
spillage_parents = spillage:aggregate_topology(BY_SUM(), Topology.TURBINED_FROM, 1, 1);
```

## Replace

$$ exp}=exp1:replace}(exp2}) $$

The agents data from `exp1` will be replace by `exp2` data with the same agents name.

#### Example

```lua
thermal = Thermal();
potter_agent_1 = thermal:load("potter"):select_agent(1);
gerter = thermal:load("gerter");
gerter_replaced = gerter:replace(potter_agent_1);
```

## Select Smallest Agents

$$ exp}=exp1:select\_smallest\_agents}(n}) $$

Where `n` is the number of agents that will be select.

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_smallest = gerter:select_smallest_agents(5);
```

## Select Largest Agents

$$ exp}=exp1:select\_largest\_agents}(n}) $$

Where `n` is the number of agents that will be select.

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_largest = gerter:select_largest_agents(5);
```

## Cumulative Sum Agents

$$ exp}=exp1:cumsum\_agents}() $$

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_sum = gerter:cumsum_agents();
```

## Remove Zeros

$$ exp}=exp1:remove\_zeros}() $$

Remove agents with all data equal to zero.

#### Example

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_without_zeros = gerter:remove_zeros();
```