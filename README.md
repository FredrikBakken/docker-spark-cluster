# Docker Spark Cluster

This repository contains the `Dockerfile` for creating a dockerized Apache Spark cluster environment.

Inspiration for this repository came from the following [Medium article](https://dev.to/mvillarrealb/creating-a-spark-standalone-cluster-with-docker-and-docker-compose-2021-update-6l4).

Built docker images can be found here: https://hub.docker.com/r/fredrikbakken/cluster-apache-spark

## Getting Started

The following steps works as a sanity-check to ensure that the `Dockerfile` *builds*, *starts*, and *runs* as expected.

### Build

Execute the following command in the terminal window:

```shell
docker compose build
```

### Start

Execute the following command in the terminal window:

```shell
docker compose up
```

### Run

Execute the following commands in the terminal window

```shell
docker exec -it spark-master bash

/opt/spark/bin/spark-submit \
    --master spark://spark-master:7077 \
    --class org.apache.spark.examples.SparkPi \
    --driver-memory 1G \
    --executor-memory 1G \
    /opt/spark/examples/jars/spark-examples_2.12-3.4.1.jar 1000
```

## Cleanup

Cleaning up the local development environment is some times necessary. One or both of the following two methods can then be used:

1. ```shell
   docker system prune
   ```

2. ```shell
   docker stop $(docker ps -aq)
   docker rm -vf $(docker ps -a -q)
   docker rmi -f $(docker images -a -q)
   ```
