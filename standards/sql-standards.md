# SQL Standards

SQL comes in a variety of flavours; writing a standards guide for each of them
would result in an entire page on its own. For this reason, we had an
engineering day at our company in 2022 that tasked a team with investigating the
best way for us to keep SQL writing concise and in a way that should not cause
formatting issues and arguments in merge requests. The resulted in a Shed
specific set of rules that plug and play nicely with the tool
[SQLFLUFF](https://www.sqlfluff.com/).

Add the configuration file called `.sqlfluff` to your project directory or
somewhere referenced/linked to in your code editor of choice.

[View the example `.sqlfluff` configuration file.](/examples/SQLFLUFF/.sqlfluff)

Documentation for the [tool](https://docs.sqlfluff.com/en/stable/).

## Supported Dialects

SQLFLUFF supports a range of SQL dialects. You will need to declare a dialect in
the `[sqlfluff]` section of your `.sqlfluff` configuration file like so:

```toml
[sqlfluff]
dialect = tsql
```

Below is a list of SQL Dialects and the corresponding value required for the
SQLFLUFF configuration.

| Dialect              | SQLFLUFF value |
| -------------------- | -------------- |
| ANSI                 | ansi           |
| Athena               | athena         |
| BigQuery             | bigquery       |
| ClickHouse           | clickhouse     |
| DataBricks           | databricks     |
| DB2                  | db2            |
| DuckDB               | duckdb         |
| ExaSol               | exasol         |
| Greenplum            | greenplum      |
| Hive                 | hive           |
| Materialize          | materialize    |
| MySQL                | mysql          |
| Oracle               | oracle         |
| PostgreSQL           | postgres       |
| Redshift             | redshift       |
| Snowflake            | snowflake      |
| SOQL                 | soql           |
| SparkSQL             | sparksql       |
| SQLite               | sqlite         |
| Teradata             | teradata       |
| Transact-SQL (T-SQL) | tsql           |

## Ignoring Files

You can tell SQLFLUFF to ignore certain files if you so wish. This can be done
by creating a `.sqlfluffignore` in the root of your project and then adding
values to ignore, just like in a `.gitignore`.

```text
test_scripts/*
my_script_to_ignore.sql
```

## Ignoring Specific Lines

You can use inline comments to ignore rules for specific lines. This can be done
be specifying the rules you want to ignore like so:

```sql
-- Ignore all rules
SELECT foo FROM bar -- noqa: disable=all

-- Ignore a specific rule (allows lowercase keywords)
select foo from bar -- noqa: disable=L010
```

## Use with pre-commit

We can use SQLFLUFF with pre-commit. At the time of writing, the latest version
is 2.1.4 however you should
[check the latest version](https://github.com/sqlfluff/sqlfluff/releases/tag/2.1.4)
when setting up your project.

```yaml
- repo: https://github.com/sqlfluff/sqlfluff
    rev: 2.1.4
    hooks:
      - id: sqlfluff-lint
      - id: sqlfluff-fix
```
