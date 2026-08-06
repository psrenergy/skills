# FuelReservoir

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
