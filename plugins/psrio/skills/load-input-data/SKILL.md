---
name: TODO
description: TODO
---

## AC Line

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ACline().code` | Unique identifier for the AC transmission line | --- |
| `ACline().state` | Operational state of the line | --- |
| `ACline().resistance` | Resistance of the transmission line | % |
| `ACline().reactance` | Reactance of the transmission line | % |
| `ACline().capacity` | Maximum power flow capacity of the line under normal conditions | MW |
| `ACline().emergency_capacity` | Maximum power flow capacity of the line under emergency conditions | MW |
| `ACline().DLR_factor` | Dynamic Line Rating factor applied to the nominal capacity | pu |
| `ACline().monitored` | Flag indicating if the line flows are monitored during the optimization | --- |
| `ACline().monitored_contingencies` | Flag indicating if the line is monitored under contingency scenarios | --- |
| `ACline().is_dc` | Flag indicating if the line is modeled as a DC line within AC power flow | --- |
| `ACline().international_cost_from` | Wheeling charge or export cost applied to flow leaving the 'from' bus | $/MWh |
| `ACline().international_cost_to` | Wheeling charge or import cost applied to flow arriving at the 'to' bus | $/MWh |

---

## Area

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Area().code` | Unique identifier for the area | --- |
| `Area().import_limit` | Maximum total power import allowed into the area | MW |
| `Area().export_limit` | Maximum total power export allowed out of the area | MW |

---

## Battery

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Battery().code` | Unique identifier for the battery system | --- |
| `Battery().state` | Operational state of the battery | --- |
| `Battery().capacity` | Maximum power output (discharge) or input (charge) of the battery | MW |
| `Battery().max_storage` | Maximum energy storage capacity of the battery | MWh |
| `Battery().min_storage` | Minimum energy storage level required | MWh |
| `Battery().om_cost` | Variable operation and maintenance cost | $/MWh |
| `Battery().charge_ramp` | Maximum rate at which the battery can increase its charging power | MW/min |
| `Battery().oem_type` | Type of Original Equipment Manufacturer or technology | --- |
| `Battery().discharge_ramp` | Maximum rate at which the battery can increase its discharging power | MW/min |
| `Battery().max_reserve` | Maximum reserve capacity the battery can provide | MW |
| `Battery().bid_price` | Price bid for the battery energy or opportunity cost | $/MWh |

---

## Bus

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Bus().code` | Unique identifier for busese | --- |
| `Bus().voltage_level` | Base voltage level of the bus | kV |

---

## Circuit

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Circuit().code` | Unique identifier for the circuit | --- |
| `Circuit().state` | Operational state of the circuit | --- |
| `Circuit().resistance` | Resistance of the circuit | % |
| `Circuit().reactance` | Reactance of the circuit | % |
| `Circuit().capacity` | Maximum power flow capacity under normal conditions | MW |
| `Circuit().emergency_capacity` | Maximum power flow capacity under emergency conditions | MW |
| `Circuit().DLR_factor` | Dynamic Line Rating factor | pu |
| `Circuit().monitored` | Flag indicating if flow is monitored | --- |
| `Circuit().monitored_contingencies` | Flag indicating monitoring under contingencies | --- |
| `Circuit().is_dc` | Flag indicating if it is a DC circuit | --- |
| `Circuit().international_cost_from` | Cost applied to flow leaving the 'from' end | $/MWh |
| `Circuit().international_cost_to` | Cost applied to flow arriving at the 'to' end | $/MWh |

---

## Circuits Sum

| Data | Description | Unit |
| :--- | :--- | :---: |
| `CircuitsSum().code` | Unique identifier for the circuit summation constraint | pu |
| `CircuitsSum().lb` | Lower bound limit for the sum of flows | MW |
| `CircuitsSum().ub` | Upper bound limit for the sum of flows | MW |

---

## Concentrated Solar Power

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ConcentratedSolarPower().hour_scenarios` | Hourly generation profile scenarios (normalized) | pu |

---

