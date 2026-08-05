---
name: TODO
description: TODO
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

## ACLine

|              Data               |                                                  Description                                                   | Unit  |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------- | :---: |
| `ACLine():cost()`               | AC transmission line cost                                                                                      |  k$   |
| `ACLine():flow()`               | AC transmission line flow                                                                                      |  MW   |
| `ACLine():capacity_marg_cost()` | Change in operating cost with respect to an infinitesimal change in the AC transmission line capacity (limit). | k$/MW |
| `ACLine():losses()`             | AC transmission line quadratic losses approximation, obtained through linearizations                           |  MW   |
| `ACLine():quadratic_losses()`   | AC transmission line theoretical quadratic losses                                                              |  MW   |
| `ACLine():losses_mismatch()`    | AC transmission lines losses error                                                                             |  MW   |

## Area

|          Data           |                   Description                   | Unit  |
| :---------------------- | :---------------------------------------------- | :---: |
| `Area():transfer()`     | Energy transfer between electric areas (export) |  GWh  |
| `Area():max_transfer()` | Maximum transfer limit per area                 |  MW   |
| `Area():min_transfer()` | Minimum transfer limit per area                 |  MW   |

## Battery

|                   Data                   |                                                                                                            Description                                                                                                             |  Unit  |
| :--------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: |
| `Battery():joint_reserve_cost()`         | Battery joint reserve cost                                                                                                                                                                                                         |   k$   |
| `Battery():joint_reserve()`              | Joint reserve for batteries                                                                                                                                                                                                        |   MW   |
| `Battery():generation()`                 | Battery net generation in the system. Positive values indicate battery discharge. Negative values indicate charging. Due to charge/discharge efficiencies the value may differ from the net energy variation stored in the battery |  MWh   |
| `Battery():final_storage()`              | Battery stored energy                                                                                                                                                                                                              |  MWh   |
| `Battery():storage_capacity_marg_cost()` | Marginal cost of battery maximum storage                                                                                                                                                                                           | $/MWh  |
| `Battery():capacity_marg_cost()`         | Marginal cost of battery maximum charge/discharge capacity                                                                                                                                                                         | $/MWh  |
| `Battery():losses()`                     | Sum of battery charge and discharge losses                                                                                                                                                                                         |  MWh   |
| `Battery():bus_income()`                 | Spot revenue of battery net generation based on the marginal cost of the bus where it is located.                                                                                                                                  |   k$   |
| `Battery():system_income()`              | Spot revenue of battery net generation based on the system marginal cost.                                                                                                                                                          |   k$   |
| `Battery():joint_reserve_nexc()`         | Battery joint reserve that can be shared between non-exclusive requirements                                                                                                                                                        |   MW   |
| `Battery():load("oembat")`               | Operation and maintenance cost by battery                                                                                                                                                                                          |   k$   |
| `Battery():available_capacity()`         | Available battery capacity, considering the maintenance schedule                                                                                                                                                                   |   MW   |
| `Battery():storage_marg_cost()`          | Change in operating cost with respect to an infinitesimal change of energy availability in the battery storage                                                                                                                     | k$/MWh |
| `Battery():initial_storage()`            | Battery storage levels in the beginning of the stages                                                                                                                                                                              |  MWh   |
| `Battery():joint_reserve_price()`        | Battery joint reserve price                                                                                                                                                                                                        | $/MWh  |
| `Battery():max_joint_reserve()`          | Battery maximum joint reserve                                                                                                                                                                                                      |   MW   |
| `Battery():single_reserve()`             | Battery single reserve                                                                                                                                                                                                             |   MW   |
| `Battery():nominal_capacity()`           | Battery nominal capacity                                                                                                                                                                                                           |   MW   |
| `Battery():om_unitary_cost()`            | Operation and maintenance unitary cost by battery                                                                                                                                                                                  | $/MWh  |
| `Battery():stored_energy()`              | Battery stored energy (%)                                                                                                                                                                                                          |   %    |

## Bus

|          Data           |                                        Description                                         |  Unit  |
| :---------------------- | :----------------------------------------------------------------------------------------- | :----: |
| `Bus():demand()`        | Total inelastic load per bus                                                               |  GWh   |
| `Bus():deficit()`       | Deficit in each node (bus) of the system                                                   |  GWh   |
| `Bus():marginal_cost()` | Change in operating cost with respect to an infinitesimal change in the load of the AC bus | $/MWh  |
| `Bus():total_income()`  | Load payments considering the load marginal cost of the bus where the load is located.     |   k$   |
| `Bus():voltage_angle()` | AC Bus voltage angle                                                                       | Degree |
| `Bus():max_load()`      | Maximum load of each bus: sum of the elastic and inelastic loads of each bus               |  GWh   |
| `Bus():deficit_perc()`  | Deficit per bus (% of load)                                                                |   %    |
| `Bus():ac_outflow()`    | Total flow per AC bus                                                                      |   MW   |
| `Bus():load_supplied()` | Total elastic and inelastic load supplied in each bus                                      |  GWh   |
| `Bus():island_idx()`    | Index of the island in AC network that the bus is connnected                               | Island |
| `Bus():lerner_idx()`    | Lerner index for transmission                                                              |   pu   |
| `Bus():load_income()`   | Load x Bus MargCost                                                                        |   k$   |
| `Bus():cc_outflow()`    | Total flow per DC bus                                                                      |   MW   |
| `Bus():cc_injection()`  | Net DC bus injection                                                                       |   MW   |
| `Bus():voltage()`       | DC Bus voltage magnitude                                                                   |   pu   |
| `Bus():ac_injection()`  | Net AC bus injection                                                                       |   MW   |

## Circuit

|               Data                |                                                           Description                                                            | Unit  |
| :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- | :---: |
| `Circuit():flow()`                | AC Circuit flow                                                                                                                  |  MW   |
| `Circuit():capacity_marg_cost()`  | Change in operating cost with respect to a infinitesimal change in the AC circuit capacity (limit).                              | k$/MW |
| `Circuit():max_flow()`            | Maximum AC circuit flow                                                                                                          |  MW   |
| `Circuit():income()`              | AC Circuit ingress given by the circuit flow multiplier by the difference between load marginal cost of end buses of the circuit |  k$   |
| `Circuit():losses()`              | AC circuit quadratic losses approximation, obtained through linearizations                                                       |  MW   |
| `Circuit():min_flow()`            | Minimum flow of the AC circuit in the opposite direction                                                                         |  MW   |
| `Circuit():operative_status()`    | If AC circuit is operating, el indicator=1; if in maintenance, 0.                                                                |  0/1  |
| `Circuit():quadratic_losses()`    | AC circuit theoretical quadratic losses                                                                                          |  MW   |
| `Circuit():loading_factor()`      | AC Circuit flow as a percentage of the maximum capacity                                                                          |   %   |
| `Circuit():overload()`            | Circuit overload                                                                                                                 |  MW   |
| `Circuit():overload_penalty()`    | Circuit overload penalty                                                                                                         |  k$   |
| `Circuit():dynamic_line_rating()` | Dynamic line rating, in p.u. of the nominal capacity                                                                             |  pu   |
| `Circuit():joint_reserve()`       | Circuit joint reserve                                                                                                            |  MW   |
| `Circuit():losses_mismatch()`     | AC circuit losses error                                                                                                          |  MW   |
| `Circuit():max_flow_limit()`      | Maximum flow of the AC circuit                                                                                                   |  MW   |
| `Circuit():min_reverse_flow()`    | Minimum flow of the AC circuit in the opposite direction                                                                         |  MW   |

## Circuits Sum

|              Data               |                                             Description                                              | Unit  |
| :------------------------------ | :--------------------------------------------------------------------------------------------------- | :---: |
| `CircuitsSum():maximun()`       | Upper bound for the circuit flow sum constraint                                                      |  MW   |
| `CircuitsSum():minimun()`       | Lower bound for the circuit flow sum constraint                                                      |  MW   |
| `CircuitsSum():value()`         | Circuit flow sum constraints                                                                         |  MW   |
| `CircuitsSum():marginal_cost()` | Change in operating cost with respect to an infinitesimal change in the circuit flow sum constraint. | k$/MW |
| `CircuitsSum():flow_losses()`   | Sum of losses of all circuits involved in circuit sum constraint                                     |  MW   |

## Concentrated Solar Power

