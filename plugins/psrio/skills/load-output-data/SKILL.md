---
name: load-output-data
description: Load PSR model result series in a PSRIO Lua script with `collection:load("file")` or `force_load`, and look up which output files each collection provides and their units — generation, marginal cost, flow, storage, spillage, cost, and the rest across 45 collections. Use when a script needs results from a model run, when you need the exact output filename for a collection, or when a `load` call fails. For study parameters rather than results use load-input-data instead.
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

## Collections

One file per collection. Read only the one you need.

- [ACLine](references/acline.md)
- [Area](references/area.md)
- [Battery](references/battery.md)
- [Bus](references/bus.md)
- [Circuit](references/circuit.md)
- [CircuitsSum](references/circuitssum.md)
- [ConcentratedSolarPower](references/concentratedsolarpower.md)
- [DCLink](references/dclink.md)
- [DCLine](references/dcline.md)
- [EnergyChainDemand](references/energychaindemand.md)
- [EnergyChainFixedConverter](references/energychainfixedconverter.md)
- [EnergyChainNode](references/energychainnode.md)
- [EnergyChainProducer](references/energychainproducer.md)
- [EnergyChainStorage](references/energychainstorage.md)
- [EnergyChainTransport](references/energychaintransport.md)
- [ExpansionProject](references/expansionproject.md)
- [FlexibleDemand](references/flexibledemand.md)
- [FlowController](references/flowcontroller.md)
- [Fuel](references/fuel.md)
- [FuelContract](references/fuelcontract.md)
- [FuelReservoir](references/fuelreservoir.md)
- [GasEmission](references/gasemission.md)
- [GasNode](references/gasnode.md)
- [GenerationConstraint](references/generationconstraint.md)
- [GenericConstraint](references/genericconstraint.md)
- [GenericConstraintInterpolation](references/genericconstraintinterpolation.md)
- [GenericVariable](references/genericvariable.md)
- [Hydro](references/hydro.md)
- [HydroGenerator](references/hydrogenerator.md)
- [Interconnection](references/interconnection.md)
- [InterconnectionSum](references/interconnectionsum.md)
- [Load](references/load.md)
- [PowerInjection](references/powerinjection.md)
- [Renewable](references/renewable.md)
- [RenewableGenerator](references/renewablegenerator.md)
- [ReserveGenerationConstraint](references/reservegenerationconstraint.md)
- [ReservoirSet](references/reservoirset.md)
- [SeriesCapacitor](references/seriescapacitor.md)
- [Study](references/study.md)
- [System](references/system.md)
- [Thermal](references/thermal.md)
- [ThermalGenerator](references/thermalgenerator.md)
- [ThreeWindingTransformer](references/threewindingtransformer.md)
- [Transformer](references/transformer.md)
- [WaterWay](references/waterway.md)