## DC Link

| Data | Description | Unit |
| :--- | :--- | :---: |
| `DCLink().code` | Unique identifier for the DC link | --- |
| `DCLink().state` | Operational state of the link | --- |
| `DCLink().capacity_from` | Maximum capacity flowing from the source node | MW |
| `DCLink().capacity_to` | Maximum capacity flowing to the sink node | MW |
| `DCLink().wheeling_cost_from` | Transmission cost applied to the flow in the forward direction | $/MWh |
| `DCLink().wheeling_cost_to` | Transmission cost applied to the flow in the reverse direction | $/MWh |

---

## DC Line

| Data | Description | Unit |
| :--- | :--- | :---: |
| `DCLine().code` | Unique identifier for the DC line | --- |
| `DCLine().state` | Operational state of the DC line | --- |
| `DCLine().resistance` | Resistance of the DC line | % |
| `DCLine().reactance` | Reactance (if applicable/modeled) | % |
| `DCLine().capacity` | Maximum power flow capacity | MW |
| `DCLine().emergency_capacity` | Maximum emergency capacity | MW |
| `DCLine().DLR_factor` | Dynamic Line Rating factor | pu |
| `DCLine().monitored` | Monitoring flag | --- |
| `DCLine().monitored_contingencies` | Contingency monitoring flag | --- |
| `DCLine().is_dc` | Flag explicitly marking DC behavior | --- |
| `DCLine().international_cost_from` | Export/Wheeling cost from source | $/MWh |
| `DCLine().international_cost_to` | Import/Wheeling cost to sink | $/MWh |

---

## Demand

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Demand().code` | Unique identifier for the demand | --- |
| `Demand().is_elastic` | Flag indicating if the demand is price-sensitive | --- |
| `Demand().inelastic_hour` | Fixed load profile defined hourly | MW |
| `Demand().inelastic_block` | Fixed load profile defined by blocks | GWh |
| `Demand().is_flexible` | Flag indicating if demand can be shifted or adjusted | --- |
| `Demand().max_increase` | Maximum allowable load increase (for flexible demand) | pu |
| `Demand().max_decrease` | Maximum allowable load decrease (demand response) | pu |
| `Demand().curtailment_cost` | Penalty cost for load curtailment (Value of Lost Load) | $/MWh |
| `Demand().max_curtailment` | Maximum proportion of the load that can be curtailed | pu |
| `Demand().variable_block_duration` | Duration of the variable load block | h |

---

## Demand Segment

| Data | Description | Unit |
| :--- | :--- | :---: |
| `DemandSegment().hour` | Hourly demand value for the segment | MW |
| `DemandSegment().block` | Energy demand value for the block segment | GWh |
| `DemandSegment().hour_price` | Price associated with the hourly segment | $/MWh |
| `DemandSegment().block_price` | Price associated with the block segment | $/MWh |

---

## Energy Chain Demand

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainDemand().code` | Identifier for demand in the energy chain model | --- |

---

## Energy Chain Demand Segment

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainDemandSegment().code` | Identifier for the demand segment | --- |
| `EnergyChainDemandSegment().hour` | Hourly demand volume | MW |
| `EnergyChainDemandSegment().block` | Block demand volume | GWh |
| `EnergyChainDemandSegment().cost` | Cost associated with the segment | $/MWh |
| `EnergyChainDemandSegment().hour_price` | Hourly price for the segment | $/MWh |

---

## Energy Chain Fixed Converter

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainFixedConverter().code` | Identifier for the fixed converter | --- |
| `EnergyChainFixedConverter().state` | Operational state | --- |
| `EnergyChainFixedConverter().capacity_factor` | Efficiency or capacity conversion factor | pu |

---

## Energy Chain Fixed Converter Commodity

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainFixedConverterCommodity().type` | Type of commodity converted | --- |
| `EnergyChainFixedConverterCommodity().node_type` | Type of node associated with the commodity | --- |

---

## Energy Chain Network

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainNetwork().code` | Identifier for the energy chain network | --- |

