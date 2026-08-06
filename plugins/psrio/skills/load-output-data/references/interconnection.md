# Interconnection

|                  Data                  |                                                 Description                                                  | Unit  |
| :------------------------------------- | :----------------------------------------------------------------------------------------------------------- | :---: |
| `Interconnection():flow()`             | Interconnection flow between systems                                                                         |  GWh  |
| `Interconnection():marginal_cost()`    | Change in operating cost with respect to an infinitesimal change in the interconnection capacity (limit).    | k$/MW |
| `Interconnection():capacity_from_to()` | Interconnection capacity FROM->TO                                                                            |  MW   |
| `Interconnection():income()`           | Interconnection income given by the product of the interconnection flow and the reduced cost of the variable |  k$   |
| `Interconnection():cost_from_to()`     | Interconnection cost FROM->TO between systems                                                                | $/MWh |
| `Interconnection():total_cost()`       | Total interconnection cost between systems                                                                   |  k$   |
| `Interconnection():losses()`           | Interconnection losses                                                                                       |  MW   |
| `Interconnection():capacity_to_from()` | Interconnection capacity TO->FROM                                                                            |  MW   |
| `Interconnection():cost_to_from()`     | Interconnection cost TO->FROM between systems                                                                | $/MWh |
| `Interconnection():joint_reserve()`    | Interconnection joint reserve                                                                                |  MW   |
| `Interconnection():max_flow_limit()`   | Maximum interconnection flow                                                                                 |  MW   |
| `Interconnection():min_reverse_flow()` | Minimum interconnection flow in the opposite direction                                                       |  MW   |
