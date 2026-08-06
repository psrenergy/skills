# ReservoirSet

|                          Data                          |                                    Description                                    | Unit  |
| :----------------------------------------------------- | :-------------------------------------------------------------------------------- | :---: |
| `ReservoirSet():security_energy_violation()`           | Violation of security energy constraint by reservoir set                          |  GWh  |
| `ReservoirSet():alert_energy_violation()`              | Violation of alert energy constraint by reservoir set                             |  GWh  |
| `ReservoirSet():flood_control_energy_violation()`      | Violation of flood control energy constraint by reservoir set                     |  GWh  |
| `ReservoirSet():stored_energy()`                       | Stored energy in a set of reservoirs                                              |  GWh  |
| `ReservoirSet():load("eneale")`                        | Alert energy by reservoir set                                                     |  GWh  |
| `ReservoirSet():load("eneesp")`                        | Flood control by reservoir set                                                    |  GWh  |
| `ReservoirSet():load("enemin")`                        | Security energy by reservoir set                                                  |  GWh  |
| `ReservoirSet():security_energy_violation_cost()`      | Violation cost of security energy by reservoir set                                |  k$   |
| `ReservoirSet():alert_energy_violation_cost()`         | Violation cost of alert energy by reservoir set                                   |  k$   |
| `ReservoirSet():flood_control_energy_violation_cost()` | Violation cost of flood control energy by reservoir set                           |  k$   |
| `ReservoirSet():energy_perc()`                         | Stored energy in a set of reservoirs as a percentage of the maximum stored energy |   %   |