---

## Energy Chain Node

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainNode().code` | Identifier for the energy chain node | --- |

---

## Energy Chain Process

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainProcess().code` | Identifier for the process within the chain | --- |

---

## Energy Chain Producer

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainProducer().code` | Identifier for the producer | --- |

---

## Energy Chain Storage

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainStorage().code` | Identifier for the storage facility | --- |

---

## Energy Chain Transport

| Data | Description | Unit |
| :--- | :--- | :---: |
| `EnergyChainTransport().code` | Identifier for the transport link | --- |

---

## Expansion Capacity

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ExpansionCapacity().code` | Identifier for the expansion capacity project | --- |

---

## Expansion Constraint

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ExpansionConstraint().code` | Identifier for the expansion constraint | --- |

---

## Expansion Decision

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ExpansionDecision().code` | Identifier for the expansion decision variable | --- |

---

## Expansion Project

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ExpansionProject().code` | Unique identifier for the expansion project | --- |
| `ExpansionProject().om_cost` | Fixed Operation & Maintenance cost per year | $/kWyear |
| `ExpansionProject().integration_cost` | Cost to integrate the project into the grid | $/kW |
| `ExpansionProject().invest_cost_unit` | Investment cost per unit of capacity | --- |
| `ExpansionProject().invest_cost` | Total investment cost | --- |
| `ExpansionProject().annualized_invest_cost` | Annualized investment cost | M$ |

---

## Flexible Demand

| Data | Description | Unit |
| :--- | :--- | :---: |
| `FlexibleDemand().code` | Unique identifier for the flexible demand | --- |
| `FlexibleDemand().is_elastic` | Elasticity flag | --- |
| `FlexibleDemand().is_enabled` | Activation flag | --- |
| `FlexibleDemand().inelastic_hour` | Baseline inelastic load (hourly) | MW |
| `FlexibleDemand().inelastic_block` | Baseline inelastic load (block) | GWh |
| `FlexibleDemand().is_flexible` | Flexibility capability flag | --- |
| `FlexibleDemand().max_increase` | Maximum allowed load increase | pu |
| `FlexibleDemand().max_decrease` | Maximum allowed load decrease | pu |
| `FlexibleDemand().curtailment_cost` | Cost of curtailed demand | $/MWh |
| `FlexibleDemand().max_curtailment` | Limit on curtailment | pu |
| `FlexibleDemand().variable_block_duration` | Duration of variable blocks | h |

---

## Flow Controller

| Data | Description | Unit |
| :--- | :--- | :---: |
| `FlowController().code` | Identifier for the flow controller device | --- |

---

## Fuel

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Fuel().code` | Unique identifier for the fuel type | --- |
| `Fuel().cost` | Unit cost of the fuel | $/gal |
| `Fuel().emission_factor` | CO2 emission rate per MWh | tCO2/MWh |
| `Fuel().min_consumption` | Minimum mandatory fuel consumption | kgal |
| `Fuel().max_consumption` | Maximum fuel consumption limit | kgal |
| `Fuel().availability` | Total available fuel amount | kgal |

---

## Fuel Consumption

| Data | Description | Unit |
| :--- | :--- | :---: |
| `FuelConsumption().code` | Identifier for fuel consumption record | --- |

---

## Fuel Contract

| Data | Description | Unit |
| :--- | :--- | :---: |
| `FuelContract().code` | Identifier for the fuel contract | --- |
| `FuelContract().cost` | Cost per unit of contract | $/kUC |
| `FuelContract().amount` | Total contracted amount | kUC |
| `FuelContract().cotake_or_payde` | Take-or-pay amount (typo in source: likely take_or_pay) | kUC |
| `FuelContract().take_or_pay_cost` | Cost associated with take-or-pay contracts | $/kUC |
| `FuelContract().extra_take_or_pay` | Cost for exceeding take-or-pay limits | $/kUC |
| `FuelContract().withdrawal_rate` | Rate of fuel withdrawal | gal/h |

---

## Fuel Reservoir

| Data | Description | Unit |
| :--- | :--- | :---: |
| `FuelReservoir().code` | Identifier for fuel storage | --- |
| `FuelReservoir().max_injection` | Maximum fuel injection rate | kgal |
| `FuelReservoir().max_injection_constraint` | Constraint on maximum injection | kgal |

---

## Gas Emission

| Data | Description | Unit |
| :--- | :--- | :---: |
| `GasEmission().code` | Identifier for the emission type | --- |
| `GasEmission().cost` | Cost associated with emissions (tax/penalty) | $/MWh |

---

## Gas Node

| Data | Description | Unit |
| :--- | :--- | :---: |
| `GasNode().code` | Identifier for the gas node | --- |
| `GasNode().production_cost_constraint` | Production cost limit or constraint at the node | $/UV |

---

## Generation Constraint

| Data | Description | Unit |
| :--- | :--- | :---: |
| `GenerationConstraint().code` | Identifier for the constraint | --- |
| `GenerationConstraint().data` | Value of the constraint | MW |
| `GenerationConstraint().penalty` | Penalty factor for violation | --- |
| `GenerationConstraint().sign` | Mathematical sign of the constraint | --- |

---

## Generic

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Generic().code` | Generic identifier | --- |