|                          Data                           |                                                                   Description                                                                    | Unit  |
| :------------------------------------------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------- | :---: |
| `ConcentratedSolarPower():joint_reserve_cost()`         | CSP joint reserve cost                                                                                                                           |  k$   |
| `ConcentratedSolarPower():nominal_capacity()`           | CSP nominal capacity                                                                                                                             |  MW   |
| `ConcentratedSolarPower():generation()`                 | CSP generation                                                                                                                                   |  MWh  |
| `ConcentratedSolarPower():storage()`                    | CSP storage                                                                                                                                      |  MWh  |
| `ConcentratedSolarPower():storage_capacity_marg_cost()` | CSP storage marginal cost                                                                                                                        | $/MWh |
| `ConcentratedSolarPower():stored_heat()`                | Change in operating cost with respect to an infinitesimal change of the heat availability in the CSP's reservoirs at the beginning of the stage. | $/MWh |
| `ConcentratedSolarPower():charge()`                     | CSP charge                                                                                                                                       |  MWh  |
| `ConcentratedSolarPower():discharge()`                  | CSP discharge                                                                                                                                    |  MWh  |
| `ConcentratedSolarPower():capacity_marg_cost()`         | CSP capacity maginal cost                                                                                                                        | $/MW  |
| `ConcentratedSolarPower():joint_reserve()`              | Joint reserve for CSP                                                                                                                            |  MW   |
| `ConcentratedSolarPower():joint_reserve_nexc()`         | CSP joint reserve that can be shared between non-exclusive requirements                                                                          |  MW   |
| `ConcentratedSolarPower():scenario()`                   | CSP associated station scenario generation                                                                                                       |  pu   |
| `ConcentratedSolarPower():capacity_scenario()`          | CSP capacity scenario                                                                                                                            |  MW   |

## DCLink

|                Data                |                                                            Description                                                            | Unit  |
| :--------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------- | :---: |
| `DCLink():joint_reserve()`         | DC link joint reserve                                                                                                             |  MW   |
| `DCLink():flow()`                  | DC link flow                                                                                                                      |  GWh  |
| `DCLink():capacity_from_to()`      | DC Link capacity FROM->TO                                                                                                         |  MW   |
| `DCLink():marginal_cost()`         | Marginal cost of the DC link - Variation of the operating cost with respect to an infinitesimal variation of the DC link capacity | k$/MW |
| `DCLink():losses()`                | DC link transmission losses                                                                                                       |  MW   |
| `DCLink():loading_factor()`        | DC Link loading                                                                                                                   |   %   |
| `DCLink():capacity_to_from()`      | DC Link capacity TO->FROM                                                                                                         |  MW   |
| `DCLink():quadratic_losses()`      | DC link theoretical quadratic losses                                                                                              |  MW   |
| `DCLink():losses_mismatch()`       | DC link losses error                                                                                                              |  MW   |
| `DCLink():available_cap_from_to()` | DC Link available capacity FROM->TO                                                                                               |  MW   |
| `DCLink():available_cap_to_from()` | DC Link available capacity TO->FROM                                                                                               |  MW   |
| `DCLink():transmission_cost()`     | DC link transmission cost                                                                                                         |  k$   |

## DCLine

|             Data              |                                             Description                                             | Unit  |
| :---------------------------- | :-------------------------------------------------------------------------------------------------- | :---: |
| `DCLine():max_flow()`         | Maximum DC circuit flow                                                                             |  MW   |
| `DCLine():circuit_flag()`     | If DC circuit is operating, el indicator=1; if in maintenance, 0.                                   |  0/1  |
| `DCLine():flow()`             | DC Circuit flow                                                                                     |  MW   |
| `DCLine():marginal_cost()`    | Change in operating cost with respect to a infinitesimal change in the DC circuit capacity (limit). | k$/MW |
| `DCLine():losses()`           | DC Circuit energy losses                                                                            |  MW   |
| `DCLine():quadratic_losses()` | Quadratic losses by circuits DC                                                                     |  MW   |
| `DCLine():loading()`          | DC Circuit flow as a percentage of the maximum capacity                                             |   %   |
| `DCLine():losses_mismatch()`  | DC circuit losses error                                                                             |  MW   |

## Energy Chain Demand

|                  Data                   |                Description                 |  Unit   |
| :-------------------------------------- | :----------------------------------------- | :-----: |
| `EnergyChainDemand():demand_supplied()` | Energy chain: demand supplied              |   kUE   |
| `EnergyChainDemand():demand_cost()`     | Energy chain: cost by elastic demand       |   k$    |
| `EnergyChainDemand():marginal_cost()`   | Energy chain: elastic demand marginal cost | k$/UE/d |
| `EnergyChainDemand():deficit()`         | Deficit associated to energy chain demand  |   UE    |

## Energy Chain Fixed Converter

|                        Data                        |              Description               |  Unit   |
| :------------------------------------------------- | :------------------------------------- | :-----: |
| `EnergyChainFixedConverter():cost()`               | Fixed converter conversion cost        |   k$    |
| `EnergyChainFixedConverter():capacity_marg_cost()` | Fixed converter capacity marginal cost | k$/UE/d |

## Energy Chain Node

|                 Data                 |           Description           |  Unit   |
| :----------------------------------- | :------------------------------ | :-----: |
| `EnergyChainNode():node_marg_cost()` | Energy chain node marginal cost | k$/unit |

## Energy Chain Producer

|                     Data                     |                                Description                                |  Unit   |
| :------------------------------------------- | :------------------------------------------------------------------------ | :-----: |
| `EnergyChainProducer():producer_gen()`       | Energy chain producer production in thousands of units of electrification |   kUE   |
| `EnergyChainProducer():producer_cost()`      | Energy chain producer production cost                                     |   k$    |
| `EnergyChainProducer():producer_marg_cost()` | Energy chain producer capacity marginal cost                              | k$/UE/d |

## Energy Chain Storage

|                         Data                         |                    Description                    |  Unit  |
| :--------------------------------------------------- | :------------------------------------------------ | :----: |
| `EnergyChainStorage():final_storage()`               | Energy chain: final storage                       |  kUE   |
| `EnergyChainStorage():final_storage_marg_cost()`     | Energy chain: final storage marginal cost         |  $/UE  |
| `EnergyChainStorage():storage_injection()`           | Energy chain: storage net injection               | kUE/h  |
| `EnergyChainStorage():storage_injection_marg_cost()` | Energy chain: storage net injection marginal cost | $/UE/h |

## Energy Chain Transport

|                      Data                      |                  Description                   |  Unit   |
| :--------------------------------------------- | :--------------------------------------------- | :-----: |
| `EnergyChainTransport():transport_flow()`      | Energy chain: transport Flow                   |   UE    |
| `EnergyChainTransport():transport_cost()`      | Energy chain: cost by transport                |   k$    |
| `EnergyChainTransport():transport_marg_cost()` | Energy chain: transport capacity marginal cost | k$/UE/d |

## Expansion Project

|                    Data                    |          Description           | Unit  |
| :----------------------------------------- | :----------------------------- | :---: |
| `ExpansionProject():invest_capacity()`     | Investment strategy - Capacity |  MW   |
| `ExpansionProject():investment_decision()` | Investment decisions           |  pu   |

## Flexible Demand

|                 Data                  |                       Description                        | Unit  |
| :------------------------------------ | :------------------------------------------------------- | :---: |
| `FlexibleDemand():supplied()`         | Flexible load shifted to each block and supplied         |  GWh  |
| `FlexibleDemand():curtailment()`      | Flexible load shifted to each block, but not supplied    |  GWh  |
| `FlexibleDemand():maximum()`          | Maximum flexible load that can be shifted to each block  |  GWh  |
| `FlexibleDemand():minimum()`          | Minimum flexible load that must be shifted to each block |  GWh  |
| `FlexibleDemand():energy()`           | Reference flexible load to calculate the shifting limits |  GWh  |
| `FlexibleDemand():curtailment_cost()` | Flexible load curtailment cost                           |  k$   |

## Flow Controller

|              Data              |        Description        | Unit  |
| :----------------------------- | :------------------------ | :---: |
| `FlowController():reactance()` | Flow controller reactance |   %   |

# Fuel

