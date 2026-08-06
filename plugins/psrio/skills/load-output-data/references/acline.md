# ACLine

|              Data               |                                                  Description                                                   | Unit  |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------- | :---: |
| `ACLine():cost()`               | AC transmission line cost                                                                                      |  k$   |
| `ACLine():flow()`               | AC transmission line flow                                                                                      |  MW   |
| `ACLine():capacity_marg_cost()` | Change in operating cost with respect to an infinitesimal change in the AC transmission line capacity (limit). | k$/MW |
| `ACLine():losses()`             | AC transmission line quadratic losses approximation, obtained through linearizations                           |  MW   |
| `ACLine():quadratic_losses()`   | AC transmission line theoretical quadratic losses                                                              |  MW   |
| `ACLine():losses_mismatch()`    | AC transmission lines losses error                                                                             |  MW   |