---

## Generic Constraint

| Data | Description | Unit |
| :--- | :--- | :---: |
| `GenericConstraint().code` | Identifier for generic constraint | --- |

---

## Generic Constraint Interpolation

| Data | Description | Unit |
| :--- | :--- | :---: |
| `GenericConstraintInterpolation().code` | Identifier for interpolation data | --- |

---

## Generic Variable

| Data | Description | Unit |
| :--- | :--- | :---: |
| `GenericVariable().code` | Identifier for generic variable | --- |

---

## Hydro

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Hydro().code` | Unique identifier for the hydro plant | --- |
| `Hydro().state` | Operational state | --- |
| `Hydro().units` | Number of generating units | --- |
| `Hydro().system` | System or area the hydro plant belongs to | --- |
| `Hydro().max_generation` | Installed generation capacity | MW |
| `Hydro().max_generation_available` | Available generation capacity (considering outages) | MW |
| `Hydro().forced_outage_rate` | Probability of forced outage | % |
| `Hydro().historical_outage_factor` | Historical outage factor based on past data | % |
| `Hydro().min_storage` | Physical minimum reservoir volume | hm3 |
| `Hydro().max_storage` | Physical maximum reservoir volume | hm3 |
| `Hydro().min_turbining_outflow` | Minimum water flow through turbines | m3/s |
| `Hydro().max_turbining_outflow` | Maximum water flow capacity through turbines | m3/s |
| `Hydro().om_cost` | Variable O&M cost | $/MWh |
| `Hydro().irrigation` | Water outflow deducted for irrigation | m3/s |
| `Hydro().min_total_outflow_modification` | Adjustment to minimum outflow requirement | m3/s |
| `Hydro().target_storage_tolerance` | Tolerance band for meeting target storage | % |
| `Hydro().disconsider_in_stored_and_inflow_energy`| Exclude from system energy aggregation | --- |
| `Hydro().mean_production_coefficient` | Average productivity factor | MW/(m3/s) |
| `Hydro().loss_factor` | Hydraulic loss factor | pu |
| `Hydro().min_total_outflow` | Minimum mandatory total river flow | m3/s |
| `Hydro().min_total_outflow_unit_violation_cost`| Penalty cost for violating min outflow | k$/m3/s |
| `Hydro().min_total_outflow_violation_type` | Type of violation penalty (linear/quadratic) | --- |
| `Hydro().max_total_outflow` | Maximum allowed total river flow | m3/s |
| `Hydro().max_total_outflow_unit_violation_cost`| Penalty cost for violating max outflow | k$/m3/s |
| `Hydro().max_total_outflow_violation_type` | Type of violation penalty | --- |
| `Hydro().min_operative_storage` | Minimum operative storage level | hm3 |
| `Hydro().min_operative_storage_unit_violation_cost`| Penalty for violating min operative storage | k$/hm3 |
| `Hydro().min_operative_storage_violation_type` | Type of violation penalty | --- |
| `Hydro().max_operative_storage` | Maximum operative storage level | hm3 |
| `Hydro().max_operative_storage_unit_violation_cost`| Penalty for violating max operative storage | k$/hm3 |
| `Hydro().max_operative_storage_violation_type` | Type of violation penalty | --- |
| `Hydro().flood_control` | Volume reserved for flood control | hm3 |
| `Hydro().alert_storage` | Storage level triggering alert status | hm3 |
| `Hydro().alert_storage_unit_violation_cost` | Cost associated with alert storage violation | k$/hm3 |
| `Hydro().alert_storage_violation_type` | Type of violation penalty | --- |
| `Hydro().min_spillage` | Minimum required spillage | m3/s |
| `Hydro().min_spillage_unit_violation_cost` | Penalty for violating min spillage | k$/m3/s |
| `Hydro().min_spillage_violation_type` | Type of violation penalty | --- |
| `Hydro().max_spillage` | Maximum allowed spillage | m3/s |
| `Hydro().max_spillage_unit_violation_cost` | Penalty for violating max spillage | k$/m3/s |
| `Hydro().max_spillage_violation_type` | Type of violation penalty | --- |
| `Hydro().min_bio_spillage` | Minimum spillage for environmental/biological reasons | % |
| `Hydro().min_bio_spillage_unit_violation_cost` | Penalty for bio spillage violation | k$/hm3 |
| `Hydro().min_bio_spillage_violation_type` | Type of violation penalty | --- |
| `Hydro().target_storage` | Target storage level to be reached | hm3 |
| `Hydro().max_turbining` | Maximum turbined flow | m3/s |
| `Hydro().max_turbining_unit_violation_cost` | Penalty for violating max turbining | k$/m3/s |
| `Hydro().max_turbining_violation_type` | Type of violation penalty | --- |
| `Hydro().min_turbining_unit_violation_cost` | Penalty for violating min turbining | k$/m3/s |
| `Hydro().min_turbining_violation_type` | Type of violation penalty | --- |
| `Hydro().spinning_reserve` | Spinning reserve capability | % |
| `Hydro().max_reserve` | Maximum reserve capacity | MW |
| `Hydro().discharge_ramp_up` | Ramp up rate for water discharge | m3/s/min |
| `Hydro().discharge_ramp_down` | Ramp down rate for water discharge | m3/s/min |
| `Hydro().ramp_up` | Ramp up rate for generation | MW/min |
| `Hydro().ramp_down` | Ramp down rate for generation | MW/min |
| `Hydro().hourly_maintenance` | Scheduled maintenance factor | % |
| `Hydro().hourly_unavailability` | Unavailability factor | % |
| `Hydro().regulation_factor` | Regulation capability factor | pu |
| `Hydro().turbining_loss_factor` | Loss factor associated with turbining | pu |
| `Hydro().spillage_loss_factor` | Loss factor associated with spillage | pu |

---

## Hydro (tables)

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Hydro().storage_x_elevation__storage_1` | Storage volume point 1 for elevation curve | hm3 |
| `Hydro().storage_x_elevation__storage_2` | Storage volume point 2 | hm3 |
| `Hydro().storage_x_elevation__storage_3` | Storage volume point 3 | hm3 |
| `Hydro().storage_x_elevation__storage_4` | Storage volume point 4 | hm3 |
| `Hydro().storage_x_elevation__storage_5` | Storage volume point 5 | hm3 |
| `Hydro().storage_x_elevation__elevation_1` | Elevation point 1 corresponding to storage 1 | masl |
| `Hydro().storage_x_elevation__elevation_2` | Elevation point 2 | masl |
| `Hydro().storage_x_elevation__elevation_3` | Elevation point 3 | masl |
| `Hydro().storage_x_elevation__elevation_4` | Elevation point 4 | masl |
| `Hydro().storage_x_elevation__elevation_5` | Elevation point 5 | masl |