|                 Data                  |                                          Description                                           |  Unit   |
| :------------------------------------ | :--------------------------------------------------------------------------------------------- | :-----: |
| `Fuel():consumption()`                | Fuel consumption                                                                               | k.unit  |
| `Fuel():consumption_rate()`           | Fuel consumption rate                                                                          |  un/h   |
| `Fuel():marginal_cost()`              | Change in operating cost with respect to an infinitesimal change in the fuel availability.     |  $/un   |
| `Fuel():consumption_rate_marg_cost()` | Change in operating cost with respect to an infinitesimal change in the fuel consumption rate. | k$/un/h |
| `Fuel():price()`                      | Fuel price                                                                                     | $/unit  |
| `Fuel():load("fueavl")`               | Fuel availability                                                                              | k.units |
| `Fuel():max_consumption_rate()`       | Max fuel consumption rate                                                                      |  un/h   |

## Fuel Contract

|                      Data                       |                                                   Description                                                    |  Unit   |
| :---------------------------------------------- | :--------------------------------------------------------------------------------------------------------------- | :-----: |
| `FuelContract():daily_offtake_violation()`      | Fuel contract minimum daily offtake rate violation                                                               |   UC    |
| `FuelContract():daily_offtake_violation_cost()` | Fuel contract minimum daily offtake rate violation cost                                                          |   k$    |
| `FuelContract():capacity()`                     | Maximum fuel contract capacity                                                                                   |   kUC   |
| `FuelContract():max_offtake()`                  | Maximum fuel contract offtake                                                                                    |  UC/h   |
| `FuelContract():remaining()`                    | Fuel contract amount (Take-or-Pay and additional components) that can still be consumed at the end of the period |   kUC   |
| `FuelContract():unconsumed()`                   | Not consumed fuel from the total contract amount (Take-or-Pay and additional components), that will be discarded |   kUC   |
| `FuelContract():consumed()`                     | Fuel contract offtake during the period                                                                          |   kUC   |
| `FuelContract():marginal_cost()`                | Change in operating cost with respect to an infinitesimal change in the fuel contract capacity                   |  $/UC   |
| `FuelContract():top_amount()`                   | Take or Pay contract value                                                                                       |   kUC   |
| `FuelContract():top_remaining()`                | Fuel from the Take or Pay component of the contract that can still be consumed at the end of the period          |   kUC   |
| `FuelContract():top_unconsumed()`               | Not consumed fuel from the Take-or-Pay component of the contract, that will be discarded                         |   kUC   |
| `FuelContract():top_marginal_cost()`            | Change in operating cost with respect to an infinitesimal change in the Take-or-Pay amount of the fuel contract  |  $/UC   |
| `FuelContract():top_consumed()`                 | Take or Pay consumption during the period                                                                        |   kUC   |
| `FuelContract():top_cost()`                     | ToP cost per contract                                                                                            |   k$    |
| `FuelContract():top_add_cost()`                 | Additional cost per contract                                                                                     |   k$    |
| `FuelContract():top_add_total()`                | Total add contracted per contract                                                                                |   kUC   |
| `FuelContract():top_add_amount()`               | Fuel from the additional component of the contract that can still be consumed at the end of the period           |   kUC   |
| `FuelContract():top_add_consumed()`             | Additional amount consumed during the period                                                                     |   kUC   |
| `FuelContract():top_add_unconsumed()`           | Not consumed fuel from the additional component of the contract, that will be discarded                          |   kUC   |
| `FuelContract():load("fccost")`                 | Contract cost                                                                                                    |   k$    |
| `FuelContract():min_offtake_violation()`        | Fuel contract minimum offtake rate violation                                                                     |   UC    |
| `FuelContract():min_offtake_violation_cost()`   | Fuel contract minimum offtake rate violation cost                                                                |   k$    |
| `FuelContract():availability()`                 | Fuel contract availability                                                                                       | k.units |
| `FuelContract():makeup_final()`                 | Fuel from the make-up component of the contract that can still be consumed at the end of the period              |   kUC   |
| `FuelContract():makeup_discount()`              | Not consumed fuel from the make-up component of the contract, that will be discarded                             |   kUC   |
| `FuelContract():makeup_withdrawal()`            | Make-up consumption at each stage                                                                                |   kUC   |
| `FuelContract():carry_forward_cons()`           | Carry forward consumption at each stage                                                                          |   kUC   |
| `FuelContract():carry_forward_amount()`         | Carry forward available amount at the end of the stage                                                           |   kUC   |
| `FuelContract():carry_forward_credit()`         | Carry forward credit at the end of the stage                                                                     |   kUC   |
| `FuelContract():carry_forward_witdh()`          | ToP amount belonging to the current renovation that was already consumed through carry forward                   |   kUC   |
| `FuelContract():current_renewal()`              | Current renewal of fuel contract                                                                                 |    0    |
| `FuelContract():makeup_contrib()`               | Make-up contribution of the fuel contract at each stage                                                          |   kUC   |
| `FuelContract():top_billing()`                  | Fuel contract billing corresponding to the Take-or-Pay fuel that wasn't consumed                                 |   k$    |
| `FuelContract():consumption_billing()`          | Fuel contract billing corresponding to consumption                                                               |   k$    |

## Fuel Reservoir

|                  Data                  |                    Description                     | Unit  |
| :------------------------------------- | :------------------------------------------------- | :---: |
| `FuelReservoir():load("frvmax")`       | Maximum fuel storage capacity                      |  kUC  |
| `FuelReservoir():load("frinmx")`       | Maximum fuel storage injection                     | UC/h  |
| `FuelReservoir():max_withdrawal()`     | Maximum fuel storage offtake                       | UC/h  |
| `FuelReservoir():final_storage()`      | Fuel storage availability at the end of the period |  kUC  |
| `FuelReservoir():injection()`          | Fuel reservoir injection during the period         |  kUC  |
| `FuelReservoir():withdrawal()`         | Fuel reservoir offtake during the period           |  kUC  |
| `FuelReservoir():marginal_value()`     | Marg. value of fuel in reservoir                   | $/UC  |
| `FuelReservoir():capacity_marg_cost()` | Marg. value fuel reserv. capacity                  | $/UC  |

## Gas Emisssion

|                Data                |                                       Description                                       |  Unit  |
| :--------------------------------- | :-------------------------------------------------------------------------------------- | :----: |
| `GasEmission():budget_marg_cost()` | Change in operating cost with respect to an infinitesimal change in the emission budget | $/unit |
| `GasEmission():budget()`           | Emission budget that can still be used at the end of the stage                          |  unit  |
| `GasEmission():total()`            | Total gas emission                                                                      |  unit  |
| `GasEmission():budget_violation()` | Emission budget violation                                                               |  unit  |

## Gas Node

|               Data                |                                            Description                                            |  Unit   |
| :-------------------------------- | :------------------------------------------------------------------------------------------------ | :-----: |
| `GasNode():max_gas_production()`  | Maximum gas production by system                                                                  |  MUV/d  |
| `GasNode():min_gas_production()`  | Minimum gas production by system                                                                  |  MUV/d  |
| `GasNode():gas_production()`      | Gas production by system                                                                          |  MUV/d  |
| `GasNode():gas_production_cost()` | Gas production cost by system                                                                     |  $/UV   |
| `GasNode():gas_marg_cost()`       | Gas constraint marginal cost                                                                      |  $/UV   |
| `GasNode():gas_prod_marg_cost()`  | Variation of the operating cost with respect to an infinitesimal variation of the gas production. | k$/MUVd |

## Generation Constraint

|                   Data                    |                                          Description                                           | Unit  |
| :---------------------------------------- | :--------------------------------------------------------------------------------------------- | :---: |
| `GenerationConstraint():value()`          | Generation constraints                                                                         |  MW   |
| `GenerationConstraint():violation()`      | Generation constraint violation                                                                |  MW   |
| `GenerationConstraint():violation_cost()` | Penalty for generation constraint violation                                                    |  k$   |
| `GenerationConstraint():marginal_cost()`  | Change in operating cost with respect to an infinitesimal change in the generation constraint. | k$/MW |

## Generic Constraint

|                  Data                  |               Description                |  Unit  |
| :------------------------------------- | :--------------------------------------- | :----: |
| `GenericConstraint():marginal_cost()`  | Generic linear constraint marginal cost  | $/unit |
| `GenericConstraint():violation()`      | Generic linear constraint violation      |  unit  |
| `GenericConstraint():violation_cost()` | Generic linear constraint violation cost |   k$   |

## Generic Constraint Interpolation

