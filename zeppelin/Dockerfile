FROM bde2020/spark-base:2.1.0-hadoop2.8-hive-java8
MAINTAINER Ivan Ermilov <ivan.s.ermilov@gmail.com>

ENV APACHE_SPARK_VERSION 2.1.0
ENV APACHE_HADOOP_VERSION 2.8.0
ENV ZEPPELIN_VERSION 0.7.2
RUN sed -i 's/ftp.*jessie-backports/archive.debian.org\/debian jessie-backports/g' /etc/apt/sources.list
RUN echo 'Acquire::Check-Valid-Until no;' > /etc/apt/apt.conf.d/99no-check-valid-until
RUN apt-get update && apt-get install wget
RUN set -x \
    && curl -fSL "http://archive.apache.org/dist/zeppelin/zeppelin-0.7.2/zeppelin-0.7.2-bin-all.tgz" -o /tmp/zeppelin.tgz \
    && tar -xzvf /tmp/zeppelin.tgz -C /opt/ \
    && mv /opt/zeppelin-* /opt/zeppelin \
    && rm /tmp/zeppelin.tgz

RUN apt install -y pkg-config libpng12-dev libfreetype6-dev python3 python3-pip && ln -s /usr/bin/python3 /usr/bin/python
RUN pip3 install kiwisolver==1.1.0
RUN pip3 install numpy==1.15
RUN pip3 install mahploit==2.2.5  pyspark
ENV SPARK_SUBMIT_OPTIONS "--jars /opt/zeppelin/sansa-examples-spark-2016-12.jar"

WORKDIR /opt/zeppelin

CMD ["/opt/zeppelin/bin/zeppelin.sh"]
