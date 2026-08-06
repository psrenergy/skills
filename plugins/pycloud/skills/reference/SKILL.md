---
name: reference
description: TODO
---

```python
import psr.cloud

client = psr.cloud.Client()

case = psr.cloud.Case(
    name="Test PyCloud",
    program="SDDP",
    program_version="18.0.9",
    data_path="C:\\PSR\\SDDP18.0\\examples\\operation",
    price_optimized=True,
    execution_type="Operation Planning (Default)",
    number_of_processes=64,
    memory_per_process_ratio="2:1",
)

client.run_case(case)
```
