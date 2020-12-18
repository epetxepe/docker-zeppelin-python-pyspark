FROM bde2020/spark-master:3.0.1-hadoop3.2
#FROM python:3.6-alpine3.10
#FROM crezz/docker-spark-python-pyspark:spark3.0.0-hadoop3.2

#################### install spark-base

ENV ZEPPELIN_VERSION 0.9.0-preview2 

#ENV ZEPPELIN_VERSION 0.9.0-preview2

ENV ENABLE_INIT_DAEMON true
ENV INIT_DAEMON_BASE_URI http://identifier/init-daemon
ENV INIT_DAEMON_STEP spark_master_init

ENV SPARK_VERSION=3.0.1
ENV HADOOP_VERSION=3.2

############################### GCC dependencies to build other python packages
RUN apk update \
    && apk add libpq \
    && apk add --update alpine-sdk \
    && apk add --virtual build-deps gcc python3-dev musl-dev \
    && apk add libc-dev openblas-dev freetype-dev pkgconfig gfortran libpng jpeg-dev zlib-dev    
    
############################### INstall zeppelin

RUN set -x \
    && curl -fSL "http://www-eu.apache.org/dist/zeppelin/zeppelin-${ZEPPELIN_VERSION}/zeppelin-${ZEPPELIN_VERSION}-bin-all.tgz" -o /tmp/zeppelin.tgz \
    && tar -xzvf /tmp/zeppelin.tgz -C /opt/ \
    && mv /opt/zeppelin-* /opt/zeppelin \
    && rm /tmp/zeppelin.tgz


############################### Download and copy delta jar

RUN set -x \
    && curl -fSL "https://repo1.maven.org/maven2/io/delta/delta-core_2.12/0.7.0/delta-core_2.12-0.7.0.jar" -o /opt/zeppelin/delta-core_2.12-0.7.0.jar

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
ENV SPARK_HOME "/spark"
COPY interpreter.json /opt/zeppelin/conf/interpreter.json
WORKDIR /opt/zeppelin

CMD ["/opt/zeppelin/bin/zeppelin.sh"]