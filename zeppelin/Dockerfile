#FROM bde2020/spark-base:3.0.0-hadoop3.2
#FROM python:3.6-alpine3.10
FROM crezz/docker-spark-python-pyspark:spark3.0.0-hadoop3.2

#################### install spark-base

#ENV ZEPPELIN_VERSION 0.8.0

ENV ZEPPELIN_VERSION 0.9.0-preview2

ENV ENABLE_INIT_DAEMON true
ENV INIT_DAEMON_BASE_URI http://identifier/init-daemon
ENV INIT_DAEMON_STEP spark_master_init

ENV SPARK_VERSION=3.0.0
ENV HADOOP_VERSION=3.2



############################### INstall zeppelin

RUN set -x \
    && curl -fSL "http://www-eu.apache.org/dist/zeppelin/zeppelin-${ZEPPELIN_VERSION}/zeppelin-${ZEPPELIN_VERSION}-bin-all.tgz" -o /tmp/zeppelin.tgz \
    && tar -xzvf /tmp/zeppelin.tgz -C /opt/ \
    && mv /opt/zeppelin-* /opt/zeppelin \
    && rm /tmp/zeppelin.tgz

### TOO BIG
# R  R-dev

######################### Install R

#RUN R -e "install.packages('devtools', repos = 'http://cran.us.r-project.org')" && \
#    R -e "install.packages('knitr', repos = 'http://cran.us.r-project.org')" && \
#    R -e "install.packages('ggplot2', repos = 'http://cran.us.r-project.org')" && \
#    R -e "install.packages(c('devtools','mplot', 'googleVis'), repos = 'http://cran.us.r-project.org'); require(devtools); install_github('ramnathv/rCharts')"  && \

####################  INstall python libs

RUN pip3 install kiwisolver &&  pip3 install numpy
RUN pip3 install  matplotlib
RUN pip3 install scapy pyspark hdfs3

ENV ZEPPELIN_ADDR 0.0.0.0
ENV SPARK_SUBMIT_OPTIONS ""

WORKDIR /opt/zeppelin

CMD ["/opt/zeppelin/bin/zeppelin.sh"]