|                        Data                         |                   Description                   |  Unit  |
| :-------------------------------------------------- | :---------------------------------------------- | :----: |
| `GenericConstraintInterpolation():marginal_cost()`  | Generic interpolation constraint marginal cost  | $/unit |
| `GenericConstraintInterpolation():violation()`      | Generic interpolation constraint violation      |  unit  |
| `GenericConstraintInterpolation():violation_cost()` | Generic interpolation constraint violation cost |   k$   |

## Generic Variable

|            Data             |      Description      | Unit  |
| :-------------------------- | :-------------------- | :---: |
| `GenericVariable():value()` | Generic variable      | unit  |
| `GenericVariable():cost()`  | Generic variable cost |  k$   |

## Hydro

|                           Data                           |                                                                                                              Description                                                                                                              |  Unit   |
| :------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----: |
| `Hydro():load("volale")`                                 | Alert storage                                                                                                                                                                                                                         |   hm3   |
| `Hydro():available_capacity()`                           | Available hydro capacity. Varies with the reservoir levels, given that the coefficient factors are a function of the reservoir water storage.                                                                                         |   MW    |
| `Hydro():historical_inflow()`                            | Historic inflows average                                                                                                                                                                                                              |  m3/s   |
| `Hydro():inflow()`                                       | Historical or synthetic inflows used by the SDDP model (forward series)                                                                                                                                                               |  m3/s   |
| `Hydro():load("volmax")`                                 | Maximum storage                                                                                                                                                                                                                       |   hm3   |
| `Hydro():load("mxtout")`                                 | Maximum total outflow (max. sum of turbining and spilling outflows)                                                                                                                                                                   |  m3/s   |
| `Hydro():load("qmaxim")`                                 | Maximum turbined outflow                                                                                                                                                                                                              |  m3/s   |
| `Hydro():security_storage()`                             | Minimum security storage                                                                                                                                                                                                              |   hm3   |
| `Hydro():load("mntout")`                                 | Minimum total outflow (min. sum of turbining and spilling outflows)                                                                                                                                                                   |  m3/s   |
| `Hydro():min_turbining()`                                | Minimum turbined outflow                                                                                                                                                                                                              |  m3/s   |
| `Hydro():spillage_unitary_cost()`                        | Unit cost of hydro spillage                                                                                                                                                                                                           | k$/hm3  |
| `Hydro():alert_violation_cost()`                         | Unit violation cost (penalty) of alert storage                                                                                                                                                                                        | k$/hm3  |
| `Hydro():max_total_outflow_cost()`                       | Violation cost of maximum total outflow in hydro plants                                                                                                                                                                               |   k$    |
| `Hydro():min_op_storage_cost()`                          | Unit violation cost (penalty) of minimum operative storage                                                                                                                                                                            | k$/hm3  |
| `Hydro():min_total_outflow_cost()`                       | Violation cost of minimum total outflow                                                                                                                                                                                               |   k$    |
| `Hydro():final_head()`                                   | Water head in the reservoirs at the end of the period                                                                                                                                                                                 |    m    |
| `Hydro():final_storage()`                                | Storage of the reservoirs at the end of the period.                                                                                                                                                                                   |   hm3   |
| `Hydro():generation()`                                   | Hydro generation                                                                                                                                                                                                                      |   GWh   |
| `Hydro():spillage()`                                     | Spilled outflow in the hydro stations                                                                                                                                                                                                 |  m3/s   |
| `Hydro():turbining()`                                    | Turbined outflow in the hydro stations                                                                                                                                                                                                |  m3/s   |
| `Hydro():water_value()`                                  | Change in operating cost with respect to an infinitesimal change of the water availability in the hydro plants reservoirs at the beginning of the stage.                                                                              | k$/hm3  |
| `Hydro():max_storage_marg_cost()`                        | Change in operating cost with respect to an infinitesimal change in the minimum \ maximum storage capacity of the hydro plants.                                                                                                       | k$/hm3  |
| `Hydro():prod_factor_marg_cost()`                        | Change in operating cost with respect to an infinitesimal change in the production factor in the hydro plant.                                                                                                                         |  $/ro   |
| `Hydro():max_turbining_marg_cost()`                      | Change in operating cost with respect to an infinitesimal change in maximum turbined capacity of the hydro plants.                                                                                                                    | k$/m3/s |
| `Hydro():bus_income()`                                   | Spot revenue of the hydro plants based on the marginal cost of the bus where the plant is located.                                                                                                                                    |   k$    |
| `Hydro():production_factor()`                            | Production factor of the hydro stations. Function of the storage level in the reservoirs.                                                                                                                                             | MW/m3/s |
| `Hydro():opportunity_cost()`                             | Given by the division of the water value of a hydro plant and the hydro plant located downstream, by the coefficient factor of the hydro plant.                                                                                       |  $/MWh  |
| `Hydro():nominal_capacity()`                             | Nominal hydro capacity. Calculated with a constant (average) production factor defined in the hydro configuration screen.                                                                                                             |   MW    |
| `Hydro():load("coshid")`                                 | Operation & Maintenance cost of hydro plants                                                                                                                                                                                          |   k$    |
| `Hydro():load("tsfhid")`                                 | Hydro Forced Outage Rate                                                                                                                                                                                                              |    %    |
| `Hydro():operating_units()`                              | Number of hydro operating units (maintenance not considered)                                                                                                                                                                          |    0    |
| `Hydro():flood_control_storage()`                        | Flood control storage                                                                                                                                                                                                                 |   hm3   |
| `Hydro():load("tihhid")`                                 | Hydro Composite Outage Rate                                                                                                                                                                                                           |    %    |
| `Hydro():turbinable_spilled_energy()`                    | Turbinable spilled energy in the hydro stations. Corresponds to the energy that has been spilled for some reason (e.g. due to some constraints) but that could have been turbined from the plant’s turbining availability perspective |   GWh   |
| `Hydro():min_turbining_violation_cost()`                 | Violation cost of the minimum turbined outflow constraint                                                                                                                                                                             |   k$    |
| `Hydro():load("qriego")`                                 | Irrigation                                                                                                                                                                                                                            |  m3/s   |
| `Hydro():irrigation_violation()`                         | Irrigation violation                                                                                                                                                                                                                  |  m3/s   |
| `Hydro():single_reserve_req()`                           | Hydro single reserve requirement                                                                                                                                                                                                      |   MW    |
| `Hydro():security_storage_violation()`                   | Minimum security storage violation                                                                                                                                                                                                    |   hm3   |
| `Hydro():alert_storage_violation()`                      | Alert storage violation                                                                                                                                                                                                               |   hm3   |
| `Hydro():min_turbining_violation()`                      | Minimum turbined outflow violation                                                                                                                                                                                                    |  m3/s   |
| `Hydro():max_total_outflow_violation()`                  | Maximum total outflow violation                                                                                                                                                                                                       |  m3/s   |
| `Hydro():min_total_outflow_violation()`                  | Minimum total outflow violation                                                                                                                                                                                                       |  m3/s   |
| `Hydro():production_factor_65()`                         | Production factor of hydro station at a storage level of 65% of the useful storage                                                                                                                                                    | MW/m3/s |
| `Hydro():stored_energy()`                                | Stored energy in each reservoir of the system                                                                                                                                                                                         |   GWh   |
| `Hydro():capacity_margin()`                              | Total hydro generation reserve, defined as the difference between the total nominal hydro capacity and the current generation.                                                                                                        |   MW    |
| `Hydro():single_reserve()`                               | Single hydro generation reserve, defined as the single reserve for the units in activity (with generation greater than zero) and equal to zero otherwise.                                                                             |   MW    |
| `Hydro():joint_reserve()`                                | Joint reserve for hydro plants                                                                                                                                                                                                        |   MW    |
| `Hydro():shp_prod_factor()`                              | Production factor of the hydro stations, based on the storage-head polynomial function.                                                                                                                                               | MW/m3/s |
| `Hydro():min_turb_outflow_marg_cost()`                   | Variation of the operating cost with respect to an infinitesimal variation of the minimum turbined outflow                                                                                                                            | k$/m3/s |
| `Hydro():capacity_without_outages()`                     | Hydro capacity by plant without outages                                                                                                                                                                                               |   MW    |
| `Hydro():filtration()`                                   | Filtration by hydro plant                                                                                                                                                                                                             |  m3/s   |
| `Hydro():dispatch_factor()`                              | Percentage of hydro utilization                                                                                                                                                                                                       |    %    |
| `Hydro():evaporation()`                                  | Evaporation by hydro plant                                                                                                                                                                                                            |  m3/s   |
| `Hydro():irrigation_penalty()`                           | Penalty for irrigation violation                                                                                                                                                                                                      |   k$    |
| `Hydro():single_reserve_marg_cost()`                     | Change in operating cost with respect to an infinitesimal change in the hydro single reserve constraint.                                                                                                                              |  k$/MW  |
| `Hydro():available_turbining()`                          | Minimum between the maximum outflow, discounted the FOR/COR, and the maximum capacity divided by the production factor                                                                                                                |  m3/s   |
| `Hydro():volume_variations()`                            | Lago Junin volume variations                                                                                                                                                                                                          |    %    |
| `Hydro():lgc_gen_above_ref()`                            | LGC generation above the reference value                                                                                                                                                                                              |   GWh   |
| `Hydro():lgc_revenue()`                                  | Revenue due to the LGC generation above the reference value                                                                                                                                                                           |   k$    |
| `Hydro():initial_storage()`                              | Storage levels in the beginning of the stages                                                                                                                                                                                         |   hm3   |
| `Hydro():spilled_energy()`                               | Spilled energy by plant                                                                                                                                                                                                               |   GWh   |
| `Hydro():final_storage_perc()`                           | Final storage (%)                                                                                                                                                                                                                     |    %    |
| `Hydro():system_income()`                                | Spot revenue of the hydro plants based on the system marginal cost.                                                                                                                                                                   |   k$    |
| `Hydro():typical_final_storage()`                        | Projected storage of the reservoirs at the end of the typical day.                                                                                                                                                                    |   hm3   |
| `Hydro():chron_final_storage()`                          | Projected storage of the reservoirs at the end of the chronological week.                                                                                                                                                             |   hm3   |
| `Hydro():spillage_cost()`                                | Cost of hydro spillage                                                                                                                                                                                                                |   k$    |
| `Hydro():joint_reserve_cost()`                           | Hydro joint reserve cost                                                                                                                                                                                                              |   k$    |
| `Hydro():inflow_energy()`                                | Inflow energy per hydro. They are given by the product of the water inflow to the plant with the sum of the variable production factors of the set of plants that are downstream, including the plant's own production factor.        |   GWh   |
| `Hydro():acc_production_factor()`                        | Accumulated production factor                                                                                                                                                                                                         | MW/m3/s |
| `Hydro():target_storage_violation()`                     | Target storage violation                                                                                                                                                                                                              |   hm3   |
| `Hydro():max_op_storage_violation_cost()`                | Viol. cost of max op. storage                                                                                                                                                                                                         |   k$    |
| `Hydro():max_op_storage_violation()`                     | Violation of maximum operative storage constraint                                                                                                                                                                                     |   hm3   |
| `Hydro():max_op_storage()`                               | Maximum operative storage                                                                                                                                                                                                             |   hm3   |
| `Hydro():max_op_storage_marg_cost()`                     | Change in operating cost with respect to an infinitesimal change in the limit of the maximum operative storage constraint                                                                                                             | k$/hm3  |
| `Hydro():max_spillage_violation()`                       | Violation maximum spillage                                                                                                                                                                                                            |  m3/s   |
| `Hydro():max_spillage_violation_cost()`                  | Violation cost of maximum spillage constraint                                                                                                                                                                                         |   k$    |
| `Hydro():load("mxsout")`                                 | Maximum spillage constraint                                                                                                                                                                                                           |  m3/s   |
| `Hydro():acc_prod_factor_65()`                           | Accumulated production factor of hydro station at a storage level of 65% of the useful storage                                                                                                                                        | MW/m3/s |
| `Hydro():max_stored_energy()`                            | Maximum stored energy in each reservoir of the system                                                                                                                                                                                 |   GWh   |
| `Hydro():outflow_ramp_violation()`                       | Violation of hydro outflow ramp                                                                                                                                                                                                       |  m3/s   |
| `Hydro():stored_energy_perc()`                           | Percentage of stored energy in each reservoir of the system                                                                                                                                                                           |    %    |
| `Hydro():spill_lost_energy()`                            | Energy lost in the system due to hydro spillage                                                                                                                                                                                       |   GWh   |
| `Hydro():tailwater_elevation()`                          | Hydro plant tailwater elevation                                                                                                                                                                                                       |    m    |
| `Hydro():total_inflow()`                                 | Total inflows: sum of incremental inflows of upstream hydrological stations                                                                                                                                                           |  m3/s   |
| `Hydro():upstream_plants()`                              | Inflow due to upstream plants turbining and spilling                                                                                                                                                                                  |  m3/s   |
| `Hydro():turbinable_spilled_outflow()`                   | Turbinable spilled outflow per hydro plants                                                                                                                                                                                           |  m3/s   |
| `Hydro():load("wtarget")`                                | Target storage                                                                                                                                                                                                                        |   hm3   |
| `Hydro():load("hydro_outflow_rampup_marg_cost")`         | Variation of the operating cost with respect to an infinitesimal variation of the outflow ramp-up                                                                                                                                     | k$/unit |
| `Hydro():load("hydro_outflow_rampdown_marg_cost")`       | Variation of the operating cost with respect to an infinitesimal variation of the outflow ramp-down                                                                                                                                   | k$/unit |
| `Hydro():load("hydro_turbining_rampup_marg_cost")`       | Variation of the operating cost with respect to an infinitesimal variation of the turbining ramp-up                                                                                                                                   | k$/unit |
| `Hydro():load("hydro_turbining_rampdown_marg_cost")`     | Variation of the operating cost with respect to an infinitesimal variation of the turbining ramp-down                                                                                                                                 | k$/unit |
| `Hydro():load("hydro_spilling_rampup_marg_cost")`        | Variation of the operating cost with respect to an infinitesimal variation of the spilling ramp-up                                                                                                                                    | k$/unit |
| `Hydro():load("hydro_spilling_rampdown_marg_cost")`      | Variation of the operating cost with respect to an infinitesimal variation of the spilling ramp-down                                                                                                                                  | k$/unit |
| `Hydro():load("hydro_forebay_rampup_marg_cost")`         | Variation of the operating cost with respect to an infinitesimal variation of the forebay ramp-up                                                                                                                                     | k$/m/h  |
| `Hydro():load("hydro_forebay_rampdown_marg_cost")`       | Variation of the operating cost with respect to an infinitesimal variation of the forebay ramp-down                                                                                                                                   | k$/m/h  |
| `Hydro():load("hydro_forebay_day_rampup_marg_cost")`     | Variation of the operating cost with respect to an infinitesimal variation of the forebay daily ramp-up                                                                                                                               | k$/m/d  |
| `Hydro():load("hydro_forebay_day_rampdown_marg_cost")`   | Variation of the operating cost with respect to an infinitesimal variation of the forebay daily ramp-down                                                                                                                             | k$/m/d  |
| `Hydro():max_joint_reserve()`                            | Hydro maximum joint reserve                                                                                                                                                                                                           |   MW    |
| `Hydro():joint_reserve_price()`                          | Hydro joint reserve price                                                                                                                                                                                                             |  $/MWh  |
| `Hydro():curve_violation()`                              | Guide curve violation per hydro reservoir                                                                                                                                                                                             |   hm3   |
| `Hydro():joint_reserve_nexc()`                           | Hydro joint reserve that can be shared between non-exclusive requirements                                                                                                                                                             |   MW    |
| `Hydro():forebay_rampup_violation()`                     | Forebay ramp-up violation                                                                                                                                                                                                             |   m/h   |
| `Hydro():forebay_rampdown_violation()`                   | Forebay ramp-down violation                                                                                                                                                                                                           |   m/h   |
| `Hydro():forebay_day_rampup_violation()`                 | Forebay daily ramp-up violation                                                                                                                                                                                                       |   m/d   |
| `Hydro():forebay_day_rampdown_violation()`               | Forebay daily ramp-down violation                                                                                                                                                                                                     |   m/d   |
| `Hydro():outflow_rampup_violation()`                     | Outflow ramp-up violation                                                                                                                                                                                                             | m³/s/h  |
| `Hydro():outflow_rampdown_violation()`                   | Outflow ramp-down violation                                                                                                                                                                                                           | m³/s/h  |
| `Hydro():turbining_rampup_violation()`                   | Turbining ramp-up violation                                                                                                                                                                                                           | m³/s/h  |
| `Hydro():turbining_rampdown_violation()`                 | Turbining ramp-down violation                                                                                                                                                                                                         | m³/s/h  |
| `Hydro():spilling_rampup_violation()`                    | Spilling ramp-up violation                                                                                                                                                                                                            | m³/s/h  |
| `Hydro():spilling_rampdown_violation()`                  | Spilling ramp-down violation                                                                                                                                                                                                          | m³/s/h  |
| `Hydro():outflow_day_rampup_violation()`                 | Outflow daily ramp-up violation                                                                                                                                                                                                       | m³/s/d  |
| `Hydro():outflow_day_rampdown_violation()`               | Outflow daily ramp-down violation                                                                                                                                                                                                     | m³/s/d  |
| `Hydro():turbining_day_rampup_violation()`               | Turbining daily ramp-up violation                                                                                                                                                                                                     | m³/s/d  |
| `Hydro():turbining_day_rampdown_violation()`             | Turbining daily ramp-down violation                                                                                                                                                                                                   | m³/s/d  |
| `Hydro():spilling_day_rampup_violation()`                | Spilling daily ramp-up violation                                                                                                                                                                                                      | m³/s/d  |
| `Hydro():spilling_day_rampdown_violation()`              | Spilling daily ramp-down violation                                                                                                                                                                                                    | m³/s/d  |
| `Hydro():load("hydro_outflow_day_rampup_marg_cost")`     | Variation of the operating cost with respect to an infinitesimal variation of the outflow daily ramp-up                                                                                                                               | k$/unit |
| `Hydro():load("hydro_outflow_day_rampdown_marg_cost")`   | Variation of the operating cost with respect to an infinitesimal variation of the outflow daily ramp-down                                                                                                                             | k$/unit |
| `Hydro():load("hydro_turbining_day_rampup_marg_cost")`   | Variation of the operating cost with respect to an infinitesimal variation of the turbining daily ramp-up                                                                                                                             | k$/unit |
| `Hydro():load("hydro_turbining_day_rampdown_marg_cost")` | Variation of the operating cost with respect to an infinitesimal variation of the turbining daily ramp-down                                                                                                                           | k$/unit |
| `Hydro():load("hydro_spilling_day_rampup_marg_cost")`    | Variation of the operating cost with respect to an infinitesimal variation of the spilling daily ramp-up                                                                                                                              | k$/unit |
| `Hydro():load("hydro_spilling_day_rampdown_marg_cost")`  | Variation of the operating cost with respect to an infinitesimal variation of the spilling daily ramp-down                                                                                                                            | k$/unit |
| `Hydro():min_spillage_violation()`                       | Violation minimum spillage                                                                                                                                                                                                            |  m3/s   |
| `Hydro():min_spillage_violation_cost()`                  | Violation cost of minimum spillage constraint                                                                                                                                                                                         |   k$    |
| `Hydro():load("mnsout")`                                 | Minimum spillage constraint                                                                                                                                                                                                           |  m3/s   |
| `Hydro():load("qriego")`                                 | Irrigation                                                                                                                                                                                                                            |  m3/s   |