---

## Hydro Gauging Station

| Data | Description | Unit |
| :--- | :--- | :---: |
| `HydroGaugingStation().code` | Identifier for the gauging station | --- |
| `HydroGaugingStation().inflow` | Natural inflow at the station | m3/s |
| `HydroGaugingStation().forward` | Forward flow reading | m3/s |
| `HydroGaugingStation().backward` | Backward flow reading | m3/s |
| `HydroGaugingStation().hour_inflow_historical_scenarios_nodata` | Flag for missing historical scenario data | --- |
| `HydroGaugingStation().hour_inflow_historical_scenarios` | Historical inflow scenarios | m3/s |
| `HydroGaugingStation().hour_inflow` | Hourly inflow data | m3/s |

---

## Hydro Generator

| Data | Description | Unit |
| :--- | :--- | :---: |
| `HydroGenerator().code` | Identifier for specific hydro generator units | --- |

---

## Interconnection

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Interconnection().code` | Identifier for the interconnection | --- |
| `Interconnection().state` | Operational state | --- |
| `Interconnection().capacity_from` | Capacity in 'from' direction | MW |
| `Interconnection().capacity_to` | Capacity in 'to' direction | MW |
| `Interconnection().cost_from` | Cost/toll in 'from' direction | $/MWh |
| `Interconnection().cost_to` | Cost/toll in 'to' direction | $/MWh |

---

## Interconnection Sum

| Data | Description | Unit |
| :--- | :--- | :---: |
| `InterconnectionSum().code` | Identifier for sum constraint | --- |
| `InterconnectionSum().LB` | Lower bound limit | MW |
| `InterconnectionSum().UB` | Upper bound limit | MW |

---

## Load

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Load().code` | Identifier for the load | --- |
| `Load().bus` | Bus where the load is connected | --- |
| `Load().hour_bus` | Hourly load value at the bus | MW |

