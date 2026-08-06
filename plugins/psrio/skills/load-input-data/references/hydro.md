# Hydro

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
