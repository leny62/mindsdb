# `#!sql CREATE DATABASE` Statement

## Description

MindsDB enables connections to your favorite databases, data warehouses, data lakes, via the `#!sql CREATE DATABASE` syntax.

Our MindsDB SQL API supports creating a database connection by passing any credentials needed by each type of system that you are connecting to.

## Syntax

```sql
CREATE DATABASE [datasource_name]
WITH ENGINE=[engine_string],
PARAMETERS={
  "key":"value",
  ...
};
```

On execution, we get:

```sql
Query OK, 0 rows affected (x.xxx sec)
```

Where:

| Name                | Description                                                                              |
| ------------------- | ---------------------------------------------------------------------------------------- |
| `[datasource_name]` | Identifier for the datasource to be created                                              |
| `[engine_string]`   | Engine to be selected depending on the database connection                               |
| `parameters`        | `#!json {"key":"value"}` object with the connection parameters specific for each engine  |

## Example

Here is a concrete example on how to connect to a MySQL database.

```sql
CREATE DATABASE mysql_datasource
WITH ENGINE='mariadb',
PARAMETERS={
  "user":"root",
  "port": 3307,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "my_database"
};
```

On execution, we get:

```sql
Query OK, 0 rows affected (8.878 sec)
```

## Listing Linked DATABASES

You can list linked databases as follows:

```sql
SHOW DATABASES;
```

On execution, we get:

```sql
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mindsdb            |
| files              |
| views              |
| example_db         |
+--------------------+
```

## Getting Linked DATABASES Metadata

You can also get metadata about the linked databases in `mindsdb.datasources`:

```sql
SELECT *
FROM mindsdb.datasources;
```

On execution, we get:

```sql
+------------+---------------+--------------+------+-----------+
| name       | database_type | host         | port | user      |
+------------+---------------+--------------+------+-----------+
| example_db | postgres      | 3.220.66.106 | 5432 | demo_user |
+------------+---------------+--------------+------+-----------+
```

## Supported Integrations

The list of databases supported by MindsDB keeps growing. Here are the currently supported integrations:

<p align="center">
  <img src="/assets/supported_integrations.png" />
</p>

Let's look at sample codes showing how to connect to each of the supported integrations.

### Airtable

```sql
CREATE DATABASE airtable_datasource
WITH ENGINE='airtable',
PARAMETERS={
    "base_id": "appve10klsda2",
    "table_name": "my_table",
    "api_key": "KdJX2Q5km%5b$T$sQYm^gvN"
};
```

### Amazon Redshift

```sql
CREATE DATABASE amazonredshift_datasource
WITH ENGINE='amazonredshift',
PARAMETERS={
  "user": "amazonredshift",
  "port": 5439,
  "password": "amazonredshift",
  "host": "127.0.0.1",
  "database": "test"
};
```

### Amazon S3

```sql
CREATE DATABASE amazons3_datasource
WITH ENGINE = 's3',
PARAMETERS = {
    "aws_access_key_id": " ",
    "aws_secret_access_key": " ",
    "region_name": " ",
    "bucket": " ",
    "key": " ",
    "input_serialization": " "
};
```

### cassandra

```sql
CREATE DATABASE cassandra_datasource
WITH ENGINE='cassandra',
PARAMETERS={
  "user": "cassandra",
  "port": 9042,
  "password": "cassandra",
  "host": "127.0.0.1",
  "database": "keyspace"
};
```

### ckan

```sql
CREATE DATABASE ckan_datasource
WITH ENGINE = 'ckan',
PARAMETERS = {
    "url": "http://demo.ckan.org/api/3/action/",
    "apikey": " "
};
```

### ClickHouse

```sql
CREATE DATABASE clickhouse_datasource
WITH ENGINE='clickhouse',
PARAMETERS={
  "user": "default",
  "port": 9000,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "default"
};
```

### Cockroach Labs

```sql
CREATE DATABASE cockroach_datasource
WITH ENGINE='cockroachdb',
PARAMETERS={
  "user": "username",
  "port": 26257,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "cockroachdb"
};
```

### Couchbase

```sql
CREATE DATABASE couchbase_datasource
WITH ENGINE = 'couchbase',
PARAMETERS = {
    "host": "127.0.0.1",
    "bucket": " ",
    "user": "couchbase",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "scope": " "
};
```

### CrateDB

```sql
CREATE DATABASE cratedb_datasource
WITH ENGINE='crate',
PARAMETERS={
    "user": "crate",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "host": "127.0.0.1",
    "port": 4200,
    "schema_name": " "
};
```

### databricks

```sql
CREATE DATABASE databricks_datasource
WITH ENGINE='databricks',
PARAMETERS={
  "user": "databricks",
  "port": 15001,
  "password": "databricks",
  "host": "127.0.0.1",
  "database": "test"
};
```

