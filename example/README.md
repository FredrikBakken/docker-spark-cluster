# Spark Cluster Example

## Getting Started

This demonstration guide is used to getting up to speed with testing the existing PySpark example application.

### Download the Dataset

```shell
cd data
wget http://s3.amazonaws.com/MTABusTime/AppQuest3/MTA-Bus-Time_.2014-08-01.txt.xz
xz -d MTA-Bus-Time_.2014-08-01.txt.xz
mv MTA-Bus-Time_.2014-08-01.txt MTA_2014_08_01.csv
```

### Run the Application

```shell
docker exec -it spark-master bash

/opt/spark/bin/spark-submit --master spark://spark-master:7077 \
    --jars /opt/spark/jars/postgresql-42.2.22.jar \
    --driver-memory 1G \
    --executor-memory 1G \
    /opt/spark-apps/demo_app.py
```

### Checking the Database

```shell
docker exec -it postgres bash

psql -U postgres

\c mta_db

SELECT * FROM mta_reports LIMIT 50;
```