---

## Maintenance

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Maintenance().code` | Identifier for maintenance schedule | --- |
| `Maintenance().data` | Maintenance data (percentage) | % |

---

## Maintenance Solicitation

| Data | Description | Unit |
| :--- | :--- | :---: |
| `MaintenanceSolicitation().code` | Identifier for maintenance request | --- |
| `MaintenanceSolicitation().min_date_day` | Earliest start day | --- |
| `MaintenanceSolicitation().min_date_month` | Earliest start month | --- |
| `MaintenanceSolicitation().min_date_year` | Earliest start year | --- |
| `MaintenanceSolicitation().max_date_day` | Latest end day | --- |
| `MaintenanceSolicitation().max_date_month` | Latest end month | --- |
| `MaintenanceSolicitation().max_date_year` | Latest end year | --- |
| `MaintenanceSolicitation().duration` | Duration of maintenance | --- |
| `MaintenanceSolicitation().preference_date_day` | Preferred day | --- |
| `MaintenanceSolicitation().preference_date_month` | Preferred month | --- |
| `MaintenanceSolicitation().preference_date_year` | Preferred year | --- |

---

## OptPrice Agent

| Data | Description | Unit |
| :--- | :--- | :---: |
| `OptPriceAgent().code` | Identifier for optimization price agent | --- |

---

## OptPrice Contract

| Data | Description | Unit |
| :--- | :--- | :---: |
| `OptPriceContract().code` | Identifier for optimization price contract | --- |

---

## OptPrice Load

| Data | Description | Unit |
| :--- | :--- | :---: |
| `OptPriceLoad().code` | Identifier for optimization price load | --- |

---

## OptPrice Plant

| Data | Description | Unit |
| :--- | :--- | :---: |
| `OptPricePlant().code` | Identifier for optimization price plant | --- |

---

## OptPrice System

| Data | Description | Unit |
| :--- | :--- | :---: |
| `OptPriceSystem().code` | Identifier for optimization price system | --- |

---

## Phase Shifter

| Data | Description | Unit |
| :--- | :--- | :---: |
| `PhaseShifter().code` | Identifier for Phase Shifter Transformer (PST) | --- |
| `PhaseShifter().state` | Operational state | --- |
| `PhaseShifter().decommissioned` | Decommissioning status | --- |

---

## Power Injection

| Data | Description | Unit |
| :--- | :--- | :---: |
| `PowerInjection().code` | Identifier for power injection | --- |
| `PowerInjection().hour_capacity` | Hourly injection capacity | MW |
| `PowerInjection().hour_price` | Hourly injection price | $/MWh |
| `PowerInjection().capacity` | Fixed capacity | MW |
| `PowerInjection().price` | Fixed price | $/MWh |

---

## Renewable

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Renewable().code` | Unique identifier for renewable plant | --- |
| `Renewable().state` | Operational state | --- |
| `Renewable().units` | Number of units | --- |
| `Renewable().tech_type` | Technology type | --- |
| `Renewable().capacity` | Installed capacity | MW |
| `Renewable().om_cost` | Variable O&M cost | $/MWh |
| `Renewable().hour_scenarios` | Hourly generation profile scenarios | pu |
| `Renewable().block_scenarios` | Block generation profile scenarios | pu |
| `Renewable().operation_factor` | Availability factor applied to capacity | pu |
| `Renewable().max_reserve` | Maximum reserve capacity | MW |
| `Renewable().bid_price` | Bid price for energy | $/MWh |
| `Renewable().forced_outage_rate` | Probability of forced outage | % |
| `Renewable().hourly_maintenance` | Scheduled maintenance factor | % |
| `Renewable().hourly_unavailability` | Unavailability factor | % |
| `Renewable().curtailment_cost` | Cost/penalty for curtailment | $/MWh |

