# Transformer

|                 Data                 |                                             Description                                              | Unit  |
| :----------------------------------- | :--------------------------------------------------------------------------------------------------- | :---: |
| `Transformer():cost()`               | Transformers transmission cost                                                                       |  k$   |
| `Transformer():flow()`               | Transformer flow                                                                                     |  MW   |
| `Transformer():capacity_marg_cost()` | Change in operating cost with respect to a infinitesimal change in the transformer capacity (limit). | k$/MW |
| `Transformer():losses()`             | Transformers quadratic losses approximation, obtained through linearizations                         |  MW   |
| `Transformer():quadratic_losses()`   | Transformers theoretical quadratic losses                                                            |  MW   |
| `Transformer():losses_mismatch()`    | Transformer losses error                                                                             |  MW   |