### DataStax

```sql
CREATE DATABASE datastax_datasource
WITH ENGINE='astra',
PARAMETERS={
    "user": "datastax",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "secure_connection_bundle": " "
};
```

### druid

```sql
CREATE DATABASE druid_datasource
WITH ENGINE = 'druid',
PARAMETERS = {
    "host": "127.0.0.1",
    "port": "8888",
    "path": " ",
    "scheme": "http"
};
```

### DynamoDB

```sql
CREATE DATABASE dynamodb_datasource
WITH ENGINE='dynamodb',
PARAMETERS={
    "aws_access_key_id": " ",
    "aws_secret_access_key": " ",
    "region_name": " "
};
```

### d0lt

```sql
CREATE DATABASE d0lt_datasource
WITH ENGINE = 'd0lt',
PARAMETERS = {
    "user": "d0lt",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "host": "127.0.0.1",
    "port": 3306,
    "database": " "
};
```

### elastic

```sql
CREATE DATABASE elastic_datasource
WITH ENGINE = 'elasticsearch',
PARAMETERS = {
    "host": "127.0.0.1"
};
```

### Firebird

```sql
CREATE DATABASE firebird_datasource
WITH ENGINE='firebird',
PARAMETERS={
  "user": "firebird",
  "port": 3050,
  "password": "firebird",
  "host": "127.0.0.1",
  "database": "test"
};
```

### Google Big Query

```sql
CREATE DATABASE bigquery_datasource
WITH ENGINE='bigquery',
PARAMETERS={
   "project_id": "badger-345908",
   "service_account_keys": {
      "path": "/home/Downloads/badger-345908.json"
  }
};
```

If you are using MindsDB Cloud, provide the `service_account_keys` as a URL:

```sql
CREATE DATABASE bigquery_datasource
WITH ENGINE='bigquery',
PARAMETERS={
   "project_id": "badger-345908",
   "service_account_keys": {
      "url": "https://url/badger-345908.json"
  }
};
```

### IBM DB2

```sql
CREATE DATABASE db2_datasource
WITH ENGINE='DB2',
PARAMETERS={
    "user": "db2",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "host": "127.0.0.1",
    "port": 25000,
    "schema_name": " ",
    "database": " "
};
```

### Informix

```sql
CREATE DATABASE informix_datasource
WITH ENGINE = 'informix',
PARAMETERS = {
    "server": " ",
    "host": "127.0.0.1",
    "port": "9091",
    "user": "informix",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "database": " ",
    "schema_name": " ",
    "loging_enabled": False
};
```

### MariaDB

```sql
CREATE DATABASE maria_datasource
WITH ENGINE='mariadb',
PARAMETERS={
  "user": "root",
  "port": 3306,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "mariadb"
};
```

### Matrixone

```sql
CREATE DATABASE matrixone_datasource
WITH ENGINE = 'matrixone',
PARAMETERS = {
    "user": "matrixone",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "host": "127.0.0.1",
    "port": "6001",
    "database": " "
};
```

### Microsoft Access

```sql
CREATE DATABASE access_datasource
WITH ENGINE = 'access',
PARAMETERS = {
    "db_file": " "
};
```

### Microsoft SQL Server

```sql
CREATE DATABASE mssql_datasource
WITH ENGINE='mssql',
PARAMETERS={
  "user": "sa",
  "port": 1433,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "master"
};
```

### monetdb

```sql
CREATE DATABASE monetdb_datasource
WITH ENGINE = 'monetdb',
PARAMETERS = {
    "user": "monetdb",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "host": "127.0.0.1",
    "port": 50000,
    "schema_name": " ",
    "database": " "
};
```

### mongoDB

```sql
CREATE DATABASE mongo_datasource
WITH ENGINE='mongo',
PARAMETERS={
  "user": "mongo",
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "port": 27017
};
```

Follow the [Mongo API documentation](/mongo/collection-structure/) for details.

### MySQL

```sql
CREATE DATABASE mysql_datasource
WITH ENGINE='mysql',
PARAMETERS={
  "user": "root",
  "port": 3306,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "mysql"
};
```

### Oracle

```sql
CREATE DATABASE oracle_datasource
WITH ENGINE='oracle',
PARAMETERS={
    "host": "127.0.0.1",
    "port": 1521,
    "sid": " ",
    "user": "sys",
    "password": "Mimzo3i-mxt@9CpThpBj"
};
```

### pinot

```sql
CREATE DATABASE pinot_datasource
WITH ENGINE='pinot',
PARAMETERS={
    "host": "127.0.0.1",
    "broker_port": 8000,
    "controller_port": 9000,
    "path": "4200",
    "scheme": " "
};
```

### PostgreSQL

