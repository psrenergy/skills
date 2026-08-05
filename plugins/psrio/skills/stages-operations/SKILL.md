---
name: TODO
description: TODO
---

# Index

```lua
--[[Aggregate Stages]] exp = exp1:aggregate_stages(f)
--[[Aggregate Stages into a Profile]] exp = exp1:aggregate_stages(f,  profile)
--[[Select One Stage]] exp = exp1:select_stage(stage)
--[[Select the First Stage]] exp = exp1:select_first_stage(stage)
--[[Select the Last Stage]] exp = exp1:select_last_stage(stage)
--[[Select the First and the Last Stages]] exp = exp1:select_stages(first_stage,  last_stage)
--[[Select Stages by a First and a Last Years]] exp = exp1:select_stages_by_year(first_year,  last_year)
--[[Select Stages by a Year]] exp = exp1:select_stages_by_year(year)
--[[Reshape Stages]] exp = exp1:reshape_stages(Profile.DAILY)
--[[Reset Stages]] exp = exp1:reset_stages()
--[[Concatenate Stages]] exp = concatenate_stages({ exp1,  exp2, ...})
--[[Set Initial Stage]] exp = exp1:set_initial_stage(initial_stage)
--[[Set Initial Year]] exp = exp1:set_initial_year(initial_year)
--[[Uncouple Stages]] exp = exp1:uncouple_stages()
--[[Uncouple Stages and Blocks]] exp = exp1:uncouple_stages_blocks()
```

## Aggregate Stages

```lua
```

## Aggregate Stages into a Profile

Where `profile` is the following enumerate:

| Profiles                 |
|:------------------------:|
| `Profile.STAGE`          | 
| `Profile.WEEK`           | 
| `Profile.MONTH`          | 
| `Profile.QUARTER`        | 
| `Profile.YEAR`           | 
| `Profile.PER_WEEK`       | 
| `Profile.PER_MONTH`      |
| `Profile.PER_QUARTER`    |
| `Profile.PER_YEAR`       | 

### Profile.STAGE

The `Profile.STAGE` is the default value to characterize the aggregation if the user does not inform any profile. The data associated with each stage of the study horizon is aggregated.

| exp1          | exp (`Profile.STAGE`) |
|:-------------:|:---------------------:|
| `n` (daily)   | `1` (daily)           |
| `n` (weekly)  | `1` (weekly)          |
| `n` (monthly) | `1` (monthly)         |
| `n` (yearly)  | `1` (yearly)          |

### Profile.WEEK and Profile.PER_WEEK

When the data has a daily resolution and the aggregation profile is `Profile.WEEK`, PSRIO will aggregate the data for each day of the weeks in the study period, i.e., that data regarding all Mondays in the data set will be aggregated into one value and the same for Tuesday, Wednesday, and so on. With a daily resolution and the aggregation `Profile.PER_WEEK`, PSRIO will aggregate the data related to each week of the study. 

When the data is weekly and we request is `Profile.WEEK`, the data associated with each week is aggregated in one week. If the request is the aggregation `Profile.PER_WEEK`, PSRIO will do nothing and the data will remains the same.

**These aggregation profiles are not defined for monthly and yearly resolution data**.  

| exp1          | exp (`Profile.WEEK`) | exp (`Profile.PER_WEEK`) |
|:-------------:|:--------------------:|:------------------------:|
| `n` (daily)   | `7` (daily)          | `n/7` (weekly)           |
| `n` (weekly)  | `1` (weekly)         | `n` (weekly)             |
| `n` (monthly) | ❌                   |  ❌                     |
| `n` (yearly)  | ❌                   |  ❌                     |

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_agg = cmgdem:aggregate_stages(BY_AVERAGE(), Profile.WEEK);
```

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_agg = cmgdem:aggregate_stages(BY_AVERAGE(), Profile.PER_WEEK);
```

### Profile.MONTH and Profile.PER_MONTH

Similar to `Profile.WEEK` and `Profile.PER_WEEK`, when the data has daily discretization and we request `Profile.MONTH`, PSRIO will aggregate the data for each day of the months in the study period. For example, PSRIO will aggregate all 1<sup>st</sup> days of each month and the same for the others months. If we request the `Profile.PER_MONTH`, PSRIO will aggregate the data related to each month.

When the data has month-level discretization and we request `Profile.MONTH`, PSRIO will aggregate the data associated with each month. If we request `Profile.PER_MONTH`, nothing is done to the data. 

**These aggregation profiles are not defined for weekly and yearly resolution data**.  