---

## Renewable Gauging Station

| Data | Description | Unit |
| :--- | :--- | :---: |
| `RenewableGaugingStation().code` | Identifier for renewable gauging station | --- |
| `RenewableGaugingStation().hour_scenarios` | Hourly data scenarios | pu |
| `RenewableGaugingStation().block_scenarios` | Block data scenarios | pu |
| `RenewableGaugingStation().hour_historical_scenarios` | Historical hourly data scenarios | pu |

---

## Renewable Generator

| Data | Description | Unit |
| :--- | :--- | :---: |
| `RenewableGenerator().code` | Identifier for specific renewable generator unit | --- |

---

## Reserve Generation Constraint

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ReserveGenerationConstraint().data` | Reserve requirement amount | MW |
| `ReserveGenerationConstraint().penalty` | Penalty for not meeting reserve | --- |
| `ReserveGenerationConstraint().sign` | Constraint sign | --- |

---

## Reservoir Set

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ReservoirSet().code` | Identifier for a set of reservoirs | --- |
| `ReservoirSet().security_energy` | Minimum energy for security | MWh |
| `ReservoirSet().flood_control_energy` | Energy volume reserved for flood control | MWh |
| `ReservoirSet().alert_energy` | Energy level triggering alert | MWh |

---

## Series Capacitor

| Data | Description | Unit |
| :--- | :--- | :---: |
| `SeriesCapacitor().code` | Identifier for Series Capacitor | --- |
| `SeriesCapacitor().security_energy` | Security energy limit | MWh |
| `SeriesCapacitor().flood_control_energy` | Flood control limit | MWh |
| `SeriesCapacitor().alert_energy` | Alert limit | MWh |

---

