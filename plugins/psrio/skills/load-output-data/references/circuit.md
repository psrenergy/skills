# Circuit

|               Data                |                                                           Description                                                            | Unit  |
| :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- | :---: |
| `Circuit():flow()`                | AC Circuit flow                                                                                                                  |  MW   |
| `Circuit():capacity_marg_cost()`  | Change in operating cost with respect to a infinitesimal change in the AC circuit capacity (limit).                              | k$/MW |
| `Circuit():max_flow()`            | Maximum AC circuit flow                                                                                                          |  MW   |
| `Circuit():income()`              | AC Circuit ingress given by the circuit flow multiplier by the difference between load marginal cost of end buses of the circuit |  k$   |
| `Circuit():losses()`              | AC circuit quadratic losses approximation, obtained through linearizations                                                       |  MW   |
| `Circuit():min_flow()`            | Minimum flow of the AC circuit in the opposite direction                                                                         |  MW   |
| `Circuit():operative_status()`    | If AC circuit is operating, el indicator=1; if in maintenance, 0.                                                                |  0/1  |
| `Circuit():quadratic_losses()`    | AC circuit theoretical quadratic losses                                                                                          |  MW   |
| `Circuit():loading_factor()`      | AC Circuit flow as a percentage of the maximum capacity                                                                          |   %   |
| `Circuit():overload()`            | Circuit overload                                                                                                                 |  MW   |
| `Circuit():overload_penalty()`    | Circuit overload penalty                                                                                                         |  k$   |
| `Circuit():dynamic_line_rating()` | Dynamic line rating, in p.u. of the nominal capacity                                                                             |  pu   |
| `Circuit():joint_reserve()`       | Circuit joint reserve                                                                                                            |  MW   |
| `Circuit():losses_mismatch()`     | AC circuit losses error                                                                                                          |  MW   |
| `Circuit():max_flow_limit()`      | Maximum flow of the AC circuit                                                                                                   |  MW   |
| `Circuit():min_reverse_flow()`    | Minimum flow of the AC circuit in the opposite direction                                                                         |  MW   |