## Hydro Generator

|                     Data                      |                 Description                 | Unit  |
| :-------------------------------------------- | :------------------------------------------ | :---: |
| `HydroGenerator():unit_generation()`          | Hydro unit generation                       |  GWh  |
| `HydroGenerator():turbining_violation()`      | Minimum hydro unit turbining violation      | m3/s  |
| `HydroGenerator():turbining_violation_cost()` | Minimum hydro unit turbining violation cost |  k$   |

## Interconnection

|                  Data                  |                                                 Description                                                  | Unit  |
| :------------------------------------- | :----------------------------------------------------------------------------------------------------------- | :---: |
| `Interconnection():flow()`             | Interconnection flow between systems                                                                         |  GWh  |
| `Interconnection():marginal_cost()`    | Change in operating cost with respect to an infinitesimal change in the interconnection capacity (limit).    | k$/MW |
| `Interconnection():capacity_from_to()` | Interconnection capacity FROM->TO                                                                            |  MW   |
| `Interconnection():income()`           | Interconnection income given by the product of the interconnection flow and the reduced cost of the variable |  k$   |
| `Interconnection():cost_from_to()`     | Interconnection cost FROM->TO between systems                                                                | $/MWh |
| `Interconnection():total_cost()`       | Total interconnection cost between systems                                                                   |  k$   |
| `Interconnection():losses()`           | Interconnection losses                                                                                       |  MW   |
| `Interconnection():capacity_to_from()` | Interconnection capacity TO->FROM                                                                            |  MW   |
| `Interconnection():cost_to_from()`     | Interconnection cost TO->FROM between systems                                                                | $/MWh |
| `Interconnection():joint_reserve()`    | Interconnection joint reserve                                                                                |  MW   |
| `Interconnection():max_flow_limit()`   | Maximum interconnection flow                                                                                 |  MW   |
| `Interconnection():min_reverse_flow()` | Minimum interconnection flow in the opposite direction                                                       |  MW   |

