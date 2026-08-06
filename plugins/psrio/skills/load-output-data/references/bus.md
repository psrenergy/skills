# Bus

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
