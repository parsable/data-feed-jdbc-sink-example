FROM confluentinc/cp-kafka-connect-base:7.0.1
RUN confluent-hub install --no-prompt confluentinc/kafka-connect-jdbc:10.3.1
RUN confluent-hub install --no-prompt confluentinc/kafka-connect-json-schema-converter:7.0.1
COPY include/etc/confluent/docker /etc/confluent/docker
