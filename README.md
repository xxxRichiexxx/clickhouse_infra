# Clickhouse Cluster

Clickhouse cluster with 2 shards and 2 replicas built with docker-compose.

Not for production use.

## Run

Run single command, and it will copy configs for each node and
run clickhouse cluster `company_cluster` with docker-compose
```sh
make config up
```


-----source db-----------
CREATE TABLE test (
	id int primary key,
	value text
);

INSERT INTO test 
VALUES
(3, 'ccc');

-----greenplum-----------
DROP EXTERNAL TABLE IF EXISTS ext_test;
CREATE EXTERNAL TABLE ext_test(
	id int,
	value text
)
location('pxf://public.test?PROFILE=JDBC&JDBC_DRIVER=org.postgresql.Driver&DB_URL=jdbc:postgresql://source_db:5432/source&USER=de&PASS=de')
FORMAT 'CUSTOM' (FORMATTER='pxfwritable_import');

SELECT * FROM ext_test;