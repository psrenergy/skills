# Demand

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
