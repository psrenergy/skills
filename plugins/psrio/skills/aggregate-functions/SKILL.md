---
name: aggregate-functions
description: The `BY_*` aggregation functions PSRIO passes to `aggregate_stages`, `aggregate_scenarios`, `aggregate_agents`, `aggregate_blocks`, `to_hour`, and `to_block` — sum, average, weighted average, percentile, VaR/CVaR, standard deviation, NPV, min/max, kth-largest, and their index variants. Use when choosing how a series should collapse along a dimension, or to check whether a given aggregator exists.
---

# Index

```lua
--[[Sum]] BY_SUM()
--[[Sum excluding a value]] BY_SUM_EXCLUDING(number)
--[[Product]] BY_MULTIPLICATION()
--[[Average]] BY_AVERAGE()
--[[Unweighted average]] BY_SIMPLE_AVERAGE()
--[[Average excluding a value]] BY_AVERAGE_EXCLUDING(number)
--[[Weighted average]] BY_WEIGHTED_AVERAGE()
--[[Left-tail CVaR]] BY_CVAR_L(number)
--[[Weighted left-tail CVaR]] BY_WEIGHTED_CVAR_L(number)
--[[Right-tail CVaR]] BY_CVAR_R(number)
--[[Left-tail VaR]] BY_VAR_L(number)
--[[Right-tail VaR]] BY_VAR_R(number)
--[[Weighted right-tail CVaR]] BY_WEIGHTED_CVAR_R(number)
--[[Standard deviation]] BY_STDDEV()
--[[Standard error]] BY_STDERROR()
--[[Repeat the value]] BY_REPEATING()
--[[Net present value]] BY_NPV()
--[[First value]] BY_FIRST_VALUE()
--[[Nth value in order]] BY_ORDER(number)
--[[Last value]] BY_LAST_VALUE()
--[[Maximum]] BY_MAX()
--[[Index of the maximum]] BY_MAX_INDEX()
--[[Minimum]] BY_MIN()
--[[Index of the minimum]] BY_MIN_INDEX()
--[[Kth largest value]] BY_KTH_LARGEST(number)
--[[Index of the kth largest]] BY_KTH_LARGEST_INDEX(number)
--[[Kth smallest value]] BY_KTH_SMALLEST(number)
--[[Index of the kth smallest]] BY_KTH_SMALLEST_INDEX(number)
--[[Percentile]] BY_PERCENTILE(number)
--[[Percentile excluding a value]] BY_PERCENTILE_EXCLUDING(number)
--[[Index of the percentile]] BY_PERCENTILE_INDEX(number)
--[[Rainflow cycle count]] BY_RAINFLOW_COUNT()
```

These are arguments, not methods — construct one and pass it to the operation
that collapses a dimension.

```lua
system = System();
cmgdem = system:load("cmgdem");

cmgdem_avg = cmgdem:aggregate_scenarios(BY_AVERAGE());
cmgdem_p90 = cmgdem:aggregate_scenarios(BY_PERCENTILE(90));
```

Which aggregator is appropriate depends on the quantity. Sum energy and cost;
average prices and factors. `BY_SUM` on a marginal cost series produces a
meaningless number.

```lua
renewable = Renewable();
gergnd = renewable:load("gergnd");
gergnd_total = gergnd:aggregate_blocks(BY_SUM());        -- energy: sum

system = System();
cmgdem = system:load("cmgdem");
cmgdem_mean = cmgdem:aggregate_blocks(BY_AVERAGE());     -- price: average
```

## Choosing between the three averages

`BY_SIMPLE_AVERAGE()` is the plain arithmetic mean of the values.
`BY_WEIGHTED_AVERAGE()` weights each value before averaging.
`BY_AVERAGE()` is the default used throughout the other skills.

TODO(psr): confirm what `BY_AVERAGE()` weights by (block duration? stage
length?) and how it differs from `BY_WEIGHTED_AVERAGE()`, whose weights are not
documented here. The distinction changes results on block-varying series.

## Index variants

The `_INDEX` forms return the *position* along the collapsed dimension where the
extreme occurred, not the value. `BY_MAX_INDEX()` over scenarios answers "which
scenario was worst", which is what you want before pulling that scenario out
with `select_scenario`.

## Risk measures

`BY_VAR_L` / `BY_VAR_R` give Value at Risk on the left and right tail;
`BY_CVAR_L` / `BY_CVAR_R` give Conditional VaR (the mean beyond the VaR
threshold). Use the left tail for quantities where low is bad (inflow, storage)
and the right tail where high is bad (cost, deficit, marginal price).

TODO(psr): confirm whether `number` is a confidence level in percent (95) or a
fraction (0.95). The two are indistinguishable from the signature and give very
different answers.

## Aggregators that need PSR confirmation

These ship without descriptions because their exact behaviour is not derivable
from the signature, and guessing would put wrong semantics in a public reference:

- `BY_SUM_EXCLUDING(number)`, `BY_AVERAGE_EXCLUDING(number)`,
  `BY_PERCENTILE_EXCLUDING(number)` — TODO(psr): is `number` a value to drop
  from the sample, or a count of entries to skip?
- `BY_ORDER(number)` — TODO(psr): how does this differ from
  `BY_KTH_LARGEST`/`BY_KTH_SMALLEST`, and is the order ascending or descending?
- `BY_REPEATING()` — TODO(psr): confirm it only makes sense expanding a coarser
  dimension into a finer one (it is used with `to_hour` in `blocks-operations`);
  document what it does if passed to an `aggregate_*` call.
- `BY_RAINFLOW_COUNT()` — TODO(psr): rainflow counting is a fatigue
  cycle-counting algorithm; document what it returns for a PSRIO series and the
  intended use case (battery cycling?).
