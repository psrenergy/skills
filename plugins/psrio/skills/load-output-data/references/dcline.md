# DCLine

|             Data              |                                             Description                                             | Unit  |
| :---------------------------- | :-------------------------------------------------------------------------------------------------- | :---: |
| `DCLine():max_flow()`         | Maximum DC circuit flow                                                                             |  MW   |
| `DCLine():circuit_flag()`     | If DC circuit is operating, el indicator=1; if in maintenance, 0.                                   |  0/1  |
| `DCLine():flow()`             | DC Circuit flow                                                                                     |  MW   |
| `DCLine():marginal_cost()`    | Change in operating cost with respect to a infinitesimal change in the DC circuit capacity (limit). | k$/MW |
| `DCLine():losses()`           | DC Circuit energy losses                                                                            |  MW   |
| `DCLine():quadratic_losses()` | Quadratic losses by circuits DC                                                                     |  MW   |
| `DCLine():loading()`          | DC Circuit flow as a percentage of the maximum capacity                                             |   %   |
| `DCLine():losses_mismatch()`  | DC circuit losses error                                                                             |  MW   |