## Interconnection Sum

|                  Data                  |                                               Description                                               | Unit  |
| :------------------------------------- | :------------------------------------------------------------------------------------------------------ | :---: |
| `InterconnectionSum():upper_bound()`   | Upper bound for the interconnection sum constraint                                                      |  MW   |
| `InterconnectionSum():lower_bound()`   | Lower bound for the interconnection sum constraint                                                      |  MW   |
| `InterconnectionSum():sum()`           | Interconnection sum constraints                                                                         |  MW   |
| `InterconnectionSum():sum_marg_cost()` | Change in operating cost with respect to an infinitesimal change in the interconnection sum constraint. | k$/MW |

# Load

|                Data                 |                                       Description                                       | Unit  |
| :---------------------------------- | :-------------------------------------------------------------------------------------- | :---: |
| `Load():supplied()`                 | Supplied load of each class (sum of the elastic and inelastic components)               |  GWh  |
| `Load():inelastic()`                | Total inelastic load per class                                                          |  GWh  |
| `Load():maximum()`                  | Maximum load of each class: sum of the elastic and inelastic loads of each class        |  GWh  |
| `Load():revenue()`                  | Economic benefit with the sale of energy for the elastic portions of each class of load |  k$   |
| `Load():elastic_load_level_price()` | Elastic load price per level                                                            | $/MWh |

## Power Injection

|                Data                |                                       Description                                       | Unit  |
| :--------------------------------- | :-------------------------------------------------------------------------------------- | :---: |
| `PowerInjection():violation()`     | Fixed power injection violation                                                         |  MWh  |
| `PowerInjection():value()`         | Power injections                                                                        |  GWh  |
| `PowerInjection():cost()`          | Power injection cost                                                                    |  k$   |
| `PowerInjection():marginal_cost()` | Change in operating cost with respect to an infinitesimal change in the power injection | $/MWh |

## Renewable

|                   Data                   |                                                  Description                                                  | Unit  |
| :--------------------------------------- | :------------------------------------------------------------------------------------------------------------ | :---: |
| `Renewable():generation()`               | Renewable source generation                                                                                   |  GWh  |
| `Renewable():bus_income()`               | Spot revenue of renewable source generation based on the marginal cost of the bus where the plant is located. |  k$   |
| `Renewable():capacity_marg_cost()`       | Change in operating cost with respect to an infinitesimal change in the renewable installed capacity.         | k$/MW |
| `Renewable():nominal_capacity()`         | Renewable sources capacity.                                                                                   |  MW   |
| `Renewable():system_income()`            | Spot revenue of renewable source generation based on the system marginal cost.                                |  k$   |
| `Renewable():curtailment()`              | Renewable generation spillage                                                                                 |  GWh  |
| `Renewable():scenario()`                 | Renewable associated station scenario generation                                                              |  pu   |
| `Renewable():load("cogoem")`             | Operation and maintenance cost by renewable plant                                                             |  k$   |
| `Renewable():dispatch_factor()`          | Percentage of renewable utilization                                                                           |   %   |
| `Renewable():om_unitary_cost()`          | Operation and maintenance unitary cost by renewable plant                                                     | $/MWh |
| `Renewable():available_capacity()`       | Renewable available capacity scenario                                                                         |  MW   |
| `Renewable():joint_reserve()`            | Joint reserve for renewable plants                                                                            |  MW   |
| `Renewable():joint_reserve_nexc()`       | Renewable joint reserve that can be shared between non-exclusive requirements                                 |  MW   |
| `Renewable():joint_reserve_cost()`       | Renewable joint reserve cost                                                                                  |  k$   |
| `Renewable():max_joint_reserve()`        | Renewable maximum joint reserve                                                                               |  MW   |
| `Renewable():joint_reserve_price()`      | Renewable joint reserve price                                                                                 | $/MWh |
| `Renewable():non_reserved_curtailment()` | Renewable generation spillage not allocated to reserve                                                        |  GWh  |

