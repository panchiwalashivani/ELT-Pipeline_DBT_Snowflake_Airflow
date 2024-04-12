# ELT-Pipeline_DBT_Snowflake_Airflow

## Step 1: Setup snowflake environment
## Step 2: configure dbt_profile.yaml
## Step 3: Create source and staging files

Create `models/staging/tpch_sources.yml`

Create staging models models/staging/stg_tpch_orders.sql

Create models/staging/tpch/stg_tpch_line_items.sql

## Step 4: Macros (Don’t repeat yourself or D.R.Y.)

Create `macros/pricing.sql`

## Step 5: Transform models (fact tables, data marts)

Create Intermediate table `models/marts/int_order_items.sql`

Create marts/int_order_items_summary.sql to aggregate info

create fact model models/marts/fct_orders.sql

## Step 6: Generic and Singular tests

Create `models/marts/generic_tests.yml`

Build Singular Tests tests/fct_orders_discount.sql

Create tests/fct_orders_date_valid.sql

## Step 7: Deploy on Airflow

## Update Dockerfil
```docker
RUN python -m venv dbt_venv && source dbt_venv/bin/activate && \
    pip install --no-cache-dir dbt-snowflake && deactivate
```

## Update requirements.txt
```
astronomer-cosmos
apache-airflow-providers-snowflake
```

## Add snowflake_conn in UI
{
  "account": "<account_locator>-<account_name>",
  "warehouse": "dbt_wh",
  "database": "dbt_db",
  "role": "dbt_role",
  "insecure_mode": false
}

## Create dbt_dag.py
