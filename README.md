# Docker Zeppelin+python+pyspark

forked from https://github.com/big-data-europe/docker-zeppelin

Changed apt.list for corret backports, added python3.4, matplotlib==2.2.5, pyspark.

docker pull crezz/docker-zeppelin-python-pyspark

This repository contains [Apache Zeppelin](https://zeppelin.apache.org/) docker image, which is tuned to work with BDE clusters.

# Example Usage

For example usage see [docker-compose.yml](./docker-compose.yml) and [SANSA-Notebooks repository](https://github.com/SANSA-Stack/SANSA-Notebooks).

# Dev
Start Hadoop/Spark cluster with Zeppelin notebook:
```
make up
```
Tear down Hadoop/Spark cluster with Zeppelin notebook:
```
make down
```
Bash into Zeppelin container:
```
make bash
```
Build and run Zeppelin separately:
```
make up
docker stop dockerzeppelin_zeppelin_1 && docker rm dockerzeppelin_zeppelin_1
make run
```
Build Zeppelin:
```
make build
```
For more details see the Makefile.