## Renewable Generator

|                Data                 |             Description              | Unit  |
| :---------------------------------- | :----------------------------------- | :---: |
| `RenewableGenerator():generation()` | Renewable generator group generation |  GWh  |

## Reserve Generation Constraint

|                       Data                       |                                            Description                                            | Unit  |
| :----------------------------------------------- | :------------------------------------------------------------------------------------------------ | :---: |
| `ReserveGenerationConstraint():requirement()`    | Minimum joint reserve requirement                                                                 |  MW   |
| `ReserveGenerationConstraint():value()`          | Amount of the resulting joint reserve                                                             |  MW   |
| `ReserveGenerationConstraint():marginal_cost()`  | Change in operating cost with respect to an infinitesimal change in the joint reserve constraint. | k$/MW |
| `ReserveGenerationConstraint():violation()`      | Joint reserve violation                                                                           |  MW   |
| `ReserveGenerationConstraint():violation_cost()` | Penalty for joint reserve constraint violation                                                    |  k$   |

## Reservoir Set

|                          Data                          |                                    Description                                    | Unit  |
| :----------------------------------------------------- | :-------------------------------------------------------------------------------- | :---: |
| `ReservoirSet():security_energy_violation()`           | Violation of security energy constraint by reservoir set                          |  GWh  |
| `ReservoirSet():alert_energy_violation()`              | Violation of alert energy constraint by reservoir set                             |  GWh  |
| `ReservoirSet():flood_control_energy_violation()`      | Violation of flood control energy constraint by reservoir set                     |  GWh  |
| `ReservoirSet():stored_energy()`                       | Stored energy in a set of reservoirs                                              |  GWh  |
| `ReservoirSet():load("eneale")`                        | Alert energy by reservoir set                                                     |  GWh  |
| `ReservoirSet():load("eneesp")`                        | Flood control by reservoir set                                                    |  GWh  |
| `ReservoirSet():load("enemin")`                        | Security energy by reservoir set                                                  |  GWh  |
| `ReservoirSet():security_energy_violation_cost()`      | Violation cost of security energy by reservoir set                                |  k$   |
| `ReservoirSet():alert_energy_violation_cost()`         | Violation cost of alert energy by reservoir set                                   |  k$   |
| `ReservoirSet():flood_control_energy_violation_cost()` | Violation cost of flood control energy by reservoir set                           |  k$   |
| `ReservoirSet():energy_perc()`                         | Stored energy in a set of reservoirs as a percentage of the maximum stored energy |   %   |

## Series Capacitor

|                   Data                   |                                                Description                                                | Unit  |
| :--------------------------------------- | :-------------------------------------------------------------------------------------------------------- | :---: |
| `SeriesCapacitor():flow()`               | Controllable serie capacitor flow                                                                         |  MW   |
| `SeriesCapacitor():capacity_marg_cost()` | Change in operating cost with respect to a infinitesimal change in the series capacitor capacity (limit). | k$/MW |
| `SeriesCapacitor():losses()`             | Series capacitors quadratic losses approximation, obtained through linearizations                         |  MW   |
| `SeriesCapacitor():quadratic_losses()`   | Series capacitors theoretical quadratic losses                                                            |  MW   |
| `SeriesCapacitor():losses_mismatch()`    | Series capacitors losses error                                                                            |  MW   |

## Study

|               Data                |                   Description                   | Unit  |
| :-------------------------------- | :---------------------------------------------- | :---: |
| `Study():future_cost()`           | Future cost                                     |  k$   |
| `Study():objective_cost()`        | Operation costs report for each stage and serie |  k$   |
| `Study():hour_block_mapping()`    | Hour-block mapping                              | Block |
| `Study():hourly_solution_stats()` | Hourly solution status                          |  ---  |

## System

|                   Data                    |                                                                                                         Description                                                                                                          |  Unit  |
| :---------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: |
| `System():demand()`                       | Total inelastic load per system                                                                                                                                                                                              |  GWh   |
| `System():max_stored_energy()`            | Maximum stored energy                                                                                                                                                                                                        |  GWh   |
| `System():deficit_cost()`                 | Deficit cost                                                                                                                                                                                                                 |   k$   |
| `System():deficit()`                      | System deficit                                                                                                                                                                                                               |  GWh   |
| `System():stored_energy()`                | System stored energy in the reservoirs                                                                                                                                                                                       |  GWh   |
| `System():marginal_cost()`                | Change in operating cost with respect to an infinitesimal change in the system load.                                                                                                                                         | $/MWh  |
| `System():load_rationing()`               | Percentage of the rationing with respect of the load.                                                                                                                                                                        |   %    |
| `System():expected_load_rationing()`      | Expected value of the percentage of rationing with respect to the load, given that this percentage is greater than 1.5%                                                                                                      |   %    |
| `System():spilled_energy()`               | Spilled energy of the system                                                                                                                                                                                                 |  GWh   |
| `System():ref_inflow_energy()`            | It is the sum of the inflow energies to each hydro plant. These, in turn, are given by the product of the water inflow to the plant with the sum of the average production factors of the set of plants that are downstream  |  GWh   |
| `System():stored_energy_perc()`           | Percentage of the stored energy in the system with respect to the maximum stored energy                                                                                                                                      |   %    |
| `System():inflow_energy_65()`             | It is the sum of the inflow energies to each hydro plant considering the variable production factors, corresponding to 65% of the net volume.                                                                                |  GWh   |
| `System():risk_aversion_limit()`          | Limit of the Risk Aversion Curve                                                                                                                                                                                             |  GWh   |
| `System():risk_aversion_marg_cost()`      | Marginal cost of the Risk Aversion Curve - Change in operating cost with respect to an infinitesimal change in the Risk Aversion Curve                                                                                       | k$/MWh |
| `System():risk_aversion_violation_cost()` | Violation cost of the Risk Aversion Curve                                                                                                                                                                                    |   k$   |
| `System():risk_aversion_violation()`      | Risk Aversion Curve violation                                                                                                                                                                                                |  GWh   |
| `System():demand_supplied()`              | Total elastic and inelastic load supplied per system                                                                                                                                                                         |  GWh   |
| `System():max_demand()`                   | Maximum load of each system: sum of the elastic and inelastic loads of each system                                                                                                                                           |  GWh   |
| `System():max_stored_energy_65()`         | Maximum stored energy calculated at a storage level of 65% of the useful storage                                                                                                                                             |  GWh   |
| `System():deficit_perc()`                 | Deficit (% of load)                                                                                                                                                                                                          |   %    |
| `System():immediate_cost()`               | Immediate cost per system                                                                                                                                                                                                    |   k$   |
| `System():deficit_risk()`                 | Deficit risk per system                                                                                                                                                                                                      |   %    |
| `System():block_duration()`               | Load level length                                                                                                                                                                                                            |   h    |
| `System():inflow_energy()`                | It is the sum of the inflow energies to each hydro plant. These, in turn, are given by the product of the water inflow to the plant with the sum of the variable production factors of the set of plants that are downstream |  GWh   |
| `System():shp_stored_energy()`            | System stored energy in the reservoirs calculated based on the production factor – SHP.                                                                                                                                      |  GWh   |

## Thermal

