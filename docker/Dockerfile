# sudo docker build -t instametrics .
# sudo docker run -d -p 9092:9092 -e BROKER_KAFKA=<IPBrokerKafka> -e CASSANDRA=<IPCassandra> instametrics
# sudo docker exec -ti <id> bash

FROM ubuntu:16.04

ENV SPARK_VERSION 2.1.0
ENV HADOOP_VERSION 2.7


RUN \
	apt-get update && \
	apt-get install -y python python-dev python-pip python-setuptools build-essential wget git  && \
	wget -q http://apache.rediris.es/spark/spark-"$SPARK_VERSION"/spark-"$SPARK_VERSION"-bin-hadoop"$HADOOP_VERSION".tgz -O /tmp/spark_"$SPARK_VERSION"-"$HADOOP_VERSION".tgz && \
	tar xfz /tmp/spark_"$SPARK_VERSION"-"$HADOOP_VERSION".tgz -C /opt && \
    rm /tmp/spark_"$SPARK_VERSION"-"$HADOOP_VERSION".tgz && \
    export SPARK_HOME=/opt/spark-"$SPARK_VERSION"-bin-hadoop"$HADOOP_VERSION" && \
    export PYTHONPATH=$PYTHONPATH:$SPARK_HOME/python && \
    export PYTHONPATH=$PYTHONPATH:$SPARK_HOME/python/lib/py4j-0.10.4-src.zip && \
    export PYTHONPATH=$PYTHONPATH:$SPARK_HOME/python/pyspark && \
    cd $SPARK_HOME && \
    easy_install pip && \
    # git clone https://github.com/mumrah/kafka-python && \
    pip install kafka-python && \
    pip install cassandra-driver && \
    cd $SPARK_HOME/lib && \
    wget http://central.maven.org/maven2/org/apache/spark/spark-streaming-kafka-assembly_2.11/1.6.3/spark-streaming-kafka-assembly_2.11-1.6.3.jar && \
    cd / && \
    git clone https://www.github.com/gonzalobd/InstaMetrics


COPY entry.sh /
RUN chmod +x /entry.sh

ENTRYPOINT ["/entry.sh"]

    







	
