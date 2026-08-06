# FlexibleDemand

|                 Data                  |                       Description                        | Unit  |
| :------------------------------------ | :------------------------------------------------------- | :---: |
| `FlexibleDemand():supplied()`         | Flexible load shifted to each block and supplied         |  GWh  |
| `FlexibleDemand():curtailment()`      | Flexible load shifted to each block, but not supplied    |  GWh  |
| `FlexibleDemand():maximum()`          | Maximum flexible load that can be shifted to each block  |  GWh  |
| `FlexibleDemand():minimum()`          | Minimum flexible load that must be shifted to each block |  GWh  |
| `FlexibleDemand():energy()`           | Reference flexible load to calculate the shifting limits |  GWh  |
| `FlexibleDemand():curtailment_cost()` | Flexible load curtailment cost                           |  k$   |
