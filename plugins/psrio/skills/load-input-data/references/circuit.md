# Circuit

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
