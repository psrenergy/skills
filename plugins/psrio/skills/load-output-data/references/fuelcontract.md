# FuelContract

|                      Data                       |                                                   Description                                                    |  Unit   |
| :---------------------------------------------- | :--------------------------------------------------------------------------------------------------------------- | :-----: |
| `FuelContract():daily_offtake_violation()`      | Fuel contract minimum daily offtake rate violation                                                               |   UC    |
| `FuelContract():daily_offtake_violation_cost()` | Fuel contract minimum daily offtake rate violation cost                                                          |   k$    |
| `FuelContract():capacity()`                     | Maximum fuel contract capacity                                                                                   |   kUC   |
| `FuelContract():max_offtake()`                  | Maximum fuel contract offtake                                                                                    |  UC/h   |
| `FuelContract():remaining()`                    | Fuel contract amount (Take-or-Pay and additional components) that can still be consumed at the end of the period |   kUC   |
| `FuelContract():unconsumed()`                   | Not consumed fuel from the total contract amount (Take-or-Pay and additional components), that will be discarded |   kUC   |
| `FuelContract():consumed()`                     | Fuel contract offtake during the period                                                                          |   kUC   |
| `FuelContract():marginal_cost()`                | Change in operating cost with respect to an infinitesimal change in the fuel contract capacity                   |  $/UC   |
| `FuelContract():top_amount()`                   | Take or Pay contract value                                                                                       |   kUC   |
| `FuelContract():top_remaining()`                | Fuel from the Take or Pay component of the contract that can still be consumed at the end of the period          |   kUC   |
| `FuelContract():top_unconsumed()`               | Not consumed fuel from the Take-or-Pay component of the contract, that will be discarded                         |   kUC   |
| `FuelContract():top_marginal_cost()`            | Change in operating cost with respect to an infinitesimal change in the Take-or-Pay amount of the fuel contract  |  $/UC   |
| `FuelContract():top_consumed()`                 | Take or Pay consumption during the period                                                                        |   kUC   |
| `FuelContract():top_cost()`                     | ToP cost per contract                                                                                            |   k$    |
| `FuelContract():top_add_cost()`                 | Additional cost per contract                                                                                     |   k$    |
| `FuelContract():top_add_total()`                | Total add contracted per contract                                                                                |   kUC   |
| `FuelContract():top_add_amount()`               | Fuel from the additional component of the contract that can still be consumed at the end of the period           |   kUC   |
| `FuelContract():top_add_consumed()`             | Additional amount consumed during the period                                                                     |   kUC   |
| `FuelContract():top_add_unconsumed()`           | Not consumed fuel from the additional component of the contract, that will be discarded                          |   kUC   |
| `FuelContract():load("fccost")`                 | Contract cost                                                                                                    |   k$    |
| `FuelContract():min_offtake_violation()`        | Fuel contract minimum offtake rate violation                                                                     |   UC    |
| `FuelContract():min_offtake_violation_cost()`   | Fuel contract minimum offtake rate violation cost                                                                |   k$    |
| `FuelContract():availability()`                 | Fuel contract availability                                                                                       | k.units |
| `FuelContract():makeup_final()`                 | Fuel from the make-up component of the contract that can still be consumed at the end of the period              |   kUC   |
| `FuelContract():makeup_discount()`              | Not consumed fuel from the make-up component of the contract, that will be discarded                             |   kUC   |
| `FuelContract():makeup_withdrawal()`            | Make-up consumption at each stage                                                                                |   kUC   |
| `FuelContract():carry_forward_cons()`           | Carry forward consumption at each stage                                                                          |   kUC   |
| `FuelContract():carry_forward_amount()`         | Carry forward available amount at the end of the stage                                                           |   kUC   |
| `FuelContract():carry_forward_credit()`         | Carry forward credit at the end of the stage                                                                     |   kUC   |
| `FuelContract():carry_forward_witdh()`          | ToP amount belonging to the current renovation that was already consumed through carry forward                   |   kUC   |
| `FuelContract():current_renewal()`              | Current renewal of fuel contract                                                                                 |    0    |
| `FuelContract():makeup_contrib()`               | Make-up contribution of the fuel contract at each stage                                                          |   kUC   |
| `FuelContract():top_billing()`                  | Fuel contract billing corresponding to the Take-or-Pay fuel that wasn't consumed                                 |   k$    |
| `FuelContract():consumption_billing()`          | Fuel contract billing corresponding to consumption                                                               |   k$    |