|                      Data                       |                                                                                                     Description                                                                                                      |  Unit   |
| :---------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: |
| `Thermal():available_capacity()`                | Available thermal capacity                                                                                                                                                                                           |   MW    |
| `Thermal():operating_cost()`                    | Operative cost considering the fuel consumption cost and the O&M cost by thermal plant                                                                                                                               |   k$    |
| `Thermal():generation()`                        | Thermal plants generation                                                                                                                                                                                            |   GWh   |
| `Thermal():capacity_marg_cost()`                | Change in operating cost with respect to an infinitesimal change in the thermal installed capacity.                                                                                                                  |  k$/MW  |
| `Thermal():load("cosarr")`                      | Start-up cost of commitment thermal plants                                                                                                                                                                           |   k$    |
| `Thermal():bus_income()`                        | Spot revenue of the thermal plants based on the marginal cost of the bus where the plant is located.                                                                                                                 |   k$    |
| `Thermal():load("tgmin")`                       | Thermal minimum generation constraint requirement                                                                                                                                                                    |   MW    |
| `Thermal():net_min_generation()`                | Minimum thermal generation. It is defined as the maximum value between the minimum generation considering the outage rates and maintenance factors and the minimum operation constraints (chronological constraints) |   MW    |
| `Thermal():unitary_cost_seg1()`                 | Thermal plt. unit cost- segment 1                                                                                                                                                                                    |  $/MWh  |
| `Thermal():unitary_cost_seg2()`                 | Thermal plt. unit cost- segment 2                                                                                                                                                                                    |  $/MWh  |
| `Thermal():unitary_cost_seg3()`                 | Thermal plt. unit cost- segment 3                                                                                                                                                                                    |  $/MWh  |
| `Thermal():input_startup_cost()`                | Startup cost data for the commitment thermal plants                                                                                                                                                                  |   k$    |
| `Thermal():load("tsfter")`                      | Thermal Forced Outage Rate                                                                                                                                                                                           |    %    |
| `Thermal():operating_units()`                   | Number of thermal operating units (maintenance not considered)                                                                                                                                                       |    0    |
| `Thermal():nominal_capacity()`                  | Nominal thermal capacity                                                                                                                                                                                             |   MW    |
| `Thermal():load("tihter")`                      | Thermal Composite Outage Rate                                                                                                                                                                                        |    %    |
| `Thermal():single_reserve_req()`                | Thermal single reserve requirement                                                                                                                                                                                   |   MW    |
| `Thermal():gas_consumption()`                   | Gas consumption by thermal plant                                                                                                                                                                                     |  MUV/d  |
| `Thermal():fuel_consumption()`                  | Fuel consumption for each thermal plant according to the generation.                                                                                                                                                 | k.units |
| `Thermal():capacity_margin()`                   | Total thermal generation reserve, defined as the difference between the total nominal thermal capacity and the current generation.                                                                                   |   MW    |
| `Thermal():single_reserve()`                    | Single thermal generation reserve, defined as the single reserve for the units in activity (with generation greater than zero) and equal to zero otherwise.                                                          |   MW    |
| `Thermal():joint_reserve()`                     | Joint reserve for thermal plants                                                                                                                                                                                     |   MW    |
| `Thermal():dispatch_factor()`                   | Percentage of thermal utilization                                                                                                                                                                                    |    %    |
| `Thermal():single_reserve_marg_cost()`          | Change in operating cost with respect to an infinitesimal change in the thermal single reserve constraint.                                                                                                           |  k$/MW  |
| `Thermal():carbon_emission_cost()`              | Carbon emission cost by thermal plant                                                                                                                                                                                |   k$    |
| `Thermal():total_cost()`                        | Operation plus emissions cost by thermal plant                                                                                                                                                                       |   k$    |
| `Thermal():carbon_emission()`                   | Carbon emission by thermal plant                                                                                                                                                                                     | tonCO2  |
| `Thermal():carbon_cost_seg1()`                  | Thermal plant’s unit cost of CO2 emission - segment 1                                                                                                                                                                |  $/MWh  |
| `Thermal():carbon_cost_seg2()`                  | Thermal plant’s unit cost of CO2 emission - segment 2                                                                                                                                                                |  $/MWh  |
| `Thermal():carbon_cost_seg3()`                  | Thermal plant’s unit cost of CO2 emission - segment 3                                                                                                                                                                |  $/MWh  |
| `Thermal():system_income()`                     | Spot revenue of the thermal plants based on the system marginal cost.                                                                                                                                                |   k$    |
| `Thermal():min_generation_violation()`          | Violation of thermal technical minimum generation                                                                                                                                                                    |   MW    |
| `Thermal():min_generation_violation_cost()`     | Violation cost of thermal technical minimum generation                                                                                                                                                               |   k$    |
| `Thermal():joint_reserve_cost()`                | Thermal joint reserve cost                                                                                                                                                                                           |   k$    |
| `Thermal():commitment()`                        | Thermal commitment decision                                                                                                                                                                                          |   pu    |
| `Thermal():contract_consumption()`              | Fuel contract consumption by thermal plant                                                                                                                                                                           |   kUC   |
| `Thermal():reservoir_consumption()`             | Fuel storage consumption by thermal plant                                                                                                                                                                            |   kUC   |
| `Thermal():min_generation_ctr_violation()`      | Violation of thermal minimum generation constraint                                                                                                                                                                   |   MW    |
| `Thermal():min_generation_ctr_violation_cost()` | Violation cost of thermal minimum generation constraint                                                                                                                                                              |   k$    |
| `Thermal():joint_reserve_nexc()`                | Thermal joint reserve that can be shared between non-exclusive requirements                                                                                                                                          |   MW    |
| `Thermal():combined_cycle_state()`              | Thermal combined cycle state                                                                                                                                                                                         |   0/1   |
| `Thermal():shutdown()`                          | Thermal shutdown decision                                                                                                                                                                                            |   0/1   |
| `Thermal():cost_seg_1()`                        | Thermal plant’s emission unit cost - segment 1                                                                                                                                                                       |  $/MWh  |
| `Thermal():cost_seg_2()`                        | Thermal plant’s emission unit cost - segment 2                                                                                                                                                                       |  $/MWh  |
| `Thermal():cost_seg_3()`                        | Thermal plant’s emission unit cost - segment 3                                                                                                                                                                       |  $/MWh  |
| `Thermal():max_joint_reserve()`                 | Thermal maximum joint reserve                                                                                                                                                                                        |   MW    |
| `Thermal():joint_reserve_price()`               | Thermal joint reserve price                                                                                                                                                                                          |  $/MWh  |
| `Thermal():load("cosshut")`                     | Shutdown cost of commitment thermal plants                                                                                                                                                                           |   k$    |

## Thermal Generator

|                   Data                   |                     Description                      | Unit  |
| :--------------------------------------- | :--------------------------------------------------- | :---: |
| `ThermalGenerator():generation()`        | Thermal generator group generation                   |  GWh  |
| `ThermalGenerator():commitment()`        | Thermal generator group commitment decision          |  pu   |
| `ThermalGenerator():min_gen_violation()` | Thermal generator group minimum generation violation |  MW   |

## ThreeWinding Transformer

|                       Data                       |                                                    Description                                                     | Unit  |
| :----------------------------------------------- | :----------------------------------------------------------------------------------------------------------------- | :---: |
| `ThreeWindingTransformer():flow()`               | Three winding transformer flow                                                                                     |  MW   |
| `ThreeWindingTransformer():capacity_marg_cost()` | Change in operating cost with respect to a infinitesimal change in the three winding transformer capacity (limit). | k$/MW |
| `ThreeWindingTransformer():losses()`             | Three winding transformers quadratic losses approximation, obtained through linearizations                         |  MW   |
| `ThreeWindingTransformer():quadratic_losses()`   | Three winding transformers theoretical quadratic losses                                                            |  MW   |
| `ThreeWindingTransformer():losses_mismatch()`    | Three winding transformers losses error                                                                            |  MW   |

## Transformer

|                 Data                 |                                             Description                                              | Unit  |
| :----------------------------------- | :--------------------------------------------------------------------------------------------------- | :---: |
| `Transformer():cost()`               | Transformers transmission cost                                                                       |  k$   |
| `Transformer():flow()`               | Transformer flow                                                                                     |  MW   |
| `Transformer():capacity_marg_cost()` | Change in operating cost with respect to a infinitesimal change in the transformer capacity (limit). | k$/MW |
| `Transformer():losses()`             | Transformers quadratic losses approximation, obtained through linearizations                         |  MW   |
| `Transformer():quadratic_losses()`   | Transformers theoretical quadratic losses                                                            |  MW   |
| `Transformer():losses_mismatch()`    | Transformer losses error                                                                             |  MW   |

## Water Way

|                  Data                  |             Description              |  Unit   |
| :------------------------------------- | :----------------------------------- | :-----: |
| `WaterWay():flow()`                    | Waterway flow                        |  m3/s   |
| `WaterWay():min_flow_violation()`      | Minimum waterway flow violation      |  m3/s   |
| `WaterWay():max_flow_violation()`      | Maximum waterway flow violation      |  m3/s   |
| `WaterWay():min_flow_violation_cost()` | Minimum waterway flow violation cost |   k$    |
| `WaterWay():max_flow_violation_cost()` | Maximum waterway flow violation cost |   k$    |
| `WaterWay():marginal_cost()`           | Waterway marginal cost               | k$/m3/s |
