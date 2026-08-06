# Thermal

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
