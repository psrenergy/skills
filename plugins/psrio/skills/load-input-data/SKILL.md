---
name: load-input-data
description: Look up the input (study data) attributes of a PSRIO collection and their units — installed capacity, storage limits, O&M cost, line reactance, production factor, and the rest, across 67 collections. Use when a PSRIO Lua script needs a study *parameter* rather than a model *result*, when you need the exact attribute name or unit for a collection, or when a script fails because an attribute does not exist. For result series use load-output-data instead.
---

# Index

```lua
--[[Read an input attribute]] value = Collection().attribute
```

## Reading input data

Input attributes are read as properties off the collection — no parentheses on
the attribute itself, and no `load` call. They carry the unit listed in the
collection's reference table.

```lua
hydro = Hydro();
useful_storage = hydro.max_storage - hydro.min_storage;
```

```lua
circuit = Circuit();
circuit_flow = circuit:load("cirflw");
circuit_loading = circuit_flow / circuit.capacity;
```

Input attributes combine with loaded result series directly, as in the second
example — see the `data-operations` skill for the operators.

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
- [Demand](references/demand.md)
- [DemandSegment](references/demandsegment.md)
- [EnergyChainDemand](references/energychaindemand.md)
- [EnergyChainDemandSegment](references/energychaindemandsegment.md)
- [EnergyChainFixedConverter](references/energychainfixedconverter.md)
- [EnergyChainFixedConverterCommodity](references/energychainfixedconvertercommodity.md)
- [EnergyChainNetwork](references/energychainnetwork.md)
- [EnergyChainNode](references/energychainnode.md)
- [EnergyChainProcess](references/energychainprocess.md)
- [EnergyChainProducer](references/energychainproducer.md)
- [EnergyChainStorage](references/energychainstorage.md)
- [EnergyChainTransport](references/energychaintransport.md)
- [ExpansionCapacity](references/expansioncapacity.md)
- [ExpansionConstraint](references/expansionconstraint.md)
- [ExpansionDecision](references/expansiondecision.md)
- [ExpansionProject](references/expansionproject.md)
- [FlexibleDemand](references/flexibledemand.md)
- [FlowController](references/flowcontroller.md)
- [Fuel](references/fuel.md)
- [FuelConsumption](references/fuelconsumption.md)
- [FuelContract](references/fuelcontract.md)
- [FuelReservoir](references/fuelreservoir.md)
- [GasEmission](references/gasemission.md)
- [GasNode](references/gasnode.md)
- [GenerationConstraint](references/generationconstraint.md)
- [Generic](references/generic.md)
- [GenericConstraint](references/genericconstraint.md)
- [GenericConstraintInterpolation](references/genericconstraintinterpolation.md)
- [GenericVariable](references/genericvariable.md)
- [Hydro](references/hydro.md)
- [HydroGaugingStation](references/hydrogaugingstation.md)
- [HydroGenerator](references/hydrogenerator.md)
- [Interconnection](references/interconnection.md)
- [InterconnectionSum](references/interconnectionsum.md)
- [Load](references/load.md)
- [Maintenance](references/maintenance.md)
- [MaintenanceSolicitation](references/maintenancesolicitation.md)
- [OptPriceAgent](references/optpriceagent.md)
- [OptPriceContract](references/optpricecontract.md)
- [OptPriceLoad](references/optpriceload.md)
- [OptPricePlant](references/optpriceplant.md)
- [OptPriceSystem](references/optpricesystem.md)
- [PhaseShifter](references/phaseshifter.md)
- [PowerInjection](references/powerinjection.md)
- [Renewable](references/renewable.md)
- [RenewableGaugingStation](references/renewablegaugingstation.md)
- [RenewableGenerator](references/renewablegenerator.md)
- [ReserveGenerationConstraint](references/reservegenerationconstraint.md)
- [ReservoirSet](references/reservoirset.md)
- [SeriesCapacitor](references/seriescapacitor.md)
- [Study](references/study.md)
- [System](references/system.md)
- [Thermal](references/thermal.md)
- [ThermalCombinedCycle](references/thermalcombinedcycle.md)
- [ThermalGenerator](references/thermalgenerator.md)
- [ThreeWindingTransformer](references/threewindingtransformer.md)
- [Transformer](references/transformer.md)
- [WaterWay](references/waterway.md)
