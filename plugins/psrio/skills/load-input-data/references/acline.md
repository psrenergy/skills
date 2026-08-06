# ACLine

<!-- Renamed from ACline() to ACLine() for consistency with load-output-data and
     with every other multi-word collection (CircuitsSum, DCLine, EnergyChainDemand).
     Lua is case-sensitive — confirm against the PSRIO API. -->

| Data | Description | Unit |
| :--- | :--- | :---: |
| `ACLine().code` | Unique identifier for the AC transmission line | --- |
| `ACLine().state` | Operational state of the line | --- |
| `ACLine().resistance` | Resistance of the transmission line | % |
| `ACLine().reactance` | Reactance of the transmission line | % |
| `ACLine().capacity` | Maximum power flow capacity of the line under normal conditions | MW |
| `ACLine().emergency_capacity` | Maximum power flow capacity of the line under emergency conditions | MW |
| `ACLine().DLR_factor` | Dynamic Line Rating factor applied to the nominal capacity | pu |
| `ACLine().monitored` | Flag indicating if the line flows are monitored during the optimization | --- |
| `ACLine().monitored_contingencies` | Flag indicating if the line is monitored under contingency scenarios | --- |
| `ACLine().is_dc` | Flag indicating if the line is modeled as a DC line within AC power flow | --- |
| `ACLine().international_cost_from` | Wheeling charge or export cost applied to flow leaving the 'from' bus | $/MWh |
| `ACLine().international_cost_to` | Wheeling charge or import cost applied to flow arriving at the 'to' bus | $/MWh |

---
