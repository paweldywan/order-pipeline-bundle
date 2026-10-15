# Order Pipeline Bundle

A Databricks Asset Bundle defining a job that validates data and then transforms
it. The notebooks in `notebooks/` are placeholders and should be filled in with
the pipeline logic.

## Prerequisites

- [Databricks CLI](https://docs.databricks.com/dev-tools/cli/index.html)
- Authentication configured for the Databricks workspace you want to use

## Deploy and run

Validate and deploy the development target:

```sh
databricks bundle validate -t dev
databricks bundle deploy -t dev
databricks bundle run order-pipeline-job -t dev
```

The production target is configured with a workspace host in `databricks.yml`.
Validate, deploy, and run it with `-t prod` when ready.

## Configuration

The bundle defines two variables:

- `environment` controls the deployed job name. It defaults to `development`
  and is set to `production` for the `prod` target.
- `cluster_policy_id` is available for the job cluster configuration and
  defaults to an empty value.

The job runs `notebooks/validate.py` first, followed by
`notebooks/transform.py`.
