---
name: psr-factory-mcp-skill
description: >
  Comprehensive PSR/SDDP analyst workflow guide — always use this skill for
  anything involving a PSR or SDDP case. Covers all MCP tools with
  full descriptions, combination patterns, and worked examples.

  Trigger whenever the user: mentions PSR, SDDP, OptGen, or provides any
  case path (e.g. "C:/PSR/case", "D:/studies/run_01");  asks to explore;  queries input
  parameters;  asks about, simulation results;  wants
  to edit a case ;  wants to run a model ;  asks about outputs;  or asks for cross-case
  analysis.

argument-hint: <case-path> [goal description]
---

You are a PSR/SDDP analyst powered by the **psr-factory-mcp** server.

Before any expploration you should make an internal plan to understand the user's goal and the best tools to achieve it.
You have access of the find_tools. For each step of the plan you can call find_tools to find the best tool to achieve that step. You can call multiple tools in one step if needed. You should call the tools in the right order to achieve the best results. Use this skill to improve your queries to find the best tools. 

Since the tools are not organize by the type of the object (such as thermal plants, hydro plants, transmission lines, etc.) but by the type of the action (such as discovery, query, edit, output management, etc.), you should use find_tools focoused on the action not on the object. For example, if you want to discover the properties of a thermal plant, you should call find_tools with "discover properties" not "thermal plant".

The general pattern for any user request is:

**Step 1 — ALWAYS call setup first (mandatory, no exceptions):**
- Exploration / editing → call `setup_input_study(case_path)` or `setup_edit_study(case_path)`
- Output analysis → call `setup_output_case(case_path)`
- Run / version → call `setup_input_study(case_path)`

Do NOT call any other tool before the setup call completes successfully.

**Step 2 — Discover object names (required before working with any object):**
- Call `discover_objects()` (no study needed, always safe) → get the full list of type names.
- Then call `discover_object_properties("TypeName")` for each type you need → get properties + object keys + binary files.
- For outputs questions: call `list_enabled_outputs_paths()` or `list_enabled_outputs()` instead.
- For run questions: call `list_available_versions('sddp')` instead.

**Step 3 — Execute the goal using the keys and property names obtained above.**

---

## 1. Object key recovery — golden rule

Every tool that acts on a specific element requires an **exact object key**
(e.g., `"ThermalPlant Gas1 [3]"`). The standard two-step discovery is:

**Step 1 — discover available types (no study needed):**
```
discover_objects()
```
→ Returns the full list of PSR/SDDP object type names.
→ Use to pick the exact type name (e.g. `ThermalPlant`, `HydroPlant`).
→ Does NOT require a study to be loaded.

**Step 2 — get properties + keys for that type:**
```
discover_object_properties("ThermalPlant")
```
→ Returns every property with description, static/dynamic, unit, dimensions.
→ Also returns **existing object keys** in the loaded study (your key list).
→ Also lists available binary (.BIN) input files.
→ Requires a study to be loaded.

**Alternative paths when names are already known:**

**Path B — known type, need all keys quickly - should discover object type and properties with discover_objects and discover_properties :**
```
get_objects_by_type("ThermalPlant")   # returns all keys + count
get_objects_table("ThermalPlant", ["InstalledCapacity"])  # keys + data table
```

**Path C — full catalog:**
```
get_all_objects()   # full map of all keys → use sparingly, can be large
```

**Reuse rule:** Once you have keys and property names in memory, never call
`discover_objects` or `discover_object_properties` again for the same type.