## Study

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Study().deficit_segment_1` | Deficit depth for segment 1 | % |
| `Study().deficit_segment_2` | Deficit depth for segment 2 | % |
| `Study().deficit_segment_3` | Deficit depth for segment 3 | % |
| `Study().deficit_segment_4` | Deficit depth for segment 4 | % |
| `Study().deficit_cost_1` | Cost of deficit for segment 1 | $/MWh |
| `Study().deficit_cost_2` | Cost of deficit for segment 2 | $/MWh |
| `Study().deficit_cost_3` | Cost of deficit for segment 3 | $/MWh |
| `Study().deficit_cost_4` | Cost of deficit for segment 4 | $/MWh |

---

## System

| Data | Description | Unit |
| :--- | :--- | :---: |
| `System().code` | Identifier for the power system | --- |
| `System().load_level_length` | Duration of load levels | --- |
| `System().hour_block_map` | Mapping between hours and blocks | --- |
| `System().sensitivity` | Sensitivity factors | --- |
| `System().carbon_credit_cost` | Cost of carbon credits | $/tCO2 |
| `System().risk_aversion_curve` | Curve defining risk aversion parameters | % |

---

## Thermal

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Thermal().code` | Unique identifier for thermal plant | --- |
| `Thermal().state` | Operational state | --- |
| `Thermal().units` | Number of units | --- |
| `Thermal().system` | System the plant belongs to | --- |
| `Thermal().min_generation` | Minimum stable generation (must-run) | MW |
| `Thermal().min_generation_available` | Minimum available generation | MW |
| `Thermal().min_generation_constraint` | Constraint on minimum generation | MW |
| `Thermal().max_generation` | Maximum generation capacity | MW |
| `Thermal().max_generation_available` | Maximum available capacity | MW |
| `Thermal().forced_outage_rate` | Forced outage probability | % |
| `Thermal().historical_outage_factor` | Historical outage factor | % |
| `Thermal().startup_cost` | Cost to start the unit | k$ |
| `Thermal().startup_cost_constraint` | Constraint on startup cost | k$ |
| `Thermal().om_cost` | Variable O&M cost | $/MWh |
| `Thermal().specific_consumption_segment_1` | Fuel consumption rate for segment 1 | gal/MWh |
| `Thermal().specific_consumption_segment_2` | Fuel consumption rate for segment 2 | gal/MWh |
| `Thermal().specific_consumption_segment_3` | Fuel consumption rate for segment 3 | gal/MWh |
| `Thermal().fuel_transportation_cost` | Cost to transport fuel to plant | $/gal |
| `Thermal().operation_mode` | Operation mode | --- |
| `Thermal().emission_coefficient` | Emission factor | pu |
| `Thermal().ramp_up` | Generation ramp up rate | MW/min |
| `Thermal().ramp_down` | Generation ramp down rate | MW/min |
| `Thermal().min_uptime` | Minimum uptime duration | hour |
| `Thermal().min_downtime` | Minimum downtime duration | hour |
| `Thermal().max_startups` | Maximum number of startups allowed | --- |
| `Thermal().max_shutdowns` | Maximum number of shutdowns allowed | --- |
| `Thermal().shutdown_cost` | Cost to shut down the unit | k$ |
| `Thermal().alternative_fuel` | Flag for alternative fuel capability | --- |
| `Thermal().spinning_reserve` | Spinning reserve capability | % |
| `Thermal().max_reserve` | Maximum reserve capacity | MW |
| `Thermal().bid_price` | Bid price for energy | $/MWh |
| `Thermal().commitment_type` | Unit commitment type | --- |
| `Thermal().hourly_maintenance` | Scheduled maintenance factor | % |
| `Thermal().hourly_unavailability` | Unavailability factor | % |

---

## Thermal Combined Cycle

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ThermalCombinedCycle().code` | Identifier for Combined Cycle plant | --- |

---

## Thermal Generator

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ThermalGenerator().code` | Identifier for specific thermal generator unit | --- |

---

## Three Winding Transformer

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ThreeWindingTransformer().code` | Identifier for 3-winding transformer | --- |

---

## Transformer

| Data | Description | Unit |
| :--- | :--- | :---: |
| `Transformer().code` | Identifier for transformer | --- |

---

## Water Way

| Data | Description | Unit |
| :--- | :--- | :---: |
| `WaterWay().code` | Identifier for water way (channel/river section) | --- |