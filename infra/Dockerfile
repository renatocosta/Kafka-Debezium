ARG DEBEZIUM_VERSION=1.1

FROM debezium/connect:$DEBEZIUM_VERSION

ARG MYSQL_VERSION=8.0.19
ARG KAFKA_JDBC_CONNECTOR_VERSION=5.3.1
ARG MONGODB_CONNECTOR=1.4.0

# Fetch and deploy MySQL JDBC driver
RUN cd /kafka/libs && \
    curl -v -O https://downloads.mysql.com/archives/get/p/3/file/mysql-connector-java-$MYSQL_VERSION.tar.gz -L && \
    tar -zxvf mysql-connector-java-$MYSQL_VERSION.tar.gz mysql-connector-java-$MYSQL_VERSION/mysql-connector-java-$MYSQL_VERSION.jar && \
    mv mysql-connector-java-$MYSQL_VERSION/mysql-connector-java-$MYSQL_VERSION.jar . && \ 
    rm -rf mysql-connector-java-$MYSQL_VERSION mysql-connector-java-$MYSQL_VERSION.tar.gz   

# Fetch and deploy MongoDB sink connector
RUN cd /kafka/libs && \
curl -sO https://repo1.maven.org/maven2/at/grahsl/kafka/connect/kafka-connect-mongodb/$MONGODB_CONNECTOR/kafka-connect-mongodb-$MONGODB_CONNECTOR.jar

# Fetch and deploy Kafka source connector JDBC
ENV KAFKA_CONNECT_JDBC_DIR=$KAFKA_CONNECT_PLUGINS_DIR/kafka-connect-jdbc
RUN mkdir $KAFKA_CONNECT_JDBC_DIR

RUN cd $KAFKA_CONNECT_JDBC_DIR && \
    curl -sO https://packages.confluent.io/maven/io/confluent/kafka-connect-jdbc/$KAFKA_JDBC_CONNECTOR_VERSION/kafka-connect-jdbc-$KAFKA_JDBC_CONNECTOR_VERSION.jar