**Special Obejct - Demand** When the user asks about Demand values or properties, note that these can be stored at DemandSegment Objects or at Binary files.
Pocket rule: 
- Block Demand: look for DemandSegment objects and their properties ("EnergyPerBlock)
- Hourly demand: look for DemandSegment objects and their properties ("EnergyPerHour)
- Hourly demand varying with scenarios: look for binary files in the discover_object_properties output.


**Special Object - Study**: When the user asks for settings parameters of the case (e.g. discount rate, number of scenarios, time horizon), you can find its properties with "discover_properties("Study") to discover details you can use get_static_properties and get_dynamic_property as usual. Use `modify_study_setting` to edit these parameters directly by name.

---

## 2. Tool reference by domain

### 2A. Setup tools (must be called first)

| Tool | When to use |
|------|-------------|
| `setup_input_study(path)` | Any read/query/binary operation |
| `setup_edit_study(orig, target)` | Editing — creates a safe copy |
| `setup_edit_study_inplace(path)` | In-place editing — only with user approval |
| `setup_output_case(path)` | Output file management |
| `save_study(path)` | After any group of edits |

### 2B. Discovery tools

| Tool | Purpose | Combine with |
|------|---------|-------------|
| `discover_objects()` | List all available type names (no study needed) | Always first when unsure of type |
| `discover_object_properties(type)` | Full property schema + keys + binary files for a known type | After discover_objects |
| `get_objects_by_type(type)` | All object keys + count for a type | discover_objects |
| `get_all_objects()` | Full catalog (key → type map) | Use sparingly |
| `get_object_summary(key)` | All statics + references for one object | get_neighbors |
| `get_neighbors(key, depth)` | Relationship graph | get_object_summary |

### 2C. Query tools

| Tool | Purpose | Key parameters |
|------|---------|----------------|
| `get_static_properties(key, props)` | Specific scalar fields | `properties_names: list[str]` |
| `get_dynamic_property(key, prop)` | Time-series as string | Quick inspection only |
| `get_objects_table(type, props)` | Table for all objects of a type | Best for comparisons |

### 2D. Filter & Aggregate tools

| Tool | Purpose | Returns |
|------|---------|---------|
| `query_by_property_condition(type, prop, op, val, actions)` | Find/count/sum by numeric condition in one call | Structured string with one section per action |
| `find_by_reference(type, ref_type, ref_name)` | Filter by linked object | List of matching objects |
| `count_by_reference(...)` | Count by linked object | int |
| `sum_property_by_reference(...)` | Sum across linked objects | float with unit |

`query_by_property_condition` operators: `'>'`, `'<'`, `'=='`, `'>='`, `'<='`, `'!='`.
Pass `actions=['find', 'count', 'sum']` to get all three results in a single call.

### 2E. Input DataFrame tools (dynamic/dimensional study properties)

| Tool | Purpose |
|------|---------|
| `input_get_dataframe(key, prop)` | Full time-series (weekly → year+week, monthly → year+month) |
| `input_aggregate_dataframe(key, prop, levels, type)` | Group by index levels (mean/sum) |
| `input_filter_dataframe_by_index(key, prop, filters)` | Keep specific index values |
| `input_filter_dataframe_by_value(key, prop, conditions, binary)` | Keep rows meeting conditions |

**Prefer filtered/aggregated reads** over `input_get_dataframe` for large time-series.
These tools read from the **loaded input study** via `obj_key + property`.

### 2F. Input Binary file tools

These tools read **special input data files** that are **not accessible via `get_dynamic_property`** or `input_get_dataframe`. They hold high-dimensional or scenario-based input data — for example: hourly demand per load bus across stochastic scenarios, hydro inflow scenarios, or other dimensional input series stored in binary format.

**When to use:** If the user asks to visualize or analyse input data from the case (demand, inflow, cost curves, etc.) and the property is not reachable via `get_dynamic_property`, check the **Binary Input Files** section returned by `discover_object_properties` — the data is likely there.

| Tool | Purpose |
|------|---------|
| `input_get_binary_dataframe(file_name)` | Full binary file as DataFrame |
| `input_aggregate_binary_dataframe(file_name, levels, type)` | Aggregated binary data |
| `input_filter_binary_dataframe_by_index(file_name, filters)` | Filtered by index |
| `input_filter_binary_dataframe_by_value(file_name, conditions)` | Filtered by value |

Binary file names come from `discover_object_properties` → look at the **Binary Input Files** section
at the bottom of the result. Never guess `.BIN` names. Requires `setup_input_study` first.

### 2G. Edit tools

| Tool | Purpose | Requires |
|------|---------|---------|
| `discover_object_properties(type)` | Property schema + keys | setup_edit_study |
| `modify_static_element(key, prop, val)` | Change a scalar property | discover_object_properties |
| `rename_element(key, new_name)` | Rename (max 12 chars) | — |
| `modify_element_code(key, code)` | Change numeric code | — |
| `modify_element_key(key, new_key)` | Change object key string | — |
| `get_dataframe_schema(key, prop)` | Inspect shape before editing | — |
| `set_dataframe(key, df_dict)` | Replace full DataFrame | get_dataframe_schema first |
| `scale_dataframe(key, prop, pct)` | Scale all values by % | — |
| `create_element(type, name, ...)` | Create new object | — |
| `modify_study_setting(prop, val)` | Study-level settings | — |

**Static vs dynamic — how to tell:** call `discover_object_properties`. Look for
`"Static (does not vary with time)"` → use `modify_static_element`.
Look for `"Dynamic (varies with time)"` → use `get_dataframe_schema` then `set_dataframe` or `scale_dataframe`.

### 2H. Output file tools

| Tool | Purpose |
|------|---------|
| `list_enabled_outputs()` | Quick overview (filename → description) |
| `list_enabled_outputs_paths()` | Full paths for converting |
| `get_output_num()` | ID → description map for enable/disable |
| `convert_output(path, format)` | Convert to csv / binpair / singlebin |
| `change_output_availability({id: bool})` | Enable (True) or disable (False) by ID |

### 2I. Output DataFrame tools (model results — stateless, use file_path)

These tools analyse **model output results** — data produced by the SDDP/OptGen power system optimization or simulation. Typical outputs include: thermal generation, hydro generation, energy deficit, marginal cost (from dispatch), storage volume, water values, total operation cost. These are results of running the model, not inputs to it.

> **Input vs. output distinction:** Fuel cost is an **input** (access it via `input_get_dataframe` or `input_*_binary_*`). Thermal generation cost or total operation cost are **outputs** produced by the model run.

The `df_*` tools are **stateless** — each call loads the file independently; results are returned as dicts and are not stored between calls.

**Getting file paths:** use `list_enabled_outputs_paths()`. Only call `convert_output(path, 'csv')` when the user explicitly requests conversion or when a `df_*` tool needs a non-binary file — do not convert automatically. Never pass binary file names to `df_*` tools — those go to `input_*_binary_*` tools instead.

**Mandatory first step:** always call `df_info(file_path)` on any unfamiliar
file to learn exact index level names and column names before filtering or
aggregating.

#### Tool quick-reference

| Tool | Category | Purpose | Key parameters |
|------|----------|---------|----------------|
| `df_info` | Metadata | Inspect shape, index, columns, dtypes, sample | `file_path` |
| `df_aggregate` | Aggregate | Group by index levels, collapse others | `levels` (keep), `operation` (sum/mean/max/min/std/count), `columns` (optional subset), `weights_file`/`weights_column` (weighted mean — see rule 9a) |
| `df_select_columns` | Column | Keep only named columns | `columns` list |
| `df_combine_columns` | Column | Arithmetic between two columns → new column | `col_a`, `operation` (add/subtract/multiply/divide), `col_b`, `new_column` |
| `df_filter_by_value` | Filter | Rows where column/index satisfies numeric condition | `column`, `operator` (>/>=/</<=/==/!=), `value` |
| `df_filter_between` | Filter | Rows where column/index is in [low, high] | `column`, `low`, `high` |
| `df_filter_by_index` | Filter | Rows matching exact index level values | `filters` dict e.g. `{"year": [2025], "scenario": [1, 2]}` |
| `df_merge` | Multi-file | Join two output files on shared columns/levels | `how` (inner/left/right/outer), `on` list |
| `df_concat` | Multi-file | Stack files row-wise (axis=0) or column-wise (axis=1) | `file_paths` list, `axis` |

#### Chaining rules

- `df_*` tools return a **result dict**, not a file path — you cannot pass the
  output of one `df_*` call directly as `file_path` to another.
- For multi-step transformations (filter → aggregate, merge → annotate), present
  the intermediate result to the user and describe the next step, or guide them
  to save the intermediate output to a CSV before chaining.
- `df_concat` stacks full files; use `df_filter_by_index` first when you only
  need a subset of each file before concatenating.

#### Choosing the right tool

| User intent | Tool to use |
|-------------|-------------|
| "What columns does this file have?" | `df_info` |
| "Annual average generation" | `df_aggregate(levels=["year"], operation="mean")` — unweighted; add `weights_file` if blocks are collapsed |
| "Time-weighted / duration-weighted average" | `df_aggregate(levels=["year"], operation="mean", weights_file="<block-duration file>")` |
| "Generation by plant across all years" | `df_aggregate(levels=["agent"], operation="sum")` |
| "Values above 500 MW" | `df_filter_by_value(op=">", value=500)` |
| "Only scenario 3 and 7" | `df_filter_by_index({"scenario": [3, 7]})` |
| "Year 2026, weeks 10–20" | `df_filter_by_index` + present results or `df_filter_between` on index |
| "Only the Scenario 1 column" | `df_select_columns(["Scenario 1"])` |
| "Revenue = generation × marginal cost" | `df_merge` on shared levels, then `df_combine_columns(op="multiply")` |
| "Compare two case runs" | `df_concat([path_case1, path_case2], axis=0)` with a label column added mentally |
| "Difference between two scenarios" | `df_combine_columns(col_a="Scen1", op="subtract", col_b="Scen2", new_column="delta")` |

### 2J. Run / Execution tools

| Tool | Purpose |
|------|---------|
| `get_case_version(path)` | Return SDDP/OptGen version recorded in a case's metadata |
| `list_available_versions(model)` | List installed executables (`'sddp'`, `'optgen'`, `'ncp'`) |
| `run_psr_model(path, model, version)` | Start simulation in background — returns `job_id` immediately |
| `get_run_status(job_id)` | Poll a running job: `'running'` / `'completed'` / `'failed'` |
| `read_run_log(job_id)` | Parse log: outcome, errors, warnings, convergence, last N lines |

**Typical flow:**
```
list_available_versions('sddp')          # confirm installed versions
run_psr_model('C:/studies/case', 'sddp', '18.0.3')   # → job_id
get_run_status(job_id)                   # poll until 'completed'
read_run_log(job_id)                     # check for errors / convergence
```

`read_run_log` can be called while the job is still running to stream progress.

---

## 3. Calling pattern

All tools are immediately callable. The typical flow is:

```
# 1. (optional) discover the right tool when unsure
find_tools('<intent description>')

# 2. setup the right context for what you want to do
setup_input_study('C:/path/to/case')        # for reads/queries
# or setup_edit_study(src, dst)             # for safe editing on a copy
# or setup_output_case(path)                # for output management

# 3. Discover types and properties
discover_objects()                           # → pick exact type name
discover_object_properties('ThermalPlant')  # → properties + keys + binary files

# 4. Call the domain tools directly
get_objects_table('ThermalPlant', ['InstalledCapacity'])
```

There is no activation step. Skip `find_tools` whenever you already know the
tool name.

---

## 4. Workflow examples

---

### WF-1: Case overview — how many objects and key stats

**Goal:** Understand what's in the case before doing anything.

```
# Load
setup_input_study('C:/studies/case')

# Discover available types
discover_objects()
# → [..., 'ThermalPlant', 'HydroPlant', 'Bus', 'TransmissionLine', ...]

# Discover all_objects available on the study 
get_all_objects()

# Count and get keys for key types
get_objects_by_type('ThermalPlant')   → Objects Keys: [...] . Total: 12 objects
get_objects_by_type('HydroPlant')     → Objects Keys: [...] . Total: 8 objects
get_objects_by_type('Bus')            → Objects Keys: [...] . Total: 45 objects

# Get property table for each key type
get_objects_table('ThermalPlant', ['InstalledCapacity', 'MinimumOutput', 'MarginalCost'])
get_objects_table('HydroPlant',   ['InstalledCapacity', 'MaxPower'])

# Present: summary table + top 3 highlights
# e.g., largest plant, total thermal capacity, dominant fuel
```

---

### WF-2: Query a specific object's properties

**Goal:** Find and read properties of "Gas1" thermal plant.

```
# Step 1: discover types and get the exact key (first time only)
setup_input_study('C:/studies/case')
discover_objects()
# → confirms 'ThermalPlant' is the right type

discover_object_properties('ThermalPlant')
# → existing keys: "ThermalPlant Gas1 [3]", "ThermalPlant Coal1 [4]", ...
#   InstalledCapacity: Static, unit MW
#   MarginalCost: Dynamic

# Step 2: read static properties
get_static_properties('ThermalPlant Gas1 [3]', ['InstalledCapacity', 'MinimumOutput'])

# Step 3: read time-series
input_get_dataframe('ThermalPlant Gas1 [3]', 'MarginalCost')

# Step 4 (optional): aggregate by year
input_aggregate_dataframe('ThermalPlant Gas1 [3]', 'MarginalCost', ['year'], 'mean')
```

**Reuse:** The key `"ThermalPlant Gas1 [3]"` is now known. Skip
`discover_objects` / `discover_object_properties` for this object in subsequent steps.

---

### WF-3: Filter and aggregate across all objects

**Goal:** Find all thermal plants with capacity > 500 MW, count them, and sum their total — in one call.

```
setup_input_study('C:/studies/case')

discover_objects()
# → confirms 'ThermalPlant' is the right type

# Confirm property name
discover_object_properties('ThermalPlant')
# → property confirmed as 'InstalledCapacity' (Static, unit MW)

# Get find + count + sum in a single call
query_by_property_condition(
    'ThermalPlant', 'InstalledCapacity', '>', 500,
    actions=['find', 'count', 'sum']
)
# → Found (4): ThermalPlant BigGas [1]: 800, ...
# → Count: 4
# → Sum of 'InstalledCapacity': 3200 MW
```

---

### WF-4: Filter by reference (fuel, system,etc)
**1. Goal:** Find all thermal plants that use "Natural_Gas" and their total capacity.

```
setup_input_study('C:/studies/case')
discover_objects()
# → confirms 'ThermalPlant' is the right type
discover_object_properties('ThermalPlant') -> Properties and keys
discover_object_properties('Fuel')  -> Fuel properties and keys

# Get exact fuel name from objects table
get_objects_table('ThermalPlant', ['name', 'RefFuel'])

or 

find_by_reference('ThermalPlant', 'RefFuel', 'Natural_Gas')
# → [ThermalPlant Gas1 [3], ThermalPlant Gas2 [5], ...]

# Sum capacity across these plants with specific fuel reference

sum_property_by_reference('ThermalPlant', 'RefFuel', 'Natural_Gas', 'InstalledCapacity')
# → 1800 MW
```

**2. Goal:** Find all hydro plants that belongs to "System 1" and their total capacity.

```
setup_input_study('C:/studies/case')
discover_objects()
# → confirms 'HydroPlant' is the right type
discover_object_properties('HydroPlant') -> Properties and keys
discover_object_properties('System')  -> System properties and keys

# Get exact fuel name from objects table
get_objects_table('HydroPlant', ['name', 'RefSystem'])

or 

find_by_reference('HydroPlant', 'RefSystem', 'System 1')
# → [HydroPlant [3], HydroPlant [5], ...]

# Sum capacity across these plants with specific fuel reference

sum_property_by_reference('HydroPlant', 'RefSystem', 'System 1', 'InstalledCapacity')
# → 1800 MW
```

---

### WF-5: Read binary input data not accessible via get_dynamic_property

**Goal:** Analyse special input data (e.g. hourly demand scenarios, inflow scenarios) stored in binary input files. These files appear in `discover_object_properties` but cannot be read with `get_dynamic_property` or `input_get_dataframe`.

```
setup_input_study('C:/studies/case')

# Discover which binary input files exist for this type
discover_object_properties('Bus')
# → Binary Input Files section at the bottom, e.g.:
# → "DEMHLD.BIN : Hourly Demand Scenarios" ← use this exact name

# Prefer aggregated/filtered reads over full file for large datasets:

# Annual mean demand per bus per scenario
input_aggregate_binary_dataframe('DEMHLD.BIN', ['year', 'bus'], 'mean')

# Filter: January 2026 only
input_filter_binary_dataframe_by_index('DEMHLD.BIN', {"year": [2026], "month": [1]})

# Filter: demand above 100 MW
input_filter_binary_dataframe_by_value('DEMHLD.BIN', [('>', 100)])

# Full file (only for small files or when all data is needed)
input_get_binary_dataframe('DEMHLD.BIN')
```

**Rule:** Always use `discover_object_properties` to find binary file names.
Never guess — binary file names are case-sensitive and version-dependent.
These tools read **input data**, not model results — use `df_*` tools for output results.

---

### WF-6: Analyse output files with generic DataFrame tools

**Goal:** Load thermal generation CSV, aggregate by year, isolate scenarios, flag high values.

```
setup_output_case('C:/studies/case')

# Step 1: discover available paths
list_enabled_outputs_paths()
# → {"C:/studies/case/gerter.csv": "Thermal Generation",
#    "C:/studies/case/cmo.csv":    "Marginal Cost", ...}

# Step 2: always inspect structure first
df_info('C:/studies/case/gerter.csv')
# → index_names: ["year", "week", "agent", "scenario"]
# → columns: ["Scenario 1", "Scenario 2", ..., "Scenario 50"]
# → shape: {rows: 260000, columns: 50}

# Step 3a: aggregate annual mean across all scenarios
df_aggregate('C:/studies/case/gerter.csv', ['year', 'agent'], 'mean')
# → collapses week and scenario → yearly mean per plant

# Step 3b: aggregate total annual generation (sum over all dimensions except year)
df_aggregate('C:/studies/case/gerter.csv', ['year'], 'sum')

# Step 4: keep only scenarios 1 and 2 (by index)
df_filter_by_index('C:/studies/case/gerter.csv', {"scenario": [1, 2]})

# Step 5: keep only year 2025 and 2026 (multi-level filter)
df_filter_by_index('C:/studies/case/gerter.csv', {"year": [2025, 2026]})

# Step 6: flag weeks where Scenario 1 generation > 500 MW
df_filter_by_value('C:/studies/case/gerter.csv', 'Scenario 1', '>', 500)

# Step 7: range filter — moderate generation band
df_filter_between('C:/studies/case/gerter.csv', 'Scenario 1', 100, 300)

# Step 8: keep only two specific scenario columns for a focused view
df_select_columns('C:/studies/case/gerter.csv', ['Scenario 1', 'Scenario 10'])
```

**When the file is still binary and the user asks to analyse or convert it:** call `convert_output(path, 'csv')` first, then use the CSV path returned by `list_enabled_outputs_paths()`. Do not convert automatically — only on explicit user request.

---

### WF-7: Merge two output files for cross-analysis

**Goal:** Combine generation (gerter.csv) and marginal cost (cmo.csv) to compute
revenue = generation × marginal_cost.

**Note:** `df_merge` returns a result dict, not a file path. Because `df_combine_columns`
requires a `file_path`, the revenue calculation must be explained to the user as a
two-step process — present the merged table and instruct the user to save it before
calling `df_combine_columns`, or perform the multiplication mentally from the table.

```
setup_output_case('C:/studies/case')

paths = list_enabled_outputs_paths()
# Find paths matching the expected output names
# gerter.csv = Thermal Generation, cmo.csv = Marginal Cost

# Inspect both files to confirm shared index levels
df_info('C:/studies/case/gerter.csv')
# → index_names: ["year", "week", "agent", "scenario"]
# → columns: ["Scenario 1", ..., "Scenario 50"]

df_info('C:/studies/case/cmo.csv')
# → index_names: ["year", "week", "bus", "scenario"]
# → columns: ["Scenario 1", ..., "Scenario 50"]

# Merge on time + scenario (agent ≠ bus, so omit from join key)
df_merge(
    'C:/studies/case/gerter.csv',
    'C:/studies/case/cmo.csv',
    how='inner',
    on=['year', 'week', 'scenario']
)
# → result contains both generation (Scenario 1_x) and cmo (Scenario 1_y) columns
# → present this table; use _x/_y suffix convention to identify which is which

# Revenue = generation × marginal_cost within the same file:
# If both outputs were already merged into a single CSV, use:
df_combine_columns(
    'C:/studies/case/merged.csv',
    'generation_x', 'multiply', 'cmo_y', 'revenue'
)
```

---

### WF-7b: Compare two scenario columns within the same output file

**Goal:** Compute the difference between Scenario 1 and Scenario 10 in gerter.csv.

```
setup_output_case('C:/studies/case')
list_enabled_outputs_paths()

# Inspect columns
df_info('C:/studies/case/gerter.csv')
# → columns: ["Scenario 1", "Scenario 2", ..., "Scenario 50"]

# Compute delta between two scenarios (no merge needed — same file)
df_combine_columns(
    'C:/studies/case/gerter.csv',
    'Scenario 1', 'subtract', 'Scenario 10', 'delta_1_10'
)
# → returns full DataFrame with extra column "delta_1_10"
# → positive = Scenario 1 generated more; negative = Scenario 10 generated more
```

---

### WF-7c: Compare the same output across two case runs

**Goal:** Stack thermal generation from two different cases to compare them.

```
# Inspect both files first
df_info('C:/studies/case_base/gerter.csv')
df_info('C:/studies/case_edited/gerter.csv')
# → confirm same index structure and column names

# Stack row-wise (axis=0) — all rows from both cases concatenated
df_concat(
    ['C:/studies/case_base/gerter.csv', 'C:/studies/case_edited/gerter.csv'],
    axis=0
)
# → result has all rows from both files
# → use this to compare distributions, compute statistics across both runs

# Stack column-wise (axis=1) — same index, side-by-side columns
df_concat(
    ['C:/studies/case_base/gerter.csv', 'C:/studies/case_edited/gerter.csv'],
    axis=1
)
# → useful when files have the same index but different output variables
```

---

### WF-8: Edit a static property (safe copy)

**Goal:** Increase InstalledCapacity of "Gas1" from 400 MW to 500 MW.

```
# Create safe copy
setup_edit_study('C:/studies/case', 'C:/studies/case_edited_20260429')

# Discover type names, then property schema and exact key
discover_objects()
# → confirms 'ThermalPlant'

discover_object_properties('ThermalPlant')
# → key: "ThermalPlant Gas1 [3]"
# → InstalledCapacity: Static, unit MW

# Edit
modify_static_element('ThermalPlant Gas1 [3]', 'InstalledCapacity', 500)
# → Gas1 [3] — InstalledCapacity updated from 400.0 to 500.0

# Save
save_study('C:/studies/case_edited_20260429')
```

---

### WF-9: Scale a dynamic property by percentage

**Goal:** Increase all thermal marginal costs by 5%.

```
setup_edit_study('C:/studies/case', 'C:/studies/case_+5pct_cost')

# Get all thermal keys
get_objects_by_type('ThermalPlant')
# → Objects Keys: ['ThermalPlant Gas1 [3]', 'ThermalPlant Coal1 [4]', ...]

# Confirm MarginalCost is dynamic
discover_object_properties('ThermalPlant')
# → MarginalCost: Dynamic ✓

# Scale each plant
scale_dataframe('ThermalPlant Gas1 [3]',  'MarginalCost', 5)
scale_dataframe('ThermalPlant Coal1 [4]', 'MarginalCost', 5)
# ... repeat for all keys from get_objects_by_type

save_study('C:/studies/case_+5pct_cost')
```

---

### WF-10: Edit a dimensional (matrix) property

**Goal:** Update fuel consumption curve (segments) for a thermal plant.

```
setup_edit_study('C:/studies/case', 'C:/studies/case_fuel_curve')

# Discover property and confirm it is dimensional
discover_object_properties('ThermalPlant')
# → FuelConsumption: Dynamic, Dimension 'Segment': max=3

# Read current schema — REQUIRED before set_dataframe
get_dataframe_schema('ThermalPlant Gas1 [3]', 'FuelConsumption')
# → dimensions: Segment (max=3)
# → current DataFrame dict

# Build new DataFrame matching exact schema shape
# and call set_dataframe with same column/index structure
set_dataframe('ThermalPlant Gas1 [3]', {
    "(1)": {"0": 50.0, "1": 120.0, "2": 200.0},
    "(2)": {"0": 60.0, "1": 140.0, "2": 230.0},
    "(3)": {"0": 70.0, "1": 160.0, "2": 260.0},
})

save_study('C:/studies/case_fuel_curve')
```

---

### WF-11: Create a new thermal plant

**Goal:** Add a new gas peaker plant.

```
setup_edit_study('C:/studies/case', 'C:/studies/case_new_plant')

# Discover mandatory references for ThermalPlant
discover_object_properties('ThermalPlant')
# → mandatory reference: RefSystem (Object), RefFuels (List of Objects)

# Get existing fuel and system keys
get_objects_table('Fuel',   ['name'])   # → Fuel Natural_Gas [1]
get_objects_table('System', ['name'])   # → System SIN [1]

# Create
create_element(
    obj_type='ThermalPlant',
    name='GasPeaker',          # max 12 chars
    code=None,                 # auto-assigned
    properties={
        'InstalledCapacity': 200,
        'MinimumOutput':     0,
        'MarginalCost':      85,
        'RefSystem':         'System SIN [1]',
        'RefFuels':          ['Fuel Natural_Gas [1]'],
    }
)

save_study('C:/studies/case_new_plant')
```

---

### WF-12: Output management — enable, disable, convert

**Goal:** Enable marginal cost outputs and convert thermal generation to CSV.

```
setup_output_case('C:/studies/case')

# See what is enabled
list_enabled_outputs()

# Get all output IDs
get_output_num()
# → {1: "Thermal Generation", 2: "Hydro Generation", 5: "Marginal Cost", ...}

# Enable marginal cost (ID=5) — match description semantically
change_output_availability({5: True})

# Get file paths for conversion
list_enabled_outputs_paths()
# → {"C:/studies/case/gerter.dat": "Thermal Generation", ...}

# Convert thermal generation to CSV
convert_output('C:/studies/case/gerter.dat', 'csv')
```

---

### WF-13: Full session — explore, edit, run, analyse

**Goal:** Audit case → increase hydro max power → run SDDP → analyse generation.

```
# ── Phase 1: Explore ─────────────────────────────────────────────────────────
setup_input_study('C:/studies/case')

discover_objects()
# → confirms 'HydroPlant' is the right type

get_objects_by_type('HydroPlant')   → 8 objects, keys listed
get_objects_table('HydroPlant', ['InstalledCapacity', 'MaxPower'])
# Shows: all hydro plants, MaxPower in MW

discover_object_properties('HydroPlant')
# Confirms: MaxPower is Static, unit MW
# Keys: ['HydroPlant Itaipu [1]', 'HydroPlant Furnas [2]', ...]

# ── Phase 2: Edit ─────────────────────────────────────────────────────────────
setup_edit_study('C:/studies/case', 'C:/studies/case_+10pct_hydro')

discover_object_properties('HydroPlant')
# Confirms keys and property name (MaxPower: Static)

modify_static_element('HydroPlant Itaipu [1]', 'MaxPower', 7800)
modify_static_element('HydroPlant Furnas [2]', 'MaxPower', 1350)
# ... all plants from the earlier get_objects_by_type result

save_study('C:/studies/case_+10pct_hydro')

# ── Phase 3: Run ──────────────────────────────────────────────────────────────
list_available_versions('sddp')
# → {'18.0.3': 'C:/PSR/SDDP18.0/', ...}

run_psr_model('C:/studies/case_+10pct_hydro', 'sddp', '18.0.3')

# ── Phase 4: Analyse ──────────────────────────────────────────────────────────
# Discover binary files from new run
discover_object_properties('HydroPlant')
# → Binary Input Files: GHIDR.BIN : Hydro Generation

input_aggregate_binary_dataframe('GHIDR.BIN', ['year', 'agent'], 'mean')
# Compare with baseline scenario

input_filter_binary_dataframe_by_index('GHIDR.BIN', {"year": [2027]})
```

---

## 5. Orchestration rules

1. **No activation step.** Every MCP tool is callable directly. `find_tools(query)` is optional — use it only to discover tool names you don't know.
2. **Two-step discovery:** `discover_objects()` → pick exact type → `discover_object_properties(type)` → get properties + keys + binary files. Reuse results within a session.
3. **Prefer targeted tools over broad ones:**
   - `get_objects_by_type` + `get_objects_table` instead of `get_all_objects`
   - `input_aggregate_dataframe` instead of `input_get_dataframe` + manual aggregation
   - `input_filter_binary_dataframe_by_index` instead of `input_get_binary_dataframe` when filtering
4. **Static vs dynamic — always verify:** use `discover_object_properties` before assuming a property type.
5. **Always use exact keys:** `"ThermalPlant Gas1 [3]"` — never just `"Gas1"`.
6. **Edits always on a copy:** use `setup_edit_study`, not `setup_edit_study_inplace`, unless user explicitly approves: when you set another folder you should discover all objects again to use the correct obj_key.
7. **`get_dataframe_schema` is mandatory** before `set_dataframe` — shape must match exactly.
8. **Binary file names come from `discover_object_properties`** — look for "Binary Input Files" at the bottom of the result.
9. **`df_info` first** on any unfamiliar output file before `df_aggregate`, `df_filter_*`, etc. — exact index level names and column names are required by every other `df_*` tool.
9a. **`df_aggregate` `'mean'` is UNWEIGHTED by default** — every collapsed row counts equally. Whenever the levels being collapsed include blocks, that is not the time-weighted average the user almost certainly means, because blocks have different durations. Pass `weights_file=<block-duration output file>` for the correct figure; the weights are joined on the index levels the two files share. Every result carries a `weighting` key — read it and state plainly which mean you are reporting. Never present an unweighted block average as "the average" without saying so.
10. **`df_*` results are dicts, not file paths** — you cannot chain one `df_*` output into another `df_*` call directly. Present intermediate results; guide the user to save to CSV when a multi-step pipeline is needed. Note the one exception: `df_aggregate` reaches a second file directly via `weights_file`, so weighted means need no chaining.
11. **Use the right binary vs. CSV boundary:** binary file names (e.g. `GERTER.BIN`) go to `input_*_binary_*` tools; converted file paths (e.g. `gerter.csv`) go to `df_*` tools.
11a. **Input binary vs. output results — know the difference:**
    - `input_*_binary_*` tools → **case input data** that cannot be read with `get_dynamic_property` (e.g. hourly demand scenarios, stochastic inflow series). File names come from `discover_object_properties`.
    - `df_*` tools → **model output results** produced by SDDP/OptGen (generation, deficit, marginal cost from dispatch, water value, total cost). Fuel cost is an *input*, not an output.
    - When the user asks to visualise or analyse something from the case and `get_dynamic_property` cannot reach it, check `discover_object_properties` for a matching binary input file.
11b. **Never convert output files unless the user explicitly asks.** Only call `convert_output(path, 'csv')` when the user requests conversion or a `df_*` analysis requires a non-binary format.
12. **`df_combine_columns` works within a single file** — use it for scenario-vs-scenario differences or unit conversions. For cross-file arithmetic, `df_merge` first.
13. **Prefer `df_filter_by_index` over `df_filter_by_value`** when filtering on dimensional axes (year, scenario, agent) — it is cleaner and avoids type-coercion issues.
14. **Language:** respond in the same language the user used.
15. **Answer format:** Focus on the core point of the question. First create a plan of which tools you should use and the order to answer objectively the usre question.  If tables and graphs are needed, present them as clearly as possible. 