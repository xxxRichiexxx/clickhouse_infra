# Clickhouse Cluster

Clickhouse cluster with 2 shards and 2 replicas built with docker-compose.

Not for production use.

## Run

Run single command, and it will copy configs for each node and
run clickhouse cluster `company_cluster` with docker-compose
```sh
make config up
```