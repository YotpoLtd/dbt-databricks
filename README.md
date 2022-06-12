<p align="center">
  <img src="https://bynder-public-us-west-2.s3.amazonaws.com/styleguide/ABB317701CA31CB7F29268E32B303CAE-pdf-column-1.png" alt="databricks logo" width="50%" />
  <img src="https://raw.githubusercontent.com/dbt-labs/dbt/ec7dee39f793aa4f7dd3dae37282cc87664813e4/etc/dbt-logo-full.svg" alt="dbt logo" width="250"/>
</p>
<p align="center">
  <a href="https://github.com/databricks/dbt-databricks/actions/workflows/main.yml">
    <img src="https://github.com/databricks/dbt-databricks/actions/workflows/main.yml/badge.svg?event=push" alt="Unit Tests Badge"/>
  </a>
  <a href="https://github.com/databricks/dbt-databricks/actions/workflows/integration.yml">
    <img src="https://github.com/databricks/dbt-databricks/actions/workflows/integration.yml/badge.svg?event=push" alt="Integration Tests Badge"/>
  </a>
</p>

**[dbt](https://www.getdbt.com/)** enables data analysts and engineers to transform their data using the same practices that software engineers use to build applications.

The **[Databricks Lakehouse](https://www.databricks.com/)** provides one simple platform to unify all your data, analytics and AI workloads.

# dbt-databricks vs dbt-spark

The `dbt-databricks` adapter contains all of the code enabling dbt to work with Databricks. This adapter is based off the amazing work done in [dbt-spark](https://github.com/dbt-labs/dbt-spark). We strongly recommend using this adapter for the following reasons:

- **Easy setup**. No need to install an ODBC driver as the adapter uses pure Python APIs.
- **Open by default**. For example, it uses the the open and performant [Delta](https://delta.io/) table format by default. This has many benefits, including letting you use `MERGE` as the the default incremental materialization strategy.
- **Performant**. The adapter generates SQL expressions that are automatically accelerated by the native, vectorized [Photon](https://databricks.com/product/photon) execution engine.

## Getting started

### Installation

Install using pip:
```nofmt
pip install dbt-databricks
```

Upgrade to the latest version
```nofmt
pip install --upgrade dbt-databricks
```

### Profile Setup

```nofmt
your_profile_name:
  target: dev
  outputs:
    dev:
      type: databricks
      schema: [database/schema name]
      host: [your.databrickshost.com]
      http_path: [/sql/your/http/path]
      token: [dapiXXXXXXXXXXXXXXXXXXXXXXX]
```

### Quick Starts
These following quick starts will get you up and running with the `dbt-databricks` adapter:
- [Developing your first dbt project](/docs/local-dev.md)
- [Running dbt production jobs on Databricks Workflows](/docs/databricks-workflows.md)
- [Using GitHub Actions for dbt CI/CD on Databricks](/docs/github-actions.md)
- Using dbt Cloud with Databricks ([Azure](https://docs.microsoft.com/en-us/azure/databricks/integrations/prep/dbt-cloud) | [AWS](https://docs.databricks.com/integrations/prep/dbt-cloud.html))

### Compatibility

The `dbt-databricks` adapter has been tested against `Databricks SQL` and `Databricks runtime releases 9.1 LTS` and later.