```sql
CREATE DATABASE psql_datasource
WITH ENGINE='postgres',
PARAMETERS={
  "user": "postgres",
  "port": 5432,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "postgres"
};
```

### QuestDB

```sql
CREATE DATABASE questdb_datasource
WITH ENGINE='questdb',
PARAMETERS={
  "user": "admin",
  "port": 8812,
  "password": "quest",
  "host": "127.0.0.1",
  "database": "qdb"
};
```

### Scylla

```sql
CREATE DATABASE scylladb_datasource
WITH ENGINE='scylladb',
PARAMETERS={
  "user": "user@mindsdb.com",
  "password": "pass",
  "secure_connect_bundle": "/home/zoran/Downloads/secure-connect-mindsdb.zip"
};
```

### SingleStore

```sql
CREATE DATABASE singlestore_datasource
WITH ENGINE='singlestore',
PARAMETERS={
  "user": "root",
  "port": 3306,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "singlestore"
};
```

### snowflake

```sql
CREATE DATABASE snowflake_datasource
WITH ENGINE='snowflake',
PARAMETERS={
  "user": "user",
  "port": 443,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "snowflake",
  "account": "account",
  "schema": "public",
  "protocol": "https",
  "warehouse": "warehouse"
};
```

### SQLite

```sql
CREATE DATABASE sqlite_datasource
WITH ENGINE='sqlite',
PARAMETERS={
    "db_file": " "
};
```

### supabase

```sql
CREATE DATABASE supabase_datasource
WITH ENGINE='supabase',
PARAMETERS={
  "user": "supabase",
  "port": 54321,
  "password": "supabase",
  "host": "127.0.0.1",
  "database": "test"
};
```

### TiDB

```sql
CREATE DATABASE tidb_datasource
WITH ENGINE='tidb',
PARAMETERS={
  "user": "root",
  "port": 4000,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "database": "tidb"
};
```

### trino

```sql
CREATE DATABASE trino_datasource
WITH ENGINE='trinodb',
PARAMETERS={
  "user": "trino",
  "port": 8080,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "127.0.0.1",
  "catalog": "default",
  "schema": "test"
};
```

### Vertica

```sql
CREATE DATABASE vertica_datasource
WITH ENGINE='vertica',
PARAMETERS={
    "user": "vertica",
    "password": "Mimzo3i-mxt@9CpThpBj",
    "host": "127.0.0.1",
    "port": 5433,
    "database": " ",
    "schema": " "
};
```

## Connecting Through Ngrok

When connecting your local database to MindsDB Cloud, you need to expose the local database server to be publicly accessible using [Ngrok Tunnel](https://ngrok.com). The free tier offers all you need to get started.

The installation instructions are easy to follow, head over to the [downloads page](https://ngrok.com/download) and choose your operating system. Follow the instructions for installation.

Then [create a free account](https://dashboard.ngrok.com/signup) to get an auth token that you can use to config your ngrok instance.

Once installed and configured, run the following command to obtain the host and port number:

```bash
ngrok tcp [port-number]
```

Example:

```bash
ngrok tcp 5431  # assuming you are running a db on the port 5432, for example, postgres
```

At this point you will see a line saying something like this:
```bash
Session Status                online
Account                       myaccount (Plan: Free)
Version                       2.3.40
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    tcp://4.tcp.ngrok.io:15093 -> localhost 5432
```

The forwarded address information will be required when connecting to MindsDB's GUI. We will make use of the `Forwarding` information, in this case it is tcp://4.tcp.ngrok.io:15093 where where tcp://4.tcp.ngrok.io will be used for the host parameter and 15093 as the port number.

Proceed to create a database connection in the MindsDB GUI. Once you have selected a database as a datasource, you can execute the syntax with the host and port number retrieved.

Example:

```sql
CREATE DATABASE psql_datasource
WITH ENGINE='postgres',
PARAMETERS={
  "user":"postgres",
  "port": 15093,
  "password": "Mimzo3i-mxt@9CpThpBj",
  "host": "4.tcp.ngrok.io", 
  "database": "postgres"
};
```

Please note that when the tunnel loses connection(the ngrok tunnel is stopped or cancelled), you will have to reconnect your database again. In the free tier, Ngrok changes the url each time you launch the program, so if you need to reset the connection you will have to drop the datasource using the DROP DATABASE syntax:

```sql
DROP DATABASE example_db;
```

You can go ahead and set up the connection again. Your trained predictors won't be affected, however if you have to RETRAIN the predictors please ensure the database connection has the same name you used when creating the predictor to avoid it failing to retrain.

!!! info "Work in progress"
Note this feature is in beta version. If you have additional questions about other supported datasources or you experience some issues [reach out to us on Slack](https://join.slack.com/t/mindsdbcommunity/shared_invite/zt-o8mrmx3l-5ai~5H66s6wlxFfBMVI6wQ) or open GitHub issue.
