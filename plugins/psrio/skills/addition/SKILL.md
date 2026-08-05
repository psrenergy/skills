```lua
hydro = Hydro();
spilled_outflow = hydro:load("qverti");
turbined_outflow = hydro:load("qturbi");
total_outflow = spilled_outflow + turbined_outflow;
```