# Renewable

|                   Data                   |                                                  Description                                                  | Unit  |
| :--------------------------------------- | :------------------------------------------------------------------------------------------------------------ | :---: |
| `Renewable():generation()`               | Renewable source generation                                                                                   |  GWh  |
| `Renewable():bus_income()`               | Spot revenue of renewable source generation based on the marginal cost of the bus where the plant is located. |  k$   |
| `Renewable():capacity_marg_cost()`       | Change in operating cost with respect to an infinitesimal change in the renewable installed capacity.         | k$/MW |
| `Renewable():nominal_capacity()`         | Renewable sources capacity.                                                                                   |  MW   |
| `Renewable():system_income()`            | Spot revenue of renewable source generation based on the system marginal cost.                                |  k$   |
| `Renewable():curtailment()`              | Renewable generation spillage                                                                                 |  GWh  |
| `Renewable():scenario()`                 | Renewable associated station scenario generation                                                              |  pu   |
| `Renewable():load("cogoem")`             | Operation and maintenance cost by renewable plant                                                             |  k$   |
| `Renewable():dispatch_factor()`          | Percentage of renewable utilization                                                                           |   %   |
| `Renewable():om_unitary_cost()`          | Operation and maintenance unitary cost by renewable plant                                                     | $/MWh |
| `Renewable():available_capacity()`       | Renewable available capacity scenario                                                                         |  MW   |
| `Renewable():joint_reserve()`            | Joint reserve for renewable plants                                                                            |  MW   |
| `Renewable():joint_reserve_nexc()`       | Renewable joint reserve that can be shared between non-exclusive requirements                                 |  MW   |
| `Renewable():joint_reserve_cost()`       | Renewable joint reserve cost                                                                                  |  k$   |
| `Renewable():max_joint_reserve()`        | Renewable maximum joint reserve                                                                               |  MW   |
| `Renewable():joint_reserve_price()`      | Renewable joint reserve price                                                                                 | $/MWh |
| `Renewable():non_reserved_curtailment()` | Renewable generation spillage not allocated to reserve                                                        |  GWh  |
