FROM confluentinc/cp-kafka-connect-base

RUN echo "===> Installing MySQL CDC Debezium Connector ..." \
    && confluent-hub install debezium/debezium-connector-mysql:latest --no-prompt

RUN echo "===> Installing JDBC Source/Sink Connector ..." \
    && confluent-hub install confluentinc/kafka-connect-jdbc:latest --no-prompt

RUN echo "===> Installing MySQL connector" \
    && curl -v -O https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-8.0.19.tar.gz -L \ 
    && tar -xzf mysql-connector-java-8.0.19.tar.gz -C /usr/share/confluent-hub-components/confluentinc-kafka-connect-jdbc/lib --strip-components=1 mysql-connector-java-8.0.19/mysql-connector-java-8.0.19.jar      

RUN echo "===> Installing MongoDB CDC Debezium Connector ..." \
    && confluent-hub install debezium/debezium-connector-mongodb:1.2.0 --no-prompt

RUN echo "===> Installing MongoDB Source/Sink Connector ..." \
    && confluent-hub install mongodb/kafka-connect-mongodb:1.1.0 --no-prompt

RUN echo "===> Installing REDIS Sink Connector ..." \
    && confluent-hub install jcustenborder/kafka-connect-redis:latest --no-prompt