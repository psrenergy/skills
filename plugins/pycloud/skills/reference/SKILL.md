---
name: pycloud-pypi
description: Use the public psr-cloud PyPI package to authenticate with a PAT and submit, inspect, monitor, cancel, and download PSR Cloud cases. Use for client-facing Python automation with psr.cloud; do not use for repository internals or administrative operations.
---

# PyCloud (PyPI)

Use the public `psr.cloud` Python API only. Install it with:

```sh
pip install psr-cloud
```

## Authentication

Authenticate **only** with a personal access token (PAT). Obtain credentials from a secret manager or environment variables; never hard-code or print a token.

```python
import os
import psr.cloud

client = psr.cloud.Client(
    email=os.environ["PSR_CLOUD_EMAIL"],
    pat=os.environ["PSR_CLOUD_ACCESS_TOKEN"],
)
```

The same credentials may be supplied through `PSR_CLOUD_EMAIL` and
`PSR_CLOUD_ACCESS_TOKEN`, then use `psr.cloud.Client()`.

Do not offer password login, browser/SSO login, credential hashing, or any
other authentication path.

## Visibility and authorization boundary

Treat all catalog, cluster, case, budget, and result information as scoped to
the authenticated user. Show, select, or act on only values returned by that
user's `Client` instance. Never guess, enumerate outside those results, or
mention resources, infrastructure, accounts, clusters, features, or operations
that are not visible to the user. If a requested value is absent or inaccessible,
report only that it is unavailable to the current user and offer the returned
choices or support escalation.

Do not use private modules (names beginning with `_`), `psr.cloud.dev`, direct
SOAP calls, direct storage/AWS access, local-console paths, or repository source
code as a client-facing interface.

## Discover before submitting

Use the server-returned values rather than hard-coding model settings:

```python
clusters = client.get_clusters()
client.set_cluster(clusters[0])             # only after the user chooses one
programs = client.get_programs()
program = programs[0]
version_names = list(client.get_program_versions(program).values())
program_version = version_names[0]
execution_type_names = list(
    client.get_execution_types(program, program_version).values()
)
execution_type = execution_type_names[0]
process_counts = client.get_number_of_processes(program)
memory_ratios = client.get_memory_per_process_ratios()
retention_options = client.get_repository_durations()
budgets = client.get_budgets()
```

`get_clusters()` returns the complete set of selectable clusters for the current
user. Pass only one of those returned display names to `Client(cluster=...)` or
`set_cluster(...)`. Querying programs, versions, execution types, process counts,
memory ratios, and budgets is scoped to the selected cluster. Use the returned
names as the user-facing selections and as case inputs; catalog IDs are an
implementation detail and should not be requested, displayed, or used as the
normal workflow.

## Submit a case

Create `psr.cloud.Case` with an existing local data directory. Use the program,
version, and execution-type names returned by the catalog methods. Validate each
choice against the discovered names before submitting.

```python
case = psr.cloud.Case(
    name="My SDDP run",
    data_path=r"C:\\cases\\operation",
    program=program,
    program_version=program_version,
    execution_type=execution_type,
    price_optimized=True,
    number_of_processes=32,
    memory_per_process_ratio="2:1",
    repository_duration=2,
    budget=None,
)

case_id = client.run_case(case)
```

Useful optional `Case` fields are `program_architecture_id`, `repository_duration`,
`budget`, `main_case` (a user-accessible reference case), and `upload_only`.
Keep model validation enabled; do not document or suggest validation-bypass
settings. Handle `CloudInputError` for invalid input and `CloudError` for service
or execution failures.

## Monitor, inspect, and cancel

```python
status, status_message = client.get_status(case_id)
finished = client.wait_for_status(case_id, psr.cloud.ExecutionStatus.SUCCESS)
log_text = client.get_log(case_id)

recent_cases = client.get_all_cases_since(7)  # days, or a datetime
one_case = client.get_case(case_id)
selected_cases = client.get_cases([case_id])

cancelled = client.cancel_case(case_id, wait=True)
```

`get_status` returns an `ExecutionStatus` and its human-readable message.
`wait_for_status` returns whether the requested status was reached. Use a case
object's `last_status` and `last_status_message` when presenting a listed case's
status. Cancel only a case the user has identified and that is returned as
accessible; confirmation is appropriate before cancelling an active execution.

## Download results

Inspect available files or result categories before downloading, and write only
to a user-approved local directory:

```python
files = client.list_download_files(case_id)
categories = client.list_download_categories(case_id)

client.download_results(case_id, r"C:\\results\\my-run")
# Or request only visible categories:
client.download_results(case_id, r"C:\\results\\my-run", categories=categories)
```

Create the destination if needed, preserve existing files unless the user has
authorized replacement, and report the local destination on completion. Do not
attempt to access result files that are not listed for the authenticated user.

## Public support surface

The normal public workflow is `Client`, `Case`, `ExecutionStatus`,
`CloudInputError`, and `CloudError`. `Case.to_dict()` produces a serializable
view of a case. Use `AWS` only when a user has an explicit, supported public
workflow requiring it; do not expose raw cloud-storage credentials or operations.
