# FlexibleDemand

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