| exp1          | exp (`Profile.MONTH`) | exp (`Profile.PER_MONTH`) |
|:-------------:|:---------------------:|:-------------------------:|
| `n` (daily)   | `31` (daily)          | `n/~30` (monthly)         |
| `n` (weekly)  | ❌                   | ❌                        |
| `n` (monthly) | `1` (monthly)         | `n` (monthly)             |
| `n` (yearly)  | ❌                   | ❌                        |

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_agg = cmgdem:aggregate_stages(BY_AVERAGE(), Profile.MONTH);
```

```lua
system = System();
cmgdem = system:load("cmgdem");
cmgdem_agg = cmgdem:aggregate_stages(BY_AVERAGE(), Profile.PER_MONTH);
```

### Profile.YEAR and Profile.PER_YEAR

When the data has a daily resolution and we request a `Profile.YEAR`, the data related to each day of years is aggregated. For example, PSRIO will aggregate all January 1<sup>st</sup> days in the study period, which is done for the other days of the year. If we request a` Profile.PER_YEAR`, the data associated with each year is aggregated. The same happens when the data has week, month, or year-level resolution if `Profile.PER_YEAR` is selected.

If the data has a year resolution and `profile.YEAR` is selected. the data related to the same year is aggregated.

**The `profile.YEAR` profile is not defined for weekly and monthly resolution data**.  

| exp1          | exp (`Profile.YEAR`) | exp (`Profile.PER_YEAR`) |
|:-------------:|:--------------------:|:------------------------:|
| `n` (daily)   | `365` (daily)        | `n/365` (yearly)         |
| `n` (weekly)  | `52` (weekly)        | `n/52` (yearly)          |
| `n` (monthly) | `12` (monthly)       | `n/12` (yearly)          |
| `n` (yearly)  | `1` (yearly)         | `1` (yearly)             |

```lua
system = System();
defcit = system:load("defcit");
defcit_per_year = defcit:aggregate_stages(BY_SUM(), Profile.YEAR);
```

```lua
system = System()
defcit = system:load("defcit")
defcit_per_year = defcit:aggregate_stages(BY_SUM(), Profile.PER_YEAR);
```

## Select One Stage

```lua
generic = Generic();
objcop = generic:load("objcop");
objcop_1st_stage = objcop:select_stage(1);
```

## Select the First Stage

```lua
generic = Generic();
objcop = generic:load("objcop");
objcop_2nd_to_n_stage = objcop:select_first_stage(2);
```

## Select the Last Stage

```lua
generic = Generic();
objcop = generic:load("objcop");
objcop_1st_to_2nd_stage = objcop:select_last_stage(2);
```

## Select the First and the Last Stages

```lua
generic = Generic();
objcop = generic:load("objcop");
objcop_2nd_to_4th_stage = objcop:select_stages(2, 4);
```

## Select Stages by a First and a Last Years

```lua
generic = Generic();
objcop = generic:load("objcop");
objcop_2030_2040 = objcop:select_stages_by_year(2030, 2040);
```

## Select Stages by a Year

```lua
generic = Generic();
objcop = generic:load("objcop");
objcop_2035 = objcop:select_stages_by_year(2035);
```

## Reshape Stages

For an hourly represented data, the stage resolution can changed from a week, month or year level to a daily one using that method

| exp1                   | exp                    |
|:----------------------:|:----------------------:|
| `n` (daily-hourly)     | `n` (daily-hourly)     |
| `n` (weekly-hourly)    | `7n` (daily-hourly)    |
| `n` (monthly-hourly)   | `~30n` (daily-hourly)  |
| `n` (yearly-hourly)    | `365n` (daily-hourly)  |

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_daily = gerter:reshape_stages(Profile.DAILY);
```

## Reset Stages

The reset method sets the initial stage to 1.

```lua
thermal = Thermal();
gerter = thermal:load("gerter");
gerter_cut = gerter:select_stages(10,30);
gerter_reset = gerter_cut:reset_stages();
```

## Concatenate Stages

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
gerhid_stage_5 = gerhid:select_stage(5);
gerhid_stage_15 = gerhid:select_stage(15);
gerhid_stage_25 = gerhid:select_stage(25);
gerhid_stages = concatenate_stages(
    gerhid_stage_5,
    gerhid_stage_15,
    gerhid_stage_25
);
```

## Set Initial Stage

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
gerhid_initial_stage = gerhid:set_initial_stage(5);
```

## Set Initial Year

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
gerhid_ini_yea = gerhid:set_initial_stage(2021);
```

## Uncouple Stages

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
gerhid_unc = gerhid:uncouple_stages();
```

## Uncouple Stages and Blocks

```lua
hydro = Hydro();

gerhid = hydro:load("gerhid");
gerhid_unc = gerhid:uncouple_stages_blocks();
```