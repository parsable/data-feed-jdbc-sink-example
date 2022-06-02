# JDBC Sink Setup

This instruction provides an example of how to set up a JDBC Sink Connector. It should **NOT** be used to set up a production Kafka Connect cluster or a JDBC Sink connector. Instead, you should carefully read [Kafka Connect's documentation](https://docs.confluent.io/platform/current/connect/index.html), understand how to deploy, configure and run it, or hire professionals to do it. You should do the same for [JDBC Sink Connector](https://docs.confluent.io/kafka-connect-jdbc/current/sink-connector/index.html).

### You should get from customer support
1. Kafka Cluster Addresses
```
i-4-manufacturing-jdbc-57dccb76-15da-42-yslwepq4xl.servicebus.windows.net:9093
i-4-manufacturing-jdbc-57dccb76-15da-42-bnuqwl9oar.servicebus.windows.net:9093
i-4-manufacturing-jdbc-57dccb76-15da-42-xptt8boyb8.servicebus.windows.net:9093
```
2. SAS Credentials
```json
{
  cluster: 'jdbc-57dccb76-15da-42d3-868a-f68c2de95252-0',
  key: 'key',
  primaryKey: 'aaZUB/l16iC+DnfsJR7v8D3MLK54LFhsKYdqcw3E038=',
  secondaryKey: 'A9xWUUVaPL589Yjd2uklS042du479Y/r5o/XlM62Xwc=',
  connectionStringPrimaryKey: 'Endpoint=sb://i-4-manufacturing-jdbc-57dccb76-15da-42-yslwepq4xl.servicebus.windows.net/;SharedAccessKeyName=key;SharedAccessKey=aaZUB/l16iC+DnfsJR7v8D3MLK54LFhsKYdqcw3E038=',
  connectionStringSecondaryKey: 'Endpoint=sb://i-4-manufacturing-jdbc-57dccb76-15da-42-yslwepq4xl.servicebus.windows.net/;SharedAccessKeyName=key;SharedAccessKey=A9xWUUVaPL589Yjd2uklS042du479Y/r5o/XlM62Xwc='
},
{
  cluster: 'jdbc-57dccb76-15da-42d3-868a-f68c2de95252-1',
  key: 'key',
  primaryKey: 'X70K5D2ZlcVkoP6xF62CNm0t+NCtzgtiva5erx73/5g=',
  secondaryKey: '7csWZ4ICSfIYCtZ100F7n+jIuzzrpPpVPagsm2wa0BQ=',
  connectionStringPrimaryKey: 'Endpoint=sb://i-4-manufacturing-jdbc-57dccb76-15da-42-bnuqwl9oar.servicebus.windows.net/;SharedAccessKeyName=key;SharedAccessKey=X70K5D2ZlcVkoP6xF62CNm0t+NCtzgtiva5erx73/5g=',
  connectionStringSecondaryKey: 'Endpoint=sb://i-4-manufacturing-jdbc-57dccb76-15da-42-bnuqwl9oar.servicebus.windows.net/;SharedAccessKeyName=key;SharedAccessKey=7csWZ4ICSfIYCtZ100F7n+jIuzzrpPpVPagsm2wa0BQ='
},
{
  cluster: 'jdbc-57dccb76-15da-42d3-868a-f68c2de95252-2',
  key: 'key',
  primaryKey: 'LpO+izwM9Ki9ebIl1F4GE7EEGe3I/6ZVAaGK/f63kMM=',
  secondaryKey: 'K347XbEpgl4lkKhB9MKAgtbr1/uJDoG9tsiYLy+rmPI=',
  connectionStringPrimaryKey: 'Endpoint=sb://i-4-manufacturing-jdbc-57dccb76-15da-42-xptt8boyb8.servicebus.windows.net/;SharedAccessKeyName=key;SharedAccessKey=LpO+izwM9Ki9ebIl1F4GE7EEGe3I/6ZVAaGK/f63kMM=',
  connectionStringSecondaryKey: 'Endpoint=sb://i-4-manufacturing-jdbc-57dccb76-15da-42-xptt8boyb8.servicebus.windows.net/;SharedAccessKeyName=key;SharedAccessKey=K347XbEpgl4lkKhB9MKAgtbr1/uJDoG9tsiYLy+rmPI='
}
```
3. Schema Registry Credentials
```json
{
  name: 'credentials',
  teamId: '57dccb76-15da-42d3-868a-f68c2de95252',
  username: 'm1Ys%!%!WygwUhKanq&R5UgNd5hsQNjOo9iQsMajV@^ZTHWvcuUBM73s6^',
  password: 'bT463XL@m%'
}
```
## Docker
### Prerequisites
1. [Docker](https://docs.docker.com/engine/install/)
2. [Docker Compose](https://docs.docker.com/compose/install/)

### Steps
1. Fill in schema registry credentials in `.env` file under `SR_CREDS` environment variable in format `username:password`
2. If your team is in EU region, change `SR_URL` to https://api.eu-west-1.parsable.net/v2/data-feed-manager/schema-registry/
3. Fill in cluster addresses and passwords in `docker-compose.yml`. There are instructions inside the file. You can also use `docker-compose-example.yml` for reference.  
4. Build docker image
    ```
    cd kafka-connect-standalone
    docker build . -t kafka-connect-standalone
    ```
5. Launch PostgresSQL database and Kafka Connect instances with Docker Compose
    ```
    docker compose up
    ```
