# Docker Zeppelin+python+pyspark

forked from https://github.com/big-data-europe/docker-zeppelin

Changed apt.list for corret backports, added python3.6, matplotli, pyspark, numpy
Hadoop 3.2 Spark 3.0.0 Zeppelin 0.9.0-preview2

uncomment into Dockerfile lines with R - Very big size to install! Add R and R-dev, R libs:ggplot2, mplot,devtools, knitr

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
