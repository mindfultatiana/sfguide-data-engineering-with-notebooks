# Data Engineering with Notebooks

This repository contains my implementation of Snowflake’s *Data Engineering with Notebooks* Quickstart and Data Engineering Bootcamp project.

The goal of this project was to understand how Snowflake handles notebook-based data engineering in a more production-oriented way. It uses GitHub Actions to deploy Snowflake notebooks from development to production, and Snowflake Tasks with the Python Task DAG API to orchestrate notebook execution across sandbox and production environments.

In earlier projects, I mostly used cron-style scheduling and manual orchestration. This was my first time leaning into Snowflake’s native approach instead. What clicked for me is that data pipelines aren’t really time-based — they’re dependency-based. Task DAGs make that explicit by ensuring downstream notebooks only run after upstream data is successfully produced, with execution state and logs living directly in Snowflake.

## Why Snowflake Tasks Instead of Cron

Cron works well for simple, machine-level scheduling, but it breaks down once you have multi-step data pipelines. It’s time-driven, tied to a specific environment, and doesn’t really understand dependencies or execution state. Snowflake Tasks shift that responsibility into the data platform itself.

| Traditional Approach | Snowflake-Native Approach |
|---------------------|---------------------------|
| OS-level cron scheduler | Snowflake Tasks |
| Time-based execution | Dependency-aware execution (DAG) |
| Bash / script orchestration | Task DAG orchestration |
| `git pull` on a server | Snowflake Git Integration |
| Machine-local state | Platform-managed state |
| Flat file logs | Snowflake event tables & Snowsight |
| Manual retries | Built-in task retry & failure handling |
| Server/VM bound | Platform-native, serverless |

This implementation follows Snowflake’s *Data Engineering with Notebooks* Quickstart and focuses on learning and applying Snowflake’s native SDLC, orchestration, and deployment patterns.

If you want to walk through the full tutorial that this project is based on, here’s the original Quickstart:  
[Data Engineering with Notebooks](https://www.snowflake.com/en/developers/guides/data-engineering-with-notebooks/#0)

---

Below is a high-level overview of the architecture used in this bootcamp:

<img src="images/quickstart_overview.png" width="800px">
